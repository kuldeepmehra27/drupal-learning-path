#### How to create PHPUnit test file in drupal? ####

To create a PHPUnit test file in Drupal, you can follow these steps:

1. **Create a module:** If you don't already have a module, create a new one using Drupal Console or manually. For example, let's create a module named my_module.

2. **Create tests/src/Unit folders:** Inside the my_module directory, create folders named tests/src/Unit.

3. **Create a PHPUnit test file:** Inside the tests folder, create a new PHP file with the name of your test, for example, MyModuleTest.php.

4. **Include the necessary dependencies:** In your test file, include the necessary dependencies using the use keyword. For example: **use Drupal\Tests\UnitTestCase;**

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

$ **./vendor/bin/phpunit --coverage-html html_reports web/modules/custom/custom_module/**


This is test file: https://github.com/kuldeepmehra27/custom_module/tree/master/tests/src/Unit/Services/MyCustomServiceTest.php



:house: [Home Page](README.md) | [<< Previous Page](phpunit-details.md)
