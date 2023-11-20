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

### Before we dive into IOC & DI, let's take a moment to have a clear understanding of what is SPRING : 

##### Spring is a popular open-source framework for building enterprise applications in Java. Developed by Pivotal Software (a division of VMware), the Spring Framework provides comprehensive infrastructure support, making it easier to develop robust and maintainable Java applications. It provide many Key features and components such as : Inversion of Control (IoC), Dependency Injection (DI), Data Access, Transaction Management, Data Access, Model-View-Controller (MVC), Security, Spring Boot ... and many other 


# Spring-Dependency-Injection 
### let's have a general overall view of What is Dependecy Injection in a simple and general terms :
#### First of all DI is a design pattern and a fundamental concept in software development, particularly in object-oriented programming. It's a technique that promotes loose coupling between different components or classes in a software system, making the code more modular, maintainable, and easier to test.
#### dependency injection refers to the process of providing the required dependencies (objects or services) that a class or component needs to function correctly, rather than letting the class create those dependencies itself. These dependencies are typically passed to the class from an external source, such as a configuration file, a framework, or another class responsible for managing the dependencies. Here are some keys aspect of why DI is very importatnt : 

#### Loose Coupling:
Loose coupling is a design principle that promotes independence between software modules. In the context of Spring and Dependency Injection (DI), it refers to reducing the degree of dependency between components or classes.

#### Flexibility: Loose coupling allows for greater flexibility in the codebase. Changes in one module do not heavily impact other modules, making the system more adaptable to modifications.
#### Maintainability: Decoupled modules are easier to maintain, as alterations or enhancements to one module are less likely to affect the entire system.

<div align="center">
     <img src="https://logicmojo.com/assets/dist/new_pages/images/couplingjava.png" alt="Image Alt Text">
</div>

#### Modularity:
DI promotes the modularity of code, making it easier to understand and maintain. Each class focuses on its primary responsibility, and dependencies are handled separately. This leads to a cleaner and more organized codebase.

#### Testability:
In unit testing, it's often essential to isolate the behavior of a specific class or component. By injecting dependencies, you can replace real dependencies with mock objects or test doubles, allowing you to test the class in isolation and verify its functionality without the need for the actual dependencies.

### What is Inversion of Control (IoC):
In traditional programming, developers have control over the flow of the application. They create and manage objects, and the application follows the logic written by the developer.
IoC is a paradigm shift where control over the application's flow is inverted. Instead of developers controlling the creation and management of objects, this control is handed over to a framework or container.

### Types of Dependency Injection :
#### Constructor Injection
##### Constructor injection involves injecting dependencies through the constructor of a class. It is considered a robust and preferred way of injecting dependencies, as it ensures that a class instance is fully initialized when it is created.

```bash

public class UserService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}

```

### Setter Injection
#### Setter injection involves injecting dependencies through setter methods. This provides flexibility and allows changing dependencies at runtime.

```bash

public class ProductService {
    private ProductRepository productRepository;

    public void setProductRepository(ProductRepository productRepository) {
        this.productRepository = productRepository;
    }
}

```

### Field injection
#### It involves injecting dependencies directly into fields of a class 

```bash

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class OrderService {
    
    @Autowired
    private PaymentService paymentService;
}


```

### Dependency Injection in Spring Configuration:
In a Spring application, dependencies are often configured in the Spring configuration files (XML or Java-based) or through annotations. let's check the following example : 

```bash

@Configuration
public class AppConfig {

    @Bean
    public UserService userService(UserRepository userRepository) {
        return new UserService(userRepository);
    }

    @Bean
    public ProductService productService(ProductRepository productRepository) {
        ProductService productService = new ProductService();
        productService.setProductRepository(productRepository);
        return productService;
    }

}


```
