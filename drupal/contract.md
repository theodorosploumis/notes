# Drupal project maintenance contract

> Drupal Maintenance and Support contract template, tips and task lists. See also [drupal/security-updates](security-updates.md)

## Parameters to consider

- Drupal version
- Hosting
- Define the [Service Level Agreement (SLA)](https://uptime.is) for uptime
- Member accounts. If anonymous can create member accounts or sumbit data there are more security issues to take care of
- User permissions and roles
- 3rd party integrations (authentication, APIs, external js libraries etc). More integrations mean more issues
- Database size and increase factor
- Is there any migration happened from older Drupal versions?
- Website activity status (traffic, bandwidth, page impressions, peaks)
- Custom modules, plugins, code
- Multisite system
- eCommerce system. eCommerce needs special treatment and specific maintenance tasks
- Other special requirements (eg Government website)

---

## Common Drupal maintenance tasks

- Drupal core security updates (with dependencies)
- Drupal core minor version upgrade (eg 8.9.2 to 8.9.11)
- Contributed (D.O.) modules security updates
- Contributed (D.O.) themes security updates (base theme)
- 3rd party integrations updates (eg update an external API endpoint)
- Update a module when a patch that was applied before is commited to a stable branch
- Apply patches
- Database and entity updates
- Bug fixes
- Keep and restore offsite backups (db, public files, code)
- Define a disaster recovery plan
- Define a maintenance plan (who, when, what, how, costs)
- Support via phone call
- Support via email
- Support via online ticketing system (backlog)
- 24x7 support (including weekends and holidays)
- Security auditing
- Spam filtering and cleansing
- Malware filtering and cleansing
- System/infrastructure updates
- Response within 1/8/24/72 hr
- Hacked website repair
- Broken link scan
- Uptime monitoring
- Version control development (git) with 3 environments (dev, stage, prod) for QA testing
- Weekly/monthly reports
- Create a knowledge database (documentation) for maintenance tasks
- Cost ($/hr) for tasks not included on the maintenance contract
- Contract duration 6/12 months

---

## Statistics

The values here are just for reference, every project has its own complexity and functionality. Also, they refer only to major sucurity updates on core and contributed modules.

- A simple Drupal 8.x+ website without many contributed modules may need about **1hr per month**.
- A multisite installation of about 5 simple sites (as above) may need **3hr per month**.
- A complex Drupal 8.x+ website with many modules and integrations may need about **6hr - 10hr per month**.
- A simple Drupal 8.x commerce website may need **6hr per month**.
- A large Drupal 8.x website with User accounts and 3rd party integrations may need more than **10hr per month**.

---

## Maintenance plan

Here is a proposed maintenance plan for Drupal websites from AdciSolutions.
Some tasks may not refer to technical maintenance but keep here for reference (eg the SEO or PageSpeed optiomizations).

- Once a month on the first Wednesday of the month - update of the minor version of Drupal with fixed bugs. It may happen more often, it depends on the severity of the bugs.
- Once a month - on the **3rd Wednesday of the month** - check security releases in modules supported by the Drupal Community.
- Once a month and every time within 2 days after deployment - track errors through Google Analytics, logging systems and human QA.
- Once in 3 months - SEO.
- Once in 6 months - check compliance with the principles of accessibility.
- Once in 6 months - Google PageSpeed Insights optimization.
- Once in 6 months - update the Drupal minor version.
- Once in 6 months - refactor front end.
- Once a year - update PHP.
- Two weeks before the certificate expires, renew the SSL certificate (automatically or manually).
- Every time the site is updated - check custom code and check the functionality of the site.
- Every time the site is updated add the new values (eg Drupal and php version) on the internal Drupal Support Sheet file.
- Once a year update the Support Contract between your company and the customer (eg add/remove tasks, alter pricing etc)

---

## Drupal Maintanance offer example

| Task   | Plan A    | Plan B    | Plan C   |
| ------ | :-------: | :-------: | :-------:|
| Core security updates | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Core minor version upgrade | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Contributed modules & theme security updates | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Bug fixes due to existing code & infrastructure | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Version control development (dev, stage, prod) | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Support via email | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Support via phone call | - | - | :heavy_check_mark: |
| 24x7 support | - | - | :heavy_check_mark: |
| Response time | 24hr | 8hr | 2hr |
| Monthly report | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Contract duration | 12 month | 12 month | 12 month |
| Urgent tasks not included in contract | 35$/hr | 35$/hr | 30$/hr |
| **Cost $/yr** | **2000** | **3000** | **5000** |

---

## Drop Support Task list

Sometimes you need to take off a project and drop maintenance and support.
Here are the basic steps to follow to accomplish this.

### Backups

- Before anything please take a **full backup of the Production environment** (database, public files, code).

### Drupal

- Change User 1 email or create new Admin users for the new Company.
- Remove or change emails for any other Company accounts (non admin).
- Remove emails from Security Updates settings (email to get alerts).
- Change 3rd party credentials if exist (eg SOLR, Elastic etc).
- Remove your credentials from the website.

### DNS

- Remove any DNS record (Cloudflare etc) that point to specific `.mycompany.domain` development subdomains for this project.
- Delete any site aliases on the server that point to `.mycompany.domain` subdomains.

### Hosting

- Remove ssh keys and known_hosts entries.
- Remove all `.git` folders.
- Remove any development related credentials for this project (eg CI keys etc).
- Remove your email from the Hosting provider.

### Other

- Disable testing tools (eg GitHub actions, BitBucket Pipelines, CircleCI, Testing screenshots etc).
- Disable server health monitoring tool (if any).
- Archive project on Internal Project Manegement tool (tasks and issues).
- Update internal Docs and Support sheet.
- Check on your Company Blog section if there is a special reference to this project (eg a showcase) and edit accordingly.
- Discuss with the Team what was the reason to drop the project support.

---

## Resources

- <https://en.wikipedia.org/wiki/Service-level_agreement>
- <https://www.appnovation.com/services/drupal-development/support-maintenance>
- <https://opensenselabs.com/blog/articles/a-drupal-support-and-maintenance-guide>
- <https://www.drupaldevelopersstudio.com/drupal-support-maintenance>
- <https://www.drupalpartners.com/services/drupal-maintenance-and-support-company>
- <https://www.optasy.com/services/drupal-maintenance-support>
- <https://www.drupalaid.com>
- <https://ixis.co.uk/drupal/support>
- <https://maintainn.com/plans>
- <https://www.web-savvy-marketing.com/wordpress-consulting/wordpress-support-and-maintenance>
- <https://www.freelock.com/product/drupal-protection-plan>
- <https://www.adcisolutions.com/knowledge/importance-website-maintenance>
- <https://www.vardot.com/en-us/ideas/resources/support-maintenance-and-growth>
