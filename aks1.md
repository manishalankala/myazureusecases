


------------------------------------------------------------------------------------------------------------------------------------------------


1. Create resource group

2. Create storage account

3. Create a Virtual Network

4. Create AKS Cluster





--------------------------------------------------------------------------------------------------------------------------------------------------








# Create resource group

409-f254f4d6-create-an-aks-cluster-that-uses-azure




# Create storage account

name : storaazr2umked42y

Location ; Central US

Replication ; Locally-redundant storage (LRS)

Account kind : Storage (general purpose v1)

![image](https://user-images.githubusercontent.com/33985509/103159884-e2de8100-47ce-11eb-9ff4-9bb919a66feb.png)




# Create a Virtual Network




az network vnet create -g 409-f254f4d6-create-an-aks-cluster-that-uses-azure -n myvnet --address-prefix 10.0.0.0/16 --subnet-name default --subnet-prefix 10.0.0.0/21


![image](https://user-images.githubusercontent.com/33985509/103159920-7fa11e80-47cf-11eb-80d6-9f0dc9cf1509.png)


![image](https://user-images.githubusercontent.com/33985509/103159923-90519480-47cf-11eb-9ebb-34e1a09e79e8.png)





# Create a New AKS Cluster


Go to kubernetes services


![image](https://user-images.githubusercontent.com/33985509/103159322-60eb5980-47c8-11eb-8c82-f8d21c8d97c6.png)


![image](https://user-images.githubusercontent.com/33985509/103159327-80828200-47c8-11eb-8212-299804f0d6f4.png)


![image](https://user-images.githubusercontent.com/33985509/103159335-92fcbb80-47c8-11eb-9158-b4063bbfec65.png)


![image](https://user-images.githubusercontent.com/33985509/103159345-a9a31280-47c8-11eb-93f3-6bc0b5be0d87.png)


![image](https://user-images.githubusercontent.com/33985509/103159358-c93a3b00-47c8-11eb-97a5-6ec1cf9c1a54.png)


![image](https://user-images.githubusercontent.com/33985509/103159983-37363080-47d0-11eb-92f3-cb793dee7169.png)

![image](https://user-images.githubusercontent.com/33985509/103159991-43ba8900-47d0-11eb-877b-b3bd9da52457.png)




![image](https://user-images.githubusercontent.com/33985509/103159433-a6f4ed00-47c9-11eb-85e4-51ca351f6093.png)


![image](https://user-images.githubusercontent.com/33985509/103159442-bd02ad80-47c9-11eb-8f27-34998439b94c.png)



In Container monitoring, click Disabled

Click Review + create



![image](https://user-images.githubusercontent.com/33985509/103160018-7bc1cc00-47d0-11eb-9c59-66bdbae5829f.png)


![image](https://user-images.githubusercontent.com/33985509/103160035-b9bef000-47d0-11eb-8562-f957e9390460.png)


![image](https://user-images.githubusercontent.com/33985509/103160063-f38ff680-47d0-11eb-985f-66576129932a.png)


![image](https://user-images.githubusercontent.com/33985509/103160072-0acee400-47d1-11eb-98d8-67e5a97de523.png)


![image](https://user-images.githubusercontent.com/33985509/103160075-1b7f5a00-47d1-11eb-894e-2b5485ec081c.png)


![image](https://user-images.githubusercontent.com/33985509/103160093-410c6380-47d1-11eb-905e-66e45ccbb757.png)



az aks list


az aks get-credentials -g 409-f254f4d6-create-an-aks-cluster-that-uses-azure -n cluster01



![image](https://user-images.githubusercontent.com/33985509/103160125-a2343700-47d1-11eb-8497-b24342570e47.png)


![image](https://user-images.githubusercontent.com/33985509/103160190-1b338e80-47d2-11eb-8daf-1d8b0d9c640a.png)


![image](https://user-images.githubusercontent.com/33985509/103160272-17ecd280-47d3-11eb-86c9-758dcb2a2b71.png)


kubectl run -it virtula-node-test --image=debian


![image](https://user-images.githubusercontent.com/33985509/103160321-cf81e480-47d3-11eb-84d6-27b9e317f596.png)

curl -L http://10.0.8.4


kubectl get pods -n kube-system


kubernetes cluster ip - 10.1.0.1

kube-dns cluster ip - 10.1.0.10




deploy.yml

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: aci-helloworld
spec:
  replicas: 1
  selector:
    matchLabels:
      app: aci-helloworld
  template:
    metadata:
      labels:
        app: aci-helloworld
    spec:
      containers:
        - name: aci-helloworld
          image: microsoft/aci-helloworld
          ports:
            - containerPort: 80
      nodeSelector:
        kubernetes.io/role: agent
        beta.kubernetes.io/os: linux
        type: virtual-kubelet
      tolerations:
        - key: virtual-kubelet.io/provider
          operator: Exists




```
