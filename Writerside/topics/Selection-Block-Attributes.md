# Selection Block Attributes

There is one part of selection blocks that was not mentioned in [Rulesets, Selectors, and Selection Blocks](Rulesets-Selectors-and-Selection-Blocks.md)

These are basically certain `@attributes` prefixed to the selection block, each one is described in the following sections.

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

## @new

This attribute can only be used in the outermost selection block, and it is used to create new assets rather than patching
assets, it takes a list of arguments in `()` after it, and these arguments do different things depending on the ruleset of
the selection block it is attached to.

| Ruleset      | Argument names        | Description of behaviour                                                                                                                                             |
|--------------|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `:parts`     | `name`                | Creates a new part asset of the name "name", it is recommended to use [KSP2 Unity Tools](https://github.com/ksp2community/KSP2UnityTools) to generate these patches. |
| `:resources` | `name`, `[is_recipe]` | Creates a new resource with "name", this resource is a recipe if `is_recipe` is passed and is true.                                                                  |
| `:json`      | `label`, `name`       | Creates a new generic json asset in Addressables with the label `label`, and name `name`.                                                                            |

> Optional arguments are surrounded by `[]`
> 
{style="note"}

> If you create a part without its prefab in Addressables, the game will crash.
> 
{style="warning"}

Examples:

```
// Create a generic json asset with the label "tests", and the name "test_1"
@new("test","test_1")
:json {
    some: "data";
    can: "go";
    in: "here";
}

// Create a new resource named stormlight
@new("Stormlight")
:resources {
    displayNameKey: "Resource/DisplayName/Stormlight";
    abbreviationKey: "Resource/Abbreviation/SL";
    isTweakable: true;
    isVisible: true;
    massPerUnit: 0;
    volumePerUnit: 0;
    specificHeatCapacityPerUnit: 2010;
    flowMode: 4;
    transferMode: 1;
    costPerUnit: 0.8;
    NonStageable: false;
    resourceIconAssetAddress: "";
    vfxFuelType: "Pressurized";
}

// Create a new recipe called ArgonEC
@new("ArgonEC", true)
:resources {
    displayNameKey: "Resource/DisplayName/Argon";
    abbreviationKey: "Resource/Abbreviation/Ar";
    +Argon {
        unitsPerRecipeUnit: 1;
    }
    +ElectricCharge {
        unitsPerRecipeUnit: 1;
    }
}
```