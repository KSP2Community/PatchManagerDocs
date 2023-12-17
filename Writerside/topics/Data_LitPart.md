# Data_LitPart

This module data's C# type is: `KSP.Modules.Data_LitPart`.

This module data's element type is: `Data_LitPart`.

This module data object has the following classes:

- `.LightObjectNames`
- `.LightMaterialNames`
- `.Duration`
- `.RedColorGradient`
- `.GreenColorGradient`
- `.BlueColorGradient`
- `.AlphaColorGradient`
- `.DefaultActionGroup`
- `.DefaultEnabledState`
- `.RequiredResourceName`
- `.RequiredResourceThreshold`
- `.LightIntensityMultiplier`

## LightObjectNames

type: `list[string]`

Names of the gameObject that should be affected by the light state

## LightMaterialNames

type: `list[string]`

Names of the materials that should be affected by the light state

## Duration

type: `real`

The duration of the on/off transition in seconds. The gradient in colorGradient will be applied over this duration.

## RedColorGradient

type: `dictionary[any]`

Red component colors of the gradient mapping the color transition

## GreenColorGradient

type: `dictionary[any]`

Blue component colors of the gradient mapping the color transition

## BlueColorGradient

type: `dictionary[any]`

Green component colors of the gradient mapping the color transition

## AlphaColorGradient

type: `dictionary[any]`

Alpha component colors of the gradient mapping the color transition

## DefaultActionGroup

type: `string (enum: KSP.Sim.KSPActionGroup)`

Action group set by default

## DefaultEnabledState

type: `boolean`

Whether the light starts enabled or not

## RequiredResourceName

type: `string`

The resource for determining if lights are on. If not specificed, no resource is tracked and lights will always stay on

## RequiredResourceThreshold

type: `real`

The minimum amount needed to keep the lights on

## LightIntensityMultiplier

type: `real`

HDR color intensity multiplier for the emissive

