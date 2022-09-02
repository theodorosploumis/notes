# Deployment workflow for Drupal

> Assuming we are using git, composer and STAGE/PROD servers. The steps can be done by a human or a CD system.

1. Get a backup of the database
2. ssh on server
3. `drush sset system.maintenance_mode TRUE` (Enable maintenance mode)
4. `git pull` (or `git checkout mytag1` if using tags)
5. `drush updb` (so we disable any modules through hook_update_N that will not come from composer)
6. `composer install`
7. `drush updb`
8. `drush cim`
9. `drush cr`
10. `drush sset system.maintenance_mode FALSE` (Disable maintenance mode)
