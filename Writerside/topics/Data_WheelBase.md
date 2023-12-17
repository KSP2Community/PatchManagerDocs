# Data_WheelBase

This module data's C# type is: `KSP.Modules.Data_WheelBase`.

This module data's element type is: `Data_WheelBase`.

This module data object has the following classes:

- `.WheelType`
- `.FitWheelColliderToMesh`
- `.Radius`
- `.Center`
- `.Mass`
- `.FrictionSharpness`
- `.WheelDamping`
- `.WheelMaxSpeed`
- `.ClipObject`
- `.AdherentStart`
- `.FrictionAdherent`
- `.PeakStart`
- `.FrictionPeak`
- `.LimitStart`
- `.FrictionLimit`
- `.GeeBias`
- `.GroundHeightOffset`
- `.InctiveSubsteps`
- `.ActiveSubsteps`
- `.TireForceSharpness`
- `.SuspensionForceSharpness`
- `.WheelColliderTransformName`
- `.WheelTransformName`
- `.SpringSlerpRate`
- `.MinimumDownforce`
- `.UseNewFrictionModel`
- `.AlignVisualAndCollider`
- `.DeploymentSubsystemNormalized`
- `.RetractionSubsystemNormalized`
- `.UseStandinCollider`

## WheelType

type: `integer`

The Wheel type. Free = free spinning wheel. Motorized - Motorized wheel (rover wheel). Leg = Landing Leg.

## FitWheelColliderToMesh

type: `boolean`

If true the collider mesh for the wheel will be resized to fit the visual mesh of the wheel

## Radius

type: `real`

The radius of the wheel

## Center

type: `dictionary[any]`

The center offset of the wheel

## Mass

type: `real`

The mass of the wheel in Tons.

## FrictionSharpness

type: `real`

The friction sharpness

## WheelDamping

type: `real`

The damping applied to the wheel

## WheelMaxSpeed

type: `real`

Max speed the wheel can do

## ClipObject

type: `string`

Allow each wheel module to specify one object that clips.

If specified this object (and all it's children) will have it's layer changed between physics ignore and default depending on the deployment state.

## AdherentStart

type: `real`

This is the tire friction curve adherent start position. For Landing Legs this will be the peak x value.

Refer to https://vehiclephysics.com/blocks/tires/

## FrictionAdherent

type: `real`

This is the tire friction curve adherent value at the start position. For Landing Legs this will be the peak y value.

Refer to https://vehiclephysics.com/blocks/tires/

## PeakStart

type: `real`

This is the tire friction curve adherent peak start position.

Refer to https://vehiclephysics.com/blocks/tires/

## FrictionPeak

type: `real`

This is the tire friction curve adherent peak value.

Refer to https://vehiclephysics.com/blocks/tires/

## LimitStart

type: `real`

This is the tire friction curve adherent lowest point start position.

Refer to https://vehiclephysics.com/blocks/tires/

## FrictionLimit

type: `real`

This is the tire friction curve adherent limit value.

Refer to https://vehiclephysics.com/blocks/tires/

## GeeBias

type: `real`

Percent increase in friction at 0g. If geeBias = 1, then frictionMultiplier = 2.0 at 0g

## GroundHeightOffset

type: `real`

The ground height to allow when launching with the wheels deployed.

## InctiveSubsteps

type: `integer`

The number of PhysX substeps when inactive

## ActiveSubsteps

type: `integer`

The number of PhysX substeps when active.

## TireForceSharpness

type: `real`

How sharply tire forces are applied.

## SuspensionForceSharpness

type: `real`

How sharply suspension forces are applied.

## WheelColliderTransformName

type: `string`

This must be the wheel collider transform name from the model.

## WheelTransformName

type: `string`

This must be the wheel transform (the bit that spins) name from the model.

This must be the deployment target transform (for Landing Legs) name from the model

## SpringSlerpRate

type: `real`

The rate as which the spring targetPosition is slerped in VPWheelCollider.

## MinimumDownforce

type: `real`

This is the minimum downforce to apply to the wheel.

## UseNewFrictionModel

type: `boolean`

If set to true will use the new friction model.

## AlignVisualAndCollider

type: `boolean`

If set to true will align the wheel visual and collider.

Only applies to wheels that are deployable.

Landing legs should set this to false and wheels set this to true.

## DeploymentSubsystemNormalized

type: `real`

Set this to a normalized value 0-1 where 0 is fully retracted and 1 is fully deployed.

Only applies to wheels that are deployable.

At this normalized time the subsystems will be turned on (suspension, wheel collider, etc) when deploying.

## RetractionSubsystemNormalized

type: `real`

Set this to a normalized value 0-1 where 0 is fully deployed and 1 is fully retracted.

Only applies to wheels that are deployable.

At this normalized time the subsystems will be turned off (suspension, wheel collider, etc) when retracting.

## UseStandinCollider

type: `boolean`

Whether to use a stand in collider or not when deploying/retracting.

This is usually only used for larger deployable wheels that need a stand-in collider before the wheel collider is created.

