# Istio-setup

Download istioctl - https://istio.io/latest/docs/setup/getting-started/#download


This would install the istio with the above file manifest .

1.Istioctl install -f istio-install.yaml. 
2. Dashboards after you install - 
  a) istioctl dashboard grafana - default username/password - admin/admin
  b) istioctl dashboard prometheus
3. kubectl label namespace default istio-injection=enabled
4. kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
5. kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
6. export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
7. export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
8. export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')
9. export TCP_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="tcp")].port}')
10. export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
11. curl -s "http://${GATEWAY_URL}/productpage" | grep -o "<title>.*</title>"
<title>Simple Bookstore App</title>

12. kubectl apply -f samples/bookinfo/networking/destination-rule-all.yaml
13. samples/bookinfo/platform/kube/cleanup.sh

# Configure AWS CLI -
1. Download aws cli - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html 
2. Add the cli bin to path variables on windows. 
3. Configure your cli by command - *aws configure* . Official documentation link - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html
4. Connect to your EKS cluster - https://docs.aws.amazon.com/cli/latest/reference/eks/update-kubeconfig.html 
for eg : aws eks update-kubeconfig --name <aws cluster name> 
  
# Configure Kubectl - 
https://kubernetes.io/docs/tasks/tools/install-kubectl/

