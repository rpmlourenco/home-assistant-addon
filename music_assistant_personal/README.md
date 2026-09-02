# Music Assistant (rpmlourenco)

This add-on runs a prebuilt ARM64 image from
[`rpmlourenco/server`](https://github.com/rpmlourenco/server). It is intended
for personal testing of that fork on Home Assistant OS.

The add-on version must match an image tag published by the `Publish personal
Music Assistant image` workflow in the server repository. To deploy a new
fork revision, publish the image with a new version and update `version` in
`config.yaml` to that same value.
