# 📱 Android App Template

GitHub Actions workflow templates for Android apps with **automatic releases**.

## 🚀 Features

- ✅ Automatic APK builds on every push
- ✅ Creates GitHub Releases (permanent, no expiry)
- ✅ Timestamped APK names: `app-20241228-2130.apk`
- ✅ Manual trigger via `workflow_dispatch`
- ✅ Version tags support (`v1.0.0`)

## 📋 Available Templates

| Template | Use For |
|----------|---------|
| `flutter-build.yml` | Flutter/Dart apps |
| `webview-build.yml` | React/Web apps wrapped in WebView |

## 🛠️ How to Use

### For New Projects

1. Create your new repo
2. Copy the appropriate workflow file to `.github/workflows/build.yml`
3. Push your code
4. APKs will appear in **Releases**

### For Existing Projects

1. Copy the workflow file to your repo's `.github/workflows/` folder
2. Rename to `build.yml`
3. Push — a new release will be created

## 📦 Download APKs

After each build:
1. Go to your repo's **Releases** tab
2. Download the latest `.apk` file
3. Install on Android device

## 🔧 Customization

### Change App Name in APK filename

**Flutter:** Reads from `pubspec.yaml` → `name:` field

**WebView:** Reads from `package.json` → `"name":` field

### Build Release APK (signed)

Replace in workflow:
```yaml
# Debug (unsigned but installable)
run: flutter build apk --debug

# Release (requires signing setup)
run: flutter build apk --release
```

### Add Signing for Play Store

Add secrets to your repo:
- `KEYSTORE_BASE64` - Base64 encoded keystore
- `KEYSTORE_PASSWORD`
- `KEY_ALIAS`
- `KEY_PASSWORD`

Then add signing step before build.

## 📁 Project Structure Expected

### Flutter
```
your-app/
├── .github/workflows/build.yml
├── pubspec.yaml
├── lib/
└── android/
```

### WebView/React
```
your-app/
├── .github/workflows/build.yml
├── package.json
├── src/
├── public/
└── android/
```

## 🏷️ Version Tags

Create a version release:
```bash
git tag v1.0.0
git push origin v1.0.0
```

This triggers a build with the tag name.

---

Made with 🤖 by Claude
