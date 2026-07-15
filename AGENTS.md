# AGENTS.md

## Project Overview

ExoSol is an early-stage smooth-voxel automation survival game spanning
planetary surfaces and space. It is planned for development in C# using the
custom ExoG™ game engine. ExoG™ uses raylib as a backend through raylib.cs.

The project emphasizes survival as infrastructure, automation with purpose,
and the progression from precarious shelter to a livable home among the stars.
Treat the repository as both a game project and a public example of clean,
maintainable game architecture.

## Technology

- Use C# for the project unless C++ becomes necessary for native integration.
- Use ExoG™ as ExoSol's game engine.
- Use raylib as an ExoG™ backend through raylib.cs.
- Isolate all direct raylib dependencies to ExoG™'s raylib Platform Module in
  the `ExoG.Platform.Raylib` assembly.
- Use NUnit for automated tests.
- Use Moq when test doubles materially improve a test; prefer simple fakes or
  real objects when they make a test clearer.
- Keep NUnit and Moq confined to test assemblies. Production assemblies must
  not reference either package.

The build system and complete repository structure are not yet settled. Do not
assume a dependency manager, directory layout, or additional framework until
the repository establishes one. Document foundational choices here and in the
README as appropriate.

## Design Principles

- Preserve the connection between planetary and space play; avoid treating
  them as unrelated game modes without a deliberate design reason.
- Treat survival needs as systems that can be addressed through building,
  logistics, and automation.
- Support progression from survival to comfort, community, and quality of life.
- Make automation serve exploration, settlement, and the creation of livable
  environments rather than existing only for its own expansion.
- Treat smooth-voxel terrain as a central gameplay and technical system.
- Prefer coherent, achievable increments over attempting the entire intended
  scope at once.

## Architecture Guidelines

- Keep simulation and gameplay rules separate from rendering, input, audio,
  and other platform-facing concerns.
- Keep raylib-specific code inside ExoG™'s `ExoG.Platform.Raylib` assembly;
  other production assemblies must not reference raylib.cs directly.
- Expose platform capabilities to the rest of the application through focused,
  engine-independent interfaces and data types.
- Treat authoritative game state as distinct from its visual representation.
- Keep systems focused, data ownership clear, and lifecycle behavior explicit.
- Design planetary and space coordinate systems, scale transitions, and
  numerical precision deliberately; do not introduce ad hoc conversions.
- Keep voxel generation, storage, meshing, editing, persistence, and rendering
  responsibilities separable even if early prototypes implement only a subset.
- Avoid premature abstraction, but do not bind core simulation rules directly
  to rendering APIs for convenience.
- Prefer incremental extensions to established architecture over broad
  rewrites.

## raylib Guidelines

- Use raylib as an ExoG™ backend through raylib.cs and only within
  `ExoG.Platform.Raylib`.
- Do not leak raylib.cs types across the Platform Module boundary.
- Use the Platform Module for raylib-backed graphics, input, audio, windowing,
  and other platform services according to the architecture established by the
  project.
- Keep drawing code free of gameplay side effects.
- Balance every acquired resource with the appropriate cleanup operation.
- Centralize ownership of windows, render targets, shaders, models, textures,
  audio, and other native resources.
- Do not scatter frame-loop ordering or global initialization across unrelated
  modules.
- Keep per-frame allocations and CPU-to-GPU transfers visible and intentional,
  especially in voxel rendering paths.

## Code and Documentation Style

Follow `.editorconfig` and conventions already present in nearby files.

- Use four spaces by default and two spaces in JSON, YAML, and Markdown files.
- Prefer explicit, readable code over clever or highly compressed code.
- Use descriptive names that reflect game and simulation concepts.
- Keep functions focused and modules reasonably small.
- Aim for 80-column readability where practical; treat 120 columns as the
  upper limit.
- Add comments when they explain intent, constraints, invariants, or non-obvious
  behavior. Do not narrate straightforward code.
- Avoid unrelated formatting changes.
- Update documentation when a change alters documented behavior, architecture,
  controls, setup, or design intent.

## C# Style

- Use file-scoped namespaces.
- Keep nullable reference types enabled and avoid suppressing nullable warnings
  without a clear reason.
- Prefer explicit, readable code over clever or highly compressed code.
- Use descriptive names that reflect domain concepts.
- Keep methods focused and classes reasonably small.
- Follow the formatting and member-ordering style of the file being edited.
- Do not introduce primary constructors unless the project convention changes.
- Keep C++ code limited to integration work that cannot reasonably be
  implemented in C#.

## Testing and Verification

- Add or update tests when changing behavior that can be tested independently
  of graphics or platform integration.
- Prefer deterministic tests for procedural generation and simulation systems.
- Write tests with NUnit and follow the conventions established by nearby test
  code.
- Use Moq at module boundaries when interaction-based verification is useful;
  do not mock concrete domain behavior merely to isolate every class.
- Keep NUnit, Moq, and all test helpers in test assemblies.
- Test observable behavior and invariants rather than private implementation
  details.
- Validate resource cleanup and lifecycle behavior where native resources are
  involved.
- Run the most focused relevant checks first, followed by broader builds and
  tests when practical.
- Do not claim a build, test, or runtime check passed unless it was actually run
  successfully.

Update this section with concrete build, test, formatting, and run commands
once the toolchain has been selected.

## Working Practices

- Inspect relevant code, tests, assets, and documentation before making
  changes.
- Check for existing uncommitted work before editing when the project is under
  version control.
- Preserve user changes and do not revert, overwrite, or reformat unrelated
  work.
- Keep changes limited to the requested scope.
- Do not add dependencies unless they materially simplify the requested work
  and fit the architecture.
- Do not commit generated build output, caches, or local configuration unless
  the repository explicitly requires it.
- Do not create commits, branches, tags, or pull requests unless explicitly
  requested.
- Do not modify licensing, attribution, trademark, or source-availability
  language without explicit direction.
- Never use destructive version-control operations unless explicitly
  authorized.

## Commit Messages

When explicitly asked to create a commit, follow the convention established by
the repository history. Until a history exists:

- Write the summary in lowercase imperative form, such as `add`, `create`,
  `implement`, `update`, `refactor`, or `remove`.
- Describe the outcome directly without a Conventional Commit prefix such as
  `feat:` or `fix:`.
- Do not end the summary with a period.
- Keep the summary concise but specific.
- Add a body only when it helps explain context, rationale, or tradeoffs.

## Verification and Handoff

Before declaring implementation work complete:

1. Review the final changes for accidental or unrelated edits.
2. Build the affected project when a build system is available.
3. Run relevant automated tests when a test system is available.
4. Perform focused runtime checks when the change affects rendering, input,
   voxel behavior, world transitions, or resource lifecycles.
5. Report what changed, what was verified, and any remaining limitations.
