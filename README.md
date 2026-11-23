# Olef Cloud CLI (`ocloud`)

**Olef Cloud control plane, remote workspaces, cloud emulators, remote device leasing, and host daemon.**

**Website:** [olef.dev](https://olef.dev) ·
**Releases:** [latest](https://github.com/olef-dev/ocloud/releases/latest) ·
**Docs & Issues:** [olef-dev/olef](https://github.com/olef-dev/olef)

This repository holds public binary releases and the changelog for `ocloud`.
The local device toolbelt (`olef`), full user documentation, agent plugins, and issue tracker live at [olef-dev/olef](https://github.com/olef-dev/olef).

Free for everyone, including commercial use; see [LICENSE.md](LICENSE.md).

## Install

Homebrew (macOS, Linux — also installs `olef`):

```bash
brew install olef-dev/tap/ocloud
```

Shell installer (macOS, Linux — standalone `ocloud` binary):

```bash
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/olef-dev/ocloud/releases/latest/download/ocloud-installer.sh | sh
```

Windows (Scoop — also installs `olef`, or the standalone PowerShell installer):

```powershell
scoop bucket add olef https://github.com/olef-dev/scoop-bucket
scoop install ocloud
```

```powershell
powershell -ExecutionPolicy Bypass -c "irm https://github.com/olef-dev/ocloud/releases/latest/download/ocloud-installer.ps1 | iex"
```

## Quickstart

```bash
ocloud login                    # sign in through app.olef.dev
ocloud link                     # link this project to a cloud workspace
ocloud run -- olef app apply    # build and run on the cloud workspace
ocloud workspace attach         # expose the workspace emulator locally for `olef`
ocloud devices catalog          # browse cloud emulators and remote phones
ocloud host setup               # register this machine as a workspace/device host
ocloud update                   # check for newer `ocloud` releases
```

## Security

See [SECURITY.md](SECURITY.md).
