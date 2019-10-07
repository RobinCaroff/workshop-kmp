author: Maxime LUMEAU, Robin CAROFF and Pierre TIBULLE
summary: Kotlin Multiplatform Workshop
id: codelab-kotlin-multiplatform
categories: codelab,kotlin
environments: Web
status: Draft
feedback link: https://github.com/RobinCaroff/workshop-kmp
analytics account: ???

# Workshop Kotlin Multiplatform

## CodeLab Overview
Duration: 0:02:00

#### Sharing Kotlin code between iOS and Android 

In this codelab you will create an iOS and Android application, by making use of Kotlin's code sharing features. 
For Android you'll be using Kotlin/JVM, while for iOS it will be Kotlin/Native.

This codelab will show you the ability to share code within Kotlin and the benefits it provides. While what we'll be looking at is a simplified application, what is shown here can be applied to real world applications, independent of their size or complexity.

You will learn how to:

#### Create an Android app with Android Studio
#### Create a shared Kotlin library
* Use it from Android app
* Start the Android application

#### Create an iOS app with Xcode
* Use the shared Kotlin library from iOS app
* Use Kotlin from Swift
* Start the iOS application

#### Improve the shared library
* Use Coroutines to validate the asynchronous ability
* Use the multiplatform Http client Ktor to call a Json Api 

Positive
: This codelab is inspired by the Jetbrains [tutorial](https://kotlinlang.org/docs/tutorials/native/mpp-ios-android.html) for the first steps

## Environment Setup
Duration: 0:04:00

You need [Android Studio](https://developer.android.com/studio/) 3.4+ for the Android part of the tutorial. 

Positive
: You can also use [IntelliJ IDEA](https://jetbrains.com/idea/) Community or Ultimate edition.

The Kotlin plugin 1.3.41 or higher should be installed in the IDE. This can be verified via Language & Frameworks | Kotlin Updates section in the Settings (or Preferences) window.

For the iOS part of the tutorial, you need a macOS 10.14+ host with Xcode 10.3+ and the tools installed and configured.

Negative
: If you don't fill in the requirements at least for the Android part, please consider pair programming !!!

## STEP ONE - Initialize the project
Duration: 0:10:00

#### In this step, we check that everything is well configured !

Clone the workshop project repository : 
``` bash
git clone https://github.com/mlumeau/workshop-kmp.git
```

Checkout the branch step_two_hellokotlinmp : 
``` bash
cd workshop-kmp
git checkout step_two_hellokotlinmp
```

This project contain an Android app, a library and an iOS project.

#### Launch the Android Studio IDE and open the project.

The project should sync and you should be able to compile and run the Android application on an emulator or a real device. 

#### Let's check that it works!

TODO - Add a picture of the app launched on an Android device

Positive
: In the project, you can see the kore module which will contain the code for the multiplatform Android/iOS library.

### For mac user :
First you have to prepare the framework for iOS

``` bash
.gradlew :kore:packForXCode 
```

It creates the directory kore/build/xcode-frameworks which contains a gradlew executable and the framework for Xcode.

Now install the pods :
``` bash
cd iosApp/kosmos
pod install
```

Negative
: In case of errors, try to reinstall pods with the last version of cocoapods

``` bash
sudo gem install cocoapods
pod deintegrate
rm Podfile.lock
pod install
```

#### Now you can open the project in Xcode
by clicking on ../workshop-kmp/iosApp/kosmos/kosmos.xcworkspace

You can compile and run the project on an iOS emulator

### If everything's fine, let's go to the second step !!!

## STEP TWO - Initialize the project
Duration: 0:10:00

#### In this step, you will implement your first multiplatform code !

First add this code in the common directory : kore/src/commonMain/kotlin/xyz/mlumeau/kosmos/kore/common.kt

``` Kotlin
package xyz.mlumeau.kosmos.kore

expect fun platformName(): String

fun createApplicationScreenMessage(): String {
    return "Kotlin Rocks on ${platformName()}"
}
```

Positive
: The keyword 'expect' means that you have to implement these function in the specific code.

Now edit the android directory : workshop-kmp/kore/src/androidMain/kotlin/xyz/mlumeau/kosmos/kore/actual.kt

``` Kotlin
package xyz.mlumeau.kosmos.kore

actual fun platformName(): String {
    return "Android"
}
```

Positive
: The keyword 'actual' corresponds to the 'expect' in the specific code.

### For mac user :

Now edit the iOS directory : workshop-kmp/kore/src/iosMain/kotlin/xyz/mlumeau/kosmos/kore/actual.kt

``` Kotlin
package xyz.mlumeau.kosmos.kore

import platform.UIKit.UIDevice

actual fun platformName(): String {
    return UIDevice.currentDevice.systemName() +
            " " +
            UIDevice.currentDevice.systemVersion
}
```
