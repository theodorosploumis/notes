# Deployment workflow for Drupal

> Assuming we are using git, composer and STAGE/PROD servers. The steps can be done by a human or a CD system.

1. Get a backup of the database and/or code
1. `drush config-set readonlymode.settings enabled 1 -y` (Enable **readonlymode** module related configuration)
1. ssh on live server
1. `drush sset system.maintenance_mode TRUE` (Enable maintenance mode)
1. `git pull` (or `git checkout mytag1` if using tags)
1. `drush updb` (so we disable any modules through hook_update_N that will not come from composer)
1. `composer install`
1. `drush updb`
1. `drush cim`
1. `drush cr`
1. `drush sset system.maintenance_mode FALSE` (Disable maintenance mode)
1. `drush config-set readonlymode.settings enabled 0 -y` (Disable readonlymode settings)

Modules used:

- https://www.drupal.org/project/readonlymode
