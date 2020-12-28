








resource-group: 1-82ea24fa-playground-sandbox

Storage account : storage112211

name: my-cluster

kubernetes-version: 1.18.10

location: eastus2

node-count: 3

generate-ssh-keys



az aks create --resource-group 1-82ea24fa-playground-sandbox --name my-cluster --kubernetes-version 1.18.10 --location eastus2 --node-count 3 --generate-ssh-keys


"dnsServiceIp": "10.0.0.10",

"dockerBridgeCidr": "172.17.0.1/16",

nodeImageVersion": "AKSUbuntu-1804-2020.12.15",

 "nodeLabels": {},
 
 "nodeTaints": null,
 
 "orchestratorVersion": "1.18.10",
 
 "osDiskSizeGb": 128,
 
vmSize": "Standard_DS2_v2"

 "principalId": "6c4ea5c0-2bc4-4140-a79a-2d5399c9d5c7",
 
 "tenantId": "3617ef9b-98b4-40d9-ba43-e1ed6709cf0d"
 
"adminUsername": "azureuser",

"location": "eastus2",

  "maxAgentPools": 10,
  
  "name": "my-cluster",
  
  "networkMode": null,
  
    "networkPlugin": "kubenet",
    
    "networkPolicy": null,
    
    "outboundType": "loadBalancer",
    
    "podCidr": "10.244.0.0/16",
    
  "serviceCidr": "10.0.0.0/16"
  

"nodeResourceGroup": "MC_1-82ea24fa-playground-sandbox_my-cluster_eastus2"


az aks get-credentials --resource-group 1-82ea24fa-playground-sandbox --name my-cluster


kubectl cluster-info

Kubernetes control plane is running at https://my-cluster-1-82ea24fa-playg-4cedc5-53c82bfa.hcp.eastus2.azmk8s.io:443

CoreDNS is running at https://my-cluster-1-82ea24fa-playg-4cedc5-53c82bfa.hcp.eastus2.azmk8s.io:443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

Metrics-server is running at https://my-cluster-1-82ea24fa-playg-4cedc5-53c82bfa.hcp.eastus2.azmk8s.io:443/api/v1/namespaces/kube-system/services/https:metrics-server:/proxy


kubectl apply -f azure-vote-all-in-one-redis.yaml

![image](https://user-images.githubusercontent.com/33985509/103198241-1cef7600-48e8-11eb-9bba-fd4463a21dfe.png)

![image](https://user-images.githubusercontent.com/33985509/103198429-99825480-48e8-11eb-9c59-94b6fd684541.png)




```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: azure-vote-back
spec:
  replicas: 1
  selector:
    matchLabels:
      app: azure-vote-back
  template:
    metadata:
      labels:
        app: azure-vote-back
    spec:
      nodeSelector:
        "beta.kubernetes.io/os": linux
      containers:
      - name: azure-vote-back
        image: mcr.microsoft.com/oss/bitnami/redis:6.0.8
        env:
        - name: ALLOW_EMPTY_PASSWORD
          value: "yes"
        ports:
        - containerPort: 6379
          name: redis
---
apiVersion: v1
kind: Service
metadata:
  name: azure-vote-back
spec:
  ports:
  - port: 6379
  selector:
    app: azure-vote-back
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: azure-vote-front
spec:
  replicas: 1
  selector:
    matchLabels:
      app: azure-vote-front
  strategy:
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1
  minReadySeconds: 5 
  template:
    metadata:
      labels:
        app: azure-vote-front
    spec:
      nodeSelector:
        "beta.kubernetes.io/os": linux
      containers:
      - name: azure-vote-front
        image: mcr.microsoft.com/azuredocs/azure-vote-front:v1
        ports:
        - containerPort: 80
        resources:
          requests:
            cpu: 250m
          limits:
            cpu: 500m
        env:
        - name: REDIS
          value: "azure-vote-back"
---
apiVersion: v1
kind: Service
metadata:
  name: azure-vote-front
spec:
  type: LoadBalancer
  ports:
  - port: 80
  selector:
    app: azure-vote-front





```
