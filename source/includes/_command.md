#Command
##IRocketCommand

```csharp
	public class CommandAheal : IRocketCommand {
		public bool RunFromConsole {
			get {
				return false;
			}
		}
		public string Name {
			get {
				return "fancy";
			}
		}
		public string Help {
			get {
				return "Returns a message to you in chat.";
			}
		}
		
		// Run the command.
		public void Execute(RocketPlayer caller, string[] command) {
			if (caller == null) {
				Logger.Log("This command cannot be called from the console.");
				return;
			}
			RocketChatManager.Say(caller, "You are fancy!");
		}
	}
	
```

An interface to create a command.

###Properties
Name | Type | Default
------------ | ----------- | -----------
RunFromConsole | bool | true only if want to run from console
Name | string | The command name.
Help | string | The help info for the command.

###Methods
Name | Parameters | Output | Description
------------ | ----------- | ----------- | ----------
Execute | RocketPlayer, string\[\] | none | Executes the command, RocketPlayer is null if called in the console
