# Istio-setup


istioctl install -f istio-install.yaml
This would install the istio with the above file manifest .

1. istioctl dashboard prometheus
2. istioctl dashboard grafana
3. kubectl label namespace default istio-injection=enabled
4. kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
5. kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
6. export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
7. export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
8. export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')
9. export TCP_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="tcp")].port}')
10.  export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
11. curl -s "http://${GATEWAY_URL}/productpage" | grep -o "<title>.*</title>"
<title>Simple Bookstore App</title>

12. kubectl apply -f samples/bookinfo/networking/destination-rule-all.yaml
13. samples/bookinfo/platform/kube/cleanup.sh

