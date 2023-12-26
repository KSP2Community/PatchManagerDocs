# Selection Actions

What can be done inside selection blocks? Well selection actions of course, of which there are multiple types of, 
described here, from least to most advanced.

## Nested Selection Blocks
The simplest thing you can do inside a selection block, is nest more selection blocks,
This is basically treated as adding an intersection selector between the outer selection blocks selector and the inner
selection blocks selector.
```
:parts {
    #wheel_0v_rover {
       /* more selection actions can go here */
    }
}
```
Here the outer selector block matches every single part, while the inner one only matches those matching the `#wheel_0v_rover`
name selector as well.


## Deleting the objects
You can very easily delete objects inside of selector blocks using the `@delete` statement followed by a semicolon.
```
:parts #wheel_0v_rover {
    @delete;
}
```
This selection action will delete any parts that match the `#wheel_0v_rover` name selector.

## Setting an objects value
You can also set an objects value directly using a selection block using the `@set` statement followed by the value and a semicolon.
```
:parts #wheel_0v_rover {
    @set {
        oh: "no"
    };
}
```
This will set the value of the `wheel_0v_rover` definition to
```json
{
  "oh": "no"
}
```
(which will actually crash the game, so don't test this one like this)

## Merging an objects value with a dictionary
You can merge an objects value with another dictionary/object using the `@merge` statement followed by the value to merge
with and a semicolon.
```
:parts #wheel_0v_rover {
    @merge {
        mass: 5
    };
}
```
This will merge the `wheel_0v_rover` with the object after it, either adding a mass field or setting it to 5.

## Setting a field in an object
You can set fields in an object using a few ways, the simplest way is to just set a field directly like follows
```
:parts #wheel_0v_rover {
    mass: 5;
}
// or
:parts #wheel_0v_rover {
    "mass": 5;
}

// You can also do operations based on the current value of the field
:parts #wheel_0v_rover {
    mass +: 5;
}

:parts #wheel_0v_rover {
    mass -: 5;
}

:parts #wheel_0v_rover {
    mass /: 5;
}

:parts #wheel_0v_rover {
    mass *: 5;
}
```
> Do not try to do `mass : mass * 5`, the second `mass` will be treated as a string, instead use `$value` or `$$mass`
> 
{style="warning"}

### Field Indexors
But sometimes the field is an array or dictionary, and you want to set a specific index of it, this is where you can do
the following
```
/* some selector */ {
    some_dictionary["some_index"]: 5;
    some_list[3]: 10;
}
```

## Define a Variable
Sometimes you want a value that you can reference in this block, and blocks below it, this is what a variable is for,
they are defined as follows `$variable-name: ...;` where `...` is the expression/value you wish to assign to the variable

```
:parts #wheel_0v_rover {
    $my-variable: 5;
}
```

## Conditionally run selection actions
These next 2 selection actions are going to be a bit more advanced than the rest, but sometimes you may want to run some
actions conditionally, and the selectors/filters aren't enough to narrow down this condition, this is where `@if`,
`@else-if`, and `@else` blocks come in. It's best to just show these in action.
```
:parts #wheel_0v_rover {
    @if $$mass < 1 
    { 
        mass: 1;
    }
    @else-if $$mass < 5
    {
        mass: 5;
    }
    @else
    {
        mass: 10;
    }
}
```
The `@else-if` and `@else` blocks are completely optional, you can have an infinite amount of `@else-if` blocks, and can
have zero or one `@else` blocks, but the `@else` block must always be last, and the `@else-if` blocks must always be after
the `@if` block. And inside these blocks you can have any selection action described on this page

## Include a mixin
For more of an explanation on mixins read the [Mixins Tutorial](Mixins.md) in the Advanced Section. But for showing how
to include a mixin, without much other explanation:
```
:parts #wheel_0v_rover {
    @include scale-mass($scale-factor:5); // Include a mixin that scales the mass of the part by a passed scale factor
}
```

Now that we've gone over these selection actions, you might have noticed a lot of references to stuff such as values,
variables, or expressions, which will be explained in the next topic
[Values, Variables, and Expressions](Values-Variables-and-Expressions.md)