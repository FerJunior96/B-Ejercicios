###############################################################
#                          WARNING!!!!                        #
# This is a sandbox environment. Using personal credentials   #
# is HIGHLY! discouraged. Any consequences of doing so are    #
# completely the user's responsibilites.                      #
#                                                             #
# The PWD team.                                               #
###############################################################
[node1] (local) root@192.168.0.18 ~
$     git clone https://github.com/dockersamples/linux_tweet_app
Cloning into 'linux_tweet_app'...
remote: Counting objects: 14, done.
remote: Total 14 (delta 0), reused 0 (delta 0), pack-reused 14
Unpacking objects: 100% (14/14), done.
[node1] (local) root@192.168.0.18 ~
$  docker container run alpine hostname
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
ff3a5c916c92: Pull complete
Digest: sha256:e1871801d30885a610511c867de0d6baca7ed4e6a2573d506bbec7fd3b03873f
Status: Downloaded newer image for alpine:latest
125034c52ca1
[node1] (local) root@192.168.0.18 ~
$  docker container ls --all
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
125034c52ca1        alpine              "hostname"          4 seconds ago       Exited (0) 3 seconds ago                       tender_bhaskara
[node1] (local) root@192.168.0.18 ~
$  docker container run --interactive --tty --rm ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
6b98dfc16071: Pull complete
4001a1209541: Pull complete
6319fc68c576: Pull complete
b24603670dc3: Pull complete
97f170c87c6f: Pull complete
Digest: sha256:5f4bdc3467537cbbe563e80db2c3ec95d548a9145d64453b06939c4592d67b6d
Status: Downloaded newer image for ubuntu:latest
root@bfed661486b9:/# ls /
bin   dev  home  lib64  mnt  proc  run   srv  tmp  var
boot  etc  lib   media  opt  root  sbin  sys  usr
root@bfed661486b9:/# ps aux
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root          1  0.1  0.0  18504  3524 pts/0    Ss   20:49   0:00 bash
root         12  0.0  0.0  34396  2912 pts/0    R+   20:50   0:00 ps aux
root@bfed661486b9:/# cat /etc/issue
Ubuntu 18.04 LTS \n \l

root@bfed661486b9:/#  exit
exit
[node1] (local) root@192.168.0.18 ~
$  cat /etc/issue
Welcome to Alpine Linux 3.7
Kernel \r on an \m (\l)

[node1] (local) root@192.168.0.18 ~
$  docker container run \
>  --detach \
>  --name mydb \
>  -e MYSQL_ROOT_PASSWORD=my-secret-pw \
>  mysql:latest
Unable to find image 'mysql:latest' locally
latest: Pulling from library/mysql
f2aa67a397c4: Pull complete
1accf44cb7e0: Pull complete
2d830ea9fa68: Pull complete
740584693b89: Pull complete
4d620357ec48: Pull complete
ac3b7158d73d: Pull complete
a48d784ee503: Pull complete
f122eadb2640: Pull complete
3df40c552a96: Pull complete
da7d77a8ed28: Pull complete
f03c5af3b206: Pull complete
54dd1949fa0f: Pull complete
Digest: sha256:d60c13a2bfdbbeb9cf1c84fd3cb0a1577b2bbaeec11e44bf345f4da90586e9e1
Status: Downloaded newer image for mysql:latest
6cc234e097d0a962d4f4881dd99df13decc98054a1dd9651db3af6db7c084b34
[node1] (local) root@192.168.0.18 ~
$  docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED    STATUS              PORTS               NAMES
6cc234e097d0        mysql:latest        "docker-entrypoint.s…"   39 seconds ago    Up 38 seconds       3306/tcp            mydb
[node1] (local) root@192.168.0.18 ~
$  docker container logs mydb
Initializing database
2018-06-14T20:51:08.216674Z 0 [Warning] [MY-011070] [Server] 'Disabling symboliclinks using --skip-symbolic-links (or equivalent) is the default. Consider not using this option as it' is deprecated and will be removed in a future release.
2018-06-14T20:51:08.216784Z 0 [System] [MY-013169] [Server] /usr/sbin/mysqld (mysqld 8.0.11) initializing of server in progress as process 31
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
2018-06-14T20:51:10.749202Z 5 [Warning] [MY-010453] [Server] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
2018-06-14T20:51:11.539484Z 5 [Warning] [MY-010315] [Server] 'user' entry 'mysql.infoschema@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539529Z 5 [Warning] [MY-010315] [Server] 'user' entry 'mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539542Z 5 [Warning] [MY-010315] [Server] 'user' entry 'mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539553Z 5 [Warning] [MY-010315] [Server] 'user' entry 'root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539572Z 5 [Warning] [MY-010323] [Server] 'db' entry 'performance_schema mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539580Z 5 [Warning] [MY-010323] [Server] 'db' entry 'sys mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539595Z 5 [Warning] [MY-010311] [Server] 'proxies_priv' entry '@ root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539744Z 5 [Warning] [MY-010330] [Server] 'tables_priv' entry'user mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.539786Z 5 [Warning] [MY-010330] [Server] 'tables_priv' entry'sys_config mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:11.936637Z 0 [System] [MY-013170] [Server] /usr/sbin/mysqld (mysqld 8.0.11) initializing of server has completed
Database initialized
MySQL init process in progress...
2018-06-14T20:51:13.845772Z 0 [Warning] [MY-011070] [Server] 'Disabling symboliclinks using --skip-symbolic-links (or equivalent) is the default. Consider not using this option as it' is deprecated and will be removed in a future release.
2018-06-14T20:51:13.845928Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.11) starting as process 82
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
2018-06-14T20:51:14.212485Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2018-06-14T20:51:14.213430Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
2018-06-14T20:51:14.226288Z 0 [Warning] [MY-010315] [Server] 'user' entry 'mysql.infoschema@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.226338Z 0 [Warning] [MY-010315] [Server] 'user' entry 'mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.226354Z 0 [Warning] [MY-010315] [Server] 'user' entry 'mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.226365Z 0 [Warning] [MY-010315] [Server] 'user' entry 'root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.226391Z 0 [Warning] [MY-010323] [Server] 'db' entry 'performance_schema mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.226412Z 0 [Warning] [MY-010323] [Server] 'db' entry 'sys mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.226428Z 0 [Warning] [MY-010311] [Server] 'proxies_priv' entry '@ root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.229507Z 0 [Warning] [MY-010330] [Server] 'tables_priv' entry'user mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.229540Z 0 [Warning] [MY-010330] [Server] 'tables_priv' entry'sys_config mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:14.238014Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.11'  socket: '/var/run/mysqld/mysqld.sock'  port: 0  MySQL Community Server - GPL.
Warning: Unable to load '/usr/share/zoneinfo/iso3166.tab' as time zone. Skippingit.
Warning: Unable to load '/usr/share/zoneinfo/leap-seconds.list' as time zone. Skipping it.
Warning: Unable to load '/usr/share/zoneinfo/zone.tab' as time zone. Skipping it.
Warning: Unable to load '/usr/share/zoneinfo/zone1970.tab' as time zone. Skipping it.
2018-06-14T20:51:17.578588Z 10 [Warning] [MY-010315] [Server] 'user' entry 'mysql.infoschema@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578634Z 10 [Warning] [MY-010315] [Server] 'user' entry 'mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578647Z 10 [Warning] [MY-010315] [Server] 'user' entry 'mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578657Z 10 [Warning] [MY-010315] [Server] 'user' entry 'root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578678Z 10 [Warning] [MY-010323] [Server] 'db' entry 'performance_schema mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578685Z 10 [Warning] [MY-010323] [Server] 'db' entry 'sys mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578696Z 10 [Warning] [MY-010311] [Server] 'proxies_priv' entry '@ root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578865Z 10 [Warning] [MY-010330] [Server] 'tables_priv' entry 'user mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:17.578890Z 10 [Warning] [MY-010330] [Server] 'tables_priv' entry 'sys_config mysql.sys@localhost' ignored in --skip-name-resolve mode.

2018-06-14T20:51:19.506218Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.11)  MySQL Community Server - GPL.

MySQL init process done. Ready for start up.

2018-06-14T20:51:19.868937Z 0 [Warning] [MY-011070] [Server] 'Disabling symboliclinks using --skip-symbolic-links (or equivalent) is the default. Consider not using this option as it' is deprecated and will be removed in a future release.
2018-06-14T20:51:19.869068Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.11) starting as process 1
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
mbind: Operation not permitted
2018-06-14T20:51:20.204043Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2018-06-14T20:51:20.205446Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
2018-06-14T20:51:20.216026Z 0 [Warning] [MY-010315] [Server] 'user' entry 'mysql.infoschema@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.216076Z 0 [Warning] [MY-010315] [Server] 'user' entry 'mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.216103Z 0 [Warning] [MY-010315] [Server] 'user' entry 'mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.216127Z 0 [Warning] [MY-010315] [Server] 'user' entry 'root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.216172Z 0 [Warning] [MY-010323] [Server] 'db' entry 'performance_schema mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.216198Z 0 [Warning] [MY-010323] [Server] 'db' entry 'sys mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.216225Z 0 [Warning] [MY-010311] [Server] 'proxies_priv' entry '@ root@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.220357Z 0 [Warning] [MY-010330] [Server] 'tables_priv' entry'user mysql.session@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.220396Z 0 [Warning] [MY-010330] [Server] 'tables_priv' entry'sys_config mysql.sys@localhost' ignored in --skip-name-resolve mode.
2018-06-14T20:51:20.226674Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.11'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server - GPL.
[node1] (local) root@192.168.0.18 ~
$    docker container top mydb
PID                 USER                TIME                COMMAND
1065                999                 0:00                mysqld
[node1] (local) root@192.168.0.18 ~
$    docker container top mydb
PID                 USER                TIME                COMMAND
1065                999                 0:00                mysqld
[node1] (local) root@192.168.0.18 ~
$  docker exec -it mydb \
>  mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version
mysql: [Warning] Using a password on the command line interface can be insecure.
mysql  Ver 8.0.11 for Linux on x86_64 (MySQL Community Server - GPL)
[node1] (local) root@192.168.0.18 ~
$  docker exec -it mydb sh
#  mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version
mysql: [Warning] Using a password on the command line interface can be insecure.
mysql  Ver 8.0.11 for Linux on x86_64 (MySQL Community Server - GPL)
#  exit
[node1] (local) root@192.168.0.18 ~
$  cd ~/linux_tweet_app
[node1] (local) root@192.168.0.18 ~/linux_tweet_app
$  cat Dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html
COPY linux.png /usr/share/nginx/html

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
[node1] (local) root@192.168.0.18 ~/linux_tweet_app
$  exit