# Data_RCS

This module data's C# type is: `KSP.Modules.Data_RCS`.

This module data's element type is: `Data_RCS`.

This module data object has the following classes:

- `.Propellant`
- `.maxThrust`
- `.shieldedCanActivate`
- `.atmosphereCurve`
- `.useThrustCurve`
- `.thrustCurve`
- `.disableUnderwater`
- `.fullThrustMin`
- `.useLever`

## Propellant

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## maxThrust

type: `real`

Maximum Thrust in kN this engine produces at 100% throttle.

## shieldedCanActivate

type: `boolean`

Can the engine be activated when shielded from airstream? ie: inside a fairing?

## atmosphereCurve

type: `dictionary[any]`

A curve to determine loss or gain of thrust due to changes in atmosphere vs vacuum values are based on ISP to ATM Pressure

## useThrustCurve

type: `boolean`

should we use a thrust curve (based on resource remaining) ?

## thrustCurve

type: `dictionary[any]`

The thrust curve to use if useThrustCurve is true.

## disableUnderwater

type: `boolean`

Is this engine disabled when under water?

## fullThrustMin

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## useLever

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

