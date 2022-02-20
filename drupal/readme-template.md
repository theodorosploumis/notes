# Project example.com

> A README template for a new (Drupal) project. Should probably be commited to git!

|  Key  | Value  |
| :--------------  | :------------------------------------- |
| -- **Customer** -- | **Customer name here**                 |
| Website          | [customer.example.com](https://customer.example.com)  |
| Contacts         | `Customer name here and maybe email`   |
| -- **Agency** -- | **NAME OF THE AGENCY HERE**            |
| Website          | [theodorosploumis.com](https://www.theodorosploumis.com) |
| Contacts         | Theodoros Ploumis                      |
| -- **Project** --| **`Project title here with Drupal version`** |
| Dates (development) | 01/01/2021 - 31/10/2021 |
| PM/Tasks         | `link to your online PM tool here`        |
| Wiki             | `link to your online Wiki tool here`      |
| Chat channel     | `link to your Chat tool here (eg Slack)`  |
| Git repository   | [git@bitbucket.org:example/example.git](https://bitbucket.org/example/example) |
| Server           | `link to your Server provider or dashboard here` |
| DNS | `link to your DNS provider or dashboard here`  |
| SMTP | `link to your DNS provider or dashboard here` |
| Site: dev branch    | http://dev.example.com (webroot `/home/www-data/example.com/dev/web`)     |
| Site: stage branch  | http://stage.example.com (webroot `/home/www-data/example.com/stage/web`) |
| Site: master branch | http://prod.example.com (webroot `/home/www-data/example.com/prod/web`)   |
| Htpasswd         | `link to your Password provider or file here` |
| Drupal admin     | `link to your Password provider or file here` |
| Database dump UI | `No UI, use only cli` |
| CI/CD dashboard  | `link to CI/CD dashboard or settings files here`|
| Contributors     | `Add the humans (Names, emails etc) that worked for this Project` |

## About

A basic introduction about this project...

## Setup

Details about setup and installation

### Installation

Install normally. Select "Install Drupal form existing configuration" option.

### Settings & Environmental Variables

Examples and notes about settings.php files and configuration.

## Development & Deployment

Example of steps.

1. Always have a fresh **working** copy of the repository.
2. Download a fresh database backup from the server and import it to your local environment. Alternatively, use drush commands to sync.
3. Export configuration **immediately** and commit what makes sense, eg: config that could have been changed by the client.
4. Do your magic!
5. Export configuration **again** to include your **new** changes and commit it.
6. Push to Bitbucket/GitHub/Gitlab: **dev** branch.
7. **Visit `/en/admin/config/development/configuration` to import configuration.**
8. **Run DB updates!**
9. Verify all is ok.
10. Merge **dev** to **stage** to trigger a deployment to the Stage site and **run steps 7 and 10** again for the Stage site.

## Online workflow commands

```
ssh ...
cd [ROOT_PATH]
git pull
composer install
drush updb
cd web
drush cim
drush cr
```

### Database commands

```
// Export db
mysqldump db_name > backup-file.sql

// Import db
mysql db_name < backup-file.sql
mysql -p -u [user] [database] < backup-file.sql
```

### Development (Dev) Site

Details about development instance (if exists).

Show information about: ssh, url, drush site-alias, htaccess credentials etc.

### Preview (Stage) Site

Details about staging instance (if exists).

### Production Site

Details about production instance.

## Other notes

