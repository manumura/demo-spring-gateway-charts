# demo-spring-gateway-charts

## Install Redis on Kubernetes: https://phoenixnap.com/kb/kubernetes-redis

``` helm repo add bitnami https://charts.bitnami.com/bitnami ```

``` helm repo update ```

``` helm install redis-test --set persistence.storageClass=nfs-client,redis.replicas.persistence.storageClass=nfs-client bitnami/redis --set volumePermissions.enabled=true ```

``` export REDIS_PASSWORD=$(kubectl get secret --namespace default redis-test -o jsonpath="{.data.redis-password}" | base64 --decode) ```

``` kubectl run --namespace default redis-client --restart='Never'  --env REDIS_PASSWORD=$REDIS_PASSWORD  --image docker.io/bitnami/redis:6.2.6-debian-10-r146 --command -- sleep infinity ```

``` kubectl exec --tty -i redis-client --namespace default -- bash ```

``` redis-cli -h redis-test-master -a $REDIS_PASSWORD ``` OR ``` redis-cli -h redis-test-replicas -a $REDIS_PASSWORD ```

``` kubectl port-forward --namespace default svc/redis-test-master 6379:6379 ```

## Install ingress controller: https://bitnami.com/stack/nginx-ingress-controller/helm

``` helm install nginx-ingress-controller-release bitnami/nginx-ingress-controller ```

## Install Prometheus / Grafana : https://tanzu.vmware.com/developer/guides/observability-prometheus-grafana-p1/

``` helm install prometheus bitnami/kube-prometheus ```

``` kubectl port-forward --namespace default svc/prometheus-kube-prometheus-prometheus 9090:9090 ```

``` helm install grafana bitnami/grafana ```

``` kubectl port-forward --namespace default svc/grafana 3000:3000 ```

``` echo "User: admin" ``` AND ``` echo "Password: $(kubectl get secret grafana-admin --namespace default -o jsonpath="{.data.GF_SECURITY_ADMIN_PASSWORD}" | base64 --decode)" ```

## Install ArgoCD : https://www.arthurkoziel.com/setting-up-argocd-with-helm/

``` helm install argo-cd-release bitnami/argo-cd ```

``` kubectl port-forward --namespace default svc/argo-cd-release-server 8080:80 ```

``` echo "Username: admin" ``` AND ``` echo "Password: $(kubectl -n default get secret argocd-secret -o jsonpath="{.data.clearPassword}" | base64 -d)" ```