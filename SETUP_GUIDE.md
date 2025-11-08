# 🚀 Jamiyat Manager - Complete Setup Guide

This guide will walk you through setting up and running the Jamiyat Manager Flutter application.

## 📋 Prerequisites

### 1. Install Flutter

1. **Download Flutter SDK:**
   - Visit: https://flutter.dev/docs/get-started/install/windows
   - Download the latest stable Flutter SDK (ZIP file)

2. **Extract Flutter:**
   - Extract the ZIP to a location like `C:\src\flutter`
   - **Important:** Don't extract to a path with spaces or special characters

3. **Add Flutter to PATH:**
   - Press `Win + X` and select "System"
   - Click "Advanced system settings"
   - Click "Environment Variables"
   - Under "System variables", find "Path" and click "Edit"
   - Click "New" and add: `C:\src\flutter\bin` (or your Flutter path)
   - Click "OK" on all dialogs

4. **Verify Installation:**
   - Open a **new** PowerShell or Command Prompt window
   - Run: `flutter doctor`
   - This will show what's installed and what's missing
   - Fix any issues it reports (usually Android toolchain)

### 2. Install Android Studio (for Android Development)

1. **Download Android Studio:**
   - Visit: https://developer.android.com/studio
   - Download and install Android Studio

2. **Set up Android SDK:**
   - Open Android Studio
   - Go to "More Actions" → "SDK Manager"
   - Install:
     - Android SDK Platform-Tools
     - Android SDK Build-Tools
     - At least one Android SDK (e.g., Android 13.0 "Tiramisu")

3. **Create an Android Emulator (Optional but Recommended):**
   - In Android Studio, go to "More Actions" → "Virtual Device Manager"
   - Click "Create Device"
   - Choose a device (e.g., Pixel 5)
   - Download a system image (e.g., Android 13)
   - Finish the setup

4. **Accept Android Licenses:**
   - Open PowerShell/Command Prompt
   - Run: `flutter doctor --android-licenses`
   - Accept all licenses by typing `y` and pressing Enter

### 3. Verify Everything is Ready

Run this command to check your setup:
```bash
flutter doctor -v
```

You should see checkmarks (✓) for:
- Flutter
- Android toolchain
- Android Studio
- VS Code or Android Studio (for IDE)

## 🏃 Running the Project

### Step 1: Navigate to Project Directory

Open PowerShell or Command Prompt and navigate to the project:
```bash
cd "C:\Users\VERSUS\Desktop\projet collect\jamiyat_manager"
```

### Step 2: Install Dependencies

```bash
flutter pub get
```

This downloads all required packages listed in `pubspec.yaml`.

### Step 3: Generate Database Code (CRITICAL!)

The project uses Drift (a Flutter database library) which requires code generation:

```bash
flutter pub run build_runner build --delete-conflicting-outputs
```

This command:
- Generates `lib/data/db/database.g.dart` (required for the app to compile)
- May take 1-2 minutes the first time
- The `--delete-conflicting-outputs` flag ensures clean generation

**⚠️ Important:** You MUST run this step before running the app, otherwise you'll get compilation errors!

### Step 4: Check Available Devices

```bash
flutter devices
```

This shows:
- Connected physical devices
- Available emulators
- Chrome (for web testing)

### Step 5: Run the App

**Option A: Run on default device**
```bash
flutter run
```

**Option B: Run on specific device**
```bash
flutter run -d <device-id>
```
(Replace `<device-id>` with the ID from `flutter devices`)

**Option C: Run on web (for quick testing)**
```bash
flutter run -d chrome
```

## 🔧 Troubleshooting

### Problem: "flutter: command not found"
**Solution:** 
- Make sure Flutter is added to PATH
- Close and reopen your terminal
- Verify with: `flutter --version`

### Problem: "No devices found"
**Solutions:**
- Start an Android emulator from Android Studio
- Connect a physical Android device via USB with USB debugging enabled
- For web: `flutter run -d chrome`

### Problem: "database.g.dart not found" or compilation errors
**Solution:**
- Run: `flutter pub run build_runner build --delete-conflicting-outputs`
- Make sure you're in the `jamiyat_manager` directory

### Problem: "Gradle build failed"
**Solutions:**
- Make sure Android Studio and Android SDK are properly installed
- Run: `flutter clean`
- Run: `flutter pub get`
- Try: `flutter run` again

### Problem: App crashes on startup
**Solutions:**
- Check if you ran the build_runner command
- Check device logs: `flutter logs`
- Make sure all dependencies are installed: `flutter pub get`

## 📱 Development Tips

### Hot Reload
While the app is running:
- Press `r` in the terminal to hot reload (fast refresh)
- Press `R` to hot restart (full restart)
- Press `q` to quit

### Re-generate Database Code
If you modify `database.dart`, run:
```bash
flutter pub run build_runner build --delete-conflicting-outputs
```

### Watch Mode (Auto-regenerate)
For active development, use watch mode:
```bash
flutter pub run build_runner watch --delete-conflicting-outputs
```
This automatically regenerates code when you save files.

### Clean Build
If you encounter strange errors:
```bash
flutter clean
flutter pub get
flutter pub run build_runner build --delete-conflicting-outputs
flutter run
```

## 📂 Project Structure

```
jamiyat_manager/
├── lib/
│   ├── main.dart              # App entry point
│   ├── app.dart               # Main app widget (RTL setup)
│   ├── core/                  # Core services & utilities
│   │   ├── di/               # Dependency injection (Riverpod providers)
│   │   ├── services/         # Backup, Excel export, Notifications
│   │   └── utils/            # Helper functions (months, etc.)
│   ├── data/                 # Data layer
│   │   ├── db/               # Database (Drift) & DAOs
│   │   └── repositories/     # Repository implementations
│   └── features/             # Feature modules
│       ├── associations/     # Associations feature
│       ├── members/          # Members feature
│       └── payments/         # Payments feature
├── pubspec.yaml              # Dependencies
└── README.md                 # Project documentation
```

## ✅ Quick Start Checklist

- [ ] Flutter installed and in PATH
- [ ] `flutter doctor` shows no critical issues
- [ ] Android Studio installed (for Android development)
- [ ] Android emulator created OR physical device connected
- [ ] Navigated to `jamiyat_manager` directory
- [ ] Ran `flutter pub get`
- [ ] Ran `flutter pub run build_runner build --delete-conflicting-outputs`
- [ ] Ran `flutter run`

## 🎯 Next Steps After Running

Once the app is running:
1. Create your first association (جمعية)
2. Add members to the association
3. Track monthly payments
4. Export data to Excel or JSON
5. Import backups from JSON

## 📞 Need Help?

- Flutter Documentation: https://flutter.dev/docs
- Flutter Community: https://flutter.dev/community
- Check `README.md` for project-specific information

---

**Happy Coding! 🎉**


