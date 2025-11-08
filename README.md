# Jamiyat Manager (Arabic RTL)

Mobile app to manage monthly financial associations. Offline-first with local SQLite (Drift), local notifications, and export/import (JSON/Excel).

> 📖 **For detailed setup instructions, see [SETUP_GUIDE.md](SETUP_GUIDE.md)**

## Prerequisites

1. **Install Flutter**
   - Download Flutter from [flutter.dev](https://flutter.dev/docs/get-started/install/windows)
   - Extract to a location like `C:\src\flutter`
   - Add `C:\src\flutter\bin` to your system PATH
   - Run `flutter doctor` to verify installation and fix any issues

2. **Install Android Studio** (for Android development)
   - Download from [developer.android.com](https://developer.android.com/studio)
   - Install Android SDK and set up an emulator, or connect a physical device

## Setup & Run

1. **Navigate to the project directory:**
   ```bash
   cd jamiyat_manager
   ```

2. **Install dependencies:**
   ```bash
   flutter pub get
   ```

3. **Generate database code (required for Drift):**
   ```bash
   flutter pub run build_runner build --delete-conflicting-outputs
   ```
   This generates the `database.g.dart` file needed by the Drift database.

4. **Run the app:**
   ```bash
   flutter run
   ```
   - If you have multiple devices/emulators, use `flutter devices` to list them
   - Then run `flutter run -d <device-id>` to target a specific device

## Development

- **Re-generate code after database changes:**
  ```bash
  flutter pub run build_runner build --delete-conflicting-outputs
  ```

- **Watch mode (auto-regenerate on file changes):**
  ```bash
  flutter pub run build_runner watch --delete-conflicting-outputs
  ```

## Project Structure
- `lib/core/` - Core services (notifications, backup, export) and dependency injection
- `lib/data/` - Database (Drift), DAOs, and repositories
- `lib/features/` - Feature modules (associations, members, payments)
  - Each feature has: `domain/`, `state/`, `ui/`
- `lib/app.dart` - Main app widget with RTL support
- `lib/main.dart` - App entry point

## Features
- ✅ Offline-first SQLite database (Drift)
- ✅ Local notifications for payment reminders
- ✅ Export/Import (JSON/Excel)
- ✅ RTL (Right-to-Left) Arabic UI support
- ✅ Riverpod for state management


