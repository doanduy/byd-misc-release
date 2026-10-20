# BYD Camera diagnostic ZIPs

Public uploads explicitly submitted from the Diagnostics tab. Archives can include vehicle API information, settings, event logs, raw camera images and stitched images. Anyone can download them; deleting a file does not remove Git history or copies.

Layout: `logs/<app-id>/YYYY/MM/<timestamp>-<uuid>.zip`. This app writes only under `logs/byd-camera/`. Other apps should use their own app-id. No VIN or account identifier in filenames. Maximum app upload: 20 MiB. Larger archives can be exported locally.

## Configure upload

Create a fine-grained GitHub token limited to **doanduy/byd-misc-release**, with **Contents: Read and write**, and an expiration date. Enter it directly on the vehicle under Diagnostics. Android Keystore encrypts it locally; it is not embedded in the APK or exported in diagnostic ZIPs. GitHub repository tokens cannot be restricted to a single folder: use this only on a trusted personal head unit. Never post the token here.

Choose Send log and confirm public upload. Copy the resulting link for debugging. Uploads are manual; the app does not upload automatically. Keep local export as a fallback for network/authorization failures.
