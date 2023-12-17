# Data_WheelSuspension

This module data's C# type is: `KSP.Modules.Data_WheelSuspension`.

This module data's element type is: `Data_WheelSuspension`.

This module data object has the following classes:

- `.suspensionTransformName`
- `.suspensionOffset`
- `.suspensionDistance`
- `.targetPosition`
- `.springRatio`
- `.damperRatio`
- `.boostRatio`
- `.maximumLoad`
- `.useDistributedMass`
- `.useAutoBoost`
- `.suspensionColliderName`
- `.adjustForHighGee`
- `.highGeeThreshold`
- `.highGeeSpringTweakable`
- `.highGeeDamperTweakable`
- `.SuspensionDirection`

## suspensionTransformName

type: `string`

The Suspension Transform Name

## suspensionOffset

type: `real`

The Suspension Offset.

This is the offset between the suspension transform and the wheel collider transform.

This is a KSP customization.

## suspensionDistance

type: `real`

The distance the Suspension moves.

Length of the suspension travel (m).

Refer to Suspension settings https://vehiclephysics.com/components/wheel-collider/#suspension-parameters

## targetPosition

type: `real`

The Wheel collider Target (anchor) position.

Relative position in the suspension travel (compression) where the wheel is located at design time.

It's a normalized value between 0 and 1 (0 - 100%)

Refer to Suspension settings https://vehiclephysics.com/components/wheel-collider/#suspension-parameters

## springRatio

type: `real`

Spring Ratio.

Refer to Suspension settings https://vehiclephysics.com/components/wheel-collider/#suspension-parameters

## damperRatio

type: `real`

Damper Ratio.

Refer to Suspension settings https://vehiclephysics.com/components/wheel-collider/#suspension-parameters

## boostRatio

type: `real`

The Boost Ratio. KSP suspension can be boosted.

## maximumLoad

type: `real`

The maximum load for the wheel suspension.

## useDistributedMass

type: `boolean`

Set true to use mass distrubited across all the vehicles wheels.

Leave this as true.

## useAutoBoost

type: `boolean`

Set false to not use KSP suspension boost.

## suspensionColliderName

type: `string`

The transform name where the wheel coillider is.

Should be a separate transform from the rest of the model and have a disabled Unity Wheel Collider component on it.

## adjustForHighGee

type: `boolean`

Set to true and Gee for the wheel is > highGeeThreshold autoBoost will be turned off

and highGeeSpringTweakable applied only if autoSpringDamper is true.

## highGeeThreshold

type: `real`

The GeeASL where high gee spring will be applied.

## highGeeSpringTweakable

type: `real`

The spring tweakable setting that will be applied if adjustForHighGee is true.

## highGeeDamperTweakable

type: `real`

The damper tweakable setting that will be applied if adjustForHighGee is true.

## SuspensionDirection

type: `integer`

The Local Axis the Ssuspension transform travels in.

