


# Create resource group

409-1d318bed-create-an-aks-cluster-that-uses-azure



# Create storage account

name : storkr5rzdwthgiak

Location ; Central US

Replication ; Locally-redundant storage (LRS)

Account kind : Storage (general purpose v1)

![image](https://user-images.githubusercontent.com/33985509/103159206-cdfdef80-47c6-11eb-8780-b2f62646bc43.png)




# Create a Virtual Network




az network vnet create -g 409-1d318bed-create-an-aks-cluster-that-uses-azure -n myvnet --address-prefix 172.17.0.0/16 --subnet-name default --subnet-prefix 172.17.1.0/24

![image](https://user-images.githubusercontent.com/33985509/103159274-c25ef880-47c7-11eb-83d4-a475aa01fbac.png)

![image](https://user-images.githubusercontent.com/33985509/103159294-08b45780-47c8-11eb-8833-68f8bb58f96a.png)


![image](https://user-images.githubusercontent.com/33985509/103159304-22559f00-47c8-11eb-8814-28d34a478146.png)




# Create a New AKS Cluster


Go to kubernetes services


![image](https://user-images.githubusercontent.com/33985509/103159322-60eb5980-47c8-11eb-8c82-f8d21c8d97c6.png)


![image](https://user-images.githubusercontent.com/33985509/103159327-80828200-47c8-11eb-8212-299804f0d6f4.png)


![image](https://user-images.githubusercontent.com/33985509/103159335-92fcbb80-47c8-11eb-9158-b4063bbfec65.png)


![image](https://user-images.githubusercontent.com/33985509/103159345-a9a31280-47c8-11eb-93f3-6bc0b5be0d87.png)


![image](https://user-images.githubusercontent.com/33985509/103159358-c93a3b00-47c8-11eb-97a5-6ec1cf9c1a54.png)






![image](https://user-images.githubusercontent.com/33985509/103159428-9e041b80-47c9-11eb-9f07-17d0485e4f83.png)

![image](https://user-images.githubusercontent.com/33985509/103159433-a6f4ed00-47c9-11eb-85e4-51ca351f6093.png)


![image](https://user-images.githubusercontent.com/33985509/103159442-bd02ad80-47c9-11eb-8f27-34998439b94c.png)



In Container monitoring, click Disabled

Click Review + create


![image](https://user-images.githubusercontent.com/33985509/103159464-018e4900-47ca-11eb-9d24-dd6d343f8f55.png)

#Run and Test an App on the Virtual Nodes
