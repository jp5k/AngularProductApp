# AngularProductApp

Angular Product Application from Pluralsight - good first Angular 2 project



## Corporate Proxy Issue When Running Project At Work
To get round corporate proxy, create a .typingsrc file in the root with the following config:

proxy="http://webfilter.ecclesiastical.com:80"

rejectUnauthorized="false"

##Chapter 2 - Getting Started

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


##Chapter 3 - First Things First 

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

An example --- export interface IProduct {
					
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
  












