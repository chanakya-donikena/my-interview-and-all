### create a virtual network 
az network vnet create \
  --resource-group $RES_GRP \
  --name chan-dev \
  --address-prefix 10.0.0.0/16 \
  --subnet-name chan-dev-public \
  --subnet-prefix 10.0.1.0/24
  
### create a subnet  
az network vnet subnet create \
  --resource-group $RES_GRP \
  --vnet-name chan-dev \
  --name chan-dev-private \
  --address-prefix 10.0.2.0/24
  
### create a public ip for nat gateway
az network public-ip create \
  --resource-group $RES_GRP \
  --name chan-dev-nat-pip \
  --sku Standard \
  --allocation-method Static
  
### create a nat gateway
az network nat gateway create \
  --resource-group $RES_GRP \
  --name chan-dev-natgw \
  --public-ip-addresses chan-dev-nat-pip \
  --idle-timeout 10
  
### Associate NAT gateway with private subnet
az network vnet subnet update \
  --resource-group $RES_GRP \
  --vnet-name chan-dev \
  --name chan-dev-private \
  --nat-gateway chan-dev-natgw
  
### create NIC 
az network nic create \
  --resource-group $RES_GRP \
  --name chan-dev-private-nic \
  --vnet-name chan-dev \
  --subnet chan-dev-private \
  --private-ip-address-version IPv4
  
### Create VM using the NIC  ## "--storage-sku Standard_LRS" for cheaper storage || or || use StandardSSD_LRS for cheap and best
az vm create \
  --resource-group $RES_GRP \
  --name chan-private-server-1 \
  --location eastus \
  --nics chan-dev-private-nic \
  --image Canonical:0001-com-ubuntu-server-jammy:22_04-lts:latest \
  --size Standard_B2s \
  --os-disk-name chan-private-server-1-osdisk \
  --os-disk-size-gb 64 \
  --storage-sku StandardSSD_LRS \
  --admin-username azureuser \
  --authentication-type ssh \
  --ssh-key-values ~/.ssh/id_rsa.pub \
  --boot-diagnostics-storage ""
  
### create Public IP for Bastion
az network public-ip create \
  --resource-group $RES_GRP \
  --name bastion-pip \
  --sku Standard \
  --location eastus
 
### command to list the subnets 
az network vnet subnet list \
  --resource-group $RES_GRP \
  --vnet-name chan-dev \
  --output table
  
### command to create subnet for Bastion  
az network vnet subnet create \
  --resource-group $RES_GRP \
  --vnet-name chan-dev \
  --name AzureBastionSubnet \
  --address-prefixes 10.0.3.0/27
  
### command to create Bastion service on Azure  
az network bastion create \
  --resource-group $RES_GRP \
  --name chan-dev-bastion \
  --public-ip-address bastion-pip \
  --vnet-name chan-dev \
  --location eastus \
  --sku Basic
  
  
### Create public ip for LoadBalancer
az network public-ip create \
  --resource-group $RES_GRP \
  --name chan-dev-lb-pip \
  --sku Standard \
  --allocation-method Static \
  --location eastus
  

### Create LoadBalancer
az network lb create \
  --resource-group $RES_GRP \
  --name chan-dev-lb \
  --sku Standard \
  --public-ip-address chan-dev-lb-pip \
  --frontend-ip-name lb-frontend \
  --backend-pool-name lb-backend \
  --location eastus
  
### Create Health Probe 
az network lb probe create \
  --resource-group $RES_GRP \
  --lb-name chan-dev-lb \
  --name http-probe \
  --protocol Tcp \
  --port 80
  
### Create loadbalancing rule
az network lb rule create \
  --resource-group $RES_GRP \
  --lb-name chan-dev-lb \
  --name http-rule \
  --protocol Tcp \
  --frontend-port 80 \
  --backend-port 80 \
  --frontend-ip-name lb-frontend \
  --backend-pool-name lb-backend \
  --probe-name http-probe \
  --load-distribution Default
