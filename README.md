# Natas 
## Natas 0
Username: natas0
Password: natas0
URL:      http://natas0.natas.labs.overthewire.org

We will get a comment in while inspecting as: <!--The password for natas1 is g9D9cREhslqBKtcA2uocGHPfMZVzeFK6 -->

And we get the password for Natas 1:g9D9cREhslqBKtcA2uocGHPfMZVzeFK6

## Natas 1
Username: natas1
Password: g9D9cREhslqBKtcA2uocGHPfMZVzeFK6
URL:      http://natas1.natas.labs.overthewire.org

Open terminal and use _curl_ _-u_ _natas1:g9D9cREhslqBKtcA2uocGHPfMZVzeFK6_ _http://natas1.natas.labs.overthewire.org/_ command to get the html code of the website.
The HTML code I get is as follows:

'''
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas1", "pass": "g9D9cREhslqBKtcA2uocGHPfMZVzeFK6" };</script></head>
<body oncontextmenu="javascript:alert('right clicking has been blocked!');return false;">
<h1>natas1</h1>
<div id="content">
You can find the password for the
next level on this page, but rightclicking has been blocked!

<!--The password for natas2 is h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7 -->
</div>
</body>
</html>
'''
