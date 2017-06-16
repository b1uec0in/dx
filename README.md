# dx for method counting.

always prints counts of field and method.

## vs. Android Studio APK Analyzer
You can see method references of classes.dex on "Build - Analyze APK" menu.
But, this is not available when build fails.

## Usage
1. Backup your original dx.jar (.../Android/sdk/build-tools/[buildToolsVersion]/lib/dx.jar)
1. Replace your dx.jar with this [dx.jar](https://github.com/b1uec0in/dx/releases/download/1.0/dx.jar)(see releases).
1. Disable dexInProcess option.
```
// file: app/build.gradle
android {
    dexOptions {
        dexInProcess false
    }
    ...
```




