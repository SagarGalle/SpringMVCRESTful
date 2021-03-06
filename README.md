SpringMVCRESTful
================


SpringMVC-RESTfulServices:

Spring MVC supports REST from version 3.0. It is easier to build restful web services with spring with it's annotation based MVC Framework. 
Now, take a look at  spring mvc restful web service handles requests from client.
The request process flow is as follows,

Description of the Project:

1.Note that in the published code,we have named Spring Dispatcher servlet class as "rest" and the url pattern is given as "/*" which means any uri with the root of this web application will call DispatcherServlet. 

DispatcherServlet will look for configuration files following this naming convention - [servlet-name]-servlet.xml. 

In this example, I have named dispatcher servlet class as "rest" and hence it will look for file named 'rest-servlet.xml'.
With ComponentScan tag, Spring auto scans all elements in the provided base package and all its child packages for Controller servlet.

Also, we have used <mvc:annotation-driven> tag instead of ViewResolver, with which we can directly send response data from the controller

2.Now proceed with writing the actual business logic. Our aim is to serve data from database in json format based on the request received. Create a table in MySql server using the following query,

CREATE TABLE tblUser(
 `userid` int(11) NOT NULL AUTO_INCREMENT,
 `firstname` varchar(45) DEFAULT NULL,
 `lastname` varchar(45) DEFAULT NULL,
 `email` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`userid`)
  )
Insert some dummy values into it.

3.Create a java class and name it as "User.java". This is a model class that represents the data in the database

4.Create a utility class to handle connections to database. The connection string properties are kept in a configuration file called "db.properties" in the src folder.

Properties configuration file should have contents such as this,

driver=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/usedb
user=root
password=welcome

5.Create a service class that performs data access operations to get data from database,

6.Finally let us now write Spring Controller Class that maps the incoming request to appropriate methods and returns response in json format. We are going to use @RestController annotation which has @Controller and @Responsebody annotated within itself.

7.If we take a look at the SpringServiceController class we have mapped all requests to the relative path '/service/user' using @RequestMapping annotation. There are two methods, one that returns all user data(getAllUsers()) does not take any additional request parameter and the other that returns data specific to a user id takes userid as parameter (/service/user/userid).

8.Run the application in Tomcat Server and launch http://localhost:8080/SpringRESTServiceJson/service/user/ from browser. You must see all user information listed in json format.

To get specific user information, userid needs to be appended to the request url such as this, 'http://localhost:8080/ SpringRESTServiceJson /service/user1'



