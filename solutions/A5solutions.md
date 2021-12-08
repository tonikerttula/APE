# Excercise A5 Solutions

I solved these excercises myself, or used a guide. These solutions work and are the official solutions, they can also be found here: https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#a5-broken-access-control

### Insecure Direct Object References

__3.__ Attributes are: role, userID.

__4.__ Open the Development Tools in the browser, and go to the Network tab.

In the lesson 3, click on View Profile.

Search forthe query "blind" in the Network tab and click on Response.

Check parameter __userID__, the expected answer is __WebGoat/IDOR/profile/userID_value__.

__5.__ I recommend checking the official solution from the link above, as the solution requires scripting! I did not complete this excercise by myself.

### Missing Function Level Access Control

__2.__ Inspect element the "Log Out" line

Below it in the HTML, you'll find the hidden elements, which are __Users__ and __Config__

__3.__ Open the Development Tools in the browser, and go to the Network tab.

Go to http://host:port/WebGoat/users.

Search for "users" in the Network tab and click on Edit and Resend.

Add the header __Content-Type: application/json__.

Check the hash in the response.
