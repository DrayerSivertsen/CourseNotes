# Design Patterns

## Delegates
Many core objects receive events of one kind or another

Delegation: appoint a different object to handle some request for you

### Why delegates?
Sometimes you want a single object to respond to multiple types of events

Kotlin and Swift are both single inheritance languages

### Singletons
Sometimes you need exactly one instance of an object throughout your program
If you only have one view[controller] that's pretty simple it holds all the objects

Note: if you turn your screen in android it deletes the previous version and presents you with a newly initialized horizontal view.

## The Singleton Pattern
The goal is to provide an object which can:
* ensure they only have one instance
* provide easy access to that instance
* control their instantiation

Kotlin:
```
object MySingleton {
    fun myMethod(): Int {
        return 5
    }
}

MySingleton.myMethod() // 5
```
Swift:
```
class Singleton {
    static let shared = Singleton()
}
```
In swift, heavy lifting is done by the static keyword
All ios apps include a AppDelegate class
* serves as a delegate to the UIApplication
* mostly there to handle to app startup stuff

assessed by:
```
let delegate = UIApplication.shared.delegate as! AppDelegate
```
Used to share something across your application

## MVC - the problem
Software typically models some actual process or logic
* game rules, business requirements, etc

Need to keep track of information from problem domain
Need to be able to cause updates

## The old days
Everything in the computer was simply text written to a screen
Users moved through program task in well-defined order

## Coming of the GUI
Controls now made up of little blobs of code
Controls have their own settings, own internal data storage

Leads to new complications:
* chances are, UI now allows data to be entered in arbitrary order
* need to updated UI elements if internal state changes

Managing state and UI are separate, but related

## Model-View-Controller
Idea: break application into loosely coupled pieces

Model
* understands what you're representing
* stores systems state
* expresses rules of problem domain
* in web-dev or networked apps, often a database server
* in mobile app, probably a class with internal data storage
* may provide functionality for data persistence

View
* shows model information to the user
* provides interface
* specific way of presenting the data in the model
* single app may have multiple views


Controller
* handles updates and communication between view and model
* center of communication between view and model
* handles input validation, does any business ops required before model is updated

* in web-dev, this is your business logic
* in app, the controller gets events from the view and interacts with the model

### Controller types
View controllers
* primarily deal with managing the view
* responds to user created events
* interacts with model as needed

Model controllers
* helps manage a complex model
* allows view controllers to focus on managing the view

Helper controllers
* consolidate a bunch of related functionality into a single place

## MVC and Mobile
Android and IOS apps have generally MVC structure
* views and activies are views
* matching class implementation is a controller

Both provide a mechanism for persistant storage of data
* standard files
* database libraries
Single view




