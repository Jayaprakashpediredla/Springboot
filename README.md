# Springboot

This repo will guide you through building and deploying a fully functional, secure, well-tested RESTful API for a hypothetical Family Cash Card application.

**What Will You Build?**
You'll be building a simple Family Cash Card application — a modern way for parents to manage allowance funds for their kiddos.

You'll use Spring Boot to progress from creating a single cash card in a database to allowing for the editing, deleting, and viewing of multiple cash cards, and finally securing your app against unauthorized access and unwanted exploits.

![image](https://github.com/Jayaprakashpediredla/Springboot/assets/45528469/7d9e6bf3-0894-4d34-a206-53c2cde259fa)


**By the end of the course, you'll be able to:**

Utilize Spring Boot to build a complete RESTful API while understanding the benefits and tradeoffs of REST.
Learn what Spring Boot offers to application developers and how it differs from the Spring Framework.
Build Web applications with Spring Web.
Use Spring Data to connect databases and map relational data to Java objects.
Use Spring Security to develop software with a Security First approach.


**--Steel Thread--**
We'll approach building our application using a Steel Thread. The idea is to first create a "thread" through all the integration points of the application. Completing the thread first has advantages, including:

Incremental delivery: It results in an end-to-end, executable application to which we can add functionality.
Risk mitigation: It can reveal hidden technical hurdles throughout the system earlier rather than later.


The three integration points in our application are the API "front door", the database, and security.
**
As we build our Family Cash Card API we will use,
Spring MVC for the web application, 
Spring Data for data access, and 
Spring Security for authentication and authorization.**


**Spring**********
Spring is a comprehensive framework that provides various modules for building different types of applications. It's like having a giant toolbox with every tool you could possibly need to build anything you want. As we build our Family Cash Card API we will use Spring MVC for the web application, Spring Data for data access, and Spring Security for authentication and authorization.

This versatility comes at a cost. Setting up a Spring application requires a lot of configuration, and developers need to manually configure various components of the framework to get an application up and running.

**Spring Boot**********
Fortunately, Spring Boot makes working with Spring much simpler. Spring Boot is like a more opinionated version of Spring. It comes with many pre-configured settings and dependencies that are commonly used in Spring applications. This makes it really easy to get started quickly, without having to worry about setting up everything from scratch. Plus, Spring Boot comes with an embedded web server, so you can easily create and deploy web applications without needing an external server.

In summary, Spring is a powerful, comprehensive framework that gives you a lot of flexibility, but can be a bit overwhelming to set up. Spring Boot is a more opinionated, streamlined version of Spring that comes with a lot of built-in features to help you get started quickly and easily



***Spring's Inversion of Control Container:***
Spring Boot takes advantage of Spring Core's Inversion of Control (IoC) container. You'll use this feature of Spring extensively while building the Family Cash Card application. There's ample documentation for this concept, but here we'll keep it simple.

Spring Boot allows you to configure how and when dependencies are provided to your application at runtime. This puts you in control of how your application operates in different scenarios.

For example, you might want to use a different database for local development than for your live, public-facing application. Your application code shouldn't care about this distinction; if it did, you'd have to hard-code every possible scenario into your application logic. Instead, Spring Boot allows you to provide an external configuration that specifies how and when such dependencies are used.

Inversion of control is often called dependency injection (DI), though this is not strictly correct. Dependency injection and accompanying frameworks are one way of achieving inversion of control, and Spring developers will often state that dependencies are "injected" into their applications at runtime. We're making this distinction clear because many software languages and frameworks implement IoC, but don't necessarily call it "dependency injection." However, within the Spring community, you'll often hear the terms used interchangeably.

Learn more about Spring's IoC Container in Spring's official documentation.(https://docs.spring.io/spring-framework/reference/core/beans.html)


****Spring Initializr***
When starting a new Spring Boot application, Spring Initializr is the recommended first step. You can think of Spring Initializr like a shopping cart for all of the dependencies your application might need. It will quickly and easily generate a complete, ready-to-run Spring Boot application.


**************************************

the following commands to use the gradle wrapper to build and test the generated application.

[~] $ cd cashcard
[~/cashcard] $ ./gradlew build
**************************************


##### API Contracts:
The software industry has adopted several patterns for capturing agreed upon API behavior in documentation and code. These agreements are often called "contracts". 
Two examples include,
Consumer Driven Contracts, 
Provider Driven Contracts. 

We define an API contract as a formal agreement between a software provider and a consumer that abstractly communicates how to interact with each other. This contract defines how API providers and consumers interact, what data exchanges looks like, and how to communicate success and failure cases.

The provider and consumers do not have to share the same programming language, only the same API contracts. For the Family Cash Card domain, let’s assume that currently there's one contract between the Cash Card service and all services using it. Below is an example of that first API contract.


Request
  URI: /cashcards/{id}
  HTTP Verb: GET
  Body: None

Response:
  HTTP Status:
    200 OK if the user is authorized and the Cash Card was successfully retrieved
    401 UNAUTHORIZED if the user is unauthenticated or unauthorized
    404 NOT FOUND if the user is authenticated and authorized but the Cash Card cannot be found
  Response Body Type: JSON
  Example Response Body:
    {
      "id": 99,
      "amount": 123.45
    }



***What Is Test Driven Development?***
It’s common for software development teams to author automated test suites to guard against regressions. Often these tests are written after the application feature code is authored. We'll take an alternative approach: we'll write tests before implementing the application code. This is called test driven development (TDD).

Why apply TDD? By asserting expected behavior before implementing the desired functionality, we’re designing the system based on what we want it to do, rather than what the system already does.

Another benefit of “test-driving” the application code is that the tests guide you to write the minimum code needed to satisfy the implementation. When the tests pass, you have a working implementation (the application code), and a guard against introducing errors in the future (the tests).

Not sure how to actually implement TDD? Don’t worry, you’ll get a lot of practice test-driving the Family Cash Card application throughout this course.

The Testing Pyramid
Different tests can be written at different levels of the system. At each level, there is a balance between the speed of execution, the “cost” to maintain the test, and the confidence it brings to system correctness. This hierarchy is often represented as a “testing pyramid”.






