# Creating a deployment yaml file

There are 3 main parts of a yamlm file

1) metadata

2) Spec

3) Status <== But this isauto generated bby k8, so no need.


## `spec` has 3 parts: `replicas`, `selector`, `template`

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: ...
  selector: ...
  template: ...
```


## Each configuration block has its own `metadata` and `spec`

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: ...
  selector: ...
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```
