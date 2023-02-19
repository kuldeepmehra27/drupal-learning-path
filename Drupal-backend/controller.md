# Controller #
#### Namespaces ####
Before moving on with the Controller we set out to write, let's break down the namespace situation in
Drupal 8 and how the folder structure needs to be inside a module.
Drupal 8 uses the PSR-4 namespace autoloading standard. In effect, this means that the namespace of
all Drupal core and module classes starts with \Drupal . For modules, the base namespace is
\Drupal\module_name , where module_name is the machine name of the module. This then maps to the /src
folder found inside the module directory (for main integration files). For PHPUnit tests, we have a
different namespace, as we will see later in the book.
So essentially, we will need a /src folder inside our module to place all of our classes that need to be
autoloaded. So, we can go ahead and create it.

#### What is Controller? ####
In Drupal, a controller is a PHP class that handles requests and generates responses. It is a key component of the Model-View-Controller (MVC) architecture and is used to implement the application logic of a Drupal site. The controller class extends the ControllerBase class and provides helper methods for working with Drupal's API. When a request is made, the routing system matches it to a specific controller method, which generates a response based on data retrieved from a model and rendered into a view. Controllers are a central part of Drupal's handling of HTTP requests and are essential for building dynamic and interactive web applications.

#### Why use Controller? ####
Controllers in Drupal are used for handling requests and implementing the application logic of a site, separating business logic from presentation, enabling code reusability, extending functionality, and providing security measures. They are a critical part of the Model-View-Controller (MVC) architecture in Drupal and help developers create dynamic and interactive web applications that are flexible and maintainable.

#### How to use Controller? ####
- Create a PHP class that extends the **ControllerBase** class.
- Define a method that will handle a specific request.
- Access the Drupal API to retrieve data from the database or perform other operations in the controller method.
- Render the output using a specific theme or render array and return it as the response to the request.
- Define a route that points to the controller method to invoke it when a request is made.
- Controllers help implement the application logic of a Drupal site and build dynamic and interactive web applications.

Example:
![Controller](/images/controller.png)

:house: [Home Page](README.md) | [<< Previous Page](routing-system.md) | [Next Page >>](services-and-di.md)
