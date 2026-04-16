## 2024-04-16 - Prevent unauthorized access to CrashActivity

**Vulnerability:** `CrashActivity` in `app/src/main/AndroidManifest.xml` was set to `android:exported="true"`. This allowed external, potentially malicious apps to launch the error-handling screen directly, potentially causing unexpected behavior or confusing the user.

**Learning:** Internal activities that handle errors or sensitive flows should not be exported unless strictly necessary for cross-app functionality. Even if an activity runs in a separate process (`android:process=":error_handler"`), it remains part of the same application and can be launched by internal components without needing to be exported.

**Prevention:** Always verify the necessity of `android:exported="true"` for any activity in the `AndroidManifest.xml`. If the activity is only intended to be launched by the app itself, explicitly set it to `android:exported="false"`.
