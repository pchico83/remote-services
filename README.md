# remote-services

A sample to develop with remote service running on Okteto

## Development workflow

- [Install the Okteto CLI](https://okteto.com/docs/getting-started/installation).
- Login to your Okteto Instance:
  ```
     $ okteto login https://pulsarplatform.okteto.dev/
     ✓ Logged in as pchico83 @ https://pulsarplatform.okteto.dev
       Run `okteto namespace` to switch your context and download your Kubernetes credentials.
  ```
- Fetch your Kubernetes credentials:
  ```
     $ okteto namespace
     ✓ Updated context 'pulsarplatform_okteto_dev' in '/Users/pablo/.kube/config'
   ```
- Deploy the Okteto Stack (check the file `okteto-stack.yml` for further configurations):
  ```
     $ okteto stack deploy
     ✓ Successfully deployed stack 'services'
  ```
  Okteto Stacks is a docker-compose like format to deploy to Kubernetes. Full docs are [available here](https://okteto.com/docs/reference/stacks).
- Go to the [Okteto UI](https://pulsarplatform.okteto.dev) and wait for your services to be up and running.
- Forward ports to localhost:
  ```
     $ okteto up
     ✓ Development container activated
     ✓ Connected to your development container
     ✓ Files synchronized
       Context:   pulsarplatform_okteto_dev
       Namespace: pchico83
       Name:      proxy
       Forward:   4306 -> 3306
                  5432 -> postgres:5432
                  7379 -> redis:6379
                  9983 -> solr:8983
                  10042 -> cassandra:9042
  ```
  `okteto up` creates a development container where your local code changes are synchronized. In this case we are just creating a fake environment to do port-forwards. Okteto port-forwards use SSH tunnels and are more reliable than standard `kubectl port-forward` commands.

From this moment, your services should be available in localhost.

## Alternative ways to deploy the Okteto Stack

You can also deploy the Okteto Stack by deploying the repo URL https://github.com/pchico83/remote-services from the [Okteto UI](https://pulsarplatform.okteto.dev), or just by clicking on this button:

[![Develop on Okteto](https://okteto.com/develop-okteto.svg)](https://pulsarplatform.okteto.dev/deploy?repository=https://github.com/pchico83/remote-services)


