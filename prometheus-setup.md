# Configure helm - 
- helm repo add stable https://kubernetes-charts.storage.googleapis.com/
- helm repo update   

# Configure Prometheus operator -
- helm install prometheus-operator stable/prometheus-operator
- Get the pod name - **kubectl get pods -n management | grep grafana**
- kubectl port-forward grafana-pod-name 3000 -n management 
- You should be able to go to grafana dashboard - http://localhost:3000 
- Use the login credentials to login into grafana. 
- username-"admin" password - "prom-operator"



# Download & Configure AWS CLI -
- Download aws cli - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html
- Add the cli bin to path variables on windows.
- Configure your cli by command - **aws configure** . Official documentation link - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html 
- Connect to your EKS cluster - https://docs.aws.amazon.com/cli/latest/reference/eks/update-kubeconfig.html for eg : **aws eks update-kubeconfig --name your-cluster-name**

# Configure Kubernete CLI -
- https://kubernetes.io/docs/tasks/tools/install-kubectl/

# Generate manual manifest and apply 

- helm show values  stable/prometheus-operator > values.yaml     
- helm install prometheus-operator stable/prometheus-operator -f values.yaml
