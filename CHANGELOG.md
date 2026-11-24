# Changelog

Release notes for Olef Cloud CLI (`ocloud`). Every release, with its binaries, is on the
[Releases page](https://github.com/olef-dev/ocloud/releases).


## v3.17.2

- A cloud session no longer opens with a spurious `cli_version_substituted` notice. `ocloud` asks a worker for the `olef` release it pairs with, instead of sending its own version into a field that names the `olef` version the worker should run for a client's execs. Since the two now version apart, an `ocloud` 3.17.1 client was asking workers for an `olef` 3.17.1 that never existed, and every session fell back to the newest installed `olef` with a warning.
- The same comparison guards `cloud_client_too_old`, which refuses a session outright. That refusal was latent: once `olef` moved ahead of `ocloud` and worker images stopped carrying old enough `olef` builds, the `ocloud` version would have sorted below the oldest installed release and every session on those images would have failed. Asking for an `olef` version makes the check meaningful again.

## v3.17.1

- `ocloud` now ships on its own independent release train and version cadence from [olef-dev/ocloud](https://github.com/olef-dev/ocloud/releases), separate from `olef` (`olef-dev/olef`).
- `ocloud update` and background update notices now check `olef-dev/ocloud/releases/latest` (overrideable with `OCLOUD_UPDATE_LATEST_URL`) and keep their own cache in `~/.olef/ocloud-update-check.json`.
- Standalone `ocloud-installer.sh` / `ocloud-installer.ps1`, Homebrew (`olef-dev/tap/ocloud`), and Scoop (`ocloud`) now download directly from `olef-dev/ocloud` without coupling updates to `olef` releases.

## Earlier releases

Olef Cloud CLI (`ocloud`) shipped alongside `olef` in v3.17.0 on [olef-dev/olef](https://github.com/olef-dev/olef/releases/tag/v3.17.0) before moving to independent releases here.
