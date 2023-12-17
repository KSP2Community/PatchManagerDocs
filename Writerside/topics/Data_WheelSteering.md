# Data_WheelSteering

This module data's C# type is: `KSP.Modules.Data_WheelSteering`.

This module data's element type is: `Data_WheelSteering`.

This module data object has the following classes:

- `.CaliperTransformName`
- `.SteeringCurve`
- `.SteeringMaxAngleCurve`
- `.SteeringResponse`

## CaliperTransformName

type: `string`

This is the caliper transform name (Steering point)

## SteeringCurve

type: `dictionary[any]`

This curve defines the rate of wheel turn related to the speed of the wheel.

The x values of the curve are the speed and the y values are the rate of wheel turn.

## SteeringMaxAngleCurve

type: `dictionary[any]`

This curve defines the maximum steering angle of wheel as a multiplier that will be applied based on the speed of the wheel.

The x values of the curve is the speed and the y values are the multiplier. y values are clamped between 0 and 1.

## SteeringResponse

type: `real`

This is how fast the wheel will turn/respond to player input.

