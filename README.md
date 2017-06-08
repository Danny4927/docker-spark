
# Docker-Spark standalone

simplified Version of infsaulo/docker-spark.
The aim is to run a simple Sparkpi in a multi-node setup via docker swarm.

To start the Spark cluster in standalone mode setup a docker swarm and add labels to the nodes:

master (change hostname **node-1** to your real hostname):

`docker node update --label-add type=spark-master node-1`

worker(change hostname **node-2** to your real hostname):

`docker node update --label-add type=spark-worker node-2`

Use:

`docker stack deploy -c docker-compose.yml spark_cluster`

to deploy spark to the cluster. 

**Note:** Without labels it won't work

**Note2:** If you are using VirtualBox make sure the network is bridge and promiscous mode is allowed

Spark History Server is available on `http://"ip of the master node":8080`

## Usefull commands:

- `docker stack ls` - see stacks and number of services
- `docker stack ps spark_cluster` - see the services of the stack "spark-cluster"
- `docker stack rm spark_cluster` - remove the stack "spark-cluster"
- `docker service inspect --pretty spark_cluster_master` - get information about the master service

### Logs
- `docker service ps SERVICE-NAME` - find which nodes the service is running
- `docker ps` - on the node which runs the service to find the container id
- `docker logs cont-id` - to get the log

If you are using the experimental daemon of docker you can also use: `docker service logs service-id`


## license

MIT
