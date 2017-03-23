---
date: 2014-12-31T00:00:00-00:00
draft: false
title: Celery in local Django development
---

Recently I set up [Celery](http://www.celeryproject.org/) to perform some background tasks for [Sibbell](http://sibbell.com), a Django project. The tasks were pretty simple, and I wasn't interested in installing [RabbitMQ](http://www.rabbitmq.com/) (which I was using on the production server) on my local machine at the time for use in the development environment.

The solution? Use the `CELERY_ALWAYS_EAGER` [setting](http://celery.readthedocs.org/en/latest/configuration.html#celery-always-eager). It runs the tasks asynchronously, which in this case was just fine.
