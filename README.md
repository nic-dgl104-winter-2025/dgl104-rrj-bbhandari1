[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MMj2nZMu)
# Rsearch and Reflection Journal
Research and Reflection Journal for DGL 104 course

# Week 8

### As developers, I encourage you to draw on programming knowledge when assessing apps. The first thing we tend to assess when critically examining an app is the interface and the UX. 
  Consider your programming knowledge when assessing apps: 
* Frameworks/libraries/APIs 
* Data structures 
* Platform-specific conventions

### User stories are a common tool employed in the design of user-facing systems 
* User stories are written in natural language from the perspective of the user 
* Typically written in the form: "As a user, I can " 
* User stories facilitate intra-team communication


### The downside of user stories is the lack of implementation details 
* Typically written without immediate consideration of technical constraints.  
* Issues related to technical considerations are sometimes overlooked (e.g. performance criteria). 
* User stories can be written with technical concerns in mind, but this may not be an ideal approach.

### A technical design document (TDD) is a written artefact that addresses technical concerns in a design context 
* Goal: Produce an unambiguous document detailing: 
* Architecture 
* Feature implementation 
* Testing plan 
* Performance criteria 
* There is no accepted standard for the development of TDDs. 
* TDDs can encompass a complete software design, or specific feature

### Functional requirements describe software features on an input/output basis 
* Just like 'functions' in programming (or in mathematics). 
* These may be included in a TDD, or related document. 
* Typically derived from user stories, or from use cases (a more technical-first approach to modeling systems).

### We can use the input/output approach to develop clear 'specifications' for our apps 
* Functional requirements and specifications are part of the standard software engineering toolkit.
* If our user story says: "as a forum user I can see posters' profile pictures as avatars", this might imply the following set of functional requirements: 
* Update profile: Enter required profile data (name, email) and optional profile data (profile pic, address, website, social accounts) -> return profile page with default content (e.g. default avatar) for incomple optional data.
    

# Week 10

### MV* refers to the collection of user interface architecture patterns using Model and View 
* Model View Controller (MVC)  
* Model View Presenter (MVP) 
* Model View Adapter (MVA) 
* Model View Intent (MVI) 
* Model View ViewModel (MVVM)

### Model View Controller was the first; Model View ViewModel is common in apps today 
* MVC developed as part of Smalltalk at Apple. 
* MVC became an integral part of iOS development. 
* MVC is a key architectural pattern on the web (Django, Ruby on Rails). 
* MVVM is presently the most commonly used in app development 
* Mobile: Jetpack Compose, SwiftUl 
* There are some MVVM-specific web frameworks too

### The common thread across all MV* patterns is separation of concerns and testable code 
* The Model contains the business logic of the app. 
* The View represents all app data and captures user interactions. 
* The Model and View should never intersect -separation of concerns. 
* All MV* patterns are graphical in nature – GUI architecture.


### Model View Controller (MVC) is a user interface design / architecture pattern 
* Sometimes referred to as a design pattern... 
* Sometimes referred to as an architectural pattern... 
* All MV* patterns are user interface driven

### The model contains the software's business logic 
* Typically data and all logic that creates, modifies and stores data. 
* Data is often modeled by OOP classes or enums. 
* Model must be completely independent of the View

### The View contains the user interface, presents data and interaction opportunities to the user
* No data nor state should be stored in the View. * The View only represents what is stored in the Model.
* Mobile: Android Studio design editor, Xcode interface builder


### The Controller mediates between the two and ensures Model and View are not connected 
* The Controller captures user actions from the View which then updates the Model. 
* The Mode notifies the Controller of changes which updates the View


### Although MVC remains fairly common in web apps, but less so in mobile today 
* MVC is still 'enforced' by frameworks like Ruby on Rails, Django, Angular, Vue and others. 
* Up until relatively recently MVC was more common with iOS apps – recently replaced by the declarative SwiftUl framework which favours MVVM. 
* Similarly with Android, although MVI was more common