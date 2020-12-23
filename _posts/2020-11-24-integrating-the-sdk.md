---
title: Configuring Your Development Environment
description: 5
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

<p><strong>Step 5</strong>: In the <strong>build.gradle</strong> file of your Android Studio project, add the following configurations.</p>



<ul>
	<li>Go to <strong>allprojects</strong> &gt; <strong>repositories</strong> and configure the Maven repository address for the HMS Core SDK.<pre><div id="copy-button1" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="pln">allprojects </span><span class="pun">{</span><span class="pln">
		repositories </span><span class="pun">{</span><span class="pln">
			maven </span><span class="pun">{</span><span class="pln"> url </span><span class="str">'https://developer.huawei.com/repo/'</span><span class="pln"> </span><span class="pun">}</span><span class="pln">
			</span><span class="pun">...</span><span class="pln">
		</span><span class="pun">}</span><span class="pln">
	</span><span class="pun">}</span><span class="pln">
	</span></code></pre>
	</li>
	<li>Go to <strong>buildscript</strong> &gt; <strong>repositories</strong> and configure the Maven repository address for the HMS Core SDK.<pre><div id="copy-button2" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="pln">buildscript </span><span class="pun">{</span><span class="pln">
		repositories </span><span class="pun">{</span><span class="pln">
		   maven </span><span class="pun">{</span><span class="pln">url </span><span class="str">'https://developer.huawei.com/repo/'</span><span class="pun">}</span><span class="pln">
			</span><span class="pun">...</span><span class="pln">
		</span><span class="pun">}</span><span class="pln">
		</span><span class="pun">...</span><span class="pln">
	</span><span class="pun">}</span><span class="pln">
	</span></code></pre>
	</li>
	<li>Go to <strong>buildscript</strong> &gt; <strong>dependencies</strong> and add build dependencies.<pre><div id="copy-button3" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="pln">buildscript </span><span class="pun">{</span><span class="pln">
		dependencies </span><span class="pun">{</span><span class="pln">
     </span><span class="str">                   //Replace {agconnect_version} with the actual AGC plugin version number.</span><span class="pln">
     </span><span class="str">                   //Example: classpath 'com.huawei.agconnect:agcp: 1.4.1.300'</span><span class="pln">
			classpath </span><span class="str">'com.huawei.agconnect:agcp:{agconnect_version}'</span><span class="pln">
		</span><span class="pun">}</span><span class="pln">
	</span><span class="pun">}</span><span class="pln">
	</span></code></pre>
	</li>
</ul>
<p><strong>Step 6</strong>: Open the Android Studio app-level build.gradle file.<br><img style="width: 300.00px" src="https://raw.githubusercontent.com/basaraksanli/gameServiceRepo/master/assets/5.png" onclick="imageclick(src)"></p>

<p><strong>Step 7</strong>: In the build.gradle file in the app directory of your Android Studio project, add the following configurations:<br>
Replace {version} of hwid with the latest version of HUAWEI Account Kit. For details, please refer to <a href= "https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/version-change-history-0000001050048874" targey=_blank>Version Change History</a>.<br>
Replace {version} of game with the latest version of HUAWEI Game Service. For details, please refer to <a href= "https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/version-change-history-0000001050123471" targey=_blank>Version Change History</a>.
</p>



<ul>
	<li>Add a dependency package to the <strong>dependencies</strong> section in the <strong>build.gradle</strong> file.<pre><div id="copy-button4" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="pln">dependencies </span><span class="pun">{</span><span class="pln">
		</span><span class="pun">...</span><span class="pln">
    </span><span class="str">            //Video Kit</span><span class="pln">
		implementation </span><span class="str">'com.huawei.hms:hwid:{version}'</span><span class="pln">
		</span><span class="pun">implementation</span><span class="str"> 'com.huawei.hms:hwid:{version}'</span><span class="pln">
	</span><span class="pun">}</span><span class="pln">
	</span></code></pre>

	</li>
	<li>Add the following information under <strong>apply plugin: 'com.android.application'</strong> in the file header:<pre><div id="copy-button6" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="pln">apply plugin</span><span class="pun">:</span><span class="pln"> </span><span class="str">'com.huawei.agconnect'</span><span class="pln">
	</span></code></pre>
	</li>
</ul>

<p><strong>Step 8</strong>: Enable data binding for MVVM architecture.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="pln">databinding </span><span class="pun">{</span>
    <span class="str">            enabled=true</span><span class="pln">
		implementation </span><span class="str">'com.huawei.hms:hwid:{version}'</span><span class="pln">
		</span><span class="pun">implementation</span><span class="str"> 'com.huawei.hms:hwid:{version}'</span><span class="pln">
	</span><span class="pun">}</span><span class="pln">
	</span></code></pre>

<p><strong>3. Configure obfuscation scripts.</strong></p>
<ul>
	<li>Configure the following information in the <strong>app/proguard-rules.pro</strong> file:<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>                <span class="pun">-</span><span class="pln">ignorewarnings</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keepattributes </span><span class="pun">*</span><span class="typ">Annotation</span><span class="pun">*</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keepattributes </span><span class="typ">Exceptions</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keepattributes </span><span class="typ">InnerClasses</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keepattributes </span><span class="typ">Signature</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keepattributes </span><span class="typ">SourceFile</span><span class="pun">,</span><span class="typ">LineNumberTable</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keep </span><span class="kwd">class</span><span class="pln"> com</span><span class="pun">.</span><span class="pln">hianalytics</span><span class="pun">.</span><span class="pln">android</span><span class="pun">.**{*;}</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keep </span><span class="kwd">class</span><span class="pln"> com</span><span class="pun">.</span><span class="pln">huawei</span><span class="pun">.</span><span class="pln">updatesdk</span><span class="pun">.**{*;}</span><span class="pln">
		</span><span class="pun">-</span><span class="pln">keep </span><span class="kwd">class</span><span class="pln"> com</span><span class="pun">.</span><span class="pln">huawei</span><span class="pun">.</span><span class="pln">hms</span><span class="pun">.**{*;}</span><span class="pln">
		</span></code></pre>
	</li>
	<li>If you are using AndResGuard, add it to the allowlist in the obfuscation script file.<pre><div id="copy-button8" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>               <span class="str"> "R.string.hms*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.string.connect_server_fail_prompt_toast"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.string.getting_message_fail_prompt_toast"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.string.no_available_network_prompt_toast"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.string.third_app_*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.string.upsdk_*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.layout.hms*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.layout.upsdk_*"</span><span class="pun">,</span><span class="pln"> 
		</span><span class="str">"R.drawable.upsdk*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.color.upsdk*"</span><span class="pun">,</span><span class="pln"> 
		</span><span class="str">"R.dimen.upsdk*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.style.upsdk*"</span><span class="pun">,</span><span class="pln">
		</span><span class="str">"R.string.agc*"</span><span class="pln">
		</span></code></pre>
	</li>
</ul>
<p><strong>4. Configure permissions in the AndroidManifest.xml file.</strong></p>
<pre><div id="copy-button9" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><span class="tag">&lt;uses-permission</span><span class="pln"> </span><span class="atn">android:name</span><span class="pun">=</span><span class="atv">"android.permission.INTERNET"</span><span class="tag">/&gt;</span><span class="pln">
</span><span class="tag">&lt;uses-permission</span><span class="pln"> </span><span class="atn">android:name</span><span class="pun">=</span><span class="atv">"android.permission.ACCESS_NETWORK_STATE"</span><span class="tag">/&gt;</span><span class="pln">
</span><span class="tag">&lt;uses-permission</span><span class="pln"> </span><span class="atn">android:name</span><span class="pun">=</span><span class="atv">"android.permission.ACCESS_WIFI_STATE"</span><span class="tag">/&gt;</span><span class="pln">
</span><span class="tag">&lt;uses-permission</span><span class="pln"> </span><span class="atn">android:name</span><span class="pun">=</span><span class="atv">"com.huawei.permission.SECURITY_DIAGNOSE"</span><span class="tag">/&gt;</span><span class="pln">
  </span></code></pre>
<p><strong>Step 4</strong>: In the Android Studio window, choose <strong>File</strong> &gt; <strong>Sync Project with Gradle Files</strong> to synchronize the project.</p>
