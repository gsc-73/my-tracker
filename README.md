# My Tracker — Capacitor WebView APK

Wraps https://gsc-73.github.io/Study_tracker/ into an installable Android APK,
using Capacitor (same approach as your other working app-building repo).

## How to use

1. Delete the old files from your GitHub repo (or make a new repo) and upload
   everything in this project, keeping the folder structure:
   - `.github/workflows/build-apk.yml`
   - `package.json`
   - `capacitor.config.json`
   - `www/index.html`
   - `icon-assets/` (5 icon PNGs)
   - `.gitignore`
2. Commit to `main`.
3. Go to the **Actions** tab → "Build Android APK" → **Run workflow**
   (or it runs automatically on push).
4. Wait ~3-5 minutes (first run is slower since it installs npm packages and
   generates the native Android project from scratch).
5. Open the finished run → **Artifacts** → download `MyTracker-debug-apk`.
6. Unzip it → `app-debug.apk` → send to your phone → install
   (allow "install unknown apps" when prompted).

## Why this should work better

Capacitor generates the entire `android/` folder (Gradle files, AGP version,
Kotlin stdlib versions, JDK compatibility) itself, matched to versions that
are tested together. That's what was causing the repeated Gradle/JDK/Kotlin
conflicts in the hand-written version — this avoids all of that.

## Changing things later

- **App name**: `appName` in `capacitor.config.json`
- **Website URL**: `server.url` in `capacitor.config.json`
- **Package/app ID**: `appId` in `capacitor.config.json`
- **Icon**: replace the 5 PNGs in `icon-assets/` (keep the same filenames)

Any change → push to `main` → Actions rebuilds automatically.
