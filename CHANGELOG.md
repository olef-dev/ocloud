# Changelog

Release notes for Olef Cloud CLI (`ocloud`). Every release, with its binaries, is on the
[Releases page](https://github.com/olef-dev/ocloud/releases).


## v3.17.1

- `ocloud` now ships on its own independent release train and version cadence from [olef-dev/ocloud](https://github.com/olef-dev/ocloud/releases), separate from `olef` (`olef-dev/olef`).
- `ocloud update` and background update notices now check `olef-dev/ocloud/releases/latest` (overrideable with `OCLOUD_UPDATE_LATEST_URL`) and keep their own cache in `~/.olef/ocloud-update-check.json`.
- Standalone `ocloud-installer.sh` / `ocloud-installer.ps1`, Homebrew (`olef-dev/tap/ocloud`), and Scoop (`ocloud`) now download directly from `olef-dev/ocloud` without coupling updates to `olef` releases.

## Earlier releases

Olef Cloud CLI (`ocloud`) shipped alongside `olef` in v3.17.0 on [olef-dev/olef](https://github.com/olef-dev/olef/releases/tag/v3.17.0) before moving to independent releases here.
