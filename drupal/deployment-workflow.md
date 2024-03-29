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
3. Login as Admin on the live website. This is needed because sometimes you may need to act imeddiately through the UI if something stragne happen.
4. `drush @mysite.myenv ssh` // ssh on the server for the specific website
5. `drush cex --diff` // See the Assumptions above. Assuming that there are no config overrides on Production.
6. `drush cset readonlymode.settings enabled 1 -y` or `drush readonlamode:set 1` (Enable **readonlymode** module related configuration)
7. `drush cset system.maintenance_mode 1 --input-format=integer` OR (drush 11.5+) `drush maint:set 1` (Enable maintenance mode, see [D.O. Enabling and Disabling Maintenance Mode](https://www.drupal.org/docs/user_guide/en/extend-maintenance.html))
8. `git status && git log` // Check if any file is overriden by mistake
9. `git pull origin XXX` (or `git checkout myTag` if using tags)
10. `drush updb` (so we disable any modules through hook_update_N that will not come from composer)
11. `composer install` // Or if we do have a good development setup and we know that any dev package is not required: `composer install --no-dev --no-script`
12. `drush updb`
13. `drush cim`
14. `drush cr`
15. `drush cset system.maintenance_mode 0 --input-format=integer` OR (drush 11.5+) `drush maint:set 0` (Disable maintenance mode)
16. `drush cset readonlymode.settings enabled 0 -y` or `drush readonlamode:set 0` (Disable readonlymode settings)
17. Clear all external system caches (eg Varnish)
18. Check Drupal report status (`admin/reports/status`) for any missed errors.

Modules used on the process above:

- <https://www.drupal.org/project/readonlymode>

## ssh config example

```ini
# ~/.ssh/config
Host gh-backend
    HostName github.com
    User git
    IdentityFile "~/.ssh/id_rsa_github_backend"
Host gh-frontend
    HostName github.com
    User git
    IdentityFile "~/.ssh/id_rsa_github_frontend"
```
