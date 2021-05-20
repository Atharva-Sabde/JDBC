# JDBC

> Basically , JDBC is a translator between Java language and Database language...

### What is java DataBase Connectivity?

> In this data driven world , everything is run on information.
And to handle all data we need database!
Also , if you have data , then you'll surely need to connect it to the outside world!
And by using JDBC we can connect our database with java.

FrontEnd       <———>      BackEnd
                       ^ —-  JDBC

Java Database Connectivity (JDBC) is an application programming interface (API) for the programming language Java, which defines how a client may access a database. It is a Java-based data access technology used for Java database connectivity. It is part of the Java Standard Edition platform, from Oracle Corporation.


![image](https://user-images.githubusercontent.com/67774570/119027637-36db4380-b9c4-11eb-8b1f-9d262d0bc3db.png)

hr



***Assume the following hypothetical story***
You are at home ...
Now ,suddenly  you need to import some expensive goods from other country...

you            → java application
country      → Database

1. obviously you don't know the local language of that country. so you'll need a translator                              → driver software
2. Now you'll need to travel the country by any means, here assuming ,you built a road for that.                     → connection
3. Now you'll also need a vehicle (truck) to bring back the goods from the the destination.                              → Statement 
4. And you'll also need to list the requirements with the vehicle .                                                                        → Query
5. And after getting approval , you will get the goods in a box ready to be loaded into your truck.                   → Resultset
