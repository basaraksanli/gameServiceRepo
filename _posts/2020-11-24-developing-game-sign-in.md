---
title: Developing the Game Sign-in Function
description: 15
---

<p><strong>Step 1</strong>: Register the callback listening function of the activity in the <b>onCreate</b> method of the Application.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
class MyApplication : Application() {
    // TODO: Set Application parameter for HuaweiMobile Services 
    override fun onCreate() {
        super.onCreate()
        // have to call this method here
        HuaweiMobileServicesUtil.setApplication(this)
    }
}
</code></pre>

<p><strong>Step 2</strong>: In the first fragment ViewModel init function, call the <b>init</b> method of <b>JosAppsClient</b> to initialize the <b>Game Service SDK</b>.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
init {
    // TODO: Initialize the Client in order to make Game Service work
    
    JosApps.getJosAppsClient(activity).init()

    gameServiceUtils = GameServiceUtils(activity, this)
    gameServiceUtils!!.signIn()
    
}
</code></pre>

<p><strong>Step 3</strong>: Call the <b>getService</b> method of <b>HuaweiIdAuthManager</b> to initialize the <b>HuaweiIdAuthService</b> object, and call the <b>silentSignIn</b> method of <b>HuaweiIdAuthService</b> to implement silent sign-in. If silent sign-in fails, call the <b>getSignInIntent</b> method of <b>HuaweiIdAuthService</b> to implement explicit sign-in.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun getHuaweiIdParams(): HuaweiIdAuthParams? {
    // TODO: Set HuaweiAuth Parameter as Game Login
    return HuaweiIdAuthParamsHelper(HuaweiIdAuthParams.DEFAULT_AUTH_REQUEST_PARAM_GAME).setIdToken().createParams()
}

//this function is used to sign in the user. If the user already signed in before, 
//it processes silent sign in. If it is the first time for the user, it starts the intent of Huawei ID sign in
fun signIn() {
// TODO: Sign in with Huawei ID    
if(playerID==null) {
        val authHuaweiIdTask =
            HuaweiIdAuthManager.getService(activity, getHuaweiIdParams()).silentSignIn()
        authHuaweiIdTask.addOnSuccessListener {
            viewModel!!.accountName.value = it.displayName
            getPlayerID()
        }.addOnFailureListener { e: Exception? ->
            if (e is ApiException) {
                val service = HuaweiIdAuthManager.getService(activity, getHuaweiIdParams())
                activity!!.startActivityForResult(service.signInIntent, 6013)
            }
        }
    }
}

</code></pre>
