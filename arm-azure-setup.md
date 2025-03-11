# Implementing IaC with ARM Templates on Azure

## **Introduction**
Azure Resource Manager (ARM) templates allow for the automation of resource deployment in Azure. This guide explains how to deploy an Azure Virtual Machine (VM) using an ARM template.

## **1. Prerequisites**
Before proceeding, ensure you have:
- **An Azure account**
- **Azure CLI installed** (`az --version`)
- **Subscription access to deploy VMs**
- **ARM template (`azure-vm-template.json`)** created

## **2. Create the ARM Template**
The ARM template defines the configuration for the VM, including its size, image, and network settings.

### **File: `azure-vm-template.json`**
```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Compute/virtualMachines",
      "apiVersion": "2022-03-01",
      "name": "MyAzureVM",
      "location": "[resourceGroup().location]",
      "properties": {
        "hardwareProfile": {
          "vmSize": "Standard_B1s"
        },
        "storageProfile": {
          "imageReference": {
            "publisher": "Canonical",
            "offer": "UbuntuServer",
            "sku": "18.04-LTS",
            "version": "latest"
          },
          "osDisk": {
            "createOption": "FromImage"
          }
        },
        "osProfile": {
          "computerName": "MyAzureVM",
          "adminUsername": "azureuser",
          "adminPassword": "YourPassword123!"
        },
        "networkProfile": {
          "networkInterfaces": [
            {
              "id": "[resourceId('Microsoft.Network/networkInterfaces', 'MyNIC')]"
            }
          ]
        }
      }
    }
  ]
}


3. Deploy the VM using Azure CLI
Use the following commands to deploy the VM:

Login to Azure
sh
az login
Create a Resource Group
sh
az group create --name MyResourceGroup --location eastus
Deploy the ARM Template
sh
az deployment group create --resource-group MyResourceGroup --template-file azure-vm-template.json
4. Verify the Deployment
To check if the VM is running:

sh
az vm list --output table
5. Delete the Deployment (Optional)
To remove the VM and all resources:

sh
az group delete --name MyResourceGroup --yes --no-wait
yaml

---

## **3. Create the ARM Template (`azure-vm-template.json`)**  

### **Create the File**  
```sh
touch azure-vm-template.json
Open and Edit the File
sh
code azure-vm-template.json
Paste the ARM Template Code
Copy and paste the JSON template from step 2.

