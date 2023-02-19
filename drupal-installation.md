#### To install Drupal using Composer, follow these steps (Linux) ####
1. Make sure that Composer is installed on your system. You can check this by running the command **composer --version** in your command line interface.

2. Create a new directory for your Drupal project and navigate to it in your command line interface.

3. Run the following command to create a new Drupal project using Composer:
```
$ composer create-project drupal/recommended-project my-site
```
Note: If you want to install a specific version, please mention that version. like this **drupal/recommended-project:^9.0.0**

This will create a new Drupal project in a directory called my-drupal-project using the latest recommended version of Drupal.

4. Once the project has been created, navigate into the new directory by running the following command:
```
$ cd my-site
```
5. Run the following command to install Drupal's dependencies:
```
$ composer install
```
This command will install Drupal and its remaining dependencies, excluding any development dependencies.

6. Next, create a new MySQL database for your Drupal site and grant a user access to it. You'll need to know the database name, username, password, and host to complete the next step.

You should now have a fully functional Drupal installation in the my-site directory. You can access it by visiting http://localhost/my-site/ in your web browser.

#### To install Drupal using Composer, In root directory ####

1. Run the following command to create a new Drupal project using Composer:
```
composer create-project drupal/recommended-project:^9.0.0 my-site --no-interaction --no-install
```
2. Now open the **composer.json** file and remove the word **web** everywhere and specify **"web-root": "."** to current directory/path.

3. Navigate into the new directory by cd command and run composer install:
```
$ cd my-site && composer install
```
Rest of same as above.

**Note:** If you want to create a virtual host, use this [script file](https://github.com/kuldeepmehra27/drupal-learning-path/blob/master/virtual-host.sh) to create the virtual host. Copy this file
into **html** directory and follow instruction mentioned on top of script file.

[Drupal official document link](https://www.drupal.org/docs/develop/using-composer/manage-dependencies)
