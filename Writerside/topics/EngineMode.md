# EngineMode
<show-structure for="chapter,procedure" depth="2"/>

This module data's C# type is: `KSP.Modules.Data_Engine.EngineMode`.

This module data's element type is: `engineMode`.

This module data object has the following classes:

- `.engineID`
- `.EngineDisplayName`
- `.thrustVectorTransformName`
- `.ThrustTransformNamesMultipliers`
- `.throttleLocked`
- `.ignitionThreshold`
- `.clampPropReceived`
- `.clampPropReceivedMinLowerAmount`
- `.allowRestart`
- `.allowShutdown`
- `.shieldedCanActivate`
- `.atmosphereCurve`
- `.useThrustCurve`
- `.thrustCurve`
- `.disableUnderwater`
- `.nonThrustMotor`
- `.minThrust`
- `.maxThrust`
- `.engineType`
- `.propellant`
- `.useEngineResponseTime`
- `.engineAccelerationSpeed`
- `.engineDecelerationSpeed`
- `.GenerateHeat`
- `.HeatAtmosphereCurve`
- `.NormalizeHeatForFlow`
- `.exhaustDamage`
- `.exhaustDamageRadiusMultiplier`
- `.ExhaustDamageValue`
- `.exhaustDamageLogEvent`
- `.exhaustSplashbackDamage`
- `.exhaustDamageFalloffPower`
- `.exhaustDamageSplashbackFallofPower`
- `.exhaustDamageSplashbackMult`
- `.exhaustDamageSplashbackMaxMutliplier`
- `.exhaustDamageDistanceOffset`
- `.exhaustDamageMaxRange`
- `.exhaustDamageMaxMutliplier`
- `.exhaustShockwave`
- `.exhaustShockwaveLogEvent`
- `.exhaustShockwaveInterval`
- `.exhaustShockwaveMultiplier`
- `.exhaustShockwaveFalloffPower`
- `.exhaustShockwaveDistanceOffset`
- `.exhaustShockwaveMaxRange`
- `.exhaustShockwaveMaxMultiplier`
- `.throttleUseAlternate`
- `.throttleResponseRate`
- `.throttleIgniteLevelMult`
- `.throttleStartupMult`
- `.throttleStartedMult`
- `.throttleInstantShutdown`
- `.throttleShutdownMult`
- `.throttleInstant`
- `.throttlingBaseRate`
- `.throttlingBaseClamp`
- `.throttlingBaseDivisor`
- `.atmChangeFlow`
- `.atmCurve`
- `.useAtmCurve`
- `.velCurve`
- `.useVelCurve`
- `.CLAMP`
- `.atmCurveIsp`
- `.useAtmCurveIsp`
- `.velCurveIsp`
- `.useVelCurveIsp`
- `.flameoutBar`
- `.flowMultCap`
- `.flowMultCapSharpness`
- `.multFlow`
- `.multIsp`
- `.engineSpoolTime`
- `.engineSpoolIdle`
- `.ModeExitWaitTime`
- `.ModeExitRunningWaitTime`
- `.ModeEnterWaitTime`
- `.ModeEnterRunningWaitTime`
- `.DeactivateEngineWaitTime`
- `.ActivateEngineWaitTime`
- `.RunAnimationOnActivateDeactivate`
- `.useThrottleIspCurve`
- `.throttleIspCurveAtmStrength`
- `.throttleIspCurve`

## Uncategorized

### engineID

type: `string`

The Engine ID. should be in English.

### EngineDisplayName

type: `string`

The Engine ID display name, should be a localization tag to get localized engine mode in the UI.

This only appears in the UI for multi-mode engines.

### thrustVectorTransformName

type: `string`

The Thrust Transform name in the model for this engine mode.

This is only used to find the thrust transforms if ThrustTransformNamesMultipliers list below is left empty.

### ThrustTransformNamesMultipliers

type: `list[dictionary[any]]`

The Thrust Transform names and Thrust multipliers in the model for this engine mode.

This will override the thrustVectorTransformName field above.

### throttleLocked

type: `boolean`

Is the throttle locked in this engine mode? EG: SRB or can be changed by the player.

### ignitionThreshold

type: `real`

When will the engine fail from lack of propellants?

Default = 0.1 or at 10% of required fuel or less the engine flames out.

### clampPropReceived

type: `boolean`

Do we clamp the return percent to the min ratio (and never request more on followups) or do we request all always, and average?

### clampPropReceivedMinLowerAmount

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### allowRestart

type: `boolean`

Can the engine be restarted in this mode? eg: SRB would be false.

### allowShutdown

type: `boolean`

Can the engine be shut down in this mode? eg: SRB would be false.

### shieldedCanActivate

type: `boolean`

Can the engine be be activated when shielded from airstream? ie: inside a fairing?

### atmosphereCurve

type: `dictionary[any]`

A curve to determine loss or gain of thrust due to changes in atmosphere vs vacuum values are based on ISP to ATM Pressure

### useThrustCurve

type: `boolean`

should we use a thrust curve (based on resource remaining) ?

### thrustCurve

type: `dictionary[any]`

The thrust curve to use if useThrustCurve is true.

### disableUnderwater

type: `boolean`

Is this engine disabled when under water?

### nonThrustMotor

type: `boolean`

If set to true this engine mode will not be included in Delta-V calculations.

### minThrust

type: `real`

Minimum Thrust in kN this engine produces at 0% throttle.

### maxThrust

type: `real`

Maximum Thrust in kN this engine produces at 100% throttle.

### engineType

type: `integer`

What type of engine is this?

### propellant

type: `dictionary[any]`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### useEngineResponseTime

type: `boolean`

Whether to apply the engine acceleration and deceleration speed variables.

### engineAccelerationSpeed

type: `real`

How quickly the engine can increase its thrust production, as a fraction of maximum/second.

### engineDecelerationSpeed

type: `real`

How quickly the engine can decrease its thrust production, as a fraction of maximum/second.

## Heat Variables

### GenerateHeat

type: `boolean`

Does this engine generate heat at all?

### HeatAtmosphereCurve

type: `dictionary[any]`

Curve to adjust heat produced based on atmosphere pressure key (coordinate)

X: Atmospheric Pressure.  1 = Kerbin Atmosphere at sea level.

Y: Defines the heat production  at the given atmosphere of pressure.

### NormalizeHeatForFlow

type: `boolean`

Do we divide the heat produced by the flow multiplier to get the final flux?

i.e. do we always produce the same heat for the same throttle setting?

## Exhaust Damage Variables

### exhaustDamage

type: `boolean`

Determines whether the engine heats up and pushes on parts that are arranged in its exhaust path.

### exhaustDamageRadiusMultiplier

type: `real`

A multiplier to the exhaust damage radius.

The radius is calculated from the Part Size category * this multiplier

### ExhaustDamageValue

type: `real`

The amount of heat added from exhaust to a part, in kW.

### exhaustDamageLogEvent

type: `boolean`

Whether damage from the engine exhaust is logged for debugging.

### exhaustSplashbackDamage

type: `boolean`

Whether the engine will receive heating from the exhaust splashing back.

### exhaustDamageFalloffPower

type: `real`

Adjusts the exponent of the exhaust damage distance falloff curve.

### exhaustDamageSplashbackFallofPower

type: `real`

Adjusts the exponent of the exhaust splashback damage distance  falloff curve.

### exhaustDamageSplashbackMult

type: `real`

Adjusts the splashback damage multiplier per Newton of force produced.

### exhaustDamageSplashbackMaxMutliplier

type: `real`

The maximum amount of splashback damage that can occur.

### exhaustDamageDistanceOffset

type: `real`

Distance from the thrust transform where exhaust damage starts to occur.

### exhaustDamageMaxRange

type: `real`

Maximum range in meters that the exhaust damage is applied.

### exhaustDamageMaxMutliplier

type: `real`

Cap on the maximum multiplier to above factors that the exhaust damage can be at.

## Exhaust Shockwave Variables

### exhaustShockwave

type: `boolean`

Whether this engine creates a shockwave.

### exhaustShockwaveLogEvent

type: `boolean`

Whether damage from shockwave events are logged for debugging.

### exhaustShockwaveInterval

type: `real`

Period of time between shockwaves. A value of -1 means this shockwave always occurs.

### exhaustShockwaveMultiplier

type: `real`

Adjusts the force in Newtons a shockwave produces for damage purposes.

### exhaustShockwaveFalloffPower

type: `real`

Adjusts the exponent of the shockwave damage distance falloff curve.

### exhaustShockwaveDistanceOffset

type: `real`

Distance from the thrust transform that the shockwave starts.

### exhaustShockwaveMaxRange

type: `real`

Maximum range in meters that shockwave damage is applied.

### exhaustShockwaveMaxMultiplier

type: `real`

Cap on the maximum multiplier that shockwave damage can be at.

## AlternateThrottle Variables

### throttleUseAlternate

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleResponseRate

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleIgniteLevelMult

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleStartupMult

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleStartedMult

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleInstantShutdown

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleShutdownMult

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttleInstant

type: `boolean`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttlingBaseRate

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttlingBaseClamp

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

### throttlingBaseDivisor

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Jet Variables

### atmChangeFlow

type: `boolean`

Atmospheric density will change fuel flow (and thus thrust)

### atmCurve

type: `dictionary[any]`

Normally thrust is proportional to density, but we allow tuning.

Tuning is especially needed because there's no stratosphere, so temperature keeps decreasing and thus speed of sound keeps decreasing.

### useAtmCurve

type: `boolean`

Do we use the atm curve? If not, and atmChangeFlow is true, just use atm linearly.

### velCurve

type: `dictionary[any]`

replacement for the existing module's velocityCurve.

Note that its x value is Mach, not m/s velocity.

High-bypass turbofans will see thrust decrease steadily from static.

Low-bypass turbofans and turbojets will see thrust decrease slightly up to about 0.2 Mach then increase steadily until the limit is reached (both in terms of heat, and incoming compression vs compressor compression).

Ramjets have 0 static thrust, and do not light until 0.3 Mach or so, but once lit have steadily increasing thrust until Mach 5, when the incoming air can no longer be slowed to subsonic (combustion must be subsonic for ramjets). Thermal limits also apply, of course.

### useVelCurve

type: `boolean`

If false, we don't use the new velCurve above.

### CLAMP

type: `real`

tunable clamp. The flow multiplier will never go below this.

### atmCurveIsp

type: `dictionary[any]`

Same as atmCurve, but changes Isp not flow

### useAtmCurveIsp

type: `boolean`

Whether to use the atmCurveIsp curve above.

### velCurveIsp

type: `dictionary[any]`

Same as velCurve but changes Isp not flow.

### useVelCurveIsp

type: `boolean`

Whether to use the velCurveIsp curve above.

### flameoutBar

type: `real`

When the flow multiplier goes below this, we Flameout the engine. NOTE: THIS FIXES ASYMMETRIC FLAMEOUTS.

### flowMultCap

type: `real`

cap beyond which increases to flow multiplier aren't fully felt (start to taper off)

### flowMultCapSharpness

type: `real`

Sharpness of the tapering off of flow increase beyond cap.

### multFlow

type: `real`

Multiplier to final flow as calculated.

### multIsp

type: `real`

Multiplier to final Isp as calculated.

## Turbine Variables

### engineSpoolTime

type: `real`

This is the Turbine Spool Up time used for Spool Up Engine FX.

### engineSpoolIdle

type: `real`

There is no tooltip attached to this field, please investigate and fill in this field if you can.

## Wait Time Variables

### ModeExitWaitTime

type: `real`

The time to wait when exiting this engine mode in seconds.

### ModeExitRunningWaitTime

type: `real`

The time to wait when exiting running state in this engine mode in seconds.

### ModeEnterWaitTime

type: `real`

The time to wait when entering this engine mode in seconds.

### ModeEnterRunningWaitTime

type: `real`

The time to wait when entering running state in this engine mode in seconds.

### DeactivateEngineWaitTime

type: `real`

The time to wait when deactivating this engine mode in seconds.

### ActivateEngineWaitTime

type: `real`

The time to wait when activating this engine mode in seconds.

### RunAnimationOnActivateDeactivate

type: `boolean`

Set this to true will run the Deploy/Retract animation on Activation and Deactivation of the engine.

## Other Variables

### useThrottleIspCurve

type: `boolean`

Should we use the Throttle ISP curve?

### throttleIspCurveAtmStrength

type: `dictionary[any]`

Modifies Isp based on throttle.

Time is pressure in atm, value is how much throttling affects Isp

(i.e. Isp = input * Lerp(1, throttleIspCurve, throttleIspCurveAtmStrength)

### throttleIspCurve

type: `dictionary[any]`

Modifies Isp based on throttle. time is throttle, value is multiplier to Isp

