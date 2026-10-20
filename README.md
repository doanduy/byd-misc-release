# byd-misc-release

Public APK releases and per-project update manifests for BYD apps. Source code and signing keys are not stored here. Voluntarily submitted public diagnostic ZIPs are stored under logs/<app-id>/YYYY/MM/. See [BYD Camera log setup](logs/byd-camera/README.md).

## Projects

| App | Package | Stable manifest |
| --- | --- | --- |
| BYD Camera | vn.duy.bydcamera | [stable.json](apps/byd-camera/stable.json) |

## Multi-project convention

- Release tags: `<app-id>/v<version>`, e.g. `byd-camera/v0.3.1`.
- Each app uses `apps/<app-id>/stable.json`; optional beta channel uses `beta.json`.
- Never use the global `/releases/latest` endpoint to update an app: it may refer to another project.
- Each app owns its package name, increasing Android versionCode and signing certificate.
- APK filenames contain the app name, version and ABI.

## Publish a version

1. Build and test signed release APKs in the source project. Preserve the certificate for upgrades.
2. Create a namespaced release and upload APK assets plus SHA256SUMS.txt.
3. Verify downloaded assets, sizes and SHA-256.
4. Update only that app's manifest on main after the assets are available.
5. Do not replace published APKs. Use a higher versionCode for fixes. Keep old releases for manual recovery.

## Manifest schema 1

Required fields: schemaVersion, appId, packageName, versionName, versionCode, minSdk, notes, assets. Assets are keyed by Android ABI (arm64-v8a, armeabi-v7a); each has url, size (bytes) and sha256.

## Install and update BYD Camera

Install 0.3.1 manually once. In 0.3.2+, open the Updates tab and select **Kiểm tra bản cập nhật**. The app selects a supported ABI and verifies SHA-256, size, package, versionCode and signing certificate before opening Android installation. Grant permission to install from BYD Camera when prompted, then select **Cài APK đã tải**. Android asks for installation confirmation.

Requires Android 10/API 29 or newer. Downloading updates needs no GitHub token. Uploading diagnostic ZIPs requires a repository-scoped token entered on the vehicle. Firmware-specific installation restrictions still apply.
