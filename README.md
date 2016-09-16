wordpress + nginx + mysql docker container
==========================================

A basic composed docker trio of wordpress, mysql, and nginx.

Nginx is configured as a reverse proxy in front of wordpress, with apache2 doing the heavy lifting.

The only requirement is to install docker and docker compose. (Tested with docker 1.12.1, docker-compose 1.8.0.)

Usage
-----

Start the container (in detached mode) with:

```
$ docker-compose up -d
```

Verify the functionality by visiting localhost:8080, which should show the Wordpress setup page.

Stop the container:

```
$ docker-compose down
```

Notes
-----

* Wordpress html files will be in a volume bound to '''.data/html/'''
* MySQL data files are similarly located in '''.data/db/'''
* The nginx config file is installed using '''envsubst''' on the '''nginx.conf.template''' file.

The environment variables defined in the proxy section of '''docker-compose.yml''' will be substituted where
referenced in the nginx template before it is installed inside the container at '''/etc/nginx/nginx.conf'''.

TODO
----

* Use a launch wrapper that will postpone the start of Apache until the database is listening.
