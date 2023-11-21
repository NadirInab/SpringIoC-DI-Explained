<div align="center">
     <img src="https://www.itprotoday.com/sites/itprotoday.com/files/java-logo_0.jpg" alt="Image Alt Text">
</div>

![Java](https://img.shields.io/badge/Spring-gold.svg)
![Java](https://img.shields.io/badge/InversionOfControl-green.svg)
![Java](https://img.shields.io/badge/LooseCoupling-green.svg)
![Java](https://img.shields.io/badge/TightCoupling-red.svg)
![Java](https://img.shields.io/badge/JavabBeans-black.svg)
![JavaDoc](https://img.shields.io/badge/annotations-purple.svg)
![JavaDoc](https://img.shields.io/badge/serviceContainer-yellow.svg)
![JavaDoc](https://img.shields.io/badge/DependencyInjection-gold.svg)
![JavaDoc](https://img.shields.io/badge/Universe-diamond.svg)
![JavaDoc](https://img.shields.io/badge/Maintainbility-khaki.svg)
![JavaDoc](https://img.shields.io/badge/Reusability-brown.svg)
![JavaDoc](https://img.shields.io/badge/Testability-green.svg)

<div align="center">
     <img src="https://blog.knoldus.com/wp-content/uploads/2018/08/DgRbnNRUcAAaBTW.jpg" alt="Image Alt Text">
</div>

### Before we dive into IOC & DI, let's take a moment to have a clear understanding of what is SPRING 👇: 

- Spring is a popular open-source framework for building enterprise applications in Java. Developed by Pivotal Software (a division of VMware).
- the Spring Framework provides comprehensive infrastructure support, making it easier to develop robust and maintainable Java applications.
- It provide many Key features and components such as : Inversion of Control (IoC), Dependency Injection (DI), Data Access, Transaction Management, Data Access, Model-View-Controller (MVC), Security, Spring Boot ... .


# Spring-Dependency-Injection 
### let's have a general overall view of What is Dependecy Injection in a simple and general terms :
#### First of all DI is a design pattern and a fundamental concept in software development, particularly in object-oriented programming.
- It's a technique that promotes loose coupling between different components or classes in a software system, making the code more modular, maintainable, and easier to test.

- dependency injection refers to the process of providing the required dependencies (objects or services) that a class or component needs to function correctly, rather than letting the class create those dependencies itself. 
- These dependencies are typically passed to the class from an external source, such as a configuration file, a framework, or another class responsible for managing the dependencies
#### Tight Coupling:
- Definition: Tight coupling refers to a situation where classes or components are highly dependent on each other's concrete implementations.
Example: Directly instantiating objects or referencing concrete classes within another class.
#### Loose Coupling:
- Definition: Loose coupling refers to reducing dependencies between components by relying on abstractions, interfaces, or dependency injection.
Example: Using interfaces, abstractions, or DI containers to decouple components.
<div>
    <img align="center" src="https://cdn.discordapp.com/attachments/892131953808130079/1176409489243656222/image.png?ex=656ec3b6&is=655c4eb6&hm=cd4719680c0f472ada200d8ea839d118ce5d9bc5bef0614aabad2285cd3470ef&"></img>
</div>


## If we needed to change/replace ClassB with ClassC because ClassC has an optimized version of the calculate() method, we need to recompile ClassA because we don't have a way to change that dependency, it's hardcoded inside of ClassA.

#### Here are some keys aspect of why DI is very importatnt 💯 : 

- **Loose Coupling ⛓️:**

#### In general it's  a design principle that promotes independence between software modules. In the context of Spring and Dependency Injection (DI), it refers to reducing the degree of dependency between components or classes.
---
- **Flexibility: ♻️ **

 Loose coupling allows for greater flexibility in the codebase. Changes in one module do not heavily impact other modules, making the system more adaptable to modifications.
 
---
 
- **Maintainability: 🏰**

Decoupled modules are easier to maintain, as alterations or enhancements to one module are less likely to affect the entire system.

---

- **Testability:** 

Facilitating isolation of behavior for unit testing.
#### Without Dependency Injection:
```java 
public class UserService {
    private final UserRepository userRepository;

    public UserService() {
        this.userRepository = new UserRepository(); // Direct instantiation
    }

    public String getUserFullName(int userId) {
        User user = userRepository.getUserById(userId);
        return user != null ? user.getFullName() : "User not found";
    }
}
```
Without DI, testing becomes difficult due to direct instantiation of UserRepository
```java
public class UserServiceTestWithoutDI {
    @Test
    public void testGetUserFullName() {
        UserService userService = new UserService();
        String fullName = userService.getUserFullName(1);
        // ...
    }
}
```
#### With Dependency Injection:
```java 
public class UserService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository; // Dependency injection through constructor
    }

    public String getUserFullName(int userId) {
        User user = userRepository.getUserById(userId);
        return user != null ? user.getFullName() : "User not found";
    }
}

```
```java 
public class UserServiceTestWithDI {
    @Test
    public void testGetUserFullName() {
        // With DI, we can inject a mock or fake UserRepository for testing
        UserRepository mockRepository = Mockito.mock(UserRepository.class);
        User user = new User(1, "John Doe");
        Mockito.when(mockRepository.getUserById(1)).thenReturn(user);
        UserService userService = new UserService(mockRepository);
        String fullName = userService.getUserFullName(1);
        assertEquals("John Doe", fullName);
    }
}
```

---

<div align="center">
     <img src="https://logicmojo.com/assets/dist/new_pages/images/couplingjava.png" alt="Image Alt Text">
</div>

### What is Inversion of Control (IoC) ❓:
In traditional programming, developers have control over the flow of the application. They create and manage objects, and the application follows the logic written by the developer.
IoC is a paradigm shift where control over the application's flow is inverted. Instead of developers controlling the creation and management of objects, this control is handed over to a framework or container.

### Types of Dependency Injection  🤔:

#### Constructor Injection
##### Constructor injection involves injecting dependencies through the constructor of a class. It is considered a robust and preferred way of injecting dependencies, as it ensures that a class instance is fully initialized when it is created.

```java

public class UserService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}

```

### Setter Injection
#### Setter injection involves injecting dependencies through setter methods. This provides flexibility and allows changing dependencies at runtime.

```java

public class ProductService {
    private ProductRepository productRepository;

    public void setProductRepository(ProductRepository productRepository) {
        this.productRepository = productRepository;
    }
}

```

### Field injection
#### It involves injecting dependencies directly into fields of a class 

```java

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class OrderService {
    
    @Autowired
    private PaymentService paymentService;
}

```

#### Why is not recomended to use field injection 🤔 ❓  
- Cyclic Dependency Risks 🔁
- Testing Challenges 🥵

### Dependency Injection in Spring Configuration:
In a Spring application, dependencies are often configured in the Spring configuration files (XML or Java-based) or through annotations. before we dive into example first of all let's understand few annotations that spring provide in order to simplifies the process of configuartion : 

# Spring Annotations Quick Reference

### Why do we use Annotation ❓

- Annotations in Java, and specifically in the context of the Spring framework, serve various purposes to enhance and simplify the development of applications.

---

### What is Component Scanning ❓

- Component scanning is the process by which Spring identifies classes with stereotype annotations (like @Component) and creates bean definitions for them.

- Spring uses component scanning to automatically discover and register components in the application context.

---

### What are stereotype annotations ❓

- In the context of Spring Framework, stereotype annotations are a group of annotations that define and identify certain types of components. These annotations provide metadata about the roles of annotated classes in the application..


## @Component 

 Marks a class as a Spring component, enabling automatic detection and registration as a bean in the Spring context.

```java

@Component
public class MyComponent {
    // ... class definition
}

```

---

## @Repository 

 Indicates that a class is a Data Access Object (DAO) and is eligible for exception translation.

```java

@Repository
public class MyRepository {
    // ... class definition
}

```

---


## @Service 

 Marks a class as a service component in the business layer.

```java

@Service
public class MyService {
    // ... class definition
}

```

---

## @Controller 

 Marks a class as a controller in the presentation layer.
 
```java

@Controller
public class MyController {
    // ... class definition
}


```

## @Autowired 

Used for automatic dependency injection. It can be applied to fields, methods, and constructors.
 
```java

@Service
public class MyService {
    @Autowired
    private MyRepository repository;

}
```
----

#### Quick Recap 👌:

Annotations in Spring serve as metadata that provides additional information to the Spring IoC container or other components. They enhance the configuration, modularity, and manageability of Spring applications.


### Spring Scopes ✅

- In Spring, a bean's scope defines the lifecycle and visibility of that bean within the Spring IoC (Inversion of Control) container. Different scopes are designed to meet various requirements in terms of object instantiation.

### Singleton 

- Only one instance of the bean is created, and it is shared across the entire Spring container.

###  Prototype

- A new instance of the bean is created every time it is requested.
- This is useful for handling mutable data specific to individual requests.


### Request

- A new instance of the bean is created for each HTTP request in a web application.
- suitable for handling request-specific data like form submissions.

### Session

- A new instance of the bean is created for each HTTP session in a web application.
- suitable for user-specific data that persists across multiple requests.


### Concluion
Understanding IoC, DI, and leveraging the Spring framework empowers developers to create software that is modular, maintainable, and scalable 💯.
