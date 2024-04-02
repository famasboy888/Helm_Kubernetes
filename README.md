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

Think of `spec` as the blueprint of the pod:
```bash
spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

## To make connections they use `labels` and `selectors`

The `metadata` part contains ==> `labels`.
```bash
metadata:
  name: nginx-deployment
  labels:                     <======
    app: nginx
```

While `specs` part contains ==> `selector`
```bash
spec:
  replicas: 3
  selector:         <=========
    matchLabels:
      app: nginx
```

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/Helm_Kubernetes/assets/23441168/7372de50-4a10-4117-8d56-fba64255f859s">
</p>


## Regarding Ports

Note: You can refer to the Dockerfile `EXPOSE` port.

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/Helm_Kubernetes/assets/23441168/343e6b07-87e0-443e-858a-a693d5e46c7e">
</p>
