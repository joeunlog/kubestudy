# Single Pod & SVC
2022-01-28

# bitnami/nginx

## Manifest

```jsx
vim pod.yaml

apiVersion: v1
kind: Pod
metadata:
  name: myweb
  labels:
    run: my-nginx
spec:
  containers:
  - name: nginx
    image: bitnami/nginx
    ports:
    - containerPort: 8080
```

```jsx
vim svc.yaml

apiVersion: v1
kind: Service
metadata:
  name: myweb-svc
spec:
  selector:
    run: my-nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

## Make Resource CMD

```jsx
kubectl create -f pod.yaml

kubectl create -f svc.yaml
```

## Curl Test

### curl pod ip

```jsx
kubectl get pods -o wide

# check pod_ip

curl pod_ip:8080
```

### curl svc ip

```jsx
kubectl get svc

# check svc_ip

curl svc_ip
```

[서비스와 애플리케이션 연결하기](https://kubernetes.io/ko/docs/concepts/services-networking/connect-applications-service/)

# Echoserver

## manifest

```jsx
vim pod.yaml

apiVersion: v1
kind: Pod
metadata:
  name: echoserver
  labels:
    run: echoserver
spec:
  containers:
  - name: echoserver
    image: k8s.gcr.io/echoserver:1.10
    ports:
    - containerPort: 8080
```

```jsx
vim svc.yaml

apiVersion: v1
kind: Service
metadata:
  name: echoserver-svc
spec:
  selector:
    run: echoserver
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

## Make Resource CMD

```jsx
kubectl create -f pod.yaml

kubectl create -f svc.yaml
```

## Curl Test

### curl pod ip

```jsx
kubectl get pods -o wide

# check pod_ip

curl pod_ip:8080
```

### curl svc ip

```jsx
kubectl get svc

# check svc_ip

curl svc_ip
```