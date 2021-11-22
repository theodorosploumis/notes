# Deployment workflow for Drupal
> Assuming we are using git, composer and STAGE/PROD servers. The steps can be done by a human or a CD system.

1. Get a backup of the database
2. ssh on server
3. git pull (or `git checkout mytag1` if using tags)
4. drush updb (so we disable any modules through hook_update_N that will not come from composer)
5. composer install
6. drush updb
7. drush cim
8. drush cr
