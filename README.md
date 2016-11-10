
# servo-nightly

[![Build Status](https://travis-ci.org/servo/servo-nightly.svg?branch=master)](https://travis-ci.org/servo/servo-nightly), nightly builds [here](https://github.com/servo/servo-nightly/releases)

This repo contains my scripts for automatic build testing on Travis.

- `update_servo.sh`: runs locally, updates or pulls the latest Servo in `./servo`
- `update_tags.py`: runs locally, creates and uploads a new Git tag, which triggers the Travis build. Combine with `update_servo.sh`. Requires `GITHUB_TOKEN` to be set.
- `setup_android.sh`: sets up Android SDK and NDK on Travis
- `upload_to_github.py`: if the build is successful, uploads `./servo/$ASSET_NAME` to GitHub for the latest tag. Requires `GITHUB_TOKEN` to be set.

Interested in cross-compiling Servo? Here is a short guide for ARM and AArch64: [mmatyas.github.io/blog/servo-short-cross-compilation-guide](https://mmatyas.github.io/blog/servo-short-cross-compilation-guide)

## Encrypted environment variables for artifact upload

In https://travis-ci.org/servo/servo-nightly/settings, under `environment
variables`, make sure that `GITHUB_TOKEN` is set to a valid token and the
"display value in build log" switch is set to "off".

To get a token, log in to GitHub as bors-servo (the credentials are saved in
the usual place) and navigate to https://github.com/settings/tokens . If
you're replacing a token, delete the old one. Then create a token with a
useful name like "servo-nightly deployment" and the `public_repo` permission,
and assign its value to `GITHUB_TOKEN` in the Travis settings UI lined above.
