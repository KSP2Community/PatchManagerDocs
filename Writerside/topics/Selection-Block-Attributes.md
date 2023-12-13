# Selection Block Attributes

There is one part of selection blocks that was not mentioned in [Rulesets, Selectors, and Selection Blocks](Rulesets-Selectors-and-Selection-Blocks.md)

These are basically certain `@attributes` prefixed to the selection block, there are only 2 of them though.

## @stage

This attribute can only be used on the outermost selection block (the one directly at the top level of the file).
It is defined as follows `@stage` followed by the stage name for the selection block as a string.

Example:
```
@stage "example:post"
:parts {
    /* ... */
}
```

Stages are described in [Stages](How-to-Use-the-Stage-System.md)

## @require

This attribute conditionally enables the patch depending on the existence or non-existence of certain mods in the current
installation. It is `@require` followed by a boolean expression (using `and`, `or`, and `not`) with the only values allowed
being mod ids as strings. These mod ids resolve to `true` if the mod is installed otherwise `false`. If the expression
resolves to true, the block is enabled, otherwise it is disabled.

This can be used at any nesting level of a patch block.

Example:
```
@require "life_support" and "resources" and not "super_life_support"
:parts {
    /* this patch will only run if the life support and resources mods are installed, but not if the super life support mod is */
}
```