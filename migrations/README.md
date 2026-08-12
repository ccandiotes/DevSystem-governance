# Governance migrations

This directory contains only migrations explicitly declared by
`../releases.json`.

A future migration uses a version-specific path named by the target release's
`migration` value and documents its exact source baseline or baselines,
affected files, preservation rules, transformation, validation, and safe
failure behavior. A migration file must not exist unless the manifest declares
the corresponding supported path, and a non-null manifest migration must
resolve to published material here.

No migration is defined for the initial
`v1.3.0-governance-lifecycle` release.
