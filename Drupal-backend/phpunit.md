# PHPUnit #

#### What is PHPUnit? ####

PHPUnit is a unit testing framework for PHP, and it is used in Drupal to write and run automated tests for Drupal code. PHPUnit is used to test different components of the system, such as modules, themes, and core functionality. Writing tests with PHPUnit helps ensure that Drupal code is working as expected, making it easier to identify and fix bugs, and catch problems early to ensure that the code is stable and reliable.

#### Why use PHPUnit? ####

- **Automated testing:** PHPUnit allows for the creation of automated tests for Drupal code.
- **Coverage analysis:** PHPUnit generates reports that show how much of your Drupal code has been tested.
- **Integration with Drupal:** PHPUnit is integrated with Drupal's testing framework, making it easy to write and run tests for Drupal code.
- **Community support:** PHPUnit has a large community of developers who use it for testing Drupal code, providing many resources for learning and troubleshooting.
- **Best practices:** PHPUnit follows best practices for writing tests, such as using assertions to check code output, ensuring reliable and accurate tests.

#### How to install/setup PHPUnit? ####

To install PHPUnit with coverage, you can follow these steps:

1. **Install Composer:** PHPUnit is typically installed using Composer, a dependency manager for PHP. You can download and install Composer from the official website: https://getcomposer.org/.

2. Navigate to drupal project root directory.

3. **Require PHPUnit:** In the project directory, run the following command to require PHPUnit and its dependencies

   $ **composer require --dev phpunit/phpunit:8.x**
   
   or install with all dependencies.
   
   $ **composer require --dev phpunit/phpunit:8.x --with-dependencies **
   
   Run this **./vendor/bin/phpunit --version** command to verify PHPUnit version.
   
   **Note:** 8.x version supported by drupal 9 if you are using drupal 8 install 7.x & this dependency **composer require --dev symfony/phpunit-bridge:^5.3**. If you face any issue related to phpunit-bridge install phpunit-bridge dependency in drupal 9 as well.

4. **Install Code Coverage:** PHPUnit comes with a built-in code coverage tool, but to generate coverage reports, you'll need to install the PHP extension Xdebug. You can install it using apt by running the following command:

    $ **sudo apt-get install php7.4-xdebug**
    
    For other OS [follow this](https://xdebug.org/docs/install) link.

5. **Enable Xdebug:** After installing Xdebug, you'll need to enable it in your PHP configuration file. To do this, open your php.ini file and add the following line: **xdebug.mode=coverage**. Now run below command to verify xdebug is enabled or not.

  $ **php -v**
  ```
    PHP 7.4.33 (cli) (built: Feb 14 2023 18:31:23) ( NTS )
    Copyright (c) The PHP Group
    Zend Engine v3.4.0, Copyright (c) Zend Technologies
      with Zend OPcache v7.4.33, Copyright (c), by Zend Technologies
      with Xdebug v3.1.6, Copyright (c) 2002-2022, by Derick Rethans   <--- This line showed Xdebug enabled successfully.
   ```

#### How to setup PHPUnit for Drupal? ####

[Drupal official link](https://www.drupal.org/docs/automated-testing/phpunit-in-drupal/running-phpunit-tests)

- We need to copy **phpunit.xml.dist** file which is located in **core** folder of drupal, we will copy this file and paste it on Drupal root folder
rename it to **phpunit.xml** here are some more parameters that you may need to modify. We can use this [sample file](phpunit.xml).
- We need to create **simpltest & browser_output** directory & setting permissions for it. So follow below command to create dir.

  $ mkdir -p web/sites/simpletest/browser_output && chmod -R 777 web/sites/simpletest
  
- Once you have set up the phpunit.xml file and created your test files, you can run PHPUnit tests for your Drupal site using the following command from the root directory of your Drupal site.

  $ ./vendor/bin/phpunit web/core/modules/user/tests/src/Unit/UserRegistrationResourceTest.php (This is for verifying existing test files)
  
  $ ./vendor/bin/phpunit **--coverage-html html** web/modules/custom/custom_module/ (coverage-html generates coverage report)
  
  If we want to test multiple modules at once we need to use testsuit and mentioned modules name in phpunit.xml file. Using below command we can run testsuit
  
  $ ./vendor/bin/phpunit --testsuite custom
  
**Note:** If you found these errors HP Fatal error:  Uncaught Error: Class 'Behat\Mink\Element\TraversableElement' not found in DocumentElement.php:24 & PHPUnit\Framework\Exception: This test uses TestCase::prophesize(), but phpspec/prophecy is not installed. So install these packages using below command.
If you found any dependency related issue install that dependencies.

$ composer require behat/mink && composer require --dev phpspec/prophecy

- if you want to run multiple test files or test suites at once, you can define them in the phpunit.xml file and then run them using the testsuite element. Here's an example of how you can define a test suite for multiple Drupal modules in the phpunit.xml file:
```
<testsuites>
 <testsuite name="Modules Test Suite">
   <directory>./modules/custom/abc_module/tests/</directory>
   <directory>./modules/custom/xyz_module/tests/</directory>
 </testsuite>
</testsuites>
```
In this example, we've defined a test suite called **Modules Test Suite** that includes two directories containing test files for two custom Drupal modules. You can add additional directory elements as needed to include more modules in the test suite.

To run the test suite, you can use the following command.

$ ./vendor/bin/phpunit --testsuite "Modules Test Suite"



:house: [Home Page](README.md) | [<< Previous Page](database.md) | [Next Page >>](phpunit-details.md)
