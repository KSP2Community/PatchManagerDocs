# builtin:functional

## Methods

### `get-function($name: string) -> closure`
Get a global function by name

### `closure.invoke($closure: closure, ...) -> any`
Execute a closure with the given arguments

### `closure.bind($closure: closure, ...) -> closure`
Return a new closure with the given arguments bound to the left side of the closure

### `closure.right-bind($closure: closure, ...) -> closure`
Return a new closure with the given arguments bound to the right side of the closure