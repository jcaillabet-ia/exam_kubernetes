# Préparation

```bash
kubectl create namespace eval
```


# mysql

```bash
kubectl apply -f mysql/mysql-local-data-folder-pv.yaml
kubectl apply -f mysql/secret.yml
kubectl apply -f mysql/service.yml
kubectl apply -f mysql/statefulset.yml
```

# test

```bash
kubectl apply -f test/fastapi-pod.yaml
```

# FastAPI

```bash
kubectl apply -f fastapi/service.yml
kubectl apply -f fastapi/deployment.yml
```

# Test de persistance du PV

```bash
kubectl delete pod mysql-0 -n eval
kubectl rollout restart deployment fastapi -n eval
```

# Reset

```bash
kubectl delete pv data
kubectl delete all --all -n eval
```