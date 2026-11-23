# Security policy

## Reporting a vulnerability

Please do not open a public issue for security problems.

Report them privately through GitHub: open the
[Security tab](https://github.com/olef-dev/ocloud/security) and
choose **Report a vulnerability**. If you can't use GitHub, email
[contact@olef.dev](mailto:contact@olef.dev) with "Security" in the
subject.

Include the `ocloud` version (`ocloud --version`), your host OS, and the
steps to reproduce. We aim to acknowledge reports within three business days.

## Supported versions

Security fixes go into the latest release. Update with `ocloud update` or
your package manager.

## Scope

`ocloud` manages Olef Cloud authentication, workspace file sync and its secret
guard, SSH/port-forwarding tunnels, remote device leases, and local workspace/device
hosts (`ocloud host`). Reports about any of them are in scope, including
credential storage, secret redaction, host isolation, and local attachment
records (see
[security and redaction](https://github.com/olef-dev/olef/blob/main/docs/security-and-redaction.md)).
