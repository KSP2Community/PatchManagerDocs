# Data_WheelBogey

This module data's C# type is: `KSP.Modules.Data_WheelBogey`.

This module data's element type is: `Data_WheelBogey`.

This module data object has the following classes:

- `.wheelTransformRefName`
- `.wheelTransformBaseName`
- `.bogeyTransformName`
- `.bogeyRefTransformName`
- `.maxPitch`
- `.minPitch`
- `.restPitch`
- `.pitchResponse`
- `.bogeyAxis`
- `.bogeyUpAxis`

## wheelTransformRefName

type: `string`

The reference transform for the wheels (the spinny bits).

## wheelTransformBaseName

type: `string`

The wheel transform name (the spinny bits). If multiple they have to have the same transform name.

## bogeyTransformName

type: `string`

The transform name for the bogey that is rotated/pitched.

## bogeyRefTransformName

type: `string`

The bogey reference transform

## maxPitch

type: `real`

## minPitch

type: `real`

The minimum pitch angle

## restPitch

type: `real`

The resting pitch (angle in degrees)

## pitchResponse

type: `real`

How fast the pitch of the bogey is rotated (in secs).

## bogeyAxis

type: `dictionary[real] (Vector3)`

The axis the bogey rotates around.

## bogeyUpAxis

type: `dictionary[real] (Vector3)`

The up axis for the bogey.

