# Solution for DVWA Execution Exercise

### Low

On the right bottom corner, you can click and see the source code.

![](https://i.gyazo.com/03c6b852bb62991c70074f787e5391fa.png)

From the source code we can see, that there is no check to see if the $target matches an IP-address, and there is no filtering for special characters. So we can enter:

> 127.0.0.1 ; cat /etc/passwd

And list the contents of the /etc/passwd file
![](https://i.gyazo.com/d1431a5238e9215761a0a7bc5a59fdb8.png)

### Medium

Checking the source code again, we can see that the __;__ and __&&__ characters are now excluded.

![](https://i.gyazo.com/d27f01b73bb6b5a6dd1beab55ec060bc.png)

However, we can still use the pipe __|__. Lets list the /etc/passwd file's contents:

> 127.0.0.1| cat /etc/passwd

![](https://i.gyazo.com/88974c1d6bce5a92ccdd75732129e369.png)

### High

I have found walkthroughs on the internet that work for this, (i.e. https://n3dx0o.medium.com/dvwa-command-execution-solutions-low-medium-high-6ee354dc2974) however, for this session, I couldn't get anything to work.
