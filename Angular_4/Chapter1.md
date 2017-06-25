# Chapter 1

## Getting Started 

* `app-root` is  an angular component 

  * Entry point for our applications

* `ng serve` will run the web app

* Angular 4 is meant to be used with TypeScript (.ts)
   * The `ng serve` command will convert ts to js
* ES6 allows for multiline strings using backticks 

## Components
* The purpose of a component is to teach the browser new html tags with their own custom functionality
* components ` ===` directives
* Components have two parts
  * 1. A `Component` decorator
  * 2. A component definition class
* An import statement defines modules we want to write in our code
  * * Imports are similar to java or ruby imports
  * * A common dependency is `Component` which is from the `@angular/core` module..
* `@Component({//...})` refers to a decorator in typescript
  * * Represent code's metadata
  * * Essentially, we're decorating a class as a Component
* The selector field of the Component represents the html tag we want the component to represent
* Angular uses style-encapsulation to have styling apply only to that component
* Curly brackets `{{ }}` imply template tags with data interpolation happening behind the scenes
* In our component class we declare fields with a type
  * example: `names: string[];` implies a string array of names
* To iterate over an array of items we use the `*ngFor` with a let clause
   * `let name of names` gets a reference to a variable name which represents a single element of our names array which is declared in our Component object.

## Accepting Inputs
* Using the `@Input()` annotation allows us to accept a value for a property from a parent template in a child template.
  * To use this we need to import the Input module from angular/core
* To pass values to a component from html, we use bracket `[]` syntax in our template
  * ex: `<ul><li *ngFor="let name of names"> <app-user-item [name]="name"> </app-user-item></li> </ul>`
    * In this example, we're iterating a list of names and passing the reference value (here called name but could easily be called something else) to the child component's input named `name`

## An aside on Angular-CLI
* Angular cli is built on top of WebPack and allows us to serve our components via `ng serve`
* Angular cli uses the `ng` commands to find and create components
  * The file .angular-cli.json specifies a main file which is the entry point for our app and bootstraps the application
  * The bootstrap process boots an Angular module 
  * An AppModule is used to bootstrap the app. AppModule is generally specified in `src/app/app.module.ts`
    * This file also specifies which component is the top-level component (ex: AppComponent)
    * AppComponent has your custom tags in the template and renders them
    * `@NgModule` adds metadata to the class immdediately following it and has several keys
    * declarations: specify the components defined in this module
      * Components must be declared in NgModule before you can use them in your templates
      * `ng generate` from angular cli will automatically add new components to NgModule
    * imports: describe module dependencies that are added via dependency injection.
      * import: imports a class at the top of a file
    * providers: Used in dependency injection so it can be used throughout our application.
    * bootstrap: tells Angular to load AppComponent as the top-level component

### String Interpolation
* Angular allows string interpolation through the `$value` symbols

  ​

## Events, functions and template variables

`<button (click)="addArticle(newtitle, newlink)" class="ui positive right floated button"> Submit link </button>`
* In the above source code we can see that our html template is calling a function addArticle on a click event to our button and passing in the vales newtitle and newclick.
  * newtitle and newlink are template variables and use this syntax in an input element `#newtitle` 
  * This assigns these tags to a local variable that can be passed to our function.
  * `#newtitle` is also called a resolve
    * it makes this variable available to the expressions within this view
    * Its represented as an object (whos value is gotten from newtitle.value) of type HTMLInputElement
  * the click event handler propagates the click event to all parent components
    * to prevent this have your function return false (telling JS to not propagate to a parent component)

## Models

* In angular its good practice to seperate the models from the views and controllers. 
  * That is, we isolate the data structures we are using from the component code
  * The model should be a typescript class that is then imported into the component and removes the use of any isolated fields
    * Then, we can instantiate this as a new class with values in our component
    * We also declare a field with the type of the class ex( article: Article) and refer to this in both our component and our view

