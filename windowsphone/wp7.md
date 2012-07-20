<!SLIDE bullets incremental>

![Windows Phone](windows_phone_logo.jpg)

* BaseCommand

<!SLIDE>

	@@@ java
	namespace Cordova.Extension.Commands
	{
	  public class Hello : BaseCommand
	  {
	    public void greet(string args)
	    {
          string name = JsonHelper
			.Deserialize<string>(args);
          string message = "Hello, " + name;

          PluginResult result = 
              new PluginResult(
				PluginResult.Status.OK,
	 			message);

          DispatchCommandResult(result);
	} } }
