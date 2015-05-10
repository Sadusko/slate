# Player
## RocketPlayer

An extension for most used player info and methods.

```csharp
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
```

### Properties
Name | Type | Default | get or set
---------- | ---------- | ---------- | ----------
Player | Player | SDG.Player Instance | get only
CSteamID | CSteamID | Player's Steam ID | get only
Features | RocketPlayerFeatures | Player's Features component | get only
Events | RocketPlayerEvents | Player's Events component | get only
Inventory | PlayerInventory | Player's Inventory | get only
SteamGroupID | CSteamID | Player's Group ID | get only
Groups | List<Group> | List of Rocket groups belonged to | get only
Permissions | List<string> | List of permissions | get only
IsAdmin | bool | true if admin, false otherwise | get only
Position | Vector3 | Player's position | get only
Stance | EPlayerStance | Player's current stance | get only
Rotation | float | Direction player is looking | get only
Stamina | byte | Player's current stamina | get only
CharacterName | string | Player's Character name | get only
SteamName | string | Player's Steam name | get only
Infection | byte | Player's Infection level | get and set
Experience | uint | Player's Experience | get and set
Health | byte | Player's Health | get only
Hunger | byte | Player's Hunger | get and set
Thirst | byte | Player's Thirst | get and set
Broken | bool | Player's broken bones | get and set
Bleeding | bool | Player is bleeding | get and set
Dead | bool | Player is dead | get only
Freezing | bool | Player is freezing | get only

###Methods

Name | Parameters | Output | Description
---------- | ---------- | ---------- | ----------
Equals | RocketPlayer | bool | Check if 2 RocketPlayers are equal
GetComponent<T> | Component | Component | Find instance of component type T
(static)FromName | string | RocketPlayer | Get RocketPlayer instance, null if not found
(static)FromCSteamID | CSteamID | RocketPlayer | Get RocketPlayer instance, null if not found
(static)FromPlayer | Player | RocketPlayer | Get RocketPlayer instance, null if not found
(static)FromSteamPlayer | SteamPlayer | RocketPlayer | Get RocketPlayer instance, null if not found
GiveItem | ushort, byte, bool=false | bool | Gives player (byte) of item id (ushort), success returns true
GiveVehicle | ushort | bool | Gives player 1 of vehicle id (ushort), success returns true
GiveZombie | byte | none | Gives this player (byte) zombie(s).
HasPermission | string | bool | Checks if player has permission (string), true if found
Kick | string | none | Kicks player for reason (string)
Ban | string, uint | none | Bans player for reason (string) and seconds (uint)
Admin | bool, RocketPlayer=null | none | Admins player if true, unadmins if false [caller (RocketPlayer)]
Teleport | RocketPlayer | none | Teleports player to another player (RocketPlayer)
Teleport | Vector3, float | none | Teleports player to position (Vector3) facing (float)
Teleport | string | bool | Teleports player to map node (string), success returns true
Heal | byte, bool?=null, bool?=null | none | Heals player by amount (byte), bleeding, and broken (bool? x2)
Suicide | none | none | Causes player to suicide
Damage | byte, Vector3, EDeathCause, ELimb, CSteamID | EPlayerKill  | How player was killed

##RocketPlayerFeatures

A set of features for players.  This is a sealed class and should be accessed through RocketPlayer.

### Properties
Name | Type | Default | get/set
---------- | ---------- | ---------- | ----------
VanishMode | bool | false | get and set
GodMode | bool | false | get and set
