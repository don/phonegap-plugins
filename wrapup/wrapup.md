<!SLIDE bullets incremental>
.notes add to script
* Maintaining plugins for multiple platforms
* Building, Packaging and Distributing plugins.
* Installing  (apt-get | npm  for plugins?)
* Making plugins work with PhoneGap build
* https://github.com/alunny/cordova-plugin-spec

# Future

<!SLIDE bullets incremental>

# Plugin Spec
* [https://github.com/alunny/cordova-plugin-spec](https://github.com/alunny/cordova-plugin-spec)

<!SLIDE>
	@@@ xml
	<plugin xmlns= ...
		    id="com.example.hello"
	    	version="0.9.0">
		<name>Hello</name>
		<asset src="www/hello.js" 
			target="hello.js" />
		<platform name="ios">
		    <header-file src="HWPHello.h" />	
		    <source-file src="HWPHello.m" />	
			<plugins-plist key="Hello" 
				string="HWPHello" />	
	    </platform>	
		<platform name="android">
			...
		</platform>
	</plugin>

<!SLIDE bullets incremental>

# pluginstall

* pluginstall PLATFORM PROJECT PLUGIN
* pluginstall ios . ~/plugins/Hello

<!SLIDE>
.notes * start writing code
* read the Cordova source
* read the Plugin source (some will be dated)

# Go Build a Plugin

<!-- !SLIDE
The team is working on documentation
.notes https://issues.apache.org/jira/browse/CB-862

# links -->

<!SLIDE>
.notes TODO add a link to these slides on github

## PhoneGap Plugins
 
Don Coleman

don@chariotsolutions.com

http://github.com/don

@doncoleman
