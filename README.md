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

<hr>



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


![image](https://user-images.githubusercontent.com/67774570/119028178-cb45a600-b9c4-11eb-8c74-90f0f77b6c7d.png)

![image](https://user-images.githubusercontent.com/67774570/119028204-d0a2f080-b9c4-11eb-9088-bfbccbef51c9.png)



***Overall Steps:*** 

1. Load & Register the Driver.
2. Establish the Connection.
3. Create the Statement.
4. Execute the Query.
5. Process Result 
6. close connection.

![image](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6da44543-b600-4554-b740-0c8602aa253a/Untitled.png)

---

STEPS TO MAKE A DATABASE  - JAVA CONNECTION :

1. import the package.
import java.sql.*;

2.  Load and Register the Driver.

    Register the library using the method : forName("Driver name");

    ex: Class.forName(com.mysql.jdbc.Driver);

        ^ Class is necessary because forName() is inside java.lang.Class ([Java reflection API](https://www.javatpoint.com/java-reflection))

    forName() belongs to class Class.

    java.lang.Class  →  Class.forName(com.mysql.jdbc.Driver)

3. Establish the Connection.

     by using the interface : Connection.
    Connection con            =         DriverManager.getConnection(link, username ,password);
    ^Interface   ^reference                ^class              ^Static Method of class DriverManager

    getConnection           (     "jdbc:mysql://localhost:3306/javaclass"   ,     "root"    ,        "2903"      );
    ^makes connection          ^ link to the database                                  ^username      ^password

    Connection obj = DriverManager.getConnection("jdbc:mysql://localhost:3306/java", root ,pass");

4. Create Statement:
Statement st = con.createStatement();
PreparedStatement pst = con.prepareStatement(qry);
CallableStatement  
5. Execute the Query:
st.executeQuery("query");
pst.execute();

6. Process the result.
The result will be stored in the object of Interface ResultSet.(Statement())
ResultSet rs = s.executeQuery(str);
rs.next() → will shift the pointer from 1 to 2
rs.getInt(1)+" "+ rs.getString(2)+" "+ rs.getInt(3);
(instead of writing all in line , use a while loop)  

7. Close the connection.

     con.close();
