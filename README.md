
# spark

simplified Version of infsaulo/docker-spark.
The aim is to run a simple Sparkpi in a multi-node setup via docker swarm.

To start the Spark cluster in standalone mode setup a docker swarm and use:

`docker stack deploy -c docker-compose.yml spark_cluster`

to deploy spark to the cluster. 
Make sure you modify the constrains int the `docker-compose.yml` according to the hostnames of your swarm nodes.

Spark History Server is available on `http://"ip of the master node":8080`

## license

MIT
