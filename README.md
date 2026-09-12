# Phonotheca releases

Download binaries for **Phonotheca**, a native macOS audio metadata editor.

This repository holds **release artifacts only** — it is not a source
repository. Every build here is compiled from
[`mysideproject/phonotheca`](https://github.com/mysideproject/phonotheca),
which is private and carries no tags; `main` there is what a release is built
from.

## Installing

Download the `.dmg` from the latest release and drag **Phonotheca** to
`Applications`. The `.zip` is the same app, archived — it is what the in-app
updater consumes.

Requirements: **Apple Silicon** (arm64), **macOS 26.0 or later**.

## Verifying a download

Every build is Developer ID signed, notarized by Apple and stapled, so
Gatekeeper accepts it without any prompt:

```sh
codesign -dv --verbose=2 /Applications/Phonotheca.app   # Developer ID Application: xiaobao luo (F896M7924Y)
spctl -a -vvv -t exec /Applications/Phonotheca.app      # accepted, source=Notarized Developer ID
xcrun stapler validate /Applications/Phonotheca.app
```

## Updates

The app updates itself through an Ed25519-signed feed at
<https://phonotheca-landing.pages.dev/appcast.xml>. Only an archive signed by
this project's release key is ever installed, so a compromised mirror cannot
push an update — and the check is gated on a key that only a released build
carries, meaning a build compiled from source performs no check and opens no
connection at all.

## Licensing

Phonotheca is a renamed continuation of
[AudioMator](https://github.com/ChrisLloydME/AudioMator) by Christopher Lloyd,
kept under the MIT license. Third-party components and their terms are listed
in the app itself under `Contents/Resources/Licenses/` and in the
[NOTICE](https://github.com/mysideproject/phonotheca/blob/main/NOTICE.md).
