# gke-ingress-test

## SSL

### Create the sertificate and a secret

```shell
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout secret.key -out secret.crt -subj "/CN=foobar.com"
kubectl create secret tls tls-secret --key=secret.key --cert=secret.crt
```
