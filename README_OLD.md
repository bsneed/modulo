Modulo
======
Modulo is a source code dependency manager.  It will focus *ONLY* on source code dependency management and nothing else.  In a similar vain to cocoapods, but not be cocoa or xcode specific.

Modulo Specification
===================

*Example modulo.spec:*

```json
{
	"name": "ios-utils",
	"projectUrl": "http://github.com/setdirection/ios-utils",
	"moduleUrl": "git@github.com:setdirection/ios-utils.git",
	"licenseUrl": "https://github.com/setdirection/ios-utils/blob/master/LICENSE",
	"sourcePaths": [
		{ "path": "/source" },
		{ "path": "/source2" }
	],
	"moduloDependenciesPath": "/dependencies",
	"moduloDependencies": [
		{ 
			"name": "ios-shared", 
			"url": "git@github.com:setdirection/ios-utils.git"
		},
		{ 
			"name": "viewjs", 
			"url": "git@github.com:setdirection/viewjs.git"
		}
	],
	"otherDependencies": [
		{ 
			"name": "AVFoundation", 
			"defaultPath": "../something/AVFoundation.framework", 
			"projectUrl": "http://developer.apple.com" 
		},
		{ 
			"name": "UIKit", 
			"defaultPath": "../something/UIKit.framework", 
			"projectUrl": "http://developer.apple.com"
		 }
	]
}
```

*Example directory structure:*

```text
modulo.spec
/source
	...
/source2
	... 
/dependencies
	/ios-shared
		modulo.spec
		/source
			...
	/viewjs
		/source
			...
```			
	
*Example of a project adding a module:*

?> modulo add ios-utils ./dependencies

or
	
?> modulo add git@github.com:setdirection/ios-utils.git ./dependencies


*Example output of the add command*

```text
Add the following directories to your project, or build paths:
	./dependencies/ios-utils/source
	./dependencies/ios-utils/source2
	./dependencies/ios-utils/ios-shared
	./dependencies/ios-utils/viewjs
	
The following additional dependencies must be added as well:
	AVFoundation.framework (usually found at "/../something/AVFoundation.framework")
	UIKit.framework (usually found at "/../something/UIKit.framework")
```


Commands
========

Add a dependency to user project.

?> modulo add [name/url] [destination] 



WIP.

Tests
=====

Modulo can be tested using scripts in the [Scripts](Scripts/) folder.

At this time, there is only one script that tests a variety of commands. It can be found at [`tests.py`](Scripts/tests.py).
It requires a working network connection as it clones and updates test repos hosted on Github. In order to use it, place the `modulo` executable to be tested at `/tmp/modulo` on your test machine and execute the script from the command line.
Currently some later tests may depend on previous ones completing successfully. This is not ideal but can be refactored as needed in the future.

