# Kotlin Apk Template 🚀

A complete, ready-to-use template for building Android apps in Kotlin. This project automates the boring stuff: compiling, signing, and releasing your APKs using GitHub Actions and Fastlane.

## 🌟 Features

- **Kotlin First**: Modern Android development setup
- **Zero Config Debug Builds**: Just push code, get an APK
- **Automated Releases**: Tag a version, get a signed APK ready for the store
- **Fastlane Integration**: Industry-standard automation tool included
- **Store Ready**: Folder structure for icons, screenshots, and descriptions

## 🏁 Step-by-Step Guide for Beginners

Follow these steps to build your first Android App using this template.

### Step 1: Create Your Repository

1. Click the green "Use this template" button at the top of this page
2. Choose "Create a new repository"
3. Give it a name (e.g., `my-awesome-app`) and create it

### Step 2: Customize the Package Name

By default, the app is named `com.example.helloworld`. You must change this to your own unique ID (e.g., `com.yourname.coolapp`).

1. Clone your new repo to your computer
2. Open `app/build.gradle` and change `namespace` and `applicationId`
3. Open `app/src/main/AndroidManifest.xml` and change `package="..."`
4. Rename the folder structure in `app/src/main/java/` to match your new package
5. Update `fastlane/Appfile` with the new package name

### Step 3: Generate a Signing Key (The "Signature")

To publish an app or install a Release version, it must be "signed" with a digital key that only you possess.

On Linux or Termux, run this command:
```bash
keytool -genkey -v -keystore release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-alias
```

(Replace `my-alias` and `my-password` with your own secure values)

- It will ask for a password. Remember it
- It will ask for details (Name, Organization, etc.). You can fill them or skip
- At the end, type `yes` to confirm
- You now have a file named `release-key.jks`. **DO NOT commit this file to GitHub**

### Step 4: Add Secrets to GitHub

GitHub needs permission to use your key and upload releases.

1. **Encode your key to Base64**:
   ```bash
   base64 -w 0 release-key.jks > keystore_b64.txt
   ```
   (On Mac, omit the `-w 0` part)

2. **Go to GitHub**:
   - Navigate to your repository **Settings > Secrets and variables > Actions**
   - Click **New repository secret**
   - Add these 4 Secrets:

| Name | Value | Description |
|------|-------|-------------|
| `SIGNING_KEY_STORE_BASE64` | Copy the entire content of `keystore_b64.txt` | The Base64 string of your `release-key.jks` file |
| `SIGNING_KEY_ALIAS` | `my-alias` | The alias name you set when running keytool |
| `SIGNING_KEY_PASSWORD` | Your key password | The password for the specific key within the keystore |
| `SIGNING_STORE_PASSWORD` | Your store password | The password for the entire `.jks` file |

### Step 5: Build & Release!

**To get a DEBUG APK (For testing):**
1. Make a change to your code
2. Push to the `main` branch
3. Go to the **Actions** tab on GitHub
4. Click the workflow run → **Download debug-apk** from Artifacts

**To get a RELEASE APK (For the Public):**
1. Create a tag with a version number (e.g., `v1.0.0`)
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
2. Go to the **Actions** tab
3. Watch the "Android Fastlane CI" workflow run
4. Once finished, go to the **Releases** section on the right side of your repo main page
5. You will see **Release v1.0.0** with your signed `app-release.apk` ready to download!

## 📂 Project Files Explained

```
├── .github/workflows/android.yml  # The brain. Configures GitHub Actions for CI/CD
├── app/
│   ├── src/main/
│   │   ├── java/                  # Your Kotlin code lives here (standard Android structure)
│   │   │   └── .../MainActivity.kt
│   │   ├── res/                   # Layouts (XML), colors, and drawables
│   │   └── AndroidManifest.xml    # App settings (permissions, name, icon, activities)
│   └── build.gradle               # Module dependencies, version codes, and configuration
├── fastlane/
│   ├── Fastfile                   # Scripts for automating the build process (debug/release)
│   └── Appfile                    # Configuration for the app's package name
├── store_assets/                  # RECOMMENDED: For publishing to app stores
│   ├── icon_512.png               # High-res icon (512x512px)
│   ├── feature_graphic.png        # Banner/Cover image (1024x500px)
│   ├── screenshots/               # Folder for 8 screenshots (phone, tablet, etc.)
│   └── metadata/                  # Folder for localized descriptions, release notes, etc.
├── gradlew                        # Script to run Gradle on Linux/Mac
└── README.md                      # This file
```

## 🛠 Tech Stack

- **Language**: Kotlin
- **Min SDK**: Android 5.0 (API 21)
- **Target SDK**: Android 14 (API 34)
- **CI/CD**: GitHub Actions + Fastlane
