# Data_Engine

This module data's C# type is: `KSP.Modules.Data_Engine`.

This module data's element type is: `Data_Engine`.

This module data object has the following classes:

- `.engineModes`
- `.UseEmissive`
- `.EmissiveMaterialNames`
- `.EmissiveTemperatureCurve`
- `.EmissiveLerpRateUp`
- `.EmissiveLerpRateDown`
- `.DeployedModeAnimationStateShortName`
- Plus `.[ID]` for every engine mode ID

## engineModes

type: `list[EngineMode]` ([EngineMode](EngineMode.md))

This is a list of all the engine modes for this engine.

This module data has a special adapter that allows you to do the following with these modes.

```
Data_Engine {
    +EngineModeId {
        // Creates a new engine mode with the engine mode id
    }
    * > #EngineModeId {
        // Selects the engine mode by id
    }
    * > engine_mode {
        // Selects all engine modes
    }
}
```

## UseEmissive

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## EmissiveMaterialNames

type: `list[string]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## EmissiveTemperatureCurve

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## EmissiveLerpRateUp

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## EmissiveLerpRateDown

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## DeployedModeAnimationStateShortName

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.