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


































