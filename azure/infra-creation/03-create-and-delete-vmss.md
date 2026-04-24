### Create VMSS 

az vmss create \
  --resource-group kml_rg_main-219268586dd740d6 \
  --name chan-dev-vmss \
  --image Ubuntu2204 \
  --instance-count 2 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --os-disk-size-gb 30 \
  --storage-sku Standard_LRS
  
### INFO : 30Gb is the minimum value to be set for VMSS storage. else, it won't work  
  
### Delete VMSS command

az vmss delete \
  --name chan-dev-vmss \
  --resource-group kml_rg_main-219268586dd740d6  
