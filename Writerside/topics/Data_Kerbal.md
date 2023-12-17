# Data_Kerbal
<show-structure for="chapter,procedure" depth="2"/>

This module data's C# type is: `KSP.Modules.Data_Kerbal`.

This module data's element type is: `Data_Kerbal`.

This module data object has the following classes:

- `.IsJetpackEquipped`
- `.JetpackMoveForce`
- `.JetpackRotateTorque`
- `.JetpackRotateMaxAngularSpeed`
- `.JetpackRotateResetEnabled`
- `.JetpackRotateResetAngularSpeedThreshold`
- `.JetpackRotateResetAngularSpeed`
- `.JetpackAlignToCameraEnabled`
- `.JetpackAlignToCameraMinAngle`
- `.JetpackAlignToCameraMaxAngle`
- `.JetpackAlignToCameraMinRotateInput`
- `.JetpackAlignToCameraMaxRotateInput`
- `.JetpackMoveForceOffset`
- `.JetpackRotateTorqueOffset`
- `.JetpackThrustLiquidDragScalar`
- `.JetpackThrustLiquidAngularDragScalar`
- `.JetpackPropellantDefinition`
- `.JetpackAtmosphereCurve`
- `.WalkRotateAngularSpeed`
- `.WalkRotateChangeAngularSpeed`
- `.WalkMoveSpeed`
- `.WalkMoveAnimationSpeed`
- `.WalkMoveStrafeSpeed`
- `.WalkMoveStrafeAnimationSpeed`
- `.RunMoveSpeed`
- `.RunMoveAnimationSpeed`
- `.RunRotateAngularSpeed`
- `.RunRotateChangeAngularSpeed`
- `.RotateDesiredDirectionEqualAngle`
- `.NormalToSprintLerpSpeed`
- `.MoveCameraUpFlipMinAngle`
- `.MoveDirectionRotateFallbackAngle`
- `.SwimSlowMoveSpeed`
- `.SwimSlowMoveAnimationSpeed`
- `.SwimSlowMoveForceCurve`
- `.SwimMoveForceOffset`
- `.SwimFastMoveSpeed`
- `.SwimFastMoveAnimationSpeed`
- `.SwimFastMoveForceMagnitudeMultiplier`
- `.SwimFastRotateSpeed`
- `.SwimFloatSurfaceUpOffset`
- `.SwimMinDepth`
- `.GroundSpherecastUpOffset`
- `.GroundSpherecastPresentLength`
- `.GroundSpherecastPresentRadius`
- `.GroundSpherecastFutureLength`
- `.GroundSpherecastFutureRadius`
- `.GroundSpherecastFutureMoveOffset`
- `.GroundAndSeaHighAltitude`
- `.SlopeMoveGroundMaxAngle`
- `.SlopeMoveUpDetectAngle`
- `.UprightRotateAngularSpeed`
- `.UprightRotateChangeAngularSpeed`
- `.JumpForceMagnitudeCurve`
- `.JumpRunMoveForceMagnitudeMultiplier`
- `.JumpMoveAngle`
- `.JumpMinStateDuration`
- `.JumpMaxStateDuration`
- `.JumpInitialForceDuration`
- `.JumpExtendForceDuration`
- `.JumpRotateAngularSpeed`
- `.JumpRotateChangeAngularSpeed`
- `.FlagLocalPositionOffset`
- `.DisableEVAAndFlightInteractInputs`
- `.ClimbStartDockDuration`
- `.ClimbStopDockDuration`
- `.ClimbCapsuleRadius`
- `.ClimbCapsuleHeight`
- `.ClimbMoveSpeed`
- `.ClimbMoveAnimationSpeed`
- `.ClimbMinObjectHeight`
- `.StepMinHeight`
- `.StepMaxHeight`
- `.StepTopMaxAngle`
- `.StepTopRaycastForwardOffset`
- `.StepTopRaycastUpOffset`
- `.StepTopRaycastLength`
- `.StepFrontRaycastForwardOffset`
- `.StepFrontRaycastUpOffset`
- `.StepFrontRaycastLength`
- `.StepUnobstructedRaycastForwardOffset`
- `.StepUnobstructedRaycastUpOffset`
- `.StepUnobstructedRaycastLength`
- `.StepClamberHeightInterpValue`
- `.StepClamberDuration`
- `.LadderTopMaxHeight`
- `.LadderTopMaxAngle`
- `.LadderTopRaycastForwardOffset`
- `.LadderTopRaycastUpOffset`
- `.LadderTopRaycastLength`
- `.LadderUnobstructedRaycastForwardOffset`
- `.LadderUnobstructedRaycastUpOffset`
- `.LadderUnobstructedRaycastLength`
- `.LadderTopClamberHeightInterpValue`
- `.LadderTopClamberDelayDuration`
- `.LadderTopClamberDuration`

## Jetpack

### IsJetpackEquipped

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### JetpackMoveForce

type: `real`

How much Move force in kN the Jetpack produces at 100% throttle at atmospheric pressure of 0.

### JetpackRotateTorque

type: `real`

How much Rotate torque in kN.m the Jetpack produces at 100% throttle at atmospheric pressure of 0.

### JetpackRotateMaxAngularSpeed

type: `real`

Max Speed in degrees per second at which Jetpack Rotate Torque can accelerate the angular velocity to, when Rotate input is being applied.

### JetpackRotateResetEnabled

type: `boolean`

Whether Jetpack Rotate Reset is enabled. If enabled, the Jetpack will automatically try to stop rotation, gradually, when no rotate input is pressed.

### JetpackRotateResetAngularSpeedThreshold

type: `real`

Speed in degrees per second above which Jetpack Rotate Reset kicks in.

### JetpackRotateResetAngularSpeed

type: `real`

Speed in degrees per second at which Jetpack Rotate gradually settles to zero angular velocity, when no Rotate input is being applied.

### JetpackAlignToCameraEnabled

type: `boolean`

Whether Jetpack Align to Camera is enabled. If enabled Rotate Input is applied to align the Character direction to Camera direction. Uses Jetpack Rotate Torque thrusts for said alignment. Occurs when Jetpack In-Use while falling.

### JetpackAlignToCameraMinAngle

type: `real`

Angle in degrees about Camera direction to align Character direction to Camera direction, above which the Align to Camera feature kicks in.

### JetpackAlignToCameraMaxAngle

type: `real`

Angle in degrees about Camera direction to align Character direction to Camera direction, at and above which the Align to Camera feature will provide JetpackAlignToCameraMaxRotateInput input delta. Reduce this angle to make things feel snappier.

### JetpackAlignToCameraMinRotateInput

type: `real`

Minimum normalized value [0, 1] to apply as Rotate Input to align Character direction to Camera direction. This will be multiplied by the PAM JetpackThrustForcePercentage to affect the Rotate Torque accordingly.

### JetpackAlignToCameraMaxRotateInput

type: `real`

Maximum normalized value [0, 1] to apply as Rotate Input to align Character direction to Camera direction. This will be multiplied by the PAM JetpackThrustForcePercentage to affect the Rotate Torque accordingly.

### JetpackMoveForceOffset

type: `real`

The local-space offset, applied to each coordinate axis, at which Move forces are applied. This offset is from the object CoM.

### JetpackRotateTorqueOffset

type: `real`

The local-space offset, applied to each coordinate axis, at which Rotate torques are applied.

### JetpackThrustLiquidDragScalar

type: `real`

Rigidbody Drag scalar to apply when the Jetpack is thrusting in a liquid or underwater. Use this to tune ease of thrusting while underwater.

### JetpackThrustLiquidAngularDragScalar

type: `real`

Rigidbody Angular Drag scalar to apply when the Jetpack is thrusting in a liquid or underwater. Use this to tune ease of thrusting while underwater.

### JetpackPropellantDefinition

type: `dictionary[any]`

Propellant that the Jetpack consumes while running.

### JetpackAtmosphereCurve

type: `dictionary[any]`

A curve to determine loss or gain of thrust due to changes in atmosphere vs vacuum values are based on ISP to ATM Pressure.

## Walk/Run

### WalkRotateAngularSpeed

type: `real`

Walk Rotate angular speed in degrees per second.

### WalkRotateChangeAngularSpeed

type: `real`

Walk Rotate change angular speed in degrees per second. I.e., how quickly it approaches the Angular Speed.

### WalkMoveSpeed

type: `real`

Walk Move speed in meters per second. This is the gameplay facing speed. Once the other animation speed field is tuned correctly, you can increase or decrease this value freely without foot sliding.

### WalkMoveAnimationSpeed

type: `real`

Walk Move Animation speed in meters per second. This animator provided value will be used to avoid foot sliding, when applying the gameplay facing speed. If you do not know what this value should be, and don't mind foot sliding temporarily, keep it at 0.

### WalkMoveStrafeSpeed

type: `real`

Walk Move Strafe speed in meters per second. This is the gameplay facing speed. Once the other animation speed field is tuned correctly, you can increase or decrease this value freely without foot sliding.

### WalkMoveStrafeAnimationSpeed

type: `real`

Walk Move Strafe Animation speed in meters per second. This animator provided value will be used to avoid foot sliding, when applying the gameplay facing speed. If you do not know what this value should be, and don't mind foot sliding temporarily, keep it at 0.

### RunMoveSpeed

type: `real`

Run Move speed in meters per second. This is the gameplay facing speed. Once the other animation speed field is tuned correctly, you can increase or decrease this value freely without foot sliding.

### RunMoveAnimationSpeed

type: `real`

Run Move Animation speed in meters per second. This animator provided value will be used to avoid foot sliding, when applying the gameplay facing speed. If you do not know what this value should be, and don't mind foot sliding temporarily, keep it at 0.

### RunRotateAngularSpeed

type: `real`

Run Rotate angular speed in degrees per second.

### RunRotateChangeAngularSpeed

type: `real`

Run Rotate change angular speed in degrees per second. I.e., how quickly it approaches the Angular Speed.

### RotateDesiredDirectionEqualAngle

type: `real`

Angle in degrees within which the current direction to desired direction angle needs to be for the alignment to be considered complete.

### NormalToSprintLerpSpeed

type: `real`

Value multiplied by delta time to speed up/slow down the lerp between normal movement and running/sprinting

### MoveCameraUpFlipMinAngle

type: `real`

Minimum angle in degrees above which we consider the Camera upside down and flip move left and move right directions. This is the angle between the following directions: [GroundContactNormal], [CameraUp].

### MoveDirectionRotateFallbackAngle

type: `real`

Equal and opposite angle in degrees under which we rotate the camera-relative move input direction by 90 degrees to improve the player's navigation experience, and also to prevent cross product from approaching zero magnitude, which would have resulted in an invalid move input direction. This is the angle between the following directions: [MoveOnGroundDirection], [GroundContactNormal].

## Swim

### SwimSlowMoveSpeed

type: `real`

Swim Slow Move speed in meters per second. This is the gameplay facing speed. Once the other animation speed field is tuned correctly, you can increase or decrease this value freely without sliding.

### SwimSlowMoveAnimationSpeed

type: `real`

Swim Slow Move Animation speed in meters per second. This animator provided value will be used to avoid sliding, when applying the gameplay facing speed. If you do not know what this value should be, and don't mind sliding temporarily, keep it at 0.

### SwimSlowMoveForceCurve

type: `dictionary[any]`

Magnitude of SwimSlowMove Force in kN. Where, X-axis: GravityMultiplier; Y-axis: ForceMagnitude.

### SwimMoveForceOffset

type: `real`

The local-space offset, applied to each coordinate axis, at which Swim Move force is applied. This offset is from the object CoM.

### SwimFastMoveSpeed

type: `real`

Swim Fast Move speed in meters per second. This is the gameplay facing speed. Once the other animation speed field is tuned correctly, you can increase or decrease this value freely without sliding.

### SwimFastMoveAnimationSpeed

type: `real`

Swim Fast Move Animation speed in meters per second. This animator provided value will be used to avoid sliding, when applying the gameplay facing speed. If you do not know what this value should be, and don't mind sliding temporarily, keep it at 0.

### SwimFastMoveForceMagnitudeMultiplier

type: `real`

Magnitude multiplier of SwimSlowMove Force that is applied when the Character is swimming and they have the run input pressed.

### SwimFastRotateSpeed

type: `real`

Swim Fast Rotate speed in degrees per second.

### SwimFloatSurfaceUpOffset

type: `real`

Swim Up offset from the Swim Surface to help determine target position to float to. Use this if the character's origin is at their feet and we want floating position should be offset downwards.

### SwimMinDepth

type: `real`

Minimum depth in meters for the Character to be in the Swim state.

## Ground

### GroundSpherecastUpOffset

type: `real`

How high up in meters from character pivot upwards along HorizonUp should the Ground spherecast originate from. This physics spherecast is responsible for ground detection.

### GroundSpherecastPresentLength

type: `real`

Length in meters of the physics spherecast of the 'In the Present' Ground spherecast. This physics spherecast occurs downwards opposite to HorizonUp, is positioned such that it is not offset by the move input direction.

### GroundSpherecastPresentRadius

type: `real`

Radius in meters of the physics spherecast of the 'In the Present' Ground spherecast. This physics spherecast occurs downwards opposite to HorizonUp, is positioned such that it is not offset by the move input direction.

### GroundSpherecastFutureLength

type: `real`

Length in meters of the physics spherecast of the 'In the Future' Ground spherecast. This physics spherecast occurs downwards opposite to HorizonUp, is positioned such that it is offset by a fixed amount along the move input direction.

### GroundSpherecastFutureRadius

type: `real`

Radius in meters of the physics spherecast of the 'In the Future' Ground spherecast. This physics spherecast occurs downwards opposite to HorizonUp, is positioned such that it is offset by a fixed amount along the move input direction.

### GroundSpherecastFutureMoveOffset

type: `real`

Offset in meters along the character velocity direction during character movement that the 'In the Future' Ground spherecast downwards opposite to HorizonUp is positioned.

### GroundAndSeaHighAltitude

type: `real`

Altitude above both Sea Level and Ground Level the character needs to be to be considered Above High Altitude or In-Orbit.

## Slope

### SlopeMoveGroundMaxAngle

type: `real`

Max angle in degrees up to which Move velocity is applied along the Slope incline. This is the max allowed angle between the following directions: [GroundContactNormal], [HorizonUp].

### SlopeMoveUpDetectAngle

type: `real`

Angle in degrees under which Move Up Slope is detected. This is the angle between the following directions: [HorizonUp], [MoveOnGroundDirection].

## Upright

### UprightRotateAngularSpeed

type: `real`

Upright Rotate correction angular speed in degrees per second.

### UprightRotateChangeAngularSpeed

type: `real`

Upright Rotate correction change angular speed in degrees per second. I.e., how quickly it approaches the Angular Speed.

## Jump

### JumpForceMagnitudeCurve

type: `dictionary[any]`

Magnitude of Jump Force that is continually applied during the Initial and Extend sub-states of Jump, if sub-state conditions are met. Where, X-axis: GravityMultiplier; Y-axis: ForceMagnitude.

### JumpRunMoveForceMagnitudeMultiplier

type: `real`

Magnitude multiplier of Jump Force that is applied when the Character is running when they press the Jump input.

### JumpMoveAngle

type: `real`

When Jump is triggered during move, the angle in degrees by which to rotate the move input direction upwards in Character local-space. This helps make the Character jump in some angled move direction when moving, as opposed to jumping straight up when stationary.

### JumpMinStateDuration

type: `real`

Minimum duration in seconds for which the Jumping CharacterState should be true. The time starts the moment the 'DoJumpImpulse' Animation Event is received.

### JumpMaxStateDuration

type: `real`

Maximum duration in seconds for which the Jumping CharacterState should be true. The time starts the moment the Jump Handler starts.

### JumpInitialForceDuration

type: `real`

Duration in seconds over which the Jump force is applied during the Initial sub-state of Jump.

### JumpExtendForceDuration

type: `real`

Duration in seconds over which the Jump force is applied during the Extend sub-state of Jump.

### JumpRotateAngularSpeed

type: `real`

Jump Rotate angular speed in degrees per second. This is used to align the character's forward direction to the jump direction, when not strafing.

### JumpRotateChangeAngularSpeed

type: `real`

Jump Rotate change angular speed in degrees per second. I.e., how quickly it approaches the Angular Speed. This is used to align the character's forward direction to the jump direction, when not strafing.

## Flag

### FlagLocalPositionOffset

type: `dictionary[any]`

Local position offset added when instantiating the flag prefab.

### DisableEVAAndFlightInteractInputs

type: `boolean`

Whether EVA and Flight Interact inputs be disabled while the plant flag animation is playing.

## Climb

### ClimbStartDockDuration

type: `real`

Duration in seconds to dock the Kerbal to the Ladder when Climb is started. I.e., the duration of the StartClimbDock sub-state of Climb.

### ClimbStopDockDuration

type: `real`

Duration in seconds to dock the Kerbal to the Ladder when Climb is stopped. I.e., the duration of the StopClimbUndock sub-state of Climb.

### ClimbCapsuleRadius

type: `real`

Radius of the character's Capsule Collider when they are in the Climb CharacterStateHandler.

### ClimbCapsuleHeight

type: `real`

Height of the character's Capsule Collider when they are in the Climb CharacterStateHandler.

### ClimbMoveSpeed

type: `real`

Climb Move speed in meters per second. This is the gameplay facing speed. Once the other animation speed field is tuned correctly, you can increase or decrease this value freely without foot/hand sliding.

### ClimbMoveAnimationSpeed

type: `real`

Climb Move Animation speed in meters per second. This animator provided value will be used to avoid foot sliding, when applying the gameplay facing speed. If you do not know what this value should be, and don't mind foot/hand sliding temporarily, keep it at 0.

### ClimbMinObjectHeight

type: `real`

Minimum height of a climbable object. Applies to very small Ladders where the climbable surface is too small compared to the character capsule dimensions. We still want the player to experience climbing height adjustments as they provide input for these small climbable objects.

## Step Clamber

### StepMinHeight

type: `real`

Minimum height for Step detection. A detected step must be above this height to be considered a valid Step. Valid Steps will show an Interact which performs a Step Clamber on use.

### StepMaxHeight

type: `real`

Maximum height for Step detection. A detected step must be below this height to be considered a valid Step. Valid Steps will show an Interact which performs a Step Clamber on use.

### StepTopMaxAngle

type: `real`

Max angle in degrees up to which a contact found by Step 'Top' detection is considered valid. This is the max allowed angle between the following directions: [StepTopContactNormal], [HorizonUp].

### StepTopRaycastForwardOffset

type: `real`

Distance offset along Character Forward in meters to help determine the Step 'Top' physics raycast position. The physics raycast direction will be downwards opposite to Character Up.

### StepTopRaycastUpOffset

type: `real`

Distance offset along Character Up in meters to help determine the Step 'Top' physics raycast position. The physics raycast direction will be downwards opposite to Character Up.

### StepTopRaycastLength

type: `real`

Length in meters of the physics raycast of the Step 'Top' physics raycast. The physics raycast direction will be downwards opposite to Character Up.

### StepFrontRaycastForwardOffset

type: `real`

Distance offset along Character Forward in meters to help determine the Step 'Front' physics raycast position. The physics raycast direction will be the Character Forward.

### StepFrontRaycastUpOffset

type: `real`

Distance offset along Character Up in meters to help determine the Step 'Front' physics raycast position. The physics raycast direction will be the Character Forward.

### StepFrontRaycastLength

type: `real`

Length in meters of the physics raycast of the Step 'Front' physics raycast. The physics raycast direction will be the Character Forward.

### StepUnobstructedRaycastForwardOffset

type: `real`

Distance offset along Character Forward in meters to help determine the Step 'Unobstructed' physics raycast position. The physics raycast direction will be the Character Forward.

### StepUnobstructedRaycastUpOffset

type: `real`

Distance offset along Character Up in meters to help determine the Step 'Unobstructed' physics raycast position. The physics raycast direction will be the Character Forward.

### StepUnobstructedRaycastLength

type: `real`

Length in meters of the physics raycast of the Step 'Unobstructed' physics raycast. The physics raycast direction will be the Character Forward.

### StepClamberHeightInterpValue

type: `real`

Percentage as normalized [0, 1] for the interpolation value at which we reach the Step's Height in the Character Up direction only, before proceeding in the Character Forward direction to reach the final valid Step 'Top' position thereafter. E.g., Choose a percentage somewhere in the middle to break apart this up-to-forward motion relatively evenly.

### StepClamberDuration

type: `real`

Duration in seconds to dock the Kerbal to the valid Step 'Top' position. I.e., the duration of the ClamberingSubState sub-state of Climb for Step clambering, specifically.

## Ladder Top Clamber

### LadderTopMaxHeight

type: `real`

Maximum height for Ladder 'Top' platform detection, by repurposing the Step detection system with different data. A detected height must be below this height to be considered a valid Ladder Top. Valid Ladder Top will show an Interact which performs a Ladder Top Clamber to the platform on use.

### LadderTopMaxAngle

type: `real`

Max angle in degrees up to which a contact found by Step 'Top' detection is considered valid, for Ladder Top Clamber purposes. This is the max allowed angle between the following directions: [StepTopContactNormal], [CharacterUp].

### LadderTopRaycastForwardOffset

type: `real`

Distance offset along Character Forward in meters to help determine the Step 'Top' physics raycast position, for Ladder Top Clamber purposes. The physics raycast direction will be downwards opposite to Character Up, and originates from Character position before Forward and Up offsets are applied.

### LadderTopRaycastUpOffset

type: `real`

Distance offset along Character Up in meters to help determine the Step 'Top' physics raycast position, for Ladder Top Clamber purposes. The physics raycast direction will be downwards opposite to Character Up, and originates from Character position before Forward and Up offsets are applied.

### LadderTopRaycastLength

type: `real`

Length in meters of the physics raycast of the Step 'Top' physics raycast, for Ladder Top Clamber purposes. The physics raycast direction will be downwards opposite to Character Up, and originates from Character position before Forward and Up offsets are applied.

### LadderUnobstructedRaycastForwardOffset

type: `real`

Distance offset along Character Forward in meters to help determine the Step 'Unobstructed' physics raycast position, for Ladder Top Clamber purposes. The physics raycast direction will be the Character Forward, and originates from CharacterCapsuleBottomPos position before Forward and Up offsets are applied.

### LadderUnobstructedRaycastUpOffset

type: `real`

Distance offset along Character Up in meters to help determine the Step 'Unobstructed' physics raycast position, for Ladder Top Clamber purposes. The physics raycast direction will be the Character Forward, and originates from CharacterCapsuleBottomPos position before Forward and Up offsets are applied.

### LadderUnobstructedRaycastLength

type: `real`

Length in meters of the physics raycast of the Step 'Unobstructed' physics raycast, for Ladder Top Clamber purposes. The physics raycast direction will be the Character Forward, and originates from CharacterCapsuleBottomPos position before Forward and Up offsets are applied.

### LadderTopClamberHeightInterpValue

type: `real`

Percentage as normalized [0, 1] for the interpolation value at which we reach the Step's Height in the Character Up direction only, for Ladder Top Clamber purposes, before proceeding in the Character Forward direction to reach the final valid Step 'Top' position thereafter. E.g., Choose a percentage somewhere in the middle to break apart this up-to-forward motion relatively evenly.

### LadderTopClamberDelayDuration

type: `real`

Duration in seconds of the delay before the clamber. I.e., the duration of a delay within the ClamberingSubState sub-state of Climb for Ladder Top clambering, specifically. Use this when a custom Climb to Clamber animation transition doesn't exist.

### LadderTopClamberDuration

type: `real`

Duration in seconds to dock the Kerbal to the valid Step 'Top' position. I.e., the duration of the ClamberingSubState sub-state of Climb for Ladder Top clambering, specifically.

