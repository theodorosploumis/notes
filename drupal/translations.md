# Drupal Translation solutions

- Views: Replace the "Current row language" option on the "Translations" tab with the "Current Interface language" etc.

## Translations steps for Drupal website

- Install MYPROFILE with any modules
- Enable additional languages (non English)
- Go to the Translation UI (`/admin/config/regional/translate`) and add translations for strings
- Go to the Configuration Translations page (`/admin/config/regional/config-translation`) and add translations for
  configuration settings forms (this can - be also done for each form on the
  form page "translations" tab).
- When ready, export all po files for each language and add this under `mymodule/translations/mymodule.de.po`. The translation path `translations/mymodule.de.po` is set on `mymodule.info.yml`. Alternatively, use a pot file (template) to generate po translations. Example on
  <https://MY-ONLINE-REPOSITORY/MYPROFILE-platform/-/tree/master/web/modules/custom/MY_CUSTOM_MODULE/translations>
- When ready, export all config yml files and copy all the files under `config/sync/language` folders under your module/theme `config/install/language` folder. See example on <https://MY-ONLINE-REPOSITORY/MYPROFILE-platform/-/tree/master/web/modules/custom/MY_CUSTOM_MODULE/config/install/language>
- Data should be translated with CSV import or through the UI (menu link items, custom content blocks, nodes, taxonomy terms etc)

| **Type** | **Configuration** | **twig templates** |**module strings** | **drupal entities** |
| :---: | :---: | :---: | :---: | :---: |
| source | po, yml | po | po |csv |
| where | yml: Inside `install/language/LANG` folder, po: Inside `translations folder` | Inside `translations` folder | Inside `translations` folder | Inside custom migration module(s) |
| Translation server, service | yes (only po, potx files) | yes | yes | no |

## Complete solution requirements

1. Export (group of) translations to po, csv, xliff, yml, xlsx. mo, REST
2. Import (group of) translations from po etc
3. Sync (update)
4. Clean/remove translations in bulk with options
5. Export translation templates (potx)
6. Translations reports and status (overview page)
7. On page translations (popup style, in-place editor etc)
8. Translations suggestions (fuzzy)
9. Translations User accounts with Roles
10. Save translations data to a database (id, source, target, context,
    suggestion, author, tags, comment, status)
11. Merge translations
12. Override translations by context (eg for another module)
13. SEO valid
14. Option to NOT translate the backend for each installed language (?)

## Drupal API, functions

1. [locale.api.php](https://api.drupal.org/api/drupal/core%21modules%21locale%21locale.api.php/9.2.x)
2. [hook_locale_translation_projects_alter](https://api.drupal.org/api/drupal/core%21modules%21locale%21locale.api.php/function/hook_locale_translation_projects_alter/9.2.x)
3. [config_translation.api.php](https://api.drupal.org/api/drupal/core%21modules%21config_translation%21config_translation.api.php/9.2.x)
4. [hook_config_translation_info_alter](https://api.drupal.org/api/drupal/core%21modules%21config_translation%21config_translation.api.php/function/hook_config_translation_info_alter/9.2.x)
5. [Internationalization](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Language%21language.api.php/group/i18n/9.2.x)
6. [locale.compare.inc](https://api.drupal.org/api/drupal/core%21modules%21locale%21locale.compare.inc/9.2.x)
7. [Translation (class)](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Annotation%21Translation.php/class/Translation/9.2.x)

## Basic drush commands

```bash
# Installs profile in DE language only
drush si MYPROFILE --locale de -y

# Install profile in en
drush si MYPROFILE -y

# Default locale commands
drush locale:check, locale:update, locale:export, locale:import

# Example, import a po file from a local folder
drush locale:import de PATH_TO_DE_PO_FILE
drush locale:import nl modules/custom/MY_CUSTOM_MODULE/translations/MY_CUSTOM_MODULE.nl.po
drush cget system.site
drush config:set language.negotiation url.prefixes.el el
```

## Drupal modules for translations

- [config_import_locale](https://www.drupal.org/project/config_import_locale)
- [config_translation_access](https://www.drupal.org/project/config_translation_access)
- [config_translation_po](https://www.drupal.org/project/config_translation_po)
- [decoupled_interface_translations](https://www.drupal.org/project/decoupled_interface_translations)
- [interface_string_stats](https://www.drupal.org/project/interface_string_stats)
- [**l10n_client**](https://www.drupal.org/project/l10n_client)
- [l10n_quick_links](https://www.drupal.org/project/l10n_quick_links)
- [l10n_tools](https://www.drupal.org/project/l10n_tools)
- [l10n_update_bundled](https://www.drupal.org/project/l10n_update_bundled)
- [locale_override](https://www.drupal.org/project/locale_override)
- [locale_trans_file](https://www.drupal.org/project/locale_trans_file)
- [locale_translation_context](https://www.drupal.org/project/locale_translation_context)
- [mfd](https://www.drupal.org/project/mfd)
- [multilingual_audit](https://www.drupal.org/project/multilingual_audit)
- [po_translations_report](https://www.drupal.org/project/po_translations_report)
- [potion](https://www.drupal.org/project/potion)
- [**potx**](https://www.drupal.org/project/potx)
- [simple_entity_translations](https://www.drupal.org/project/simple_entity_translations)
- [simple_tmgmt](https://www.drupal.org/project/simple_tmgmt)
- [string_translation_ui](https://www.drupal.org/project/string_translation_ui)
- [**tmgmt**](https://www.drupal.org/project/tmgmt)
- [tmgmt_spreadsheet](https://www.drupal.org/project/tmgmt_spreadsheet)
- [tranc](https://www.drupal.org/project/tranc)
- [translate_set](https://www.drupal.org/project/translate_set)
- [translate_side_by_side](https://www.drupal.org/project/translate_side_by_side)
- [translate_tool](https://www.drupal.org/project/translate_tool)
- [translate_tool](https://www.drupal.org/project/translate_tool)
- [translated_config](https://www.drupal.org/project/translated_config)
- [translation_extractor](https://www.drupal.org/project/translation_extractor)
- [translation_form](https://www.drupal.org/project/translation_form)
- [views_entity_translations_links](https://www.drupal.org/project/views_entity_translations_links)
- [yaml_translation_import](https://www.drupal.org/project/yaml_translation_import)

## Translations sheet columns

The basic columns needed when translating using a Sheet (e.g. Google Sheets),

- location (where us the string coming from)
- source (the string to translate, always in English)
- target (the translated string)
- suggestion (fuzzy)
- context (a special key to distinct this translation from similar)
- comments
- updated (date)
- author (latest)

## Translation Process with external service

A. Translate

```bash
Translator → Google Sheets (xls) → csv → po (for non Entities) (OR)
Translator → l10n_server (or Service) → translate (manually or through the service API) → export to po file
```

B. Import to Projects

```bash
po → "/translations/PROJECT.LANGCODE.po" file each project root (git)
```

## Common translation issues

## Tools

1. [localize.drupal.org](https://localize.drupal.org) (official Drupal localize server)
2. [drupal.org/project/l10n_server](https://www.drupal.org/project/l10n_server)
3. [localizejs.com](https://localizejs.com/products/web) (translation service, on the fly translation through DOM)
4. [poeditor.com](https://poeditor.com/) (translation service)
5. [poedit.net](https://poedit.net/) (translation service)
6. [weblate.org](https://weblate.org/) (translation service)
7. [mlocati.github.io/jsgettext](https://mlocati.github.io/jsgettext) (Online convert from/to po, pot, mo)

## Scripts

1. [Gist: Convert .po files from Drupal7 to .yml for Drupal9](https://gist.github.com/Dimitris1990/0aabe4cabd0d12e0fbffccac1536ae9e)

## D.O related issues

1. [Configuration language being overwritten during module install](https://www.drupal.org/project/drupal/issues/2905295)
   (2905295)
1. [Translated Config Override should default to original language values if there are no translations](https://www.drupal.org/project/drupal/issues/2993984)
   (2993984)
1. [Add string context and location filters to the translate interface](https://www.drupal.org/project/drupal/issues/2123543)
   (2123543)
1. [Regression: not possible to delete source strings in Drupal 8 interface translation](https://www.drupal.org/project/drupal/issues/2503893)
   (2503893)
1. [META: Modernize Locale module](https://www.drupal.org/node/3215707)
   (3215707)

## Documentation

1. [drupal.org/docs/8/api/translation-api/overview](https://www.drupal.org/docs/8/api/translation-api/overview)
2. [drupal.org/community/contributor-guide/reference-information/localize-drupal-org/working-with-offline/po-and](https://www.drupal.org/community/contributor-guide/reference-information/localize-drupal-org/working-with-offline/po-and)
3. [drupal.org/docs/7/multilingual/translating-site-interfaces/contribute-a-translation-to-localizedrupalorg](https://www.drupal.org/docs/7/multilingual/translating-site-interfaces/contribute-a-translation-to-localizedrupalorg)
4. [api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Language%21language.api.php/group/i18n](https://api.drupal.org/api/drupal/core!lib!Drupal!Core!Language!language.api.php/group/i18n/)
5. [api.drupal.org/api/drupal/core!modules!locale!locale.api.php/group/interface_translation_properties/8.2.x](https://api.drupal.org/api/drupal/core!modules!locale!locale.api.php/group/interface_translation_properties/8.2.x)
