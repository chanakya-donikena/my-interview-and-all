### azure command to create Kubernetes cluster AKS
az aks create \
  --resource-group kml_rg_main-219268586dd740d6 \
  --name chan-dev-cluster \
  --node-count 2 \
  --node-vm-size Standard_D2s_v3 \
  --enable-managed-identity \
  --generate-ssh-keys



### After creating AKS cluster, close the cloudshell and login again and the enter AKS login commands from "Connect"

### delete AKS cluster  
az aks delete \
  --resource-group kml_rg_main-219268586dd740d6 \
  --name chan-dev-cluster \
  --yes \
  --no-wait
  
  
