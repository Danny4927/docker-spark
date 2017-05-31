
# Docker-Spark standalone

**Current State:** _spark master is running, but worker is not connecting_

simplified Version of infsaulo/docker-spark.
The aim is to run a simple Sparkpi in a multi-node setup via docker swarm.

To start the Spark cluster in standalone mode setup a docker swarm and use:

`docker stack deploy -c docker-compose.yml spark_cluster`

to deploy spark to the cluster. 
Make sure you modify the constrains int the `docker-compose.yml` according to the hostnames of your swarm nodes.

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
