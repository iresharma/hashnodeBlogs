## MVP in flutter

# MVP in flutter

### MVP Architecture

Models - View - Presenter architecture is an extended version on model - view - controller architecture which is mostly used to design User Interfaces.

![https://upload.wikimedia.org/wikipedia/commons/d/dc/Model_View_Presenter_GUI_Design_Pattern.png](https://upload.wikimedia.org/wikipedia/commons/d/dc/Model_View_Presenter_GUI_Design_Pattern.png)

In my personal experience MVP is the best design pattern or architecture that you can go for in small scale personal and production projects.
I always seen the MVP architecture only been used in native iOS and Android development, but in a framework like flutter which supports and promotes breaking code of and making files as small as possible it's important to have an MVP approach

```python
- Project
	- Android          # already there
	- ios              # already there
	- build            # already there
	- release          # To keep the latest build handy
		- latest.apk
	- assets           # Your typical assets folder
		- fonts
		- images
		- logo
		- JSON/Animation # Lottie .jsons or rive .flrs
	- lib
		- Config         # Config files linke theme.dart and stuff
		- Models         # Various Models
			- DataModels.  # Data models like User model
			- ViewModels.  # View models like provider for a complex animation
		- Service        # Presenter folder
			- API          # handler files for REST API calls
			- firebase.    # handler files for firebase
			- Cache        # handler files for caching data (I prefer hivedb)
			- Global       # Files with global functions and stuff
		- Views          # Various Views
		- Widgets        # Components
```

### Config Folder

This is the so called configs folder containing the configs file. The config files in case of flutter would be files like 

- ThemeConfig.dart
- Router.dart
- APISecret.dart

### Models Folder

Models folder this is supposed be the Models to be things like user models, response model and things like that. I prefer to put all the providers necessary in here as well

This folder I usually divide into two sub folders:

- DataModels
- ViewsModels

### Servcie

This folder is what would include our **presenter** part of the **MVP** pattern.
This usually contains things like

- API

    I use chopper for my API calls so all the service files and the generated .chopper.dart files go here separated in diff. folders

- Firebase

    This contains all firebase related stuff, like any functions talking to firestore / Firebase Storage functions and things like FCM and dynamic links setup

- Cache

    This contains files that have functions related to caching function, I use hiveDb so I'd generally have a folder called typeAdapters and have all my adapters there

- Global

    This is a wrapper folder for files containing global functions, like basic string manipulation and stuff

### Views

This is pretty self explanatory containing file related to various views / pages of the app

### Widgets

To all web developers this would correspond to the Components folder in your React or Vue app. To others this folder will contain files including reusable widgets

#### This about it for MVP in flutter I hope this was helpful to you.
