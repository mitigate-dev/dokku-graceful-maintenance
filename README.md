# dokku-graceful-maintenance

Put your app into maintenance mode gracefully.

dokku-graceful-maintenance modifies your nginx.conf to respond with HTTP 503 status code to health check requests. This way existing sessions on the server will not get instantly terminated.

### Installation

```shell
sudo dokku plugin:install https://github.com/mak-it/dokku-graceful-maintenance
```

### Commands

```
graceful-maintenance:on <app>    Enable maintenance mode for app
graceful-maintenance:off <app>   Disable maintenance mode for app
```

### Usage

First, set up HEALTHCHECK_ENDPOINT env variable for your app:

```
dokku config:set <app> HEALTHCHECK_ENDPOINT=/status
```

Enable maintenance mode:
```
$ sudo dokku graceful-maintenance:on <app>
-----> Enabling maintenance mode for <app>
-----> Done
```

Disable maintenance mode:
```
$ sudo dokku graceful-maintenance:off <app>
-----> Disabling maintenance mode for <app>
-----> Done
```
