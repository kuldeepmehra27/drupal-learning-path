# Services and Dependency Injection #
#### What is Services? ####
A service is any object managed by the services container.

Key points to remember:
- Services in Drupal refer to the various functionalities that are provided by the drupal core, contributed modules, or custom modules.
- Services can take many forms, such as authentication, content management, search, media, e-commerce, social media integration, and analytics.
- Drupal allows developers to create custom services, which can be accessed by other modules or external applications using APIs.
- Services play a critical role in extending the functionality of a website and can be used to build complex, powerful applications.

#### Why use Services? ####
why services are used in Drupal:

- Services are used to extend the core functionality of Drupal and add new features to a website.
- They make it easy to connect Drupal with other applications and systems by exposing functionality via web services and APIs.
- Services can decouple Drupal from the front-end presentation layer, which provides greater flexibility and scalability.
- They can be reused across multiple sites and applications, providing a more efficient development process.
- Services can be used to automate common tasks, such as content creation, user management, and data import/export.
- They provide a way to integrate Drupal with other systems, such as CRM tools, e-commerce platforms, and marketing automation tools.
- Services are an essential component of Drupal, providing a way to extend the platform's functionality and integrate it with other systems and applications.

#### What is Dependency Injection? ####
As defined by Wikipedia, “ dependency injection is a technique whereby one object supplies the dependencies of another object. A dependency is an object that can be used (a service). An injection is the passing of a dependency to a dependent object (a client) that would use it. The service is made part of the client’s state.”

It simply means passing the service (i.e. dependency) to the client (i.e. dependent). This passing of the service to the client rather than allowing the client to build/find the service is known as dependency injection.

#### Why use Dependency Injection? ####
- It helps developers build modular, flexible, testable, decoupled functionality, code more reusable, and maintainable code.
- It separates concerns and dependencies in code.
- It allows code to be divided into smaller, more manageable pieces.
- It promotes encapsulation by ensuring each object is responsible for its own functionality.
- It allows for easier testing of individual components.
- In web development, it is particularly useful for building complex applications.
- These complex applications rely on many interdependent objects and services.
