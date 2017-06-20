# dx for method counting

always prints counts of field and method.

## vs. Android Studio APK Analyzer
You can see method references of classes.dex on "Build - Analyze APK" menu in Android Studio.<br/>
But if your build fails, there is no APK.<br/>
You can't know how many methods are to be removed for build success.


## Output sample
<pre>...
...
:app:compileDevDebugJavaWithJavac
:app:compileDevDebugNdk UP-TO-DATE
:app:compileDevDebugSources
:app:transformClassesWithDexForDevDebug
<b style="color:red">String ID count: 91,857  (max:-1)
type ID count: 12,636  (max:65535)
proto ID count: 18,417  (max:65535)
field ID count: 72,011  (max:65535)
method ID count: 81,181  (max:65535)
Dex: Error converting bytecode to dex:
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




