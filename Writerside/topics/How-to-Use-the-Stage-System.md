# Stages
<show-structure for="chapter,procedure" depth="2"/>

Patch Manager implicitly orders your patches into something called "stages", which are distinct temporal steps for when
your patch will run in relation to others. A stage is essentially a name, with a list of relations to their location in
time compared to other stages, either "before" certain stages, or "after" other stages.

## Implicit Stages

Patch Manager defines a list of these stages implicitly, with 2 for each mod in the game

1. `mod_id`, which is defined as after the `mod_id:post` of the previous mod in the mod loader, or not after anything for the first mod
2. `mod_id:post`, which is defined by default as after `mod_id`

## Defining Custom Stages

Patch Manager also allows you to define custom stages, with their own relations to other stages. There are 3 different
forms for this.

> To maintain ordering across patch files in your mod for stages, it is recommended to define all your stages in a 
> `stages.patch` file in your mods `patches/` folder, as otherwise the ordering of mod implicit or global implicit stages
> is undefined and not determinative for your mod.
> 
{style="tip"}

### Mod Implicit Stages

Mod implicit stages are the easiest to define, they are defined using `@define-stage "stage_name";` at the top level.

These stages are defined as being after the last mod implicit stage defined in your mod, or if there were no previous
mod implicit stages defined for your mod, it is defined as being after `mod_id`.

This also changes the definition of `mod_id:post` to be after the newly defined stage name.

Examples of defining implicit stages:

```
@define-stage "do-something";
@define-stage "do-something-else";
@define-stage "do-something-yet-more";
```

### Global Implicit Stages

Global implicit stages are the second easiest to define, they are defined using `@define-stage "stage_name": @global;`
at the top level.

These stages are defined as being after the last global stage defined anywhere, or if there were no previous global stages
defined, after the last mod in the load orders `mod_id:post`.

Examples of defining global implicit stages:

```
@define-stage "do-something-but-global": @global;
@define-stage "do-something-else-but-global": @global;
```

### Explicit Stages

Explicit stages are the hardest to define, as they require you to explicitly define the relation your stage has to other
stages. They are defined using `@define-stage "stage_name": {...};` at the top level where `...` is a list of statements
of the following form.

Either, `@after "stage-name";` which forces this stage to run after the aforementioned stage name, *if* said stage name 
is defined, otherwise it is ignored, or `@before "stage-name";` which forces this stage to run before the defined
stage, *if* said stage is defined, otherwise it is ignored.

Here are a few examples of defining explicit stages:

```
@define-stage "do-something-after-something-else": 
{
    @after "do-something-else";
};
@define-stage "do-something-before-something":
{
    @before "do-something";
};
@define-stage "do-something-after-something-else-but-before-something-yet-more":
{
    @after "do-something-else";
    @before "do-something-yet-more";
};
```

> If you make an explicit stage that has a circular dependency, it will break Patch Manager, and likely most patches
> in general. For example, do not do `@after "mod_id:post";` and `@before "mod_id";` with the same mod ID in your
> definition.
> 
{style="warning"}

#### Referencing Stages from Other Mods

If you want to define your stages to be relative to another mods stage, you have to prefix the name of the other mods stage
with the mod id of that other mod and a `:`, an example of which follows this, using the `do-something` stage from 
`other_mod`:

```
@define-stage "do-something-after-other-mod-stage" {
    @after "other_mod:do-something";
}
```

## Using Stages for your Patches

By default, every single top level selection block in your mod is defined to run at the stage `mod_id`, but you can change
this by using the `@stage "stage-name"` attribute on your selection block.

Here is an example of using this to make a patch run in the post stage of a mod:

```
@stage "my_mod:post"
:parts {
    /* do stuff */
}
```

### Using Stages from Other Mods

Similar to defining explicit relationships to stages from other mods, you can have your patch run during another mods stage
by prefixing the name that mod uses for that stage with that mods id.

Here is an example of this:

```
@stage "other_mod:do-something"
:parts {
    /* do something but during another mods stage */
}
```