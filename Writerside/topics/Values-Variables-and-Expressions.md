# Values, Variables, and Expressions
<show-structure for="chapter,procedure" depth="2"/>

Now that you have seen the ways to filter down to the data you want to patch, and even the exact actions to do what you
want to modify something, you may be wondering how to describe the ways you want to modify the data. This is where 
Values, Variables, and Expressions come in, these are the ways to express, store, and manipulate data within Patch Manager.

## Values
Values are the most basic way to express data in Patch Manager, of which, there are a few basic types of them.

### Null Values (type: none)
This type of value is best described as a lack of data, and there is only one value under this type: `null`.

### Boolean Values (type: bool)
This type of value holds yes/no answers, whether something is the case or not, etc..., there are exactly 2 values of
this type:

true
: Represents a boolean value that is similar to "yes", or "that is the case"

false
: Represents a boolean value that is the opposite of `true`, meaning "no", or "that is not the case"

### Integer Values (type: integer)
This type is the representation of mathematical integers (positive or negative numbers, without decimal points).
Values of this type are usually written out as base 10 numbers, though they can also be written in base 16 with a `0x`
prefix. Here are a few examples of integer values:

```
0
-1
5
32
0xFF31 (this is a hexadecimal/base 16 number)
-0xF3
```

### Floating Point Values (type: real)
This type is the closest representation to the mathematical concept of a real number (positive/negative, with decimal points).
Values of this type are written out as base 10 numbers (with decimal points always). A few examples of floating point
values are as follows:

```
0.0
1.
1.5
-3.2
5.9999999999993
4.124
```

### String Values (type: string)
This type of value represents sequences of characters, usually forming words or similar constructs, but not necessarily.
They are represented as a sequence of characters enclosed by single (`'`) or double (`"`) quotes.
A few examples are as follows:
```
"Hello, World"
"12334"
'Pi = 3.14159'
"eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee"
' '
""
"\n"
```

#### String Escape Sequences { collapsible="true" default-state="expanded"}
Sometimes though, you may want to represent characters in your strings that you can't represent normally, such as nested
quotes, or a line break, or certain unicode characters, this is where "escape sequences" come in, these are sequences
started by a `\\` that are used to represent an entirely separate character.

| Escape Sequence | Replaced By                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------|
| `\\\\`          | `\\`                                                                                                   |
| `\\'`           | `'`                                                                                                    |
| `\\"`           | `"`                                                                                                    |
| `\\n`           | A newline (ASCII `0x0A`)                                                                               |
| `\\r`           | A carriage return (ASCII `0x0D`)                                                                       |
| `\\f`           | A form feed (ASCII `0x0C`)                                                                             |
| `\\t`           | A horizontal tab character (ASCII `0x09`)                                                              |
| `\\v`           | A vertical tab character (ASCII `0x0B`)                                                                |
| `\\a`           | An alert character (ASCII `0x07`)                                                                      |
| `\\0`           | Unicode character number `0`                                                                           |
| `\\uxxxxx`      | Unicode character `xxxx` where `xxxx` is a hexadecimal value                                           |
| `\\xn[n][n][n]` | Unicode character `nnnn` where `nnnn` is a hexadecimal value (variable length version of the previous) |
| `\\Uxxxxxxxx`   | Unicode character `xxxxxxxx`                                                                           |


### List Values (type: list)
This type of value represents a sequence of values, it is represented by a `,` separated list of values (of any type)
surrounded by `[` and `]`. A few examples are as follows:
```
[1,2,3,4,5,6,7]
[]
["A",5,3.9,true]
[[1,2,3],4,5,6,]
```
As you can see, nested lists are allowed, and so are trailing commas.

### Map Values (type: dictionary)
This type of value represents a relation of keys to values, the keys are strings that are optionally enclosed in quotes,
it is represented by a `,` separated list of `key: value` or `"key": value` pairs surrounded by `{` and `}`. A few
examples are as follows:
```
{}
{
    name: "Bob",
    age: 15,
    pronouns: "It/Its",
    relationships: [
        {
            "Name": "Jimmy",
            "Relation": "Brother",
        },
        {
            "Name": "Johnny",
            "Relation": "Father",
        }
    ]
    favorite-food: "Pizza",
    is-alive: true
}
{
    red: 0xff0000,
    green: 0x00ff00,
    blue: 0x0000ff
}
```
As you can see, nested dictionaries are allowed, and so are trailing commas.

### Deletion Values (type: deletion)
This is a special type of value, represented by `@delete` that when assigned to anything, deletes the thing it is being
assigned to.

### Other Types

There is actually one more value type that is considerably more advanced called a `closure` explained within the
[Functions and Closures](Functions.md) page.

### Truthiness
Even though there is a specific `bool` type that already exists, every value has a measure called truthiness, which
describes how close to acting as a `true` boolean value it is, if a value is acting as such it is called truthy, 
otherwise it is called falsy or not truthy. The following table describes the criteria for truthiness for each type of value

| Value Type   | Criteria for Truthiness                |
|--------------|----------------------------------------|
| `none`       | Values of this type are always falsy   |
| `bool`       | `true` is truthy, `false` is falsy     |
| `integer`    | Values of this type are always truthy  |
| `real`       | Values of this type are always truthy  |
| `string`     | Values of this type are always truthy  |
| `list`       | Values of this type are always truthy  |
| `dictionary` | Values of this type are always truthy  |
| `deletion`   | Values of this type are always falsy   |


## Variables

Variables are the primary way to store data outside of objects, and access preexisting data as is the case with implicit
variables. They are usually represented by identifiers prefixed by either `$` or `$$`, examples being `$my-value` or 
`$$communicationRange`. There are 2 types of variables, implicit variables, which are the aforementioned preexisting data,
and user defined variables, which are variables defined to store stuff.

### Implicit Variables
Implicit variables are variables that are implicitly defined in certain contexts, and may or may not exist.

#### $current
This variable holds the value representation of the current object you are editing with your selection block.
Note: if you are editing multiple objects, each objects edit technically runs individually therefore it is a singular
object

#### $parent
This variable holds the value representation of the parent of the current object you are editing with your selection block.

#### $value
This variable is defined only when doing field editing, and it is defined as the current value of the field you are editing.
Useful for stuff like scaling the fields value by a number or similar.

#### $$... (object local variables)
This isn't a single variable, but a set of variables of the form `$$field-name` that is defined as the current value of
the field named `field-name` in the current object.
To better explain it, here are a few example usages
```
:part #wheel_0v_rover {
    $x: $$mass; // $x is set to the value of the mass field of the wheel
    $y: $$crewCapacity; //$y is set to the value of the crewCapacity field of the wheel (should be zero lol)
}
```

### User Defined Variables
User defined variables are variables usually defined as such `$identifier: [expression];`, where they can later be
referred to by `$identifier`. And now is a perfect time to go over the rules for identifiers. Identifiers are a sequence
of characters that can start with `a-z`, `A-Z`, and `_`, and then can be followed by those characters and also `0-9`, `.`
and `-`. So `_xyz-0-1-23.4` is a valid identifier but `9rt-g` is not.

## Expressions
Now that you have learned how to express and store/access data, the last thing you need to learn is how to modify data
and combine it with other pieces of data. The way to do this, is expressions, which are essentially a sequence of operations
that can be done on data, like the mathematical concept of an expression. The individual components that describe the
actions being done are called operators, and the expressions being used with these operators are called operands.

### Foreword: Prefix Expressions { collapsible="true" default-state="expanded" }
A foreword before going into expressions, certain operators (i.e. `+`, `-`, `*`, and `/`) that are typically binary, can
be used without a left hand expression if they are the leftmost operator in a field-setting selection action, in this 
case, they are treated as the left hand expression being `$value`, which allows for easy expression of simple actions
such as scaling a value and what not.
An example of this usage is
```
:parts #wheel_0v_rover {
    mass: *5;
}
```
where the `*` is a prefix operator, and this means multiply the mass by 5, as `$value` is equal to the current value of
the mass. If you are familiar with other programming languages, this is basically how to represent `+=`, `-=`, `*=`, and
`/=` for fields.

But as for the reason that this is in the foreword, and this is important, is that if you want to set a field to a value
that is a negative number, **ALWAYS** wrap it in `()` like as follows

```
:parts #wheel_0v_rover {
    mass: (-5);
}
```

> If you do not wrap your negative values in parentheses, it will be treated like a prefixed subtraction operation
> 
{style="warning"}

### Values and Variables as expressions
With the foreword out of the way, the simplest type of expression has already been described, values and variable
references.

```
$result: 5; // A value of 5 as an expression
$result-a: $result; // Using the variable $result as an expression
```

### Unary Prefix Operators
There are 3 unary prefix expressions: `not`, `+`, and `-`, a unary prefix operator means that the operator is placed directly
to the left of the expression that it is being operated upon, example being `-$something`

#### +
This operator actually is the equivalent of doing nothing, it multiplies its operand by `+1`
Example:
```
$result-c: +$result-b; // Essentially sets $result-c to $result-b (5)
```

#### -
This operator multiplies its operand by `-1`
Example:
```
$result-d: -$result-c; // Sets $result-d to $result-b multiplied by -1 (-5)
```

#### not
This operator returns `false` if its operand resolves to a value being <tooltip term="truthy">truthy</tooltip>,
otherwise it returns `true`.

Example:
```
$result-e: not true; // Set to false as true is truthy
$result-f: not $result-e; // Set to true as $result-e being false is not truthy 
```

### Binary Numeric Operators

Binary numeric operators, are operators that usually (but not always) operate on numbers, and are placed as an infix 
between the 2 expressions making up their operand

#### +
This operator results in the value of its 2 operands added together, when used on operands that are numbers 
(`integer`/`real`), and if either operand is a `real` it will return a `real` otherwise it returns an `integer`
```
$a: 5;
$b: $a+5; // Results in 10, as 5+5 is 10
```
This operator can also have different results depending on the other operands it has.
These results are defined in the following sections, any combination not described will throw an error.
##### string + string
If the operands to `+` are strings, then this will concatenate the 2 strings, that is put them together end to end creating
a new string.
```
$a: "Hello";
$b: "World";
$c: $a+$b; // Becomes "HelloWorld"
```

##### list + list
If the operands to `+` are lists, then this will append all values of the righthand list to the lefthand list creating
a new list.
```
$a: [1,2,3];
$b: [7,8,9];
$c: $a+$b; // Becomes [1,2,3,7,8,9]
```

#### -
This operator results in the value of its right hand operand subtracted from the value of its left hand operand, when used on 
operands that are numbers (`integer`/`real`), and if either operand is a `real` it will return a `real` otherwise it 
returns an `integer`.
```
$a: 10;
$b: $a-11; // Becomes -1 as 10 - 11 is -1
```
When used on any other data types, it will throw an error.

#### *
This operator results in the value of its 2 operands multiplied, when used on
operands that are numbers (`integer`/`real`), and if either operand is a `real` it will return a `real` otherwise it
returns an `integer`.
```
$a: 10;
$b: $a * 10; // Becomes 100 as 10 * 10 is 100
```
This operator can also have different results depending on the other operands it has.
These results are defined in the following sections, any combination not described will throw an error.

##### string * integer and integer * string
When you use the `*` operator to multiply a string and an integer or vice versa, the result is the string repeated by
an amount that is the value of the integer.
```
$a: "hi";
$b: "hi"*3; // "hihihi"
```

##### list * integer and integer * list
Similar to the above, the result of multiplying a string and a list is the list repeated by an amount that is the value
of the integer.
```
$a: [1];
$b: $a*10; // [1,1,1,1,1,1,1,1,1,1]
```

#### /
This operator results in the value of its left hand operand divided by the value of its right hand operand, when used on
operands that are numbers (`integer`/`real`), and if either operand is a `real` it will return a `real` otherwise it
returns an `integer`.
```
$a: 10;
$b: $a/2; // Becomes 5 as 10 / 2 is 5
```
When used on any other data types, it will throw an error.
#### %
This operator results in the the remainder of the division of the value of its left hand by the value of its right hand 
operand when used on operands that are numbers (`integer`/`real`), and if either operand is a `real` it will return a 
`real` otherwise it returns an `integer`.
```
$a: 10;
$b: $a%3; // Becomes 1 as the remainder of 10/3 is 1
```
When used on any other data types, it will throw an error.

### Binary Equality Operators

### Binary Relational Operators

### Binary Boolean Operators

### Subscript Operator

### Ternary Operator

### Other Operators

There are a few other operators not described here that are described within the [Functions and Closures](Functions.md) 
page.

### Combining Expressions

## What next