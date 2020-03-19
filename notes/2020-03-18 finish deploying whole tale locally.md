## 2020-03-18 Finish deploying whole tale locally

### Repeated deployment process starting from cloning of `whole-tale/deploy-dev`

- Restored third increment to system backup made [2020-03-16](../notes/2020-03-16%20set%20up%20artemis%20for%20running%20whole%20tale%20locally.md).

- Cloned the `whole-tale/deploy-dev` repo:
	```
	tmcphill@artemis:~$ git clone git@github.com:whole-tale/deploy-dev.git
	Cloning into 'deploy-dev'...
	remote: Enumerating objects: 491, done.
	remote: Total 491 (delta 0), reused 0 (delta 0), pack-reused 491
	Receiving objects: 100% (491/491), 163.54 KiB | 3.03 MiB/s, done.
	Resolving deltas: 100% (283/283), done.
	```
- Copied freshly downloaded `acme.json` file to `traefik/acme` directory in clone.  Note that this is different from the (incorrect) destination for the file used previously:
	```
	tmcphill@artemis:~/deploy-dev/traefik$ mkdir acme
	tmcphill@artemis:~/deploy-dev/traefik$ cd acme
	tmcphill@artemis:~/deploy-dev/traefik/acme$ mv ~/Downloads/acme.json .
	```
-  Set required ownership and permissions on `acme.json`:
	```
	tmcphill@artemis:~/deploy-dev/traefik/acme$ sudo chown root:root acme.json
	tmcphill@artemis:~/deploy-dev/traefik/acme$ sudo chmod 0600 acme.json
	tmcphill@artemis:~/deploy-dev/traefik/acme$ ls -al
	total 20
	drwxr-xr-x 2 tmcphill users  4096 Mar 18 17:47 .
	drwxr-xr-x 4 tmcphill users  4096 Mar 18 17:43 ..
	-rw------- 1 root     root  10686 Mar 18 17:45 acme.json
	```

- Performed the `make services` and `make dev` steps as before.  Output limited to the final stage starting from the invocation of `setup_girder.py` which previously failed due to misplaced `acme.json` file:
	```
	tmcphill@artemis:~/deploy-dev$ make services
	. . .
	tmcphill@artemis:~/deploy-dev$ make dev
	. . .
	./setup_girder.py
	Waiting for Girder to start
	Creating admin user
	Creating default assetstore
	Enabling plugins
	Restarting girder to load plugins
	Waiting for Girder to restart
	Waiting for Girder to restart
	Waiting for Girder to restart
	Waiting for Girder to restart
	Waiting for Girder to restart
	Setting up Plugin
	Create a Jupyter image
	Create an RStudio image
	Create a JupyterLab image
	Create OpenRefine image
	Create Jupyter Spark image
	-------------- You should be all set!! -------------
	try going to https://girder.local.wholetale.org and log in with:
	  user : admin
	  pass : XXXXXXXXXXXXXXX

	tmcphill@artemis:~/deploy-dev$
	```
- Noted no errors in output from either Make target.

- Confirmed that expected services are running...
	```
	tmcphill@artemis:~/deploy-dev$ docker service ls
	ID                  NAME                MODE                REPLICAS            IMAGE                             PORTS
	ehru4vhatfc2        wt_dashboard        replicated          1/1                 wholetale/dashboardproxy:latest
	gz1so9l186fl        wt_dashboard_next   replicated          1/1                 bodom0015/ng-dashboard:wt
	tvfham7v07m9        wt_girder           replicated          1/1                 wholetale/girder:latest
	uwm5ddoqzogc        wt_mongo            replicated          1/1                 mongo:3.2
	p6wa7c1xl04i        wt_redis            replicated          1/1                 redis:4-stretch
	atcuev2twcu2        wt_registry         replicated          1/1                 registry:2.6
	9rk562xwei03        wt_traefik          replicated          1/1                 traefik:alpine                    *:80->80/tcp, *:443->443/tcp, *:8080->8080/tcp
	```
	...along with healthy-looking containers...
	```
	tmcphill@artemis:~/deploy-dev$ docker ps
	CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS              PORTS               NAMES
	1c5c221ad460        wholetale/girder:latest           "/usr/local/bin/dock…"   10 minutes ago      Up 10 minutes       8080/tcp            wt_girder.1.4z9eukkizmhd8tcchcrqimj5d
	49d4d999cf69        wholetale/gwvolman:latest         "/docker-entrypoint.…"   11 minutes ago      Up 10 minutes                           celery_worker
	78f52e7923f5        bodom0015/ng-dashboard:wt         "nginx -g 'daemon of…"   11 minutes ago      Up 11 minutes       80/tcp              wt_dashboard_next.1.vs2vkfushlxc90h39pft5pwfe
	07a608bc7a48        registry:2.6                      "/entrypoint.sh /etc…"   11 minutes ago      Up 11 minutes       5000/tcp            wt_registry.1.wsk44vnn1prax77ffxj3p7o78
	19305f8b00f8        wholetale/dashboardproxy:latest   "nginx -g 'daemon of…"   11 minutes ago      Up 11 minutes       80/tcp              wt_dashboard.1.u9bo215cfn8yfyozdxjlf8xby
	a137fe0cc89b        redis:4-stretch                   "docker-entrypoint.s…"   11 minutes ago      Up 11 minutes       6379/tcp            wt_redis.1.dglhphke48c96d0y03gk7jf3d
	8527d254bd54        mongo:3.2                         "docker-entrypoint.s…"   11 minutes ago      Up 11 minutes       27017/tcp           wt_mongo.1.lw95pw2ap5xwk815er2ir1e0d
	5f23e74102e3        traefik:alpine                    "/entrypoint.sh trae…"   12 minutes ago      Up 11 minutes       80/tcp              wt_traefik.1.ihnyqzxaxk5f66hduxjngmuc9
	```
	...and the `celery_worker` in particular:
	```
	tmcphill@artemis:~/deploy-dev$ docker ps | grep celery_worker
	49d4d999cf69        wholetale/gwvolman:latest         "/docker-entrypoint.…"   12 minutes ago      Up 12 minutes                           celery_worker 
	```
