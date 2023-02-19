# Controller #
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
```
<?php 

namespace Drupal\my_module\Controller;

use Drupal\Core\Controller\ControllerBase;

/**
 * Provides a page controller for the custom module.
 */
class MyModuleController extends ControllerBase {

  /**
   * Returns a simple response for the "hello" page.
   */
  public function helloPage() {
    $build = [
      '#markup' => $this->t('Hello World!'),
    ];
    return $build;
  }

}
```
