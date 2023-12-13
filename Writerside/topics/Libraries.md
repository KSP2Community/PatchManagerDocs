# Libraries

There may come a time, and hopefully quite soon that time may come, that you wish to organize duplicated values between
your patches, or values duplicated between patch files and the like into one spot that you can import them from, this is
where libraries come in! Libraries are special patch files that don't contain any patches and are not executed by default
but only when they are imported into another patch file, or even into patch files in other mods.

Libraries are great places to store the following:

- Constant values used across your patches, especially ones other mods may want to use if they are trying to do stuff after you
- Common functions used in your patches, and functions for other mods to use as well. Described in [Functions and Closures](Functions.md)
- Common mixins used in your patches, and mixins for other mods to use as well. Described in [Mixins](Mixins.md)

## Creating Libraries

Libraries are created quite easily, just prepend the name of a patch file with an `_`, for example `_constants.patch` and
`_functions.patch`, and for organization purposes these should go under the `patches/libraries` folder. In these files
you can put any top level statement described in [Top Level Statements](Top-Level-Statements.md) except for selection
blocks. (yes this includes importing other libraries).

An example library file is as follows:
`_constants.patch`
```
$example-CONSTANT_A: 5;
$example-CONSTANT_B: 3.14159;
```
This library defines 2 constants, `$example-CONSTANT_A` and `$example-CONSTANT_B`.

> If you are intending the library you are making to be used by other mods, you should "namespace" your declarations.
> This is such that if 2 mods accidentally define the same constant, they will not overlap.
> To do this, you should prefix all declarations that your mod uses with either your mod id, or a shortening that uniquely
> represents your mod id (e.g. `PatchManager` -> `pm`) like such `prefix-DECLARATION_NAME` (e.g. `$pm-PATCH_NUMBER`).
> And then you must always refer to your declaration with that prefix.
> 
> (This does not apply to custom member functions such as functions that begin with `list.` or `dictionary.`, though you
> could still follow up after the `.` with the prefix if you wish)
> 
{style="tip"}

## Using Libraries

Using libraries in your patch files couldn't be simpler, just do a use statement at the top level, the syntax of which is
`@use` followed by the library file name (without the `_` prefix, or the `.patch` file extension) as a string, and a `;`.
Then every single declaration in that library should be imported into your current patch file.

An example of using the library described earlier is as follows:
```
@use "constants";
$tau: $example-CONSTANT_B * 2; // Define tau as 2 pi, where pi is defined in the library.
```
> This way of importing libraries only works if this library is in the same general mod as the patch file you are
> importing it into, for importing libraries from other mods, and builtin libraries, read the next 2 sections.
> 
{style="warning"}

## Using Libraries from Other Mods

Using libraries from other mods is similar to the above, but you have to prefix the library name with the mod id of the
mod you are importing from followed by a colon, for example `example:constants`.

An example of using the library described earlier from another mod is as follows:
```
@use "example:constants";
$tau: $example-CONSTANT_B * 2; // Define tau as 2 pi, where pi is defined in the library.
```

## Using Builtin Libraries

Using builtin libraries is exactly the same as using libraries from other mods, except the prefix is `builtin:`.
All the builtin libraries that exist are defined in the [Builtin Library Reference](Builtin-Library-Reference.md).

An example of using the `builtin:math` library is as follows:
```
@use "builtin:math";
$half-pi: $PI/2; // Defines half-pi as pi/2
```

> The builtin libraries do not follow the name prefixing rules described in the previous sections, but rather use raw
> unprefixed names, such as `$PI`, `$TAU`, `$E` in the case of `builtin:math`
> 
{style="warning"}
