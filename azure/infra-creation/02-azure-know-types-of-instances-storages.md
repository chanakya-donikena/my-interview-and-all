## Command to find Types of VMs and their capacity

az vm list-sizes --location eastus --output table

## Example output

Name                NumberOfCores    MemoryInMb
------------------  ---------------  ----------
Standard_DS1_v2     1                3584
Standard_DS2_v2     2                7168


## to find for a specific VM

az vm list-sizes --location eastus \
  --query "[?name=='Standard_DS1_v2']"
