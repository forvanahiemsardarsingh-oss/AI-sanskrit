# Build APK with GitHub Actions (No EAS Required)

Created: `.github/workflows/build-apk.yml`

## 🚀 Trigger the Build (2 minutes)

### Step 1: Push the new workflow to GitHub
1. Go to your repo: `https://github.com/forvandanamsardarsingh-oss/AI-sanskrit`
2. Click **"Add file"** → **"Upload files"**
3. Upload: `.github/workflows/build-apk.yml`
4. Commit message: "Add APK build workflow"
5. Click **"Commit changes"**

### Step 2: Trigger the build
1. Go to **Actions** tab
2. Click **"Build APK"** in left sidebar
3. Click **"Run workflow"** dropdown → **"Run workflow"**
4. Wait 15-20 minutes for build

### Step 3: Get your APK
After build completes:
- Go to **Actions** → Click the completed run
- Scroll down to **Artifacts** → Download `vachas-ai-apk`
- OR go to **Releases** tab for direct download link

## 📱 Update Install Page

Once you have the download link, edit `install.html`:

```javascript
// Line ~180, change this:
APK_CONFIG.downloadUrl = '';

// To your release URL:
APK_CONFIG.downloadUrl = 'https://github.com/forvandanamsardarsingh-oss/AI-sanskrit/releases/download/v1/vachas-ai.apk';
```

Then push the updated `install.html` to GitHub.

## 🔗 Your Install Link Will Be

```
https://forvandanamsardarsingh-oss.github.io/AI-sanskrit/install.html
```

With working download button!

---

**Note:** If Android build fails (no android folder), the workflow will create a placeholder. For full APK, you need the Android project structure from the original vachas-ai folder.
