Bugsnag Notifier for CakePHP
=======

This plugin allows you to use [Bugsnag](https://bugsnag.com) with CakePHP projects. Get notified when your application breaks and view detailed logs and stack traces on specific exceptions and errors.

The `BugsnagErrorHandler` class extends the default CakePHP `ErrorHandler` so the functions of the built in class continue to work.

Quick Start
---------

Use one of the following methods to include this library in your project.

1. [Install this plugin with Composer](#install-with-composer)
2. [Place the files](#install-by-placing)

Once you've included this library you should modify: `app/Config/core.php`. Make sure to enter your own API key.

```php
Configure::write('BugsnagCakephp.apikey', '{yourbugsnagapikey}');

Configure::write('Exception', array(
    'handler' => 'BugsnagErrorHandler::handleException',
    'renderer' => 'ExceptionRenderer',
    'log' => true
));

Configure::write('Error', array(
    'handler' => 'BugsnagErrorHandler::handleError',
    'level' => E_ALL & ~E_DEPRECATED,
    'trace' => true
));
```

And make sure the plugin is loaded by adding the following line to: `app/Config/bootstrap.php`.

```php
// place after the 'require' statement for the Bugsnag library.
App::uses('BugsnagErrorHandler', 'BugsnagCakephp.Lib');
```

Install with Composer
----

1.  Modify `composer.json` to include the following lines:

    ```json
    "require": {
      "label305/bugsnag-cakephp": "0.1.*"
    },
    ...
    "extra": {
        "installer-paths": {
            "app/Plugin/{$name}/": ["label305/bugsnag-cakephp"]
        }
    }
    ```

3.  And run `composer update`.

2. Require the Bugsnag PHP library in `app/Config/bootstrap.php`.

    ```php
    require ROOT . DS . 'vendor' . DS . 'bugsnag' . DS . 'bugsnag' . DS . 'build' . DS . 'bugsnag.phar';
    ```

Install by placing
---

1.  Place the files from this repository in `app/Plugin/BugsnagCakephp`

2.  Download the latest [bugsnag.phar](https://raw.github.com/bugsnag/bugsnag-php/master/build/bugsnag.phar)
    to your PHP project.

3.  Require it in `app/Config/bootstrap.php`.

    ```php
    require_once 'path' . DS . 'to' . DS . 'bugsnag.phar';
    ```
    
4. Make sure the php extention `mbstring` is installed.

License
---------
Copyright 2014 Label305 B.V.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
