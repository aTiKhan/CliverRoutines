# CliverRoutines

## Overview
A cross-platform C# lib that exposes generally used routines: 
- serializing which replaces standard .NET settings for desktop applications; 
- logging with threading and session support;
- auxiliary routines;

## Framework
.NET Standard 2.0

## Supported platforms
It is supposed to run anywhere with .NET Standard lib supported. 
Presumably it will run on any Xamarin platforms (probably with minor updates required). 

The most concern is peculiarities of the target file system because serializing and logging routines write/read files and do everything as automatically as possible.

### Tested on:
- Windows 7, 10 in C# projects of any configuration built in Visual Studio;
- macOS High Sierra 10.12 in Xamarin.Mac projects built in Visual Studio for Mac;


## Serializing 
### Classes: 
Cliver.Config, Cliver.Settings 

### Description
It is more powerful and flexible that the built-in .NET settings for desktop and provides such features like:
- saving to disk and restoring from disk of values of class members that need it;
- serializing types are flexibly defined in the application;
- serializing types can inherite from another serializing types;

### How to use:
Define a class that is to be serialized and make it a subclass of Cliver.Settings class. Create anywhere a public class member of this type. Add the following calls in the beginning of the app: 

(optionally) Cliver.Config.Initialize(); 

(mandatory) Cliver.Config.Reload();

That's all. Now the members will be set to the previously serialized values if any, otherwise keep the values they are initialized with.

To serialize current value of a member, call Save() in it.

Look at some of my recent C# projects in github to see a live usage example.


## Logging 
### Classes: 
Cliver.Log

### Description
It provides such features like:
- thread-safe;
- (option) writting log files per thread;
- (option) writting logs in sessions that an app can open and close many times during its work;
- (option) automatic old log cleanup; 

### How to use:
Add the following calls in the beginning of the app: 

(optionally) Cliver.Log.Initialize();

To write to log call either Cliver.Log.Write() or Cliver.Log.Main.Write() or more specific methods.

Look at some of my recent C# projects in github to see a live usage example.

## Auxiliary routines 
### Description
Anything handy that is needed in general development.

### How to use:
Look at some of my recent C# projects in github to see a live usage example.
