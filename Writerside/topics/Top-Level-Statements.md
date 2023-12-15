# Top Level Statements

Patch Manager supports other top level statements than just the selection block construct described in
[Rulesets, Selectors, and Selection Blocks](Rulesets-Selectors-and-Selection-Blocks.md). This page will list how to use
all of them.

## Importing Libraries
Libraries are described in [Libraries](Libraries.md).

To reiterate how to import them though, you use `@use` followed by the library name as a string, or if it is a builtin
library/a library from another mod, you prefix the library name with `builtin:` or `other-mod-id:` respectively.

For example:
```
@use 'builtin:debug'; // Import the builtin debug library.
```

## Declare Variables
You can declare variables at the top level much like you can in selection blocks, with the `$variableName: [value];`
construct

```
$my-variable: 5;
$my-other-variable: $my-variable*2;
```

## Define Stages
Stages are explained in [Stages](How-to-Use-the-Stage-System.md), which is an advanced topic.

But for an example of a stage definition to put here:

```
@define-stage "after-mod_c": {
    @after "mod_c:post";
};
```

## Define Functions
Functions are explained in [Functions and Closures](Functions.md), which is an advanced topic.

But for an example of a function to put here:

```
// Define a function that doubles whatever value is put into it.
@function double($value) {
    @return $value * 2;
}
```

## Define Mixins
Mixins are explained in [Mixins](Mixins.md), which is an advanced topic.

But for an example of a mixin to put here:
```
// Define a mixin to be used in ResourceContainers to scale the units.
@mixin scale-resource($amount: 1) {
  capacityUnits: *$amount;
  initialUnits: *$amount;
}
```

## Conditionals
Conditionals are essentially the same as in selection blocks, but rather than selection actions going inside them,
top level statements do.
```
$my-variable: 3;
@if $my-variable == 3 {
    @use "library_3";
} @else-if $my-variable < 3 {
    @use "library_4";
} @else {
    @use "library_5";
}
```

## Selection Block
This is described in the aforementioned [Rulesets, Selectors, and Selection Blocks](Rulesets-Selectors-and-Selection-Blocks.md)
page, but there are a few other things that can be done with them that are described in [Selection Block Attributes](Selection-Block-Attributes.md)

But for reiterate here, this top level statement looks similar to the following:
```
:parts #wheel_0v_rover {
    /* ... */
}
```

## Declare Labels to be Patched

Patch Manager by default only patches a subset of Addressables labels, that being every label it has a ruleset for, as 
of writing this documentation, that is `parts_data` and `resources`. If you wish to use the generic `:json` ruleset for 
a value of a separate label, then you need to tell patch manager that you want to patch that label as well. You can do
this by writing `@patch` followed by a comma separated list of strings and a semicolon.

```
@patch "label_a", "label_b", "label_c";
```

> Do not unnecessarily patch labels, the more labels that are patched, the slower patch manager will run on startups where it has to rebuild its cache.
> 
{style="warning"}

## Declare Configs

You can declare configs as a top level statement, configs are described in [Configs](Config.md), which is an advanced tutorial.

For an example config declaration:

```
@create-config "ls-constants", "day-length": 21600;
```

## Update configs

You can also update configs as a top level statement.

For an example of this:

```
@update-config 0, "ls-constants", "ls-day-length": 86400;
```