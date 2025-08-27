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

### Resources

- [Drupal.org IDE Documentation](https://www.drupal.org/docs/develop/development-tools)
- [Drupal Coding Standards](https://www.drupal.org/docs/develop/standards)
- [PhpStorm Drupal Tutorial](https://confluence.jetbrains.com/display/PhpStorm/Drupal+Development+using+PhpStorm)
- [VS Code Drupal Setup Guide](https://www.drupal.org/docs/develop/development-tools/configuring-visual-studio-code)
