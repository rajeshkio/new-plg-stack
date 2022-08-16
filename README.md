kubectl create ns monitoring
 kubectl create ns demo
 kubectl create ns sock-shop
 helm upgrade --install loki grafana/loki-stack -n monitoring --set grafana.enabled=true
 kubectl get secret --namespace monitoring loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
 helm upgrade --install promtail grafana/promtail -n monitoring --values prom-values.yaml
 kubectl config set-context --current --namespace=monitoring
 kubectl get secret --namespace monitoring loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
 kubectl apply -f application/ -n demo
 kubectl apply -f application/
 helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
 helm upgrade --install prometheus prometheus-community/kube-prometheus-stack --set grafana.enabled=false --values prometheus-values.yaml
 helm upgrade --install prometheus prometheus-community/kube-prometheus-stack --set grafana.enabled=false --values monitoring/prometheus-values.yaml
 kubectl apply -f application/ -n demo
 kubectl apply -f manifests/ -n sock-shop

