




az group list

az storage account list

az vm list


az vm create -n MYVMTEST -g 72-dd12ac51-accessing-and-using-the-azure-cloud-sh --image UbuntuLTS --admin-username azureuser --generate-ssh-keys


Get-AzResourceGroup

Get-AzStorageAccount

Get-AzVM

Get-AzResource | ft

clear



Remove-AzVM -Name myVM -ResourceGroupName 72-dd12ac51-accessing-and-using-the-azure-cloud-sh

Get-AzVM

exit
