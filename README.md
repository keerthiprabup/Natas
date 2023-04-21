# Natas 
## Natas 0
Username: natas0
Password: natas0
URL:      http://natas0.natas.labs.overthewire.org

We will get a comment in while inspecting as: <!--The password for natas1 is g9D9cREhslqBKtcA2uocGHPfMZVzeFK6 -->

We found the pass!!

## Natas 1
Username: natas1
Password: g9D9cREhslqBKtcA2uocGHPfMZVzeFK6
URL:      http://natas1.natas.labs.overthewire.org

Open terminal and use _curl_ _-u_ _natas1:g9D9cREhslqBKtcA2uocGHPfMZVzeFK6_ _http://natas1.natas.labs.overthewire.org/_ command to get the html code of the website.

After analyzing the code you will get a comment:<!--The password for natas2 is h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7 -->

We found the pass!!

## Natas 2
Usename: natas2
Password: h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7
URL:      http://natas2.natas.labs.overthewire.org

After entering the website, inspect the site and analyze the html code.

You will get a image code on the path _/files/pixel.png_ .

Edit the path in the browser as _http://natas2.natas.labs.overthewire.org/files_ and check for the existence of any other files in it.

You will be shown up with a file named _user.txt_, open the file.

We found the pass!!

## Natas 3
Username: natas3
Password: G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q
URL:      http://natas3.natas.labs.overthewire.org 

While inspecting you will be getting a message saying "Not even google will find it this time".

Go with changing the path to _robots.txt_ and hence you will get a path _/s3cr3t/_, navigate to it.

You will get a file named _users.txt_, and you will get the password for the next level.

The final path would be like: _http://natas3.natas.labs.overthewire.org/s3cr3t/users.txt_

## Natas 4
Username: natas4
Password: tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm
URL:      http://natas3.natas.labs.overthewire.org

Here the website mentioned that the website _http://natas5.natas.labs.overthewire.org/_ should refer the login of the natas4 site to get the website.

I used burpe suite to intercept the request to set the referer.

For that open the burpe suite and go with capturing the request in proxy and intercept the requests.

Add a line _Referer:_ _http://natas5.natas.labs.overthewire.org/_ and forward the request.

Swipe on to the browser.

Hurray!! we got the pass.

