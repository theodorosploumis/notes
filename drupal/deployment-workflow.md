# Deployment workflow for Drupal

## Assumptions

- We are using git for vcs.
- We are using composer.
- We are deploying a Drupal 8+ version.
- There are some tests already passed (on DEV, STAGE environments only). Continue only if tests pass.
- We have a [drush alias](https://www.drush.org/latest/site-aliases) for each environment.

## Deployment steps

> The steps can be done by a human or a Continuous Deployment (CD) system.
> The commands can be executed using drush site aliases.

1. Allocate time required for the deployment.
2. Get a backup of the database, code, and public files (a full backup). // ToDo: Add the Drush command for that
3. `drush @mysite.myenv ssh` // ssh on the server for the specific website
4. `drush cset readonlymode.settings enabled 1 -y` (Enable **readonlymode** module related configuration)
6. `drush cset system.maintenance_mode TRUE` (Enable maintenance mode)
7. `git pull` (or `git checkout mytag1` if using tags)
8. `drush updb` (so we disable any modules through hook_update_N that will not come from composer)
9. `composer install`
10. `drush updb`
11. `drush cim`
12. `drush cr`
13. `drush cset system.maintenance_mode FALSE` (Disable maintenance mode)
14. `drush cset readonlymode.settings enabled 0 -y` (Disable readonlymode settings)

Modules used on the process above:

- <https://www.drupal.org/project/readonlymode>
