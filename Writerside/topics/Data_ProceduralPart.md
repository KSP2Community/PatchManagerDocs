# Data_ProceduralPart

This module data's C# type is: `KSP.Modules.Data_ProceduralPart`.

This module data's element type is: `Data_ProceduralPart`.

This module data object has the following classes:

- `.BasePartDensity`
- `.ProceduralPartTypeName`
- `.PartMultiJointScaleSliderKey`

## BasePartDensity

type: `real`

Part density is the initially set mass from the part prefab / the initial default mesh area.

It is used to modify the mass and cost of the procedural part based on the shape set by the player at runtime.

If you do not set this value (or reset it to -1) it will be calculated and set when you export the prefab to the part JSON file.

## ProceduralPartTypeName

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## PartMultiJointScaleSliderKey

type: `string`

Set this string to the Name of the slider in the OffsetSliderSystem that you want to use to set the joint positions along for a multi-joint part that is set to use a single axis.

