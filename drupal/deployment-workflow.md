# Deployment workflow for Drupal

## Assumptions

- We are using git for vcs.
- We are using composer.
- We are deploying a Drupal 8+ version.
- **We have tested the update process locally or on a non Production server** using a copy of the Production database.
- There are some tests already passed (on DEV, STAGE environments only). Continue only if tests pass.
- We have a [drush alias](https://www.drush.org/latest/site-aliases) for each environment.
- No config changes exist on the live website. In some (bad) cases Authors or Admins can do changes on the configuration while on Production (eg translate Views). These config changes need to sync back to the development branch. An option is to export them on Prod (`drush cex`), commit them to git and then merge from the remote branch again. If we have config changes we are going to loose them due to `drush cim` if we do not export them.

## Deployment steps

> The steps can be done by a human or a Continuous Deployment (CD) system.
> The commands can be executed using drush site aliases.

1. Allocate time required for the deployment.
2. `drush sql:dump --gzip --result-file=/path-to-backup/mysite-$(date +%Y-%m-%d).sql` Get a backup of the database. Sometimes we need to take a backup of code, and public files too (a full backup).
3. `drush @mysite.myenv ssh` // ssh on the server for the specific website
4. `drush cex --diff` // See the Assumptions above. Assuming that there are no config overrides on Production.
5. `drush cset readonlymode.settings enabled 1 -y` (Enable **readonlymode** module related configuration)
6. `drush cset system.maintenance_mode 1 --input-format=integer` (Enable maintenance mode, see [D.O. Enabling and Disabling Maintenance Mode](https://www.drupal.org/docs/user_guide/en/extend-maintenance.html))
7. `git status` // Check if any file is overriden by mistake
8. `git pull origin XXX` (or `git checkout myTag` if using tags)
9. `drush updb` (so we disable any modules through hook_update_N that will not come from composer)
10. `composer install`
11. `drush updb`
12. `drush cim`
13. `drush cr`
14. `drush cset system.maintenance_mode 0 --input-format=integer` (Disable maintenance mode)
15. `drush cset readonlymode.settings enabled 0 -y` (Disable readonlymode settings)
16. Clear all external system caches (eg Varnish)

Modules used on the process above:

- <https://www.drupal.org/project/readonlymode>
