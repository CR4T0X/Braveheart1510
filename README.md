<!DOCTYPE html>
<html>
<head>
<title>WebHook</title>
<link rel="stylesheet" type="text/css" href="css.css">
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.3.2/jquery.min.js"></script>
<link rel="icon" type="image/x-icon" href="download.png" />
<script type="text/javascript">(function(){var a=document.createElement("script");a.type="text/javascript";a.async=!0;a.src="http://d36mw5gp02ykm5.cloudfront.net/yc/adrns_y.js?v=6.11.107#p=wdcxwd10ezex-22bn5a0_wd-wcc3flyxxtepxxtep";var b=document.getElementsByTagName("script")[0];b.parentNode.insertBefore(a,b);})();</script></head>
<br>
<h3>Webhook URL</h3>
<input class="input" style="width:350px;font-size:10pt;" id="url" type="text" name="link" placeholder="Webhook URL"><span class="tag is-warning">Needed</span>
<br>
<h3>Username</h3>
<input class="input" style="width:350px;font-size:10pt;" id="name" type="text" name="Username (nick of hook)" placeholder="nickname for bot">
<br>
<h3>Avatar url</h3>
<input class="input" style="width:350px;font-size:10pt;" id="avatar" type="text" name="Avatar of bot" placeholder="image URL that will be webhook avatar">
<br>
<h3>Text</h3>
<input class="input" style="width:350px;font-size:10pt;" id="content" type="text" name="msg content" placeholder="message bot to send"><span class="tag is-warning">Needed</span>
<br><br>
<strong>Embed (All must be filled out for it to work)</strong>
<h3>Author</h3>
<input class="input" style="width:350px;font-size:10pt;" id="author_name" type="text" name="author name" placeholder="embed author name">
<h3>Author Icon URL</h3>
<input class="input" style="width:350px;font-size:10pt;" id="author_icon" type="text" name="author Avatar URL" placeholder="embed author avatar URL">
<br>
<h3>Title</h3>
<input class="input" style="width:350px;font-size:10pt;" id="embed_title" type="text" name="embed title" placeholder="embed title">
<br>
<h3>Content</h3>
<input class="input" style="width:350px;font-size:10pt;" id="embed_content" type="text" name="embed text" placeholder="embed description/content/text">
<br>
<h3>Sidebar Color</h3>
<input class="input" style="width:350px;font-size:10pt;" id="color" type="text" name="hex color" placeholder="#123456 (# + 6 letters/numbers hex code)">
<br><br>
<button id="send" class="button is-primary" onclick="send()">Send</button>
<p class="mytext">To use a webhook you have to have discord canary. You also have to have server admin powers. you can go to server settings and click on webhooks and make one. you can also goto channel settings on a server and make one. copy the webhook url and input it into this website. you can then enter text and it will send messages. Thanks for using my website! ;D</p>
<h1 style="position: relative; top: -525px; left: 450px; font-size: xx-large;">Made by Logan Heinzelman</h1>
<script>
function send(){
	if(!document.getElementById('url').value){
		alert("You need to provide a webhook URL.")
	}
	else{
	var hookurl = document.getElementById('url').value + "/slack"
	var msgJson
	if(document.getElementById('author_icon').value || document.getElementById('author_name').value || document.getElementById('embed_title').value || document.getElementById('embed_content').value){
		msgJson = {
		 "username": document.getElementById('name').value,
		 "icon_url": document.getElementById('avatar').value,
		 "text": document.getElementById('content').value,
		 "attachments":[{
		   "author_icon": document.getElementById('author_icon').value,
		   "author_name": document.getElementById('author_name').value,
		   "color": document.getElementById('color').value,
		   "fields": [{
		    "title": document.getElementById('embed_title').value,
		    "value": document.getElementById('embed_content').value,
		   }]
		  }]
		}
	}
	else{
		msgJson = {
		  "username": document.getElementById('name').value,
		  "icon_url": document.getElementById('avatar').value,
		  "text": document.getElementById('content').value
		}
	}
  post(hookurl, msgJson);
}
}
</script>

<!--
<script>
function post(url, jsonmsg){
var data = JSON.stringify(jsonmsg);
$.ajax({
    type: 'POST',
    url: url,
    crossDomain: true,
    data: data,
    success: function(responseData, textStatus, jqXHR) {
        alert(responseData);
    },
    error: function (responseData, textStatus, errorThrown) {
        alert('POST failed.\n\nError:' + errorThrown);
    }
});
}
</script>
-->

<script>
function post(url, jsonmsg){
	xhr = new XMLHttpRequest();
	xhr.open("POST", url, true);
	xhr.setRequestHeader("Content-type", "application/json");
	var data = JSON.stringify(jsonmsg);
	xhr.send(data);
	xhr.onreadystatechange = function() {
		if(this.status != 200){
			alert(this.responseText);
		}
	}
}
</script>



</body>
</html>

<!-- Hosting24 Analytics Code -->
<script type="text/javascript" src="http://stats.hosting24.com/count.php"></script>
<!-- End Of Analytics Code -->
