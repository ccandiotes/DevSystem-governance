# Governed handoff transport

Substantial governed payloads use repository-backed handoff branches rather
than conversational copy/paste. Active Issue specifications exist only on a
dedicated `handoff/issues/<identifier>` branch with annotated immutable tag
`handoff/issues/<identifier>/ready`, under
`.devsystem/handoffs/issues/<identifier>/`; they are not maintained on the
default branch.

Each artefact contains exactly `manifest.json` and `body.md`. The manifest names
the artefact type, identifier, producing and receiving roles, authorized
operation, lifecycle status, exact Issue title, and SHA-256 digest of the
normalized payload. The concise canonical publication trigger identifies the
handoff; the Implementer derives and verifies its branch, ready tag, immutable
commit, repository-relative path, and digest.

After successful publication and exact content verification, the GitHub Issue
becomes authoritative. The handoff branch and ready tag are then deleted. The
artefact never overrides later governed changes to the Issue.
