# postgres-k8s
A simple K8s postgresql installation

Clone repository:

`gclf git@github.com:escalante29/postgres-k8s.git`

Create cluster:

`kind create cluster --name postgresql --image kindest/node:v1.31.1`

Get Cluster info:

`kubectl cluster-info --context kind-postgresql`

Create NS for PostgreSQL:

`k create ns postgresql`

Define k8s secret:

```
kubectl -n postgresql create secret generic postgresql \
  --from-literal POSTGRES_USER="postgresadmin" \
  --from-literal POSTGRES_PASSWORD='admin123' \
  --from-literal POSTGRES_DB="postgresdb" \
  --from-literal REPLICATION_USER="replicationuser" \
  --from-literal REPLICATION_PASSWORD="replicationPassword"
```


Export PGSQL default env vars in pod:

```
export PGDATABASE=postgresdb
export PGUSER=postgresadmin
export PGPASSWORD=admin123
```