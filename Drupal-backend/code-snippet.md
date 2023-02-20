#### my_module.services.yml ####
```
services:
  my_module.data_service:
    class: Drupal\my_module\MyCustomService
    arguments: ['@database']
````

#### MyCustomService.php ####
```
<?php

namespace Drupal\my_module;

use Drupal\Core\Database\Connection;

/**
 * My custom service class.
 */
class MyCustomService {

  /**
   * The database service.
   *
   * @var \Drupal\Core\Database\Connection
   */
  protected $database;

  /**
   * Constructs a my custom service object.
   *
   * @param \Drupal\Core\Database\Connection $database
   *   Database instance.
   */
  public function __construct(Connection $database) {
    $this->database = $database;
  }

  /**
   * Do something method.
   */
  public function doSomething() {
    // Use the database service in your custom logic.
  }

}
```

#### MyController.php ####
```
<?php

namespace Drupal\my_module\Controller;

use Drupal\Core\Controller\ControllerBase;
use Drupal\my_module\MyCustomService;
use Symfony\Component\DependencyInjection\ContainerInterface;

/**
 * My controller class.
 */
class MyController extends ControllerBase {

  /**
   * My custom service.
   *
   * @var \Drupal\my_module\MyCustomService
   */
  protected $myCustomService;

  /**
   * My controller constructor.
   *
   * @param \Drupal\my_module\MyCustomService $my_custom_service
   *   My custom service object.
   */
  public function __construct(MyCustomService $my_custom_service) {
    $this->myCustomService = $my_custom_service;
  }

  /**
   * {@inheritDoc}
   */
  public static function create(ContainerInterface $container) {
    return new static(
      $container->get('my_module.data_service')
    );
  }

  /**
   * My data method.
   *
   * @return void
   */
  public function myDataMethod() {
    // Call the doSomething method on the injected service.
    $this->myCustomService->doSomething();
    // Your controller logic goes here.
  }

}
```
