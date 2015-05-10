# Plugin
## RocketPlugin
> If you want to use a configuration, choose RocketPlugin<IRocketConfiguration>

```csharp
public class MyFancyPlugin : RocketPlugin {

	public static MyFancyPlugin Instance;
	private bool messageSent = false;
	
	protected override void Load() {
		Instance = this;
	}
	
	protected override void Unload(){
		//Clean up your mess before the plugin is unloaded
	}
	
	private void FixedUpdate() {
		if (this.Loaded && !this.messageSent) {
			RocketChatManager.Say(Translate("myfancyplugin_message"));
			messageSent = true;
		}
	}
	
	private override Dictionary<string, string> DefaultTranslations{
		get
		{
			return new Dictionary<string, string>(){
				{"myfancyplugin_message","Hi Dave."}
			};
		}
	}
}
```

### Fields
Name | Type | Default
---------- | ---------- | ----------
Loaded | boolean | Is true as soon as translation & configuration is initialized

## RocketPlugin&lt;IRocketConfiguration&gt;
> Specify a implementation of the interface IRocketConfiguration as type parameter

```csharp
public class MyFancyPlugin : RocketPlugin<MyFancyConfiguration> {

	public static MyFancyPlugin Instance;
	private bool messageSent = false;
	
	protected override void Load() {
		Instance = this;
	}
	
	protected override void Unload(){
		//Clean up your mess before the plugin is unloaded
	}
	
	private void FixedUpdate() {
		if (this.Loaded && !this.messageSent && Configuration.ShowConfiguration) {
			RocketChatManager.Say(Translate("myfancyplugin_message",42));
			messageSent = true;
		}
	}
	
	private override Dictionary<string, string> DefaultTranslations{
		get
		{
			return new Dictionary<string, string>(){
				{"myfancyplugin_message","The number is: {0}"}
			};
		}
	}
}
```

<aside class="notice">
See <a href="#rocketplugin<irocketconfiguration>">IRocketConfiguration</a> for details on how to create a configuration class 
</aside>

### Fields
Name | Type | Default
---------- | ---------- | ----------
PlayerInstance | RocketPlayer | Current RocketPlayer instance
Configuration | &lt;IRocketConfiguration&gt; | Contains the values from your configuration

