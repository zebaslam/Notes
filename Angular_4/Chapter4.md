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
