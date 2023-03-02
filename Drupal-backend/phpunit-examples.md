#### How to create PHPUnit test file in drupal? ####

To create a PHPUnit test file in Drupal, you can follow these steps:

1. **Create a module:** If you don't already have a module, create a new one using Drupal Console or manually. For example, let's create a module named my_module.

2. **Create tests/src/Unit folders:** Inside the my_module directory, create folders named tests/src/Unit.

3. **Create a PHPUnit test file:** Inside the tests folder, create a new PHP file with the name of your test, for example, **MyModuleTest.php**.
   **Note:** The convention is to append the word "Test" as a suffix to every test file.

4. **Include the necessary dependencies:** In your test file, include the necessary dependencies using the use keyword.
   
   For example: **use Drupal\Tests\UnitTestCase;**

5. **Define the test class:** Define a class for your test by extending the appropriate Drupal test base class. For example:
```
class MyModuleTest extends UnitTestCase {
  // Your test code goes here.
}
```
6. **Write your test code:** Write your test code inside the test class. Use PHPUnit's assertion methods to check that your code is working as expected.

7. **Run the tests:** Run the tests by running the following command in the terminal from the root directory of your Drupal site:
   
   $ **./vendor/bin/phpunit modules/custom/my_module/**
   
  This will run all the tests in the tests directory of your my_module module. If you only want to run a specific test, add the name of the test file to the command:
  
  $ **./vendor/bin/phpunit modules/custom/my_module/tests/Unit/Services/MyModuleServicesTest.php**

![Test file dir struture](/images/test-dir-example.png)

# Working example #

Clone this repo: https://github.com/kuldeepmehra27/custom_module in your drupal custom module folder. Than run below command.

$ **./vendor/bin/phpunit --coverage-html test-reports web/modules/custom/custom_module/**

  ![Drupal custom module test](/images/phpunit-for-custom-module.png)
 
  After running tests on your custom Drupal module, navigate to the root folder of your project and check the **test-reports** folder. Inside the "test-reports" folder, you should see an **index.html** file. Open this file in your web browser to view the coverage details of your custom module.


This is test file: https://github.com/kuldeepmehra27/custom_module/tree/master/tests/src/Unit/Services/MyCustomServiceTest.php

> If you want to explore more about Drupal class methods related to PHPUnit testing, you can check the Drupal core PHPUnit test files. These files provide in-depth examples of how to create test classes, use PHPUnit's assertion methods, and interact with Drupal services and objects. By studying the core tests, you can gain a better understanding of how Drupal works and how to write reliable and maintainable test code for your own modules.

:house: [Home Page](README.md) | [<< Previous Page](phpunit-details.md)
