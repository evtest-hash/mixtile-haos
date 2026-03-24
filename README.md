# Mixtile HAOS

`mixtile-haos` is a thin overlay repository for building Home Assistant OS for Mixtile Edge 2.

## Layout

- `haos/`: upstream `home-assistant/operating-system` pinned to a stable release tag
- `external/`: Mixtile Edge 2 board support and patches

## Build

Builds run in GitHub Actions through `.github/workflows/build-release.yml`.

## Sync upstream

When upstream publishes a new stable HAOS release, move the `haos/` submodule to that tag, then rerun the build workflow.
