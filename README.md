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

# Spring-Dependency-Injection 
### Before we dive into IOC container in spring, let's have a general overall view of What is Dependecy Injection in a simple and general terms :
#### First of all DI is a design pattern and a fundamental concept in software development, particularly in object-oriented programming. It's a technique that promotes loose coupling between different components or classes in a software system, making the code more modular, maintainable, and easier to test.
#### dependency injection refers to the process of providing the required dependencies (objects or services) that a class or component needs to function correctly, rather than letting the class create those dependencies itself. These dependencies are typically passed to the class from an external source, such as a configuration file, a framework, or another class responsible for managing the dependencies. Here are some keys aspect of why DI is very importatnt : 

#### Loose Coupling:
Dependency injection reduces the tight coupling between classes by ensuring that a class doesn't directly instantiate its dependencies. This makes the code more flexible and easier to change because it allows you to swap out or modify dependencies without affecting the class that relies on them.

#### Modularity:
DI promotes the modularity of code, making it easier to understand and maintain. Each class focuses on its primary responsibility, and dependencies are handled separately. This leads to a cleaner and more organized codebase.

#### Testability:
In unit testing, it's often essential to isolate the behavior of a specific class or component. By injecting dependencies, you can replace real dependencies with mock objects or test doubles, allowing you to test the class in isolation and verify its functionality without the need for the actual dependencies.
