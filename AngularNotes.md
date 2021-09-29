# Angular Notes

## General

New project is following in CLI:

`ng new angular-tour-of-heroes`

To open application in a browser, port 4200 default

`ng serve --open`

Angular's interpolation binding syntax are `{{ }}`

File pathing - it is possible to have relative paths rather than absolute paths.

ALWAYS do work in ngOninit rather than constructor !!

Angular docs are great for API lookups.

## Services - 
Lots of good info in John Papa and Ward Bell Pluralsight play  by play
When creating a service, dependency injection is scoped.  Only put service in declaration
of the of the lowest component in the hierarchy that needs it.

Use HTTP_PROVIDERS in app component as the import.  This will give http service and anything 
extra you needed.  Always import and declare this in app component.  Same with rxjs.  Put this 
in app component, then everything has it within your application.

Always catch errors from observables.

## Barrels
Angular2/core is a barrel.  Use barrels in an index.ts file to export what you need.  In 
app.component you can then import whatever you need from that particular module.

## POSTMAN
Like SOAPUI, but great for checking data back from server.

## Notes from Pluralsight Angular Forms by Mark Zamoyta
Covers template driven forms (but also applies to reactive forms too)

Can the angular2 seed project
git clone xxxx yyyy will clone the repository into your respository named 'yyyy'
OR easier way is just to use the angular CLI.
`ng new angular-tour-of-heroes`

To get latest version of Angular Cli
------------------------------------
`npm update -g @angular/cli`

Then to generate a new project using the CLI 
ng new MyNewProject 

Then cd into project, and to serve it up:
`ng serve --open`

npm install
-----------
calling npm install will look in package.json and install everything we need. Also call npm 

Reactive Forms (i.e not ones used on this course)
-------------------------------------------------
Use a component's template. 
They create a Form Model in TypeScript (which must be kept in sync with the template)
Main advantage is that you can then Unit Test against the Form Model (rather than the DOM itself)
Also, validation can be in the form model itself. 

Important - note that HttpModule and FormsModule need to be imported in app.module for this Pluralsight Course.

The application is bootstrapped using main.ts which passes in the AppModule.  This is then also bootstrapped in 
app.module.ts

The Home form where all the course is centered
----------------------------------------------
Just add a selector directive from the app.component.html file `<app-home></app-home>`

Template variable #form takes in the directive ngForm using following syntax:
`#form="ngForm"`  Can then bind directly to #form, e.g. form.pristine

Specify ngModel on an input or any tag, to make angular aware of it.  And must associate a name with the tag.

Browser Validation
------------------
Important to turn OFF browser validation by using novalidate in the form tag.  This is an HTML standard, not an angular 
feature. 

Bootstrap
---------
Go to [getbootstrap.com] and go to get started.  In the CDN section, just copy the .css (don't worry about the js
or the theme!!).  Just paste the link at the bottom of the index.html section. 

 