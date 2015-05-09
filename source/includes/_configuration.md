# Configuration
IRocketConfiguration

```csharp
public class MyFancyConfiguration : IRocketConfiguration {

	public IRocketConfiguration DefaultConfiguration{
		get {
			MyFancyConfiguration configuration = new MyFancyConfiguration();
			configuration.ShowConfiguration = true; 
			return configuration;
		}
	}
	
	public bool ShowConfiguration;
	
}
```

### Fields
Name | Type | Default
---------- | ---------- | ----------
DefaultConfiguration | IRocketConfiguration | Return the default configuration, used to create the configuration file

