# Data_WheelMotor

This module data's C# type is: `KSP.Modules.Data_WheelMotor`.

This module data's element type is: `Data_WheelMotor`.

This module data object has the following classes:

- `.driveResponse`
- `.idleDrain`
- `.wheelSpeedMax`
- `.torqueCurve`
- `.useResources`
- `.requiredResource`

## driveResponse

type: `real`

This is the wheel drive response. How fast the motor applies torque.

## idleDrain

type: `real`

The amount of EC consumed when the motor is at idle. Total drain is rate * (inputApplied + idleDrain).

Rate is the rate defined in the requiredResource construct.

## wheelSpeedMax

type: `real`

Maximum speed the wheel can do.

## torqueCurve

type: `dictionary[any]`

The motor torque curve.

The X axis is the curent velocity, the Y axis is how much torque the motor will generate at the X velocity.

## useResources

type: `boolean`

Whether the motor consumes resources.

## requiredResource

type: `dictionary[any]`

Resource required to operate this module if the above property is true.

