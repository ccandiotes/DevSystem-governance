# Project Workflow Reference

The Product Owner / Reviewer normally uses semantic instructions; the
Implementer performs the deterministic Git and GitHub mechanics defined in
`AGENTS.md`.

## AI conversation bootstrap

The Product Owner selects the correct repository/workspace, identifies the AI
role, and uses one short prompt. Previous conversation history is unnecessary.

`PROJECT.md` records the current development focus and recommended
conversation titles using these formats:

```text
<Project Name> - Architect - <Development Focus>
<Project Name> - Implementer - <Development Focus>
```

Use the current development focus as the recommended boundary for starting
fresh Architect and Implementer conversations. When it changes, open new
conversations with the recorded titles and run the prompts below. Titles and
conversation lifecycle aid navigation and context only; GitHub Issues remain
authoritative for requirements and GitHub Projects for priority and scheduling.

### Architect prompt

```text
Bootstrap Architect for <Project Name>.

Reconstruct context from repository governance and current GitHub state. Verify
identity and governance baseline where available. Do not change state. Report
readiness, discrepancies, relevant open work, and the next Product Owner action.
```

### Implementer prompt

```text
Bootstrap Implementer for <Project Name>.

Reconstruct context from repository governance and current GitHub state. Verify
identity, branch/status, synchronization, governance baseline, required
documents, and GitHub access. Do not change state. Report readiness,
discrepancies, relevant assigned work, and the next Product Owner action.
```

Both roles read `PROJECT.md`, `AGENTS.md`, `DECISIONS.md`, this workflow,
`PLANNED_FEATURES.md`, and `CHANGELOG.md`, followed by task-relevant documents
and actual GitHub work. The response reports role, verified identity/baseline,
current state, open work, authority understanding, discrepancies, and readiness,
then ends with the guided `Next action` block. Bootstrap never authorizes it.

## Development focus and repository milestones

The current development focus identifies the primary body of work being
pursued and provides the conversation boundary. It may become `None` or
maintenance-oriented when active development pauses.

Repository milestones instead describe significant achieved or intended
outcomes or states. Generated projects begin with `Deployed`, meaning the
governed project has been established successfully in its intended working
environment. Where applicable, its Issues verify project identity and required
configuration; local Git and GitHub setup; governance deployment on the default
branch; placeholder resolution; Architect and Implementer bootstrap; local
workspace, repository, and connector access; elected GitHub Project setup; and
mandatory project-specific deployment requirements.

When GitHub is used, GitHub Milestones own live Issue membership and completion
state. GitHub Projects are optional planning views and do not own milestone
state. `PROJECT.md` preserves concise milestone context rather than duplicating
Issue tracking or schedules. `First Release` may be suggested or configured as
a later milestone but is not mandatory, and extensions may recommend
domain-appropriate milestone conventions.

## Governance baseline lifecycle

The installed governance baseline is distribution-owned metadata, not editable
project configuration. `PROJECT.md` presents it and
`.devsystem/governance.json` records the installed version and optional
read-only upstream manifest. The project release version is independent.

The repository's installed governance remains authoritative and fully usable
offline. The upstream source is authoritative only for published governance
releases and migration material; discovery cannot override local governance.
When tooling is available, a read-only check may report the installed baseline,
whether upstream is reachable, and whether a defined compatible migration is
available.

Synchronization is never automatic. It requires explicit Product Owner
authorization and an auditable repository change from the known installed
version to a named target. Migrations distinguish:

- upstream-managed common governance;
- project-configured identity and roles;
- project-owned decisions, history, planned features, and documentation; and
- mixed files requiring an explicit merge or transformation.

Project-owned state is preserved. If no compatible migration is defined, the
update remains unapplied and manual review is required. Validation must complete
before updated installed metadata becomes authoritative, and failures leave the
existing governance intact.

## Normal lifecycle

### Guided handoffs

At workflow boundaries, Architect and Implementer responses end with advisory
next step guidance:

```text
Next action
Owner: <responsible role>
Action: <decision or manual step>
Trigger or artefact: <exact wording or ready-to-use content>
Conditions: <required review, validation, authorization, or blocker>
```

This guidance does not authorize the next action. Architect responses
proactively supply agreed Issue drafts, decision wording, review or closure
comments, tag names and annotations, or planned-feature entries and identify
their single authoritative destination. Implementer responses report status,
validation, manual actions, and the next trigger. If no valid step exists, the
response explains why.

### Semantic trigger terminal-state contract

Every semantic trigger has a defined outcome:

```text
current governed state → authorized semantic trigger → authorized substeps
                       → expected terminal state
```

The receiving role completes all substeps already authorized by a Product Owner
trigger without seeking redundant confirmation. Later suggested actions remain
separate authorization boundaries, and no trigger expands Issue scope or
bypasses validation, repository protection, human review, or acceptance.

| Trigger | Expected terminal state |
|---|---|
| `Bootstrap Architect` or `Bootstrap Implementer` | Read-only readiness report, discrepancies, authority summary, and guided next action |
| `Implement issue #N` | Validated implementation and evidence; no publication unless separately authorized |
| `Implement issue #N and prepare submission` | Draft PR awaiting Architect and Product Owner / Reviewer review |
| `Validate implementation` | Validation evidence, failures, and blockers reported |
| `Review documentation impact` | Impact assessed, material updates validated, and rationale reported |
| `Prepare submission` | Draft PR awaiting Architect and Product Owner / Reviewer review |
| `Architect review PR #N` | Decision, findings, review wording, and next Product Owner / Reviewer action |
| `PR #N merged` | Synchronized default branch, verified result, branch cleanup, and guided next action |
| `Architect review issue #N` | `KEEP OPEN` or `READY TO CLOSE`, with reason and guided next action |
| `Close issue #N with architect comment` | Exact comment recorded, Issue closed, and resulting state reported |
| `Maintain governance: <authorized change>` | Validated change submitted by the authorized method, or a genuine blocker reported |
| `Create tag <tag-name>` | Verified annotated tag present locally and remotely; no Release is inferred |
| `Audit workspace` | Read-only evidence, discrepancies, blockers, and next action reported |
| `Check governance baseline` | Installed baseline and optional upstream compatibility reported without repository changes |
| `Synchronize governance to <version>` | Validated reviewable migration change, or unchanged governance with a blocker/manual-migration report |

Genuine blockers include unverifiable identity, unsafe worktree state,
unexpected Issue or PR state, protection failure, authorization ambiguity,
unresolvable validation failure, unavailable required access, scope overrun, or
a required human decision. The response identifies the intended terminal state,
stopping point, blocker and reason, responsible role, and exact next governed
action. Convenience confirmation alone is not a blocker.

### Deterministic semantic handoff contract

Successful transitions continue from terminal state to a canonical handoff:

```text
current state → semantic trigger → authorized execution → terminal state
              → canonical next trigger or explicit human/no-action state
```

Semantic triggers are stable workflow protocol identifiers. With exactly one governed
successor, the `Trigger or artefact` field contains it verbatim with only the
Issue or PR number substituted. Explanation may accompany but never paraphrase,
broaden, shortcut, or replace that trigger.

#### Context informs; the active repository governs

Related conversation, workspace, repository, subsystem, and project context may
support reasoning but never authorizes a transition. Authority remains verified
active-repository identity and governance, authoritative GitHub state, active
Issues and PRs, and explicit Product Owner / Reviewer decisions. A role uses
related context without selecting, replacing, or bypassing the active
repository's canonical handoff.

| Completed state | Canonical successor behavior |
|---|---|
| Architect has prepared an Issue for implementation | `Implement issue #N and prepare submission` |
| Draft PR created or updated by the combined implementation trigger | `Architect review PR #N` |
| Architect has reviewed a PR | Product Owner / Reviewer validation and merge decision; no AI trigger crosses this human boundary |
| Product Owner / Reviewer has merged an accepted PR | `PR #N merged` |
| Post-merge synchronization and cleanup are complete | `Architect review issue #N` when the parent Issue is ready for acceptance review |
| Architect Issue review returns `READY TO CLOSE` | `Close issue #N with architect comment` |
| Authorized Issue closure is complete | `Issue #N closed` |
| Governance maintenance is complete | Report its authorized result; if no governed work follows, state that no action is currently required |

Where several successors are valid, list the permitted canonical choices and
the required Product Owner / Reviewer decision without choosing it. A genuine
blocker never receives a success-path successor; use the blocker report and let
governance determine the repeat or recovery action. A dormant or complete state
may report `Next action: none` rather than inventing a transition.

Exact canonical triggers and permitted transitions let future tooling detect a
missing or unexpected handoff as a protocol-conformance failure, including
human-decision and no-action states, without interpreting arbitrary prose.

Each planning state has one authority:

| State | Authority |
|---|---|
| Agreed future idea | `PLANNED_FEATURES.md` |
| Requirement and acceptance criteria | GitHub Issue |
| Live milestone membership and completion state | GitHub Milestone |
| Optional priority, scheduling, roadmap, and cross-repository views | GitHub Project |
| Proposed implementation and review evidence | Pull Request |
| Requirement completion state | Closed GitHub Issue |
| Product/version history | `CHANGELOG.md` |
| Durable high-level repository milestone context | `PROJECT.md` |
| Immutable version/release identity | Git tag |
| Optional release presentation/distribution metadata | GitHub Release associated with the tag |

Promote information between authorities rather than duplicating it. GitHub
Milestones own live Issue membership and completion state. GitHub Projects are
optional and may reference milestones, but they do not define requirements or
own milestone state. During
implementation, the Issue continues to own the requirement and acceptance
criteria while the linked PR owns the proposed implementation increment and
review evidence. `PROJECT.md` preserves concise high-level milestone context.
Git tags are immutable version or release authorities; optional GitHub Releases
add presentation or distribution metadata without replacing the tag.

```text
requirement → GitHub Issue → Architect implementation intent
→ Implementer work → Draft PR → Architect recommendation
→ Product Owner / Reviewer validation and merge → Implementer branch cleanup
→ Architect Issue review → Product Owner-authorized closure
```

`Architect prepare implementation for Issue #N` normally produces one copy/paste
instruction headed `Implement issue #N and prepare submission`. The Implementer
verifies and synchronizes the repository, implements the approved scope,
assesses documentation impact, validates, commits intended changes, pushes only
the feature branch, creates or updates the Draft PR, and stops for review.

The standalone `Implement issue #N`, `Validate implementation`, `Review
documentation impact`, and `Prepare submission` triggers remain available for
intentionally staged or interactive work. After human merge use `PR #N merged`.
Ask the Architect to `Architect review issue #N`; only after `READY TO CLOSE`
use `Close issue #N with architect comment`. Tagging is a separate optional
action: `Create tag <tag-name>`.

## Governance maintenance

`Maintain governance: <authorized change>` permits narrow, Product
Owner-authorized, non-functional maintenance of governance Markdown without a
parent Issue. Examples are recording an Architect-worded pre-Issue future idea,
correcting formatting or typos, and repairing internal links.

The Implementer verifies eligibility, changes only authorized files, validates
and reviews the exact diff, and reports evidence. Product or generated-template
behaviour, source code, architecture, authority boundaries, configuration, and
workflow changes require the normal Issue workflow.

Eligible files are `PLANNED_FEATURES.md` under its existing lifecycle, root
governance Markdown and `docs/*.md` for non-semantic corrections, and matching
template Markdown only when generated behaviour stays unchanged.

The Product Owner separately authorizes either a direct maintenance commit to
the synchronized default branch when protections permit, or a focused branch
and Draft PR. A maintenance PR records `governance maintenance`, authorization,
scope, and validation but needs no parent Issue. Maintenance never adds a GitHub
Project item or bypasses repository protections.

## Emergency Git reference

```shell
git status --short --branch
git branch --all
git log --oneline --decorate -10
git remote -v
git fetch --prune origin
git switch <Default Branch>
git pull --ff-only origin <Default Branch>
```

Never force-push, rewrite the default branch, replace tags, or guess deletion
targets. Use `Audit workspace` when state is unclear.
