## Create a SQL Server
## Azure SQL databases live inside a logical SQL server.
az sql server create \
  --name chan-dev-sql-server-12345 \
  --resource-group kml_rg_main-d77e6a74799c48ae \
  --location eastus \
  --admin-user myadminuser \
  --admin-password MyStrongP@ssword123
  
 
## Configure Firewall Rule (Allow your IP)
## Otherwise you won’t be able to connect. 
az sql server firewall-rule create \
  --resource-group kml_rg_main-d77e6a74799c48ae \
  --server chan-dev-sql-server-12345 \
  --name AllowMyIP \
  --start-ip-address 0.0.0.0 \
  --end-ip-address 0.0.0.0
  
 
## Create the SQL Database
az sql db create \
  --resource-group kml_rg_main-d77e6a74799c48ae \
  --server chan-dev-sql-server-12345 \
  --name chan-dev-database \
  --service-objective S0 \
  --backup-storage-redundancy Local \
  --max-size 50GB
  
  
## Get Connection String
az sql db show-connection-string \
  --client ado.net \
  --name chan-dev-database \
  --server chan-dev-sql-server-12345
  
## Example output for Connection String
Server=tcp:chan-dev-sql-server-12345.database.windows.net,1433;
Initial Catalog=chan-dev-database;
Persist Security Info=False;
User ID=<username>;
Password=<password>;
MultipleActiveResultSets=False;
Encrypt=true;
TrustServerCertificate=False;
Connection Timeout=30;

## Delete SQL database server
az sql server delete \
  --name chan-dev-sql-server-12345 \
  --resource-group kml_rg_main-d77e6a74799c48ae \
  --yes

## If you want to delete only the DB instead of DB server
az sql db delete \
  --resource-group kml_rg_main-d77e6a74799c48ae \
  --server chan-dev-sql-server-12345 \
  --name chan-dev-database \
  --yes
