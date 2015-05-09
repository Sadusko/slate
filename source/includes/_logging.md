#Logging
## Logger

```csharp
Logger.LogError(ErrorMessage);
Logger.LogException(Exception);
Logger.LogWarning(Warning);
Logger.Log(Exception)
Logger.Log(Message);
```

Sends a message to the console and to save in the log.

### Methods
Name | Parameters | Output
---------- | ---------- | ----------
Log | string | white string to console
Log | exception | red exception error to console
LogException | exception | red exception error to console
LogError | string | red error to console
LogWarning | string | yellow string to console
