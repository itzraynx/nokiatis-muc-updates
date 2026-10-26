# Nokiatis MUC update security

Download Nokiatis MUC only from the Releases in this repository:

https://github.com/itzraynx/nokiatis-muc-updates/releases

Official Android package:

```text
com.nokiatis.muc
```

Official Team Nokiatis signing certificate SHA-256:

```text
DD:A7:F0:01:A4:DC:1D:A3:A7:C3:9C:0A:45:C8:10:10:C0:E6:6A:D0:A4:A9:52:F8:15:E7:9E:E6:98:C1:EF:C6
```

An APK from another site, or an APK whose checksum or signing certificate does not match the official release information, is not an official Team Nokiatis update.

The in-app updater verifies the manifest, APK size, SHA-256, package name and version before opening Android's installer. Android itself also refuses to install an update over Nokiatis MUC if the new APK is signed with a different key.
