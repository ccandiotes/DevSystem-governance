# Initial Project Deployment

This generated package is a complete governed repository baseline. Follow this
sequence literally; no Product Owner Git commands are required:

1. Keep this generated folder as the local workspace for **ConfiguratorDBTransfer**. Do
   not copy it into a pre-existing repository clone.
2. Create the Implementer environment or conversation rooted at this folder and
   copy and send the complete project-specific `Bootstrap Implementer` prompt
   from [`workflow_reference.md`](workflow_reference.md). Do not send only the
   trigger identifier `Bootstrap Implementer`; the complete prompt supplies the
   repository-reconstruction instructions. Bootstrap is read-only and should
   identify that repository preparation remains. Use the suggested title
   `ConfiguratorDBTransfer - Implementer - Resolve ACL Issues`. If the interface names
   conversations only after their first turn, rename it after bootstrap.
3. Ensure the Implementer can authenticate to GitHub. Issue this exact
   authorization: `Prepare initial repository`. It prepares repository
   **elexon_ConfiguratorDBTransfer** at **https://github.com/ccandiotes/elexon_ConfiguratorDBTransfer** on default branch
   **main**, but cannot commit or publish it.
4. Review the reported repository address, branch, generated-file inventory,
   validation, and staged differences. If correct, issue the separate
   authorization: `Publish initial repository`.
5. The Implementer creates and publishes the first commit, then verifies that
   the local folder and GitHub repository agree. This does not authorize later
   implementation work.
6. Configure repository/connector access for both roles. Repository access is
   essential because Issues, Pull Requests, branches, and other GitHub records
   are workflow authority. Current interfaces may place this under **User
   Settings → Applications → Connector** or a named GitHub connector; treat the
   navigation as changeable product guidance, not permanent governance.
7. Create the Architect conversation and copy and send the complete project-specific
   `Bootstrap Architect` prompt from
   [`workflow_reference.md`](workflow_reference.md). Do not send only the
   trigger identifier `Bootstrap Architect`. Use the suggested title
   `ConfiguratorDBTransfer - Architect - Resolve ACL Issues`, renaming it after its first turn
   where necessary. Then copy and send the complete project-specific `Bootstrap
   Implementer` prompt again in the existing Implementer conversation.
8. Verify both roles report repository **elexon_ConfiguratorDBTransfer**, URL
   **https://github.com/ccandiotes/elexon_ConfiguratorDBTransfer**, branch **main**, and the installed
   governance baseline.
   `Project Type: Not specified`, `Organisation: Not specified`, and
   `Development Focus: None` are valid values and do not block readiness.
9. Confirm the repository and GitHub state—not conversation history—are the
   workflow authority. Complete the `Deployed` checks, then use the normal
   governed workflow for the first capability.

`Prepare initial repository` and `Publish initial repository` are distinct
authority boundaries. The first changes only local preparation state; the
second authorizes the reviewed initial commit and GitHub publication. Manual Git
commands remain fallback or troubleshooting guidance.

Both triggers use `Target: Implementer`. The complete bootstrap prompts use
`Target: Architect` and `Target: Implementer` respectively. `Owner` remains the
Product Owner / Reviewer who chooses or authorizes the transition; naming a
target does not transfer that authority. When both bootstrap roles are valid
next steps, present both target/prompt choices and let the Product Owner choose
the order.

GitHub Projects are optional planning views. Deployment does not authorize
implementation, automatic governance synchronization, or any later workflow
transition.
