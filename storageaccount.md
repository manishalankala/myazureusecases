
1.Create a Storage Account

2.Enable versioning & soft delete

3.Create a Blob Container

4.upload item to storage

5.Reference links








---------------------------------------------------------------------------------------------------------
# Create a Storage Account
---------------------------------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/33985509/103046196-a705aa80-4587-11eb-9ad5-b034bc4734e4.png)


Replication:

LRS = Locally redundant storage

ZRS = Zone redundant

GRS = Geo redundant storage

RA-GRS = Read access Geo redundant storage

GZRS = Geo zone redundant storage

RA-GZRS = Read access Geo zone redundant storage


![image](https://user-images.githubusercontent.com/33985509/103046357-34e19580-4588-11eb-97a3-a10026d32bed.png)

---------------------------------------------------------------------------------------------------------
# Enable versioning & soft delete
---------------------------------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/33985509/103046404-635f7080-4588-11eb-94bc-f7f39ab2b099.png)

![image](https://user-images.githubusercontent.com/33985509/103046542-eda7d480-4588-11eb-8655-a44d12151f82.png)

![image](https://user-images.githubusercontent.com/33985509/103046553-f7c9d300-4588-11eb-8990-7feff751c1b5.png)

---------------------------------------------------------------------------------------------------------
# Create a Blob Container
---------------------------------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/33985509/103046846-ecc37280-4589-11eb-93d1-a365557f189f.png)

![image](https://user-images.githubusercontent.com/33985509/103046929-3449fe80-458a-11eb-8d7d-d6743ffd7554.png)

![image](https://user-images.githubusercontent.com/33985509/103046953-47f56500-458a-11eb-9350-2f469ae56415.png)

![image](https://user-images.githubusercontent.com/33985509/103046978-5774ae00-458a-11eb-925e-583574501aa4.png)

---------------------------------------------------------------------------------------------------------
# upload item to storage
---------------------------------------------------------------------------------------------------------


![image](https://user-images.githubusercontent.com/33985509/103047067-960a6880-458a-11eb-8c16-f11b1ac832a5.png)


![image](https://user-images.githubusercontent.com/33985509/103047298-4d9f7a80-458b-11eb-883b-532c8aea9d97.png)


https://teststoragemine.blob.core.windows.net/mine1/IMG1.JPG

![image](https://user-images.githubusercontent.com/33985509/103047331-6d36a300-458b-11eb-8623-a1bc28376f6e.png)


Hot - Optimized for storing data that is accessed frequently.

Cool - Optimized for storing data that is infrequently accessed and stored for at least 30 days.

Archive - Optimized for storing data that is rarely accessed and stored for at least 180 days with flexible latency requirements (on the order of hours).


---------------------------------------------------------------------------------------------------------
# Reference links
---------------------------------------------------------------------------------------------------------

https://docs.microsoft.com/en-us/azure/storage/common/infrastructure-encryption-enable?tabs=portal#register-to-use-infrastructure-encryption

https://docs.microsoft.com/en-us/azure/storage/blobs/network-file-system-protocol-support


https://docs.microsoft.com/en-us/azure/storage/common/account-encryption-key-create?tabs=powershell#register-to-use-the-account-encryption-key
