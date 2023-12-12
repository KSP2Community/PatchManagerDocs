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
You can merge an objects value with another dictionary/object using the `@merge` statement followed by the value to merge with and a semicolon.
```
:parts #wheel_0v_rover {
    @merge {
        mass: 5
    };
}
```
This will merge the `wheel_0v_rover` with the object after it, either adding a mass field or setting it to 5.

## 