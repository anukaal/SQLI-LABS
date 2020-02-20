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
