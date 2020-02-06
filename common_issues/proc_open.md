# proc_open(): fork failed - Cannot allocate memory

Example:

    Installing magento/project-community-edition (2.3.2) - Installing magento/project-community-edition (2.3.2): Loading from cache

     Created project in arandomproject
    Loading composer repositories with package information
    Updating dependencies (including require-dev)

     Package operations: 422 installs, 0 updates, 0 removals - Installing magento/magento-composer-installer (0.1.13): Loading from cache

     proc_open(): fork failed - Cannot allocate memory

     The archive may contain identical file names with different capitalization (which fails on case insensitive filesystems)
    Unzip with unzip command failed, falling back to ZipArchive class

     The following exception is caused by a lack of memory or swap, or not having swap configured
    Check https://getcomposer.org/doc/articles/troubleshooting.md#proc-open-fork-failed-errors for details

     PHP Warning: proc_open(): fork failed - Cannot allocate memory in phar:///usr/bin/composer/vendor/symfony/console/Application.php on line 952
    Warning: proc_open(): fork failed - Cannot allocate memory in phar:///usr/bin/composer/vendor/symfony/console/Application.php on line 952

     [ErrorException]
     proc_open(): fork failed - Cannot allocate memory

## Suggested Fixes:

#### Upgrading PHP version

#### Reallocating additional swap

Refer to System administration [how-to-create-swapfile](how-to-/system_administrations/how-to-create-swapfile.md)

#### Adding more memory

#### Remove vendor directory to not build from cache (Do not do on production)

     rm -rf vendor/
     rm -rf composer.lock
     composer clear-cache
     composer install --prefer-dist
