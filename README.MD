# Azure ARM Templates for Resource Deployment

This repository contains two Azure Resource Manager (ARM) templates for deploying Azure resources. These templates help automate the provisioning of infrastructure in Azure.

---

## Files in This Repository

### 1. `create-vm.json`
This template provisions a virtual machine along with its associated resources. The following resources are created:
- **Storage Account**: For storing diagnostic logs and VM-related data.
- **Public IP Address**: For external access to the virtual machine.
- **Network Security Group (NSG)**: With a rule allowing inbound SSH (port 22).
- **Virtual Network (VNet)**: Configured with a subnet linked to the NSG.
- **Network Interface**: Connects the VM to the virtual network.
- **Virtual Machine (VM)**: An Ubuntu 16.04-LTS virtual machine with the size `Standard_A2_v2`.

#### Key Features
- Secure SSH access.
- Dynamic public IP allocation.
- Pre-configured diagnostics for boot logs.

---

### 2. `storage-account.json`
This template provisions a storage account with customizable parameters.

#### Parameters
- **`StorageAccountTier`**: Defines the storage account tier. Defaults to `Premium`. Allowed values are:
  - `Premium`
  - `Standard`

#### Key Features
- Creates a `StorageV2` type account.
- Configurable tier for different performance needs.
- Named resource for easier identification.

---

## Usage

### Prerequisites
- Azure CLI installed and authenticated.
- Proper permissions to deploy resources in an Azure subscription.
- A resource group already created in the desired region.

### Deployment Steps
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name

2. Deploy the templates using Azure CLI:

    ### For create-vm.json:
```bash
    az deployment group create \
  --resource-group <resource-group-name> \
  --template-file create-vm.json

