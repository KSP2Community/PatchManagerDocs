# Class Capture Selector

Sometimes you may want to check if an object has a class, and see if the sub-object that class represents has a certain value
or use a certain value, but you don't want to go into the class, or can't if you for example are adding another sub-object
to the parent that depends on that value. With the selectors that currently exist, that'd require having to write some
form of function instead to search the current object for that class and the value you want from that class. This is why
the class capture selector exists. It allows you to select objects with a class, and run expressions on the sub-objects
representing those classes and bring them into the scope of your current object.

## Using the Class Capture Selector.

The class capture selector starts off the same way as the class selector, with the `.class-name`, but it is followed by
a `:[...]`, where the `...` is a list of function statements to run in the scope of the sub-object that the class represents.
In this scope, you get access to the `$$field-name` implicit variables, and the `$current` implicit variable as well. Any
variables you define here though get passed back out of the selector into the selection block the selector is attached to.

For an example of how this works, here is a patch which will add a module to all parts that have an antenna, but have the
data of that module be based off of the communication range of the part's antenna.

```
:parts {
    // Now let's do our "class capture", the .Module_DataTransmitter is the module for an antenna
    .Module_DataTransmitter:[
        $commRange: $$CommunicationRange; // And this is our capture, where we are capturing the object local value $$CommunicationRange from the Antenna module, and storing it in a scope local variable of $commRange
    ] {
        // In this scope $commRange is accessable, but $$CommunicationRange is not
        // Add the module like usual
        +Module_Test {
            // And the data
            +Data_Test {
                // Setting the value of Test inside the data to our captured value
                Test: $commRange;
            }
        }
    }
}
```