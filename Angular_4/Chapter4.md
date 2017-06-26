# Forms in Angular
**FormControls**: Encapsulate the inputs in our forms and give us objects to work with them

**Validators**: Give us the ability to validate inputs, any way we'd like

**Observers**: Let us watch our form for changes and respond accordingly 

## FormControlS and FormGroupS
### FormControl
* FormControl represents a single input field- it is the smallest unit of an Angular form.
* FormControls encapsulate the field's value, and states such as being valid, dirty (changed) or has errors.
  * You can query a form control for errors, dirty and if the control is valid.
* FormGroup is a collection of FormControls that are also queryable and is used in the typical multi-field form. 

## FormModule
* FormsModule gives us template driven directives such as 
  * ngModel
  * NgForm
* ReactiveFormModule gives us directives like
  * formControl
  * ngFormGroup
### ngForm
* ngForm does something non-obvious, that is, it automatically attaches to to any form tags if the FormsModule is imported. This is useful but confusing.
* ngForm provides the following functionality:
  * A FormGroup named ngForm
  * An (ngSubmit) output
* Ex: `<form #f="ngForm" (ngSubmit)="onSubmit(f.value)">`
  * In english: When I submit thus
  * The `#v=thing` syntax says we want to create a local variable for this view.
  * In the above example, we create a variable #f which represents an alias to ngForm which comes from the ngForm directive (auto attached to form tag)
  * ngForm has type FormGroup which means f is of type FormGroup.
  * on submit (ngSubmit) we get the values (key/value pairs) of the form group and pass it to a function `onSubmit` defined in our component class

### input and NgModel
An example form: 
```
<div>
  <h2>Demo Form: Sku</h2>
  <form #f="ngForm"
        (ngSubmit)="onSubmit(f.value)">

    <div class="field">
      <label for="skuInput">SKU</label>
      <input type="text"
             id="skuInput"
             placeholder="SKU"
             name="sku" ngModel>
    </div>

    <button type="submit">Submit</button>
  </form>
</div>
```
* Above we used `ngModel` with no attribute value. We created a *one way binding* and created a FormControl on this form with the name sku (this is from the name attribute from the input tag). 
* NgModel creates a new FormControl that is automatically added to the parent FormGroup and then binds the DOM element to the new FormControl. Essentially, it creates an association between the input tag and the FormControl by a name (in this case "sku").

### Aside: ngModel vs NgModel
* PascalCase like NgModel implies we're specifying the class and referring to the object as its defined in code. 
* CamelCase like ngModel comes from the selector of the directive and is only used in the DOM/template

## FormBuilder
FormBuilder helps us build forms by making FormControls and FormGroups. 
```
import { Component, OnInit } from '@angular/core';
import {
  FormBuilder,
  FormGroup
} from '@angular/forms';

@Component({
  selector: 'app-demo-form-sku-with-builder',
  templateUrl: './demo-form-sku-with-builder.component.html',
  styles: []
})
export class DemoFormSkuWithBuilderComponent implements OnInit {
  myForm: FormGroup;

  constructor(fb: FormBuilder) {
    this.myForm = fb.group({
      'sku': ['ABC123']
    });
  }

  ngOnInit() {
  }

  onSubmit(value: string): void {
    console.log('you submitted value: ', value);
  }

}
```
* We first inject FormBuilder as an import 
* myForm is an instance variable typed to be a FormGroup
* The constructor of the component will create an instance of FormBuilder and assign it to the fb variable.
  * control - creates a new FormControl
  * group- creates a new FormGroup
    * fb.group(...) takes a key value object (in our case we have one key (sku) and a default value for this key of ABC123).
* This will change our view to:
```  
<form [formGroup]="myForm"
        (ngSubmit)="onSubmit(myForm.value)"
        class="ui form">

    <div class="field">
      <label for="skuInput">SKU</label>
      <input type="text"
             id="skuInput"
             placeholder="SKU"
             [formControl]="myForm.controls['sku']">
    </div>

  <button type="submit" class="ui button">Submit</button>
  </form>
```
* In the above snippet, were telling Angular we want to use myForm as the FormGroup for this form. 
 * Note: NgForm wont be applied to a form that has formGroup
* The above snippet also binds the formControl directive to specify that we want to look at myForm.controls and use the existing sky FormControl for this input.
