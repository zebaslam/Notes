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
		* In this example, we're iterating a list of names and passing the reference value (here called name but could easily be called something else) to the child component
