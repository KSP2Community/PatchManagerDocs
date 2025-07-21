# builtin:parts

This contains helper functions specifically for parts

## Methods

### `find-module($part-object: Part, $module-name: string) -> Module`
Finds a module in a part data object, returns null if one could not be found

### `add-module($part-object: Part, $module: Module) -> Part`
Adds a module to a part, returning a new part with the given module

### `remove-module($part-object: Part, $module-name: string) -> Part`
Removes a module from a part, returning a new part without the given module

### `replace-module($part-object: Part, $module-name: string, $module: Module) -> Part`
Replaces a module within a part, returning a new part with the module replaced

### `create-module($type: string) -> Module`
Creates a new module with the given type

### `find-module-data($part-module: Module, $module-data-name: string) -> ModuleData`
Finds a given module data within a module

### `add-module-data($part-module: Module, $module-data: ModuleData) -> Module`
Adds a module data to a module

### `remove-module-data($part-module: Module, $module-data-name: string) -> Module`
Removes a module data from a module

### `replace-module-data($part-module: Module, $module-data-name: string, $module-data: ModuleData) -> Module`
Replaces a module data in a module

### `create-module-data($type: string) -> ModuleData`
Creates a new module data object

### `get-data-object($module-data: ModuleData) -> dict`
Gets the data object for a module data

### `set-data-object($module-data: ModuleData, $data-object: dict) -> ModuleData`
Sets the data object for a module data