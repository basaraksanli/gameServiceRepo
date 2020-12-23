---
title: "Developing the Achievements Capabilities"
description: 25
---



<p><strong>Step 1</strong>: Get the references of the <b>AchievementClient</b> and <b>BuoyClient</b>. The BuoyClient class defines the APIs related to floating windows. The AchievementsClient class defines APIs for managing game achievements, for example, obtaining the game achievement list, incrementing an achievement, and setting steps required for unlocking an achievement.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
init {
    this.activity = activity
    this.viewModel = viewModel

    // TODO: Get the references of the Achievement Client and BuoyClient

    achievementClient = Games.getAchievementsClient(activity)
    buoyClient = Games.getBuoyClient(activity)

}
</code></pre>

<p><strong>Step 2</strong>: Develop the function which unlocks the achievement using achievementID. This can be also used without the callback function.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun unlockAchievement(achievementID: String) {
// TODO: Unlock Achievement using reachwithResult function
    val task: Task<Void> =
        achievementClient!!.reachWithResult(achievementID)
    task.addOnSuccessListener { v: Void? ->
        Log.d("Unlock Achievement", "reach  success")
    }.addOnFailureListener { e: Exception? ->
        if (e is ApiException) {
            val result = ("rtnCode:"
                    + e.statusCode)
            Log.d("Unlock Achievement", "reach result$result")
        }
    }
}
</code></pre>

<p><strong>Step 3</strong>: Develop the function which reveals the achievement using achievementID. This can be also used without the callback function.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun revealAchievement(achievementId: String) {
    // TODO: Reveal Hidden Achievement with visualizeWithResult function
    val task =
        achievementClient!!.visualizeWithResult(achievementId)
    task.addOnSuccessListener {
        Log.d("revealAchievement", "revealAchievemen isSucess")
    }.addOnFailureListener { e ->
        if (e is ApiException) {
            val result = "rtnCode:" + e.statusCode
            Log.d("revealAchievement", "achievement is not hidden$result")
        }
    }

</code></pre>

<p><strong>Step 4</strong>: Develop the function which increments the steps of the Achievement. Option to choose the method with or without a callback. Callback function inform us if the process was successful.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun increment(achievementId: String?, isChecked: Boolean) {
// TODO: Increment step count of the achievement using grow function or use the grow function with a call back
    if (!isChecked) {
        achievementClient!!.grow(achievementId, 1)
    } else {
        incrementWithResult(achievementId!!, 1)
    }
</code></pre>

<p><strong>Step 5</strong>: Increment the step count of the achievement with a callback function.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun increment(achievementId: String?, isChecked: Boolean) {
private fun incrementWithResult(
    achievementId: String,
    stepsNum: Int
) {
    // TODO: Increment step count of achievement using growWithResult with a callback
    val task =
        achievementClient!!.growWithResult(achievementId, stepsNum)
    task.addOnSuccessListener { isSucess ->
        if (isSucess) {
            Log.d("AchievementIncrement", "incrementAchievement isSucess")
        } else {
            Log.d("AchievementIncrement", "achievement can not grow")
        }
    }.addOnFailureListener { e ->
        if (e is ApiException) {
            val result = "rtnCode:" + e.statusCode
            Log.d("AchievementIncrement", "has bean already unlocked$result")
        }
    }
}
</code></pre>

<p><strong>Step 6</strong>: Develop the function which set the steps of the Achievement. Option to choose the method with or without a callback. Callback function inform us if the process was successful.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun setStep(achievementId: String?, stepsNum: Int, isChecked: Boolean) {
    // TODO: set step count of the achievement using makeSteos function or use the makeStep function with a call back
    if (!isChecked) {
        achievementClient!!.makeSteps(achievementId, stepsNum)
    } else {
        setStepsWithResult(achievementId!!, stepsNum)
    }
}
</code></pre>

<p><strong>Step 7</strong>: Set step count of the achievement with a callback function.</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
//Same function but task version, can attach callbacks
private fun setStepsWithResult(
    achievementId: String,
    stepsNum: Int
) {
    // TODO: Set step count of achievement using makeStepsWithResult with a callback
    val task =
        achievementClient!!.makeStepsWithResult(achievementId, stepsNum)
    task.addOnSuccessListener { isSucess ->
        if (isSucess) {
            Log.d("AchievementSetStep", "setAchievementSteps isSucess")
        } else {
            Log.d("AchievementSetStep", "achievement can not makeSteps")
        }
    }.addOnFailureListener { e ->
        if (e is ApiException) {
            val result = "rtnCode:" + e.statusCode
            Log.d("AchievementSetStep", "step num is invalid$result")
        }
    }

}
</code></pre>

