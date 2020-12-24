# Ruby Cheat Sheet

## Symbols (`:symbol`)
- Symbols are immutable objects (but **not** immutable strings)
- Are a more efficient way of working with strings as they occoupy less memory and exist only once throughout program

### When to use Symbols vs Strings?
- If contents of string is relevant, use string
- If identity of string is important, use symbol
- A new string is a new object but a symbol exists only once per program
- Note: symbols stay in the program until it exits and thus can consume a lot of memory that cant be freed until program exits

### Symbols and Interpolation
The `to_s` method is implicitly called on interpolated symbols
```
symbol = :cats
string = "It is raining #{symbol} and dogs."
# results in 'It is raining cats and dogs.'
```

## Strings
### Shovel Operator (`<<`) vs `+=` for Strings
Shovel operator uses in place modification (it is an alias of concat) and the plus equals operator will create a new string. 
In place operation is about 1.5 times faster than the plus equals operator.

## Iteration
### `&` Syntax
`&` is used to iterate over each element in a collection typically with the `map` method.
* `['a', 'b'].map(&:capitalize)` capitalizes each element in the array

## Classes and Objects
Class names are often nouns.

### Instance Variables
Instance variables are always of the format `@variable`

### Getters and Setters
* Use `attr_reader` to create getter methods
* Use `attr_writer` to create setter methods.
* Use `attr_accessor` to create both setters and getters for an instance variable.

Format would be: `attr_reader :x, :y, :z`

### Inheritance
The following shows that Magazine is a subclass of Publication: `class Magazine < Publication`. `<` is the inherits symbol.

## Modules
Modules are bundles of methods and constants that can be `include`d in a class but cannot be instantiated.
They use the `module` keyword.
Module names are often adjectives.
