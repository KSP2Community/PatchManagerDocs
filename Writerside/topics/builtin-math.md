# builtin:math

## Constants

### `PI`
Equal to the constant Pi

### `TAU`
Equal to 2*PI

### `E`
Equal to euler's number

## Methods

### `square-root($value: real) -> real`
Get the square root of a real

### `cube-root($value: real) -> real`
Get the cube root of a real

### `pow($x: real, $y: real) -> real`
Raise x to the y'th power

### `ln($a: real) -> real`
Get the natural logarithm of a real

### `log($a: real, $base: real) -> real`
Get a logarithm of a number

### `log10(ax: real) -> real`
Get the log base 10 of a number

### `ceiling($a: real) -> real`
Round a number up

### `floor($a: real) -> real`
Round a number down

### `max(...: reals) -> real`
Get the maximum of the given arguments

### `min(...: reals) -> real`
Get the minimum of the given arguments

### `list.max($list: list[real]) -> real`
Get the maximum of the list

### `list.min($list: list[real]) -> real`
Get the minimum of the list

### `round($x: real) -> real`
Round a real

### `sign($x: real) -> real`
Get the sign of a real

### `sin($a: real) -> real`
Compute sin(a)

### `cos($a: real) -> real`
Compute cos(a)

### `tan($a: real) -> real`
Compute tan(a)

### `sinh($a: real) -> real`
Compute sinh(a)

### `cosh($a: real) -> real`
Compute cosh(a)

### `tanh($a: real) -> real`
Compute tanh(a)

### `asin($a: real) -> real`
Compute arcsin(a)

### `acos($a: real) -> real`
Compute arccos(a)

### `atan($a: real) -> real`
Compute arctan(a)

### `atan2($x: real, $y: real) -> real`
Compute atan2(x,y)

### `interpolate($a: real, $b: real, $t: real) -> real`
Compute `(1 - t) * a + t * b`, or the linear interpolation of a and b a t

### `list.normalize($vector: list[real]) -> list[real]`
Treat a list as a vector and normalize the values

### `normalize(...: reals) -> list[real]`
Treat the arguments as a vector and normalize them