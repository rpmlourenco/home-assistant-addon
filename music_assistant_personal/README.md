# Music Assistant (rpmlourenco)

This add-on runs a prebuilt ARM64 image from
[`rpmlourenco/server`](https://github.com/rpmlourenco/server). It is intended
for personal testing of that fork on Home Assistant OS.

The add-on version must match an image tag published by the `Publish personal
Music Assistant image` workflow in the server repository. To deploy a new
fork revision, publish the image with a new version and update `version` in
`config.yaml` to that same value.

## Current image

The image repository is:

```text
ghcr.io/rpmlourenco/server
```

The exact image tag is the `version` value in `config.yaml`. The catalog version
must only be changed after the matching image has been built and published
successfully.

## Maintenance documentation

The server repository is the single source of truth for the personal changes,
image architecture, build procedure and upgrades from new Music Assistant
stable versions:

[Personal Music Assistant fork maintenance guide](https://github.com/rpmlourenco/server/blob/main/docs/PERSONAL_FORK.md)

The server is maintained on `main`. Numbered releases use immutable Git tags and
matching image/add-on versions; old version branches are historical only.

## Updating Home Assistant

1. Refresh the repositories in **Settings → Apps**.
2. Open **Music Assistant (rpmlourenco)**.
3. Confirm that the offered version matches `config.yaml` and an existing image
   tag.
4. Create an appropriate backup.
5. Run the add-on update.
6. Confirm that the add-on returns to **Running** and the Music Assistant UI
   opens normally.

Updating this add-on restarts its container; it does not require a full Home
Assistant restart.
