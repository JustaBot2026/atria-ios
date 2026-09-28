# Atria on iPhone from Windows

This copy includes a GitHub Actions workflow that builds an **unsigned iPhone IPA** on a GitHub-hosted Mac.

## Requirements

- iPhone on **iOS 26.1 or newer** (Atria's current deployment target).
- WHOOP **4.0** for strap connectivity.
- A GitHub account.
- SideStore or Sideloadly on Windows for signing/installing the generated IPA.

## Build the IPA

1. Put the full contents of this repository on GitHub.
2. Confirm this file exists on GitHub:
   `.github/workflows/build-atria-ipa.yml`
3. Open the **Actions** tab.
4. Select **Build Atria iPhone IPA**.
5. Click **Run workflow**.
6. Wait for the run to finish.
7. Open the successful run and download the artifact **Atria-iPhone-unsigned**.
8. Unzip that artifact. It contains `Atria-iPhone-unsigned.ipa`.

## Install from Windows

Import `Atria-iPhone-unsigned.ipa` into SideStore or Sideloadly and let that tool sign it with your Apple Account.

The workflow intentionally removes the widget extension from the final sideload IPA. The widget requires an App Group and creates extra provisioning/App-ID complexity for a free Apple Account. The core Atria app remains present. HealthKit may be unavailable in a sideloaded/free-signing build if the resulting provisioning profile does not contain the HealthKit entitlement; Atria checks for that entitlement before HealthKit operations.

## WHOOP pairing

Atria is currently designed for WHOOP 4.0. Before pairing, make sure the official WHOOP app is not actively connected to the strap. Open Atria and follow its pairing flow.

## If GitHub Actions fails

Download the `Atria-build-log` artifact from the failed run and send that log back for diagnosis.
