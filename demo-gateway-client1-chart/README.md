### Commands

``` helm create demo-gateway-client1-chart ```

``` helm template demo-gateway-client1-chart ```

``` helm lint demo-gateway-client1-chart ```

``` helm install demo-gateway-client1-chart --debug --dry-run demo-gateway-client1-chart ```

``` helm install demo-gateway-client1-release demo-gateway-client1-chart ```

``` helm list -a ```

``` kubectl get all ```

``` kubectl get deployments ```

``` kubectl get pods ``` AND ``` kubectl logs ${POD_NAME} ```

``` helm upgrade demo-gateway-client1-release demo-gateway-client1-chart ```

``` helm delete demo-gateway-client1-release ```

# Get a shell to the running container

``` kubectl exec --stdin --tty <POD_NAME> -- bash ```

``` apt-get update; apt-get install curl ```

``` curl demo-gateway-client2:8080/config/topics ``` OR ``` curl demo-gateway-client2.default.svc.cluster.local:8080/config/topics ``` (<service-name>.<namespace>.svc.cluster.local:<port>)

``` env ``` (show environment variables)

# Deploy to namespace

``` kubectl create namespace dev ```

``` helm install -n dev -f demo-gateway-client1-chart/environments/values.dev.yaml demo-gateway-client1-release demo-gateway-client1-chart ```

``` helm delete demo-gateway-client1-release -n dev ```