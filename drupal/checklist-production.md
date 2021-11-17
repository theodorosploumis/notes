# Drupal production checklist

An example of a simplified checklist for a Drupal website launch.
Current example includes migration tasks from a 7.x website to 9.x.
The steps bellow are not mandatory and their order is not strict.

## Checklist

### 1. Setup
- [ ] Other: Define the datetime for the launch to happen.
- [ ] Merge git branch stage to master (Pull Request)
- [ ] `git pull && composer install --no-dev && drush cim -y && drush updb`
- [ ] Drupal: Content freeze (usually on stage website)
- [ ] Server: Fix permissions for translations folder and update translations
- [ ] Drupal: Update project translations `/admin/reports/translations/check`
- [ ] Drupal: Set private folder (if need to)
- [ ] Drupal: Force unique subdomain redirect (force www or non-www)
- [ ] Drupal: Fix settings.php warnings
  - [ ] trusted host patterns
  - [ ] simplei (drupal module settings)
  - [ ] private files

### 2. Migrations
- [ ] Server: Copy public files from 7.x
- [ ] Server: Copy db from Stage to Prod (except if there is no new content on stage)
- [ ] Drupal: Execute final migrations (from the frozen production 7.x db)
- [ ] Drupal: Disable all migration related modules.
  - [ ] custom_migrate_\* (current site custom migrations)
  - [ ] migrate_plus
  - [ ] migrate_tools
  - [ ] migrate_upgrade
  - [ ] migrate_drupal
  - [ ] migrate_ui
  - [ ] migrate

### 3. Clean up
- [ ] Drupal: Remove old Super Admin users
- [ ] Drupal: Remove demo Nodes and content

### 4. Production prepare
- [ ] Server: Add cron jobs
- [ ] Drupal: Disable displaying errors on screen
- [ ] Drupal: Disable modules used on development except if they are needed.
  - [ ] devel
  - [ ] kint
  - [ ] vardumper
  - [ ] email_reroute
  - [ ] stage_file_proxy
  - [ ] shield
  - [ ] views_ui
  - [ ] field_ui
  - [ ] webform_ui
- [ ] Drupal: Enable Caching modules and set performance.
  - [ ] page_cache (core)
  - [ ] dynamic_page_cache (core)
  - [ ] big_pipe (core)
  - [ ] advagg
  - [ ] http_cache_control
  - [ ] quicklink
  - [ ] http_override_headers
  - [ ] lazy
  - [ ] minifyhtml
  - [ ] critical_css
- [ ] Drupal: Enable dblog and check for mass php errors, 404 errors etc
- [ ] Drupal: Download a complete whole archive of the new website (code, database, public files)

### 5. GDPR
- [ ] GDPR: Remove IP tracking on Webforms
- [ ] GDPR: Remove IP tracking on dblog
- [ ] GDPR: Add cookies banner

### 6. Updates
- [ ] Drupal: Run cron several times to index on Search or sitemap
- [ ] Drupal: Update sitemap.xml and inform the Search Engines about it
- [ ] Drupal: Rebuild content permissions

### 7. Production
- [ ] Server: Change DNS
- [ ] Drupal: Test all forms to send emails (if set to)
- [ ] Other: Update LastPass passwords and links
- [ ] Server: Move old 7.x site to a protected new subdomain

### 8. After launch
- [ ] Other: Give all the required passwords to the customer
- [ ] Other: Give all the required files and manuals to the customer, provide education
- [ ] Other: Sing a Support contract with the customer
- [ ] Other: Update project Documentation and internal company Documentation
- [ ] Other: Generate internal report for company. Examples.
  - [ ] Google page speed results (compared to the old website)
  - [ ] new/interesting drupal modules used
  - [ ] issues we solved
  - [ ] patches applied
  - [ ] tasks time estimations that were wrong
  - [ ] findings about Drupal or other used services
  
### 9. Sales/Promotion
- [ ] Promotion: Write helpful Blog post(s) about the project
- [ ] Promotion: Ask for a customer testimonial
- [ ] Promotion: Add project to the website portfolio


## Resources

- https://www.drupal.org/project/production_checklist
- https://github.com/alehkot/drupal-launch-checklist
- https://github.com/meSingh/product-launch-checklist
- https://www.vardot.com/en-us/ideas/resources/website-project-pre-post-launch-checklists
