# Excercise A2 Solutions

I solved these excercises myself, or used a guide. These solutions work and are the official solutions, they can also be found here: https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#a2-broken-authentification

### Authentication Bypasses

__2.__ Open the Development Tools in the browser, and go to the Network tab.

Click the Submit-button without typing anythin in the text fields.

Locate the query to verify-account in the Network tab and click on Edit and Resend. It can be found easily by hovering your mouse over the text fields or the submit button.

Modify the parameters __secQuestion0=&secQuestion1=&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=yourid__ to __secQuestion2=&secQuestion3=&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=yourid.__

### JWT tokens

I recommend reading up the official solution guide. I did not solve this excercise myself. https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#jwt-tokens

### Password reset

__2.__ There is a bug on WebWolf that prevents access to Mailbox.

Click on Forgot your password?.

Enter the email address {user}@....

Open the mail on WebWolf to retrieve the new password.

__4.__ admin and green, jerry and orange, tom and purple, larry and yellow.

__5.__ Try every choice and read up the advice!

__6.__ If you are using WebWolf in this excercise, I recommend going to the official page to read up the solution, as I did not complete it. https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#password-reset

### Secure Passwords

Try using letters, numbers and special characters. Don't use words linked to the website, your username or typical letter combinations (i.e. qwerty). Have enough lenght.
