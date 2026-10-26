# Team Nokiatis release process

This file records the safe order for publishing a mandatory Nokiatis MUC update. The order matters: never point users to an APK that has not been built, downloaded back from GitHub and verified.

## 1. Build in the private source repository

1. Bump the app marketing version and Android `versionCode`.
2. Every release must use a strictly higher `versionCode` than the previous official release.
3. Build with the stable Team Nokiatis release key.
4. Download the built APK from the CI/release artifact; do not trust only the local filename.

## 2. Verify the APK before publishing

Confirm all of the following:

- package: `com.nokiatis.muc`;
- expected version name and `versionCode`;
- ZIP integrity;
- exact byte size;
- SHA-256 checksum;
- signer certificate SHA-256:

```text
DDA7F001A4DC1DA3A7C39C0A45C81010C0E66AD0A4A952F815E79EE698C1EFC6
```

## 3. Create the public GitHub Release

Create a release tagged `vX.Y.Z` in this repository and attach:

- `NokiatisMUC-vX.Y.Z.apk`;
- a copy of the new `update.json` as a release asset, used by the app as its secondary manifest source.

The release notes must include the version, versionCode, file size, SHA-256, signer fingerprint, direct APK link and a clear instruction to install over the existing app without uninstalling.

## 4. Publish `update.json` last

Only after the APK asset is uploaded and its public download works, replace `update.json` on `main` with the new manifest.

For a fully mandatory release:

```json
{
  "schemaVersion": 1,
  "channel": "stable",
  "packageName": "com.nokiatis.muc",
  "latestVersion": "X.Y.Z",
  "latestVersionCode": 123,
  "minSupportedVersionCode": 123,
  "forceUpdate": true
}
```

The rest of the manifest contains the exact APK URL, filename, byte size, SHA-256, signing-certificate SHA-256, release page, notes and publication time.

## 5. Verify the public channel

Before announcing the update:

1. Open the public release while signed out or in a private/incognito window.
2. Download the APK from the public direct link.
3. Re-check its size and SHA-256 against `update.json`.
4. Open the raw `update.json` URL and confirm it is valid JSON.
5. Test on a device with the previous official version installed, with existing library/download data.
6. Confirm the old version locks, downloads, verifies, opens Android's installer, updates in place and preserves data.

## Important limits

- Android does not allow an ordinary sideloaded app to silently install its own update. The user must confirm in Android's installer. The first in-app update may also require enabling **Allow from this source** for Nokiatis MUC.
- Versions older than 1.5.0 do not contain the mandatory gate, so they cannot be retroactively locked.
- A device that has never reached the update feed while online cannot know that a newer mandatory release exists. Once v1.5.0 or later sees the mandate, the app stores it and remains locked offline.
- Never commit APK files to Git history. APKs belong only in GitHub Release assets.
