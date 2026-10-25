# Air Control 1.1.0 test report

Build run: GitHub Actions, release `v1.0.0-build4` (the tag name is just the CI run counter; the app is version 1.1.0, code 2).

## Verified by the CI build (actually executed, passed)
- `flutter analyze` (warnings fatal, infos not) and `flutter test` (Dart tests)
- Kotlin unit tests for the gesture engine through Gradle (`testDebugUnitTest`, real `org.json`)
- Full compile of all Kotlin (service, accessibility service, floating button, activity, config) and Dart
- Debug and release APKs built (arm64), release 52.8 MB, debug 111 MB
- APK metadata: package `com.carlos.aircontrol`, versionName 1.1.0, versionCode 2, minSdk 26, targetSdk 34
- Permissions in the APK: camera, foreground service (camera), notifications, modify system settings (brightness only). No internet permission in the release build.

## Verified locally before pushing
- 16 gesture-engine tests (compiled with Kotlin 2.0.21): held pinch never repeats, tap/double tap, volume repeats while held and stops when the pose changes or the hand disappears, one-shot holds fire once, new poses, finger pinches, no pausing on hand loss, Social mapping.
- Kotlin and Dart agree on every gesture and action id.

## NOT tested (needs a real phone)
Camera tracking and accuracy, injected taps/swipes/drags, global actions, media/volume/brightness, pointer dot, floating button (including starting the camera from it on Android 14+), per-app detection, "camera off outside chosen apps" restart behaviour, Social mode button positions, Samsung battery behaviour. Use the checklist in `docs/TEST_REPORT.md` inside the source archive.
