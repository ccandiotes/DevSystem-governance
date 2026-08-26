# Repository-backed governed handoffs

Use conversation for reasoning and short triggers. When another role needs a
substantial governed payload exactly, use a repository-backed handoff artefact.
The initial supported type is a GitHub Issue specification.

An active specification uses a dedicated remote branch
`handoff/issues/<identifier>` and annotated immutable tag
`handoff/issues/<identifier>/ready`. It adds exactly these files to the
default-branch base:

```text
.devsystem/handoffs/issues/<identifier>/manifest.json
.devsystem/handoffs/issues/<identifier>/body.md
```

The manifest fixes the schema/type, identifier, Architect producer, Implementer
receiver, publication operation, `ready` state, payload path, and SHA-256. The
manifest also fixes the exact Issue title. The payload is UTF-8 with LF endings
and one trailing newline. The branch starts
from synchronized default-branch state and contains only that handoff. Both
roles access it through the repository; no shared filesystem is assumed.

The Product Owner authorizes production with `Architect prepare Issue
specification <identifier>`. The Architect validates, commits, and pushes the
artefact, creates the write-once annotated ready tag at the exact commit, and
reports direct review links plus machine evidence. This does not authorize
publication. After reviewing that ready-tagged version, the Product Owner may
send the Implementer:

```text
Publish issue specification <identifier>
```

The Implementer derives the branch, ready tag, and path from the identifier;
fetches without force; rejects missing, ambiguous, lightweight, replaced, or
branch/tag-divergent state; and validates the exact commit, inventory, manifest,
valid UTF-8, required headings outside structurally valid fenced code blocks,
and digest; publishes the recorded title and `body.md` without material change;
reads the Issue back; and compares the title and normalized body exactly.
Unclosed or malformed fences are rejected while valid fenced examples remain
supported. Body normalization is limited to line endings and one trailing
newline. A successful GitHub operation without content verification is not
success.

Commit/digest data is resolved and checked by the Implementer rather than copied
through conversation. Any mismatch or partial operation blocks authority
transfer. Never infer or
repair governed content from conversation. Failed artefacts remain available
for retry or Product Owner disposition. After exact verification, the GitHub
Issue becomes authoritative and the exact handoff branch is deleted locally and
remotely together with its ready tag. Unique identifiers support concurrent
handoffs; absence of both refs marks retirement and one-ref-only state is
invalid. Later governed Issue changes always take precedence.
