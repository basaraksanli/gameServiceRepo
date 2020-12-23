## Table of Contents

 * [Introduction](#introduction)
 * [Installation](#installation)
 * [Configuration ](#configuration )
 * [Supported Environments](#supported-environments)
 * [Sample Code](#Sample-Code)
 * [License](#license)
 
 
## Introduction
    HMS Game Service Achiements Codelab code encapsulates APIs of the HUAWEI Game Service SDK and Account Kit SDK. It provides sample achievement usage for your reference or usage.
    Before you use this codelab, it's assumed that you already have a HUAWEI developer account and have already created an app to implement the HMS Game Services Achievement capabilities. If you haven't,    please refer to https://developer.huawei.com/consumer/en/doc/start/introduction-0000001053446472 and https://developer.huawei.com/consumer/en/doc/development/AppGallery-connect-Guides/agc-introduction.
    
    model:       The package name which refers to a question object.
    ui:          The package name which shows the interface of the app to the user.
    constant:    The package which contains the constant values of the project.
    

## Installation
    Before using HMS Game Service Achievements Codelab code, check whether the Android Studio environment has been installed. 
    Download the HMS Game Service Achievements Codelab project by zip or clone in Github.
    Wait for the gradle build in your project.
    
## Supported Environments
	•	Android Studio 4.4 or later version
	•	Java JDK 1.8 or later version
	•	EMUI 3.0 or later version
	•	HMS Core (APK) 5.0.1.310 or later version

## Configuration 
    1. Register and sign in to HUAWEI Developers.
    2. Create a project and then create an app in the project, enter the project package name.
    3. Go to Project Settings > Manage APIs, find the Account Kit and Game Service, and enable it.
    4. Go to Project Settings > General information, click Set next to Data storage location under Project information, and select a data storage location in the displayed dialog box.
    5. Download the agconnect-services.json file and place it to the app's root directory of the project.
    6. Add the Maven repository address maven {url 'https://developer.huawei.com/repo/'} and plug-in class path 'com.huawei.agconnect:agcp:1.4.1.300' to the project-level build.gradle file.
    7. Add apply plugin: 'com.huawei.agconnect' to the last line of the app-level build.gradle file.
    8. Configure the dependency com.huawei.hms:hwid:5.0.1.301 and com.huawei.hms:game:5.0.3.301 in the app-level buildle.gradle file.
    9. Synchronize the project.
	
## Sample Code
    HMS Game Service Achiements Codelab uses Game Service Manager class in the project in order to manage achievement capabilities .The following describes methods related with Achievements in the project.

    1) Initialize Game Service and Achievements Clients
    You can initialize the Game Service and Achivements Clients using the init method in the Game Services Manager object.
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt
    
    2) Sign in using Account Kit
    You can sign in through Account Kit using the signIn method in Game Services Manager.
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt
    
    3) Unlock Achievement 
    You can unlock an achievement providing achievementID as parameter.
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt
    
    4) Increment Step
    You can increment an achievement step providing achievementID as parameter. If isChecked boolean is true, step will be incremented without a callback.
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt
    
    5) Set Step
    You can set the current step of the achievement by providing achievementID and stepNumber as parameters. If isChecked boolean is true, step will be set without a callback.
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt
    
    6) Increment step with Result
    You can increment a step as well as obtaining the result callback
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt
    
    7) Set Step with Result
    You can set a step as well as obtaining the result callback
    Code location src/main/java/com.codelabs.gameservices/huawei/GameServicesManager.kt

##  License
    HMS Game Service Achievements Codelab is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).
