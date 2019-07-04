# Docker Swarm playground

```bash
docker swarm init

docker network create --attachable=true --driver=overlay service_mesh_network

cd src/main/yaml

docker stack deploy --compose-file=service_mesh service_mesh
docker stack deploy --compose-file=database database
docker stack deploy --compose-file=management management
docker stack deploy --compose-file=monitoring_push monitoring_push
docker stack deploy --compose-file=monitoring_pull monitoring_pull
docker stack deploy --compose-file=logging logging
docker stack deploy --compose-file=tracing tracing
docker stack deploy --compose-file=message_queue message_queue
```

```bash
docker exec -it database_cassandra cqlsh
```

```cassandraql
create keyspace hiberbee WITH replication = {'class': 'SimpleStrategy', 'replication_factor' : 1};
create keyspace jaeger WITH replication = {'class': 'SimpleStrategy', 'replication_factor' : 1};
```

```
127.0.0.1 localhost traefik.localhost vault.localhost rabbitmq.localhost chronograf.localhost grafana.localhost influxdb.localhost
```
