---
title: Overview of AKS hybrid cluster provisioning from Azure (preview)
description: An overview of AKS hybrid cluster provisioning from Azure.
ms.topic: overview
ms.date: 06/22/2023
author: sethmanheim
ms.author: sethm 
ms.lastreviewed: 10/12/2022
ms.reviewer: abha

# Intent: As an IT Pro, I want to learn how to create and manage AKS hybrid clusters on-premises from Azure
# Keyword: provisioned clusters 
---

# Overview of AKS hybrid cluster provisioning from Azure (preview)

Currently you can manage the lifecycle of AKS hybrid clusters through PowerShell and Windows Admin Center. AKS hybrid cluster provisioning from Azure enables you to use familiar tools like the Azure portal, Azure CLI and Azure Resource Manager templates to create and manage your AKS hybrid clusters running on Azure Stack HCI 22H2 and Windows Server. Azure Arc is automatically enabled on all your AKS hybrid clusters so you can use your Microsoft Entra identity for connecting to your clusters from anywhere. This ensures your developers and application operators can provision and configure Kubernetes clusters in accordance with company policies. We've also simplified the end-to-end security posture for your AKS hybrid clusters through Microsoft Defender for Cloud.  

Microsoft continues to focus on delivering a consistent user experience for all your AKS clusters. If you have created and managed AKS using Azure, you'll feel right at home managing AKS hybrid clusters with familiar Azure portal or Azure CLI management experiences.

You'll also be able to deploy applications at scale using GitOps in both AKS and AKS hybrid clusters. GitOps applies development practices like version control, collaboration, compliance, and continuous integration/continuous deployment (CI/CD) to infrastructure automation.

At this time, you can perform the following operations through the Azure portal, Azure CLI and Resource Manager templates:

- Create/list/show AKS hybrid preview clusters.
- Give users access to Azure Resource Manager resources like AKS hybrid clusters, nodepools and vnet object through Azure RBAC.
- Access the AKS hybrid cluster using kubectl and your Microsoft Entra identity.
- Add/list/show Linux and Windows nodepools on your AKS hybrid cluster.
- Delete your AKS hybrid clusters and nodepools.

With Azure Arc, you can use the following Azure services on your AKS hybrid cluster provisioning from Azure:

- Container Insights
- GitOps v2
- Open Service Mesh
- Azure Key Vault

To create and manage AKS clusters from Azure, you must install the key components described in the following sections.

## Microsoft On-premises Cloud (MOC)

Microsoft On-premises Cloud (MOC) is the management stack that enables the virtual machines on Azure Stack HCI and Windows Server-based SDDC to be managed by Azure. MOC consists of:

- A single instance of a highly available cloud agent service deployed in the cluster. This agent runs on any one node in the Azure Stack HCI or Windows Server cluster and is configured to fail over to another node.
- A node agent running on every Azure Stack HCI physical node.

## Azure Arc Resource Bridge

Azure Arc Resource Bridge connects a private cloud (for example, Azure Stack HCI, VMWare/vSphere, or SCVMM) to Azure and enables on-premises resource management from Azure. Azure Arc Resource Bridge provides the line of sight to private clouds required to manage resources such as Kubernetes clusters on-premises through Azure.

## Arc Kubernetes cluster extensions

A cluster extension is the on-premises equivalent of an Azure Resource Manager resource provider. Just as the **Microsoft.ContainerService** resource provider manages AKS clusters in Azure, the AKS hybrid cluster extension, once added to your Arc Resource Bridge, helps manage AKS hybrid clusters via Azure.

## Custom location

A custom location is the on-premises equivalent of an Azure region and is an extension of the Azure location construct. Custom locations provide a way for tenant administrators to use their data center with the right extensions installed, as target locations for deploying Azure service instances.

## Key personas and roles

### Infrastructure administrator role

The role of the infrastructure administrator is to set up the platform components: for example, setting up Azure Stack HCI or Windows Server, the AKS host management cluster, Arc Resource Bridge, the AKS hybrid cluster extension, and the custom Location. The admin role then creates on-premises networks that the Kubernetes operator uses to create AKS hybrid clusters.

### Kubernetes operator role

Kubernetes operators create and run applications on their on-premises AKS hybrid clusters. The operator is given scoped Azure RBAC access to the Azure subscription, Azure custom location, and AKS hybrid network by the infrastructure administrator. No access to the underlying on-premises infrastructure is necessary.

Once the operator has the required access, they are free to create AKS hybrid cluster according to application needs - Windows/Linux node pools, Kubernetes versions, etc. The operator can also assign AKS cluster administrator permissions to other Microsoft Entra users in their organization, to access the provisioned AKS hybrid clusters. Operators and Kubernetes cluster administrators can then run their containerized applications via the Azure Arc Flux v2 extension.

## Next steps

- [Quickly test AKS hybrid cluster provisioning from Azure on an Azure ](aks-hybrid-preview-azure-vm.md)
- [Review preview requirements if you have an Azure Stack HCI or Windows Server cluster](aks-hybrid-preview-requirements.md)
