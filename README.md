# FaderBay — releases

Update feed and downloads for FaderBay, a per-application audio mixer and
router for macOS.

This repository contains no source. It exists because the source
repository is private and the update feed has to be reachable without a
credential — Sparkle will send any HTTP header you give it, but a token
baked into every copy of an app is a shared secret, not a login.

- **Appcast:** <https://manuelmann.github.io/faderbay-releases/appcast.xml>
- **Downloads:** the `.dmg` files under [`docs/`](docs/). The newest is
  whichever one the first `<enclosure>` in the appcast names — the
  directory listing is alphabetical, not chronological. The `.delta`
  files beside them are update patches, not installers.

## Before you download

- **Requires macOS 26 or newer.** Every appcast entry carries a
  `sparkle:minimumSystemVersion`; that is the authority, not this line.
- **It lives in the menu bar.** Launching it opens no window and puts
  nothing in the Dock.
- **It asks once for permission to record audio.** That permission is how
  it sees other applications' output at all — there is no mixer without
  it.
- **It offers to install a Core Audio driver.** That step asks for an
  administrator password and restarts Core Audio, which stops audio for a
  moment in *every* application on the Mac, and then quits FaderBay so
  its taps are not torn down mid-flight. Declining is fine: per-app
  faders, routing and metering all work without it. What the driver adds
  is a device for the Mac's volume keys to act on, per-app gain applied
  inside the sink, and the loopback send.
- **It updates itself.** It checks daily and offers; it never installs
  without asking.

## What the signatures mean

Builds are signed with a Developer ID certificate and notarised by Apple.
Each entry in the appcast additionally carries an EdDSA signature that the
installed app verifies against the public key baked into it — so an update
is only accepted if it came from the holder of that key, whatever happens
to this repository.

There is no changelog here. The appcast carries no release notes and the
release pages live in the private source repository.
