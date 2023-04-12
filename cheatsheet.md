
## Persistent volumes

```bash
kubectl exec $POD_NAME -c nginx -- cat /var/log/nginx/access.log
```

## Resizing PVC

```bash
kubectl run -it --rm --image=mysql:5.6 --restart=Never mysql-client -- mysql -h mysql -ppassword
```

```sql
CREATE DATABASE testingResize;
USE testingResize;
CREATE TABLE anEmptyTable (k VARCHAR(256), v TEXT);
SHOW TABLES;
```

```
kubectl patch deployment mysql -p '{ "spec": { "replicas": 0 }}'

kubectl patch pvc mysql-pv-claim -p '{ "spec": { "resources": { "requests": { "storage": "6Gi" }}}}'

kubectl describe pvc mysql-pv-claim

kubectl patch deployment mysql -p '{ "spec": { "replicas": 1 }}'

kubectl run -it --rm --image=mysql:5.6 --restart=Never mysql-client -- mysql -h mysql -ppassword
```

```SQL
SHOW DATABASES;
USE testingResize;
SHOW TABLES;
```

