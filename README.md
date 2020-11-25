# Ingress redirects en masse

We have a whole host of hostnames we want to redirect to another hostname. This is the Way.

## Configuration

Use `kubernetes/default.vars.yaml` as reference and `kubernetes/production.vars.yaml` as example.

## Building and deploying

    emsk -E production -- run -n static
