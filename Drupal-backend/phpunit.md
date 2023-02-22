# PHPUnit #

#### What is PHPUnit? ####

PHPUnit is a unit testing framework for PHP, and it is used in Drupal to write and run automated tests for Drupal code. PHPUnit is used to test different components of the system, such as modules, themes, and core functionality. Writing tests with PHPUnit helps ensure that Drupal code is working as expected, making it easier to identify and fix bugs, and catch problems early to ensure that the code is stable and reliable.

#### Why use phpunit? ####

- **Automated testing:** PHPUnit allows for the creation of automated tests for Drupal code.
- **Coverage analysis:** PHPUnit generates reports that show how much of your Drupal code has been tested.
- **Integration with Drupal:** PHPUnit is integrated with Drupal's testing framework, making it easy to write and run tests for Drupal code.
- **Community support:** PHPUnit has a large community of developers who use it for testing Drupal code, providing many resources for learning and troubleshooting.
- **Best practices:** PHPUnit follows best practices for writing tests, such as using assertions to check code output, ensuring reliable and accurate tests.

#### How to install/setup phpunit? ####

To install PHPUnit with coverage, you can follow these steps:

1. **Install Composer:** PHPUnit is typically installed using Composer, a dependency manager for PHP. You can download and install Composer from the official website: https://getcomposer.org/.

2. Navigate to drupal project root directory.

3. **Require PHPUnit:** In the project directory, run the following command to require PHPUnit and its dependencies:

   $ **composer require --dev phpunit/phpunit:8.x**
   
   Run this **./vendor/bin/phpunit --version** command to verify PHPUnit version.
   
   **Note:** 8.x version supported by drupal 9 if you are using drupal 8 install 7.x.

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

#### How to setup phpunit for Drupal? ####

- We need to copy **php.xml.dist** file which is located in **core** folder of drupal, we will copy this file and paste it on Drupal root folder
rename it to **phpunit.xml** here are some more parameters that you may need to modify. We can use this [sample file](phpunit.xml).
- We need to create **simpltest & browser_output** directory & setting permissions for it. So follow below command to create dir.
  $ mkdir -p web/sites/simpletest/browser_output && chmod -R 777 web/sites/simpletest
- Once you have set up the phpunit.xml file and created your test files, you can run PHPUnit tests for your Drupal site using the following command from the root directory of your Drupal site.

  $ ./vendor/bin/phpunit web/core/modules/user/tests/src/Unit/UserRegistrationResourceTest.php (This is for verifying existing test files)
  
  $ ./vendor/bin/phpunit **--coverage-html html** web/modules/custom/custom_module/ (coverage-html generates coverage report)
  
**Note:** If you found these errors HP Fatal error:  Uncaught Error: Class 'Behat\Mink\Element\TraversableElement' not found in DocumentElement.php:24 & PHPUnit\Framework\Exception: This test uses TestCase::prophesize(), but phpspec/prophecy is not installed. So install these packages using below command.

$ composer require behat/mink && composer require --dev phpspec/prophecy
  









:house: [Home Page](README.md) | [<< Previous Page](database.md)
