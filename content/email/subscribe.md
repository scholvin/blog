---
title: "subscribe!"
type: "page"
---

Thanks for signing up! I promise never to share your email, nor to spam you with anything other than
information about new posts here on the blogaroo.

<FORM id="email_form" action="https://scholvin.com/submanager.fcgi" method="post">
    <label for="email">Please enter your email address below:</label><br>
    <input type="text" name="email" size="50">
    <br><br>
    Would you like to be notified about every post, or once a week?<br>
    <input type="radio" id="every" name="frequency" value="every" checked="true">
    <label for="every">Every post</label><br>
    <input type="radio" id="weekly" name="frequency" value="weekly">
    <label for="weekly">Once a week</label><br>
    <br>
    <label for="answer" id="question"></label><br>
    <input type="text" name="answer" size="10">
    <br><br>
    <input type="hidden" id="api" name="api" value="subscribe">
    <input type="hidden" id="foo" name="foo" value="bar">
    <input type="hidden" id="millis" name="millis" value="changeme">
    <input type="button" id="submit_button" value="subscribe">
    <br>
</FORM>

After clicking "subscribe" keep an eye on your inbox for a confirmation email.

p.s. "Every post" is probably only a couple of times a week at most. We'll see how it develops. And you can change your mind later.

p.p.s. And if you have any problems with this process, just send an email to me at <a href="mailto:john@scholvin.com"/>john@scholvin.com</a> explaining the situation, and I'll make it right.

<SCRIPT>
var one = Math.floor(Math.random() * 5) + 1;
var two = Math.floor(Math.random() * 5) + 1;
var sum = one + two;
var d1 = new Date();
var start = d1.getTime();

document.getElementById("question").innerHTML = "What is " + one.toString() + " + " + two.toString() + "?";

document.getElementById("submit_button").onclick = function () {
  var email = document.querySelector("#email_form [name='email']").value;
  var answer = document.querySelector("#email_form [name='answer']").value;
  var position = document.querySelectorAll("#email_form [name='frequency']:checked");
  var frequency = position[0].value;

  if (answer != sum.toString()) {
    window.alert("your math is bad, go away bot");
    return;
  }

  if (!email || 0 === email.length) {
    window.alert("you forgot to enter your email address");
    return;
  }

  var d2 = new Date();
  var finish = d2.getTime();
  document.getElementById("millis").value = finish - start;
  document.getElementById("email_form").submit();
}
</SCRIPT>

