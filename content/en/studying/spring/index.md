---
title: "Spring MVC"

authors:
  - admin

date: '2025-10-12T00:00:00Z'

links:
  - type: site
    url: https://github.com/wlsdudwjd/spring-servlet

tags:
  - Spring
  - Java
  - Servlet
  - MVC
  - Backend
  - HTTP

featured: true

share: false

reading_time: false
---

##From Servlets to Spring MVC: Learning the Evolution of Java Web Development
This time, I took the opportunity to trace the evolution of web applications, a technology that can be called the core of Java backend development.

Why Web Applications? Most modern applications operate in a web environment. The countless services we use every day are, in fact, web applications. Java backend developers play a critical role in developing the server-side logic for these applications, and the most powerful tool used for this is the Spring Framework—specifically, Spring MVC.

To gain a deep understanding of Spring MVC, which helps us develop complex web applications quickly and easily, I studied its foundational technologies step-by-step, starting from its very roots.

1. The Beginning of Java Web Tech: Servlets
Everything started with Servlets. A Servlet is pure Java code that receives a client's request, processes business logic, and generates a dynamic HTML response. However, this approach had a major drawback: HTML code had to be written directly within the Java code as strings (e.g., out.println("<html>...")). This made modifying the view (the UI) cumbersome and severely harmed readability.

2. Separating the View: JSP (JavaServer Pages)
JSP emerged to compensate for this shortcoming. JSP is a technology that allows embedding Java code within an HTML document, which made collaboration between designers and developers much easier. Thanks to this, the task of presenting the view became much more manageable.

But JSP alone was not enough. Business logic and presentation code were still mixed in a single file. As projects grew larger, this led to "spaghetti code," which became increasingly difficult to maintain.

3. The Start of Role Separation: The MVC Pattern
To solve this problem, a design philosophy called the MVC (Model-View-Controller) pattern emerged.

Model: Manages the data and business logic.

View: Manages the screen (UI) shown to the user. (JSP)

Controller: Acts as the intermediary, receiving the user's request and connecting the Model and View. (Servlet)

By clearly separating these roles, the code became much more structured and reusable.

4. The Birth of Spring MVC and its Practical Use
Implementing the MVC pattern manually still involved a lot of repetitive and cumbersome work. Developers began to create MVC frameworks to make using this pattern easier, and the most successful and overwhelmingly popular of these became Spring MVC.

Spring MVC handles the complex processes required for MVC implementation on behalf of the developer, providing an environment where one can focus solely on the business logic. This study covered everything from the origins of Spring MVC to the modern techniques used in the field, allowing me to personally understand why countless companies choose Spring.

I will continue to share my experiences as I conduct my own projects using these technologies. Thank you!

You can check out the code I've studied so far via the link attached above!