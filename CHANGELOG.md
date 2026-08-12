# Governance release history

This history records released governance behavior, not DevSystem application
or source-code releases. Published release meaning is append-only; material
changes require a new governance version.

## v1.3.0-governance-lifecycle — 2026-08-12

### Reason

Establish a sustainable governance lifecycle for generated projects and remove
governance version from Product Owner configuration.

### Material changes

- Made governance version DevSystem-owned distribution metadata.
- Added installed baseline metadata to generated projects.
- Added optional, read-only upstream release discovery.
- Preserved each project repository as the authority for active governance.
- Defined explicit authorization and migration-aware safety for synchronization.
- Distinguished upstream-managed, project-configured, project-owned, and mixed
  governance state.

### Affected governance areas

Baseline and release manifests, generated `.devsystem/governance.json`,
generator validation and reporting, repository authority rules, semantic
governance triggers, workflow guidance, and architecture documentation.

### Compatibility and migration

This is the initial public distribution release. No migration from an earlier
baseline is declared or supplied. Projects on another baseline require manual
review. The empty `migrates_from` array and null `migration` value in
`releases.json` are authoritative.
