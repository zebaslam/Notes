# Built in Directives

## ng-if
* The same as angular 1.x ng-if
* Examples:
  * `<div *ngIf="a > b"></div>` Would display dif if a > b
  * `<div *ngIf="myFunc()"></div>` Would display div if myFunc() is true
  
## ng-switch
* Switch case statements for evaluating a single statement
* ```<div [ngSwitch]="myVar"> <div *ngSwitchCase="'A'"> var is A</div> <div *ngSwitchCase="'B'"> var is B </div> <div *ngSwitchDefault> var is something else</div> </div>```

## ngClass
* ngClass allows you to dynamically set and change the CSS for a dom element. 
* `<div [ngClass]="{bordered: isBordered}"> Using object literal. {{ isBordered ? "ON" : "OFF" }} </div>`
  * You define isBordered ina component file as an instance variable and toggle it etc.

## ngFor
* Syntax: `*ngFor="let item of items"`
 * item is a template variable receiving each element of the items array
 * The items is the collection of items from your controller 
* Getting an index
 * Ex: `<div class="ui list" *ngFor="let c of cities; let num = index"> <div class="item"> {{ num +1 }} - {{ c }} </div></div>`
 
## ngNonBindable 
* `<span class="pre" ngNonBindable> This is what {{ content }} rendered. </span>`
* This displays the above line exactly as written because angular wont compile or bind the content
