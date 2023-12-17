# Data_ControlSurface
<show-structure for="chapter,procedure" depth="2"/>

This module data's C# type is: `KSP.Modules.Data_ControlSurface`.

This module data's element type is: `Data_ControlSurface`.

This module data object has the following classes:

- `.CtrlTransformDir`
- `.CtrlTransformRotAxis`
- `.CtrlTransformSign`
- `.CtrlSurfacePivotTransformName`
- `.CtrlSurfaceLiftTransformName`
- `.CtrlSurfaceDeployTransformName`
- `.DeployTransformRotAxis`
- `.CtrlSurfaceRange`
- `.UseCtrlSurfaceDeployAngle`
- `.CtrlSurfaceDeployAngle`
- `.CtrlSurfaceMinimumLockAngleForControl`
- `.ReverseMirrorDeployement`
- `.UseExponentialSpeed`
- `.ActuatorSpeedNormalScale`
- `.MinimumDeployAngle`
- `.MeshAreaLiftMultiplier`
- `.DisableLiftingSurfaceForce`
- `.ApplyLiftSurfaceForceAtBase`
- `.ApplyLiftSurfaceForceAtPivotMidpoint`
- `.IgnoreSASInputs`
- `.DefaultActionGroup`

## Uncategorized

## Control Surface Behaviour

## Control Surface Setup

### CtrlTransformDir

type: `string (enum: KSP.Modules.Data_LiftingSurface+TransformDir)`

The Transform Direction that lift is provided in.

This is relative to the CtrlSurfacePivotTransformName or the CtrlSurfaceLiftTransformName Transform if it is defined.

### CtrlTransformRotAxis

type: `string (enum: KSP.Modules.Data_LiftingSurface+TransformDir)`

The Transform Axis that the control surface rotates around.

This is relative to the CtrlSurfacePivotTransformName Transform.

### CtrlTransformSign

type: `real`

1 = Positive transformDir, -1 = Negative transformDir

### CtrlSurfacePivotTransformName

type: `string`

The transform that will be adjusted to show the visual impact of the control surface motion.

### CtrlSurfaceLiftTransformName

type: `string`

The transform that will be used to calculate lift for the control surface.

Most of the time this would be the same as the CtrlSurfacePivotTransformName.

### CtrlSurfaceDeployTransformName

type: `string`

The Transform Axis that the control surface deploys around.

This is relative to the CtrlSurfaceDeployTransformName Transform.

### DeployTransformRotAxis

type: `string (enum: KSP.Modules.Data_LiftingSurface+TransformDir)`

The Transform Axis that the control surface deploys around.

This is relative to the CtrlSurfaceDeployTransformName Transform.

### CtrlSurfaceRange

type: `real`

Range (in degrees) the control surface can deflect and deploy.

### UseCtrlSurfaceDeployAngle

type: `boolean`

Whether to use the CtrlSurfaceDeployAngle for the deployment angle. If false will use CtrlSurfaceRange for the deployment angle.

### CtrlSurfaceDeployAngle

type: `real`

Angle (in degrees) the control surface will deploy.

### CtrlSurfaceMinimumLockAngleForControl

type: `real`

Minimum angle of ‘deployment’ that the control surface must be at to actuate. If the part is only deployed to this or less, it won’t tilt in response to control inputs.

### ReverseMirrorDeployement

type: `boolean`

If set to true when the part is a mirror copy the deployment rotation will be reversed.

If set to false when the part is a mirror copy the deployment rotation will NOT be reversed.

### UseExponentialSpeed

type: `boolean`

Movement type for the ctrlsurface. false == use MoveTowards, true == use Lerp

### ActuatorSpeedNormalScale

type: `real`

How fast the control surface actuator will try to respond in Degrees/sec

### MinimumDeployAngle

type: `real`

If AllowMinimumDeplyAngle is true use this to set the minimum deploy angle.

### MeshAreaLiftMultiplier

type: `real`

Multiple of Area of Mesh to get lift value.

### DisableLiftingSurfaceForce

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### ApplyLiftSurfaceForceAtBase

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### ApplyLiftSurfaceForceAtPivotMidpoint

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### IgnoreSASInputs

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### DefaultActionGroup

type: `string (enum: KSP.Sim.KSPActionGroup)`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

