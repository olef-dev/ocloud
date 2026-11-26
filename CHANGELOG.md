# Changelog

Release notes for Olef Cloud CLI (`ocloud`). Every release, with its binaries, is on the
[Releases page](https://github.com/olef-dev/ocloud/releases).


## v3.18.0

- **Deterministic `next_actions` across CLI, MCP, and skills**: `ocloud --json` emits structured, shell-quoted `next_actions` hints across every command family (auth, workspaces, sessions, runs, agents, local checkouts, schedules, subscriptions, jobs, tokens, validators, circuit breakers, inbox/threads, builds, devices, and doctor), replacing stale command prefixes and placeholder arguments. `ocloud mcp` now returns standardized MCP-tool-vocabulary `next_actions` in both success payloads and errors, and the `ocloud` Claude Code / Codex plugin skills teach agents how to act on and surface them.
- **Zero-LLM cloud jobs, scoped API tokens, WASM validators, and circuit breakers**: adds `ocloud job` (idempotent runs, concurrency groups, artifact staging, SSE/cursor logs, `--breaker`, `--hold-on-fail` debug holds, and `--` ad-hoc command separation), `ocloud token` (`sdtok_*` scoped API tokens, rotation, IP CIDR allowlists, and keyless OIDC exchange), `ocloud validator` (org-owned WASM validators with dry-run testing and deletion), `ocloud breaker` (environment circuit breakers with bounded TTLs and half-open probes), and `ocloud schedule graduate`.
- **Workspace-first agent workflows and human question waits**: streamlines agent creation, workspace attachment, subscription prompts, and `ocloud inbox` / `ocloud thread` waiting on human questions with answer-version handling.
- **One-command self-update (`ocloud update --apply`)**: verifies SHA-256 checksums, macOS Developer ID signatures, and install receipts before atomically replacing the binary.

## v3.17.3

- Local agents and checkouts reach the CLI. An agent can be started as a local folder, linked to this computer's host, or checked out from its workplace — in `--edit` mode, where the workplace keeps serving while you work on a copy, or `--live`, where an exclusive lease routes the agent's events to this machine until you `--abort` it. New subcommands: `agent init`, `link`, `checkout`, `open`, `local`, `diff`, `pull`, `deploy`, `redeploy` and `baseline`. Work goes back with `agent redeploy`, which previews the revision diff and a preflight audit unless `--yes` is given, and carries the setup layer alone or the agent's auto-memory with it.
- `agent open` launches Claude Code or Codex against a local agent folder's isolated home, so an agent's instructions, settings, skills and subagents can be edited and run without touching your own `~/.claude` or `~/.codex`.
- `ocloud agent import` is gone, along with the MCP panel's and web app's setup cards for it. `agent checkout` and `agent redeploy` replace it: where `import` pushed this computer's runtime setup one way with no record, a checkout pulls the agent's own revision down, shows what changed before anything is sent, and leaves a revision behind.
- A live checkout is idempotent: taking one twice no longer opens a second lease, memory hydrates when a folder moves from `edit` to `live`, and an agent whose memory spans revisions fetches each part it needs.

These commands need an Olef Cloud deployment serving the agent revision and
checkout routes (`/v1/agents/{id}/revisions`, `/checkout`, `/baseline`). A
control plane older than those routes has nothing to answer them with.

## v3.17.2

- A cloud session no longer opens with a spurious `cli_version_substituted` notice. `ocloud` asks a worker for the `olef` release it pairs with, instead of sending its own version into a field that names the `olef` version the worker should run for a client's execs. Since the two now version apart, an `ocloud` 3.17.1 client was asking workers for an `olef` 3.17.1 that never existed, and every session fell back to the newest installed `olef` with a warning.
- The same comparison guards `cloud_client_too_old`, which refuses a session outright. That refusal was latent: once `olef` moved ahead of `ocloud` and worker images stopped carrying old enough `olef` builds, the `ocloud` version would have sorted below the oldest installed release and every session on those images would have failed. Asking for an `olef` version makes the check meaningful again.

## v3.17.1

- `ocloud` now ships on its own independent release train and version cadence from [olef-dev/ocloud](https://github.com/olef-dev/ocloud/releases), separate from `olef` (`olef-dev/olef`).
- `ocloud update` and background update notices now check `olef-dev/ocloud/releases/latest` (overrideable with `OCLOUD_UPDATE_LATEST_URL`) and keep their own cache in `~/.olef/ocloud-update-check.json`.
- Standalone `ocloud-installer.sh` / `ocloud-installer.ps1`, Homebrew (`olef-dev/tap/ocloud`), and Scoop (`ocloud`) now download directly from `olef-dev/ocloud` without coupling updates to `olef` releases.

## Earlier releases

Olef Cloud CLI (`ocloud`) shipped alongside `olef` in v3.17.0 on [olef-dev/olef](https://github.com/olef-dev/olef/releases/tag/v3.17.0) before moving to independent releases here.
