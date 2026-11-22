# Aarindam Photography Billing — Android project starter

This package contains the offline-first billing app web interface and a Capacitor configuration for packaging it as an Android app.

## Features in the included app
- Invoice creation and automatic invoice numbering
- Event types including Photoshoot and Reels
- Service charge fields: Photography / Cinematography, Travel, Editing, Others
- Partial payments and payment history
- Expense records and estimated profit/loss reports
- Invoice print flow (use Android print dialog / Save as PDF where supported)
- WhatsApp sharing
- JSON backup and restore
- Local browser/WebView storage; no account or server required

## Build an APK (requires a computer)

Install Node.js 20+ and Android Studio with the Android SDK. Then, from this folder:

```bash
npm install
npx cap add android
npx cap sync android
npx cap open android
```

In Android Studio, wait for Gradle sync, then choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**. For a shareable release, use **Build > Generate Signed Bundle / APK** and create/store your signing key safely.

The debug APK is usually generated under `android/app/build/outputs/apk/debug/`. A signed release APK is generated under the corresponding `release` folder.

## Important data note
Invoice and expense records are stored locally on that device. Use the app's **Export backup** regularly and keep the JSON backup somewhere safe. Clearing app data or uninstalling can erase local records. Test backup and restore before relying on it for business records.

## Current packaging status
This is an Android-ready Capacitor source project, not a compiled APK. An Android SDK/Gradle build environment is needed to generate and sign the APK. No signing key is included.


## Build APK from an Android phone using GitHub Actions (cloud build)

1. Sign in to GitHub in your phone browser and create a **private** repository named `aarindam-photography-app`.
2. Upload the contents of this project folder to the repository root (not the parent folder). Make sure `.github/workflows/android-apk.yml` is included.
3. Open the repository's **Actions** tab and allow workflows if GitHub asks.
4. Select **Build Aarindam Photography APK**, tap **Run workflow**, then **Run workflow** again.
5. Wait for the run to finish with a green check. Open that run, scroll to **Artifacts**, and download `Aarindam-Photography-debug-apk`.
6. Extract the ZIP on your phone and install `app-debug.apk`. Android may ask you to allow installation from your browser or file manager.

This workflow produces a debug-signed APK for private testing and installation. It is not a Play Store release build. Keep the GitHub repository private.

**Security / feature status:** The current source uses browser/WebView local storage and includes invoice, payment, expense, report, print-to-PDF, WhatsApp and JSON backup flows. A first-launch PIN lock is not implemented in this source package yet; do not treat the app as PIN-protected until that feature is added and tested.
