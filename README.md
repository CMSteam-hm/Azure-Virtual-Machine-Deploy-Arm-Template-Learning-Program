# Azure Linux Virtual Machine ARM Template

## Project Overview

This project demonstrates Infrastructure as Code (IaC) using Azure Resource Manager (ARM) templates. The template deploys a complete Linux Virtual Machine environment in Microsoft Azure, including networking resources and security configurations.

## Resources Deployed

* Ubuntu 24.04 Linux Virtual Machine
* Virtual Network (VNet)
* Subnet
* Public IP Address
* Network Interface Card (NIC)
* Network Security Group (NSG)

## Prerequisites

Before deployment, ensure you have:

* An active Azure Subscription
* Azure CLI installed
* SSH public key generated
* Appropriate permissions to create Azure resources

## Template Structure

### Parameters

User-defined values supplied during deployment:

* vmName
* adminUsername
* vmSize
* sshPublicKey

### Variables

Reusable values generated within the template:

* vnetName
* subnetName
* publicIpName
* nicName

### Resources

Defines all Azure resources created during deployment.

### Outputs

Displays deployment information such as:

* Virtual Machine Name
* Public IP Address

## Deployment Using Azure CLI

```bash
az group create \
  --name MyResourceGroup \
  --location southafricanorth

az deployment group create \
  --resource-group MyResourceGroup \
  --template-file azuredeploy.json \
  --parameters vmName=myLinuxVM \
               adminUsername=azureuser \
               sshPublicKey="$(cat ~/.ssh/id_rsa.pub)"
```

## Validation

The deployment was validated successfully. Screenshots included in this repository demonstrate:

* Successful deployment
* Running Virtual Machine
* SSH connection to the Linux VM

## Files Included

* azuredeploy.json
* deployment-output-log.txt
* VMrunning.PNG
* VMsuccess.PNG

## Author

Created as part of the Azure Infrastructure as Code Lab.
