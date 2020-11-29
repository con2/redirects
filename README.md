# Redirects en masse on Kubernetes

We have a whole host of hostnames we want to redirect to another hostname. This is the Way.

## Why not just use the `nginx.ingress.kubernetes.io/temporal-redirect` annotation?

It takes place **before** [cert-manager](https://cert-manager.io/) challenge solvers, effectively breaking LetsEncrypt for domains using it. There are [some](https://github.com/jetstack/cert-manager/issues/235) [issues](https://github.com/jetstack/cert-manager/issues/235) that have been filed against `cert-manager` and `ingress-nginx` solving the similar case for HTTP -> HTTPS redirect and basic auth, but not `temporal-redirect` specifically.

So instead we opt for an `nginx` pod with configuration mounted from a ConfigMap into under `/etc/nginx/conf.d`.

## Configuration

Use `kubernetes/default.vars.yaml` as reference and `kubernetes/production.vars.yaml` as example.

## Building and deploying

    emsk -E production -- run -n redirects
