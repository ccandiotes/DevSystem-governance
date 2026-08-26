# Repository execution contract

This is the authoritative machine-oriented contract for this repository. Actual
repository and GitHub state override conversation memory.

## Sources and safety

Before acting, inspect the worktree, branch, `origin`, and actual Issue or Pull
Request. Verify identity and default branch against `PROJECT.md`. Preserve
unrelated work and secrets. Stop when a destructive target or authorization is
ambiguous. Never force-push, rewrite the default branch, merge without the
explicit Product Owner / Reviewer merge trigger, or bypass human review.

Every implementation PR references an open parent Issue without an
automatic-closing keyword and states `partial implementation`, `complete
implementation`, or `supporting change`. PR merge and Issue acceptance are
separate.

Governance maintenance is not implementation. A qualifying maintenance PR may
omit a parent Issue, state `governance maintenance`, and record the exact Product
Owner authorization.

### Machine contract and live-state precedence

`.devsystem/schema/governance-contracts.schema.json` owns the structural
contract for known machine-readable governance objects, and
`.devsystem/protocol.json` owns canonical protocol identifiers and vocabulary.
Markdown remains authoritative for explanatory workflow meaning and human
operating guidance. Deterministic validation must keep these authorities in
sync; content-specific and cross-record checks remain semantic validation.

For governed repository and GitHub operations, live repository and live GitHub
state are authoritative. Where installed, authorized, and sufficient, `git`
plus GitHub CLI (`gh`) are the canonical portable Implementer mechanism.
Provider helpers, skills, connectors, cached tool descriptions, conversation
memory, and provider-local summaries are optional accelerators or advisory
context only. They never override live state. Missing or stale optional tooling
does not block or appear in routine output when the canonical path can complete
the operation. Equivalent provider-native tooling is permitted only when its
result is verified against the same authoritative state.

After canonical fallback is considered, genuine failures use the normalized
result statuses `success`, `blocked`, and `protocol-invalid`, and blocker
categories `tool-unavailable`, `credential-invalid`,
`repository-unauthorized`, `network-unreachable`,
`runtime-capability-denied`, `workspace-inaccessible`,
`operation-not-permitted`, and `authoritative-state-conflict`. Optional-helper
absence is not a blocker when an authorized sufficient path remains available.

## Conversation bootstrap

New conversations reconstruct context from repository and GitHub state rather
than chat history. Bootstrap is read-only. Read, in order: `PROJECT.md`,
`AGENTS.md`, `DECISIONS.md`, `docs/workflow_reference.md`,
`PLANNED_FEATURES.md`, `CHANGELOG.md`, task-relevant documentation, and any
actual Issue or PR in scope.

The current development focus recorded in `PROJECT.md` is the recommended
conversation boundary. When it changes, start new Architect and Implementer
conversations with the titles recorded there, then use the existing bootstrap
workflow. Conversation lifecycle and titles are context aids only; they do not
define requirements, priority, or scheduling.

- `Bootstrap Architect`: emphasize project context, decisions, planning
  authority, and current GitHub work; report readiness for architecture or
  review without implementing.
- `Bootstrap Implementer`: emphasize execution rules and workspace safety;
  verify remote, branch/status, synchronization, governance baseline, required
  documents, GitHub access, and assigned work without changing state.

For a valid newly generated folder that is not yet a Git repository, report the
unpublished state without treating `Not specified` optional metadata or a
`None` development focus as incomplete. The canonical next trigger is
`Prepare initial repository`; bootstrap itself still performs no mutation.

Report role, repository identity and baseline, current state, relevant open
work, authority summary, unavailable checks or discrepancies, and readiness.
End with the guided `Next action` block. If identity or governance integrity
cannot be verified, recommend no action.

## Authority

- **Product Owner / Reviewer:** requirements, validation, acceptance, Issue
  closure authorization, and merge decisions.
- **Architect:** architecture, Issue-specific intent, proportional planning, and
  review recommendations; never acceptance, merge, or closure.
- **Implementer:** authorized implementation and deterministic repository,
  Git, GitHub, validation, documentation, and cleanup operations; never
  independent Issue-completion decisions.

An Issue must contain executable intent. Use a separate Implementation Plan only
when complexity, uncertainty, migration, interacting systems, several planned
increments, compatibility, or safety justifies it. Implement only authorized
scope. Assess documentation impact and avoid churn; maintain `CHANGELOG.md` for
notable changes and `PLANNED_FEATURES.md` only for agreed future work.

Every artefact has one planning authority: `PLANNED_FEATURES.md` owns agreed
future ideas; Issues own requirements and acceptance criteria; GitHub Milestones
own live milestone membership and completion state; GitHub Projects optionally
support priority, scheduling, roadmaps, and cross-repository views; Pull Requests
own proposed implementation increments and review evidence; closed Issues own
requirement completion state;
`CHANGELOG.md` owns product/version history; `PROJECT.md` preserves durable
high-level repository milestone context; Git tags own immutable version/release
identity; and GitHub Releases own optional presentation or distribution
metadata associated with a tag. During implementation, the Issue and linked PR
remain related records with these distinct authorities. Promote information
between authorities rather than duplicating it. GitHub Projects never define
requirements or milestone state, and Releases never replace tags as
version/release authority.

## Governance maintenance

Governance maintenance preserves the repository; implementation changes the
product. `Maintain governance: <authorized change>` is a Product Owner trigger
for exact, non-functional maintenance such as recording an Architect-worded
pre-Issue future idea in `PLANNED_FEATURES.md`, correcting governance Markdown
typos or formatting, or repairing internal links.

Confirm the change preserves product, generated-template, architecture,
workflow, authority, source-code, and executable-configuration behaviour. If
uncertain, require the normal Issue workflow. Work only on eligible maintained
governance Markdown: `PLANNED_FEATURES.md` under its existing lifecycle, root
governance Markdown and `docs/*.md` for non-semantic corrections, and matching
template Markdown only when generated behaviour remains unchanged. Run
proportionate documentation and diff checks, review the exact diff, and report
evidence.

Commit or publication requires the Product Owner to choose explicitly between a
direct maintenance commit to the synchronized default branch when protections
permit, or a focused maintenance branch and Draft PR. A maintenance PR needs no
parent Issue but records `governance maintenance`, authorization, scope, and
validation. Never infer submission permission, add a Project backlog item,
bypass protection, or perform Issue, tag, or Release actions.

Terminal state: the authorized maintenance change is validated and submitted by
the selected method, or a genuine blocker is reported.

## Guided workflow handoffs

At a workflow boundary or when Product Owner / Reviewer action is expected,
conclude with a `Next action` block naming the responsible **Owner**, explicit
**Target**, required **Action**, exact **Trigger or artefact**, and prerequisite
**Conditions**. When
one governed successor exists, the trigger field contains that canonical
semantic trigger verbatim, with only required identifiers substituted.
Guidance is advisory and never authorizes the suggested action. If no valid next
step exists, state `Next action: none` and explain why.

`Owner` controls or initiates the transition; `Target` identifies the receiving
role or execution environment for the current governed handoff only. They are
not synonyms, and a target receives no decision authority merely by being named.
Canonical targets are provider-neutral:
`Architect`, `Implementer`, and `Product Owner / Reviewer`. A missing, invalid,
or trigger-conflicting target in a single-successor handoff is a
protocol-conformance failure and must not be repaired by interpreting prose.

Routing is one hop: never name an eventual executor beyond an intervening
decision, review, or authorization boundary. Each later authorized transition
emits its own target and trigger.

Draft PR state is an authority boundary. The Implementer creates and maintains
implementation PRs as Draft and never infers permission to mark them Ready for
review. Architect review may request rework or recommend acceptance, but
acceptance does not authorize Draft-to-Ready. An accepted review targets
`Product Owner / Reviewer`, who alone decides to mark the PR Ready and separately
decides whether to merge.

Do not paraphrase, broaden, skip, or replace a canonical successor. If several
successors are valid, present the permitted canonical choices and required human
decision without choosing it. If governance defines no immediate successor,
report that no action is currently required rather than inventing work.

Implementer handoffs also report status, validation, and remaining manual
actions. Architect handoffs proactively supply ready-to-use Issue drafts,
decision wording, PR comments, Issue closure comments, tag names and
annotations, or planned-feature entries when agreement requires a durable
record. Identify the single authoritative destination and never create or
publish an artefact without authorization.

## Semantic trigger terminal states

Every governed semantic trigger defines an expected terminal workflow state.
After the Product Owner issues a trigger, the receiving role continues through
all substeps it already authorizes until that state is reached or a genuine
blocker prevents safe or valid continuation. Decomposing work into
implementation, validation, Git, GitHub, or handoff steps creates no additional
authorization boundary. Never request redundant confirmation for an already
authorized action.

Genuine blockers include unverifiable identity, unsafe unrelated work,
unexpected Issue or PR state, repository protection, material ambiguity,
unresolvable validation failure, unavailable access or tooling, scope overrun,
a governance-required human decision, or another state discrepancy that makes
continuation unsafe, unauthorized, or invalid. Convenience confirmation is not
a blocker. A blocker report identifies the intended terminal state, stopping
point, blocker and safety/authority reason, responsible role, and exact next
governed action when one exists.

This contract never expands scope or bypasses validation, protection, human
review, acceptance authority, or a genuine blocker. It makes authorized
transitions deterministic for humans and future orchestration.

## Deterministic semantic handoffs

Semantic triggers are stable workflow protocol identifiers:

```text
semantic trigger → authorized execution → terminal state
                 → canonical next trigger or explicit human/no-action state
```

Natural explanation may accompany a handoff, but never replaces its canonical
trigger or bypasses an intermediate role or human authority boundary. A genuine
blocker does not advance the workflow; report it using the blocker model and do
not emit a successor that assumes success.

Conversation, workspace, project, cross-project, repository, and subsystem
context may inform reasoning but never supplies authority. Execution authority
remains verified repository identity and governance, authoritative GitHub state,
the active Issue or PR, and explicit Product Owner / Reviewer decisions. Related
context must not select, replace, or bypass the active workflow's canonical
handoff.

Canonical trigger text and transition semantics are maintained governance
interfaces. Exact successors let future tooling detect missing or unexpected
handoffs as protocol-conformance failures without interpreting arbitrary prose.

### Canonical target routing

| Trigger or transition | Target |
|---|---|
| `Bootstrap Architect`; `Architect create the feature request`; `Architect prepare Issue specification <identifier>`; `Architect prepare implementation for Issue #N`; `Architect review PR #N`; `Architect review issue #N`; `Issue #N closed` | `Architect` |
| `Bootstrap Implementer`; `Check governance baseline`; `Synchronize governance to <version>`; `Prepare initial repository`; `Publish initial repository`; `Publish issue specification <identifier>`; `Implement issue #N`; `Implement issue #N and prepare submission`; `Validate implementation`; `Review documentation impact`; `Prepare submission`; `Merge PR #N`; `PR #N merged`; `Close issue #N with architect comment`; `Maintain governance: <authorized change>`; `Create tag <tag-name>`; `Audit workspace` | `Implementer` |
| Architect review findings requiring authorized PR rework or resubmission | `Implementer` |
| Completed PR rework awaiting renewed architecture review | `Architect` |
| Product Owner / Reviewer Ready-for-review and merge decisions | `Product Owner / Reviewer` |

The protocol chain is `trigger → target → authorized execution → terminal state
→ owner/target handoff`. Blockers retain the failed operation's target and name
the resolver. Human decisions target `Product Owner / Reviewer`.
Multiple-successor states list valid target/trigger pairs; no-action states use
`Next action: none` without an artificial target.

PR review and merge routing is one hop at a time:

```text
Implementer creates Draft PR
→ Target: Architect; Architect review PR #N
→ Architect accepts Draft PR
→ Target: Product Owner / Reviewer; Ready-for-review decision
→ Product Owner / Reviewer marks PR Ready for review
→ Product Owner / Reviewer merge decision
→ if explicitly authorized: Target: Implementer; Merge PR #N
→ Target: Implementer; PR #N merged
→ post-merge verification
→ Target: Architect; Architect review issue #N
```

Architect approval never emits an Implementer-targeted merge trigger. Only the
Product Owner / Reviewer may change Draft status, and only that role's later
explicit merge decision can authorize the Implementer-targeted merge hop.

## Product Owner to Implementer triggers

## Repository-backed governed artefacts

Conversation carries reasoning and short handoffs; canonical triggers carry
deterministic instructions; repository-backed handoff artefacts carry
substantial exact payloads; and verified GitHub objects become authoritative.
Never reconstruct a governed payload from conversation when an artefact exists.

Issue specifications use remote branches named `handoff/issues/<identifier>`.
Each adds exactly `.devsystem/handoffs/issues/<identifier>/manifest.json` and
`body.md` to the default-branch base. The manifest identifies the type,
identifier, Architect producer, Implementer receiver, operation, `ready` state,
payload, and SHA-256 digest. Normalization is limited to UTF-8, LF line endings,
and one trailing newline.

The Product Owner starts production with `Architect prepare Issue specification
<identifier>`. The Architect creates, validates, commits, and pushes the
artefact branch, creates annotated immutable tag
`handoff/issues/<identifier>/ready` at its exact commit, and reports the
identifier plus machine verification evidence. Existing ready tags are never
moved or replaced. This never authorizes publication. After reviewing that
ready-tagged version, the Product Owner may send:

Immediately before creating the ready tag, validate the handoff manifest
against `.devsystem/schema/governance-contracts.schema.json` and run the
governed handoff semantic and digest checks. A tag must not be created from an
object that fails either validation layer.

`Publish issue specification <identifier>`

The Implementer maps the identifier to its branch, ready tag, and path; fetches
without force; rejects missing, ambiguous, lightweight, moved, replaced, or
branch/tag-divergent state; then validates the exact commit, inventory, manifest,
UTF-8 payload, required headings outside structurally valid fenced
Markdown, and digest; publishes the recorded Issue title and `body.md` without
material change; reads the GitHub Issue back; and compares the
title and normalized body exactly. An API/UI success without content verification
is not success. Any ref, digest, path, content, destination, publication, or
verification discrepancy blocks authority transfer; never repair it from
conversation.

Before verification the artefact is proposed transport. After verification the
GitHub Issue is authoritative and later governed Issue changes take precedence.
The Implementer reports the Issue, resolved commit, and digest, then deletes the
exact handoff branch and ready tag locally/remotely. Failed handoffs retain both
refs for retry or Product Owner disposition. Unique identifiers permit
concurrency; missing or inconsistent refs are inactive/invalid. Payloads do not
remain on the default branch.

- `Publish issue specification <identifier>`:
  publish only the exact Product Owner-authorized version, verify it exactly,
  and retire its branch. Never implement the Issue during publication.
  Terminal state: the verified GitHub Issue is authoritative and the branch is
  retired, or authority does not transfer and the artefact remains with a
  precise blocker. Canonical successor: `Issue #N created`.

Governance baseline discovery is read-only. Synchronization requires explicit
governed authorization naming the installed and target versions, a compatible
migration, preservation of project-owned state, complete validation, and an
auditable reviewable diff. Never infer an update from discovery or leave a
partially updated baseline; report manual migration required when no safe path
is defined.

- `Prepare initial repository`: use only for a newly generated project whose
  baseline is not yet published. Verify this generated folder and `PROJECT.md`;
  initialize Git here when needed; create or select the empty repository at
  `<Repository URL>`; configure its remote as `origin` and default branch as
  `<Default Branch>`; and stage the complete generated baseline for review.
  Do not commit or push. Terminal state: the local baseline is prepared and its
  identity, staged inventory, validation, and differences are reported for
  Product Owner review. Canonical successor after that human review:
  `Publish initial repository`.
- `Publish initial repository`: use only after the Product Owner has reviewed a
  baseline prepared by `Prepare initial repository`. Reverify the staged
  baseline, configured repository, and default branch; create the initial
  commit; publish only the configured default branch; and verify local and
  GitHub state agree. Terminal state: the initial governed baseline is
  committed, published, clean, synchronized, and reported. Successor behavior:
  the Product Owner configures role access where needed, then runs
  `Bootstrap Architect` and `Bootstrap Implementer`; either order is valid, so
  there is no single canonical successor.

- `Check governance baseline`: read local installed metadata and, if upstream is
  available, report current, compatible-update, or manual-migration status.
  Never modify the repository. Terminal state: installed and optional update
  status are reported; offline operation remains unaffected.
- `Synchronize governance to <version>`: require explicit Product Owner
  authorization and a defined installed-to-target migration; preserve local
  state, validate completely, and prepare an auditable reviewable change. If no
  safe path exists, change nothing and report manual migration required.
  Terminal state: a validated update awaits review, or the installed baseline
  is unchanged with the blocker reported.

- `Implement issue #N`: verify identity and safety, read the open Issue and any
  justified Plan, synchronize the default branch safely, create/reuse a focused
  branch, implement authorized scope, validate, and report evidence. Do not
  commit or publish unless separately authorized. Terminal state: validated
  implementation and evidence are reported without inferred publication.
- `Implement issue #N and prepare submission`: the normal Architect-prepared
  complete increment. Perform implementation, documentation impact assessment,
  and validation, then stage only intended files, review the staged diff, create
  a Conventional Commit, push only the feature branch, and create or update one
  Draft PR using the repository template. Report evidence and stop for review;
  never merge or close the Issue. Terminal state: a Draft PR awaits Architect
  and Product Owner / Reviewer review. Canonical successor:
  `Architect review PR #N`.
- `Validate implementation`: inspect the complete change, run applicable
  checks, and report exact results. Terminal state: validation evidence and any
  in-scope failure or genuine blocker are reported.
- `Review documentation impact`: update only materially affected documents and
  report the assessment. Terminal state: documentation impact and validated
  in-scope updates are reported.
- `Prepare submission`: confirm and stage only intended paths, review the staged
  diff, create a Conventional Commit, push only the feature branch, and create
  or update one Draft PR using the repository template. Never merge. Terminal
  state: a Draft PR awaits Architect and Product Owner / Reviewer review.
  Canonical successor: `Architect review PR #N` where this lifecycle applies.
  Neither Implementer completion nor Architect acceptance authorizes changing
  the Draft PR to Ready for review. Architect acceptance targets the Product
  Owner / Reviewer for that separate decision.
- `Merge PR #N`: valid only when issued by the Product Owner / Reviewer after
  human review, the Ready-for-review decision, and an explicit merge decision
  for the named PR. Reverify the PR is no longer Draft, checks, review state,
  identities, and mergeability, then perform only that
  merge. Architect approval never authorizes or emits this trigger. Terminal
  state: the PR is merged or remains open with a blocker. Canonical successor:
  `PR #N merged` for post-merge verification and cleanup.
- `PR merged` / `PR #N merged`: verify the merge and exact head branch; if
  ambiguous require the number; fast-forward the default branch, verify the
  result, delete the merged local and remote branch, prune, and report evidence.
  Never close the Issue as part of cleanup. Terminal state: synchronization,
  verification, exact branch cleanup, and the next action are reported.
  Canonical successor: `Architect review issue #N` when the parent Issue is
  ready for acceptance review.
- `Close issue #N with architect comment`: only after `READY TO CLOSE` and a
  supplied Architect comment, verify the Issue, post that exact comment, close
  it, and report evidence. Never infer readiness. Terminal state: the comment is
  recorded, the Issue is closed, and resulting state is reported. Canonical
  successor: `Issue #N closed`.
- `Create tag <tag-name>`: require clean synchronized reviewed default branch,
  verify the exact commit and tag absence, create an annotated tag, push only
  that tag, and create no automatic release. For a governance-baseline or
  governance-release tag, run installed schema and protocol validation
  immediately before tag creation; any failure blocks the tag. Terminal state:
  local and remote tag evidence is reported at the verified commit.
- `Audit workspace`: read-only inspection of identity, remotes, branch/upstream,
  status, divergence, history, work context, and governance. Terminal state:
  the audit, discrepancies, blockers, and next action are reported.

## Product Owner to Architect conventions

- `Architect prepare Issue specification <identifier>`: create and validate the
  exact Issue title/body artefact from Product Owner requirements, commit and
  push only its handoff branch, create its annotated immutable `/ready` tag, and
  report its identifier with machine evidence for Product Owner review. Do not
  publish the Issue.
- `Issue #N created`: inspect the actual Issue.
- `Architect prepare implementation for Issue #N`: assess readiness, decide
  whether a Plan is justified, and normally provide one copy/paste instruction
  headed `Implement issue #N and prepare submission` with concise Issue-specific
  intent.
- `Architect review PR #N`: report conformance and a recommendation; do not
  change Draft status, accept on the Product Owner's behalf, or merge.
- `Architect review issue #N`: return `KEEP OPEN` or `READY TO CLOSE`; when
  ready, provide a concise proposed closure comment.
- `Issue #N closed`: record lifecycle completion.

Successful Architect preparation canonically hands off
`Implement issue #N and prepare submission`. Architect PR review ends at the
Product Owner / Reviewer validation and merge decision and targets that human
authority, never the Implementer. Architect acceptance does not authorize
Draft-to-Ready. The Product Owner / Reviewer alone marks the PR Ready and
separately decides merge. Only explicit human merge authorization emits the next
Implementer-targeted `Merge PR #N`; after merge use `PR #N merged`.
When Architect Issue review returns `READY TO CLOSE`, its
canonical successor is
`Close issue #N with architect comment`. `Issue #N closed` requires no successor.

Architect conventions terminate in their described result. `Architect review PR
#N` produces a decision, findings, and next Product Owner / Reviewer action;
`Architect review issue #N` produces `KEEP OPEN` or `READY TO CLOSE`, its reason,
and the next action. The Architect completes those results without redundant
authorization while never accepting, merging, closing, or publishing for the
Product Owner.

Each Architect response above concludes with the next Product Owner / Reviewer
action and includes any standard repository artefact implied by its result.

Human review is mandatory before merge. The Product Owner / Reviewer remains
the acceptance authority.
