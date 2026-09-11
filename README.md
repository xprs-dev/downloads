# XPRS downloads

This repository serves the current XPRS release files at
https://xprs.dev/downloads/ (for example
`https://xprs.dev/downloads/v1.2.17/xprs-1.2.17-android-arm64-v8a.apk`).

It holds no binaries. `.github/workflows/publish.yml` runs every hour, takes
the newest stable release and the newest release overall from
[xprs-dev/app](https://github.com/xprs-dev/app/releases), and deploys their
files to GitHub Pages as an artifact. `tags.txt` records what is deployed.

The update feed at https://xprs.dev/updates/ (written by the
[website](https://github.com/xprs-dev/xprs-dev.github.io)'s `sync.yml`) points
at these files, and waits until a release is here before it names it. An XPRS
phone normally fetches an update by sha256 over Reticulum from an always-on
station; this site is the fallback, and what the download page links to.

To publish a release right away instead of waiting for the hour:

```sh
gh workflow run publish.yml -R xprs-dev/downloads
```

See `docs/f-droid.md` and `release.sh` in the app repository.
