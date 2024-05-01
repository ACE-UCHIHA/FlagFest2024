<p align="center"><a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.herokuapp.com?font=Pixelify+Sans&size=25&pause=1000&color=0CF730&center=true&random=false&width=700&lines=Official+writeup+of+Boot2root+category" alt="Typing SVG" /></a></p>

>Challenge category: Boot2root

>Author: @h4x0r3rr0r

>Writeup by: @Isaac Newtom





The flag for Fax-Corporation Intro was the exact url that was embedded in the "Fax-Corporation"
Just had to copy and paste it.
It would look like this ```flagfest{https://tryhackme.com/jr/faxcorpdev}```


Right after getting the machine IP and scanning it with nmap we discover there are 3 ports open

```
PORT   STATE SERVICE REASON
21/tcp open  ftp     syn-ack ttl 60
22/tcp open  ssh     syn-ack ttl 60
80/tcp open  http    syn-ack ttl 60
```

After enumerating and fuzzing the website for dir that is open in port 80
we discover there is a Administrator Login portal in ```/administrator-login.html```
In the source code of /administrator-login.html there was this comment in the html
```bruh "204f2ea6051c33fc2b53674b07086f83f5814c084f3e5ec07fc48e88d33313a3" ```
This was SHA256 hash we got "```mychemicalromance```" after cracking this

we also discovered some interesting files

```
/login.php             
/index.html          
/announcements.txt       
/404.html                
/robots.txt      
/wp-admin              
/user_upload
```


Now if we try to brute force the Administrator Login portal, after brute forcing for a while you'll realize this is useless. Yes it was a rabbit hole.


checking the ```/announcements.txt``` you'll get creds for the ftp that is running on port 21

FTP Creds :
        Username : ```userftpdjohn```
        Password : ```goodbyeftpworld123@#!```

Now we log in and list all the files and dir with ```ls -la```
and we get two files:
```
.wp-web-manage-00.txt
wp-web-manage-01.txt
```



In the .wp-web-manage-00.txt you'll get a username "```IsThatYouBruhAdmin```" for the Administrator Login portal


Now let's try to login with the user: ```IsThatYouBruhAdmin``` and pass: ```mychemicalromance```
and we are Admin.
 In the Admin panel we get a option to upload files from ```/fax-corp_uploadsite-management.html```

 so we upload a php reverse shell and look for it in ```/user_upload```, It is there.

 Now we setup a listener and execute the php file to get a reverse shell.
 we'll find the flag for ```Fax-Corp System Access``` in ```/var/www/web.txt```

 After enumerating the system we get a ssh key in ```/var/www/html/wp-admin/managers-ssh-creds.bak``` for the user manager.

Now we login as manager and find the flag for ```Fax-Corp User Access``` in managers home dir.

Finally we try to escalate our privileges and get root.

we will find that ```/usr/bin/wget``` has SUID that will let us use wget using roots privilege.

We will use this wget to escalate our privilege
```
TF=$(mktemp)
chmod +x $TF
echo -e '#!/bin/sh -p\n/bin/bash -p 1>&0' >$TF
wget --use-askpass=$TF 0
```


We finally got the same privilege as root.
The final flag for ```Fax-Corp System Root Access``` can be found in ```/root/root.txt```
