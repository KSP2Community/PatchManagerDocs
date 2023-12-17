# Data_Fairing
<show-structure for="chapter,procedure" depth="2"/>

This module data's C# type is: `KSP.Modules.Data_Fairing`.

This module data's element type is: `Data_Fairing`.

This module data object has the following classes:

- `.FloatingNodeSize`
- `.FloatingAttachNodeTag`
- `.FloatingNodePosition`
- `.FloatingNodeDirection`
- `.FloatingNodeIsMultiJoint`
- `.FloatingNodeMultiJointMaxCount`
- `.FloatingNodeMultiJointOffset`
- `.FairingNode`
- `.NoseTip`
- `.EdgeWarp`
- `.AberrantNormalLimit`
- `.LocalUpAxis`
- `.Pivot`
- `.BaseModelTransformName`
- `.CapRadius`
- `.BaseRadius`
- `.CloseRadius`
- `.MaxRadius`
- `.SnapThreshold`
- `.CreateShellColliders`
- `.NumberOfCollidersPerCrossSection`
- `.MinHeightRadiusRatio`
- `.CrossSectionHeightMin`
- `.CrossSectionHeightMax`
- `.ConeSweepRays`
- `.ConeSweepPrecision`
- `.ShouldCapOnAutoGenerate`
- `.MassAreaRatio`
- `.FairingSideCount`
- `.FairingLengthSnapIncrement`
- `.FairingRadiusSnapIncrement`
- `.FairingSmoothingAngle`
- `.FairingThickness`
- `.FairingStartHeight`
- `.AllowConstructionTypeChange`
- `.AllowFloatingNodeChange`
- `.DefaultFairingEnabledToggle`
- `.DefaultAutoConstruction`
- `.DefaultDeployType`
- `.DefaultFloatingNodeState`
- `.LengthEditMinimum`
- `.LengthEditMaximum`
- `.LengthEditDefault`
- `.StageToggleDefault`
- `.MaxAutoFairingTargetRadius`
- `.MinAutoFairingTargetRadius`


## Floating node

### FloatingNodeSize

type: `real`

The attach node size of the floating node

### FloatingAttachNodeTag

type: `string`

Attach node tag that will be given to the dynamic attach node

### FloatingNodePosition

type: `dictionary[any]`

Local position of the floating node relative to the part

### FloatingNodeDirection

type: `dictionary[any]`

Local direction that the floating node moves when the Length value is changed

### FloatingNodeIsMultiJoint

type: `boolean`

Whether the floating attach node will produce a multi-joint connection

### FloatingNodeMultiJointMaxCount

type: `integer`

If FloatingNodeIsMultiJoint, the amount of joints the array should have

### FloatingNodeMultiJointOffset

type: `real`

If FloatingNodeIsMultiJoint, the distance between joints. Does nothing otherwise

## Fairing construction parameters

### FairingNode

type: `string`

ID of the attach node, other than the floater, that will yield an automatic fairing

### NoseTip

type: `real`

How "pointy" the cap panel is

### EdgeWarp

type: `real`

Roughness of the sides of the mesh.

### AberrantNormalLimit

type: `real`

Max steepness to prevent normal artifacting in the mesh

### LocalUpAxis

type: `dictionary[any]`

The "up" direction of the fairing

### Pivot

type: `dictionary[any]`

The relative center of the procedural mesh

### BaseModelTransformName

type: `string`

Name of the base object

### CapRadius

type: `real`

Max radius of the cap

### BaseRadius

type: `real`

Radius of the base object

### CloseRadius

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### MaxRadius

type: `real`

Max radius of a cross section

### SnapThreshold

type: `real`

If less than this increment, new increment will be the last valid value

### CreateShellColliders

type: `boolean`

Whether to create shell colliders or not

### NumberOfCollidersPerCrossSection

type: `integer`

Amount of colliders per cross section

### MinHeightRadiusRatio

type: `real`

Measure to avoid fairings being flat or too skinny

### CrossSectionHeightMin

type: `real`

Min allowed height per cross section

### CrossSectionHeightMax

type: `real`

Max allowed height per cross section

### ConeSweepRays

type: `integer`

Amount of rays per sweep. Used to determine payload intersection

### ConeSweepPrecision

type: `real`

Distance apart from each ray. Used to determine payload intersections

### ShouldCapOnAutoGenerate

type: `boolean`

Whether an automatically generated fairing should be capped (does nothing for ConstructionType = Custom)

## Procedural Generation Tuneables

### MassAreaRatio

type: `real`

Mass per square unit of paneling

### FairingSideCount

type: `integer`

Max amount of edges that the 3D mesh will have. More sides is more rounded but more RAM usage

### FairingLengthSnapIncrement

type: `real`

The amount of each vertical "step" increment when VAB snap is on

### FairingRadiusSnapIncrement

type: `real`

The amount of each horizontal "step" increment when VAB snap is on

### FairingSmoothingAngle

type: `real`

The smoothing angle of the fairing mesh, in degrees

### FairingThickness

type: `real`

The thickness of the fairing mesh

### FairingStartHeight

type: `real`

Position along the fairing axis on the host part where the procedural mesh starts. Zero = part prefab origin

## Procedural Controls

### AllowConstructionTypeChange

type: `boolean`

Allow change of construction mode in the PAM

### AllowFloatingNodeChange

type: `boolean`

Allow change of floating node vis in the PAM

### DefaultFairingEnabledToggle

type: `boolean`

Whether the fairing will be enabled by default

### DefaultAutoConstruction

type: `boolean`

Whether the fairing will have automatic construction set by default

### DefaultDeployType

type: `integer`

Deploy Type set by default

### DefaultFloatingNodeState

type: `boolean`

The starting state of the floating node

### LengthEditMinimum

type: `real`

The minimum distance of the Length value. Should be greater or equal to the min cross section length

### LengthEditMaximum

type: `real`

The maximum distance of the Length value

### LengthEditDefault

type: `real`

The default distance of the Length value

### StageToggleDefault

type: `boolean`

Default value for the Staging toggle

### MaxAutoFairingTargetRadius

type: `integer`

The highest part radius an auto-generated fairing should target when constructing. Part size index, [0,10] range, -1 being automatic

### MinAutoFairingTargetRadius

type: `integer`

The smallest part radius an auto-generated fairing should target when constructing. Part size index, [0,10] range, -1 being automatic

