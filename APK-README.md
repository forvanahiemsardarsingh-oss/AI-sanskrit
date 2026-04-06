# Vachas AI - APK Build (299MB Optimized)

This is the optimized APK version of Vachas AI, designed to stay under the 299MB Play Store limit with silent background downloads for heavy features.

## 📦 Build Configuration

- **Target Size**: 299MB (Play Store limit)
- **Compression**: Maximum (ProGuard + Resource Shrinking)
- **Architecture**: arm64-v8a only (excludes x86, x86_64)
- **Features**: Core app only, extras download on-demand

## 🚀 Quick Start

```bash
# Install dependencies
pnpm install

# Build APK
node scripts/build-apk.js

# Or use EAS directly
eas build --platform android --profile production --local
```

## 📱 Silent Download Features

The following features are **excluded** from the initial APK and download silently:

| Feature | Size | Priority |
|---------|------|----------|
| Sanskrit TTS | 150MB | Low |
| Panini Grammar Engine | 40MB | Medium |
| Video Lessons | 200MB | Low |
| 3D Sanskrit Models | 100MB | Low |
| Offline Dictionary | 80MB | Medium |
| Audio Mantras | 120MB | Medium |

**Total**: ~690MB (downloaded on-demand)

### Download Conditions

Silent downloads occur when:
- ✅ App is in background
- ✅ Connected to WiFi
- ✅ Device is charging
- ✅ Storage space available

## 🗜️ Size Optimizations Applied

### Code
- ProGuard obfuscation & shrinking
- Hermes bytecode compilation
- Tree shaking & dead code elimination
- Minification (console/debugger stripped)

### Assets
- WebP images only (excludes PNG/JPEG)
- Font subsetting (Devanagari + Latin)
- JSON minification & deduplication
- Heavy assets excluded from bundle

### Native Libraries
- Excluded: `libjsc.so`, `libc++_shared.so`
- Single architecture: arm64-v8a
- No x86/x86_64 support

## 📂 Project Structure

```
vachas-ai-apk/
├── app.json              # Expo config with APK optimizations
├── eas.json              # EAS build profiles
├── metro.config.js       # Aggressive bundler optimization
├── lib/
│   ├── apkDownloadManager.ts  # Silent download handler
│   └── ...
├── scripts/
│   ├── build-apk.js      # APK build script
│   └── optimize-build.js # Asset optimization
└── feature-modules/      # Placeholder for CDN modules
```

## ☁️ CDN Setup

Upload feature modules to your CDN:

```bash
# Feature modules should be hosted at:
https://assets.vachas.ai/modules/{module-id}.zip

# Example:
https://assets.vachas.ai/modules/sanskrit-tts.zip
https://assets.vachas.ai/modules/panini-engine.zip
```

## 🔧 Manual Build Steps

If the build script fails, follow these steps:

1. **Install EAS CLI**
   ```bash
   npm install -g eas-cli
   ```

2. **Login to Expo**
   ```bash
   eas login
   ```

3. **Configure Build**
   ```bash
   eas build:configure
   ```

4. **Run Production Build**
   ```bash
   eas build --platform android --profile production --local
   ```

## 📊 Size Monitoring

Check APK size after build:

```bash
# Find APK
ls -lh android/app/build/outputs/apk/release/*.apk

# Check size
du -h android/app/build/outputs/apk/release/app-release.apk
```

## ⚠️ Troubleshooting

### Build exceeds 299MB
1. Run `node scripts/optimize-build.js`
2. Check `metro.config.js` exclusions
3. Verify no heavy assets in bundle

### Silent downloads not working
1. Check `apkDownloadManager.ts` config
2. Verify CDN URLs in `app.json`
3. Test with app in background + charging

### Native library issues
1. Clean build: `cd android && ./gradlew clean`
2. Rebuild: `eas build --platform android --profile production`

## 📝 Play Store Submission

1. Build AAB for Play Store:
   ```bash
   eas build --platform android --profile production-aab
   ```

2. Upload to Play Store Console
3. Set download size warning at 299MB
4. Enable "App Bundle" for dynamic delivery

## 🎯 Core APK Contents (Included)

- ✅ React Native core
- ✅ Expo modules (Router, Font, Asset)
- ✅ UI components & screens
- ✅ Authentication
- ✅ Basic lessons & quizzes
- ✅ Lightweight sanskrit data
- ✅ Essential fonts (subsetted)

## 📥 User Experience

1. **Download**: 299MB from Play Store
2. **Install**: Core app ready immediately
3. **Background**: Heavy features download silently
4. **Ready**: Full functionality within minutes

## 🔗 Links

- CDN Base: `https://assets.vachas.ai`
- API Base: `https://api.vachas.ai`
- Support: `support@vachas.ai`

---

**Built with Expo & React Native** | **Optimized for India/ Nepal markets**
