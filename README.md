# gke-ingress-test

## Create Services

```shell
$ kubectl apply -f services/
deployment "hello-deployment" created
service "hello-service" created
deployment "hey-deployment" created
service "hey-service" created
```

## TLS

### Create the sertificate and a secret

```shell
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout secret.key -out secret.crt -subj "/CN=foobar.com"
kubectl create secret tls tls-secret --key=secret.key --cert=secret.crt
```

### Create TSL Ingress

```shell
kubectl apply -f ingress-tls.yaml
ingress "fanout-ingress-tls-gce" created
```

## Ingress

### Create Ingress

```shell
kubectl apply -f ingress.yaml
ingress "fanout-ingress-gce" created
```