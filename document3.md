###############################################################
#                          WARNING!!!!                        #
# This is a sandbox environment. Using personal credentials   #
# is HIGHLY! discouraged. Any consequences of doing so are    #
# completely the user's responsibilites.                      #
#                                                             #
# The PWD team.                                               #
###############################################################
[node1] (local) root@192.168.0.28 ~
$ docker swarm init --advertise-addr $(hostname -i)
Swarm initialized: current node (51dcno2xojehjzw5uxzea2lmd) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-5b0jawcb2x2ffcuu6mhj91jfnittrdy6w69ykhy0ypu2cita7e-6nv1le98s87u6jbe85eqbtzsg 192.168.0.28:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and followthe instructions.

[node1] (local) root@192.168.0.28 ~
$ docker node ls
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
51dcno2xojehjzw5uxzea2lmd *   node1               Ready               Active         Leader              18.03.1-ce
[node1] (local) root@192.168.0.28 ~
$ git clone https://github.com/docker/example-voting-app
Cloning into 'example-voting-app'...
remote: Counting objects: 482, done.
remote: Total 482 (delta 0), reused 0 (delta 0), pack-reused 482
Receiving objects: 100% (482/482), 229.43 KiB | 11.47 MiB/s, done.
Resolving deltas: 100% (179/179), done.
[node1] (local) root@192.168.0.28 ~
$ cd example-voting-app
[node1] (local) root@192.168.0.28 ~/example-voting-app
$ docker stack deploy --compose-file=docker-stack.yml voting_stack
Creating network voting_stack_default
Creating network voting_stack_frontend
Creating network voting_stack_backend
Creating service voting_stack_worker
Creating service voting_stack_visualizer
Creating service voting_stack_redis
Creating service voting_stack_db
docker stack ls
Creating service voting_stack_vote
Creating service voting_stack_result
[node1] (local) root@192.168.0.28 ~/example-voting-app
$ docker stack ls
NAME                SERVICES
voting_stack        6
[node1] (local) root@192.168.0.28 ~/example-voting-app
$ docker stack services voting_stack
ID                  NAME                      MODE                REPLICAS     IMAGE                                          PORTS
0fdvntedtdcj        voting_stack_db           replicated          0/1     postgres:9.4
cl37qlm18eyg        voting_stack_vote         replicated          0/2     dockersamples/examplevotingapp_vote:before     *:5000->80/tcp
czvy9xg70h51        voting_stack_visualizer   replicated          0/1     dockersamples/visualizer:stable                *:8080->8080/tcp
khwz97epnm8x        voting_stack_worker       replicated          0/1     dockersamples/examplevotingapp_worker:latest
qv6otgdfleab        voting_stack_result       replicated          0/1     dockersamples/examplevotingapp_result:before   *:5001->80/tcp
y44vr877iv79        voting_stack_redis        replicated          0/1     redis:alpine                                   *:30000->6379/tcp
[node1] (local) root@192.168.0.28 ~/example-voting-app
$ docker service ps voting_stack_vote
ID                  NAME                  IMAGE      NODE                DESIRED STATE       CURRENT STATE              ERROR            PORTS
kslb4iv1q074        voting_stack_vote.1   dockersamples/examplevotingapp_vote:before   node1               Running             Preparing 10 seconds ago