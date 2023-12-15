# Configs
<show-structure for="chapter,procedure" depth="2"/>

> This is going to be added in Patch Manager 0.5.0, it is currently not out
>
{style="note"}

Configs are a way of having universally accessible configuration for your patches, available at patch time, this can be
useful for like if you have a constant that you want other mods to be able to change, or if you want mods to be able to
provide overrides to your defaults for specific parts.

## Defining Configs

> It is recommended for you to define your configs in files under patch files in the `patches/configs/` directory for
> organizational purposes.
>
{style="tip"}

Defining configs is quite simple, you do `@define-config "config-label", "config-name": [config data as a value];`


For a few examples of defining configs:

```
@define-config "ls-constants", "ls-day-length": 5;
@define-config "ls-overrides", "cockpit_1v_m1_crew": {
    days-of-food: 5,
    days-of-water: 5,
    days-of-oxygen: 5
};
```

> Config object names can be the same as long as they have different labels, what fully qualifies a config name is the
> name and label.
> 
{style="note"}


## Updating Configs

To update a preexisting config, you do `@update-config update-priority, "config-label", ["config-name"]: [update-expression];`

The update priority means that in the case of multiple updates on the same config, the ones with the lower priority will
be run first. This is an expression.

The update expression has `$value` set as the current value of the config pointed to by the label and name, or the current
value of the dictionary of configurations pointed to by config-label if only that is selected. And the update expression
also allows prefix expressions.

A few examples of updating configurations
```
$config-update-priority: 5;

@update-config $config-update-priority, "ls-constants", "ls-day-length": *2;

@update-config $config-update-priority*2, "ls-overrides", "cockpit_1v_m1_crew": {
    days-of-food: 10,
    days-of-water: 10,
    days-of-oxygen: 10
};

@use "builtin:dictionary";

@update-config $config-update-priority, "ls-overrides": $value:merge(
    {
        wheel_0v_rover: {
            days-of-food: 5,
            days-of-water: 5,
            days-of-oxygen: 5
        },
        wheel_1v_rover: {
            days-of-food: 5,
            days-of-water: 5,
            days-of-oxygen: 5
        }
    }
);
```

## Using Configs

To use configs, you can grab them using 2 different methods, `get-config`, and `get-configs`. These are available
in the `builtin:config` library.

> Only get configs from within selection blocks, or functions that are only called from within selection blocks. If
> you do not do this, it will be an error as the configs will not be "ready" before selection blocks are run.
> 
{style="warning"}

### get-config($label,$name)

This allows you to get the value of a single config object with its label and name, or if that config object does not
exist it returns `null` (allowing for you to do easy checking).

Here is an example of using this:
```
@use 'builtin:config';

:parts {
    $override: get-config("ls-overrides",$$partName); // Get the possible override for the part name
    @if $overrride { // if the override is not null, e.g. in the case where the part name is "cockpit_1v_m1_crew"
        // Do stuff.
    }
}
```

### get-configs($label)

This gets a dictionary of all configs that are defined under the passed label, with the keys being the names of the configs,
if there are no such configs, it will return an empty dictionary.

```
@use 'builtin:config';
:parts {
    $test: get-configs("ls-constants") // returns {ls-day-length: 10}
}
```

### Specific Examples of Config Usage

The following are a few specific examples as to what configs can be used for.

#### Allowing Overrides for Specific Parts

Say for the sake of example, that you are writing a life support mod that adds its resources in a small amount to every
single command pod, but, you wanted to allow other mods to be able to override this amount. There are a few ways that 
you could go about this.
1. The mod author could just add its resources to the pod and you could check for this.
    - This falls flat because this make the mods parts depend on your mod, when they may want to have an optional dependency
2. The mod author could do a patch after yours on its parts to update the values
   - This also falls flat, because it requires making use of the staging system which can be a bit complex and can have
   pitfalls
3. You could set up your mod to be moddable itself with configs for part overrides
    - This requires more work from you, but makes your mod as easily moddable as possible for other modders

For an example of how you could set this up, assuming you have 3 resources you want to add to parts `food`, `water`, and
`oxygen`.

First make a library called `_configs.patch` for your mod or similar, this will contain a function for generating an
override config dictionary. The reason this is a function is such that if you add stuff to your mod for stuff you want
to add, or change what gets added, then it won't break old patches. And also it allows you to set up default arguments.

```
@use 'constants'; // Assume this has your default constants

@func ls-create-override($days-of-food: $ls-DEFAULT-DAYS, $days-of-water: $days-of-food, $days-of-oxygen: $days-of-food)
{
    @return {
        days-of-food: $days-of-food,
        days-of-water: $days-of-water,
        oxygen-per-day: $days-of-oxygen
    };
}
```

And then in your main patch for adding these resources to the parts, you can set it up like follows, grabbing the 
config values at the start.

```
@use 'constants';
@use 'builtin:config';

:parts {
    $possible-override: get-config("ls-overrides",$$partName); // "ls-override" is your label for your configs.
    $days-food: $possible-override["days-of-food"] @if $possible-override @else $ls-DEFAULT-DAYS;
    $days-water: $possible-override["days-of-water"] @if $possible-override @else $ls-DEFAULT-DAYS;
    $days-oxygen: $possible-override["days-of-oxygen"] @if $possible-override @else $ls-DEFAULT-DAYS;
    * > resourceContainers {
        $crewCapacity: $parent["crewCapacity"];
        @if $crewCapacity > 0 {
            +Oxygen {
                capacityUnits: $days-food * $ls-OXYGEN-PER-SECOND * $ls-DAY-LENGTH * $crewCapacity;
                initialUnits: $days-food * $ls-OXYGEN-PER-SECOND * $ls-DAY-LENGTH * $crewCapacity;
            }
            +Water {
                capacityUnits: $days-water * $ls-WATER-PER-SECOND * $ls-DAY-LENGTH * $crewCapacity;
                initialUnits: $days-water * $ls-WATER-PER-SECOND * $ls-DAY-LENGTH * $crewCapacity;
            }
            +Food {
                capacityUnits: $days-oxygen * $ls-FOOD-PER-SECOND * $ls-DAY-LENGTH * $crewCapacity;
                initialUnits: $days-oxygen * $ls-FOOD-PER-SECOND * $ls-DAY-LENGTH * $crewCapacity;
            }
        }
    }
}
```

And then any other modders can add override configs for their parts like the following for example:

```
@use 'builtin:meta';
@if exists-mod("ls") { // Check first if the mod exists
    @use 'ls:configs';
    @create-config "ls-overrides", "their_part_name": ls-create-override(10); // Utilize the default values to initialize days of food, water, and oxygen to 10
}
```

#### Creating Overridable Constants

Say now, you want the length of a day to be configurable inside your life support mod (for example if you are using some form of different solar system),
then, you can use the config system to create modifiable constants.

To start, you should move the constants for your mod you want to be mutable into a file under the configs directory
with any name, lets go with `constants.patch` for this, in there you would define your constants as configs as follows
```
@create-config "ls-constants", "day-length": 21600;
```

Then in your patches where you use these constants, you instead grab the value of the constant at patch time, for example
using the previous patch:

```
@use 'constants';
@use 'builtin:config';

:parts {
    $possible-override: get-config("ls-overrides",$$partName); // "ls-override" is your label for your configs.
    $days-food: $possible-override["days-of-food"] @if $possible-override @else $ls-DEFAULT-DAYS;
    $days-water: $possible-override["days-of-water"] @if $possible-override @else $ls-DEFAULT-DAYS;
    $days-oxygen: $possible-override["days-of-oxygen"] @if $possible-override @else $ls-DEFAULT-DAYS;
    $day-length: get-config("ls-constants","day-length");
    * > resourceContainers {
        $crewCapacity: $parent["crewCapacity"];
        @if $crewCapacity > 0 {
            +Oxygen {
                capacityUnits: $days-food * $ls-OXYGEN-PER-SECOND * $day-length * $crewCapacity;
                initialUnits: $days-food * $ls-OXYGEN-PER-SECOND * $day-length * $crewCapacity;
            }
            +Water {
                capacityUnits: $days-water * $ls-WATER-PER-SECOND * $day-length * $crewCapacity;
                initialUnits: $days-water * $ls-WATER-PER-SECOND * $day-length * $crewCapacity;
            }
            +Food {
                capacityUnits: $days-oxygen * $ls-FOOD-PER-SECOND * $day-length * $crewCapacity;
                initialUnits: $days-oxygen * $ls-FOOD-PER-SECOND * $day-length * $crewCapacity;
            }
        }
    }
}
```

And then, other mods can easily change the day length for your mod using the `@update-config` statement, like the following
for example:

```
@update-config 0, "ls-constants", "ls-day-length": 86400;
```