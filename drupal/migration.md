# Migration to Drupal

> A basic of tips, best practices and resources about migration to Drupal.

## Prepare for migration

Most of the times you need to create a report about the site/source that will be migrated to Drupal.

If you are going to migrate from an old (7.x or less) Drupal site and need to generate a Report please check [drupal-report](https://github.com/theodorosploumis/drupal-report).

## Tips

- **Before starting get an overview** (as an anonymous user) of the webpages that will be migrated (eg following the Main menu). Doing this you will get an idea of what content types and widgets exist on the site. Eg if there are many images or links to internal files inside text fields will require a custom HTML persing.
- Generate a sheet of the entities, fields etc to be migrated.
- Use always the **migrate_plus** module.
- Always create and enable a custom module that will contain any **custom migration plugins** and initial **configuration**.
- Migrate only data, not settings or other special configuration (eg avoid migrating permissions, site settings, node settings etc).
- Don't rely on existing core (or contrib) yml files. Always clone and override these to your custom module to be able to alter it later.
- Some core yml files use many other migrations as dependencies. Keep things simple and create a custom migration Plugin instead of using many migrations.
- Every migration is unique and not generic and refers to a specific website but prefer a generic custom module name to allow easy copy - paste of files for future migrations.
- Create Groups of migrations that are supposed to run together (eg Paragraphs) and create the same entities on the new website.
- Always try to run migrations from cli (drush) and not the UI.
- Create several Views on the old website (that will be migrated) if it is built on Drupal that allows you to get an overview of the old data and have a UI when testing (Nodes, Users, Paragraphs, Fields, Menu links etc).
- Document the custom module with a README file (mappings, process, drush commands, what to excpect, dependencies, manual process, database credentials example etc).
- While developing the migrations import and export configuration continuously until you get the results you expect. When the experiments are finished copy the final yml files back to the custom module (after removing key `_core`). Or better use the [config_devel](https://www.drupal.org/project/config_devel) module).
- Before migrating private files it is required to copy them to the new website (on the private folder) using rsync or any other similar tool.
- If there is a multilingual node migration to happen use a custom field to keep information about the old nid (eg an integer field) to allow you better testing.
- Be careful when migrating Drupal 7.x (or 6.x) websites that have asymmetric field values (eg Paragraphs).
- When migrating from old Drupla versions (eg 7.x) be careful with some **special field**s. For example the `vid` (revision id) and `uuid` fields most of the times cause issues (this is because Drupal itself is adding such data on each table by default when creating an entry so overriding these through migration might cause entity API errors). Thngs getting worse when the old site is `multilingual` and has a process to keep `revisions`.
- If you want to skip a migration row you have to `return FALSE;` on the `function prepareRow(Row $row)`.
- If you want to get real distinct rows (eg only 1 row with the same title) do not try to do this on the `query()` function but on the `prepareRow(Row $row)` function. Function `query()` usually returns error when running the migration due to the mysql restrictions.
- If you need to get data from html tags or massage html content use the PHP `DOMDocument` library.
- When you create demo content on Stage Environment and then run migrations again with update you may have unsxpected results because the new migrated ids may exist and will be skipped.
- After migration is run on the Production website uninstall all the migration related modules.
- Search on [Drupal.org code](https://git.drupalcode.org/search?search=migration_dependencies&project_id=59858&group_id=2) for migration yml files before creating your custom one.
- Search on Drupal.org for contributed modules related to a special migration (eg Media) before creating your custom one.

## Testing migrations

- Random test some old `/node/NID` paths exist on the new website.
- For a multilingual website an old node that is not the translation source should have a new nid.
- Test an old node of type X that references some Paragraphs of type Y do have the same Paragraphs on the new website.
- Test path aliases exist.
- Test menu links exist.
- Test files exist.
- Test field values of Paragraph X exist (this needs a database lookup or a custom Views to inspect).
- Test language of the website (redirect) when visiting as anonymous user (check if redirect follows the user browser).
- Test node translation form: add
- Test node translation form: edit
- Test node translation form: delete
- Test node translation form: unpublish (should hide the equivalent menu link and language switch link)
- Test node: add translation, update moderation state, revert revisions etc

## References

Notice: The references were added for the 9+ version.

- [Drupal.org Docs - Migrate API](https://www.drupal.org/docs/drupal-apis/migrate-api)
- [drupalmigrate.org](https://drupalmigrate.org)
- [Migration modules](https://drupalmigrate.org/search/modules)
- [migrate_tools drush commands](https://www.drupal.org/node/1561820)
- [Drupal core migrate yml files, 1](https://git.drupalcode.org/project/drupal/-/tree/10.0.x/core/modules/node/src/Plugin/migrate/source)
- [Drupal core migrate yml files, 2](https://git.drupalcode.org/project/drupal/-/tree/10.0.x/core/modules/node/migrations)
- [Migrate Drupal from 8.x to 10.x](migration-8-plus)

## Useful modules to install

- [migrate_tools](https://www.drupal.org/project/migrate_tools)
- [migrate_plus](https://www.drupal.org/project/migrate_plus)
- [migrate_devel](https://www.drupal.org/project/migrate_devel)

## DB example for migration

```php
// This is an example of a migration database settings.
// The key "migrate" is the default.
$databases['migrate']['default'] = array (
  'database' => 'drupal7',
  'username' => 'drupal7',
  'password' => 'drupal7',
  'prefix' => '',
  'host' => 'database.7x-website.host',
  'port' => '3306',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' => 'mysql',
);
```

## Drupal structure to investigate on

- Nodes
- Blocks
- Taxonomy terms
- Menus
- Media/Files
- Paragraphs
- field_group
- field_collection
- Views
- Forms (webforms etc)
- Special fields
- Multilingual
- Text editors and options
- User roles & permissions
- Users
- JS libraries used
- Search
- Sitemap
- Authoring tools

## Migration "source" plugins list

Notice: The list is not complete and may depends on several contributed modules and not only core.

If you want to get your current project **migrate source plugin** list run:

```bash
drush ev "print_r(array_keys(\Drupal::service('plugin.manager.migrate.source')->getDefinitions()));"
```

```txt
block
d6_block_translation
d7_block_translation
d6_box
d6_box_translation
d7_block_custom
d7_block_custom_translation
d6_field_instance_per_form_display
d6_field_instance
d6_field_instance_option_translation
d6_field_instance_per_view_mode
d6_field
d6_field_instance_label_description_translation
d6_field_option_translation
d7_field_instance_per_form_display
d7_field_instance
d7_view_mode
d7_field_instance_per_view_mode
d7_field
d7_field_instance_label_description_translation
d7_field_option_translation
d6_file
d6_upload_instance
d6_upload
d7_file
d6_filter_format
d7_filter_format
d6_imagecache_presets
d7_image_styles
menu_link
d6_menu_link_translation
d7_menu_link_translation
d7_menu_link_localized
empty
embedded_data
md_empty
variable
content_entity:block_content
content_entity:file
content_entity:media
content_entity:menu_link_content
content_entity:node
content_entity:path_alias
content_entity:redirect
content_entity:taxonomy_term
content_entity:user
d8_config
variable_multirow
d6_variable_translation
d7_variable_translation
url
table
d6_node
d6_view_mode
d6_node_revision
d6_node_complete
d6_node_type
d7_node
d7_node_revision
d7_node_complete
d7_node_type
d7_node_entity_translation
d6_url_alias
d7_url_alias
d7_path_redirect
d6_path_redirect
menu
action
d7_theme_settings
d7_menu_translation
extension
d6_taxonomy_vocabulary_translation
d6_term_node
d6_taxonomy_term
d6_term_localized_translation
d6_term_node_revision
d6_taxonomy_vocabulary
d6_taxonomy_vocabulary_per_type
d7_taxonomy_term_translation
d7_taxonomy_vocabulary_translation
d7_taxonomy_term
d7_term_localized_translation
d7_taxonomy_term_entity_translation
d7_taxonomy_vocabulary
update_settings
user_picture_instance
profile_field
d6_profile_field_option_translation
d6_user_picture
d6_profile_field_values
d6_user_picture_file
d6_user_role
d6_user
d7_user_entity_translation
d7_user_role
d7_user
pathauto_pattern
```

## Migration "process" plugins list

Notice: The list is not complete and may depends on several contributed modules and not only core.

If you want to get your current project **migrate process plugin** list run:

```bash
drush ev "print_r(array_keys(\Drupal::service('plugin.manager.migrate.process')->getDefinitions()));"
```

```txt
array_build
array_pop
array_shift
block_plugin_id
block_region
block_settings
block_theme
block_visibility
callback
concat
convert_tokens
d6_field_field_settings
d6_field_file
d6_field_instance_defaults
d6_field_instance_option_translation
d6_field_option_translation
d6_field_type_defaults
d6_imagecache_actions
d6_path_redirect
d6_profile_field_option_translation
d7_field_instance_defaults
d7_field_instance_option_translation
d7_field_instance_settings
d7_field_option_translation
d7_field_settings
d7_field_type_defaults
d7_path_redirect
d7_redirect_source_query
debug
default_entity_value
default_value
dom
dom_apply_styles
dom_migration_lookup
dom_remove
dom_select
dom_str_replace
download
entity_exists
entity_generate
entity_lookup
entity_value
explode
extract
field_bundle
field_formatter_settings_defaults
field_instance_widget_settings
field_link
field_settings
field_type
file_blob
file_copy
file_uri
filter_format_permission
filter_id
filter_settings
flatten
format_date
forum_vocabulary
gate
get
link_options
link_uri
log
machine_name
mailsystem_modules
make_unique_entity_field
menu_link_parent
merge
migration_lookup
multiple_values
node_complete_node_lookup
node_complete_node_revision_lookup
node_complete_node_translation_lookup
null_coalesce
path_set_translated
process_field
profile_field_settings
route
service
shield_paths
single_value
skip_on_404
skip_on_empty
skip_on_value
skip_row_if_not_set
static_map
str_replace
substr
sub_process
target_bundle
timezone
transpose
urlencode
user_langcode
```

## Migration code examples

- TBD
