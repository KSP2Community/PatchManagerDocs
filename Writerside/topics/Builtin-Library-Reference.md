# Builtin Library Reference

This section shall list all the builtin libraries that patch manager has, link to the pages of their documentation
and then list the methods and variables in them with a short description.

## builtin:debug
Main page: [`builtin:debug`](builtin-debug.md)

- `debug-log($value) -> none`
  - Logs values to the unity console log
- `serialize($value) -> string`
  - Used for converting any value to a string that uniquely
represents the value.

## builtin:dictionary
Main page: [`builtin:dictionary`](builtin-dictionary.md)

- `dictionary.set($dict,$key,$value) -> dictionary`
  - Used for updating a key in a dictionary
- `dictionary.merge($original-dict,$new-dict) -> dictionary`
  - Used to merge 2 dictionaries together into one
- `dictionary.keys($dict) -> list`
  - Gets a list of keys from a dictionary
- `dictionary.values($dict) -> list`
  - Gets a list of values from a dictionary
- `dictionary.remove($dict,$key) -> dictionary`
  - Removes a value from a dictionary
- `dictionary.count($dict) -> integer`
  - Gets the number of items in a dictionary

## builtin:functional
Main page: [`builtin:functional`](builtin-functional.md)

- `get-function($name) -> closure`
  - Used to convert a function into a closure
- `closure.invoke($closure, ...) -> any`
  - Used to invoke a closure
- `closure.bind($closure, ...) -> closure`
  - Used to bind arguments to the left hand side of a closure
- `closure.right-bind($closure, ...) -> closure`
  - Used to bind arguments to the right hand side of a closure

## builtin:list
Main page: [`builtin:list`](builtin-list.md)
- `list.append($list,$value) -> list`
  - Used to append a value onto the end of a list
- `list.append-all($list, $values) -> list`
  - Used to append a list of values onto the end of a list
- `list.create(...) -> list`
  - Used to create a list from the arguments
- `list.sort($list, [$comparator]) -> list`
  - Used to sort a list, with an optional comparison function
- `list.map($list,$closure) -> list`
  - Used to map a closure onto a list
- `list.filter($list,$closure) -> list`
  - Used to filter a list depending on the results of a closure
- `list.reduce($list,$initial-value,$closure) -> any`
  - Used to reduce a list using a closure
- `list.length($list) -> integer`
  - Used to get the length of a list
- `list.join($list,$separator:"") -> string`
  - Join a list into a string with an optional separator
## builtin:math
Main page: [`builtin:math`](builtin-math.md)
- `square-root($value) -> real`
  - Take the square root of a number
- `cube-root($value) -> real`
  - Take the cube root of a number
- `pow($x,$y) -> real`
  - Calculate $x ^ $y
- `ln($a) -> real`
  - Calculate the natural log of a number
- `log($a,$base) -> real`
  - Calculate the logarithm of a number at a base
- `log10($a) -> real`
  - Calculate the base 10 logarithm of a number
- `ceiling($a) -> real`
  - Calculate the ceiling of a number
- `floor($a) -> real`
  - Calculate the floor of a number
- `abs($a) -> real`
  - Calculate the absolute value of a number
- `max(...) -> real`
  - Return the maximum value of the arguments
- `min(...) -> real`
  - Return the minimum value of the arguments
- `list.max($list) -> real`
  - Return the maximum value of a list
- `list.min($list) -> real`
  - Return the minimum value of a list
- `round($x) -> real`
  - Rounds a value
- `sign($x) -> real`
  - Returns the sign of a value
- `$E -> real`
  - Euler's number
- `sin($a) -> real`
  - Calculate the sine of an angle
- `cos($a) -> real`
  - Calculate the cosine of an angle
- `tan($a) -> real`
  - Calculate the tangent of an angle
- `sinh($a) -> real`
  - Calculate the hyperbolic sine of an angle
- `cosh($a) -> real`
  - Calculate the hyperbolic cosine of an angle
- `tanh($a) -> real`
  - Calculate the hyperbolic tangent of an angle
- `asin($a) -> real`
  - Calculate the inverse sine of a number
- `acos($a) -> real`
  - Calculate the inverse cosine of a number
- `atan($a) -> real`
  - Calculate the inverse tangent of a number
- `atan2($y,$x) -> real`
  - Calculate the atan2 of $y and $x
- `$PI -> real`
  - Pi
- `$TAU -> real`
  - 2 * Pi
- `interpolate($a,$b,$t) -> real`
  - Linear interpolation
- `list.normalize($vector) -> list`
  - Normalize a list treating it as a vector
- `normalize(...) -> list`
  - Normalize the arguments treating them as a vector
## builtin:meta
Main page: [`builtin:meta`](builtin-meta.md)
- `exists-mod($mod-name) -> boolean`
  - Check if a mod is loaded in the current ksp2 instance
- `exists-function($function-name) -> boolean`
  - Check if a function is defined
## builtin:reflection
Main page: [`builtin:reflection`](builtin-reflection.md)
- `typeof($value) -> string`
  - Gets a values type as a string

## builtin:string
Main page: [`builtin:string`](builtin-string.md)
- `string.length($string) -> integer`
  - Gets the length of a string
- `string.reverse($string) -> string`
  - Reverse a string
- `string.starts-with($string,$other-string) -> boolean`
  - Check if a string starts with another string
- `string.ends-with($string,$other-string) -> boolean`
  - Check if a string ends with another string
- `string.contains($string,$other-string) -> boolean`
  - Check if a string contains another string
- `string.to-codepoint($string) -> int`
  - Convert a one character string to a unicode codepoint
- `codepoint-to-string($codepoint) -> string`
  - Convert a unicode codepoint to a single character string

## builtin:type-conversion
Main page: [`builtin:type-conversion`](builtin-type-conversion.md)
- `to-bool($value) -> boolean`
  - Convert a value to a boolean
- `to-real($value) -> real`
  - Convert a value to a real
- `to-integer($value) -> integer`
  - Convert a value to an integer
- `to-string($value) -> string`
  - Convert a value to a string
- `dictionary.to-list($dict) -> list`
  - Convert a dictionary to a list
- `list.to-dictionary($list) -> dictionary`
  - Convert a list to a dictionary
- `string.to-list($string) -> list`
  - Convert a string to a list of single characters
## builtin:config
Main page: [`builtin:config`](builtin-config.md)
- `get-config($label,$name) -> any`
  - Get a specific config
- `get-configs($label) -> dictionary`
  - Get all configs under a label
## builtin:parts
Main page: [`builtin:parts`](builtin-parts.md)
- `find-module($part-object,$module-name) -> dictionary/none`
  - Find a module on a part object
- `add-module($part-object,$module) -> dictionary`
  - Add a module to a part object
- `remove-module($part-object,$module-name) -> dictionary`
  - Remove a module from a part object
- `replace-module($part-object, $module-name, $module) -> dictionary`
  - Replace the module in a part object
- `create-module($type) -> dictionary`
  - Create a module object based on a type name (the module type must be in a loaded assembly)
- `find-module-data($part-module,$module-data-name) -> dictionary/none`
  - Find a module data in a module object
- `add-module-data($part-module,$module-data) -> dictionary`
  - Add module data to a module object
- `remove-module-data($part-module,$module-data-name) -> dictionary`
  - Remove module data from a module object
- `replace-module-data($part-module,$module-data-name,$module-data) -> dictionary`
  - Replace module data in a module object
- `create-module-data($type)`
  - Create a module data object based on a type name (the module data type must be in a loaded assembly)
- `get-data-object($module-data) -> dictionary`
  - Get the data object from a module data object
- `set-data-object($module-data,$data-object) -> dictionary`
  - Set the data object in a module data object