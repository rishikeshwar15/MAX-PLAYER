# 🍎 MAX PLAYER — iOS Build Guide (No Mac Required!)

## ⚠️ Problem: Windows-ல் iOS Build செய்ய முடியாது

```
flutter build ios
# Error: Could not find an option named "--no-codesign"
# Reason: Flutter Windows SDK-ல் iOS build command இல்லை
```

**Apple's Rule:** iOS build செய்ய **macOS + Xcode** கட்டாயம் தேவை.

---

## ✅ Solution 1: Codemagic (Free M1 Mac - Recommended)

**Codemagic** = Free cloud Mac server. Apple M1 chip. iOS build செய்யலாம்.

### Step-by-Step:

#### 1. Sign Up (Free)
- https://codemagic.io/signup
- GitHub account-ஆல் login செய்யலாம்

#### 2. Add Project
- "Add Application" → Connect GitHub repo
- OR "Upload .zip" → Upload MAX PLAYER folder

#### 3. Use Our Config
`codemagic.yaml` file already created! Codemagic automatic-ஆக read செய்யும்.

#### 4. Start Build
- "Start new build" → Select `ios-build` workflow
- Build time: ~10-15 minutes
- **Free tier:** 500 build minutes/month

#### 5. Download IPA
- Build முடிந்ததும் `.ipa` file download செய்யலாம்
- Location: `Artifacts` tab

---

## ✅ Solution 2: GitHub Actions (Automatic)

`.github/workflows/build.yml` already created!

### How to Use:
1. Push code to GitHub
2. Go to GitHub → Actions → "Build APK + iOS"
3. Click "Run workflow"
4. Wait ~15 minutes
5. Download IPA from `Artifacts`

**Free tier:** 2000 minutes/month (Linux), macOS included

---

## ✅ Solution 3: MacStash / Any Mac

உங்களிடம் Mac இருந்தால்:

```bash
# 1. Project copy செய்யவும்
cd MAX_PLAYER

# 2. Dependencies
flutter pub get

# 3. CocoaPods
cd ios
pod install
cd ..

# 4. Build iOS (Simulator)
flutter build ios --simulator

# 5. Build IPA (Release)
flutter build ipa

# Output: build/ios/ipa/MAX_PLAYER.ipa
```

---

## 📋 What Gets Built

| File | Description |
|------|-------------|
| `.ipa` | iOS App Store Package (install via TestFlight/AltStore) |
| `.app` | iOS App Bundle (development) |

---

## 🚀 Install IPA on iPhone (Without App Store)

### Method 1: AltStore (Free)
1. Install AltStore on PC + iPhone
2. Connect iPhone to PC
3. Install `.ipa` via AltStore

### Method 2: TestFlight (Official)
1. Apple Developer account ($99/year)
2. Upload IPA to App Store Connect
3. TestFlight-ல் distribute செய்யலாம்

---

## 📁 Files Created for iOS Build

| File | Purpose |
|------|---------|
| `codemagic.yaml` | Codemagic CI config |
| `.github/workflows/build.yml` | GitHub Actions config |
| `IOS_BUILD.md` | macOS local build guide |
| `ios/` | iOS project files (ready) |

---

## 🎯 Quick Summary

| Platform | Your PC | Solution |
|----------|---------|----------|
| Android APK | ✅ Windows works | `flutter build apk` |
| iOS IPA | ❌ Mac needed | Codemagic (free) or GitHub Actions |

**Easiest:** Codemagic-ல் upload செய்து 10 நிமிடத்தில் IPA download செய்யலாம்! 🎉
