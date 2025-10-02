# Setup Guide — Avatar Cloud Demo

This guide explains how to deploy the Avatar Cloud Demo: an IIS-hosted ASP.NET app connected to Azure SQL Database.

## 1. Prerequisites
- Azure subscription (South Africa North region)
- Resource group: `rg-my-avatar-spoke`
![Resource Group](../diagrams/rg-avatar-spoke.png)
- Log Analytics workspace: `la-avatar-demo`
![Log Analytics Workspace](../diagrams/la-workspace.png)
- Visual Studio Code / PowerShell / Azure CLI

## 2. Deploy Infrastructure
1. Create a Windows Server VM 
![Windows Server VM Creation](../diagrams/vm_create_ws2019_running.png)
![Windows Server VM Creation](../diagrams/vm_ws2019.png)


   - Size: Standard B2s (demo-friendly)
   - NSG: Allow HTTP (80/8080) + RDP (3389, restricted to your IP)
   ![NSG Allow HTTP (80/8080) + RDP 3389](../diagrams/nsg_creation.png)
   ![NSG Allow HTTP (80/8080) + RDP 3389](../diagrams/nsg_port80_allow.png)
   ![NSG Allow HTTP (80/8080) + RDP 3389](../diagrams/nsg_rule_source_ip_port.png)



2. Create Azure SQL Database
   - Server: `avatar-sql-server-01`
   ![SQL Server Create](../diagrams/logical_sql_server.png)
   - Database: `appdb`
   ![SQL Database Creation](../diagrams/db.png)
   - Tier: Basic/S0 (demo-friendly)

3. Configure Networking
   - SQL firewall: allow VM public IP + your workstation IP
   ![SQL Firewall Rules](../diagrams/firewall_rules_az_services.png)
   - Disable “Allow Azure services” unless required
   ![SQL Server Access Rules](../diagrams/avatar_sql_networking.png)

## 3. Configure IIS + App 
1. Install IIS + ASP.NET features on the VM
![VM RDP Connect](../diagrams/vm_connect.png)
![VM Access](../diagrams/in_vm.png)
![Table Creation](../diagrams/table_created.png)
![DB Schema](../diagrams/sql_schema.png)
![Web Config](../diagrams/webconfig.png)
![Site Tree](../diagrams/site_tree.png)
![AppDemoSite Port Allocation](../diagrams/iism_appdemosite_basicsettings.png)
![Live Site](../diagrams/avatar_cloud_iis_live.png)
![Live DB Test](../diagrams/connection_string%20_error.png)

   
