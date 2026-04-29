# 🍎 MAX PLAYER — iOS Build Guide

> **Important:** iOS builds require **macOS + Xcode**. Flutter on Windows does NOT support `flutter build ios`.

---

## Why iOS Build Fails on Windows

```
flutter build ios --release
# Error: Could not find an option named "--release".
```

The Flutter SDK on Windows only supports these build targets:
- `flutter build apk` — Android APK
- `flutter build appbundle` — Android App Bundle
- `flutter build web` — Web app
- `flutter build windows` — Windows desktop

**iOS is NOT available on Windows** because Apple requires Xcode (macOS only).

---

## ✅ iOS Source Code Status

Your iOS project is **fully configured** and ready to build on macOS:

| File | Status |
|------|--------|
| `ios/Runner/Info.plist` | ✅ Configured |
| `ios/Runner.xcodeproj/project.pbxproj` | ✅ Configured |
| `ios/Runner/AppDelegate.swift` | ✅ Ready |
| `ios/Runner/Assets.xcassets/AppIcon.appiconset/` | ✅ Icons generated |
| `ios/Flutter/Release.xcconfig` | ✅ Ready |

---

## 🛠️ Build Steps (macOS Required)

### 1. Prerequisites
- macOS 12+ (Monterey or newer)
- Xcode 14+ (from Mac App Store)
- Flutter SDK installed on Mac
- CocoaPods: `sudo gem install cocoapods`

### 2. Clone/Transfer Project to Mac
```bash
# Option A: Git clone
git clone <your-repo-url>
cd MAX_PLAYER

# Option B: Copy from Windows via USB/Cloud
# Copy entire project folder to Mac
```

### 3. Install Dependencies
```bash
flutter pub get
```

### 4. Install iOS Pods
```bash
cd ios
pod install
cd ..
```

### 5. Build for iOS Device (Debug)
```bash
flutter build ios --debug
```

### 6. Build for iOS Device (Release)
```bash
# Requires Apple Developer account for signing
flutter build ios --release
```

### 7. Build IPA for Distribution
```bash
# Creates .ipa file for TestFlight/App Store
flutter build ipa

# Output: build/ios/ipa/MAX_PLAYER.ipa
```

### 8. Build without Code Signing (Testing only)
```bash
flutter build ios --no-codesign
```

---

## 📋 Flutter iOS Build Options

```bash
flutter build ios --help
```

| Flag | Purpose |
|------|---------|
| `--debug` | Debug build (default) |
| `--release` | Release build (optimized) |
| `--no-codesign` | Skip code signing |
| `--simulator` | Build for iOS Simulator |

---

## 🔧 Troubleshooting

### "Could not find an option named --release"
**Cause:** You're on Windows.  
**Fix:** Use a Mac with Xcode installed.

### "CocoaPods not installed"
```bash
sudo gem install cocoapods
```

### "No valid code signing certificates"
**Fix:** Open Xcode → Preferences → Accounts → Add Apple ID → Download certificates.

---

## 📱 Already Built Successfully

| Platform | Status | File |
|----------|--------|------|
| **Android** | ✅ Built (98.3 MB) | `website/MAX-PLAYER-v3.0.apk` |
| **iOS** | ⏳ Ready (needs Mac) | Source in `ios/` folder |
| **Web** | ✅ Available | `flutter build web` |
| **Windows** | ✅ Available | `flutter build windows` |

---

## 🚀 Quick Reference

```bash
# Android (works on Windows/Linux/Mac)
flutter build apk --release

# iOS (macOS ONLY)
flutter build ios
flutter build ipa

# Web
flutter build web --release

# Windows
flutter build windows --release
```

---

**Your iOS code is ready — just needs a Mac to compile!** 🍎
