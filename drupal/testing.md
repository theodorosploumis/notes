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
- Send notifications

## Examples

What to test with a Drupal project:

- REST API (CRUD operations)
- REST API (Permissions)
- Functionality (eg module API, test functions)
- Permissions (eg a Druapl user can access a page)
- Integration (eg PHP versions, dependencies versions, Drupal core versions)
- UI (Expected behavior on a Drupal page)
- Code validation according to standards.
