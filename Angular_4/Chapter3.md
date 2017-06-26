# Built in Directives

## ng-if
* The same as angular 1.x ng-if
* Examples:
  * `<div *ngIf="a > b"></div>` Would display dif if a > b
  * `<div *ngIf="myFunc()"></div>` Would display div if myFunc() is true
  
## ng-switch
* Switch case statements for evaluating a single statement
* ```<div [ngSwitch]="myVar"> <div *ngSwitchCase="'A'"> var is A</div> <div *ngSwitchCase="'B'"> var is B </div> <div *ngSwitchDefault> var is something else</div> </div>```

##ngClass
* ngClass allows you to dynamically set and change the CSS for a dom element. 
* `<div [ngClass]="{bordered: isBordered}"> Using object literal. {{ isBordered ? "ON" : "OFF" }} </div>`
  * You define isBordered ina component file as an instance variable and toggle it etc.
