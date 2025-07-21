# builtin:list

## Methods

### `list.append($list: list, $value: any) -> list`
Append a value to the end of the list

### `list.append-all($list: list, $values: list) -> list`
Append a list to the end of the list

### `list.create(...) -> list`
Create a list from the given arguments

### `list.sort($list: list, [$comparator: closure]) -> list`
Sort a list, optionally with a given comparator.

Comparators are binary functions with the given behaviour:
a < b -> negative
a = b -> 0
a > b -> positive

### `list.map($list: list, $closure: closure) -> list`
Apply a function to an entire list, returning a new list

### `list.filter($list: list, $closure: closure) -> list`
Apply a predicate to an entire list, returning a new list

### `list.reduce($list: list, $initial-value: any, $closure: closure) -> any`
Reduce a list using a given method

### `list.length($list: list) -> integer`
Get the length of a list

### `list.join($list: list, [$separator: string]) -> string`
Join a list into a string using an optional separator

### `list.remove($list: list, $to-remove: any) -> list`
Remove a given value from a list

### `list.remove-all($list: list, $to-remove: list) -> list`
Remove all the values in the other list from a list

### `list.slice($list: list, $start: integer, $end: integer) -> list`
Get a subset of a list