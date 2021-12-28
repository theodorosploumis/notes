# Drupal Testing and CI/CD

> A simple structure of testing tasks and tips for Drupal.

## Testing

- Speed test (lighthouse score)
- Functional testing
- UI testing with behat
- JS testing with nightwatch, cypress etc
- Browser support testing
- A11y testing
- Stretch test (jmeter, artillery, k6 etc)
- Unit testing
- Add testing results budges to README
- Send notifications

## CI/CD

- Build docker image
- Update Gitpod workspace docker image (prebuild, if exists)
- Create a git release with Release.txt (eg on GitHub)
- Deploy on STAGE/PRODUCTION etc
- Generate a sanitized database backup from Production
- Get screenshots (eg for different devices and screen sizes)
- Send notifications

## Examples

What to test with a Drupal project:

- dev\* and \*\_ui modules are disabled on Production
- A user for Role X can submit a node form
- New site can be installed from configuration and/or demo content
- REST API (CRUD operations)
- REST API (get Nodes single, list, filtering, pager)
- REST API (get Views)
- REST API (get Blocks)
- REST API (get Configuration values)
- REST API (get Settings variables)
- REST API (stress test)
- REST API (security test)
- REST API (Permissions)
- Functionality (eg module API, test functions)
- Permissions (eg a Druapl user can access a page)
- Integration (eg PHP versions, dependencies versions, Drupal core versions)
- UI (Expected behavior on a Drupal page)
- Code validation according to standards
- Entity fields machine name patterns
- Broken JS functionality
- CKEditor buttons exist
- System: can create a new release/tag
- System: take a Prod database backup
- System: sanitize database
- System: rollback site to a snapshot
- drupal_rector & upgrade_status report
