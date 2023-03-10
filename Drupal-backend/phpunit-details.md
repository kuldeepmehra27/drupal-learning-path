
#### What is prophecy? ####

Prophecy is a testing tool for Drupal that is used to write unit tests for modules. It allows developers to define the behavior of **mock objects** using a simple and expressive syntax, making it easier to write and maintain tests. Prophecy is often used in combination with other testing tools in the Drupal ecosystem to ensure that modules work correctly and don't have unexpected interactions with other parts of the system.

[Using prophecy in Drupal](https://www.drupal.org/docs/automated-testing/phpunit-in-drupal/using-prophecy)

#### What is Mocking Object in PHPUnit? ####

Mocking objects in PHPUnit involves creating objects that **simulate/replicate the behavior of real objects for testing purposes**. This can be useful for isolating code and controlling the behavior of dependencies. PHPUnit provides a built-in mocking framework to create mock objects and define their behavior, helping developers write more robust tests and catch issues early in the development process.

#### What is mean by coverage or code coverage in PHPUnit? ####

Code coverage in PHPUnit is a **measure of how much of your code is covered by automated tests. It shows which lines of code were executed during a test run and which lines were not**, providing a report that helps you identify areas of your code that are not being tested. Code coverage is an important metric for assessing the quality of your tests.

#### What is assertion in PHPunit? ####

In PHPUnit, **assertions are methods that verify expected results during the execution of a test** by comparing actual values produced by the code with expected values. PHPUnit provides a range of assertion methods that can be used to test different types of values, and using assertions helps to catch issues early in the development process by providing useful information when tests fail.

1. **assertTrue($condition)** - Checks if a given condition is true.

   Example: $this->assertTrue($result > 0);

2. **assertFalse($condition)** - Checks if a given condition is false.

   Example: $this->assertFalse(empty($array));

3. **assertEmpty($value)** - Checks if a value is empty.

   Example: $this->assertEmpty($result);
   
4. **assertNotEmpty($value)** - Checks if a value is not empty.

   Example: $this->assertNotEmpty($result);
   
5. **assertArrayHasKey($key, $array)** - Checks if an array has a given key.

   Example: $this->assertArrayHasKey('name', $result);
   
6. **assertEquals($expected, $actual)** - Checks if two values are equal.

   Example: $this->assertEquals(42, $result);
   
7. **assertNotEquals($expected, $actual)** - Checks if two values are not equal.

   Example: $this->assertNotEquals(0, count($array));
   
8. **assertInstanceOf($expected, $actual)** - Checks if an object is an instance of a given class.

   Example: $this->assertInstanceOf(MyClass::class, $result);
   
9. **assertNotInstanceOf($expected, $actual)** - Checks if an object is not an instance of a given class.

   Example: $this->assertNotInstanceOf(MyClass::class, $result);
   
10. **assertIsArray($value)** - Checks if a value is an array.

    Example: $this->assertIsArray($result);

[Check this link](https://docs.phpunit.de/en/9.5/assertions.html) for more details.

#### What is setup() Method? ####

setUp() is a method in PHPUnit that is **called before each test method and is used to set up the test environment** and prepare objects for the test. It is used to perform repetitive tasks required for each test case method, like initializing objects or connecting to databases.

  ![Setup](/images/setup.png)

#### ContainerBuilder() ####

ContainerBuilder is a class in Drupal used to **manage the dependency injection container**, which holds and manages objects and services throughout the application. It is used to define and register services, set parameters, and manage dependencies.

#### \Drupal::setContainer() ####

\Drupal::setContainer() is a static method in Drupal **that sets the global service container**, which holds and manages objects and services throughout the application, for the current request. It allows developers to replace the default container with a custom implementation created using the ContainerBuilder class. 

#### Argument::any() ####

Argument::any() is a PHPUnit method that lets you indicate a placeholder value for an argument in a mocked method call. This is useful **when you want to match any value for the argument (Regardless pass argument)** and do not care about its specific value.

#### @covers ####

@covers is a PHPUnit annotation used to explicitly specify which code is being covered by a test method. It can be used to ensure that code coverage reports accurately reflect the code being tested, but may require updates whenever the code being tested is refactored or updated.

#### @codeCoverageIgnore ####

In PHPUnit, @codeCoverageIgnore is an annotation that can be used to exclude a method or class from being included in the code coverage report. It can be used at the class level to exclude all methods within a class, or at the method level to exclude a specific method. This annotation is useful for testing code that cannot be easily covered by automated tests, but should be used with caution as it can obscure areas of the codebase that are not being tested.

   ![Code coverage ignore](/images/code-coverage-ignore.png)
   
#### @codeCoverageIgnoreStart and @codeCoverageIgnoreEnd ####

@codeCoverageIgnoreStart and @codeCoverageIgnoreEnd are annotations used in PHPUnit to **exclude specific sections of code** from being included in the code coverage report. These annotations mark the beginning and end of the code block to be ignored and can be useful when testing code that interacts with external dependencies or contains debug or experimental code.
  
   ![code coverage ignore start end](/images/coverage-ignore-start-end.png)

#### @dataProvider ####

In PHPUnit, @dataProvider is used to specify a method **that provides data to a test method**. The data provider method should return an array of arrays or an Iterator object where each item is an array containing the data for each test case. The test method is executed once for each set of data provided by the data provider method, and the arguments of the test method are set to the values of the array items.

   ![Data provider](/images/Data-provider.png)

#### tearDown() ####

The teardown method (also known as tearDown()) is a method defined in a test class that is executed automatically after each test method in the class has been run. **Its purpose is to clean up any resources or reset any state changes made during the test method**, ensuring that subsequent test methods are not affected by the previous test method. The tearDown() method is used to perform various cleanup tasks such as closing database connections, removing temporary files, resetting global variables, or restoring a system configuration, to ensure a clean and consistent environment for each test method.

  ![Data provider](/images/teardown.png)


:house: [Home Page](README.md) | [<< Previous Page](phpunit.md) | [Next Page >>](phpunit-examples.md)

