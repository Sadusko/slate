# Components
## RocketPlayerComponent
> To use, your class should inherit from this component

```csharp
public class PluginPlayer : RocketPlayerComponent {

	public bool HasKitten;
	
	public void Load() {
		this.HasKitten = true;
	}
	
	public void FixedUpdate() {
		if (this.Loaded && this.HasKitten) {
			RocketChatManager.Say(this.PlayerInstance, "You have a kitten!");
		}
	}
}
```

Applied to all players when they connect and removed when they disconnect (or plugin unloaded).

### Fields
Name | Type | Default
---------- | ---------- | ----------
PlayerInstance | RocketPlayer | Current RocketPlayer instance

<aside class="notice">
Include Rocket.Components in your references.
</aside>
