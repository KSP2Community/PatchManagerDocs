# Part Reference
<show-structure for="chapter,procedure" depth="2"/>

A part object's C# type is: `KSP.Sim.Definitions.PartData`.

A part object's element type is: `parts_data`.

Part objects have the following classes:

- `.partName`
- `.author`
- `.category`
- `.family`
- `.childStageOffset`
- `.cost`
- `.crewCapacity`
- `.stageOffset`
- `.isCompound`
- `.sizeCategory`
- `.stageType`
- `.resourceCosts`
- `.tags`
- `.stagingIconAssetAddress`
- `.PartSizeDiameter`
- `.angularDrag`
- `.breakingForce`
- `.breakingTorque`
- `.buoyancy`
- `.buoyancyUseSine`
- `.coLiftOffset`
- `.coMassOffset`
- `.coPressureOffset`
- `.coBuoyancy`
- `.coDisplacement`
- `.crashTolerance`
- `.explosionPotential`
- `.fuelCrossFeed`
- `.heatConductivity`
- `.mass`
- `.maxTemp`
- `.attachRules`
- `.attachNodes`
- `.resourceContainers`
- `.AllowKinematicPhysicsIfIntersectTerrain`
- `.serializedPartModules`
- `.resourceSummary`
- `.PAMModuleSortOverride`
- `.PAMModuleVisualsOverride`
- `.collisionVolumeBoundsScale`
- `.emissiveConstant`
- `.maximumDrag`
- `.minimumDrag`
- `.physicsMode`
- `.inverseStageCarryover`
- `.skinMassPerArea`
- `.bodyLiftOnlyUnattachedLift`
- `.bodyLiftOnlyAttachName`
- `.maxLength`
- `.radiatorHeadroom`
- `.radiatorMax`
- `.skinMaxTemp`
- `.skinInternalConductionMult`
- `.thermalMassModifier`
- `.buoyancyUseCubeNamed`
- `.oabEditorCategory`
- `.partType`
- `.PreferredOrientation`
- `.MirrorTechnique`
- `.CanSuggestOrientation`
- `.PickUpPointOffset`
- `.PickupRotationPointOffset`
- `._title`
- `._subtitle`
- `._description`
- `._manufacturer`
- Plus one for every single module as in `.Module_...`

## Meta data

### partName

type: `string`

A unique key for the part - appears in save files, not user facing.

### author

type: `string`

The name of the person or people working on the part

## Descriptors

### category

type: `string (enum: PartCategories)`

The category of this part, categories are described on the [Wiki](https://wiki.spacewarp.org/wiki/Category).

### family

type: `string`

The family of this part, families are described on the [Wiki](https://wiki.spacewarp.org/wiki/Family).

### childStageOffset

type: `integer`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### cost

type: `integer`

The cost of the part, unused.

### crewCapacity

type: `integer`

How many Kerbals this part can hold.

### stageOffset

type: `integer`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### isCompound

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### sizeCategory

type: `string (enum: KSP.OAB.MetaAssemblySizeFilterType)`

The size of this part category wise, these are described on the [Wiki](https://wiki.spacewarp.org/wiki/Size_Category)

If you are using LOABE, that adds more possible size categories.

### stageType

type: `string (enum: KSP.OAB.AssemblyPartStageType)`

The stage type of this part, these are described on the [Wiki](https://wiki.spacewarp.org/wiki/Stage_Type)

### resourceCosts

type: `list[dictionary[any]]`

A list of the costs of resources, unknown to me what this does.

### tags

type: `string`

A space separated list of tags for the part used in searching.

### stagingIconAssetAddress

type: `string`

The address to the addressables asset used for staging

### PartSizeDiameter

type: `real`

The diameter of the part

## Properties

### angularDrag

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### breakingForce

type: `real`

The force required to break this part.

### breakingTorque

type: `real`

The torque required to break this part.

### buoyancy

type: `real`

How dense the part is.

### buoyancyUseSine

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### coLiftOffset

type: `dictionary[real] (Vector3)`

A 3d vector for the center of lift offset.

### coMassOffset

type: `dictionary[real] (Vector3)`

A 3d vector for the center of mass offset.

### coPressureOffset

type: `dictionary[real] (Vector3)`

A 3d vector for the center of pressure offset.

### coBuoyancy

type: `dictionary[real] (Vector3)`

A 3d vector for the center of buoyancy.

### coDisplacement

type: `dictionary[real] (Vector3)`

A 3d vector for the center of displacement.

### crashTolerance

type: `real`

The speed it takes to break this part in a crash.

### explosionPotential

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### fuelCrossFeed

type: `boolean`

Enabled if fuel can feed through this part, otherwise disabled

### heatConductivity

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### mass

type: `real`

The mass of the part in tons.

### maxTemp

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### attachRules

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### attachNodes

type: `list[dictionary[any]]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### resourceContainers

type: `list[ResourceContainer]` ([Resource Containers](Resource-Containers.md))

This contains a list of all the resources contained in this part, Patch Manager provides specializations for editing/grabbing these like the following

```
:parts {
    /* Adding Resources */
    * > resourceContainers {
        +Methalox {
            /* ... */
        }
    }

    /* Editing Resources */
    * > resourceContainers {
        Methalox {
            /* ... */
        }
    }
```

### AllowKinematicPhysicsIfIntersectTerrain

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### serializedPartModules

type: `list[Module]` ([Part Modules](Part-Modules.md))

This contains a list of all the part modules on this part, to add or edit parts please use the selector syntax like the following, and not edit this field directly

```
:parts {
    /* Adding Modules */
    +Module_Something {
        /* ... */
    }

    /* Editing Modules */
    * > Module_Something {
        /* ... */
    }
```

### resourceSummary

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Parts Manager Overrides

### PAMModuleSortOverride

type: `list[dictionary[any]]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### PAMModuleVisualsOverride

type: `list[dictionary[any]]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Editor

### collisionVolumeBoundsScale

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Captured but unsorted

### emissiveConstant

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### maximumDrag

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### minimumDrag

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### physicsMode

type: `string (enum: KSP.Sim.PartPhysicsModes)`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### inverseStageCarryover

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### skinMassPerArea

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### bodyLiftOnlyUnattachedLift

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### bodyLiftOnlyAttachName

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### maxLength

type: `integer`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### radiatorHeadroom

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### radiatorMax

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### skinMaxTemp

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### skinInternalConductionMult

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### thermalMassModifier

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### buoyancyUseCubeNamed

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## OAB Settings

### oabEditorCategory

type: `string (enum: KSP.OAB.OABEditorPartCategory)`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### partType

type: `string (enum: KSP.OAB.AssemblyPartTypeFilter)`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### PreferredOrientation

type: `string (enum: KSP.OAB.OABOrientation)`

Allows a part to specify what orientation it considers its primary. The mode specified will see the part oriented similarly to how it is in the prefab by default. The part will try to maintain this orientation regardless of VAB mode.

### MirrorTechnique

type: `string (enum: KSP.OAB.MirrorTechnique)`

Allows specifying what type of mirror logic is used for this part. May impact how other parts interact with it. The Auto setting is configurable on OAB.prefab

### CanSuggestOrientation

type: `boolean`

Based on all of the other settings, from orientation preference to mirror technique and category, suggest a rotation for this part only if no use rotation is provided. By default, no suggestions are made.

### PickUpPointOffset

type: `dictionary[real] (Vector3)`

Offset at which the player cursor "grabs" the part when in OAB

### PickupRotationPointOffset

type: `dictionary[real] (Vector3)`

Offset at which the part is rotated in the OAB when the player is grabbing a part

### _title

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### _subtitle

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### _description

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### _manufacturer

type: `string`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

