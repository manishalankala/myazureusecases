


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







![image](https://user-images.githubusercontent.com/33985509/103159433-a6f4ed00-47c9-11eb-85e4-51ca351f6093.png)


![image](https://user-images.githubusercontent.com/33985509/103159442-bd02ad80-47c9-11eb-8f27-34998439b94c.png)



In Container monitoring, click Disabled

Click Review + create


![image](https://user-images.githubusercontent.com/33985509/103159464-018e4900-47ca-11eb-9d24-dd6d343f8f55.png)



![image](https://user-images.githubusercontent.com/33985509/103159502-6b0e5780-47ca-11eb-8f2b-55ea247180bd.png)


#Run and Test an App on the Virtual Nodes
