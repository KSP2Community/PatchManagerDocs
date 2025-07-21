# builtin:type-conversion

## Methods

### `to-bool($value: any) -> boolean`
Convert a value into a boolean

### `to-real($value: any) -> real`
Convert a value to a real number, only works with integers, reals, and strings

### `to-integer($value: any) -> integer`
Convert a value to an integer, only works with integers, reals, and strings

### `to-string($value: any) -> string`
Convert a value into a string

### `dictionary.to-list($dict: dictionary) -> list[list]`
Convert a dictionary to a list of key value pairs (represented as 2 item lists)

### `list.to-dictionary($list: list[list]) -> dictionary`
Does the opposite of dictionary.to-list

### `string.to-list($str: string) -> list[string]`
Convert a string to a list of its characters