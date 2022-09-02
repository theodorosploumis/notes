# Exclude Modules on Configuration

As of [Drupal 8.8.0](https://www.drupal.org/node/3079028) we can exclude whole module configuration from export/import.
This is a way to have different modules enabled on each environment (Dev, Stage, Prod etc) although they share the same drupal configuration.

When you run `drush cim` or `drush cex` the excluded modules will not sync and their settings will remain unchanged.

## Important Notices

- The same `$settings['config_exclude_modules']` should exist **on all the environments (local or online)**. Not only on Dev.
- When you import/export the **whole Configuration** to/from an environment from the Drupal Configuration Sync page (`/admin/config/development/configuration`) the `$settings['config_exclude_modules']` works too.
- If you want to **enable or disable or change settings of a module you can still do this through the UI**. UI is not affected by the exclusion list. But the configuration will not be exported later on.
- When you import the **whole Database** to an environment the `$settings['config_exclude_modules']` does not exclude any module or configuration. But when you run `drush cim/cex` it will work exclude these modules again. So basically, if you copy the whole database you need to manually add/remove these modules again.
- Need to use drush 10+.
- D.O. docs say:

```php
/**
 * Exclude modules from configuration synchronization.
 *
 * On config export sync, no config or dependent config of any excluded module
 * is exported. On config import sync, any config of any installed excluded
 * module is ignored. In the exported configuration, it will be as if the
 * excluded module had never been installed. When syncing configuration, if an
 * excluded module is already installed, it will not be uninstalled by the
 * configuration synchronization, and dependent configuration will remain
 * intact. This affects only configuration synchronization; single import and
 * export of configuration are not affected.
 *
 * Drupal does not validate or sanity check the list of excluded modules. For
 * instance, it is your own responsibility to never exclude required modules,
 * because it would mean that the exported configuration can not be imported
 * anymore.
 *
 * This is an advanced feature and using it means opting out of some of the
 * guarantees the configuration synchronization provides. It is not recommended
 * to use this feature with modules that affect Drupal in a major way such as
 * the language or field module.
 */
```

## Example

Here is an example of such a setting on `settings.php` file:

```php
$settings['config_exclude_modules'] = [
  'page_cache',
  'dynamic_page_cache',
  'devel',
  'kint',
  'stage_file_proxy',
  'backup_migrate',
  'reroute_email',
  'automated_cron',
  'dblog',
  'dynamic_page_cache',
  'page_cache',
  'big_pipe',
  'shield',
  'advagg',
  'advagg_bundler',
  'advagg_cdn',
  'advagg_validator',
  'advagg_ext_minify',
  'advagg_css_minify',
  'advagg_js_minify',
  'advagg_mod',
  'advagg_old_ie_compatibility',
];
```

## Resources

- <https://www.drupal.org/node/3079028>
- <https://drupal.stackexchange.com/q/291639/12163>
- <https://drupal.stackexchange.com/q/188817/12163>
