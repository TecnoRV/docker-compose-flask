# docker-compose-flask

```

+-------------+       +------------+         +--------------+     +-----------+
|             |       |            |         |              |     |           |
|    nginx    +-------+  gunicorn  +---------+  flask app   +-----+   redis   |
|             |       |            |         |              |     |           |
+-------------+       +------------+         +--------------+     +-----------+

```

## Environments setup
We need to install docker-compose previouslly

## Quick start

### First build and up

```sh
$ git clone https://github.com/TecnoRV/docker-compose-flask.git
$ cd docker-compose-flask
$ sudo docker-compose build
$ sudo docker-compose up -d
```

### Check the service running information

```sh
$ sudo docker-compose ps
           Name                         Command               State           Ports
--------------------------------------------------------------------------------------------
dockercomposeflask_nginx_1   /usr/sbin/nginx                  Up      0.0.0.0:80->80/tcp
dockercomposeflask_redis_1   docker-entrypoint.sh redis ...   Up      6379/tcp
dockercomposeflask_web_1     /runserver.sh                    Up      0.0.0.0:8000->8000/tcp
```

## Test the web service

```sh
$ curl http://127.0.0.1
Hello Container World! I have been seen 1 times and my hostname is 25d45dc20b24.
$ curl http://127.0.0.1/hello
Hello Container World, this is my first Flask Demo with Docker! I have been seen 2 times and my hostname is 25d45dc20b24.
$ curl -XGET 'http://127.0.0.1/hello'
Hello Container World, this is my first Flask Demo with Docker! I have been seen 3 times and my hostname is 25d45dc20b24.
```

### If you want, you can stop the service

```sh
$ sudo docker-compose stop
Stopping dockercomposeflask_nginx_1 ... done
Stopping dockercomposeflask_web_1   ... done
Stopping dockercomposeflask_redis_1 ... done
```
