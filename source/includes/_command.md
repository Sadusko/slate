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
				return "aheal";
			}
		}
		public string Help {
			get {
				return "Heals you if you are admin and sets you god and vanished.";
			}
		}
		
		// Run the command.
		public void Execute(RocketPlayer caller, string[] command) {
			if (caller == null) {
				Logger.Log("This command cannot be called from the console.");
				return;
			}
			if (command.Length > 0) {
				RocketChatManager.Say(caller, "This command is only for yourself.");
				return;
			}
			// Check if Admin
			if (caller.IsAdmin && caller.Equals(RocketPlayer.FromName(command[0]))) {
				caller.Features.GodMode = true;
				caller.Features.VanishMode = true;
				caller.Infection = 0;
				caller.Hunger = 0;
				caller.Thirst = 0;
				caller.Freezing = 0;
				caller.Heal(100, true, true);
				RocketChatManager.Say(caller, String.Format("You are an Admin {0} [{1}], and now a vanished god at full health."), caller.CharacterName, caller.SteamName);
			} else {
				RocketChatManager.Say(caller, String.Format("For trying to call this admin-only command, you get more zombies {0} [{1}]!", caller.CharacterName, caller.SteamName));
				caller.GiveZombie(50);
			}
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
Execute | RocketPlayer, string[] | none | Executes the command, RocketPlayer is null if called in the console
