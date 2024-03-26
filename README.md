# Terraform Azure Development Environment Project

## Overview
This repository contains Terraform configuration files used to build a development environment in Azure. The infrastructure includes a resource group, virtual network, and a Linux virtual machine among other components. T

## Infrastructure Components
- Resource Group: A container that holds related resources for an Azure solution.
- Virtual Network: Provides network functionality to the resources connected to it.
- Subnet: Divides a virtual network into smaller segments.
- Network Security Group: Contains security rules to filter network traffic.
- Virtual Machine: An Azure Linux VM configured for development purposes.

## How to Use
To deploy this environment, ensure you have Terraform installed and configured with AzureRM provider. Run the following commands:
- terraform init: Initialize a Terraform working directory.
- terraform plan: Generate and show an execution plan.
- terraform apply: Execute the actions proposed in a Terraform plan.

Make sure to review the plan before applying to avoid unexpected changes.

## Project Structure
- main.tf: Contains the main set of configuration files where all the Azure resources are defined.
- variables.tf: Defines variables used within the main.tf.
- outputs.tf: Specifies the output configuration for resource attributes.

## Key Learning Topics
The configuration covers:
- Initializing providers and resources with Terraform.
- Associating subnets with network security groups.
- Provisioning and managing a Linux VM with SSH access in Azure.
- Utilizing Terraform state files to track the state of the infrastructure.
- Implementing Terraform outputs for resource attribute visibility.
- Defining and using variables to parameterize Terraform configurations.

## Contact
For any suggestions or contributions to the project, please reach out on GitHub or through the provided LinkedIn and Twitter links.
