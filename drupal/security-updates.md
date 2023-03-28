# Drupal security updates

> Drupal security updates guide and best practices.


## Important things to know

- Drupal core and contrib modules security updates are maintained by the [Drupal security team](https://www.drupal.org/drupal-security-team).
- **Security release "windows" are every Wednesday for Drupal contributed projects, and one Wednesday a month (usually the third Wednesday) for Drupal core.** See more at [D.O.: Security release numbers and release timing](https://www.drupal.org/drupal-security-team/security-release-numbers-and-release-timing)
- For Drupal core the **bug fix/feature** release window is on the **first Wednesday of the month**.
- For Drupal core the **security** release window on the **third Wednesday of the month**.
- Security releases happen between 16:00 UTC and 22:00 UTC.
- D.O. Security updates list: <https://www.drupal.org/security>
- D.O. Security updates Twitter alerts: <https://twitter.com/drupalsecurity>

## When to do the updates

- Always use a maintenance window and a **shared calendar** (with the customer) to plan the updates. For example. you should not do the updates (even if there is a sec. issue) when the site is having a high traffic campaign.
- Prefer the same dates as Drupal core security releases. For example, **the third Wednesday of each month** is a good option to plan for updates otherwise go for **the very next Monday**.
- ASAP when the security issue is of high priority.
- Do not do the updates late on the day (at least 4 hours before leaving the office) or on the last day of the week (eg Friday).
- Try to do the updates when all the related parts are active (developers, sysadmin, hosting provider, customer etc)
- Do not plan for updates then other systems (eg the Hosting Provider) is also having a maintenance window.

## Best practices

- Security updates should be done as a "**first level task**" and not as a minor boring task.
- During the update the developer(s) should always follow all the steps even if you are sure they are not needed.
- During the update the developer(s) should not be tired, doing multitasking, talking on the phone etc.
- During the update the developer(s) should not be on a hurry when doing the sec. updates.
- After the update the developer(s) should monitor the site for some time and be ready to revert/act if anything happens (eg for 1 day).
- Demand a **content freeze** during the updates (you can use the module [readonlymode](https://www.drupal.org/project/readonlymode) or the core **maintenance_mode** variable for that).
- Decide the **Maintenance windows** (date or range of dates).
- Use a **Maintenance windows calendar** (a calendar shared with the parts evolved where the site owner should mention which dates should not be an option for security updates).
- Send **Maintenance emails** before and after the update (inform the customer about the **upcoming** update, inform the customer about the update **happened**).
- Create a **technical report** about each update (git tag/commit, Drupal core, Drupal contrib versions, PHP packages versions). You can use tools like [generate_drupal_report](https://github.com/theodorosploumis/generate_drupal_report).
- Add **datetime to bash history** so each cli command has a datetime entry.
- Use a special **cli color when ssh on a Production server** (eg make it with red background).
- Allow for emergency **system rollback** from the UI (code, database, public files). This is needed in cases where an error occur after a sec. update and there is lack of communication between the sec. team and the site owner.
- First complete the sec. updates on a **full copy of the Prod site (code, db, public files, same server config)** before doing the same on Prod.
- Establish a **manual (UAT) testing** guide to allow the customer check the updates.
- Establish a **clean plan about the responsibilities**. Who is going to have each responsibility, which are the communication options (email, phone etc), which are the tasks need to be done when a problem arise etc.
- If there are **many companies or vendors evolving** be careful about any misunderstands and delays that may happen due to the number of the people evolved.
- Developers and other parts evolved should update a **shared checklist** for all the steps required.

## Updating Drupal distributions (installation profiles)

> For example [open social](https://www.drupal.org/project/social) [opigno_lms](https://www.drupal.org/project/opigno_lms) etc.

- Some distributions (e.g. Open Social) already have a recommended process to run updates and sometimes there is also a UI for updates. Follow that guide instead of yours.
- Prefer to use a **strict version** of the distribution on `composer.json`.
- Let the distribution handle the 2nd level requirements (eg Drupal modules) and **don't override them on `composer.json`** unless there is a reason to do so.
- Before any update please read carefully the distribution changelog and notes.
- Check your current version of the distribution (the `composer.json` of it) with the new version you want to update to. This will allow you to inspect which packages and settings have changed on the new `composer.json`.
- If there are conflicts on updates try to delete the `composer.lock` before upadating.
- If there are conflicts on updates read the composer logs carefully and then try to fix each problem line by line.
- Command `composer why X` is your friend.
- It is a good practice to not leave your projects that depend on a Drupal distribution without updates for a long time.
- It is a good practice to get informed (e.g. through Drupal RSS or GitHub watch) about new releases of the Drupal distribution you depend to.


## Monitor site health

- Uptime monitoring (external SASS, eg [uptimerobot](https://uptimerobot.com), [New Relic](https://newrelic.com))
- Get SMS and email alerts for PHP fatal errors on Drupal

## UAT examples for Drupal

- View a node (for each bundle)
- Edit a node (for each bundle)
- View a list (views)
- User login works
- Webform submissions work
- Search works
- Cron task works
- SMTP and mail system works
- There are no JS errors on console

## Related guides

- [Drupal report](https://github.com/theodorosploumis/drupal-report)
- [Generate drupal report script](https://github.com/theodorosploumis/generate_drupal_report)
- [Notes: Drupal Contract](contract.md)
- [Notes: Deployment workflow for Drupal](deployment-workflow.md)
- [Notes: Testing Drupal](testing/README.md)
