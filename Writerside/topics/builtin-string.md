# builtin:string

## Methods

### `string.length($string: string) -> integer`
Returns the length of a string

### `string.reverse($string: string) -> string`
Returns the reverse of a string

### `string.starts-with($string: string, $other-string: string) -> boolean`
Returns true if `$string` starts with `$other-string`

### `string.ends-with($string: string, $other-string: string) -> boolean`
Returns true if `$string` ends with `$other-string`

### `string.to-codepoint($string: string) -> integer`
Converts a 1 character string into a unicode codepoint

### `codepoint-to-string($codepoint: integer) -> string`
Converts a unicode codepoint into a 1 character string