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
   
   $ **composer require --dev phpunit/phpunit:8.x --with-dependencies**
   
   Now create a bridge between raw php library and Symfony since Drupal is inheriting symfony.
   For that we need to install another library run below command
   
   $ **composer require --dev symfony/phpunit-bridge:^5.3**
   
   Run this $ **./vendor/bin/phpunit --version** command to verify PHPUnit version.
   
   **Note:** If you're using Drupal 9, it supports PHPUnit version 8.x. However, if you're using Drupal 8, you should install version 7.x. You can install PHPUnit globally using the **composer global** command, but it's recommended to install it per Drupal project.
   
4. **Install Code Coverage:** PHPUnit comes with a built-in code coverage tool, but to generate coverage reports, you'll need to install the PHP extension Xdebug. You can install it using following command:

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

- We need to copy **phpunit.xml.dist** file which is located in **core** folder of drupal, **we will copy this file and paste it on Drupal root folder**
rename it to **phpunit.xml** here are some more parameters that you may need to modify. We can use this [sample file](phpunit.xml).
- We need to create **simpltest & browser_output** directory & setting permissions for it. So follow below command to create dir.

  $ mkdir -p web/sites/simpletest/browser_output && chmod -R 777 web/sites/simpletest
  
- Once you have set up the phpunit.xml file and created your test files, you can run PHPUnit tests for your Drupal site using the following command from the root directory of your Drupal site.

  $ **./vendor/bin/phpunit web/core/modules/user/tests/src/Unit/UserRegistrationResourceTest.php** (This is for verifying existing drupal core test files)
  
     ![Phpunit for core](/images/phpunit-for-core.png)
     
    **Note:** If you encounter the these errors. Uncaught Error: Class **'Behat\Mink\Element\TraversableElement'** not found in DocumentElement.php:24 & PHPUnit\Framework\Exception: This test uses TestCase::prophesize(), but phpspec/prophecy is not installed. You can resolve them by installing the necessary packages using the following command.

  $ **composer require behat/mink && composer require --dev phpspec/prophecy**
  
     If you encounter any dependency related issues during installation, you can resolve them by installing the required dependencies.
  
  $ **./vendor/bin/phpunit --coverage-html test-reports web/modules/custom/custom_module/** (coverage-html generates coverage report)
  
     ![Phpunit for custom module](/images/phpunit-for-custom-module.png)
  
  If we want to test multiple modules at once we need to use testsuit and mentioned modules name in phpunit.xml file. Using below command we can run testsuit
  
  $ **./vendor/bin/phpunit --testsuite custom**

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

$ **./vendor/bin/phpunit --testsuite "Modules Test Suite"**

**Note:** These all are commands and setup validated and tested on **Ubuntu OS**. For other **OS** only XDEBUG setup (steps 4 & 5) are different.

:house: [Home Page](README.md) | [<< Previous Page](database.md) | [Next Page >>](phpunit-details.md)
