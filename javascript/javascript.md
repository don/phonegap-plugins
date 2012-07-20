<!SLIDE>

![js](js.png)

<!SLIDE>
.notes cordova.exec is the method that lets javascript call into native code
each platform has their own implementation but the interface is the same
 * win - the success callback
 * fail - the error callback
 * service - the name of the service to use
 * action - the action to run in cordova
 * args - Zero or more arguments to pass to the method

	@@@ javascript
	    cordova.exec(successCallback,
				 	 failureCallback,
					 service,
					 action, 
					 args)


<!SLIDE>

	@@@ javascript
	    cordova.exec(win,
				 	 fail,
					 service,
					 action, 
					 args)


<!SLIDE>

	@@@ javascript
		var win = function (result) {
			alert (result);		
		}

		var fail = function (error) {
			alert ("Error " + error)
		}

<!SLIDE>	
.notes when we run cordova.exec it calls into our native plugin
if the plugin is successful, it will call win with the String "Hello, World"

	@@@ javascript
		var service = "Hello",
			action = "greet",
			args = ["World"];

	    cordova.exec(win, fail, 
			service, action, args);

			
<!SLIDE>	
.notes it is fine to call cordova.exec directly
typically a plugin provides wrapper javascript to make a nicer API for the plugins
usually you'll see the success failure callbacks as the last parameters, since they are optional

	@@@ javascript
	var greet = function (name, win, fail) {
		cordova.exec(win, fail, 
			"Hello", "greet", [name]);	    
	}

	greet("World", win, fail);
	
<!SLIDE>
.notes TODO make sure this works!

	@@@ javascript
	cordova.define("cordova/plugin/hello",
	  function (require, exports, module) {

	    var exec = require('cordova/exec');

	    function greet(name, win, fail) {
	      exec(win, fail, "Hello",
	          "greet", [name]);
	    }

	    module.exports = {
	      greet: greet
	    }
	  }
	);
