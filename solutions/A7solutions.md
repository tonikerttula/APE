# Excercise A7 Solutions

I solved these excercises myself, or used a guide. These solutions work and are the official solutions, they can also be found here: https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#a7-cross-site-scripting-xss

__2.__ Many browsers prohibit running Javascript in the URL bar, but open Developer Tools, and run the script in console.

> javascript:alert(document.cookie);

![](https://tonikerttula.files.wordpress.com/2021/11/image-76.png?w=1024)

__7.__ Run the scipt in the __Enter your credit card number:__ box:

> <script>alert()</script>

__10.__ Open the Development Tools in the browser, and go to the Debugger tab.

Go to the path goatApp/View/GoatRouter.js and open the file.

Search "routes" to find 'test/:param': 'testRoute'.

Answer is __start.mvc#test/__

__11.__

Open the Development Tools, and go to the Console tab.

Navigate to the URL http://host:port/WebGoat/start.mvc#test/<script>webgoat.customjs.phoneHome()<%2Fscript>.

The number is in the function output
  
__12.__
  
1. Solution 4
  2. Solution 3
  3. Solution 1
  4. Solution 2
  5. Solution 4
  
