---
title: Configuring Your Development Environment
description: 15
---


<h2><strong>Enabling HUAWEI Game Service</strong></h2>
<p><strong>Step 1</strong>: Sign in to AppGallery Connect, click <Strong>My projects</Strong>, find your project, and click your desired app. On the page that is displayed, go to <strong>Project settings</strong> > <strong>Manage APIs</strong>.</p>
<p><strong>Step 2</strong>: Toggle the <strong>Huawei Account</strong> and <strong>Game Service</strong> switches.<br><img style="width: 800.00px" src="https://raw.githubusercontent.com/basaraksanli/gameServiceRepo/master/assets/3.png" onclick="imageclick(src)"></p>

<h2><strong>Integrating the HMS Core SDK</strong></h2>
<p>For Android Studio, Huawei provides the HMS Core SDK that can be integrated by using the Maven repository. Before developing your game app, you will need to integrate the HMS Core SDK into your Android Studio project.</p>


<p><strong>Step 1</strong>: Sign in to AppGallery Connect, click <strong>My projects</strong>, find your project, and click your desired app. On the page that is displayed, go to <strong>Project settings</strong> > <strong>General information</strong>.</p>

<p><strong>Step 2</strong>: In the App information area, click <strong>agconnect-services.json</strong> to download the configuration file.</p>

<p><strong>Step 3</strong>: Copy the <strong>agconnect-service.json</strong> file to the project root directory.<br><img style="width: 600.00px" src="https://raw.githubusercontent.com/basaraksanli/gameServiceRepo/master/assets/4.png" onclick="imageclick(src)"></p>

<p><strong>Step 4</strong>: Open the Android Studio project-level <strong>build.gradle</strong> file.</p>

<p><strong>Step 5</strong>: In the <strong>build.gradle</strong> file of your Android Studio project, add the following configurations.

    <pre><div id="copy-button1" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>allprojects {
    repositories {
        google()
        jcenter()
        maven {url 'https://developer.huawei.com/repo/'}
    }
}

buildscript {
    repositories {
        google()
        jcenter()

        maven {url 'https://developer.huawei.com/repo/'}
    }
}

buildscript {
    dependencies {
        classpath 'com.android.tools.build:gradle:3.4.2'
        classpath 'com.huawei.agconnect:agcp:1.4.1.300'
    }
}
</code></pre>
</p>

<p><strong>Step 6</strong>: Open the Android Studio app-level build.gradle file.<br><img style="width: 300.00px" src="https://raw.githubusercontent.com/basaraksanli/gameServiceRepo/master/assets/5.png" onclick="imageclick(src)"></p>

<p><strong>Step 7</strong>: In the <b>build.gradle</b> file in the <b>app directory</b> of your Android Studio project, add the following configurations:<br>
Replace {version} of <strong>hwid</strong> with the latest version of HUAWEI Account Kit. For details, please refer to <a href= "https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/version-change-history-0000001050048874" targey=_blank>Version Change History</a>.<br>
Replace {version} of <strong>game</strong> with the latest version of HUAWEI Game Service. For details, please refer to <a href= "https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/version-change-history-0000001050123471" targey=_blank>Version Change History</a>.




	<pre><div id="copy-button6" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>apply plugin: 'com.huawei.agconnect'

dependencies {
    implementation'com.huawei.hms:hwid:{version}'
    implementation'com.huawei.hms:game:{version}'
}
</code></pre>
	
</p>

<p><strong>Step 8</strong>: Enable data binding for MVVM architecture.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>dataBinding{
    enabled=true
}
</code></pre>

<p><strong>Step 9</strong>: Click <strong>Sync Now</strong> to synchronize the configurations.<br><img style="width: 800.00px" src="https://raw.githubusercontent.com/basaraksanli/gameServiceRepo/master/assets/7.png" onclick="imageclick(src)"></p>


<h2><strong>Configure obfuscation scripts</strong></h2>
<p><strong>Step 1</strong>: Sign in to AppGallery Connect, click <Strong>My projects</Strong>, find your project, and click your desired app. On the page that is displayed, go to <strong>Project settings</strong> > <strong>Manage APIs</strong>.<br><img style="width: 400.00px" src="https://raw.githubusercontent.com/basaraksanli/gameServiceRepo/master/assets/8.png" onclick="imageclick(src)"></p>

<p><strong>Step 2</strong>: Add obfuscation configurations.<br>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>-ignorewarnings
-keepattributes *Annotation*
-keepattributes Exceptions
-keepattributes InnerClasses
-keepattributes Signature
-keepattributes SourceFile,LineNumberTable
-keep class com.hianalytics.android.**{*;}
-keep class com.huawei.updatesdk.**{*;}
-keep class com.huawei.hms.**{*;}

</code></pre></p>

