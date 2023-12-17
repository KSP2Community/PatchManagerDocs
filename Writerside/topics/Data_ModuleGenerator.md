# Data_ModuleGenerator
<show-structure for="chapter,procedure" depth="2"/>

This module data's C# type is: `KSP.Modules.Data_ModuleGenerator`.

This module data's element type is: `Data_ModuleGenerator`.

This module data object has the following classes:

- `.IsAlwaysActive`
- `.Status`
- `.ResourceSetting`
- `.UseDecay`
- `.DecayTime`
- `.DecayCurve`
- `.StartDecayImmediately`
- `.FluxGenerated`
- `.AutoShutdown`
- `.AutoShutdownTemperature`
- `.SafeOperationTemperature`
- `.UseEmissive`
- `.UseEmissiveTemperature`
- `.EmissiveMaterialNames`
- `.EmissiveTemperatureCurve`
- `.EmissiveLerpRateUp`
- `.EmissiveLerpRateDown`

## Uncategorized

## General Parameters

### IsAlwaysActive

type: `boolean`

This should not be enabled at the same time as AutoShutdown

### Status

type: `string (enum: KSP.Modules.GeneratorStatus)`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### ResourceSetting

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Decay Controls

### UseDecay

type: `boolean`

Whether the output should be reduced with time

### DecayTime

type: `real`

How long the generator takes to decay completely, in seconds

### DecayCurve

type: `dictionary[any]`

Curve that maps fractional lifetime to fractional output

### StartDecayImmediately

type: `boolean`

If true, the decay timer starts as soon as the part is spawned. If false, the decay timer starts when MET starts

## Thermal Controls

### FluxGenerated

type: `real`

This should be 0 if IsAlwaysActive is enabled

### AutoShutdown

type: `boolean`

This should not be enabled at the same time as IsAlwaysActive

### AutoShutdownTemperature

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### SafeOperationTemperature

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Emissive Controls

### UseEmissive

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### UseEmissiveTemperature

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### EmissiveMaterialNames

type: `list[string]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### EmissiveTemperatureCurve

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### EmissiveLerpRateUp

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### EmissiveLerpRateDown

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

