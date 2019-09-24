# Importing the assets

## Configuring Serilog

Before starting importing a ```Logger``` from ``Serilog`` is needed.

Here an example code to log in your current base directory.

```C#
 var logFilePath = $"{AppDomain.CurrentDomain.BaseDirectory}\\Logs\\logs.json";
            Log.Logger = new LoggerConfiguration()
               .MinimumLevel.Debug()
               .WriteTo.File(logFilePath, rollingInterval: RollingInterval.Day)
               .CreateLogger();
```

## Fetching the configured languages
Before starting importing you need to fetch all the umbraco configured languages. **Uvendia** provides you with such a method:

```C#
var languages = UmbracoSettings.GetUmbracoConfiguredLanguages();
```
The namespace is ``Uvendia.Domain.Repositories``.

## Importing
The code below shows how to import the assets:

```C#
var response = await Manager.Execute(data, languages, Log.Logger);
```

### Reponse object

The expected ``response code`` is ``OK``.
But in case that's not true. The response object contains all the necessary information to trace back any issue that has occurred.

```C#
namespace Uvendia.Importer.Process
{
    public class ProcessResponse
    {
        /// <summary>
        /// Gets or sets the response code.
        /// </summary>
        /// <value>
        /// The response code.
        /// </value>
        public ResponseCode ResponseCode { get; set; } = ResponseCode.Ok;
        /// <summary>
        /// Gets or sets the (info, warning or error) message.
        /// </summary>
        /// <value>
        /// The message.
        /// </value>
        public List<string> Messages { get; set; } = new List<string>();
        /// <summary>
        /// Gets or sets the validation errors.
        /// </summary>
        /// <value>
        /// The validation errors.
        /// </value>
        public List<string> ValidationErrors { get; set; } = new List<string>();
        /// <summary>
        /// Gets or sets the exception.
        /// </summary>
        /// <value>
        /// The exception.
        /// </value>
        public Exception MainException { get; set; }

        public List<Exception> Exceptions { get; set; } = new List<Exception>();

        /// <summary>
        /// Gets or sets the processed data.
        /// </summary>
        /// <value>
        /// The processed output data.
        /// </value>
        public object ProcessedData { get; set; }
    }
}
```