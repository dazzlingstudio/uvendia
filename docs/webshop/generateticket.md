# Generating e-ticket

To generate an event e-ticket use the ``ReportCreator`` object.

```C#
var rm = ReportCreator.GenerateTicketPDF(order, Thread.CurrentThread.CurrentCulture.Name);
var stream = ReportCreator.GenerateReportAsStream(reportModel, out string mimeType);
return File(stream, mimeType, reportModel.FileName);
```