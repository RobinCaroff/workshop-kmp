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

Sharing Kotlin code between iOS and Android 

In this codelab we will create an iOS and Android application, by making use of Kotlin's code sharing features. 
For Android we'll be using Kotlin/JVM, while for iOS it will be Kotlin/Native.

This codelab will show you the ability to share code within Kotlin and the benefits it provides. While what we'll be looking at is a simplified application, what is shown here can be applied to real world applications, independent of their size or complexity.

You will learn how to:

* Create an Android app with Android Studio
* Create a shared Kotlin library
  - Use it from Android app
  - Start the Android application
* Create an iOS app with Xcode
  - Use the shared Kotlin library from iOS app
  - Use Kotlin from Swift
  - Start the iOS application
* Improve the shared library
  - Use Coroutines to validate the asynchronous ability
  - Use the multiplatform Http client Ktor to call a Json Api 

**Resources:** 
* This codelab is inspired by the Jetbrains [tutorial](https://kotlinlang.org/docs/tutorials/native/mpp-ios-android.html)

## Environment Setup
Duration: 0:04:00

You need [Android Studio](https://developer.android.com/studio/) 3.4+ for the Android part of the tutorial. 

Positive
: You can also use [IntelliJ IDEA](https://jetbrains.com/idea/) Community or Ultimate edition.

The Kotlin plugin 1.3.41 or higher should be installed in the IDE. This can be verified via Language & Frameworks | Kotlin Updates section in the Settings (or Preferences) window.

For the iOS part of the tutorial, you need a macOS 10.14+ host with Xcode 10.3+ and the tools installed and configured.

Negative
: If you don't fill in the requirements at least for the Android part, please consider pair programming !!!

## Checkout the Git repo
Duration: 0:05:00

