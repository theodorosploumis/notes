# Drupal security updates

> Drupal security updates guide and best practices.

## Important things to know

- Drupal core and contrib modules security updates are maintained by the [Drupal security team](https://www.drupal.org/drupal-security-team).
- **Security release "windows" are every Wednesday for Drupal contributed projects, and one Wednesday a month (usually the third Wednesday) for Drupal core.** See more at [D.O.: Security release numbers and release timing](https://www.drupal.org/drupal-security-team/security-release-numbers-and-release-timing)
- For Drupal core the **bug fix/feature** release window is on the **first Wednesday of the month**.
- Security releases happen between 16:00 UTC and 22:00 UTC.
- D.O. Security updates list: <https://www.drupal.org/security>
- D.O. Security updates Twitter alerts: <https://twitter.com/drupalsecurity>

## When to do the updates

- Always use a maintenance window and a **shared calendar** (with the customer) to plan the updates. For example. you should not do the updates (even if there is a sec. issue) when the site is having a high traffic campaign.
- Prefer the same dates as Drupal core security releases. For example, **the third Wednesday of each month** is a good option to plan for updates.
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
