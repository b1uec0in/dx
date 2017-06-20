# dx for method counting

always prints counts of field and method. (modified version of original dx.jar)

## vs. Android Studio APK Analyzer
You can see method references of classes.dex on "Build - Analyze APK" menu in Android Studio.<br/>
But if your build fails, there is no APK. You can't use APK analyzer anymore.

If you don't want to use `MultiDex` and you want to know how many methods are to be removed for build success, `dx for method counting` will be more helpful.

## Output sample
<pre>...
...
:app:compileDevDebugJavaWithJavac
:app:compileDevDebugNdk UP-TO-DATE
:app:compileDevDebugSources
:app:transformClassesWithDexForDevDebug
<b style="color:red">string ID count: 91,857
type ID count: 12,636
proto ID count: 18,417
field ID count: 72,011 (max:65535 +6476)
method ID count: 81,181 (max:65535 +15646)
Error converting bytecode to dex:
Cause: com.android.dex.DexIndexOverflowException: Too many field references: 72011; max is: 65535.
    UNEXPECTED TOP-LEVEL EXCEPTION:
    ...
    ...</b>
</pre>

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




