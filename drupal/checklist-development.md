# Drupal 9.x Project Development Checklist

A checklist of common tools, settings, modules etc to check for a Drupal 9.x web project

> Want to use a **Docker** image for development? Head to <https://github.com/theodorosploumis/gitpod-drupal-workspace>!

**How to use this?**
I usually copy this checklist to a Github issue so I won't forget anything.
Most of the times I delete items from the list so this is the full list.

## Server type

- [ ] Ubuntu LTS, stable (eg 22.04)

## Server setup

Prefer to install all software globally.

- [ ] php8 (see [required php extensions](https://drupal.org/docs/8/system-requirements/php-requirements) for drupal 9.x)
- [ ] mysql
- [ ] apache2
- [ ] git
- [ ] patch
- [ ] [drush-launcher](https://github.com/drush-ops/drush-launcher)
- [ ] [composer](https://getcomposer.org)
- [ ] openssh-server(ssh/sftp)
- [ ] nodejs/npm (if needed)
- [ ] Caching (eg memcache, redis etc)
- [ ] Backups (files, db, all)
- [ ] DNS (2 domains, STAGE and PRODUCTION)

## Dev Packages (if needed)

- [ ] [sass-lang.com](https://sass-lang.com/)

## SaaS

- [ ] Create Github/Bitbucket/Gitlab repository
- [ ] Create Project Management project (eg Jira, Redmine etc)
- [ ] Create a Trello board (if using Trello)
- [ ] Setup Slack
- [ ] Setup CI (eg Travis)
- [ ] Setup CD (eg GitHub Actions)

## Drupal Settings

ToDo: See template for **settings.php**.

- [ ] Enable dev mode
- [ ] Enable php error_log
- [ ] Enable apache2 error_log
- [ ] Copy ssh keys
- [ ] Setup private and public files folders and permissions
- [ ] Logging system and alerts (eg on Slack)

## Modules/Themes

See [Drupal favorite modules](favorites.md).

## Site Architecture

- [ ] Content types
- [ ] Vocabularies
- [ ] Entity Fields
- [ ] Blocks
- [ ] Menus and menu links
- [ ] View modes
- [ ] User Roles
- [ ] Views
- [ ] Text editor filters
- [ ] Text editor widgets/plugins
- [ ] Image styles
- [ ] REST pages
- [ ] Site functionality (eg search, mailchimp etc)
- [ ] New things to try (eg a new tool)

## Testing

- [ ] User Scenarios/Stories
- [ ] Test UI functionality (behat)
- [ ] Test user permissions (PhpUnit)
- [ ] Test user input (behat)
- [ ] Test browsers (browserstack etc)
- [ ] Test devices (mobile, tablet, desktop)
- [ ] [W3C WAI level 1 accessibility validation](https://validator.w3.org/)
- [ ] [Google Mobile Friendly](https://www.google.com/webmasters/tools/mobile-friendly/) test
- [ ] [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/) test
- [ ] [Pingdom Website Speed Test](http://tools.pingdom.com/fpt/)
- [ ] [Yellow Lab Tools](https://yellowlab.tools)

## Development tasks

- [ ] Create Project folder
- [ ] Create drush aliases
- [ ] git-flow init
- [ ] Setup **cron jobs**
- [ ] Set xdebug
- [ ] IDE setup (eg Phpstorm)
- [ ] Create [teamocil](https://github.com/remi/teamocil) file
- [ ] Create bash aliases
- [ ] Create basic docker images needed (eg for testing or local development)
- [ ] Create ddev/lando setup
- [ ] Create gitpod setup

## After development tasks

- [ ] Disable modules: *_ui, dblog, devel, admin_menu, simplytest, kint.
- [ ] Enable Caches
- [ ] Enable syslog module
- [ ] Provide customer credentials
- [ ] Maintenance agreement
- [ ] Submit to SE (eg Google), use xmlsitemap
- [ ] Submit to [Google Analytics](https://analytics.google.com)
- [ ] Submit to [Google Webmaster tools](https://www.google.com/webmasters/tools)
- [ ] Submit to Showcase sites
- [ ] Publish on my personal site (work)
- [ ] Publish any Open source project that can be useful
