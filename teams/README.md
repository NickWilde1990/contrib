# GETTING STARTED

[Drupal Documentation](https://www.drupal.org/documentation )

The examples in this documentation uses path "/var/www/html/drupal8.dev" and
virtual host "drupal8.dev", you should substitute as necessary.

## COMPOSER


### Install composer and create a new Drupal site

[Using Composer To Manage Drupal Dependencies](https://www.drupal.org/docs/develop/using-composer/using-composer-to-manage-drupal-site-dependencies )

For a quick and easy start that will install Drupal Console, Drush and PHPUnit
try [Option A: drupal-composer/drupal-project](https://github.com/drupal-composer/drupal-project )

### Update Drupal core

```
/var/www/html/drupal8.dev $ composer update drupal/core --with-dependencies
```

### Import a Drupal module

```
/var/www/html/drupal8.dev $ composer require drupal/<module_name\>
```

### Update a Drupal module

```
/var/www/html/drupal8.dev $ composer update drupal/<module_name\>
```

## DRUPAL CONSOLE

If you created your Drupal site using composer, Drupal Console and Drush
will already be installed. If not, you can install Console using Composer.

[Install Drupal Console Using Composer](https://docs.drupalconsole.com/en/getting/composer.html)

[Online Documentation](https://hechoendrupal.gitbooks.io/drupal-console/content/en/index.html)

### Setup developer mode

```
/var/www/html/drupal8.dev $ cp web/sites/default/default.services.yml web/sites/default/services.yml
/var/www/html/drupal8.dev $ cp web/sites/example.settings.local.php web/sites/settings.local.php
/var/www/html/drupal8.dev $ drupal site:mode dev
```

Uncomment the code following this comment in web/sites/default/settings.php
```
* Load local development override configuration, if available.
```

## DRUSH

[Documentation](http://docs.drush.org/en/8.x/ )

## CODING STANDARDS

[Drupal Coding Standards](https://www.drupal.org/docs/develop/standards)

[Drupal Coder Project](https://www.drupal.org/project/coder)

### Install/Configure Coder

[Installing Coder Sniffer](https://www.drupal.org/node/1419988)

```
/var/www/html/drupal8.dev $ composer global require drupal/coder
/var/www/html/drupal8.dev $ composer global require dealerdirect/phpcodesniffer-composer-installer
/var/www/html/drupal8.dev $ sudo ln -s /home/admin/.composer/vendor/squizlabs/php_codesniffer/scripts/phpcs /usr/bin/phpcs
/var/www/html/drupal8.dev $ file /usr/bin/phpcs
/var/www/html/drupal8.dev $ sudo ln -s /home/admin/.composer/vendor/squizlabs/php_codesniffer/scripts/phpcbf /usr/bin/phpcbf
/var/www/html/drupal8.dev $ file /usr/bin/phpcbf
/var/www/html/drupal8.dev $ phpcs --config-set installed_paths /home/admin/.composer/vendor/drupal/coder/coder_sniffer
```

### Usage - check code

```
/var/www/html/drupal8.dev/web/modules $ phpcs --standard=Drupal mymodule > mymodule.diff
```

### Usage - fix code

`/var/www/html/drupal8.devweb/modules $ phpcbf --standard=Drupal mymodule > mymodule.fix`

_Note_: Use caution with phpcbf, commit code first to ensure you can rollback if necessary.

[Drupal Markdown Coding Standards](https://www.drupal.org/docs/develop/coding-standards/markdown-coding-standards) are yet to be confirmed


