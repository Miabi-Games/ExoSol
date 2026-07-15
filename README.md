# ExoSol

**ExoSol** is a smooth-voxel automation survival game spanning planetary
surfaces and space, with advanced technology and play across both terrestrial
and orbital environments.

The game is planned for development in **C#** using the custom **ExoG™** game
engine, with **raylib** as its backend through **raylib.cs**. Its current source
code is publicly available under the MIT License.

> The factory is not only for production. It is how the player makes a home
> among the stars.

## Project Status

ExoSol is in early development. The design and technical foundation are still
being established, so features, architecture, and scope may change rapidly.

The project is intended to explore:

- smooth-voxel terrain and world interaction
- planetary exploration, survival, and settlement
- spaceflight and play beyond planetary surfaces
- automation, logistics, and resource processing
- the growth of shelters into comfortable, sustainable homes
- scalable, maintainable game and simulation architecture

## Core Concept

ExoSol combines survival pressure, automation progression, settlement building,
and exploration across planets and space.

Early play should feel physical and vulnerable. The player gathers resources,
shapes terrain, establishes shelter, and builds the infrastructure needed to
survive in unfamiliar environments. Over time, manual work gives way to
machines, logistics networks, environmental systems, and increasingly capable
settlements.

Survival is only the beginning. A successful settlement should grow beyond
meeting minimum needs to provide safety, comfort, routine, beauty, privacy,
community, and purpose. The player's creations should not only keep people
alive; they should make distant worlds worth living on.

Space expands that progression beyond a single surface. Planetary and space
play should form parts of one connected experience, with exploration,
transportation, industry, and settlement operating across different
environments and scales.

## Design Goals

- **Survival as infrastructure**  
  Food, shelter, safety, and environmental protection are systems the player
  can solve through construction and automation.

- **Home as progression**  
  Settlements should develop from precarious outposts into places where people
  can live, belong, and thrive.

- **Wants beyond needs**  
  Once survival is secure, comfort, dignity, beauty, social life, and other
  quality-of-life concerns should matter.

- **A smooth-voxel world**  
  Terrain should be continuous and shapeable rather than limited to a grid of
  visible blocks.

- **Planets and space**  
  Surface exploration, spaceflight, and off-world construction should belong
  to a connected game world and progression.

- **Automation with purpose**  
  Machines and logistics should help sustain life, expand settlements, and
  make hostile environments livable.

- **A strong technical foundation**  
  The broader scope requires clear boundaries, testable systems, and an
  architecture that can grow without obscuring the game's core ideas.

## Technology

ExoSol is planned for development in C# using the custom ExoG™ game engine.
ExoG™ will use [raylib](https://www.raylib.com/) as a backend through the
raylib.cs bindings. Direct raylib integration will be isolated to ExoG™'s
raylib Platform Module in the `ExoG.Platform.Raylib` assembly.

Automated tests will use NUnit, with Moq available when mocking is appropriate.
Both are test-only dependencies and will not be used by production assemblies.
C++ may be introduced only if it becomes necessary for native integration.

The build process and detailed project structure will be documented as they
are established.

## Repository Goals

This repository is both a game project and a public development showcase. It
is intended to demonstrate:

- game and simulation architecture
- smooth-voxel world technology
- gameplay systems and automation design
- readable, maintainable code
- iterative prototyping and technical documentation

## Source Availability

The source code currently published in this repository is available under the
MIT License and may continue to be used under that license.

Public development of ExoSol is experimental and should not be understood as a
commitment to publish the source code of every future version. Future
development, releases, or portions of the project may use a different
source-availability or distribution model.

## License

The contents currently published in this repository are released under the MIT
License. See [LICENSE](LICENSE) for details.

This license continues to apply to versions already released under it. It does
not constitute a promise that future versions of ExoSol, or all future project
assets and source code, will be published under the same license or made
publicly available.

ExoSol, ExoG™, and Miabi Games™ are names associated with Mia B. Regula, doing
business as Miabi Games™.
