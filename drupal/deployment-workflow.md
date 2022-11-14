# Deployment workflow for Drupal

## Assumptions

- We are using git for vcs.
- We are using composer.
- We are deploying a Drupal 8+ version.
- There are some tests already passed (on DEV, STAGE environments only). Continue only if tests pass.

## Deployment steps

> The steps can be done by a human or a Continuous Deployment (CD) system.

1. Allocate time required for the deployment.
2. Get a backup of the database, code, and public files (a full backup).
3. `drush cset readonlymode.settings enabled 1 -y` (Enable **readonlymode** module related configuration)
4. ssh on live server
5. `drush cset system.maintenance_mode TRUE` (Enable maintenance mode)
6. `git pull` (or `git checkout mytag1` if using tags)
7. `drush updb` (so we disable any modules through hook_update_N that will not come from composer)
8. `composer install`
9. `drush updb`
10. `drush cim`
11. `drush cr`
12. `drush cset system.maintenance_mode FALSE` (Disable maintenance mode)
13. `drush cset readonlymode.settings enabled 0 -y` (Disable readonlymode settings)

Modules used on the process above:

- <https://www.drupal.org/project/readonlymode>
