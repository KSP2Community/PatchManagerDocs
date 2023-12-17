# Data_ActiveRadiator

This module data's C# type is: `KSP.Modules.Data_ActiveRadiator`.

This module data's element type is: `Data_ActiveRadiator`.

This module data object has the following classes:

- `.RadiatorDirection`
- `.ProceduralRadiatorFluxPerAreaUnit`

## RadiatorDirection

type: `integer`

This is the axis direction we should use to calculate the area of the radiator for procedural radiators.

Will not be used if the radiator is NOT procedural.

## ProceduralRadiatorFluxPerAreaUnit

type: `real`

This is the amount of flux removed from the radiator calculated from the area of the radiator for procedural radiators.

Will not be used if the radiator is NOT procedural.

This will be used to calculate the fluxRemoved value.

