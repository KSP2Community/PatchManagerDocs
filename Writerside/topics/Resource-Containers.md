# Resource Containers

The class of resource containers in C# is: `KSP.Sim.ResourceSystem.ContainedResourceDefinition`.
The element type of resource containers is: The name of the resource.
Resource containers have the following classes:
- `.name`
- `.capacityUnits`
- `.initialUnits`
- `.NonStageable`

## name

type: `string`

The name of the resource being stored (e.g. `Methalox`)

## capacityUnits

type: `real`

The capacity of the resource

## initialUnits

type: `real`

How much of the resource is there to start

## NonStageable

type: `boolean`

Does this contain a non-stageable resource?