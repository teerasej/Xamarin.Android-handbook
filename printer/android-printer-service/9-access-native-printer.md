
# ใช้ Printer Manager

การเรียกใช้ Printer Manager จะลดขั้นตอนจาก[แบบวิธี Share ไปที่ printer service](8-use-share.md) ลง 1 ขั้นตอน

## 1. สร้าง custom printer adapter จำเป็นต้องเขียนโดยเฉพาะฝั่ง Android เพื่อให้สามารถทำงานกับไฟล์เฉพาะได้

สร้างไฟล์ **CustomPrintDocumentAdapter.cs**

```cs
using System;
using Android.OS;
using Android.Print;
using Java.IO;

namespace PDFPrinter
{
    public class CustomPrintDocumentAdapter : PrintDocumentAdapter
    {
        internal string FileToPrint { get; set; }

        internal CustomPrintDocumentAdapter(string filePath)
        {
            FileToPrint = filePath;
        }
        public override void OnLayout(PrintAttributes oldAttributes, PrintAttributes newAttributes, CancellationSignal cancellationSignal, LayoutResultCallback callback, Bundle extras)
        {
            if (cancellationSignal.IsCanceled)
            {
                callback.OnLayoutCancelled();
                return;
            }


            PrintDocumentInfo pdi = new PrintDocumentInfo.Builder(FileToPrint).SetContentType(PrintContentType.Document).Build();

            callback.OnLayoutFinished(pdi, true);
        }

        public override void OnWrite(PageRange[] pages, ParcelFileDescriptor destination, CancellationSignal cancellationSignal, WriteResultCallback callback)
        {
            InputStream input = null;
            OutputStream output = null;

            try
            {
                //Create FileInputStream object from the given file
                input = new FileInputStream(FileToPrint);
                //Create FileOutputStream object from the destination FileDescriptor instance
                output = new FileOutputStream(destination.FileDescriptor);

                byte[] buf = new byte[1024];
                int bytesRead;

                while ((bytesRead = input.Read(buf)) > 0)
                {
                    //Write the contents of the given file to the print destination
                    output.Write(buf, 0, bytesRead);
                }

                callback.OnWriteFinished(new PageRange[] { PageRange.AllPages });

            }
            catch (FileNotFoundException ex)
            {
                //Catch exception
                System.Diagnostics.Debug.WriteLine(ex);
            }
            catch (Exception e)
            {
                //Catch exception
                System.Diagnostics.Debug.WriteLine(e);
            }
            finally
            {
                try
                {
                    input.Close();
                    output.Close();
                }
                catch (IOException e)
                {
                    e.PrintStackTrace();
                    System.Diagnostics.Debug.WriteLine(e);
                }
            }
        }
    }
}

```

## 2. เรียกใช้ Print Manager

```cs
// MainActivity.cs

buttonPrintPDF.Click += async (sender, e) =>
            {
                // await Share.RequestAsync(new ShareFileRequest
                // {
                //     Title = "PDF File",
                //     File = new ShareFile(localPDFFile.AbsolutePath, "application/pdf")
                // });

                var printManager = (PrintManager)GetSystemService(Context.PrintService);
                var printAdapter = new CustomPrintDocumentAdapter(localPDFFile.AbsolutePath);
                printManager.Print("My print", printAdapter, null);
            };
```