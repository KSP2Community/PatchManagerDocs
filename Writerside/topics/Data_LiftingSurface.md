# Data_LiftingSurface

This module data's C# type is: `KSP.Modules.Data_LiftingSurface`.

This module data's element type is: `Data_LiftingSurface`.

This module data object has the following classes:

- `.omnidirectional`
- `.liftCurve`
- `.liftMachCurve`
- `.dragCurve`
- `.dragMachCurve`
- `.liftingSurfaceCurve`
- `.transformDir`
- `.transformSign`
- `.transformName`
- `.nodeEnabled`
- `.attachNodeName`
- `.perpendicularOnly`
- `.useInternalDragModel`

## omnidirectional

type: `boolean`

If true lift is the same whether the surface is upside down or not.

## liftCurve

type: `dictionary[any]`

This curve is evaluated to obtain coefficient of lift for a given angle of attack in degrees.

## liftMachCurve

type: `dictionary[any]`

This curve is evaluated to obtain coefficient of lift multiplier based on the current mach speed of the vessel.

## dragCurve

type: `dictionary[any]`

This curve is evaluated to obtain coefficient of drag for a given angle of attack in degrees.

## dragMachCurve

type: `dictionary[any]`

This curve is evaluated to obtain coefficient of drag multiplier based on the current mach speed of the vessel.

## liftingSurfaceCurve

type: `string`

The name of the lifting surface curve that will be used from PhysicsGlobals.

## transformDir

type: `integer`

The Transform Direction that lift is provded in.

## transformSign

type: `real`

1 = Positive transformDir, -1 = Negative transformDir

## transformName

type: `string`

The Transform that provides the lift. If left blank will use the part transform.

## nodeEnabled

type: `boolean`

If True the attachNodeNode must be attached to provide lift and drag forces.

## attachNodeName

type: `string`

The attachNodeNode that must be attached if nodeEnabled is true.

## perpendicularOnly

type: `boolean`

If true the lift is projected on plane that is the normal of the velocity direction.

## useInternalDragModel

type: `boolean`

Use the drag model in this module to calculate and apply drag forces.

