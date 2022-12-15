# HELM Chart Demo
## _Demo helm cart installer for deploying web app writen in nodejs, it can be used to deploy in differenct environments and also pass a JWT token as configuration_

## Features

- Have different values for differenct environments (dev, staging and prod)
- Has capability of setting a JWT token and use it bearer token

In "src" folder the web application is available with it's Dockerfile.
Create a docker and use it's imaage in the helm chart values.

To add JWT token use secrets.yaml in /chart/ path, example is shown below

```sh
apiVersion: v1
kind: Secret
metadata:
  name: jwt-token
type: Opaque
data:
  ACCESS_TOKEN_SECRET: 1f4caee5b193fddb26762e97ab5a38630ad60f6dddf5dab8748b39877b3e604c81c75072245b416398e27388be9b42cd715274d5743375e135630d088e2e74d4
  REFRESH_TOKEN_SECRET: 18f44d3342c2af59e7c4b84cfb9c3ee9723f0786ab1587155459e6181a9364e51f697057640a8930c4183badbb059b0c6438eea214511d0f4008ed2413992803
```

Here is an example on how to use it in different environments

```sh
helm install release1 sample-app -n dev -f values-dev.yaml
helm install release2 sample-app -n staging -f values-staging.yaml
helm install release3 sample-app -n prod -f values-prod.yaml
```