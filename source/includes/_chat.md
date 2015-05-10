# ChatManager
RocketChatManager

```csharp
RocketChatManager.Say(caller, "Message about how fancy I am here.");
RocketChatManager.Say(caller.CSteamID, "Messaeg about how fancy I am here");
RocketChatManager.Say("Broadcast about how fancy Rocket is.");
```

### Methods
Name | Parameters | Output
---------- | ---------- | ----------
Say | player, string | private message to player
Say | CSteamID, string | private message to player
Say | string | broadcasts message to server
