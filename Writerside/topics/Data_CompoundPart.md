# Data_CompoundPart

This module data's C# type is: `KSP.Modules.Data_CompoundPart`.

This module data's element type is: `Data_CompoundPart`.

This module data object has the following classes:

- `.StartAnchorName`
- `.StartAnchorTransform`
- `.StartAnchorLookTransform`
- `.EndAnchorName`
- `.EndAnchorTransform`
- `.EndAnchorLookTransform`
- `.LinkerName`
- `.LinkerMinLength`
- `.LinkerMaxLength`

## StartAnchorName

type: `string`

Name of the starting anchor object to place at the start anchor end of the compound part.

If this is blank then it is assumed the whole part prefab model is placed at the start anchor end.

You Must supply both a StartAnchorName and EndAnchorName to use this feature.

## StartAnchorTransform

type: `string`

Transform where to place the linker/connector object at the start point of the compound part.

If this is blank the linker will be placed at the start anchor part transform position

## StartAnchorLookTransform

type: `string`

Optional Transform that will be made to look at the other Anchor.

## EndAnchorName

type: `string`

Name of the ending anchor object to place at the end anchor end of the compound part.

If this is blank then it is assumed the whole part prefab model is placed at the end anchor end.

You Must supply both a StartAnchorName and EndAnchorName to use this feature.

## EndAnchorTransform

type: `string`

Transform where to place the linker/connector object at the end point of the compound part.

If this is blank the linker will be placed at the end anchor part transform position

## EndAnchorLookTransform

type: `string`

Optional Transform that will be made to look at the other Anchor.

## LinkerName

type: `string`

Name of the the linker/connector object transform which should be part of the part model.

## LinkerMinLength

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## LinkerMaxLength

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

