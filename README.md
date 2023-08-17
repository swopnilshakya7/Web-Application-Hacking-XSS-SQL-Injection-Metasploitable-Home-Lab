# Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab

<h2>Description</h2>
This project is a home lab for the hands on demonstration of common Cross Site Scripting and SQL injection attacks. In the end, the ways to code the web application is also provided to prevent websites from such attacks.

<br />


<h2>Languages and web attack techniques</h2>

- <b>SQL (Structured Query Language)</b>
- <b>JavaScript | HTML | PHP</b>
- <b>Cross Site Scripting</b>
- <b>SQL Injection</b>



<h2>Environments Used </h2>

- <b>Oracle VM box</b> 
- <b>Kali Linux</b>
- <b>Metasploitable web server</b>

<p align="left">

<h2>LAB </h2>

For safe practice, we are going to use the vulnerable web server provided by metasploit. The name of the web server is metasploitable. </br>
https://sourceforge.net/projects/metasploitable2-gohack/files/

</br>
We need to download this:</br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/12839ec1-bc67-4a72-bf88-4906fe202dad)


</br>After the successful download, now we can run the ova file via Virtual box.

We need to go to File>import appliances> Choose the .ova file</br>


![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/54a922c3-4e5a-4d52-9c34-84ccbfd4af1d)



Provide a good RAM and CPU usage for the system so that it will be running smoothly.</br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/81adbd38-a850-4f94-8735-5c5aa1709a58)



Make sure to do the Network setting of the server by right clicking the server> Settings> Network Tab> and in the adapter section, choose bridge adapter so that the server will be reachable through other virtual machine and your own laptop Operating System too.

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/7d8e0eea-0298-4c4d-a432-7c6b881ea20e)


Now, we can select the metasploitable2-H4k from the virtual box and click start to run the machine. Since it is a web server, it will run in text based interface instead of a GUI (Graphical User Interface)/
First default, </br>
username= msfadmin </br>
password= msfadmin </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/750ffa65-4a2b-4c21-80d4-3b8a743e42c6)


Note: password won’t appear on the screen </br>

By getting this machine up via virtual box, we will be able to call it using web browser in our attacking machine (it can be another virtual machine or our own machine). So for that, we need to know the ip address of the Metasploitable to use that in the web browser of the attacker machine. </br>

To get the ip address, </br>
Command:  ip a </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/8d35b6ce-2790-44fa-9f62-7d062473323d)


Here, we can see the IP address of the web server is 10.0.0.210 which we are going to use in our attacker machine to open the web application (vulnerable web application).

We are using our kali machine to exploit the web application. So we can go to our browser and type the ip address.</br>


![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/8826526c-4597-479b-b953-1ed74a589a45)


We will be able to something like this.</br>



<h3>Hacking from browser</h3></br>

This web server contains 5 different vulnerabilities. For now, we ill be just focusing on one of them. We will look the DVWA (Darn Vulnerable Web App).  DVWA has got different vulnerability levels. And for this lab, we will be using the lowest security level.

We need to click on DVWA to use this vulnerability for the hacking. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/e28d51aa-d8d5-40a2-aa31-2063da6f911f)



We will see a php website. The default username and password for this web app is: </br>
username: admin </br>
password: password </br>

To use the lowest security level of the website, we just need to click on DVWA Security that we can see on the left and then choose the security level to low and click Submit.</br>


![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/53fe1db7-cb3e-4719-b4b0-811f3a41b635)



With this security level, we will be able to perform cross site scripting and SQL injection attacks on the website. These two attacks belongs to most popular web application attacks. </br>


<h4>Cross site scripting attack</h4> </br>

Cross Site Scripting attack is also referred to as code injection attack as an attacker can inject a code of their choice, sometimes as a reflection and in case of stored XSS, as a permanent web application defect too. </br>

I) Reflected XSS </br>
Lets try the reflected XSS for first. To do that, we need to click the XSS reflected on the left tab. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/84f9b4a3-dfd2-4211-831c-f0d6503ef585)


We will reach this page on the website. This is specially designed for the reflected XSS. 
If we simply type our name and press the submit button, the site will reply by using the user input as 
Hello your_name. Here, we can see a simple form with submit page. 

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/a49b9ae1-c390-4db0-b986-dc2e3e9d607c)


Such that, there is chances of reflected XSS on the website.

For reflected XSS, we can simply use a simple Java Script Command.
alert(“You’ve been hacked!”);.
By putting this as the input in the form field with proper html tag we will be able to execute the reflected XSS in the website.

So, lets try this as the input in the form.
<script>alert(“You’ve been hacked!”);</script>


![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/05b73a12-13f6-4dda-95b3-d44efb1e4963)



Here,

Instead of showing Hello <script>alert(“You’ve been hacked!”);</script>, the site is reflecting our javascript code. That simply means the website is vulnerable to reflected XSS.

</br>
II) Stored XSS </br>
Stored XSS is more harmful than any reflected XSS as it stays in the database of the website server. And anyone who visits the page will get impacted from the injected code.

Example of probable Stored XSS: A forum where users can input their comments. The comments get stored in the database of the website and whenever any user visit the same page, the comment will be there and get executed.

To perform this attack, lets go the Stored XSS page by clicking on the XSS stored on the left tab. And try the page work with the following input under name and message boxes. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/0eef5a4d-2ceb-4812-9d6c-8bc6d8669ea2)



Here, we can see that our comment got stored in the database of the website and always gets loaded when this page is called. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/9a5a4be2-b8e0-419d-9f79-7ac3c0e06cf6)



Now, lets test with our JavaScript and HTML code injection, we can also test this page. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/67bdd8b7-818b-4527-82cf-8163f2738f43)


</br>
The output: </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/511b8c00-c9b4-4e6f-9146-d888143d36e0)





</br>
Every time we refresh this page or try to reload this page on other machine too, same output will come as all the time the script will get executed as it is saved in permanently in the web server.

So, lets take one step further to analyze the consequences. </br>

Instead of one simple alert via JS, we can also embed a link on this. Such that, whenever any viewer or visitor visits the page, will get directed to that link.

For that, JS code injection can be done as follows. </br>

<script>window.location.href=”website_or_link_of_your_choice.com”;</script> </br>

For example, lets put swopnilshakya.com.np for now. Our payload will become, </br>
 
<script>window.location.href=”https://www.swopnilshakya.com.np”;</script> </br>

Before, we test this payload we can completely renew the database of our site. So that our previous alert payload will get deleted from the web server.
For that, we need to click on the setup tab of left side and then Create/ Reset Database button.




![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/59babc67-1602-4ab3-bc5c-f836888f4313)













Lets try the new payload of website. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/10a67f85-8162-4b0a-a8c7-a5cc7f85c3d8)



When we submit this payload and click on the link, the site will completely get redirected to the link we have provided in the payload. And as this payload will be stored in the web server, every time we execute the page, the payload and site execution will be also done. 

We can try reloading the page or reach the page by clicking on XSS stored button on the left tab, we will be redirected to: https://www.swopnilshakya.com.np. </br>

















<h4>SQL Injection </h4>


SQL (Structured Query Language) is a language used in most of the databases. SQL injection refers to inserting malicious SQL code to trick the web application and steal, expose the sensitive data or bypass the authorizations too which are linked with the back end databases of the web application.

One of the most common SQL qurey while accessing the database is: </br>
1. SELECT password FROM users WHERE username=’swopnil’ </br>

This query is designed to take the username from user and show the password of that user if its available in the database of web server. Hence, the output will only come if there is a user whose name is swopnil. The query will get the truth value and will result the password of respective row. 

Lets see a simple query by modifying the above one. </br>

2. SELECT password FROM users WHERE username=’swopnil’ OR 1=’1’ </br>

In this query, there are two sections, one is asking for username to give the result password for that specific username if it exist or the query becomes true while another portion is a true false case. If the user will put 1 as the input for that the whole query will be true as the logic defines that the query will be true when either of the section is true. 

With the help of sql injection, we can modify the query number 1 to query number 2 to make the truth value true for the query and output result from the database. We can see the practical demonstration of this case by clicking to the SQL injection tab on the left side of our web application metasploitable. </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/79c0c6b4-d632-41fd-ae4b-1dde94b3385b) </br>


We have to put ‘ OR 1=’1  in the box and submit to modify the main sql qurey behind the webpage to the one we modified. So, that 1=1 is always true and it will return the results from the database. </br>


![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/5c10f1df-0c5b-4a4a-9b66-c921c739a469) </br>


Here

We can see that the query got true and resulted in the data from the database of web server.


We can try this even in different way using the union commad. Union command in SQL joins two different queries and results accordingly.
Lets try this payload: ‘ union select user, password from users# </br>

' UNION SELECT user, password from users# </br>



we can see the results as per our query. </br>


![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/26f8e41d-86a7-4c1e-a2e1-f1048a188cd4)



</br>


<h3> Securing Web applications </h3>

The metasploitable webserver is not just for ethical hacking learning but it also does have the ways to secure the site with these common attacks. For that, in every vulnerable page, there is viw source button on the right bottom corner. With that, we can view the page source code. We need to view the source codes of each page in different security levels and compare it to learn the ways of securing a web application.

Lets see the page of sql injection with security level: low, medium and high respectively and compare them. </br>

Low: </br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/b4c34673-9308-40c5-ab99-f2a70ed072b1)


Here, id is the variable of php code which is storing the user input and it is being directly passed to the database query without any filtration or sanization. Such that whatever we put as the input will be directly presented in front of the database. So injection is lot easier.

</br>
Medium:</br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/859c998b-ca9b-4360-a803-310daaac3408)


Here, first the user input is being stored in the $id variable and then being passed through the function mysql_real_escape_string(). With the help of which, the user input is being sanitzed. The function adds escape characters (backslash \) before any special characters like  quotation marks. And database treats any character after the escape character as text not the part of code.

</br>
High:</br>

![image](https://github.com/swopnilshakya7/Web-Application-Hacking-XSS-SQL-Injection-Metasploitable-Home-Lab/assets/140642619/1ebca61d-8683-4cba-905f-8826fd352e9a)

</br>
In this level, more security and sanitizing of user input is being added.
The stripslashes() function removes the backslashes from the users text which gives another level step of sanitation to the user input. </br>

For each type of web attacks, we can do the same way of learning to analyze the way of protecting the web application.





<p align="left">
<br/> Step 1: Virtual machine setup.<br/>
