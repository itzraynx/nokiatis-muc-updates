# Nokiatis MUC — Official Updates

Official update feed and signed Android APK releases for **Nokiatis MUC** by **Team Nokiatis**.

## Download the latest official release

➡️ **[Latest Nokiatis MUC release](https://github.com/itzraynx/nokiatis-muc-updates/releases/latest)**

Install the APK **over your existing Nokiatis MUC app**. Do not uninstall first. Because official updates use the same Android package and the same Team Nokiatis signing key, Android preserves your library, playlists, likes, settings and downloaded songs.

## What belongs in this repository

This public repository is only for:

- the official `update.json` feed read by Nokiatis MUC;
- signed official APK files attached to GitHub Releases;
- release notes and update instructions.

The app's private source code is not stored here.

## In-app updates

From Nokiatis MUC **1.5.0** onward, the app checks this repository's official update feed. When Team Nokiatis marks a release as required, older supported installs must update before continuing.

The update inside the app will:

1. download the official APK with progress;
2. verify its file size and SHA-256 checksum;
3. verify that it is package `com.nokiatis.muc` with the expected version;
4. verify the Team Nokiatis signing certificate when Android exposes it for the downloaded archive;
5. open Android's package installer.

Android still shows its own final **Install/Update** confirmation. Normal Android apps distributed outside Google Play cannot silently install an APK or bypass that system confirmation.

## Verify an official APK

Official builds use:

- **Package:** `com.nokiatis.muc`
- **Signer:** Team Nokiatis
- **Signing certificate SHA-256:**

```text
DD:A7:F0:01:A4:DC:1D:A3:A7:C3:9C:0A:45:C8:10:10:C0:E6:6A:D0:A4:A9:52:F8:15:E7:9E:E6:98:C1:EF:C6
```

Each release and the `update.json` feed publish the APK's exact size and SHA-256. Only download Nokiatis MUC from this repository's Releases.
