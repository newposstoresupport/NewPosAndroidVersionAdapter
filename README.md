# NewPosAndroidVersionAdapter
This repository provides the behavior changes and new features of different major versions of Android and highlights the points to note on POS devices.

## Android POS version adaptation complete guide
This open source public repository is maintained by NEWPOS internal professional developers in line with Google's Android updates. It aims to provide customers with compatibility summary and template code for different major Android versions, and to improve NEWPOS customers' development efficiency and code quality on NEWPOS Android POS devices.



# The documents we provide are for reference only.
  ### Android 13 changes compiled by NEWPOS developers
  * [English](Android13/english/Android13vsAndroid10BehaviorChanges.pdf)
  * [Chinese](Android13/chinese/Android13相较Android10的API行为变更.pdf)

  ### Android 12 changes compiled by NEWPOS developers
  * [English](Android12/english/Android12vsAndroid10BehaviorChanges.pdf)
  * [Chinese](Android12/chinese/Android12相较Android10的API行为变更.pdf)



### Adaptation process
* Here we take the adaptation of Android 13 as an example. The first step is to modify the values of targetSdk and compileSdk in the build.gradle file in the main module.


New version gradle configuration, gradle or gradle.kts
```groovy
android {

    compileSdk 33
    defaultConfig {
        //......
        targetSdk 33
    }
}
```


Old version gradle configuration
```groovy
android {

    compileSdkVersion 33
    defaultConfig {
        ......
        targetSdkVersion 33
    }
}
```


* Next, make some version judgments in the code and make sure the new version is compatible with the old version.

```java
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
    ......
} else {
    ......
}
```

```java
if (context.getApplicationInfo().targetSdkVersion >= Build.VERSION_CODES.TIRAMISU) {
    ......
} else {
    ......
}
```



### compileSdk & targetSdk
* The following briefly introduces the meaning of compileSdk and targetSdk, Just for our understanding.

    * targetSdk：The target adaptation version tells the system how the app is adapted. If the targetSdk of the app is lower than the system version, the new system will make some new features backward compatible. If we want to adapt to a certain Android version, we must adjust the targetSdk to this version level, otherwise some adaptation anomalies may occur on some models. If we simply increase the targetSdk level without adapting to the features of the new version, the app may have functional anomalies on the new system, which is generally manifested as app crashes or failure to obtain data.

    * compileSdk：Compile source code version. We can change the version of the Android SDK source code we see in the code by modifying this version level. It also determines the version used by the compiler when checking the code.



# Android Developers Official Website Address
  * [Android 14](https://developer.android.com/about/versions/14/behavior-changes-all)
  * [Android 13](https://developer.android.com/about/versions/13/behavior-changes-all)
  * [Android 12](https://developer.android.com/about/versions/12/behavior-changes-all)
  * [Android 11](https://developer.android.com/about/versions/11/behavior-changes-all)
  * [Android 10](https://developer.android.com/about/versions/10/behavior-changes-all)




## License

See the [Apache 2.0 license](https://github.com/PAXSTORE/paxstore-3rd-app-android-sdk/blob/master/LICENSE) file for details.

    Copyright 2025 NEWPOSTech CO., LTD ("NEWPOS")
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at following link.
    
         http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.