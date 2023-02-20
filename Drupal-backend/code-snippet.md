#### my_module.services.yml ####
```
services:
  my_module.data_service:
    class: Drupal\my_module\CustomService
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
    // Use the database and logger services in your custom logic.
  }

}
```
