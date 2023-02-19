# Routing System #
In Drupal, routing is the process of mapping URLs to specific content and functionality within a Drupal site. When a user clicks on a link or enters a URL into their browser, Drupal uses routing to determine which page or content to display.

Routing in Drupal is handled by the Drupal menu system, which provides a structured way to define paths and their corresponding callbacks. The menu system is used to define the routing for all pages, including nodes, views, and custom pages.

Routing in Drupal also includes the ability to define custom URLs for content and functionality. This allows developers to create custom routes.

[Click here](https://www.drupal.org/docs/drupal-apis/routing-system/routing-system-overview#s-routes-and-controllers) to get how route system works.

#### routing.yml files #### 
A module would define routing rules in **module_name.routing.yml**.
Example:
```
example.content:
  path: '/example'
  defaults:
    _controller: '\Drupal\example\Controller\ExampleController::content'
    _title: 'Hello World'
  requirements:
    _permission: 'access content'
```
- The **path** section specifies the URL path that will trigger this route. In this case, the path is /example.
- The **defaults** section defines default values for the route. In this case, it specifies that the route should use the ExampleController class to handle the request and that the page title should be "Hello World".
- The **requirements** section defines any requirements that must be met in order for the route to be accessible. In this case, the route requires the user to have the "access content" permission.

[Click here](https://www.drupal.org/docs/drupal-apis/routing-system/structure-of-routes) to get more details about routes structure.

#### Using parameters in routes ####
1. Define the route with parameters in the YAML format like below:
```
mymodule.example:
  path: '/example/{name}'
  defaults:
    _controller: '\Drupal\mymodule\Controller\MyController::example'
  requirements:
    _permission: 'access content'
```
In this example, we are defining a route named mymodule.example with a path of /example/{name}. The curly braces around parameter indicate that it is a dynamic parameter. The defaults key specifies the controller that will handle this route. The requirements key sets the permission required to access this route.

2. Create the controller class in your module & pass this **name** paramerter. This pararmeter name should be same as mentioned in routing.yml file. To see what additional parameters are available in Drupal, [check the documentation.](https://www.drupal.org/docs/8/api/routing-system/parameters-in-routes/using-parameters-in-routes)

References:
[Drupal routing system](https://www.drupal.org/docs/drupal-apis/routing-system)
