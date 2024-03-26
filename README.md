## Introduction


This README.md provides a summary of key concepts covered in the Terraform Azure course designed to help facilitate quick reviews and aid in learning. Below you'll find sections on various Terraform and Azure topics, along with brief explanations and code examples.
## Terraform Basics
● Infrastructure as Code (IaC): Terraform allows you to define and provision your cloud infrastructure using a high-level configuration language.
● Terraform Configuration Files: Written in HashiCorp Configuration Language (HCL), these files have .tf extensions and allow you to describe the desired state of your cloud resources.
● Terraform Providers: Plugins that interact with cloud providers' APIs. The azurerm provider is used for Azure.
hcl
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "=3.0.0"
    }
  }
}
● Terraform Init: Initializes the working directory, installs the required providers.
● Terraform Plan: Shows the execution plan, what Terraform will do when you apply your configuration.
● Terraform Apply: Executes the plan and creates the described resources.  -auto-approve  -refresh-only
## Azure Resource Management
● Resource Groups: Containers that hold related resources for an Azure solution.
hcl
resource "azurerm_resource_group" "mtc-rg" {
  name     = "mtc-resources"
  location = "East US"
  tags = {
    environment = "dev"
  }
}
● Virtual Networks and Subnets: Allow Azure resources to communicate with each other, the internet, and on-premises networks.
hcl
resource "azurerm_virtual_network" "mtc-vn" {
  name                = "mtc-network"
  location            = azurerm_resource_group.mtc-rg.location
  address_space       = ["10.0.0.0/16"]
}

resource "azurerm_subnet" "mtc-subnet" {
  name                 = "mtc-subnet"
  virtual_network_name = azurerm_virtual_network.mtc-vn.name
  address_prefixes     = ["10.0.1.0/24"]
}
● Network Security Groups (NSGs): Act as a firewall for associated Azure Virtual Networks, filter network traffic.
hcl
resource "azurerm_network_security_group" "mtc-sg" {
  name                = "mtc-sg"
  location            = azurerm_resource_group.mtc-rg.location
}

resource "azurerm_network_security_rule" "mtc-dev-rule" {
  access = "Allow"
  direction = "Inbound"
}
● Public IP Addresses: Provide an identity to your Azure resources on the internet.
hcl
resource "azurerm_public_ip" "mtc-ip" {
  name                = "mtc-ip"
  allocation_method   = "Dynamic"
}
## Virtual Machines
● Azure Linux Virtual Machine: Represents an Azure VM running the Linux operating system.
hcl
resource "azurerm_linux_virtual_machine" "mtc-vm" {
  name                = "mtc-vm"
  size                = "Standard_F2"
  admin_username      = "adminuser"

  network_interface_ids = [ azurerm_network_interface.mtc-nic.id ]

  os_disk {
    storage_account_type = "Standard_LRS"
  }

  source_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "18.04-LTS"
    version   = "latest"
  }
}
● Custom Data and Provisioners: You can provide a cloud-init script or use provisioners for custom configuration upon VM creation.
## Review and Next Steps
This summary captures the essence of what you've learned about Terraform and Azure Resource Management. Remember to consistently review Terraform's official documentation and practice by applying your knowledge to real-world scenarios to solidify your understanding.