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




  
  **Labs:**

  **Lesson 1: GET – Error-Based – Single Quotes – String**

You get a **“Welcome Dhakkan”** (a Hindi slang word that usually refers to a stupid person). The programmer for SQLI Labs definitely has a good sense of humor. Now we get a parameter “id” with numeric value injection.
We have the login name Dumb and the password is Dump. So basically we added a parameter to the URL and pointed that parameter to the first record. There was an immediate query from the browser to the database table to fetch the record for id=1. Similarly, you can fire the query for subsequent records like 2, 3, 4….
Here is the actual query which ran at the back end:

**Select * from TABLE where id=1;**


  **Lesson 2: GET – Error-Based – Integer-Based**
  
Now we try to attack the application similarly by putting in strings such as “abc“and “abcd.” We observe that for lesson 2 we receive an error from the database. Next we do a bit of tampering with the number and add a ‘ (single quote) with the number.
We again get an error in the Mysql server for incorrect syntax.
**You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ‘\’ LIMIT 0,1′ at line 1**


