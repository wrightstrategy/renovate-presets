<!-- ws:dev begin — generated; do not hand-edit -->
<!-- ws:dev source=wrightstrategy/bridge:conventions/dev.md version=1 sha256=215cbf640cce8816628068bf6664dcd4b06a822cd9b4accb51d44bc8f4b92590 -->
# Coding Universe

Shared Wright Strategy rules: **Binding** boundaries cannot be weakened locally;
**Default** choices apply unless replaced in root `AGENTS.md` → `Local departures`.
Record the default, scope, replacement, and reason there. Definitions
and format: `docs/agents/ws-dev-reference.md#standard-authority-and-local-departures`.
Workflow policy stays in its owning skill; local departures never waive gates or checks.

<a id="standing-defaults"></a>

## Standing rules

- **Default — Mindset:** GitOps — git is the source of truth; declarative over manual.
- **Default — Communication:** write for the operator. Lead with what changed and what you
  need from them; explain terms beside their plain meaning.
- **Default — Ordinary work:** write implementation yourself, in-session.
- **Binding — Agent roles:** primary authors write plans/specs; earned parallelism or isolation
  uses Orca orchestration in a ready runtime, never hidden host subagents or silent executor
  CLIs. Workers never dispatch onward and are released before teardown. Shipped work meets
  the owning review gate however it was produced.
- **Binding — Review gates:** use `ws-dev:pr-review` for implementation PRs and
  `ws-dev:doc-review` for finished specs/plans before the human gate. Tiny work
  (trivial, behavior-preserving) and other exceptions use only the owning skill's recorded
  paths. Departures go in the review comment or log; a silent skip is never a waiver.
- **Binding — Work management:** before filing development work, use `ws-dev:linear` and
  its canonical `docs/standards/work-management.md` filing contract in dotfiles. Cross-repo
  requests use `ws-dev:repo-request`. Track agent work in Linear, never GitHub issues;
  link PRs to Linear.
- **Binding — Secrets:** never in git.
- **Default — Configuration:** commit `.env.example`; keep values in 1Password / SOPS /
  GitHub Environments. Fail fast on missing config; prefer OIDC or short-lived tokens,
  subject to applicable security/authentication contracts.
- **Default — Python:** use `uv`, not pip; commit `uv.lock`; never commit `.venv/`.
- **Default — TypeScript:** Bun for agent/scripting code; commit `bun.lock`; `"strict": true`.
- **Default — Commits:** Conventional Commits, imperative subject <70 chars; body says why.
- **Binding — Attribution:** agent commits carry truthful `Authored-By: Claude|Codex|Grok|Cursor`
  (reconciliation: `Reconciled-By:`); `Co-Authored-By:` only for authors of shipped bytes.
- **Binding — Deploy steps:** record required external actions (env, migration, job, cutover,
  out-of-app step) as a `deploy/next/` entry in the same PR; edit superseded entries in place.
  Follow the reference's migration scope for repos on `deploy_next.md` or `Deploy:` trailers.
- **Default — Testing:** `bun test` / `pytest`; behavioral test names; real dependencies over
  mocks that can drift. Required checks and verification obligations remain in force.
- **Default — CI runners:** private CI uses `runs-on: [self-hosted, ci]` (fresh VM, no LAN);
  document GitHub-hosted exceptions.
- **Default — Runtime:** one foreground process, stdout/stderr logs, clean `SIGTERM`;
  HTTP `/healthz` + `/readyz`; explicit, idempotent migrations. Preserve actual consumer contracts.
- **Binding — Docs:** reconcile living/reference docs with changes. Decisions land in their
  living home plus a dated `docs/decisions/` entry; ADRs are frozen (never extend or supersede).
  Finish with `ws-dev:doc-audit` or `docs not needed: <reason>`.
- **Default — Releases:** Python: python-semantic-release, tag-only, dispatched; JS/TS:
  Changesets. release-please is deprecated; migrate when release tooling is touched.
- **Binding — Release versions:** an org-built image homelab runs in production ships SemVer from
  `1.0.0` before first deploy (tag `vX.Y.Z` or `<app>@X.Y.Z`, image `X.Y.Z`); pin `X.Y.Z@sha256:…`.
- **Binding — Release information:** accurate deployment changes, breaking changes and image
  index digest let a deployer bump a pin without reading source. Preserve published interfaces.
- **Binding — Write scope:** write only the repository you are working in; for a change
  elsewhere, file Linear to its owning team. The cluster and homelab's hosts are homelab's:
  change them, or SSH to them, only from homelab. Reads are open: repos and read-only `kubectl`
  (no Secret data, `exec`, `port-forward`, `proxy`). Existing owner-authorized exceptions
  retain their scope.
- **Binding — Instruction files:** `AGENTS.md` is canonical; `CLAUDE.md` is the one-line
  `@AGENTS.md` adapter. Each repository owns its copy of these rules; change a shared rule in
  every copy. Reference copy: `wrightstrategy/dotfiles`.
- **Default — Local guidance:** smallest useful layout outside the shared rules.

## Tripwires

Read the applicable source; its rule labels govern. These pointers add no waiver path.

| Before you… | Read |
|---|---|
| write GitHub Actions beyond runner tier, `timeout-minutes`, one-run-per-change | `docs/agents/ws-dev-reference.md#github-actions` |
| write any `concurrency:` stanza, merge-queue config, or deploy workflow | `docs/agents/ws-dev-reference.md#concurrency-and-merge-queues` |
| write Dockerfiles, container CI, or release-promote flows | `docs/agents/ws-dev-reference.md#container-images--ci` |
| ship images or touch secret-scan gates | `docs/agents/ws-dev-reference.md#supply-chain-integrity` |
| edit Dependabot/Renovate config, registries, or osv-scanner | `docs/agents/ws-dev-reference.md#dependency-updates` |
| write a deploy step, or rotate/file the deploy-steps file | `docs/agents/ws-dev-reference.md#deploy-steps` |
| set up releases, cut one, hotfix, or first deploy an app to homelab | `docs/agents/ws-dev-reference.md#versioning--releases` |
| touch GitHub Packages auth (a 403 or Renovate 401 on "correct" config is this) | `docs/agents/ws-dev-reference.md#github-packages` |
| build or modify a web app | `homeapps/packages/web-ui` — shared UI spine, `create-app`, earn-its-place |
| parallelize or isolate work in an Orca runtime | `docs/agents/ws-dev-reference.md#parallel-and-isolated-work` |
| work in an Orca worktree | `docs/agents/ws-dev-reference.md#orca-worktree-checkpoints` |
| record, waive, or depart from any review gate | `ws-dev:pr-review` / `ws-dev:doc-review` |
| need filing/routing rules beyond the two destinations | `docs/standards/work-management.md` (in `wrightstrategy/dotfiles`) |
<!-- ws:dev end -->

<!-- ws:system-context begin — generated from wrightstrategy/bridge registry.toml; do not hand-edit -->
This repo is: Published public Renovate preset generated from bridge.
It **consumes**: `bridge`. It's **consumed by**: nothing yet.
Full map: `wrightstrategy/bridge` → `ARCHITECTURE.md`.
<!-- ws:system-context end -->
