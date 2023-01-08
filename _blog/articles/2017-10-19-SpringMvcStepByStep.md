---
layout:     post
title:      Spring MVC Tutorial for Beginners - in 25 Easy Steps
date:       2022-10-19 12:31:19
summary:    In this course, you will learn the basics developing a Basic Todo Management Application using Spring MVC with Login and Logout functionalities.
categories: SpringFramework
permalink:  /spring-mvc-tutorial-for-beginners
image: /images/spring-framework-category.png
---

Developing your first Spring MVC Web Application is fun.

In this course, you will learn the basics developing a Basic Todo Management Application using Spring MVC with Login and Logout functionalities.

You will build the website step by step - in more than 25 steps. This course would be a perfect first step as an introduction to Java Web Application Development.

You will be using Spring (Dependency Management), Spring MVC, Spring Security (Authentication and Authorization), BootStrap (Styling Pages), Maven (dependencies management), Eclipse (IDE) and Tomcat Web Server. We will help you set up each one of these.

## Course Link
[![Image](/images/Course-Spring-MVC-For-Beginners-Build-Java-Web-App-in-25-Steps.png "Spring MVC For Beginners : Build Java Web App in 25 Steps")](https://links.in28minutes.com/MISC-SPRING-MVC){:target="_blank"}



## You will learn

You will learn about
- DispatcherServlet
- Basic Todo Management Application with Login/Logout
- Model, Controllers, ViewResolver and Filters
- Forms - DataBinding, Validation
- Annotation based approach - @RequestParam, @PathVariable, @ModelAttribute, @SessionAttributes etc
- Bootstrap to style the page
- Spring Security
- Internationalization
- Exception Handling
- Basic REST Services

## Step Wise Details

- Step 11 : Configure application to use Spring MVC
- Step 12 : First Spring MVC Controller, @ResponseBody, @Controller
- Step 13 : Redirect to Login JSP - LoginController, @ResponseBody - and View Resolver
- Step 14 : DispatcherServlet and Log4j
- Step 15 : Show userid and password on the welcome page - ModelMap and @RequestParam
- Step 16 : LoginService and Remove all JEE Servlets based code
- Step 17 : Spring Auto-wiring and Dependency Management - @Autowired and @Service
- Step 18 : Create TodoController and list-todos view. Make TodoService a @Service and inject it.
- Step 19 : Web Application Architecture
- Step 20 : More about Spring Framework
- Step 21 : Session vs Model vs Request - @SessionAttributes
- Step 22 : New Todo and redirect to a Controller
- Step 23 : JSTL
- Step 24 : Bootstrap - using Webjars
- Step 25 : Let's delete a Todo
- Step 26 : Use Bootstrap to format and add HTML5 Validations
- Step 27 : Introduce JSR 349 Validations using Hibernate Validator First Command Bean.
- Step 28 : Let's update a Todo
- Step 29 : Let's add a Target Date for Todo - Use initBinder to Handle Date Fields
- Step 30 : Navigation bar and JSP Fragments
- Step 31 : Let's prepare for Spring Security
- Step 32 : Initial Setup for Spring Security
- Step 33 : Refactor and add Logout Functionality using Spring Security
- Step 34 : Exception Handling in Spring MVC - @ControllerAdvice, @ExceptionHandler and error-page in web dot xml
- Step 35 : Let's add Internationalization - i18n
- Step 36 : Basic Spring Rest Services - @RestController and jackson-databind
- Step 37 : More Rest Services - @PathVariable


## Step By Step Details

### Step 01 : Up and running with a Web Application in Tomcat

In this step, we will quickly setup a running web application.

> Tip : This is one of the few steps where you copy code in! We would want to ensure that you have a running web application without any mistakes.

You can run the project using Run as > Maven build > tomcat7:run.

You can copy code from 
- [Step 01 on Github Repository](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step01.md)

\pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.in28minutes</groupId>
	<artifactId>in28Minutes-first-webapp</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>war</packaging>
	<dependencies>
		<dependency>
			<groupId>javax</groupId>
			<artifactId>javaee-web-api</artifactId>
			<version>6.0</version>
			<scope>provided</scope>
		</dependency>
	</dependencies>
	<build>
		<pluginManagement>
			<plugins>
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-compiler-plugin</artifactId>
					<version>3.2</version>
					<configuration>
						<verbose>true</verbose>
						<source>1.7</source>
						<target>1.7</target>
						<showWarnings>true</showWarnings>
					</configuration>
				</plugin>
				<plugin>
					<groupId>org.apache.tomcat.maven</groupId>
					<artifactId>tomcat7-maven-plugin</artifactId>
					<version>2.2</version>
					<configuration>
						<path>/</path>
						<contextReloadable>true</contextReloadable>
					</configuration>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>
</project>
```

\src\main\java\webapp\LoginServlet.java

```java
package webapp;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/*
 * Browser sends Http Request to Web Server
 * 
 * Code in Web Server => Input:HttpRequest, Output: HttpResponse
 * JEE with Servlets
 * 
 * Web Server responds with Http Response
 */


@WebServlet(urlPatterns = "/login.do")
public class LoginServlet extends HttpServlet {

	@Override
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
		PrintWriter out = response.getWriter();
		out.println("<html>");
		out.println("<head>");
		out.println("<title>Yahoo!!!!!!!!</title>");
		out.println("</head>");
		out.println("<body>");
		out.println("My First Servlet");
		out.println("</body>");
		out.println("</html>");

	}

}
```
\src\main\webapp\WEB-INF\web.xml
```xml
<!-- webapp/WEB-INF/web.xml -->
<web-app xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
	version="3.0">

	<display-name>To do List</display-name>

	<welcome-file-list>
		<welcome-file>login.do</welcome-file>
	</welcome-file-list>

</web-app>
```
Java Platform, Enterprise Edition (Java EE) JEE6

Servlet is a Java programming language class used to extend the capabilities of servers  that host applications accessed by means of a request-response programming model.

Notes
- ```extends javax.servlet.http.HttpServlet``` - All servlets should extend HttpServlet class
- ```@WebServlet(urlPatterns = "/login.do")``` - Provide the url pattern to access the servlet
- ```doGet(HttpServletRequest request, HttpServletResponse response)``` - To handle the RequestMethod GET we need to implement doGet method.

Configuring welcome-file-list in web.xml will ensure that url http://localhost:8080/ redirects to http://localhost:8080/login.do

```xml
<welcome-file-list>
	<welcome-file>login.do</welcome-file>
</welcome-file-list>
```

### Step 02 : First JSP

[Complete code](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step02.md)

#### Notes
- Create LoginServlet again
- Redirect to a view - JSP

#### Code Snippets and Examples

Redirect to a view - JSP

\src\main\java\webapp\LoginServlet.java
```java
request
 .getRequestDispatcher("/WEB-INF/views/login.jsp")
 .forward(request, response);
```

\src\main\webapp\WEB-INF\views\login.jsp
```jsp
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
My First JSP!!!
</body>
</html>
```



### Step 03 : Adding a Get Parameter name

[Complete code](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step03.md)

#### Notes
- Passing a Request Parameter Name

#### Code Snippets and Examples

We read the request parameter and set it as a request attribute. Request attributes can be accessed from the view (jsp).

\src\main\java\webapp\LoginServlet.java

```java
request.setAttribute("name", 
		request.getParameter("name"));
```

\src\main\webapp\WEB-INF\views\login.jsp
```
My First JSP!!! My name is ${name}
```

### Step 04 : Adding another Get Parameter Password

[Complete code](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step04.md)

#### Code Snippets and Examples

\src\main\java\webapp\LoginServlet.java
```
request.setAttribute("password",
                  request.getParameter("password"));
```

\src\main\webapp\WEB-INF\views\login.jsp
```
My First JSP!!! My name is ${name} and password is ${password}
```

### Step 05 : Let's add a form

[Complete code](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step05.md)

#### Code Snippets and Examples

\src\main\java\webapp\LoginServlet.java
```
@Override
protected void doGet(HttpServletRequest request, HttpServletResponse response)
		throws IOException, ServletException {
	request
		.getRequestDispatcher("/WEB-INF/views/login.jsp")
		.forward(request, response);
}
```

\src\main\webapp\WEB-INF\views\login.jsp
```jsp
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
	<form action="/login.do" method="POST">
		Name : <input type="text" /> <input type="submit" />
	</form>
</body>
</html>
```

\src\main\webapp\WEB-INF\views\welcome.jsp
```
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
Welcome ${name}
</body>
</html>
```

### Step 06 : New Form and doPost

[Complete code](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step06.md)

\src\main\java\webapp\LoginServlet.java
```
@Override
protected void doPost(HttpServletRequest request, HttpServletResponse response)
		throws IOException, ServletException {
	request.setAttribute("name", request.getParameter("name"));
	request.getRequestDispatcher("/WEB-INF/views/welcome.jsp").forward(request, response);
}
```

\src\main\webapp\WEB-INF\views\welcome.jsp
```
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
Welcome ${name}
</body>
</html>
```

### Step 07 : Adding Password and Validation of User Id

[Complete code](https://github.com/in28minutes/JavaWebApplicationStepByStep/blob/master/Step07.md)

#### Code Snippets and Examples

\src\main\java\webapp\LoginService.java
```
public class LoginService {
	public boolean validateUser(String user, String password) {
		return user.equalsIgnoreCase("in28Minutes") && password.equals("dummy");
	}

}
```

\src\main\java\webapp\LoginServlet.java
```
@Override
protected void doPost(HttpServletRequest request, HttpServletResponse response)
		throws IOException, ServletException {
	String name = request.getParameter("name");
	String password = request.getParameter("password");

	boolean isValidUser = service.validateUser(name, password);

	if (isValidUser) {
		request.setAttribute("name", name);
		request.getRequestDispatcher("/WEB-INF/views/welcome.jsp")
				.forward(request, response);
	} else {
		request.setAttribute("errorMessage", "Invalid Credentials!!");
		request.getRequestDispatcher("/WEB-INF/views/login.jsp")
				.forward(request, response);
	}
}
```

\src\main\webapp\WEB-INF\views\login.jsp
```
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
	<p><font color="red">${errorMessage}</font></p>
	<form action="/login.do" method="POST">
		Name : <input name="name" type="text" /> Password : <input name="password" type="password" /> <input type="submit" />
	</form>
</body>
</html>
```


###  Step 11 : Configure application to use Spring MVC

#### What we will do

Before we start with the Flows, we need to configure application to use Spring MVC
- Lets do a little bit of Refactoring. Mini Step 1: Rename package webapp to com.in28minutes.jee
- We need Spring MVC Framework and its dependencies. Mini Step 2 : Add required jars to the project
- Spring MVC uses Front Controller Pattern -> Dispatcher Servlet. Mini Step 3 : Add Dispatcher Servlet to web.xml
- DispatcherServlet needs an Spring Application Context to launch. We will create an xml (/WEB-INF/todo-servlet.xml). Mini Step 4: Add Spring Context

#### Useful Snippets
pom.xml
```
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>4.2.2.RELEASE</version>
		</dependency>
```
web.xml
```
	    <servlet>
	        <servlet-name>dispatcher</servlet-name>
	        <servlet-class>
	            org.springframework.web.servlet.DispatcherServlet
	        </servlet-class>
	        <init-param>
	            <param-name>contextConfigLocation</param-name>
	            <param-value>/WEB-INF/todo-servlet.xml</param-value>
	        </init-param>
	        <load-on-startup>1</load-on-startup>
	    </servlet>
	
	    <servlet-mapping>
	        <servlet-name>dispatcher</servlet-name>
	        <url-pattern>/spring-mvc/*</url-pattern>
	    </servlet-mapping>
```
todo-servlet.xml
```
	<beans xmlns="http://www.springframework.org/schema/beans"
	    xmlns:context="http://www.springframework.org/schema/context"
	    xmlns:mvc="http://www.springframework.org/schema/mvc"
	    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
	    http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd
	    http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
	
	    <context:component-scan base-package="com.in28minutes" />
	
	    <mvc:annotation-driven />
	    
	</beans>

```


#### Flows:
- Flow 1. Login Servlet -> GET -> login.jsp
- Flow 2. Login Servlet -> POST (Success) -> welcome.jsp
- Flow 3. Login Servlet -> POST (Failure) -> login.jsp (with error message)

#### Files List
### \\src\main\webapp\WEB-INF\views\login.jsp Deleted
### \pom.xml Deleted
### \src\main\java\webapp\LoginService.java Deleted
### \src\main\java\webapp\LoginServlet.java Deleted
### \src\main\webapp\WEB-INF\views\welcome.jsp Deleted
### \src\main\webapp\WEB-INF\web.xml Deleted


##### /pom.xml New
```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.in28minutes</groupId>
	<artifactId>in28Minutes-springmvc</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>war</packaging>

	<dependencies>
		<dependency>
			<groupId>javax</groupId>
			<artifactId>javaee-web-api</artifactId>
			<version>6.0</version>
			<scope>provided</scope>
		</dependency>

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>4.2.2.RELEASE</version>
		</dependency>
	</dependencies>

	<build>
		<pluginManagement>
			<plugins>
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-compiler-plugin</artifactId>
					<version>3.2</version>
					<configuration>
						<verbose>true</verbose>
						<source>1.8</source>
						<target>1.8</target>
						<showWarnings>true</showWarnings>
					</configuration>
				</plugin>
				<plugin>
					<groupId>org.apache.tomcat.maven</groupId>
					<artifactId>tomcat7-maven-plugin</artifactId>
					<version>2.2</version>
					<configuration>
						<path>/</path>
						<contextReloadable>true</contextReloadable>
					</configuration>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>
</project>
```
##### /src/main/java/com/in28minutes/jee/LoginService.java New
```
package com.in28minutes.jee;

public class LoginService {
	public boolean validateUser(String user, String password) {
		return user.equalsIgnoreCase("in28Minutes") && password.equals("dummy");
	}

}
```
##### /src/main/java/com/in28minutes/jee/LoginServlet.java New
```
package com.in28minutes.jee;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet(urlPatterns = "/login.do")
public class LoginServlet extends HttpServlet {

	private LoginService service = new LoginService();

	@Override
	protected void doGet(HttpServletRequest request,
			HttpServletResponse response) throws IOException, ServletException {
		request.getRequestDispatcher("/WEB-INF/views/login.jsp").forward(
				request, response);
	}

	@Override
	protected void doPost(HttpServletRequest request,
			HttpServletResponse response) throws IOException, ServletException {
		String name = request.getParameter("name");
		String password = request.getParameter("password");

		boolean isValidUser = service.validateUser(name, password);

		if (isValidUser) {
			request.setAttribute("name", name);
			request.getRequestDispatcher("/WEB-INF/views/welcome.jsp").forward(
					request, response);
		} else {
			request.setAttribute("errorMessage", "Invalid Credentials!!");
			request.getRequestDispatcher("/WEB-INF/views/login.jsp").forward(
					request, response);
		}
	}

}
```
##### /src/main/webapp/WEB-INF/todo-servlet.xml New
```
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:mvc="http://www.springframework.org/schema/mvc"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
    http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd
    http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">

    <context:component-scan base-package="com.in28minutes" />

    <mvc:annotation-driven />
    
</beans>
```
##### /src/main/webapp/WEB-INF/views/login.jsp New
```
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
    <p><font color="red">${errorMessage}</font></p>
    <form action="/login.do" method="POST">
        Name : <input name="name" type="text" /> Password : <input name="password" type="password" /> <input type="submit" />
    </form>
</body>
</html>
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp New
```
<html>
<head>
<title>Yahoo!!</title>
</head>
<body>
Welcome ${name}
</body>
</html>
```
##### /src/main/webapp/WEB-INF/web.xml New
```
<web-app xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
    version="3.0">

    <display-name>To do List</display-name>

    <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>
            org.springframework.web.servlet.DispatcherServlet
        </servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/todo-servlet.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>dispatcher</servlet-name>
        <url-pattern>/spring-mvc/*</url-pattern>
    </servlet-mapping>
</web-app>
```

###  Step 12 : First Spring MVC Controller, @ResponseBody, @Controller

#First Spring MVC Controller
- @RequestMapping(value = "/login", method = RequestMethod.GET)
- http://localhost:8080/spring-mvc/login
- web.xml - <url-pattern>/spring-mvc/*</url-pattern>
- Why @ResponseBody?
- Importance of RequestMapping method
- Can I have multiple urls rendered from Same Controller?

#Snippets
```
package com.in28minutes.springmvc;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class LoginController {

	@RequestMapping(value = "/login")
	@ResponseBody
	public String sayHello() {
		return "Hello World dummy";
	}
}

```

###  Step 13 : Redirect to Login JSP - LoginController, @ResponseBody - and View Resolver

##### /src/main/java/com/in28minutes/springmvc/login/LoginController.java New
```
package com.in28minutes.springmvc.login;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

@Controller
public class LoginController {
	@RequestMapping(value = "/login", method = RequestMethod.GET)
	public String showLoginPage() {
		return "login";
	}
}
```
##### /src/main/webapp/WEB-INF/todo-servlet.xml Modified
New Lines
```
    <bean
        class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix">
            <value>/WEB-INF/views/</value>
        </property>
        <property name="suffix">
            <value>.jsp</value>
        </property>
    </bean>
```

#### Redirect to Login JSP
- View Resolver in todo-servlet.xml
- Update LoginController
- Remove @ResponseBody
- More about View Resolver

#### Snippets

```
  <bean
        class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix">
            <value>/WEB-INF/views/</value>
        </property>
        <property name="suffix">
            <value>.jsp</value>
        </property>
    </bean>
```

###  Step 14 : DispatcherServlet and Log4j

##### /pom.xml Modified
New Lines
```
<dependency>
	<groupId>log4j</groupId>
	<artifactId>log4j</artifactId>
	<version>1.2.17</version>
</dependency>
```

##### /src/main/resources/log4j.properties New
```
log4j.rootLogger=TRACE, Appender1, Appender2
 
log4j.appender.Appender1=org.apache.log4j.ConsoleAppender
log4j.appender.Appender1.layout=org.apache.log4j.PatternLayout
log4j.appender.Appender1.layout.ConversionPattern=%-7p %d [%t] %c %x - %m%n
 
```
##### /src/main/webapp/WEB-INF/views/login.jsp Modified
New Lines
```
    <form action="/spring-mvc/login" method="POST">
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp Modified
New Lines
```
Welcome ${name}. 
```
#### What we want to do:
- Understand importance of DispatcherServlet.
- Add Logging Framework Log4j to understand the flow much more. 

#### Spring MVC Request Flow
- DispatcherServlet receives HTTP Request. 
- DispatcherServlet identifies the right Controller based on the URL.
- Controller executes Business Logic.
- Controller returns a) Model b) View Name Back to DispatcherServlet.
- DispatcherServlet identifies the correct view (ViewResolver).
- DispatcherServlet makes the model available to view and executes it.
- DispatcherServlet returns HTTP Response Back.
- Flow : http://docs.spring.io/spring-framework/docs/2.0.8/reference/images/mvc.png

###  Step 15 : Show userid and password on the welcome page - ModelMap and @RequestParam

##### /src/main/java/com/in28minutes/springmvc/login/LoginController.java Modified
New Lines
```java

	@RequestMapping(value = "/login", method = RequestMethod.POST)
	public String handleUserLogin(ModelMap model, @RequestParam String name,
			@RequestParam String password) {
		model.put("name", name);
		model.put("password", password);
		return "welcome";
	}
}
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp Modified
New Lines
```
Welcome ${name}. You entered ${password}
```
#### What we will do:
- Show userid and password on the welcome page.
- We will not use Spring Security for now.
- ModelMap model
- @RequestParam String name

###  Step 16 : LoginService and Remove all JEE Servlets based code

##### /src/main/java/com/in28minutes/jee/LoginService.java Deleted
##### /src/main/java/com/in28minutes/jee/LoginServlet.java Deleted

##### /src/main/java/com/in28minutes/springmvc/login/LoginController.java Deleted

##### /src/main/java/com/in28minutes/login/LoginController.java New
```
package com.in28minutes.login;

import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;

import com.in28minutes.login.LoginService;

@Controller
public class LoginController {

	private LoginService loginService = new LoginService();

	@RequestMapping(value = "/login", method = RequestMethod.GET)
	public String showLoginPage() {
		return "login";
	}

	@RequestMapping(value = "/login", method = RequestMethod.POST)
	public String handleUserLogin(ModelMap model, @RequestParam String name,
			@RequestParam String password) {

		if (!loginService.validateUser(name, password)) {
			model.put("errorMessage", "Invalid Credentials");
			return "login";
		}

		model.put("name", name);
		return "welcome";
	}
}
```

##### /src/main/java/com/in28minutes/login/LoginService.java New
```
package com.in28minutes.login;

public class LoginService {
	public boolean validateUser(String user, String password) {
		return user.equalsIgnoreCase("in28Minutes") && password.equals("dummy");
	}

}
```

##### /src/main/webapp/WEB-INF/views/login.jsp Modified
New Lines
```
    <form action="/login" method="POST">
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp Modified
New Lines
```
Welcome ${name}. You are now authenticated.
```

##### /src/main/webapp/WEB-INF/web.xml Modified
New Lines
```
        <url-pattern>/</url-pattern>
```
#### What we will do:
- Use LoginService to validate userid and password.
- Remove all the old controller code and lets use only Spring MVC here on. 
- For now : We are not using Spring Autowiring for LoginService.
- Change URL to http://localhost:8080/login

###  Step 17 : Spring Auto-wiring and Dependency Management - @Autowired and @Service

##### /src/main/java/com/in28minutes/login/LoginController.java Modified
New Lines
```
import org.springframework.beans.factory.annotation.Autowired;
	@Autowired
	private LoginService loginService;
```
##### /src/main/java/com/in28minutes/login/LoginService.java Modified
New Lines
```
import org.springframework.stereotype.Service;
@Service
public class LoginService {
```
#### What we will do:
- Learn about Spring Auto-wiring and Dependency Management.
- Use Auto-wiring to wire LoginService.
- @Autowired, @Service

###  Step 18 : Create TodoController and list-todos view. Make TodoService a @Service and inject it.

##### /src/main/java/com/in28minutes/model/Todo.java New
```
package com.in28minutes.model;

import java.util.Date;

public class Todo {
	private int id;
	private String user;
	private String desc;
	private Date targetDate;
	private boolean isDone;

	public Todo(int id, String user, String desc, Date targetDate, boolean isDone) {
		super();
		this.id = id;
		this.user = user;
		this.desc = desc;
		this.targetDate = targetDate;
		this.isDone = isDone;
	}

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getUser() {
		return user;
	}

	public void setUser(String user) {
		this.user = user;
	}

	public String getDesc() {
		return desc;
	}

	public void setDesc(String desc) {
		this.desc = desc;
	}

	public Date getTargetDate() {
		return targetDate;
	}

	public void setTargetDate(Date targetDate) {
		this.targetDate = targetDate;
	}

	public boolean isDone() {
		return isDone;
	}

	public void setDone(boolean isDone) {
		this.isDone = isDone;
	}

	@Override
	public int hashCode() {
		final int prime = 31;
		int result = 1;
		result = prime * result + id;
		return result;
	}

	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Todo other = (Todo) obj;
		if (id != other.id)
			return false;
		return true;
	}

	@Override
	public String toString() {
		return String.format(
				"Todo [id=%s, user=%s, desc=%s, targetDate=%s, isDone=%s]", id,
				user, desc, targetDate, isDone);
	}

}
```
##### /src/main/java/com/in28minutes/todo/TodoController.java New
```
package com.in28minutes.todo;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

import com.in28minutes.todo.service.TodoService;

@Controller
public class TodoController {

	@Autowired
	private TodoService service;

	@RequestMapping(value = "/list-todos", method = RequestMethod.GET)
	public String showLoginPage(ModelMap model) {
		model.addAttribute("todos", service.retrieveTodos("in28Minutes"));
		return "list-todos";
	}
}
```
##### /src/main/java/com/in28minutes/todo/service/TodoService.java New
```
package com.in28minutes.todo.service;

import java.util.ArrayList;
import java.util.Date;
import java.util.Iterator;
import java.util.List;

import org.springframework.stereotype.Service;

import com.in28minutes.model.Todo;

@Service
public class TodoService {
	private static List<Todo> todos = new ArrayList<Todo>();
	private static int todoCount = 3;

	static {
		todos.add(new Todo(1, "in28Minutes", "Learn Spring MVC", new Date(),
				false));
		todos.add(new Todo(2, "in28Minutes", "Learn Struts", new Date(), false));
		todos.add(new Todo(3, "in28Minutes", "Learn Hibernate", new Date(),
				false));
	}

	public List<Todo> retrieveTodos(String user) {
		List<Todo> filteredTodos = new ArrayList<Todo>();
		for (Todo todo : todos) {
			if (todo.getUser().equals(user))
				filteredTodos.add(todo);
		}
		return filteredTodos;
	}

	public void addTodo(String name, String desc, Date targetDate, boolean isDone) {
		todos.add(new Todo(++todoCount, name, desc, targetDate, isDone));
	}

	public void deleteTodo(int id) {
		Iterator<Todo> iterator = todos.iterator();
		while (iterator.hasNext()) {
			Todo todo = iterator.next();
			if (todo.getId() == id) {
				iterator.remove();
			}
		}
	}
}
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp New
```
<html>
<head>
<title>Todos for ${name}</title>
</head>
<body>
<H1>Your Todos</H1>
 ${todos}
</body>
</html>
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp Modified
New Lines
```
Welcome ${name}. You are now authenticated. <a href="/list-todos">Click here</a> to start maintaining your todo's.
```
#### What we will do:
- Create TodoController and list-todos.jsp
- Make TodoService a @Service and inject it

### Pending for Next Step New
- ${name} is not available in list-todos.jsp
- in28Minutes is hardcoded in TodoController

###  Step 19 : Web Application Architecture

#### What we will do:
- Lets discuss about Architecture of web applications

###  Step 20 : More about Spring Framework

#### What we will do:
- Lets discuss about Spring

###  Step 21 : Session vs Model vs Request - @SessionAttributes

##### /src/main/java/com/in28minutes/login/LoginController.java Modified
New Lines
```
import org.springframework.web.bind.annotation.SessionAttributes;
@SessionAttributes("name")
public class LoginController {
```
##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```
@Controller
@SessionAttributes("name")
public class TodoController {

	@Autowired
	private TodoService service;

	@RequestMapping(value = "/list-todos", method = RequestMethod.GET)
	public String showLoginPage(ModelMap model, String name) {
		String user = (String) model.get("name");
		model.addAttribute("todos", service.retrieveTodos(user));
		return "list-todos";
	}
}
```
#### What we will do:
- Session vs Model vs Request.
- Be cautious about what you use Session for.
- @SessionAttributes("name") and how it works?
- Why use Model?  "adding elements directly to the HttpServletRequest (as request attributes) would seem to serve the same purpose.  The reason to do this is obvious when taking a look at one of the requirements we have set for the MVC framework:  It should be as view-agnostic as possible, which means we’d like to be able to incorporate view technologies not bound to the HttpServletRequest as well." - Rod Johnson et. al’s book Professional Java Development with the Spring Framework 
- Spring documentation states that the @SessionAttributes annotation “list the names of model attributes which should be transparently stored in the session or some conversational storage.” 

###  Step 22 : New Todo and redirect to a Controller

##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```
	@RequestMapping(value = "/list-todos", method = RequestMethod.GET)
	public String showTodosList(ModelMap model) {
		String user = (String) model.get("name");
		model.addAttribute("todos", service.retrieveTodos(user));
		return "list-todos";
	}

	@RequestMapping(value = "/add-todo", method = RequestMethod.GET)
	public String showTodoPage() {
		return "todo";
	}

	@RequestMapping(value = "/add-todo", method = RequestMethod.POST)
	public String addTodo(ModelMap model, @RequestParam String desc) {
		service.addTodo((String) model.get("name"), desc, new Date(), false);
		model.clear();// to prevent request parameter "name" to be passed
		return "redirect:/list-todos";
	}
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
 <a class="button" href="/add-todo">Add</a>
```
##### /src/main/webapp/WEB-INF/views/login.jsp Modified
New Lines
```
<title>Login Page</title>
```
##### /src/main/webapp/WEB-INF/views/todo.jsp New
```
<html>
<head>
<title>Login Page</title>
</head>
<body>
    <form action="/add-todo" method="POST">
        Description : <input name="desc" type="text" /> <input type="submit" value="add" />
    </form>
</body>
</html>
```
#### What we will do:
- Add Facility to add New Todo
- todo.jsp
- Importance of redirect:/list-todos
- Importance of model.clear();

###  Step 23 : JSTL

##### /pom.xml Modified
New Lines
```
<dependency>
	<groupId>javax.servlet</groupId>
	<artifactId>jstl</artifactId>
	<version>1.2</version>
</dependency>
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
	<H1>Your Todos</H1>
	<div>
		<table>
			<caption>Your Todos are</caption>

			<thead>
				<tr>
					<th>Description</th>
					<th>Date</th>
					<th>Completed</th>
				</tr>
			</thead>

			<tbody>
				<c:forEach items="${todos}" var="todo">
					<tr>
						<td>${todo.desc}</td>
						<td>${todo.targetDate}</td>
						<td>${todo.done}</td>
					</tr>
				</c:forEach>
			</tbody>
		</table>
	</div>

	<a class="button" href="/add-todo">Add</a>
```

#### What we will do:
- Display Todos in a table using JSTL Tags
- <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
- Add Dependency for jstl

###  Step 24 : Bootstrap - using Webjars

##### /pom.xml Modified
New Lines
```
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>bootstrap</artifactId>
            <version>3.3.6</version>
        </dependency>
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>jquery</artifactId>
            <version>1.9.1</version>
        </dependency>
        
```
##### /src/main/webapp/WEB-INF/todo-servlet.xml Modified
New Lines
```
    <mvc:resources mapping="/webjars/**" location="/webjars/"/>
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
<link href="webjars/bootstrap/3.3.6/css/bootstrap.min.css"
    rel="stylesheet">

<div class="container">

	<table class="table table-striped">

<a class="button" href="/add-todo">Add</a>

<script src="webjars/jquery/1.9.1/jquery.min.js"></script>
<script src="webjars/bootstrap/3.3.6/js/bootstrap.min.js"></script>
```
#### What we will do:
- Add bootstrap to give basic formatting to the page : We use bootstrap classes container,table and table-striped.
- We will use webjars

#### Useful Snippets
```     
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>bootstrap</artifactId>
            <version>3.3.6</version>
        </dependency>
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>jquery</artifactId>
            <version>1.9.1</version>
        </dependency>
        
  		<mvc:resources mapping="/webjars/**" location="/webjars/"/>
  
		<script src="webjars/jquery/1.9.1/jquery.min.js"></script>
	    <script src="webjars/bootstrap/3.3.6/js/bootstrap.min.js"></script>
		<link href="webjars/bootstrap/3.3.6/css/bootstrap.min.css"
	    		rel="stylesheet">

```

###  Step 25 : Let's delete a Todo

##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```

	@RequestMapping(value = "/delete-todo", method = RequestMethod.GET)
	public String deleteTodo(@RequestParam int id) {
		service.deleteTodo(id);

		return "redirect:/list-todos";
	}

```
##### /src/main/java/com/in28minutes/todo/service/TodoService.java Modified
New Lines
```
	public void addTodo(String name, String desc, Date targetDate,
			boolean isDone) {
		todos.add(new Todo(++todoCount, name, desc, targetDate, isDone));
	}
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
<th></th>
<td>
	<a type="button" class="btn btn-warning" 
		href="/delete-todo?id=${todo.id}">Delete</a>
</td>
<a type="button" class="btn btn-success" href="/add-todo">Add</a>
```

#### What we will do:
- Add functionality to delete a todo

#### Useful Snippets
```     
	<a type="button" class="btn btn-warning" 
		href="/delete-todo?id=${todo.id}">Delete</a>
```

###  Step 26 : Use Bootstrap to format and add HTML5 Validations

##### /src/main/webapp/WEB-INF/views/todo.jsp Modified
New Lines
```
<title>Your Todo</title>
<link href="webjars/bootstrap/3.3.6/css/bootstrap.min.css"
	rel="stylesheet">

	<div class="container">
		<form action="/add-todo" method="post">
			<fieldset class="form-group">
				<label>Description</label>
				<input name="desc" type="text" class="form-control" required="required"/>
			</fieldset>
			<button type="submit" class="btn btn-success">Add</button>
		</form>
	</div>

	<script src="webjars/jquery/1.9.1/jquery.min.js"></script>
	<script src="webjars/bootstrap/3.3.6/js/bootstrap.min.js"></script>

```
#### What we will do:
In this short step:
- Format Add Todo Page
- Add Html5 Form Validations

#### Useful Snippets
```     
	<fieldset class="form-group">
		<label>Description</label>
		<input name="desc" type="text" class="form-control" required="required"/>
	</fieldset>

```

###  Step 27 : Introduce JSR 349 Validations using Hibernate Validator First Command Bean.

##### /pom.xml Modified
New Lines
```
<dependency>
	<groupId>org.hibernate</groupId>
	<artifactId>hibernate-validator</artifactId>
	<version>5.0.2.Final</version>
</dependency>
		
```
##### /src/main/java/com/in28minutes/model/Todo.java Modified
New Lines
```
	@Size(min = 10, message = "Enter atleast 10 Characters.")
	private String desc;
```
##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```
	@RequestMapping(value = "/add-todo", method = RequestMethod.GET)
	public String showAddTodoPage(ModelMap model) {
		model.addAttribute("todo", new Todo());
		return "todo";
	}

	@RequestMapping(value = "/add-todo", method = RequestMethod.POST)
	public String addTodo(ModelMap model, @Valid Todo todo, BindingResult result) {

		if (result.hasErrors())
			return "todo";

		service.addTodo((String) model.get("name"), todo.getDesc(), new Date(),
				false);
		model.clear();// to prevent request parameter "name" to be passed
		return "redirect:/list-todos";
	}

```
##### /src/main/webapp/WEB-INF/views/todo.jsp Modified
New Lines
```
<%@taglib uri="http://www.springframework.org/tags/form" prefix="form"%>
		<form:form method="post" commandName="todo">
				<form:label path="desc">Description</form:label>
				<form:input path="desc" type="text" class="form-control"
					required="required"/>
				<form:errors path="desc" cssClass="text-warning" />
		</form:form>
```
#### What we will do:
- Lets use a command bean for Todo
- Add Validations
- The JSR 303 and JSR 349 defines specification for the Bean Validation API (version 1.0 and 1.1, respectively), and Hibernate Validator is the reference implementation.

#### Useful Snippets
```     
		<%@taglib uri="http://www.springframework.org/tags/form" prefix="form"%>

		<form:form action="/add-todo" method="post" commandName="todo">
			<fieldset class="form-group">
				<form:label path="desc">Description</form:label>
				<form:input path="desc" type="text" class="form-control" required="required"/>
			</fieldset>
		</form:form>
		
		<dependency>
    			<groupId>org.hibernate</groupId>
    			<artifactId>hibernate-validator</artifactId>
    			<version>5.0.2.Final</version>
 		</dependency>

		@Size(min = 10, message = "Enter atleast 10 Characters.")
		
		@Valid Todo todo, BindingResult result

		if (result.hasErrors())
			return "todo";
		
		<form:errors path="desc" cssClass="text-warning" />
		
```
###  Step 28 : Let's update a Todo

##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```

	@RequestMapping(value = "/update-todo", method = RequestMethod.GET)
	public String showUpdateTodoPage(ModelMap model, @RequestParam int id) {
		model.addAttribute("todo", service.retrieveTodo(id));
		return "todo";
	}

	@RequestMapping(value = "/update-todo", method = RequestMethod.POST)
	public String updateTodo(ModelMap model, @Valid Todo todo,
			BindingResult result) {
		if (result.hasErrors())
			return "todo";

		todo.setUser("in28Minutes"); //TODO:Remove Hardcoding Later
		service.updateTodo(todo);

		model.clear();// to prevent request parameter "name" to be passed
		return "redirect:/list-todos";
	}

```
##### /src/main/java/com/in28minutes/todo/service/TodoService.java Modified
New Lines
```

	public Todo retrieveTodo(int id) {
		for (Todo todo : todos) {
			if (todo.getId() == id)
				return todo;
		}
		return null;
	}

	public void updateTodo(Todo todo) {
		todos.remove(todo);
		todos.add(todo);
	}

```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
	<a type="button" class="btn btn-primary" 
		href="/update-todo?id=${todo.id}">Edit</a>
```
##### /src/main/webapp/WEB-INF/views/todo.jsp Modified
New Lines
```
	<form:hidden path="id"/>
	<button type="submit" class="btn btn-success">Submit</button>
```
#### What we will do:
- Add Update Functionality
- Lets Use the Same JSP as earlier.

#### Useful Snippets
```
	public Todo retrieveTodo(int id) {
		for (Todo todo : todos) {
			if (todo.getId() == id)
				return todo;
		}
		return null;
	}

	public void updateTodo(Todo todo) {
		todos.remove(todo);
		todos.add(todo);
	}
   
   todo.setUser("in28Minutes"); //TODO:Remove Hardcoding Later
   service.updateTodo(todo);
   
   <form:hidden path="id"/>  
```

###  Step 29 : Let's add a Target Date for Todo - Use initBinder to Handle Date Fields

##### /pom.xml Modified
New Lines
```
<dependency>
	<groupId>org.webjars</groupId>
	<artifactId>bootstrap-datepicker</artifactId>
	<version>1.0.1</version>
</dependency>
```
##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```
	@InitBinder
	protected void initBinder(WebDataBinder binder) {
		SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
		binder.registerCustomEditor(Date.class, new CustomDateEditor(
				dateFormat, false));
	}

```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt"%>
	rel="stylesheet">

<td><fmt:formatDate pattern="dd/MM/yyyy"
		value="${todo.targetDate}" /></td>
<td><a type="button" class="btn btn-primary"
	href="/update-todo?id=${todo.id}">Edit</a> <a type="button"
	class="btn btn-warning" href="/delete-todo?id=${todo.id}">Delete</a>

<script src="webjars/bootstrap/3.3.6/js/bootstrap.min.js"></script>
```

##### /src/main/webapp/WEB-INF/views/todo.jsp Modified
New Lines
```
    <div class="container">
        <form:form method="post" commandName="todo">
            <form:hidden path="id" />
            <fieldset class="form-group">
                <form:label path="desc">Description</form:label>
                <form:input path="desc" type="text" class="form-control"
                    required="required" />
                <form:errors path="desc" cssClass="text-warning" />
            </fieldset>
            <fieldset class="form-group">
                <form:label path="targetDate">Target Date</form:label>
                <form:input path="targetDate" type="text" class="form-control"
                    required="required" />
                <form:errors path="targetDate" cssClass="text-warning" />
            </fieldset>
            <button type="submit" class="btn btn-success">Submit</button>
        </form:form>
    </div>
    <script src="webjars/jquery/1.9.1/jquery.min.js"></script>
    <script src="webjars/bootstrap/3.3.6/js/bootstrap.min.js"></script>
    <script
        src="webjars/bootstrap-datepicker/1.0.1/js/bootstrap-datepicker.js"></script>
    <script>
        $('#targetDate').datepicker({
            format : 'dd/mm/yyyy'
        });
    </script>
```
#### What we will do:
- Make real use of the Target Date Field
- initBinder method

#### Useful Snippets
```
	<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt"%>
	<fmt:formatDate pattern="dd/MM/yyyy"
									value="${todo.targetDate}" />
									
	
	@InitBinder
	protected void initBinder(WebDataBinder binder) {
		SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
		binder.registerCustomEditor(Date.class, new CustomDateEditor(
				dateFormat, false));
	}
	
	<dependency>
		<groupId>org.webjars</groupId>
		<artifactId>bootstrap-datepicker</artifactId>
		<version>1.0.1</version>
	</dependency>
	
	<script
		src="webjars/bootstrap-datepicker/1.0.1/js/bootstrap-datepicker.js"></script>

	<script>
		$('#targetDate').datepicker({
			format : 'dd/mm/yyyy'
		});
	</script>
		
```

###  Step 30 : Navigation bar and JSP Fragments

##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```
	@RequestMapping(value = "/add-todo", method = RequestMethod.POST)
	public String addTodo(ModelMap model, @Valid Todo todo, BindingResult result) {

		if (result.hasErrors())
			return "todo";

		service.addTodo((String) model.get("name"), todo.getDesc(),
				todo.getTargetDate(), false);
		model.clear();// to prevent request parameter "name" to be passed
		return "redirect:/list-todos";
	}
```
##### /src/main/webapp/WEB-INF/views/common/footer.jspf New
```

<script src="webjars/jquery/1.9.1/jquery.min.js"></script>
<script src="webjars/bootstrap/3.3.6/js/bootstrap.min.js"></script>
<script
	src="webjars/bootstrap-datepicker/1.0.1/js/bootstrap-datepicker.js"></script>

</body>
</html>
```
##### /src/main/webapp/WEB-INF/views/common/header.jspf New
```
<%@taglib uri="http://www.springframework.org/tags/form" prefix="form"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt"%>
<html>
<head>
<title>Todos Application</title>
<link href="webjars/bootstrap/3.3.6/css/bootstrap.min.css"
	rel="stylesheet">
</head>

<body>

```
##### /src/main/webapp/WEB-INF/views/common/navigation.jspf New
```
<nav role="navigation" class="navbar navbar-default">

	<div class="">
		<a href="http://www.in28minutes.com" class="navbar-brand">in28Minutes</a>
	</div>

	<div class="navbar-collapse">
		<ul class="nav navbar-nav">
			<li class="active"><a href="/login">Home</a></li>
			<li><a href="/list-todos">Todos</a></li>

		</ul>
	</div>

</nav>
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
<%@ include file="common/header.jspf"%>
<%@ include file="common/navigation.jspf"%>
<div class="container">
	<table class="table table-striped">
		<caption>Your Todos are</caption>
		<thead>
			<tr>
				<th>Description</th>
				<th>Date</th>
				<th>Completed</th>
				<th></th>
			</tr>
		</thead>
		<tbody>
			<c:forEach items="${todos}" var="todo">
					<td>${todo.desc}</td>
					<td><fmt:formatDate pattern="dd/MM/yyyy"
							value="${todo.targetDate}" /></td>
					<td>${todo.done}</td>
					<td><a type="button" class="btn btn-primary"
						href="/update-todo?id=${todo.id}">Edit</a> <a type="button"
						class="btn btn-warning" href="/delete-todo?id=${todo.id}">Delete</a>
					</td>
			</c:forEach>
		</tbody>
	</table>
	<div>
		<a type="button" class="btn btn-success" href="/add-todo">Add</a>
	</div>
</div>
<%@ include file="common/footer.jspf"%>
```
##### /src/main/webapp/WEB-INF/views/login.jsp Modified
New Lines
```
<%@ include file="common/header.jspf"%>
<%@ include file="common/navigation.jspf"%>
<div class="container">
	<p>
		<font color="red">${errorMessage}</font>
	</p>
	<form action="/login" method="POST">
		<fieldset class="form-group">
			<label>Name</label> <input name="name" type="text"
				class="form-control" />
		</fieldset>
		<fieldset class="form-group">
			<label>Password</label> <input name="password" type="password"
				class="form-control" />
		</fieldset>
		<button type="submit" class="btn btn-success">Submit</button>
	</form>

</div>

<%@ include file="common/footer.jspf"%>
```
##### /src/main/webapp/WEB-INF/views/todo.jsp Modified
New Lines
```
<%@ include file="common/header.jspf"%>
<%@ include file="common/navigation.jspf"%>
<div class="container">
	<form:form method="post" commandName="todo">
		<form:hidden path="id" />
		<fieldset class="form-group">
			<form:label path="desc">Description</form:label>
			<form:input path="desc" type="text" class="form-control"
				required="required" />
			<form:errors path="desc" cssClass="text-warning" />
		</fieldset>
		<fieldset class="form-group">
			<form:label path="targetDate">Target Date</form:label>
			<form:input path="targetDate" type="text" class="form-control"
				required="required" />
			<form:errors path="targetDate" cssClass="text-warning" />
		</fieldset>
		<button type="submit" class="btn btn-success">Submit</button>
	</form:form>
</div>
<%@ include file="common/footer.jspf"%>
<script>
	$('#targetDate').datepicker({
		format : 'dd/mm/yyyy'
	});
</script>
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp Modified
New Lines
```
<%@ include file="common/header.jspf"%>
<%@ include file="common/navigation.jspf"%>
<div class="container">
	Welcome ${name}. You are now authenticated.
</div>

<%@ include file="common/footer.jspf"%>
```
#### What we will do:
- Add a navigation bar
- Use JSP Fragments
- Exercise : Align the login & welcome pages.
- Exercise : Highlight the correct menu item.

#### Useful Snippets
```
<nav role="navigation" class="navbar navbar-default">
	<div class="">
		<a href="http://www.in28minutes.com" class="navbar-brand">in28Minutes</a>
	</div>
	<div class="navbar-collapse">
		<ul class="nav navbar-nav">
			<li class="active"><a href="/login">Home</a></li>
			<li><a href="/list-todos">Todos</a></li>

		</ul>
	</div>
</nav>
```

###  Step 31 : Let's prepare for Spring Security

##### /src/main/java/com/in28minutes/login/LoginController.java Modified
New Lines
```
	@RequestMapping(value = "/", method = RequestMethod.GET)
	public String showWelcomePage(ModelMap model) {
		model.put("name", "in28Minutes");
		return "welcome";
	}
```
##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```

	@RequestMapping(value = "/list-todos", method = RequestMethod.GET)
	public String showTodosList(ModelMap model) {
		String user = getLoggedInUserName(model);
		model.addAttribute("todos", service.retrieveTodos(user));
		return "list-todos";
	}

	@RequestMapping(value = "/add-todo", method = RequestMethod.POST)
	public String addTodo(ModelMap model, @Valid Todo todo, BindingResult result) {

		if (result.hasErrors())
			return "todo";

		service.addTodo(getLoggedInUserName(model), todo.getDesc(),
				todo.getTargetDate(), false);
		model.clear();// to prevent request parameter "name" to be passed
		return "redirect:/list-todos";
	}

	private String getLoggedInUserName(ModelMap model) {
		return (String) model.get("name");
	}

```
##### /src/main/webapp/WEB-INF/views/common/navigation.jspf Modified
New Lines
```
			<li class="active"><a href="/">Home</a></li>
```
##### /src/main/webapp/WEB-INF/views/login.jsp Deleted
#### What we will do:
- Prepare for Using Spring Security
- Remove All the Login Related Functionality
- Make Welcome the default page - with some hardcoding to start with.
- Refactor getLoggedInUserName
- Update Home Page Link in navigation

#### Useful Snippets
```
```

###  Step 32 : Initial Setup for Spring Security

##### /pom.xml Modified
New Lines
```
		<dependency>
			<groupId>org.springframework.security</groupId>
			<artifactId>spring-security-web</artifactId>
			<version>4.0.1.RELEASE</version>
  		</dependency>

       <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-config</artifactId>
            <version>4.0.1.RELEASE</version>
        </dependency>	
```
##### /src/main/java/com/in28minutes/security/SecurityConfiguration.java New
```
package com.in28minutes.security;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@Configuration
@EnableWebSecurity
public class SecurityConfiguration extends WebSecurityConfigurerAdapter {

	@Autowired
	public void configureGlobalSecurity(AuthenticationManagerBuilder auth)
			throws Exception {
		auth.inMemoryAuthentication().passwordEncoder(org.springframework.security.crypto.password.NoOpPasswordEncoder.getInstance()).withUser("in28Minutes").password("dummy")
				.roles("USER", "ADMIN");
	}

	@Override
	protected void configure(HttpSecurity http) throws Exception {
		http.authorizeRequests().antMatchers("/login").permitAll()
				.antMatchers("/", "/*todo*/**").access("hasRole('USER')").and()
				.formLogin();
	}
}
```
##### /src/main/webapp/WEB-INF/web.xml Modified
New Lines
```
    
   <filter>
    		<filter-name>springSecurityFilterChain</filter-name>
    		<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
   </filter>
 
   <filter-mapping>
   		<filter-name>springSecurityFilterChain</filter-name>
    		<url-pattern>/*</url-pattern>
   </filter-mapping> 
    
```
#### What we will do:
- Get Setup for Spring Security

###  Step 33 : Refactor and add Logout Functionality using Spring Security

##### /src/main/java/com/in28minutes/login/LoginController.java Deleted
##### /src/main/java/com/in28minutes/login/LoginService.java Deleted
##### /src/main/java/com/in28minutes/login/LogoutController.java New
```
package com.in28minutes.login;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.springframework.security.core.Authentication;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.web.authentication.logout.SecurityContextLogoutHandler;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

@Controller
public class LogoutController {

	@RequestMapping(value = "/logout", method = RequestMethod.GET)
	public String logout(HttpServletRequest request,
			HttpServletResponse response) {
		Authentication auth = SecurityContextHolder.getContext()
				.getAuthentication();
		if (auth != null) {
			new SecurityContextLogoutHandler().logout(request, response, auth);
		}
		return "redirect:/";
	}
}
```
##### /src/main/java/com/in28minutes/login/WelcomeController.java New
```
package com.in28minutes.login;

import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

@Controller
public class WelcomeController {

	@RequestMapping(value = "/", method = RequestMethod.GET)
	public String showWelcomePage(ModelMap model) {
		model.put("name", getLoggedInUserName());
		return "welcome";
	}

	private String getLoggedInUserName() {
		Object principal = SecurityContextHolder.getContext()
				.getAuthentication().getPrincipal();

		if (principal instanceof UserDetails)
			return ((UserDetails) principal).getUsername();

		return principal.toString();
	}

}
```
##### /src/main/java/com/in28minutes/todo/TodoController.java Modified
New Lines
```

	private String getLoggedInUserName() {
		Object principal = SecurityContextHolder.getContext()
				.getAuthentication().getPrincipal();

		if (principal instanceof UserDetails)
			return ((UserDetails) principal).getUsername();

		return principal.toString();
	}

```
##### /src/main/webapp/WEB-INF/views/common/navigation.jspf Modified
New Lines
```
		<ul class="nav navbar-nav navbar-right">
			<li><a href="/logout">Logout</a></li>
```
#### What we will do:
- Remove Hardcoding of User Name
- Remove LoginService
- Rename LoginController to WelcomeController
- Add Logout Functionality


###  Step 34 : Exception Handling in Spring MVC - @ControllerAdvice, @ExceptionHandler and error-page in web dot xml

##### /src/main/java/com/in28minutes/common/ExceptionController.java New
```
package com.in28minutes.common;

import javax.servlet.http.HttpServletRequest;

import org.apache.commons.logging.Log;
import org.apache.commons.logging.LogFactory;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;

@ControllerAdvice
@EnableWebMvc
public class ExceptionController {

	private Log logger = LogFactory.getLog(ExceptionController.class);

	@ExceptionHandler(value = Exception.class)
	public String handleError(HttpServletRequest req, Exception exception) {
		logger.error("Request: " + req.getRequestURL() + " raised " + exception);
		return "error";
	}
}
```
##### /src/main/java/com/in28minutes/common/LogoutController.java New
```
package com.in28minutes.common;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.springframework.security.core.Authentication;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.web.authentication.logout.SecurityContextLogoutHandler;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

@Controller
public class LogoutController {

	@RequestMapping(value = "/logout", method = RequestMethod.GET)
	public String logout(HttpServletRequest request,
			HttpServletResponse response) {
		Authentication auth = SecurityContextHolder.getContext()
				.getAuthentication();
		if (auth != null) {
			new SecurityContextLogoutHandler().logout(request, response, auth);
		}
		return "redirect:/";
	}
}
```
##### /src/main/java/com/in28minutes/login/LogoutController.java Deleted
##### /src/main/java/com/in28minutes/login/WelcomeController.java Deleted
##### /src/main/java/com/in28minutes/welcome/WelcomeController.java New
```
package com.in28minutes.welcome;

import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

@Controller
public class WelcomeController {

	@RequestMapping(value = "/", method = RequestMethod.GET)
	public String showWelcomePage(ModelMap model) {
		model.put("name", getLoggedInUserName());
		return "welcome";
	}

	private String getLoggedInUserName() {
		Object principal = SecurityContextHolder.getContext()
				.getAuthentication().getPrincipal();

		if (principal instanceof UserDetails)
			return ((UserDetails) principal).getUsername();

		return principal.toString();
	}

}
```
##### /src/main/webapp/WEB-INF/views/error.jsp New
```
<%@ include file="common/header.jspf"%>
<%@ include file="common/navigation.jspf"%>
<div class="container">
	Application has encountered an error. Please contact support on ...
</div>

<%@ include file="common/footer.jspf"%>
```
##### /src/main/webapp/WEB-INF/web.xml Modified
New Lines
```
   
    <error-page>
	    <location>/WEB-INF/views/error.jsp</location>
	</error-page>
```
#### What we will do:
- Basic Exception Handling
- Exception Handling is a cross cutting concern
- Do not handle exceptions in Controllers or Services, if you cannot add value to them.
- Bit of refactoring on the controllers
- @ControllerAdvice and Controller Specific Exception Handling
- Handling Errors thrown from Views

#### Useful Snippets
```
@ControllerAdvice
@EnableWebMvc
public class ExceptionController {

	private Log logger = LogFactory.getLog(ExceptionController.class);

	@ExceptionHandler(value = Exception.class)
	public String handleError(HttpServletRequest req, Exception exception) {
		logger.error("Request: " + req.getRequestURL() + " raised " + exception);
		return "error";
	}
}

<error-page>
	    <location>/WEB-INF/views/jsp/error.jsp</location>
</error-page>
```

###  Step 35 : Let's add Internationalization - i18n

##### /src/main/resources/messages_en.properties New
```
welcome.message=Welcome in English
todo.caption= Todo Caption in English
```
##### /src/main/resources/messages_fr.properties New
```
welcome.message=Welcome in French
todo.caption= Todo Caption in French
```
##### /src/main/webapp/WEB-INF/todo-servlet.xml Modified
New Lines
```
	<bean id="messageSource"
		class="org.springframework.context.support.ReloadableResourceBundleMessageSource">
		<property name="basename" value="classpath:messages" />
		<property name="defaultEncoding" value="UTF-8" />
	</bean>
	<bean id="localeResolver"
		class="org.springframework.web.servlet.i18n.SessionLocaleResolver">
		<property name="defaultLocale" value="en" />
	</bean>
	<mvc:interceptors>
		<bean id="localeChangeInterceptor"
			class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor">
			<property name="paramName" value="language" />
		</bean>
	</mvc:interceptors>
```
##### /src/main/webapp/WEB-INF/views/common/header.jspf Modified
New Lines
```
<%@taglib uri="http://www.springframework.org/tags" prefix="spring"%>
```
##### /src/main/webapp/WEB-INF/views/list-todos.jsp Modified
New Lines
```
		<caption><spring:message code="todo.caption" /></caption>
```
##### /src/main/webapp/WEB-INF/views/welcome.jsp Modified
New Lines
```
	<spring:message code="welcome.message" /> ${name}.
```
#### What we will do:
- Let's i18n.
- Exercise : Internationalize Rest of the Stuff
- http://localhost:8080/list-todos?language=en

###  Step 36 : Basic Spring Rest Services - @RestController and jackson-databind


##### /pom.xml Modified
New Lines
```
<dependency>
	<groupId>com.fasterxml.jackson.core</groupId>
	<artifactId>jackson-databind</artifactId>
	<version>2.5.3</version>
</dependency>
```
##### /src/main/java/com/in28minutes/todo/rest/TodoRestController.java New
```
package com.in28minutes.todo.rest;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

import com.in28minutes.model.Todo;
import com.in28minutes.todo.service.TodoService;

@RestController
public class TodoRestController {
	@Autowired
	private TodoService service;

	@RequestMapping(value = "/todo/", method = RequestMethod.GET)
	public List<Todo> listAllTodos() {
		List<Todo> users = service.retrieveTodos("in28Minutes");
		return users;
	}

}
```
##### /src/main/resources/log4j.properties Modified
New Lines
```
log4j.rootLogger=DEBUG, Appender1
```
#### What we will do:
- Basic Spring Rest Services.

###  Step 37 : More Rest Services - @PathVariable

##### /src/main/java/com/in28minutes/todo/rest/TodoRestController.java Modified
New Lines
```
	@RequestMapping(value = "/todo/{id}", method = RequestMethod.GET)
	public Todo retrieveTodo(@PathVariable("id") int id) {
		return service.retrieveTodo(id);
	}
```
#### What we will do:
- One More Spring Rest Services.
- @PathVariable("id") int id
#### Useful Snippets

```
produces = MediaType.APPLICATION_JSON_VALUE
```



## Spring MVC Exercises

## Read Documentation
http://docs.spring.io/spring/docs/current/spring-framework-reference/html/mvc.html

## Try a Few Spring Exercises From the Guide
https://spring.io/guides

## Setup Showcase Application
https://github.com/spring-projects/spring-mvc-showcase

## Try using the Spring Initializr
https://start.spring.io

### Some Theory

- Complete Reference
	- http://docs.spring.io/spring/docs/current/spring-framework-reference/html/mvc.html
- Architecture Diagram
	- http://docs.spring.io/spring/docs/current/spring-framework-reference/html/images/mvc.png
- Dispatcher Servlet
	- Dispatches requests to handlers, with configurable handler mappings
	- View Resolution
	- Locale, time zone and theme resolution 
	- Support for uploading files.
- Flexible Data Binding
	- Any POJO can be used as a command or form backing object
	- Highly Flexible Data Binding. Databinding Errors do not throw exceptions. They only cause validation errors.
- Flexible View Resolution
	- Controller can either
		- Return a View
		- Return a View or Model
		- Write to response stream directly
- Flexible Controller Methods
- Accepting Variety of Parameters
	- Request or response objects : ServletRequest or HttpServletRequest.
	- Session object (Servlet API): of type HttpSession. 
	- Other Options: http://docs.spring.io/spring/docs/current/spring-framework-reference/html/mvc.html#mvc-ann-methods
- Support Multiple Return Types
	- A ModelAndView object
	- A Model object
- @ModelAttribute Methods
	- Indicates the purpose of that method is to add one or more model attributes.
	- Invoked before @RequestMapping methods.
	- Used to fill the model with commonly needed attributes 
	  - Drop down values for form
	  - Command or Form Backing Objects
- Method Argument
	- To automatically add/retrieve value from Model
	- It can be stored in session as well using @SessionAttributes.
- Validation
	- Automatic
	- @Valid annotation

##### Customized
You can also invoke validation using your own custom validator 
```
@RequestMapping(path = "/something", method = RequestMethod.POST)
public String processSubmit(@ModelAttribute("todo") Pet Todo, BindingResult result) {
    new TodoValidator().validate(todo, result);
    if (result.hasErrors()) {
        return "todo";
    }
    // ...
}
```

##### @ControllerAdvice

- Can contain @ExceptionHandler, @InitBinder, and @ModelAttribute annotated methods
- These methods will apply to @RequestMapping methods across all controller hierarchies

##### Hibernate Validator : JSR 349 Reference Implementation
For more information refer http://docs.jboss.org/hibernate/validator/5.0/reference/en-US/html_single/#validator-defineconstraints-spec


