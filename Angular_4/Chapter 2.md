# Chapter 2: How Angular Works

## Application 

* Components are equivalent to directives from Angular JS
* An application in angular is nothing but a tree of components
* The topmost component is the application component
* Components are composable; that is, we can build larger components from smaller ones
  * Additionally, Components are rendered in a parent/child format and rendered recursively

## Inputs and Outputs

* `<products-list [productList]="products" (onProductSelected)="productWasSelected($event)"></products-list>`
  * The [square brackets] pass inputs 
  * (parentheses) handle outputs.
    * Inputs flow into your component via input bindings and events flow out of your component through output bindings. 
  * `(onProductSelected)` represents the onProductSelected output from the ProductsList component  we want to listen on
  * `productWasSelected` is the function we want to call when something new is sent to this output
  * `$event` is a special variable that represents the thing emitted on (sent to) the output
* `@Component ({selector: 'my-component'}) class MyComponent {@Input ('shortName') name: String; @Input('oldAge') age: number;}`
  * **Property name** (name, age) represents how the incoming property will be visible in the controller
  * The @Input argument (shortName, oldAge) configures how the property is visible to the 
    outside world
* The output syntax follows the format of `(output)="action"`
* **EventEmitter**: An object that implements the Observer pattern, it will maintain a list of subscribers and publish events to them.
  * ``` let ee= new EventEmitter(); ee.subscribe((name: string) => console.log(`Hello ${name}`)); ee.emit("Nate");```