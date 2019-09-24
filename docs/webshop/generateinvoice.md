# Generating invoice

To generate an order invoice use the ``ReportCreator`` object.

```C#
var rm = ReportCreator.GenerateOrderInvoicePDF(order, Thread.CurrentThread.CurrentCulture.Name);
var stream = ReportCreator.GenerateReportAsStream(rm, out string mimeType);
return File(stream, mimeType, rm.FileName);
```