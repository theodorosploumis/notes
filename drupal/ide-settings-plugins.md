# IDE Settings and Plugins for Drupal Development

## Overview

This guide covers IDE configurations, plugins, and settings optimized for Drupal development across popular IDEs and editors.

## PhpStorm

### Essential Plugins

**Drupal-Specific:**
- [Drupal Support](https://plugins.jetbrains.com/plugin/7487-drupal-support) - Core Drupal support with code completion and inspections
- [Symfony Support](https://plugins.jetbrains.com/plugin/7219-symfony-support) - Essential for modern Drupal (built on Symfony)
- [Composer Support](https://plugins.jetbrains.com/plugin/7631-composer) - Composer integration
- [Twig Support](https://plugins.jetbrains.com/plugin/7303-twig) - Twig template engine support

**Code Quality:**
- [PHP Inspections (EA Extended)](https://plugins.jetbrains.com/plugin/7622-php-inspections-ea-extended-) - Advanced PHP inspections
- [PHP Annotations](https://plugins.jetbrains.com/plugin/7320-php-annotations) - Better annotation support
- [Deep Assoc Completion](https://plugins.jetbrains.com/plugin/9927-deep-assoc-completion) - Array completion
- [PHP Toolbox](https://plugins.jetbrains.com/plugin/8133-php-toolbox) - Additional PHP tools

**Development Workflow:**
- [DDEV Integration](https://plugins.jetbrains.com/plugin/18813-ddev-integration) - DDEV local development
- [String Manipulation](https://plugins.jetbrains.com/plugin/2162-string-manipulation) - Text manipulation tools
- [AceJump](https://plugins.jetbrains.com/plugin/7086-acejump) - Quick navigation
- [Code With Me](https://plugins.jetbrains.com/plugin/14896-code-with-me) - Collaborative coding

### PhpStorm Configuration

#### File Templates
Add Drupal-specific file templates:

**Drupal Module (.info.yml):**
```yaml
name: ${MODULE_NAME}
type: module
description: '${DESCRIPTION}'
package: Custom
core_version_requirement: ^9 || ^10 || ^11
dependencies:
  - drupal:node
```

**Drupal Service (.services.yml):**
```yaml
services:
  ${MODULE_NAME}.${SERVICE_NAME}:
    class: Drupal\${MODULE_NAME}\${CLASS_NAME}
    arguments: ['@entity_type.manager', '@current_user']
```

#### Code Style Settings
- **Settings → Code Style → PHP**
  - Set to "Drupal" coding standards
  - Enable "Use 'use' for classes from the current namespace"
  - Set array formatting to align values

#### Live Templates
Add custom live templates for Drupal:

```php
// Drupal hook implementation
/**
 * Implements hook_$HOOK$().
 */
function $MODULE$_$HOOK$($PARAMETERS$) {
  $END$
}

// Drupal service injection
public function __construct($PARAMETERS$) {
  parent::__construct($PARAMETERS$);
  $END$
}
```

### Settings Recommendations

**Editor → General:**
- Enable "Show whitespaces"
- Set tab size to 2 spaces
- Enable "Ensure line feed at file end on Save"

**Inspections:**
- Enable all Drupal-specific inspections
- Configure PHPDoc inspections for Drupal standards

## Visual Studio Code

### Essential Extensions

**Drupal-Specific:**
- [Drupal Syntax Highlighting](https://marketplace.visualstudio.com/items?itemName=marcostazi.VS-code-drupal) - Drupal file support
- [Twig Language 2](https://marketplace.visualstudio.com/items?itemName=mblode.twig-language-2) - Twig syntax highlighting
- [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) - YAML support for .info.yml files

**PHP Development:**
- [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client) - PHP intelligence
- [PHP DocBlocker](https://marketplace.visualstudio.com/items?itemName=neilbrayfield.php-docblocker) - DocBlock generation
- [PHP Debug](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug) - Xdebug integration

**Code Quality:**
- [PHP CS Fixer](https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer) - Code formatting
- [PHPStan](https://marketplace.visualstudio.com/items?itemName=swordev.phpstan) - Static analysis

### VS Code Settings

#### settings.json
```json
{
  "php.suggest.basic": false,
  "php.validate.enable": false,
  "intelephense.stubs": [
    "bcmath",
    "bz2",
    "Core",
    "curl",
    "date",
    "dom",
    "fileinfo",
    "filter",
    "gd",
    "gettext",
    "hash",
    "iconv",
    "json",
    "libxml",
    "mbstring",
    "mcrypt",
    "mysql",
    "mysqli",
    "password",
    "pcntl",
    "pcre",
    "PDO",
    "pdo_mysql",
    "Phar",
    "readline",
    "regex",
    "session",
    "SimpleXML",
    "sockets",
    "sodium",
    "standard",
    "superglobals",
    "tokenizer",
    "xml",
    "xdebug",
    "xmlreader",
    "xmlwriter",
    "yaml",
    "zip",
    "zlib",
    "wordpress",
    "drupal"
  ],
  "intelephense.environment.includePaths": [
    "web/core",
    "web/modules",
    "web/themes"
  ],
  "[php]": {
    "editor.defaultFormatter": "junstyle.php-cs-fixer"
  },
  "emmet.includeLanguages": {
    "twig": "html"
  }
}
```

#### Code Snippets
Add Drupal snippets via **Preferences → Configure User Snippets → php.json:**

```json
{
  "Drupal Hook": {
    "prefix": "hook",
    "body": [
      "/**",
      " * Implements hook_${1:hook_name}().",
      " */",
      "function ${2:module_name}_${1:hook_name}($3) {",
      "  $4",
      "}"
    ],
    "description": "Drupal hook implementation"
  },
  "Drupal Service": {
    "prefix": "service",
    "body": [
      "/**",
      " * ${1:Service description}.",
      " */",
      "class ${2:ServiceClass} {",
      "",
      "  /**",
      "   * Constructor.",
      "   */",
      "  public function __construct($3) {",
      "    $4",
      "  }",
      "",
      "}"
    ],
    "description": "Drupal service class"
  }
}
```

## Sublime Text

### Essential Packages

Install via Package Control:
- **Drupal** - Drupal syntax highlighting and snippets
- **PHP-Twig** - Twig template support
- **SublimeLinter-php** - PHP linting
- **Composer** - Composer support
- **YAML Nav** - YAML file navigation

### Sublime Text Settings

#### Preferences.sublime-settings
```json
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true,
  "ensure_newline_at_eof_on_save": true,
  "trim_trailing_white_space_on_save": true,
  "rulers": [80],
  "word_wrap": false
}
```

## Vim/Neovim

### Essential Plugins

**Plugin Manager:** Use vim-plug, Vundle, or Packer

**Drupal-Specific:**
- [vim-drupal](https://github.com/arnested/vim-drupal) - Drupal syntax and detection
- [phpcomplete-extended](https://github.com/m2mdas/phpcomplete-extended) - Enhanced PHP completion

**General PHP:**
- [vim-php-namespace](https://github.com/arnaud-lb/vim-php-namespace) - PHP namespace utilities
- [phpactor](https://github.com/phpactor/phpactor) - PHP language server

### Vim Configuration

#### .vimrc additions
```vim
" Drupal coding standards
autocmd FileType php setlocal expandtab shiftwidth=2 tabstop=2 softtabstop=2
autocmd FileType yaml setlocal expandtab shiftwidth=2 tabstop=2 softtabstop=2
autocmd FileType twig setlocal expandtab shiftwidth=2 tabstop=2 softtabstop=2

" Drupal file detection
augroup drupal
  autocmd!
  autocmd BufRead,BufNewFile *.module set filetype=php
  autocmd BufRead,BufNewFile *.install set filetype=php
  autocmd BufRead,BufNewFile *.theme set filetype=php
  autocmd BufRead,BufNewFile *.inc set filetype=php
  autocmd BufRead,BufNewFile *.info.yml set filetype=yaml
augroup END
```

## General IDE Configurations

### Code Style Settings

**For all IDEs, configure:**
- **Indentation:** 2 spaces (no tabs)
- **Line endings:** LF (Unix)
- **Character encoding:** UTF-8
- **Max line length:** 80 characters
- **Trailing whitespace:** Remove on save
- **Final newline:** Ensure present

### File Associations

Configure proper syntax highlighting for Drupal files:
- `.module` → PHP
- `.install` → PHP
- `.theme` → PHP
- `.inc` → PHP
- `.info.yml` → YAML
- `.libraries.yml` → YAML
- `.routing.yml` → YAML
- `.services.yml` → YAML
- `.twig` → Twig/HTML

### Debugging Configuration

#### Xdebug Setup
Configure Xdebug for step-through debugging:

**php.ini:**
```ini
[Xdebug]
xdebug.mode=debug
xdebug.start_with_request=yes
xdebug.client_port=9003
xdebug.client_host=localhost
xdebug.log=/tmp/xdebug.log
```

### Recommended Tools Integration

**DDEV Integration:**
- Configure IDE to recognize DDEV's PHP interpreter
- Set up remote debugging through DDEV
- Use DDEV's built-in tools (PHPMyAdmin, Mailhog)

**Drush Integration:**
- Configure Drush path in IDE
- Set up Drush command shortcuts
- Enable Drush autocomplete

**Composer Integration:**
- Enable Composer dependency management
- Configure autoloading paths
- Set up dependency inspection

## IDE-Specific Drupal Features

### PhpStorm Advanced Features

**Database Integration:**
- Connect to Drupal database
- Enable SQL dialects for Drupal
- Query console integration

**HTTP Client:**
- Test Drupal REST APIs
- JSON:API endpoint testing
- Authentication headers setup

### VS Code Drupal Workflow

**Task Integration:**
- Configure Drush tasks
- Set up build tasks for themes
- Enable terminal integration

**Git Integration:**
- Configure Git hooks for Drupal
- Enable commit message templates
- Branch management for features

## Performance Optimization

### Memory Settings
Increase IDE memory allocation for large Drupal projects:
- **PhpStorm:** `idea.vmoptions` → `-Xmx4096m`
- **VS Code:** Adjust `files.watcherExclude` for node_modules
- **Vim:** Configure `set maxmempattern=5000`

### Indexing Optimization
Exclude unnecessary directories:
- `node_modules/`
- `vendor/`
- `web/sites/default/files/`
- `.git/`
- Build directories (`dist/`, `build/`)

## Team Development Standards

### Shared Configurations
Store team IDE configurations in project:
- `.vscode/settings.json` for VS Code
- `.idea/` directory for PhpStorm (selective commits)
- `.editorconfig` for cross-IDE consistency

### Code Quality Integration
- **PHP_CodeSniffer:** Configure Drupal standards
- **PHPStan:** Set up Drupal-specific rules
- **ESLint:** Configure for Drupal JavaScript
- **Stylelint:** Set up for Drupal CSS/SCSS

## Troubleshooting

### Common Issues

**PHP Path Issues:**
- Verify PHP interpreter path
- Check Composer global bin directory
- Ensure Drush launcher is accessible

**Namespace Resolution:**
- Clear IDE caches
- Rebuild autoload files
- Check include paths configuration

**Performance Issues:**
- Exclude large directories from indexing
- Increase memory allocation
- Disable unused plugins/extensions

### Resources

- [Drupal.org IDE Documentation](https://www.drupal.org/docs/develop/development-tools)
- [Drupal Coding Standards](https://www.drupal.org/docs/develop/standards)
- [PhpStorm Drupal Tutorial](https://confluence.jetbrains.com/display/PhpStorm/Drupal+Development+using+PhpStorm)
- [VS Code Drupal Setup Guide](https://www.drupal.org/docs/develop/development-tools/configuring-visual-studio-code)

---

> **Note:** This document focuses on defensive development tools and configurations. Always verify that plugins and extensions are from trusted sources before installation.