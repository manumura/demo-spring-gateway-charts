### Commands

# Create release

``` helm create demo-gateway-chart ```

``` helm template demo-gateway-chart ```

``` helm lint demo-gateway-chart ```

``` helm install demo-gateway-chart --debug --dry-run demo-gateway-chart ```

``` helm install demo-gateway-release demo-gateway-chart ```

``` helm list -a ```

``` kubectl get all ```

``` kubectl get deployments ```

``` kubectl get pods ``` AND ``` kubectl logs ${POD_NAME} ```

``` helm upgrade demo-gateway-release demo-gateway-chart ```

``` helm delete demo-gateway-release ```

# Get a shell to the running container

``` kubectl exec --stdin --tty <POD_NAME> -- bash ```

``` apt-get update; apt-get install curl ```

``` curl demo-gateway-client2:8080/config/topics ``` OR ``` curl demo-gateway-client2.default.svc.cluster.local:8080/config/topics ``` (<service-name>.<namespace>.svc.cluster.local:<port>)

``` env ``` (show environment variables)

# Deploy to namespace

``` kubectl create namespace dev ```

``` helm install -n dev -f demo-gateway-chart/environments/values.dev.yaml demo-gateway-release demo-gateway-chart ```

``` helm delete demo-gateway-release -n dev ```