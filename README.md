# FaderBay — releases

Update feed and downloads for FaderBay, a per-application audio mixer and
router for macOS.

This repository contains no source. It exists because
[Sparkle](https://sparkle-project.org) cannot authenticate anywhere, so
the appcast it polls has to be served without a login.

- **Appcast:** <https://manuelmann.github.io/faderbay-releases/appcast.xml>
- **Downloads:** the `.dmg` files under [`docs/`](docs/)

Builds are signed with a Developer ID certificate and notarised by Apple.
Each entry in the appcast additionally carries an EdDSA signature that the
installed app verifies against the public key baked into it — so an update
is only accepted if it came from the holder of that key, whatever happens
to this repository.
