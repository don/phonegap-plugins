<!SLIDE bullets incremental>
.notes the concepts for iOS are the same but the implementation is a bit different
implement CDVPlugin
create instance methods for each action
ObjectiveC
XCode 
.notes Plugin Directory will exist if you've created your project with the cordova command line scripts

![iOS](ios_title.png)

* CDVPlugin

<!SLIDE>

	@@@ c
	#import <Cordova/CDVPlugin.h>
	
	@interface HWPHello : CDVPlugin

	- (void) greet:(NSMutableArray*)arguments 
		  withDict:(NSMutableDictionary*)opt;

	@end

<!SLIDE>

	@@@ c
	#import <Cordova/CDVPlugin.h>

	@interface HWPHello : CDVPlugin

	- (void) greet:(NSMutableArray*)arguments 
		  withDict:(NSMutableDictionary*)opt;
		
	- (void) leave:(NSMutableArray*)arguments 
		  withDict:(NSMutableDictionary*)opt;

	@end


<!SLIDE>
.notes id is the callbackId
note that in iOS we need to use the callbackId and decide to call success or failure

	@@@ c
	- (void)greet:(NSMutableArray*)args ...
	{
	  NSString* id = [args objectAtIndex:0];

	  NSString* name = [args objectAtIndex:1];
	  NSString* msg = [NSString
	    stringWithFormat: @"Hello, %@", name];

	  CDVPluginResult* result = [
		CDVPluginResult 
		resultWithStatus:CDVCommandStatus_OK
	     messageAsString:msg];

	  [super success:result callbackId:id];
	}
	
<!SLIDE>

![cordova.plist](cordova.plist.png)

<!SLIDE>

	@@@ c
	CDVPluginResult* result = // ...
	NSString* javaScript = 
		[result toSuccessCallbackString:id];
		
	[self writeJavascript:javaScript]



