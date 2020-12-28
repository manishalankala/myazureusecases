## Contents


1.Check Azure Resource Provider

2.Creating a Resource Group

3.Current AKS Versions

4.Creating the AKS Cluster

5.Retrieving your Credentials

6.Validating the Cluster

7.Deploying 

8.Delete

-------------------------------------------------------------------------------------------------------------------------------

## Requirements :

A Microsoft Azure subscription

Owner or User Access Administrator role on the Azure subscription

Permission to create and register applications on Azure Active Directory


Launch Cloud Shell

![image](https://user-images.githubusercontent.com/33985509/103198761-74421600-48e9-11eb-8527-27d6f6b25640.png)


![image](https://user-images.githubusercontent.com/33985509/103198785-7dcb7e00-48e9-11eb-92a0-e975970bef07.png)


![image](https://user-images.githubusercontent.com/33985509/103198852-a5bae180-48e9-11eb-8356-a5b926be78a6.png)








"az account show"







![image](https://user-images.githubusercontent.com/33985509/103198950-e7e42300-48e9-11eb-8d4b-1151dc2948a1.png)



az account list


select the correct account by noting the subscription name field and running


az account select --subscription SUBSCRIPTION_NAME



-------------------------------------------------------------------------------------------------------------------------------

## Check Azure Resource Provider


az provider list --query "[?registrationState=='Registered'].{Name:namespace, State:registrationState}" -o table



providers are not registered, run the az provider register command as shown below, replacing the PROVIDER_NAME with the actual name of the provider.


az provider register --namespace PROVIDER_NAME --wait



----------------------------------------------------------------------------------------------------------------------------------


## Creating a Resource Group

az group create --name my-cluster --location eastus2

az group list

![image](https://user-images.githubusercontent.com/33985509/103199290-d2232d80-48ea-11eb-96f0-1cfad70aec01.png)


-----------------------------------------------------------------------------------------------------------------------------------


## Current AKS Versions

az aks get-versions --location eastus2 -o table

![image](https://user-images.githubusercontent.com/33985509/103199399-131b4200-48eb-11eb-8adf-c6321221e957.png)



---------------------------------------------------------------------------------------------------------------------------------


## Creating the AKS Cluster



az aks create subcommand also automatically creates a service principal for the cluster to use when interacting with other services in Microsoft Azure




az aks create --resource-group 1-82ea24fa-playground-sandbox --name my-cluster --kubernetes-version 1.18.10 --location eastus2 --node-count 3 --generate-ssh-keys


resource-group: 1-82ea24fa-playground-sandbox

Storage account : storage112211

name: my-cluster

kubernetes-version: 1.18.10

location: eastus2

node-count: 3

generate-ssh-keys




```
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

```


------------------------------------------------------------------------------------------------------------------------------------

## Retrieving your Credentials


az aks get-credentials --resource-group 1-82ea24fa-playground-sandbox --name my-cluster




------------------------------------------------------------------------------------------------------------------------------------

## Validating the Cluster

kubectl get nodes


![image](https://user-images.githubusercontent.com/33985509/103199836-18c55780-48ec-11eb-8b00-c53ac455c67f.png)



kubectl cluster-info

Kubernetes control plane is running at https://my-cluster-1-82ea24fa-playg-4cedc5-53c82bfa.hcp.eastus2.azmk8s.io:443

CoreDNS is running at https://my-cluster-1-82ea24fa-playg-4cedc5-53c82bfa.hcp.eastus2.azmk8s.io:443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

Metrics-server is running at https://my-cluster-1-82ea24fa-playg-4cedc5-53c82bfa.hcp.eastus2.azmk8s.io:443/api/v1/namespaces/kube-system/services/https:metrics-server:/proxy



![image](https://user-images.githubusercontent.com/33985509/103200080-bf115d00-48ec-11eb-99f9-cb7363bfdff9.png)



------------------------------------------------------------------------------------------------------------------------------------


## Deploying a Sample Application


kubectl apply -f azure-vote-all-in-one-redis.yaml

![image](https://user-images.githubusercontent.com/33985509/103198241-1cef7600-48e8-11eb-9bba-fd4463a21dfe.png)

![image](https://user-images.githubusercontent.com/33985509/103198429-99825480-48e8-11eb-9c59-94b6fd684541.png)



------------------------------------------------------------------------------------------------------------------------------------


## Yaml





azure-vote-all-in-one-redis.yaml


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


## Delete




az group delete --name my-cluster
