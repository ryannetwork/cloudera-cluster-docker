# Cloudera Cluster Docker

This repository contains configuration to build docker images for running a cloudera cluster. 

### Network
You must create a network before running a cluster from docker-compose.

`docker network create cloudera-cluster-net`

### Basic docker commands

- To run a new container with bash: `docker run --rm -i -t CONTAINER_ID bash`
- To run a bash session in a container which has already been started: `docker exec -i -t CONTAINER_ID bash`

### Gateway commands

The default gateway container is run from docker-compose configuration to provide faster access to its tools (there is no overhead for container running every time when you execute a command). 

`docker exec -i -t gateway hdfs dfs -ls /`

Also you can run a new container based on the gateway image. In such case you must set a network.

`docker run --rm -i -t --network cloudera-cluster-net ipogudin/cloudera-cluster-gateway hdfs dfs -ls /`

# Useful links
- [Installing and Deploying CDH Using the Command Line](https://www.cloudera.com/documentation/enterprise/latest/topics/cdh_ig_command_line.html)