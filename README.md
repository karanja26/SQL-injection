<h1>Disclaimer</h1>
<br>The content of this project is intended solely for educational and ethical purposes. The skills and knowledge shared are to be used only for lawful activities, such as securing systems and networks with proper authorization. Unauthorized access, tampering, or exploitation of any computer systems or networks is illegal and punishable by law. By participating in this project, you agree to abide by all applicable laws and to use your skills responsibly.</br>
<h1>SQL injection<h1> 
<h2>Description</h2>
<br>SQL injection is a code injection technique that exploits vulnerabilities in an application's software by inserting malicious SQL queries into input fields. This can allow attackers to manipulate a database, gaining unauthorized access to data or executing administrative operations.
  Automated Tools and Scripts: Attackers increasingly use automated tools to scan for and exploit SQL injection vulnerabilities. Tools like SQLmap can automate the discovery and exploitation of SQL injection flaws.
<br/>
  SQL injection is the most common and devastating attack that attackers can use to take control of data-driven web applications and websites. It is a code injection technique that exploits a security vulnerability in a website or application’s software. SQL injection attacks use a series of malicious SQL (Structured Query Language) queries or statements to directly manipulate any type of SQL database. Applications often use SQL statements to authenticate users, validate roles and access levels, store, obtain information for the application and user, and link to other data sources. SQL injection attacks work when applications do not properly validate input before passing it to a SQL statement.
When attackers use tactics like SQL injection to compromise web applications and sites, the targeted organizations can incur huge losses in terms of money, reputation, and loss of data and functionality.
As an ethical hacker or penetration tester (hereafter, pen tester), you must possess sound knowledge of SQL injection techniques and be able protect against them in diverse ways such as using prepared statements with bind parameters, whitelist input validation, and user-supplied input escaping. Input validation can be used to detect unauthorized input before it is passed to the SQL query.
The labs in this module give hands-on experience in testing a web application against various SQL injection attacks.

<h2>Tools and appplication usedused</h2>
<b>SQLmap </b>
<br>sqlmap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database servers. It comes with a powerful detection engine, many niche features, and a broad range of switches—from database fingerprinting and data fetching from the database to accessing the underlying file system and executing commands on the OS via out-of-band connections.</br>
<br>You can use sqlmap to perform SQL injection on a target website using various techniques, including Boolean-based blind, time-based blind, error-based, UNION query-based, stacked queries, and out-of-band SQL injection.
In this task, we will use sqlmap to perform SQL injection attack against MSSQL to extract databases.
</br>
<h2>Environment used</h2>
<b>Windows 11,Parrot security machine</b>
<h2>Program walkthrough:</h2>
<br>Note: In this task, you will pretend that you are a registered user on the http://www.moviescope.com website, and you want to crack the passwords of the other users from the website’s database.</br>

<p align="center">
  step 1.	Click  Parrot Security to switch to the Parrot Security machine.
	In the login page, the attacker username will be selected by default. Enter password in the Password field and press Enter to log in to the machine.

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/fffb9faa-c83d-4aeb-9315-88e1eb1d4439"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 2.	Click the Mozilla Firefox icon from the menu bar in the top-left corner of Desktop to launch the web browser.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/eb86ba46-7f32-4601-a59b-ff8ec91dd68e"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 3.Type http://www.moviescope.com/ and press Enter. A Login page loads; enter the Username and Password as sam and test, respectively. Click the Login button.
Note: If a Would you like Firefox to save this login for moviescope.com? notification appears at the top of the browser window, click Don’t Save.<br>5.	Once you are logged into the website, click the View Profile tab on the menu bar and, when the page has loaded, make a note of the URL in the address bar of the browser.</br>

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/a9cc68a0-ed61-4abf-a616-11adaf2c9da9"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 4.Right-click anywhere on the webpage and click Inspect Element (Q) from the context menu, as shown in the screenshot.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/4209c51e-775d-4529-b5fe-82e214f025cc"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>
<p align="center">
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/8821dd7f-1468-4580-a3f2-09180e76ce5d"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 5.The Developer Tools frame appears in the lower section of the browser window. Click the Console tab, type document.cookie in the lower-left corner of the browser, and press Enter.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/3f076295-8d2c-4ff2-aaee-90a124abc45d"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 6.Select the cookie value, then right-click and copy it, as shown in the screenshot. Minimize the web browser.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/6bbb55c6-8f11-4baf-85ae-dbdb605581c3"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 6.Click the MATE Terminal icon at the top of the Desktop window to open a Parrot Terminal window.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/8481a2b3-3806-452d-81d8-50a2235da2ef "alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 7.A Parrot Terminal window appears. In the terminal window, type sudo su and press Enter to run the programs as a root user.
In the [sudo] password for attacker field, type your password and press Enter.
Note: The password that you type will not be visible.

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/6d5549f7-8539-4142-8300-c1b8843235b5" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 8.In the Parrot Terminal window, type sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value that you copied in Step 5]" --dbs and press Enter.
Note: In this query, -u specifies the target URL (the one you noted down in Step 5), --cookie specifies the HTTP cookie header value, and --dbs enumerates DBMS databases.
The above query causes sqlmap to enforce various injection techniques on the name parameter of the URL in an attempt to extract the database information of the MovieScope website

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/8090aee6-8a67-4481-9d2d-0717e503a0bf"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 9.If the message Do you want to skip test payloads specific for other DBMSes? [Y/n] appears, type Y and press Enter.
	If the message for the remaining tests, do you want to include all tests for ‘Microsoft SQL Server’ extending provided level (1) and risk (1) values? [Y/n] appears, type Y and press Enter.
	Similarly, if any other message appears, type Y and press Enter to continue.

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/027c14e8-9043-4023-8d79-d0ea102e9699" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 9.sqlmap retrieves the databases present in the MSSQL server. It also displays information about the web server OS, web application technology, and the backend DBMS, as shown in the screenshot.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/ac3db0e2-a5e3-4879-b330-2dc585ab7153"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 10.Now, you need to choose a database and use sqlmap to retrieve the tables in the database. In this lab, we are going to determine the tables associated with the database moviescope.
Type sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step 6]" -D moviescope --tables and press Enter.
Note: In this query, -D specifies the DBMS database to enumerate and --tables enumerates DBMS database tables.
The above query causes sqlmap to scan the moviescope database for tables located in the database.

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/c0060dc0-3420-4cd5-8cf1-55158ba82370" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 11.sqlmap retrieves the table contents of the moviescope database and displays them, as shown in screenshot. 
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/e9ce9b33-09c4-4551-94c4-7b5d3947af2f"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 12.Now, you need to retrieve the table content of the column User_Login.
Type sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step 6]" -D moviescope -T User_Login --dump and press Enter to dump all the User_Login table content.

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/ca6b0b2c-ea6c-4356-8ec5-d209f58bc499"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 13.sqlmap retrieves the complete User_Login table data from the database moviescope, containing all users’ usernames under the Uname column and passwords under the password column, as shown in screenshot.
You will see that under the password column, the passwords are shown in plain text form.
	
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/7bedb2ce-aaf6-4426-8652-bd6cf4f1ae4d" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 14.To verify if the login details are valid, you should try to log in with the extracted login details of any of the users. To do so, switch back to the web browser, close the Developer Tools console, and click Logout to start a new session on the site.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/cdff5470-2b33-403b-b360-f11daf85dbda" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 15.The Login page appears; log in into the website using the retrieved credentials john/qwerty.
Note: If a Would you like Firefox to save this login for moviescope.com? notification appears at the top of the browser window, click Don’t Save.
 
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/ee33b567-3de3-43bf-b597-78552d4b072f"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 16.You will observe that you have successfully logged into the MovieScope website with john’s account, as shown in the screenshot.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/29e82ffc-c987-4fe1-9c48-02aa6d9de516"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 17.Now, switch back to the Parrot Terminal window. Type sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in " --os-shell and press Enter.
Note: In this query, --os-shell is the prompt for an interactive OS shell.
 
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/f1063cb2-dcf1-4550-9558-acc2e4318c1d"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 18.If the message do you want sqlmap to try to optimize value(s) for DBMS delay responses appears, type Y and press Enter to continue.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/f26d7403-68dd-4092-a8cc-ff13e5cf4180" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>


<p align="center">
  step 19.sqlmap will retrieve the hostname of the machine on which the target web application is running, as shown in the screenshot. 
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/9b5fe266-298f-4633-ab51-d5b7ad81e3c8"
alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 20.Type TASKLIST and press Enter to view a list of tasks that are currently running on the target system.
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/4b645c8e-9a63-4462-be5f-7c00a9166e37"alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 21.If the message do you want to retrieve the command standard output? appears, type Y and press Enter.
The above command retrieves the tasks and displays them under the command standard output section, as shown in the screenshots below.
 
 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/1713f17b-1902-49c9-856c-0c330dc45532" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>

<p align="center">
  step 22.Following the same process, you can use various other commands to obtain further detailed information about the target machine.
To view the available commands under the OS shell, type help and press Enter.

 <br/>
  <img src="https://github.com/karanja26/SQL-injection/assets/55892563/d503a1c4-fccc-4c08-828c-b528510a346f" alt="image" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
  <br/>
</p>
________________________________________  

	This concludes the demonstration of how to launch a SQL injection attack against MSSQL to extract databases using sqlmap.
	Close all open windows and document all the acquired information.
	You can also use other SQL injection tools such as Mole (https://sourceforge.net), Blisqy (https://github.com), blind-sql-bitshifting (https://github.com), and NoSQLMap (https://github.com) to perform SQL injection attacks.

