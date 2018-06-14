###############################################################
#                          WARNING!!!!                        #
# This is a sandbox environment. Using personal credentials   #
# is HIGHLY! discouraged. Any consequences of doing so are    #
# completely the user's responsibilites.                      #
#                                                             #
# The PWD team.                                               #
###############################################################
[node1] (local) root@192.168.0.18 ~
$ docker container run -ti ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
6b98dfc16071: Pull complete
4001a1209541: Pull complete
6319fc68c576: Pull complete
b24603670dc3: Pull complete
97f170c87c6f: Pull complete
Digest: sha256:5f4bdc3467537cbbe563e80db2c3ec95d548a9145d64453b06939c4592d67b6d
Status: Downloaded newer image for ubuntu:latest
root@748c47836f0a:/# apt-get update
Get:1 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:3 http://security.ubuntu.com/ubuntu bionic-security/universe Sources [5646 B]
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [83.2 kB]
Get:5 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [38.5 kB]
Get:6 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [1075 B]
Get:7 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:8 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [123kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic/universe Sources [11.5 MB]
Get:10 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [186 kB]
Get:11 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [11.3 MB]
Get:12 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [13.5 kB]
Get:13 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1344 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe Sources [32.4 kB]
Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages[1663 B]
Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [178 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [106 kB]
Get:18 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages[2793 B]
Fetched 25.4 MB in 3s (7333 kB/s)
Reading package lists... Done
root@748c47836f0a:/# apt-get install -y figlet
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  figlet
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 133 kB of archives.
After this operation, 752 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic/universe amd64 figlet amd64 2.2.5-3 [133 kB]
Fetched 133 kB in 0s (316 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package figlet.
(Reading database ... 4035 files and directories currently installed.)
Preparing to unpack .../figlet_2.2.5-3_amd64.deb ...
Unpacking figlet (2.2.5-3) ...
Setting up figlet (2.2.5-3) ...
update-alternatives: using /usr/bin/figlet-figlet to provide /usr/bin/figlet (figlet) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man6/figlet.6.gz because associated file /usr/share/man/man6/figlet-figlet.6.gz (of link group figlet) doesn't exist
root@748c47836f0a:/# exit
exit
[node1] (local) root@192.168.0.18 ~
$