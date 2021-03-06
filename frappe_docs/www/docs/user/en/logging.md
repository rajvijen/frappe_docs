---
add_breadcrumbs: 1
title: Logging
image: /assets/frappe_io/images/frappe-framework-logo-with-padding.png
metatags:
  description: >
    Overview of the out of the box logs in Frappe
---

# Logging

Logging events can significantly improve the debugging experience. Frappe's development and production environments come with logging capabilities out of the box.

There's two main categories of logs based on accessibility. Desk Logs, which are stored in your site database and can be accessed and queried as Documents and the Server Logs, that are stored in files managed by a Log Rotation system.


## Desk Logs

Logs that can be accessed via the Desk UI _(generally searched for, from the [Awesomebar](/docs/user/en/desk#awesomebar))_. These track the operational events generally; but you can utilize their APIs to track about anything from your Frappe apps.

Some of the logs in the `Core` module are:

- [Access Log](https://docs.erpnext.com/docs/user/manual/en/using-erpnext/access-log)
- [Activity Log](#activity-log)
- [Error Log](https://frappe.io/blog/development/better-error-logging-with-frappe)
- [Scheduled Job Log](#scheduled-job-log)


You can find more information about them from the embedded links. The best way to find out more about each of them is checking them out directly on your site.


## Server Logs

Server Logs generally consist of lower level, transactional data as compared to those accessible from Desk. From Version 13, logs are available at site level too. These site logs are created by the Frappe Application, while many of the bench level log files are generated by the processes that support your Frappe environment. From your bench folder, you may find logs under:

- `./logs`
- `./sites/{site}/logs`

At the time of writing this, only `frappe.web.log` and `scheduler.log` are logged at site and bench-level. At bench level, some of the most useful files could be:

- `bench.log`
- `scheduler.log`
- `worker.log`

Tracking the bench commands executed, status of the jobs run by your [Scheduler](/docs/user/en/tutorial/task-runner#scheduled-tasks) or [Background Jobs](/docs/user/en/guides/app-development/running-background-jobs) can be found in these logs.

> Note: To enable Frappe Web Logging on your site, update the site config with `enable_frappe_logger`: true

### Processes

Server Logs may be generated by the [bench CLI](/docs/user/en/tutorial/bench), your process manager or the Frappe application directly. Your process managers take care of getting all the moving parts up and running for your Frappe environment as well as directing output and error streams to your log files.

Apart from the *"always running"* default logging, you can also use [Monitor](/docs/user/en/debugging#monitoring) to log more information about all the requests to your site.


### Maintainence

The log files generated by your process manager may get pretty large over time if you aren't paying attention. To know which files you have to track for this, checkout the `supervisor.conf` or `Procfile` on your bench, depending on whether you're running a production or development instance respectively.


### More

In a production environment, you'd likely want to log more information for your Frappe Applications or the processes that make up your Frappe Environment. Here's some resources you could go over to find out more.

Frappe Application

- [Frappe Logging API](/docs/user/en/api/logging)

Server Monitoring

- [MySQL](https://dev.mysql.com/doc/refman/5.7/en/server-logs.html)
- [PostgreSQL](https://www.postgresql.org/docs/current/runtime-config-logging.html)
- [NGINX](https://docs.nginx.com/nginx/admin-guide/monitoring/logging/)
