# Routing System #
#### What is Routing? ####
In Drupal, routing is the process of mapping URLs to specific content and functionality within a Drupal site. When a user clicks on a link or enters a URL into their browser, Drupal uses routing to determine which page or content to display.

Routing in Drupal is handled by the Drupal menu system, which provides a structured way to define paths and their corresponding callbacks. The menu system is used to define the routing for all pages, including nodes, views, and custom pages.

Routing in Drupal also includes the ability to define custom URLs for content and functionality. This allows developers to create custom routes.

[Click here](https://www.drupal.org/docs/drupal-apis/routing-system/routing-system-overview#s-routes-and-controllers) to get how route system works.

#### Why use Routing? ####
Routing is an essential part of web application development, and in Drupal, it allows developers to define clear and structured URL hierarchies for their sites, making it easier for users and search engines to understand the content and organization of the site. Routing also enables developers to reuse code and logic across different parts of their site, and to define permissions and access controls to ensure security. In Drupal specifically, the routing system is used to match incoming requests to the appropriate controller, allowing developers to build dynamic and extensible web applications that are easy to maintain and secure.

#### How to use Routing? ####
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

#### Using parameters in routes / Route variables ####
A very common requirement is to have a variable route parameter (or more) that gets used by the
code that maps to the route, for example, the ID or path alias of the page you want to show. These
parameters can be added by wrapping a certain path element into curly braces, like so:
```
path: '/hello/{param}'
```
Here, {param} will map to a $param variable that gets passed as an argument to the controller or handler
responsible for this route. So, if the user goes to the hello/jack path, the $param variable will have the
jack value and the controller can use that.
Additionally, Drupal 8 comes with parameter converters that transform the parameter into something
more meaningful. For example, an entity can be autoloaded and passed to the Controller directly
instead of an ID. Also, if no entity is found, the route acts as a 404, saving us a few good lines of
code. To achieve this, we will also need to describe the parameter so that Drupal knows how to
autoload it. We can do so by adding a route option for that parameter:
```
options:
  parameters:
    param:
      type: entity:node
```
So, we have now mapped the {param} parameter to the node entity type. Hence, if the user goes to
hello/1 , the node with the ID of 1 will be loaded (if it exists).
We can do one better. If, instead of {param}, we name the parameter {node} (the machine name of the
entity type), we can avoid having to write the parameters option in the route completely. Drupal will
figure out that it is an entity and will try to load that node by itself. Neat, no?
So keep these things in mind the next time you need to write dynamic routes.

EX: 
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

:house: [Home Page](README.md) | [Next Page >>](controller.md)
