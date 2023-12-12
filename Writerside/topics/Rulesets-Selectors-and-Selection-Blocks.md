# Rulesets, Selectors, and Selection Blocks

Rulesets? Selectors? Selection Blocks? as the most fundamental constructs of a language?

That's because of what Patch Manager fundamentally is, the patch manager language may be turing complete like any other
programming language, but its similarity to other programming language in most regards ends there, it is first and
foremost a dataset transformation language, and a functional programming language second, and only to aid in the former.

Now that that is out of the way, what are the aforementioned rulesets, selectors, and selection blocks?
These are constructs that are used to help filter out from the dataset exactly what you want to patch, and what you want to do with it.

Let's start with the last one in the list, Selection Blocks are `{}` blocks preceded by a selector.
Then, selectors are just what comes before the opening of the selector block.
And finally, rulesets are a special subset of selector that are always the first, they decide which dataset you are
acting upon.

For an example of this in action:
```
:parts #wheel_0v_rover {
    /* ... */
}
```

This is an example of a single selection block, with its single selector breaking down as follows:
`:parts #wheel_0v_rover` is an intersection selector of `:parts` and `#wheel_0v_rover`, i.e. all the objects that match
the first selector `:parts` in that intersection are filtered through the second `#wheel_0v_rover`.
`:parts` as the first selector is also a "ruleset", it tells patch manager that we want to patch part objects specifically
and as such it pulls in every single part object to be filtered through the rest of the selectors.
`#wheel_0v_rover` is a name matching selector, it matches all objects going through it that have a name that matches
"wheel_0v_rover".

## List of Builtin Rulesets
- `:parts` this ruleset matches the part definitions in the game (and makes their object form more ameniable to patching)
- `:resources` this ruleset matches the resource definitions in the game (and again makes their object form more ameniable to patching)
- `:json` this ruleset just matches every json file and does no transformations on them

## List of Selectors

| Selector Name             | Usage     | Description                                                                                                                                         |
|---------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Intersection Selector     | `a b`     | When 2 selectors are separated by white space, it selects only objects that match both selectors                                                    |
| Combination Selector      | `a,b`     | When 2 selectors are separated by a comma, it selects all objects that match either selector                                                        |
| Precedence Selector       | `(a)`     | Wrap a selector in parentheses to ensure the order of selection is to your liking                                                                   |
| Name Selector             | `#xyz`    | Selects all objects that have a name, the name can include single character and multi character wildcards (?/*)                                     |
| Without Name Selector     | `~#xyz`   | Does the exact opposite of the name selector                                                                                                        |
| Element Selector          | `xyz`     | Matches a field (usually used in the child selector construct)                                                                                      |
| Class Selector            | `.xyz`    | Matches objects that have a certain class in their class list (depends on the ruleset but a lot of the time just a list of fieldnames)              |
| Class Capture Selector    | `.xyz:[]` | (Advanced) matches objects that have a certain class and capture variables from the object that class refers to inside the `[]`                     |
| Without Class Selector    | `~.xyz`   | Matches all objects that do not have a certain class                                                                                                |
| Child Selector            | `*>Field` | Grabs all the children of every object from the lefthandside selector and filters those children through the righthandside selector                 |
| Element Addition Selector | `+xyz`    | Adds an element to every object going through the selector and selects that element                                                                 |
| Ensure Element Selector   | `%xyz`    | For every object going through this selector, if it has a certain element, select that, otherwise add that element to the object and then select it |


But what can be done inside selection blocks? That is what [Selection Actions](Selection-Actions.md) are for.