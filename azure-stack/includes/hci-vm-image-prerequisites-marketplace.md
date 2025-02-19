---
author: alkohli
ms.author: alkohli
ms.service: azure-stack
ms.subservice: azure-stack-hci
ms.topic: include
ms.date: 09/26/2022
---


- You have Azure subscription credentials (Microsoft Account or Microsoft Entra user).

- You have access to an Azure Stack HCI cluster. This cluster is deployed, registered, and connected to Azure Arc.

   - Go to the **Overview** page in the Azure Stack HCI cluster resource. On the **Server** tab in the right-pane, the **Azure Arc** should show as **Connected**.
    
    :::image type="content" source="../hci/manage/media/manage-vm-resources/azure-arc-connected.png" alt-text="Screenshot of the Overview page in the Azure Stack HCI cluster resource showing Azure Arc as connected." lightbox="../hci/manage/media/manage-vm-resources/azure-arc-connected.png":::

- To enable Azure Arc VMs on your Azure Stack HCI, see [Deploying Azure Arc resource bridge](/azure-stack/hci/manage/azure-arc-vm-management-overview#azure-arc-resource-bridge-deployment-overview). As a part of Arc Resource Bridge deployment, you also create a custom location for your Azure Stack HCI cluster that you'll use later in the scenario. The custom location also appears in the **Overview** page for the Azure Stack HCI cluster.
