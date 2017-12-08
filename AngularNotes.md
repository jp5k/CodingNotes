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

