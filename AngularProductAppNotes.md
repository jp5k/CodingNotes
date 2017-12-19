# Angular Product App Notes

## AngularProductApp

Angular Product Application from Pluralsight - good first Angular 2 project



## Corporate Proxy Issue When Running Project At Work
To get round corporate proxy, create a .typingsrc file in the root with the following config:

proxy="http://webfilter.etc.com:80"

rejectUnauthorized="false"

## Chapter 2 - Getting Started

Angular has expressive HTML/Powerful Data Binding/Modular By Design/Built in back end navigation

 Application = Component + Component + Component & Services

Each Component = Template HTML (**the view**)  +  Class (Properties and Methods) **(the code)** + Metadata **(Additional Data to Angular)**

Define angular modules to group components into cohesive functionality.
Every app has **at least one** module, called the Root Angular Module.

[D.Kurata problem solver](https://blogs.msmvps.com/deborahk/angular-2-getting-started-problem-solver/)   for blog of course.

Our Application has   index.html  -->  App Component --> Welcome Component    
											|									
											|-> Product List Component  -->  Star Component (nested)
													|							  ->
													|							  |	
													|-> Product Detail Component --
			Product Data Service


## Chapter 3 - First Things First 

__Typescript__

Strongly typed, therefore intellisense, refactoring, tooling etc..

Superscript of Javascript, transpiles to plain JS.

Implements class-based-object orientation (interfaces, inheritance,etc..)
  
[Typescript Playground](http://www.typescriptlang.org/Playground)

See also pluralsight course TypeScript fundamentals, Angular with TypeScript

npm (node package manager) - command line utility.  Interfaces with repos of open source projects.  
Installs libraries, packages , and applications.  

https://www.npmjs.com  (installing node also installs npm)

Setting up an Angular 2 App normally requires the following:
1. Create an application
2. Add package definition and config files
3. Install the packages
4. Create the app's Angular module
5. Create the main.ts file
6. Create the host web page (index.html)

OR download the quick steps from https://github.com/angular/quickstart   OR AngularCli (creates files and sets up boiler plate application) https://github.com/angular/angularCli

app is default directory (The main App directory)

Each subfolder within the directory represents subfeatures of the application.

npm install --> installs all libraries we need

npm start --> starts the lite-server, watching "tsc-w" (typescript compiler in watch mode)

Each .ts typescript file will transcompile to a js javascript file,l with a js.map file to help debugging.  

Modules - help with namespace resolution and code organisation.  If we use an 'export' declaration in a class, that file automatically becomes a module.

Angular has at least one module (the app module).  

Within each module, define the set of components associated with the module.

Each component belongs to **one and only one** angular module.

In index.html we configure 'Systemjs.config.js' for importing all of our code files within Systemjs.config it defines the main app as being the entry point.  

## Chapter 4 - Introduction to components 

Component is made up of the following:  
1. Template **(view layout, created with HTML, includes bindings and directives)**   
2. Class (properties and Methods) **Code supporting the view, created with TypeScript ** 
3. Metadata **Extra data for angular, Defined with a decorator ** 

Decorator is a function that adds metadata to a class, it's members, or its method arguments.  Always prefixed with @ e.g. @Component is a decorator (can also build our own decorators).  If decorating a class, the decorator is directly **above the class definition**.  A selector **:** within a decorator allows component to be used in html, uses a directive name e.g. 'pm-app'.

Component should always have a view (HTML).  

Use {{ }} for data binding of elements (e.g. page Title).

__Importing what we need__

Need 'import' statement in module to let application know about an external function or class, like import in java.  Import allows import of external functionality from our own modules, angular, or 3rd parties.  
@angular/core   @angular/animate   @angular/http    @angular/router  

https://www.npmjs.com/~angular  for list of external angular modules.
e.g. import{Component} from 'angular/core';

app.component.ts   (first part is module name, second part is type of ES module, third part marks it as typescript.

Selector: `pm-app`  **NOTE BACKTICKS VERY IMPORTANT, NOT QUOTES !!!!** 

__Bootstrap__

Loads the root component.  index.html is the main page of an application (the only true web page) often called a SPA.  
Directive = Custom element e.g. <pm-app>

Bootstrap steps:
1. index.html has Systemjs.config which starts up application by importing 'app' (the 'app' ES module)
2. Systemjs.config.js then has app:{main : './main.js} which loads 'main' as the first entry module.
3. main.ts then bootstraps our first angular module,
4. Need app.module.ts set up with @NgModule decorator, which bootstraps a component.  


## Chapter 5 - Templates, Interpolation, and Directives (e.g. logic if and for statements)

__Templates__

Either inline templates using " " OR inline template over multiple lines using backticks ` `
**BUT LINKED TEMPLATES ARE MUCH BETTER ** Use TemplateUrl (relative to index.html folder) : 'productList.component.html'
[http://getbootstrap.com/](Twitter bootstrap link to get bootstrap project set up, css etc...)

**Use a component as a directive** = When a component has a selector, e.g. 'pm-products', then it can be used as a directive.  Can then use a components directive (e.g. html) in any other component ,e.g. <pm-products></pm-products>.  Angular looks to the **angular module** to see if the directive is defined in that angular module.

Component belongs to **1 and only 1** Angular module.  Ensure directive is visible to any component that uses it.  a) Can declare component in angular module  (b) If already declared in another module, then must import that module.  (e.g. see imports and declarations in aa.module.ts)


__Binding__

Coordinates communication between the component's class and its template and often involves processing data.  

One way is interpolation e.g. <h1>{{pageTitle}}</h1>   This is bound to export class AppComponent {pageTitle: String = 'Acme Products';}

Can also have concatenation calculation methods, e.g. {{2 * 20 + 1}}  or {{'Title:' + getTitle()}}   or assign to variable <h1 innerText = {{pageTitle}}> </h1>

Template --> **Display**   	Class (properties and methods)

Template <-- **Events**    	Class (properties and methods) 


__Directive__

Custom HTML element or attribute used to power up and extend our HTML.  Can be custom or built in.

Angular structured directives = *ngIf = If Logic

*ngFor = for loops  e.g. <table class = 'table' *ngIf='products && productsLnegth'>  <-- manipulates the DOM

Angular gets *ngIf and *ngFor from importing the BrowserModule.

typeScript has concept of any[] array for a data type we don't know about.  

<tr *ngFor = 'let product of products'> <td></td> <td>{{product.productName}}</td>

for...of (iterates over iterable objects such as array)

for...in (iterates over teh properties of an object) think of in(dex)


## Chapter 6 - Data Binding and Pipes

We want 2 way binding between Component and DOM.  This allows for elements to be displayed, and to get feedback from events on page.  Property binding allows element property to be bound to template expression.

<img[src] = 'product.imageUrl'>   **NOTE element property ALWAYS in [], template expression for binding source always in '' )

or could have <img src = {{product.imageUrl}}>

Very similar to property binding is **Event Binding** for receiving events from the form.  e.g. <button (click) = 'toggleImage()'>  (this will call a specified method in the component).

[For list of valid events](https://developer.mozilla.org/en-US/docs/web/Events) from Mozilla onClick etc.  Javascript has ternary operator {{showImage ? 'Hide' : 'Show'}} Image

Two way binding (for filter box for example on our application).  Do this using [] and () for property AND event binding.  **Banana in a box [()]**

<input[(ngModel)] = 'listFilter'>  this is a two way binding directive.

**IMPORTANT** in the module, use 'imports' for 3rd party imports.  Use 'declarations' for our own components.

__Transforming Data with Pipes__

Used to transform bound properties before display.  Built in pipes: date, number, decimal, percent, currency, json, slice etc..
Can have custom pipes which we build ourselves.  

Pipe examples:

1. {{product.productCode | lowercase }}
2.  Also can chain pipes {{product.price | currency | lowercase }}
3. Can accept parameters {{product.price | currency : 'USD' : true : '1.2-2}}   This will be to 2 decimal places.

In summary for binding there are 4 types
----------------------------------------
D     <---  Interpolation:{{pageTitle}}  ---------------------------  C

O	 <--Property Binding : <img[src] = 'product.imageUrl'>            O

M    ----- Event Binding: <button(click) = 'toggleImage()'>  --->     M

.    <---  Two way Binding <input [(ngModule)] = 'listFilter'/>       PONENT

The two way binding needs FormModule in appropriate module.  


## Chapter 7 - More on Components
                                                     
Benefits : Strong typing and Interfaces , Encapsulates styles, Lifecycle hooks, Custom Pipes, Relative paths with Module ID

Interfaces allow CUSTOM typing.  Interface = a **sepcification** identifying a related set of functionality.  

A class commits to supporting the specification by implementing the interface.   Can then use the interface as a data type.  

Interfaces are development time only (not found in javascript).  ONLY USED FOR STRONG TYPING.

An example ---  

			export interface IProduct {
					
                      product Id : number ;
					                                  
                      productName : String;
                      
                      CalculateDiscount(percent : number) : number : number ;    }
                      
To use, then import {IProduct} from '.IProduct'; products : IProduct[] = [...];  

Call interface file 'product.ts'.  Can also build out IProduct to have product class if we needed methods within that class.  

Encapsulating component styles.  Templates sometimes require unique styles.

Component decorator allows us to encapsulate styles.  Styles and StyleUrls.

@Component({
   
   styles : ['thead { color : #337AB7; }']})     **OR HAVE AN EXTERNAL STYLE SHEET**
   
@Component({
   
   styleUrls : ['app/products/product-list.component.css']})
   
THE STYLES ARE THEN ENCAPSULATED WITHIN THE COMPONENT

__Lifecycle Hooks__

Component has lifecycles managed by angular.

Create -> Render -> Create and Render Children -> Process changes --> Destroy

OnInit: Perform component initialisation, retrieve data (good for receiving data)

OnChanges : Perform action after change to input properties 

OnDestroy : Perform cleanup  

Implement the lifecylce hook OnInit interface e.g. implements OnInit { 

then have method such as ngOnInit() : void { console.log ('In OnInit'); }

__Transform Data with Pipes - can build customisabe pipes__

(see product-filter.pipe.ts) file.  It implements the PipeTransform interface and uses the @Pipe decorator.

This is used to filter the search String text.  

__Relative Path With Module ID__

To avoid referencing paths absolute from application root.

Can use relative path by using 'moduleId' within the @Component decorator.  

module.id is available when using the commonJS module format.

It contains the absolute URL of the component class module file.  

Just have to add module.id in component, angular takes care of the rest.  


## Chapter 8 - Building Nested Components - reusable components   
                                                                        
A component should only be Nest-able if its template only manages a fragment of a larger view.  It must have a selector / It optionally communicates with its container.

Pass data between a nested components using @Input and @Output

Nested components sit within the main component.  

__Input and Output Properties__ e.g. nested components for star rating.  Pass into nested component to display star rating, if user clicks on stars then pass out of nested component.  We therefore create a Star.Component. Put it in **shared** folder. Uses five stars, and crops stars based on width.

Use a nested component as a directive; <ai-star> </ai-star>

Use @Input decorator to decorate any properties in the nested components class.  Then set the value using property binding e.g. <ai-star [rating] = 'product.starRating'></ai-star>

@Output decorator used to pass information back out from Nested component to container component.  Within star.component.ts

@Output() notify : EventEmitter<String> = new EventEmitter<String>();

onClick {this.notify.emit('clicked!') : } etc...

Think of @Input and @Output decorators as the public API in the nested component.  Everything else is contained within the component and template and doesn't leak out.  


## Chapter 9 - Services and Dependency Injection (get rid of hard coded product details)

Service = a class with a focussed purpose (clear name, PascalCasing, append service to name)

Used for features that: are independent from any particular content , provide shared data or logic across components, encapsulate external interactions.

Product Data Service is therefore created in our example.  

Best to register service with angular, who creates a single instance of this service as a class (singleton).  Container of created service instances.  The Angular Injector manages these instances.  

Dependency Injection - passed into Component's constructor.  e.g. Constructor(private _myService){}.   All data is then shared with all services which use the data service.  

To build a service : a) create the service class   b) Define the metadata with a decorator  c) import what we need   e.g. look at product.service.ts

Use the @Injectable decorator for services for clarity.  

To register a service, we must register a 'provide' (code that can create or return a service) typically the service class itself.  

Define in a **component** (injectable to component and its children)  OR Angular module metadata (injectable everywhere in the application.

For our example, best to register service at **root-app** as it will needed by both product and productList components.  

providers:[ProductService]   <-- add this to components decorator in app.component.ts   Can register multiple services in this array if we want to.  

Once registered, use the components **constructor** for the dependency injection to use the service.  

pattern is this:     

private _productService;
  
  constructor(productService: ProductService){
  
  _productService = productService;}   
  
  There is a typescript shorthand for this:
  
  Constructor(private _productService : ProductService){ }
  
  ngOnInit lifecylce hook in product.list.component.ts is great place to call the service.  
  
  ngOnInit() : void {
    this.products = this._productService.getProducts();              


## Chapter 10 - Retrieving Data Using HTTP - Observables and Reactive Extensions

Observables and Reactive Extensions - help manage asynchronous data.  Treat events as collections (an array whose items arrive asynchronously over time)

Angular uses Reactive Extensions (RxJS) to achieve this.

Observable operators - Methods on observables that compose new observables.  Transform the source observable operators - methods on observables that compose new observables.  Transform the source observable in some way.  Process each value as it is emitted.  Examples : map, filter, take, merge.

[good to show marble diagrams](http://rxmarbles.com)

**Example of product.service.ts**
(Basically, see product.service.ts for a good example of using the @Injectable() decorator, and the Observable operators.)


Exception Handling **The Exception handling is quite involved, worth looking at Chapter 10 again**
------------------

See product.service.ts for examples of error handling for http request

The 'do' method allows us to peak at data without altering the flow of data.

Need to also **subscribe to an observable**  

x.subscripbe(valueFn, errorFn)   //Observable

x.subscribe(valueFn, errorFn, completeFn)   //Observable

So, any class which needs to subscribe to the product list, will do it like this (basically subscribing to the observable)

ngOninit():void{
  this.productService.getProducts()
  .subscribe(products => this.products = products,
  error => this.errorMessage = <any>error);
  
## Chapter 11 - Navigation an Routing Basics

Each view is configured in index.html file, taking it in turns.  Configure a route for each component.

Define options/actions.  Tie a route to each option/action

routerLink  HTML5 doesn't require # navigation

Routing is component based.  One router managed by angular router service.  

Register 'RouterModule' in app.module.ts in imports array.  

RouterModule.forRoot([]) sets up all the routers that we need.  **(array of routes, pass in our routes here !!! **
  
Configure routes = {path:'products',Component:ProductListComponent},

use parameters using 'product/:id' for example

**SEE CONFIGURING ROUTES SLIDE !!!! IMPORTANT!!!! match these up to app.module.ts**

In index html, need to set base tag <base href = "/">  

Tying routest to actions - can use option, link, image etc... Can type the URL in address bar/bookmark.  Can click forward or back buttons.  Angular will do this automatically.

Use routerLink to each 'a' tag in template within component.  

Need to use <router-outlet> to actually place a view.  Do this within the template.  Within component.  

**Checklist**

1) Nestable components -> Define a selector (provides name of directive)  Thus NO route, as component is nested in another.  

2) Routed components (designed for components which should be a view in our application).  No selector.  Configure routes (and tie these to actions).

Routing - configure routes. Tie routes to actions.  Place the view.  

Add RouterOutlet directive.  Identifies where to display the routed components view.  Specified in the host component's template.  

Add RouterLink directive as an attribute.  Clickable element.  Bind to a link parameters array.  

a) Define base element.

b) Add RouterModule (add each route to array using RouterModule.forRoot)

**order matters** Path:url segment for the route - no leading slash '' for default route   '*' for wildcard route


## Chapter 12 - Advanced Routing (pass parameters, routing through code, guards)

**Passing parameters** - use /:id   (parameter value in our route)

Within the routerLink, pass in the required parameter.  

Use snapshot **OR** observable to get parameter from URL  (observable good if need to scroll through different items on same page)

+ is shortcut in .js to convert string to numeric ID

**Active route with code** Use for example on a save button when need to save data, then route.  or to pre-load data to a route.   

Import the Router Service.  Define dependency on router service using a private constructor argument.  Router interface is therefore injected into class.

this._router.navigate(['/products']);

**Guards** - limiting access to routers (e.g. admin access, or asking user if they want to navigate away from page)

a) CanActivate (guard navigation to a route)

b) CanDeactivate (guard navigation from a route)

c) Resolve (pre-fetch data before activating a route)

d) CanLoad - prevent asynchronous routing 

(a) from above was covered in the course.  Do this in the usual way: define a class, add the decorator, import what we need (as a SERVICE)

Use the @Injectable service.  Implements CanActivate.

See ProductDetailGuard (i.e. product-guard-service.ts  to see an example of this, where we don't want invalid URLs

canActivate(): boolean     Register in app.module.ts

Add the canActivate() method within the RouterModule.forRoot() of where the routings are defined.

Use ActivatedRouteSnapshot to get data from URL at that point in time.  

Always need to Register the guard service provider.  **MUST BE REGISTERED IN ANGULAR MODULE, NOT A COMPONENT.  THIS IS BECAUSE IT NEEDS ROUTING OVERARCHING DETAIL ** 

**Remember html *ngIf trick at top of template to delay page load if getting binding errors when page loads before data is bound.  See example in product-detail.component.html  

*ngIf = 'product' (makes sure product is loaded before page loads)


## Chapter 13 - Angular Modules
	
Module is a class with an NgModule decorator.

It organizes the application into blocks / External capabilities from external libraries / Aggregate and re-export e.g. HttpModule, RouterModule

Module declares components/directives/pipes.  Bootstraps our initial component.  

Exports modules, components and pipes, meaning they are available for other modules to use.  

Imports modules too.  Can register services.  Think of it as a **BOX**

Importing a module brings in functionality exported by that module.  

app.module.ts   <-- Root module, by convention called app.module 


** Bootstrap Array Truths **
1. Every application must bootstrap at least one component, the root application component.
2. The bootstrap array should only be used in the root application module, AppModule (i.e not in any other modules)

** Declarations Array Truths (use the declarations array to define components, directives)  **
1. Every component, directive and pipe we create must belong to one and only one module.
2. Only  declare components, directives and pipes (NOT classes, services or other modules)
3. Never re-declare components, directives or pipes that belong to antoher module.
4. All declared components, directives and pipes are private by default.  They are only accessible to other components, directives and pipes declared in the same module.  
5. The Angular module provides the template resolution environment for its component templates.  

** Exports Array Truths (allows components, directives and pipes to be shared with other modules.  Can also rexport @angular modules and 3rd party modules, and our own modules ) **
1. Export any component, directive, or pipe if another component needs it
2. Re-export modules to re-export their components, directives and pipes
3. We can re-export something without importing it first
4. Never export a service (these should be put in services array at root module so they cna be injected anywhere in application)

** Imports Array Truths (extend capabilities from other angular modules.  Import modules which give us components, directives and pipes e.g. FormsModule, HttpModule, 3rd party modules **
1. Importing a module makes available any exported components, directives and pipes from that module.
2. Only import what this module needs.
3. Importing a module does not provide access to its imported modules. (i.e imports are **NOT** inherited

**THINK OF A MODULE AS A BOX NOT A TREE STRUCTURE **

** Providers Array Truths (register services at the module level (such as ProductDetailGuard) **
1. Any service provider added to the providers array is registered at the **root** of the application and is available to any class.  
So... need to be careful here.  If added to a module declarations array, then it will be accessible to **all** classes in the application.    If want it to only be in the component (or set of components) define it in the **components providers array**
2. Don't add services to the providers array of a shared module .  There should only be **one** instance of a singleton service.  Consider building a CoreModule for services and importing it once in the AppModule.  This will help ensure the services will only be registered once in AppModule.  
3. Routing Guards must be added to the providers array of an Angular Module.  

** Feature Modules (separation of concerns e.g. ProductModule, adding the ProductList and ProductDetailComponents**
1. BrowserModule should only be pulled into root application.  moduleOnly (appModule).  Import CommonModule - this exposes ngFor and ngIf

We define ProductService and Product Detail Guard within the ProductModule to keep the code consistent, even though the services will be available to all of the application.  

We then import the ProductModule into the AppModule in the import array:  

forRoot  (rooting in app module (or refactored module, BUT USE ONLY ONCE !!)

forChild (rooting in feature module)

**Shared Modules (Organise set of commonly used pieces into one module, and export those pieces so that they can be imported into any module that needs it.  Selectively aggregate shared pieces, e.g. star component**

**AppModule - used to orchestrate the application as a whole**
Needs BrowserModule as an import and HTTPModule.  Also import router module, and configure the roots for the application - configure the roots and the wildcards.
Also, import the productModule.  Declarations declare the components which are declared in the app module.  Also declares the bootstrap array [AppComponent] - when application loads it launches this bootstrapped AppComponent.  

We could also refactor the application routing module.  

CoreModules --> set of services which need to be loaded when app is loaded.  Be sure this is loaded ONLY once in core application module.  

** EXCELLENT DIAGRAM IN THIS PROJECT, ANGULAR MODULE LAYOUT.png  and Angular MODULE LAYOUT 2 ,  SUMS UP MODULE LAYOUT WELL!!!! **

## Chapter 14 - Setup Revisited 
**tsconfig.json typescript compiler config file**  Presence of this file indicates the root of the application.

"target":"es5"  Map files help with debugging 

d.ts  = typescript definition file

typings.json = has global dependencies (for libraries that don't provide a type definition file )

**package.json** (insight into npm packaging)

application name, description, author, etc   scripts/dependencies/devdependencies  are the 3 key parts to the file.

dependencies = libraries the application needs to run  --> twitter bootstrap, rxjs, etc...

devDependencies = additional for development   typescript/typings/lite-server etc...

npm install uses the dependencies and gets all the libraries it needs.

npm start will compile AND start the lite-server

System.config.js --> configures the system.js (an es file loader, that automatically loads the files for our application which means we don't need script tags for every file in our application).

paths: defines alias where system files are located.

app: Defines where all angular bundles are located.

packages: defines which class to bootstrap first (main.js) in our example.

**index.html** -> script tages load some important libraries

shim.min.js is for core .js  (es2015 capabilities)

zone.js for data binding

reflect.js --> for reading decorator metadata

**bootstrap process** --> main.ts  file bootstraps the application  using dynamic bootstrapping and JIT compiler  (could use AOT ahead of time compiler) for mobile devices.

Angular CLI --> a command line interface for Angular

ng new APM (Creates a working Angular application with all required starter files)

ng g Component product-list  = creates new component to product-list  AND MUCH MORE  - unit and end to end tests see [this link](https://cli.angular.io/) 

Also, components, pipes, directives, services.  