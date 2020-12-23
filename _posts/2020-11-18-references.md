---
title: "Developing the Achievement List Page"
description: 10
---
<h2><strong>Method 1: Game Service Client Achievement Intent</strong></h2>
<p> Huawei Game Service provides developers an Achievement Intent to show achievements to user. You can use this function for achievement list. In order to use this function we need to create a task on <b>showAchievementListIntent.</b></p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
fun showAchivementList() {
    // TODO: Show Achievement List using achievement client.
    val task =
        achievementClient!!.showAchievementListIntent
    task.addOnSuccessListener { intent: Intent? ->
        if (intent == null) {
            Log.d("achivementsList", "intent = null")
        } else {
            try {
                activity!!.startActivityForResult(intent, 1)
            } catch (e: java.lang.Exception) {
                Log.d("achivementsList", "Achievement Activity is Invalid - " + e.message)
            }
        }
    }.addOnFailureListener { e: java.lang.Exception? ->
        if (e is ApiException) {
            val result = ("rtnCode:"
                    + e.statusCode)
            Log.d("achivementsList", "result:$result")
        }
    }
}
</code></pre>

<h2><strong>Method 2: Recycler view with custom adapter</strong></h2>
<p> However, in this codelab, we developed a custom recycler view to show achievements. We are retrieving the achievements from the client then adding the each achievement to the custom adapter list. Please see the code below:</p>

<pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
private fun getAchievements(){
    // TODO: get achievements from the client and add each achievement to the custom adapter list.
    val task: Task&lt;List&lt;Achievement&gt;&gt; =
        achievementClient.getAchievementList(true)
    task.addOnSuccessListener(OnSuccessListener { data ->
        if (data == null) {
            Log.w("Achievement", "achievement list is null")
            return@OnSuccessListener
        }
        for (achievement in data) {
            achievementList.add(achievement)
        }
        achievementListAdapter!!.value = AchievementListAdapter(achievementList, fragment.requireContext())
        progressBarVisibility.value = View.GONE
    }).addOnFailureListener { e ->
        if (e is ApiException) {
            val result = "rtnCode:" +
                    (e as ApiException).statusCode
            Log.e("Achievement", result)
        }
    }
}

</code></pre>




