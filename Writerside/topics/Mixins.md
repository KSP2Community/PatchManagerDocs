# Mixins

Mixins are a simple way of preventing yourself from repeating the same pattern over and over in your patches.
They are quite simple to declare, and to use.

## Declaring a mixin

Mixins are declared using the `@mixin` top level state followed by the name of the mixin, and then an `(`, an optional
list of mixin parameters, followed by a `)` and then a `{` and then any amount of [Selection Actions](Selection-Actions.md).
then a `}`.

For a very simple mixin declaration with no parameters:

```
@mixin scale-mass-by-two() {
    mass *: 2;
}
```

### Mixin Parameters

As mentioned before, mixins can have parameters, they are a comma separated list of `$parameter-name`, with optional
default values, which then make them of the form `$parameter-name:[default-value-expression]`.

Here are a few examples of the above:

```
// Mixin with one parameter
@mixin scale-mass-by($N) {
    mass *: $N;
}
// Mixin with one default parameter
@mixin scale-max-temp-by($N:2) {
    maxTemp *: $N;
}
// Mixin with 2 parameters, one default
@mixin scale-mass-by-and-max-temp-by($mass-scale,$temp-scale:$mass-scale) {
    mass: *$mass-scale;
    maxTemp *: $temp-scale;
}
```

> The default values for mixin parameters can depend on previous parameters, as when computing the value of parameters
> the computation is done from left to right.
> 
{style="note"}

### Slotted Mixins

Sometimes you may want your mixin to take more than just values as arguments, and this is where "Slotted Mixins" come in
these can take a set of selection actions as a "parameter", and this set can be executed using the `@mixin-slot` keyword

```
// Unslotted mixin
@mixin ps-pam-override() {
    PAMModuleVisualsOverride +: [
        {
            PartComponentModuleName: PartComponentModule_PartSwitch,
            ModuleDisplayName: "VSwift/PartSwitch",
            ShowHeader: true,
            ShowFooter: false
        }
    ];
}

// Slotted mixin
@mixin part-switch() {
    +Module_PartSwitch {
        +Data_PartSwitch {
            @mixin-slot // Whatever selection actions are passed will be executed when this action is executed
        }
    }
    @include ps-pam-override()
}
```


## Using Mixins

Now that you have declared mixins, you need to be able to include them into your selection blocks, using the following
construct: `@include mixin-name([parameters])`, the parameters are a comma separated list of values corresponding to
the parameters defined in the mixin declaration, but they can also be named in the form of `$parameter-name:[passed-value]`.

What including a mixin does, is essentially copy and paste all the selection actions declared within the mixin into your
selection block in a sub environment (as in similar to a `* {...}` selection block), and replace the parameters in the mixin with the values you passed.

Here are a few examples of including the mixins defined above:

```

:parts #wheel_0v_rover {
    @include scale-mass-by-two() // Scale the mass by 2 using the parameterless mixin
    @include scale-max-temp-by() // Scale the max temp by 2, as the default value of $N is 2
}

:parts #wheel_1v_rover {
    @include scale-mass-by(2) // Scale the mass by 2 using the parameterized mixin
    @include scale-max-temp-by($N:2) // Scale the max temp by 2, and explicitly name the argument
}

:parts #wheel_2v_rover {
    @include scale-mass-by-and-max-temp-by(2) // Scale the mass by 2, and the max temp by 2 as the $temp-scale is equal to $mass-scale by default
}

:parts #wheel_2v_rover_rugged {
    @include scale-mass-by-and-max-temp-by(2,4) // Scale the mass by 2, and the max temp by 4
}

:parts #wheel_3v_rover {
    @include scale-mass-by-and-max-temp-by($temp-scale:4,$mass-scale:2) // Scale the mass by 2, and the max temp by 4, passing the parameters in reverse
}
```


> Due to mixins copying the selection actions into a sub environment, any variables you declare in a mixin will only
> be available in the mixin, and not in the outer selection block.
> 
{style="warning"}

### Using Slotted Mixins

To use slotted mixins, the process is the same as a normal `@include` process, but after the `(...)` you start a selection block using
`{` and then putting the set of actions you want to be put into the slot and closing it with a `}`.

```
@use "VSwift:*";
:parts #KLSS_water_tank_2v_1x2 {
    @include part-switch() { // Everything in the `{}` will be executed when the mixin hits a `@mixin-slot` keyword
        +Pipes {
            +No {
                Transforms: [];
            }
            +Yes {
                Transforms: [
                    Pipes,
                    "Sub Hatch"
                ];
            }
        }
        +Crossbars {
            +No {
                Transforms: [];
            }
            +Yes {
                Transforms: [
                    "Cross Armature"
                ];
            }
        }
    }
}
```