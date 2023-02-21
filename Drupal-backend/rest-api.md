# Rest API #

#### What is REST? ####
REST, short for Representational State Transfer, is an architecture style used to set standards for communication between different computer systems on the web. RESTful systems, which follow these standards, are known for being stateless and for separating client and server concerns. Being stateless means the server doesn't keep track of the client's previous requests, and separating concerns helps with maintaining and scaling the system. 

![Rest model](/images/rest-model.png)

**Client:** In API, the client is the user or software that interacts with the API, like a developer who uses an API to read and write data or a web browser that calls the API to render information on the screen.

**Resource**: A resource is an object that the API provides information about and can be a user, a photo, or a hashtag, among others. Each resource has a unique identifier, which can be a name or a number.

#### Stateless ####

In REST, systems are stateless, meaning that the server and client don't need to keep track of each other's previous interactions. This is done by using resources, which are objects or things that are stored or sent between services. REST systems rely on standard operations and don't need interfaces, which helps with reliability, performance, and scalability. This allows components to be updated or reused without affecting the entire system. Next, we'll look at how communication happens between the client and server in a RESTful interface.

#### Communication between Client and Server ####

In the REST architecture, clients send requests to retrieve or modify resources, and servers send responses to these requests. Let’s take a look at the standard ways to make requests and send responses.

#### Making Requests ####

REST requires that a client make a request to the server in order to retrieve or modify data on the server. A request generally consists of:

- an HTTP verb, which defines what kind of operation to perform
- a header, which allows the client to pass along information about the request
- a path to a resource
- an optional message body containing data

#### HTTP Verbs ####

There are 4 basic HTTP verbs we use in requests to interact with resources in a REST system:

- **GET —** retrieve a specific resource (by id) or a collection of resources
- **POST —** create a new resource
- **PUT —** update a specific resource (by id)
- **DELETE —** remove a specific resource by id
[Read more about rest](https://www.codecademy.com/article/what-is-rest)

# [Custom REST Resources](https://www.drupal.org/docs/drupal-apis/restful-web-services-api/custom-rest-resources) #

**canonical & create:** In Drupal REST, "canonical" and "create" are two operations used to retrieve a single resource and create a new resource respectively. To define these operations for a custom resource, you can use the RESTful Web Services module, create a custom plugin that extends the appropriate base class for your resource and define the operations using annotations. The Drupal 8 REST API can then be used to access your custom resource using the canonical and create operations.

First install [Rest UI](https://www.drupal.org/project/restui) module so we can easy maintain rest end points.

**Creating the Resource Plugins:** Create a PHP file in the module directory and define the resource you want to expose. Ex:

![Module dir](/images/module-dir.png)
![Create rest](/images/create-rest.png)

**Define required methods:** Define required methods like get, post etc and add logic according to requirements. Ex:

![Create rest](/images/define-methods.png)

**Enable rest plugin:** Goto this location **admin/config/services/rest**, enable rest plugin with required [authentication provider](https://www.drupal.org/docs/8/api/authentication-api/overview).

![Enable rest](/images/Enable-rest-resource.png)
![Rest settings](/images/rest-settings.png)

**Configure permissions:** Set up permissions for the REST resource in your Drupal 8 installation. For example, you can give the "anonymous" user role permission to access the custom resource by going to **"People" -> "Permissions" -> "RESTful Web Services"** and enabling the methods for the "Custom Resource" resource.

![Rest permission](/images/Rest-permission.png)

**Test the API:** Use a REST client to test your custom API and ensure that it is working as expected. For example, you can use a tool like Postman to make a requests to the custom resource URL's.

![Rest example](/images/rest-example.png)

#### Create a custom authentication provider ####

If you want to create custom authentication provider [follow this official doc](https://www.drupal.org/docs/drupal-apis/authentication-api/create-a-custom-authentication-provider).

:house: [Home Page](README.md) | [<< Previous Page](services-and-di.md) | [Next Page >>](caching.md)
