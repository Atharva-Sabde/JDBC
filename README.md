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

![image align="right"](https://user-images.githubusercontent.com/67774570/119028434-15c72280-b9c5-11eb-99fb-a00e6b9b6228.png)


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
     
     
$$================================   Preparation   ================================$$

There are two methods to add and connect the JDBC jar files.

- Paste it in the 'ext'  folder of jre.( will work globally , but if the project is moved to another machine , program won't run, as the JAR file could be missing on the other machine.)
- Make new folder  'lib' inside each Project of eclipse and build path. ( specific to the parent project , but moves with the project [mobility] , and run on any machine )

---

### MySql Connector :                                                        [ com.mysql.jdbc.Driver ]

Download the Connection .jar file from internet.  [ jar file is a library :  com.mysql.jdbc.Driver ]

Extract it and paste it in the ext folder inside JRE. [C:\Program Files\Java\jre1.8.0_281\lib\ext]

After creating a project , you need to set build path for the sql 

Add the build path to the project:

1. right click project
2. Properties
3. build path
4. libraries 
5. Add library > jre system library > Finish



### Oracle Connector:                                            [ oracle.jdbc.driver.OracleDriver ]

1. Make a New Project 
2. Make a New Folder called "lib"  
3. Go to the downloaded Oracle Connector File  and copy it .
4. Right click on lib and paste it.
5. open lib , and right click on the pasted file and select "Build Path" 
6. Select "Add to Build Path". and Done!



There are 4 different types of drivers:
1. Native driver (ODBC bridge) for MS access.
2.  Pure java drivers
3. Oracle driver
4. PostgreSql driver
5. MySql driver   (com.mysql.jdbc.Driver)

![image](https://user-images.githubusercontent.com/67774570/119269087-97ac8b00-bc13-11eb-8ab8-a4c65fdd6520.png)

<br> <hr>

![image](https://user-images.githubusercontent.com/67774570/119269103-a2672000-bc13-11eb-8674-5197ffa4c5ac.png)


<hr>
## Statements:

Statements are the Interfaces 

CRUD : Create-Read-Update-Delete

Three Types of operations :

![image](https://user-images.githubusercontent.com/67774570/119876215-47039d80-bf45-11eb-8b0b-252c783f1c4f.png)

[link](https://www.javastudypoint.com/2018/09/Statement-vs-PreparedStatement-vs-CallableStatement-in-java.html)

[https://www.javastudypoint.com/2018/09/Statement-vs-PreparedStatement-vs-CallableStatement-in-java.html](https://www.javastudypoint.com/2018/09/Statement-vs-PreparedStatement-vs-CallableStatement-in-java.html)

1. **Statement**                   :   Normal statement         (DQL operations)        [ select ]

→ Passing the query is not needed for compilation , because it compiles for every execution.

→ Passing the query is mandatory for execution : executeQuery(qry);

---

every time  sql statement is sent to the database , it does 2 things:

1. compilation of statement multiple times.    
2. Execution of the query multiple times.  [executeQuery(String )   [executeUpdate(String  )
