# Sanho Git Operation Review Validation

- Run ID: `sanho-review-20260804-bdea8b0-094414`
- Sanho revision: `bdea8b08a6820c62c78619bb97c0bff65c8cb8e4`
- Sanho version: `v0.1.3-11-gbdea8b0`
- Git: `2.50.1 (Apple Git-155)`
- Go: `go1.26.5 darwin/arm64`
- Validation repositories: `sanho-server`, `sanho-client`, and `sanho-docs`
- Overall status: `PASS WITH DOCUMENTATION FINDING`

## Completed evidence

- `make test`: PASS.
- Race gate for Git, filesystem, CLI, and CLI integration packages: PASS.
- H11 stale Git-operation guard and linked-worktree isolation: PASS.
- H12 merge backend with 1,000 rewrites: PASS.
- H12 apply backend with 1,000 non-empty rewrites: PASS.
- H13 Git-owned source, forged input rejection, optional extra-info, and SHA-256 object IDs: PASS.
- H01 canonical docs to client/server synchronization, dirty-layer preservation,
  automatic main-first publication, and client reverse publication: PASS.
- H02 alias/direct-URL bypass blocking, tag-only/deletion allowance, recovery,
  and post-publication push: PASS.

## Review finding

The documented H12 apply-backend fixture that combines one real change with
many intentionally empty commits is not executable with Git 2.50.1: the apply
backend stops with `Patch is empty`. Replacing the empty commits with 1,000
real file-change commits validates Sanho reconciliation successfully. This is
a hands-on checklist defect, not a Sanho runtime failure.

## Real-remote evidence

- Starting main SHAs: server `6cbc558d32aa408f25df84424fab1bad89b49f3e`,
  client `48b4be3784d46cbf0d2ae195e53f36b411e3063d`, docs
  `38843f8a43e9c53f1fafbc6a0544fe5363623c31`.
- Initial validation publication: docs
  `1d31762146742cffa7a48afb6bca89bcb8166723`, client
  `12994158b948b5819e6fd3f95a0d6e9e03fff195`, server
  `8978c9b937b3560873e848b5d7f82dd1a9abb4cf`.
- Pending alias and direct-URL branch pushes returned non-zero with no main or
  target-ref changes. Tag-only push and branch deletion succeeded.
- After main publication, alias and direct-URL branch pushes succeeded. All
  temporary branches and the temporary tag were deleted.
- This client edit is the reverse-publication proof. The final server sync and
  final remote main SHAs are recorded in the review handoff.
