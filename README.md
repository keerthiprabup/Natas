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
URL:      http://natas4.natas.labs.overthewire.org

Here the website mentioned that the website _http://natas5.natas.labs.overthewire.org/_ should refer the login of the natas4 site to get the website.

I used burpe suite to intercept the request to set the referer.

For that open the burpe suite and go with capturing the request in proxy and intercept the requests.

Add a line _Referer:_ _http://natas5.natas.labs.overthewire.org/_ and forward the request.

Swipe on to the browser.

Hurray!! we got the pass.

## Natas 5
Username: natas5
Password: Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD
URL:      http://natas5.natas.labs.overthewire.org

The website mentions like that we are not logged in!

Inspect the page and go to the cookies option availble at applications.

There you can see that the loggedin value is 0, change it into 1 and refresh the page.

We got the pass!!

## Natas 6
Username: natas6
Password: fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR
URL:      http://natas6.natas.labs.overthewire.org

We could see a input bar in this website;

Inspect the page, you will note this _/includes/secret.inc_ in it.

Add the path to the browser.

You will get a string $secret = "FOEIUWGHFEEUHOFUOIU"- it is the thing we need to search in the web page.

We got the pass!!

## Natas 7

Username: natas7
Password: jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr
URL:      http://natas7.natas.labs.overthewire.org

We got a hint by inspecting the website:
<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->

Update the path as: _http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8_

Hurray!! We got the pass.

## Natas 8
Username: natas8
Password: a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB
URL:      http://natas8.natas.labs.overthewire.org

We got from the source code that:
$encodedSecret = "3d3d516343746d4d6d6c315669563362"

And the type of encoding is specified as:
bin2hex(strrev(base64_encode($secret)))

So we need to decrypt the encoded value in the reverse way as decode hex, reverse the string and decode the base64 string.

Input the resultant string in the secret input bar and we will find the pass.

## Natas 9
Username: natas9
Password: Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd
URL:      http://natas9.natas.labs.overthewire.org

I could see the source code is excecuting command in its program like grep.

So let us try cat command in the search bar to view the passwd file with the commad: _;cat_ _/etc/natas_webpass/natas10_

Hurray!! We got the pass.

## Natas 10
Username: natas10
Password: D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE
URL:      http://natas10.natas.labs.overthewire.org

This one is likely as such as the previous one but it is mentioned that in the source code to not to use '/[;|&]/'

So we try it with the command: .* cat /etc/natas_webpass/natas11 #

And it worked!!

## Natas 11
Username: natas11
Password: 1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
URL:      http://natas11.natas.labs.overthewire.org

We get that the cookies were encryted using xor cipher and the algorithm of the encryption was mentioned in the source code.

The encrypted cookie can be found at the application->cookie options in the inspect option.
The code for decrypting the key:  
    
    $cookie = "MGw7JCQ5OC04PT8jOSpqdmkgJ25nbCorKCEkIzlscm5oKC4qLSgubjY=";  
  
    function xor_encrypt($in) {  

      $key = json_encode(array( "showpassword"=>"no", "bgcolor"=>"#ffffff"));  
      $text = $in;  
      $outText = '';  
  
      // Iterate through each character  
     for($i=0;$i<strlen($text);$i++) {  
     $outText .= $text[$i] ^ $key[$i % strlen($key)];  
      }  
  
     return $outText;  
    }  
    echo xor_encrypt(base64_decode($cookie)); 
After getting the key, encode the cookie with the key using the program:
    
    $data = array( "showpassword"=>"yes", "bgcolor"=>"#ffffff");  
    function xor_encrypt($in) {  
        $key = 'qw8Jqw8Jqw8Jqw8Jqw8Jqw8Jqw8Jqw8Jqw8Jqw8Jqw8Jqw8Jq';  
        $text = $in;  
        $outText = '';  
  
        // Iterate through each character  
        for($i=0;$i<strlen($text);$i++) {  
        $outText .= $text[$i] ^ $key[$i % strlen($key)];  
    }  
  
        return $outText;  
    }  
    echo base64_encode(xor_encrypt(json_encode($data)));
You will get the proper cookie as:MGw7JCQ5OC04PT8jOSpqdmk3LT9pYmouLC0nICQ8anZpbS4qLSguKmkz
Change the cookie in the website and reload.

We got the password!!

## Natas 12
Username: natas12
Password: YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG
URL:      http://natas11.natas.labs.overthewire.org

By observing the website and the source code, we can upload a file to the backend and excecute commands by scripting inside the file.
As it is looking for jpg, we are going to make a jpg file to upload.

We need to store the command: <?php echo system("cat /etc/natas_webpass/natas13"); ?> inside the file.
To input the file as a php excecutable file we change the extension from jpg to php on the inspect tab filename=suhgvsdfg.jpg.

Uploading the file redirects to a hyperlink following password.

## Natas 13
Username: natas13
Password: lW3jYRI02ZKDBb8VtQBU1f6eDRo6WEj9
