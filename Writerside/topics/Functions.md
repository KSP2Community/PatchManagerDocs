# Functions and Closures
<show-structure for="chapter,procedure" depth="2"/>

Functions and closures are both ways of defining sequences of expressions for later use, and/or encapsulating your expressions.


## Function Declarations
Functions are declared as a top level statement using `@func [identifier](parameter-list) {...}` where in the `...` is
a list of function level statements. The parameter list is a ',' separated list of parameters of the form `$parameter-name` or
`$parameter-name:[expression]` where the expression describes the default value for that parameter.

Functions have access to every top level variable declared/imported before the function declaration inside their body,
and they have access to every function defined even after their declaration, as long as that definition is reached by
the time of the function call.

A few example function declarations are as follows:

```
@func parameterless() {
}

@func add($a,$b) {
    @return $a+$b;
}

@func create-map($a,$b:$a,$c:$a) {
    @return {
        a: $a,
        b: $b,
        c: $c
    };
}
```

> The default values for function parameters can depend on previous parameters, as when computing the value of parameters
> the computation is done from left to right.
>
{style="note"}

### Declaring "Member" functions

Sometimes you may want to overload functions depending on the type of the first argument when called like a member function
(described below), or you may want the function to only be used with that type when used like a member function, in that
case you can define your functions with the name prefixed by the "type" of argument you want the first argument to be, or
to overload based on. These types are defined in [Values, Variables, and Exceptions](Values-Variables-and-Expressions.md),
where they are in parentheses in the headers of the different types of Values.

A few example of member functions is as follows

```
@func integer.successor($int) {
    @return $int+1;
}

@func real.successor($real) {
    @return $real+1.0;
}

@func list.max($list) {
    $max: null;
    @each $value in $list {
        @if max {
            $max: $max @if $max > $value @else $value;
        } @else {
            $max: $value;
        }
    }
    @return $max;
}
```

## Invoking Functions

To invoke a function in an expression, it is quite simple, you put the function name you want to invoke, then a `(`, a 
comma separated list of expressions for the parameters (parameters can also be named, by doing `$parameter-name:expression`), and 
a `)`. This when computed will pass the parameters into the function, and run it, and it will evaluate to the result of
the function you wanted to call.

A few examples of this are as follows:

```
$test-a: parameterless(); // Returns null due to the implicit declaration
$test-b: add(1,2); // Adds 1 and 2 together using only positional parameters
$test-c: add(1,$b:2); // Adds 1 and 2 together, uses a named parameter for the second paramter
$test-d: create-map(5); // Returns {a:5,b:5,c:5}, due to default arguments
$test-e: create-map($c:1,$b:2,$a:3); 
```

### Invoking "Member" Functions

To invoke a "member" function, you do `[expression]:[function-name]([arguments])`, which computes the expression, and gets
the type of the resulting value for checking which function it needs to call, as first it checks for a function named
`[type].[function-name]` and if that exists, it will use that function, otherwise it will use the default function named
`[function-name]`. And once this function is found, it will be invoked, with the leftmost argument being the result of
the computation of the expression, and the other arguments passed to the right of that.

A few examples of invoking the previous declared functions as member functions are as follows:

```
$test-a: 5:successor(); // Should be 6, calls integer.successor
$test-b: 5.0:successor(); // Should be 6.0, calls real.successor
$test-c: [1,2,3]:max(); // Should be 3, calls list.max
$test-d: 5:add(2); // Should be 7, calls add
```

## Closure Declarations

A closure is an anonymous function who is a child of the environment that it is in (i.e.) it has access to all the
variables in the environment it was declared in that were declared before its declaration. They are declared much like
functions, but instead have no names, and are not at the top level, but rather values inside of expressions.

A few examples of closure declarations are as follows:

```
$list-first: @func($list) {
    @return $list[0];
}

$max: @func($a,$b:0) {
    @return $a @if $a > $b @else $b;
}
```

> The "type" of closures for member function declarations is `closure`
> 
{style="note"}

## Invoking Closures

To invoke closures you must have the `builtin:functional` library imported, which defines a member function called
`closure.invoke`, which when called with a closure and the closures arguments (named or positional are allowed), invokes
the closure with the list of arguments passed, and returns the result.

Examples of this, invoking the previously defined closures above are as follows:
```
@use "builtin:functional";

$test-a: closure.invoke($list-first,[0,1,2]); // $test-a should be 0
$test-b: $list-first:invoke([0,1,2]); // test-b should also be 0, but this shows invoking closures using member call syntax
$test-c: $max:invoke(5,$b:6); // test-c should be 6, this shows using named arguments in invoking closures
```

## Function/Closure Level Statements

Functions and closures have different statements allowed within them than that of selection blocks and the top level.

### Variable Declarations

Variable declarations are the same as every other place they can be declared, `$variable-name: [expression]`.

For an example of variable declarations within a function:

```
@func variable-func($a:5) {
    $b: $a + 3;
    $c: $b * 4;
    @return $b + $c;
}
```

> When declaring variables in a function, remember that each level of blocks in a function is still the same "scope"
> Meaning that if you declare a variable inside a while loop for example, it still is accessible outside the while loop
> This can be quite useful for "mutating" variables within a function, but it is different behaviour than a lot of other
> programming languages.
> 
> The reasoning for this, is that there is no "update" variable syntax, so re-declaring the same variable seems the best
> way to "mutate" a variable, and if loops and the like made separate scopes, there would be no way at all to do any
> updates.
> 
{style="note"}

### Conditionals

Conditionals follow the same `@if`, `@else-if`, `@else` structure as in other selection blocks and top level statements.

For an example of conditionals within a function:
```
@func factorial($n) {
    @if $n == 0 {
        return 1;
    } @else-if $n == 1 {
        return 1;
    } @else {
        return $n * factorial($n - 1);
    }
}
```

### Returning Values

Returning the results of functions to the invoker is quite simple, you just do `@return [expression];`.

For example, the following function always returns 5 when called.

```
@func return-five() {
    @return 5;
}
```

> If you do not return a value from your function, it will implicitly return `null`
> 
{style="note"}

### For Loops

For loops allow you to repeat a block of function statements over a range of numbers, they are of the form
`@for $value from [start] through/to [end] {...}` where the `...` is the block of function statements. The difference
between `through` and `to`, is that `through` includes the endpoint, and `to` does not. The loop then iterates `$value`
over every from the start to whatever end value it has.

For examples of usages of for loops:

```
@func for-loop-test() {
    $sum-a: 0;
    @for $test-value from 0 through 10 {
        $sum-a +: $test-value;
    }
    // at this point $sum-a is 55
    $sum-b: 0;
    @for $test-value from 0 to 10 {
        $sum-b +: $test-value;
    }
    // at this point $sum-b is 45 as it did not include 10 in the sum
    @return $sum-a - $sum-b; // 10
}
```

> For loops support being done in reverse, you can have a start that is greater than the end
> 
> i.e. you can do `@for $value from 10 through 0 {...}`
> 
{style="note"}

### Each Loops

"Each" loops are used to iterate over collections/sequences (strings/lists/maps), there are 2 forms for them:

1. `@each $value in $collection {...}`
2. `@each $key, $value in $collection {...}`

In both forms, the `...` is the list of function statements you want to do for each item in the collection, the difference
is the second one gives you both the key, and value for each item in the collection, in the case of strings and lists this
is the index starting from 0, otherwise, it is the key for the object in the map.

A few example of each loops are as follows:
```
@func each-loop-test {
    $new-string: "";
    @each $character in "Hello, World!" {
        @if $character != "e" {
            $new-string: $new-string+$character
        }
    }
    // $new-string is now "Hllo, World!"
    $scores-by-index: [5,3,1];
    $total-score: 0;
    @each $index, $score in $scores-by-index {
        $total-score +: (($index+1)*$score);
    }
    // $total-score should be 5*1 + 3*2 + 1*3 or 5+6+3 or 14
    $dict: {
        "a": "hello",
        "b": "world",
        "c": "!"
    };
    $pretty-dict: "{\n";
    @each $key, $value in $dict {
        $pretty-dict +: "\t" + $key + ": \"" + $value + "\",\n";
    }
    $pretty-dict: $pretty-dict + "}";
    // $pretty-dict is now the following 5 lines as a string
    // {
    //     a: "hello",
    //     b: "world",
    //     c: "!",
    // }
}
```

### While Loops

While loops are loops that repeat a sequence of function statements while a condition remains true, they are of the form
`@while [condition] {...}` where `...` is the sequence of function statements you wish to repeat while `[condition]` evaluates
to true.

An example of a while loop is as follows:

```
@function collatz-steps($n) {
    $steps: 0;
    @while $n != 1 {
        $n: $n/2 @if ($n % 2) == 0 @else (3 * $n)+1;
        $steps +: 1;
    }
    @return $steps;
}
```

> While loops are the only loops that have the possibility of running forever. ***DO NOT*** do this,
> if you do, then KSP2 will never load, and you will have to kill it. In fact, if you can do your construct using another
> form of loop, use that other loop.
> 
{ style="warning"}