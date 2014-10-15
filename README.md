SpringMVCRESTful
================

                                        SpringFramework

•	Spring is a light weight and open source framework created by Rod Johnson in 2003. Spring is a complete and a modular framework,  means spring framework can be used for all layer implementations for a real time application or spring can be used for the development of particular layer of a real time application unlike struts [ only for front end related ] and hibernate [ only for database related ], but with spring we can develop all layers
•	Spring framework is said to be a non-invasive means it doesn’t force a programmer to extend or implement their class from any predefined class or interface given by Spring API, in struts we used to extend Action Class right that’s why struts is said to be invasive
•	In case of struts framework, it will forces the programmer that, the programmer class must extend from the base class provided by struts API
•	Spring is light weight framework because of its POJO model
•	Spring Framework made J2EE application development little easier, by introducing POJO model
Spring having this much of demand because of the following 3 reasons….
•	Simplicity
•	Testability
•	Loose Coupling
Simplicity
Spring framework is simple because as it is non-invasive, POJO and POJI model
Testability
Actually for writing the spring application, server [Container] is not mandatory, but for struts applications we need a server, and for EJB too.  If we want to test the application it may need lot of changes in the source and each time we must restart the server to view the changes, which is little tedious and time taking but we can over come this in Spring, for testing spring application server is not mandatory spring has it own container to run the applications.
Spring can be used to develop any kind of java application, means we can develop starting from console application to enterprise level application
Loose Coupling
In spring objects are loosely coupled, this is the core concept of spring framework .

Pitfalls:
Complex: One of the major criticisms faced by the Spring framework is that it is complex! No so clear focus, more than 2400 classes, 49 other tools and tons of the other things make it complicated for the developers.
Longer Learning Curve: If you’re a newbie developer, it would be quite difficult for you to learn Spring framework. The main reason behind this is a whole host of new programming methods and detailing require understanding how to set up the Spring XML configuration file.
All the Spring applications require a lot of XML: If you’ve ever worked with Spring framework, you might be knowing that applications developed using Spring framework often require a huge amount of XML. So, if you’re considering Spring for your next development, be prepared to spare a lot of time coding in XML.
Tons of parallel mechanisms frustrate developers: Of course, parallel mechanisms are useful to perform the same task in different ways. However, when we talk about Spring framework, you will find multiple parallel mechanisms, which at the end confuses developers. It makes developers to spend lots of understanding each of them and choose the best one among them.
Lack of Guidelines: No clear guidance on cross-site scripting attacks and cross-site request forgery attacks in Spring MVC documentation. Also, it suffers from a several security holes.
Unlike any other technology or frameworks, Spring too suffers from certain drawbacks or criticisms. However, it also brings a whole host of development and deployment related benefits for the developers, which at the end simplifies their tasks. Ensure that you keep in mind all the pros and cons discussed in this post before you go ahead for Spring development
SpringMVC-RESTfulServices:
Spring MVC supports REST from version 3.0. It is easier to build restful web services with spring with it's annotation based MVC Framework. 
Now, take a look at  spring mvc restful web service handles requests from client. The request process flow is as follows,
1.Client application issues request to web service in the form of URI's.

  Example: http://example.com/service/greetings/mohan
2. All HTTP Requests are intercepted by DispatcherServlet (Front End Controller). - This is defined in the web.xml file.
3. DispatcherServlet looks for Handler Mappings. Spring MVC supports three different ways of mapping request URI's to controllers : annotation, name conventions and explicit mappings. Handler Mappings section defined in the application context file, tells DispatcherServlet which strategy to use to find controllers based on the incoming request.
4. Requests are now processed by the Controller and response is returned to DispatcherServlet. DispatcherServlet looks for View Resolver section in the application context file. For RESTFul web services, where our web controller returns ModelAndView object or view names, 'ContentNegotiatingResolver' is used to find the correct data representation format.

5. There is also an alternate option to the above step. Instead of forwarding ModelAndView object from Controller, we can directly return data from Controller using @ResponseBody annotation . We can find more information on using ContentNegotiatingResolver or ResponseBody annotation to return response .

Description of the Project:(SpringMVC-RESTful services)
1.Note that in the published code,we have named Spring Dispatcher servlet class as "rest" and the url pattern is given as "/*" which means any uri with the root of this web application will call DispatcherServlet.  DispatcherServlet will look for configuration files following this naming convention - [servlet-name]-servlet.xml. In this example, I have named dispatcher servlet class as "rest" and hence it will look for file named 'rest-servlet.xml'.
With ComponentScan tag, Spring auto scans all elements in the provided base package and all its child packages for Controller servlet. Also, we have used <mvc:annotation-driven> tag instead of ViewResolver, with which we can directly send response data from the controller
2.Now proceed with writing the actual business logic. Our aim is to serve data from database in json format based on the request received. Create a table in MySql server using the following query,
CREATE TABLE tblUser(
2	  `userid` int(11) NOT NULL AUTO_INCREMENT,
3	  `firstname` varchar(45) DEFAULT NULL,
4	  `lastname` varchar(45) DEFAULT NULL,
5	  `email` varchar(100) DEFAULT NULL,
6	  PRIMARY KEY (`userid`)
7	)
Insert some dummy values into it.
3. Create a java class and name it as "User.java". This is a model class that represents the data in the database
4. Create a utility class to handle connections to database. The connection string properties are kept in a configuration file called "db.properties" in the src folder.
Properties configuration file should have contents such as this,

driver=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/usedb
user=root
password=welcome
5. Create a service class that performs data access operations to get data from database,

6. Finally let us now write Spring Controller Class that maps the incoming request to appropriate methods and returns response in json format. We are going to use @RestController annotation which has @Controller and @Responsebody annotated within itself.
7.If we take a look at the SpringServiceController class we have mapped all requests to the relative path '/service/user' using @RequestMapping annotation. There are two methods, one that returns all user data(getAllUsers()) does not take any additional request parameter and the other that returns data specific to a user id takes userid as parameter (/service/user/userid).

8.Run the application in Tomcat Server and launch http://localhost:8080/SpringRESTServiceJson/service/user/ from browser. You must see all user information listed in json format.

To get specific user information, userid needs to be appended to the request url such as this, 'http://localhost:8080/ SpringRESTServiceJson /service/user1'


