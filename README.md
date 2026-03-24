# Mixtile HAOS

`mixtile-haos` is a thin overlay repository for building Home Assistant OS for Mixtile Edge 2.

## Layout

- `haos/`: upstream `home-assistant/operating-system` pinned to a stable release tag
- `external/`: Mixtile Edge 2 board support and patches
- `.github/workflows/`: build, sync, and historical backfill automation

## Branch model

- `main`: the only long-lived branch, always tracking the latest stable HAOS release line
- `port/<version>`: temporary historical or next-major adaptation branch, for example `port/11.5`
- release tags: `mixtile-haos-<haos-version>-r<revision>`

## Release policy

- historical majors are published once and then frozen
- historical backfill starts at `11.5`
- the fixed historical targets are `11.5`, `12.4`, `13.2`, `14.2`, `15.2`, `16.3`, and `17.1`
- future work stays on `main` and follows the latest stable HAOS release only

## Workflows

- `Build Mixtile Edge 2`: validates any `git_ref`, or publishes a validated tag when `mode=publish`
- `Sync latest HAOS release`: watches the latest official HAOS stable release and opens an issue when `main` is behind upstream
- `Backfill major release`: validates one historical `port/<version>` branch at a time; the `port/<version>` branch must already be prepared and pushed
- `Publish validated release`: tags a validated ref as `mixtile-haos-<version>-rN` and dispatches the publish build
