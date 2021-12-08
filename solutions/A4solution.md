# Excercise A4 Solution

I solved these excercises myself, or used a guide. These solutions work and are the official solutions, they can also be found here: https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#a4-xml-external-entities-xxe

__3.__ Open the Development Tools in the browser, and go to the Network tab.

On WebGoat, post a comment.

Search the "simple" query in the Network tab and click on Edit and Resend.

Edit the body with: <?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>.

__4.__ Open the Development Tools in the browser, and go to the Network tab.

On WebGoat, post a comment.

Search the "content-type" query in the Network tab and click on Edit and Resend.

![](https://i.gyazo.com/c72ebfecf09f763ede6a0bde43ee1639.png)

If you want to copy and paste the code, head to the official site linked on top of the page, this markdown document refused to show it as text.

__7.__ I did not complete this excercise myself, so head to the official solutions to see how it's done! https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#a4-xml-external-entities-xxe
