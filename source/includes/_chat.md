# ChatManager
RocketChatManager

```csharp
public class CommandFancyMe : IRocketCommand
{
  public bool RunFromConsole { get { return false; } }
  public string Name { get { return "FancyMe"; } }
  public string Help { get { return "My fancy helpful info."; } }
  public CommandFancyMe() {}
  
  public void Execute(RocketPlayer caller, string[] Args)
  {
    //Targets a specified player - In this case the user who issued the command
    RocketChatManager.Say(caller, "Message about how fancy I am here.");
  }
}
```

### Fields
Name | Type | Default
---------- | ---------- | ----------
ChatManager | RocketChatManager | Returns a specified string or value to the server or a player

