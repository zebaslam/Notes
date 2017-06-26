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
  * on submit (ngSubmit) we get the values (key/value pairs) of the form group and pass it to a function onSubmit defined in our component class
