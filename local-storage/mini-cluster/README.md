## Mongodb set up replica sets

### Set Mongodb Replica Sets

```sh
$ kubectl exec -it mongo-stateful-set-master-0 -- /bin/bash
$ mongo
$> rs.initiate()
$> conf=rs.conf()
$> conf.members[0].host="mongodb-service-master:27017"
$> rs.reconfig(conf)
$> rs.add("mongodb-service-replica-1")
$> rs.add("mongodb-service-replica-2")
$> rs.status()
```

### save mongodb connection string to Secrets

```sh
$ kubectl apply -f mongodb-connection-string.secret.yaml
```
