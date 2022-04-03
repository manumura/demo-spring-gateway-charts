### Commands

``` helm create demo-gateway-client2-chart ```

``` helm template demo-gateway-client2-chart ```

``` helm lint demo-gateway-client2-chart ```

``` helm install demo-gateway-client2-chart --debug --dry-run demo-gateway-client2-chart ```

``` helm install demo-gateway-client2-release demo-gateway-client2-chart ```

``` helm list -a ```

``` kubectl get all ```

``` kubectl get deployments ```

``` kubectl get pods ``` AND ``` kubectl logs ${POD_NAME} ```

``` helm upgrade demo-gateway-client2-release demo-gateway-client2-chart ```

``` helm delete demo-gateway-client2-release ```

# Get a shell to the running container

``` kubectl exec --stdin --tty <POD_NAME> -- bash ```

``` apt-get update; apt-get install curl ```

``` curl demo-gateway-client1:8080/config/topics ``` OR ``` curl demo-gateway-client1.default.svc.cluster.local:8080/config/topics ``` (<service-name>.<namespace>.svc.cluster.local:<port>)

``` env ``` (show environment variables)

# Deploy to namespace

``` kubectl create namespace dev ```

``` helm install -n dev -f demo-gateway-client2-chart/environments/values.dev.yaml demo-gateway-client2-release demo-gateway-client2-chart ```

``` helm delete demo-gateway-client2-release -n dev ```