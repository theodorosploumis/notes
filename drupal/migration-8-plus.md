# Migrations from 8.x to any latest major version

> Notes about migrating a Drupal 8.x or 9.x website to 10.x+. The same approach works for any future migration from a Drupal 8+ project.

## Commands

```bash
# Install upgrade_status module
composer install --dev
composer require drupal/upgrade_status --dev

# Check custom modules for deprecated code
composer require phpunit/phpunit:"7.*" --dev
composer require mglaman/drupal-check --dev
drupal-check -d web/modules/custom

# Enable module and test upgrades
drush en -y upgrade_status
drush upgrade_status:analyze --all

# If no module need to be updated test core upgrade
# Every project not compatible will disallow the upgrade in composer
rm -rf vendor web/core web/modules/contrib composer.lock
composer require drupal/core-recommended:^10.0

# If there are available 10.x readiness patches apply them with composer
# If there are not patches available create them manually or
# download these modules in modules/custom folder
# Otherwise you can use the drupal-lenient endpoint. See https://dgo.to/3240297
composer config repositories.lenient composer https://packages.drupal.org/lenient

# If there are modules or themes to fix use rektor or drupal-check to fix them
# Install drupal-check globally
composer global require mglaman/drupal-check

# And finally... install
composer install

# Take a db backup
...

# Run db updates
drush updb

# Check drupal logs for warning and fix them

# Disable upgrade_status
drush pmu -y upgrade_status
```

## Tips

- Modules that do have patches for 10.x compadibility require 8.x core so they cannot apply through composer! You can download these modules as 'custom' and apply there any patches.
- For the problem above you can also use the Drupal **lenient** endpoint so you allow patches to be applied. See <https://dgo.to/3240297> and <https://github.com/mglaman/composer-drupal-lenient>.
- You may need `dev` versions for several modules.
- Some of the major drupal modules may not have 10.x support.
- If you do the same process for other environments (eg from `dev` to `stage`) don't forget to run `drush updb` after the first `composer install`. Otherwise the `drush cim` may cause errors like `The base theme stable cannot be uninstalled, because theme classy depends on it`.

## References

- [drupal/upgrade_status](https://www.drupal.org/project/upgrade_status)
- [drupal/rector](https://www.drupal.org/project/rector)
- [mglaman/drupal-check](https://github.com/mglaman/drupal-check)
- [Change records for Drupal core 9.0.x](https://www.drupal.org/list-changes/drupal/published?to_branch=9.0.x)

## Articles

- <https://dev.acquia.com/blog/how-prepare-your-drupal-8-site-move-drupal-9>
- <https://www.drupal.org/docs/upgrading-drupal/how-to-prepare-your-drupal-7-or-8-site-for-drupal-9>
- [Preparing Drupal.org projects for Drupal 9](https://www.drupal.org/node/3053183)
- <https://drupalize.me/tutorial/upgrade-drupal-9>
- <https://www.drupal.org/docs/develop/using-composer/using-drupals-lenient-composer-endpoint>

## db updates example

```bash
-----------------------------------------------------------
  Module           Update ID
  migrate_drupal   Add revision ID to entity reference translation migrate_map tables
  system           entity_revision_metadata_bc_cleanup
  system           uninstall_classy
  system           uninstall_entity_reference_module
  system           uninstall_simpletest
  system           uninstall_stable
```
