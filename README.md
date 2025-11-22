# Hello World: Minimal Kotlin APK Template

**Compile Android APKs in 2 minutes - ZERO installation required!**

> **Just click "Use this template" and start coding - no Android Studio, no SDK, no JDK needed!**

## 🚀 How It Works

This template uses **GitHub Actions** to compile your APK automatically. You only need a GitHub account - no development tools required!

### 3-Step Process:
1. **Click "Use this template"** → Create your repository
2. **Edit code directly on GitHub**
3. **Download APK from Actions tab**

Your APK compiles automatically on every code change!

## 🎯 Get Started Now

### Step 1: Create Your Project
- Click the **"Use this template"** button above
- Name your new repository
- Create it (public or private)

### Step 2: Customize Your App
Edit these files directly on GitHub:

| File | What to Change |
|------|----------------|
| `app/src/main/res/values/strings.xml` | App name & text |
| `app/src/main/res/layout/activity_main.xml` | UI layout |
| `app/src/main/res/values/colors.xml` | Color scheme |
| `app/src/main/java/.../MainActivity.kt` | App logic |

### Step 3: Get Your APK
1. After saving changes, go to **Actions** tab
2. Click the latest workflow run
3. Download the `app-debug-apk` artifact
4. Install on your Android device!

## 📁 Project Overview

```
./
├── app/                               # Your app code here
│   └── src/main/
│       ├── java/.../MainActivity.kt   # Main logic
│       ├── res/layout/                # UI layouts
│       └── res/values/                # Strings, colors, themes
├── fastlane/                         # Play Store setup
└── .github/workflows/build.yml       # Auto-compilation!
```

## 🛠️ Advanced Features

### Local Development (Optional)
If you want to fully develop locally later:

```bash
git clone your-repo-url
./gradlew assembleDebug
```

*Git push will also trigger a github action to compile the apk, you don't really need local tools*

### Play Store Ready
Includes Fastlane configuration and all required store metadata.

## 🌟 Why This Template?

- ✅ **Zero installation** - code in browser, get APK
- ✅ **Instant setup** - 2 minutes from template to APK
- ✅ **Professional foundation** - proper structure
- ✅ **Play Store compatible** - includes all metadata

---

**Ready to start? Click "Use this template" above!** 🚀

