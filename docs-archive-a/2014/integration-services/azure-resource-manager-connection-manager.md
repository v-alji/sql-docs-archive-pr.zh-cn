---
title: Azure 资源管理器连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1dce4def11f14072295dbf3cde9d5ab77304fe74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587575"
---
# <a name="azure-resource-manager-connection-manager"></a><span data-ttu-id="c6b4d-102">Azure 资源管理器连接管理器</span><span class="sxs-lookup"><span data-stu-id="c6b4d-102">Azure Resource Manager Connection Manager</span></span>
<span data-ttu-id="c6b4d-103">借助 Azure 资源管理器连接管理器  ，SSIS 包能够使用[服务主体](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)管理 Azure 资源。</span><span class="sxs-lookup"><span data-stu-id="c6b4d-103">The **Azure Resource Manager Connection Manager** enables an SSIS package to manage Azure resources using a [service principal](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>

<span data-ttu-id="c6b4d-104">若要创建和配置 Azure 资源管理器连接管理器\*\*\*\*，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c6b4d-104">To create and configure an **Azure Resource Manager Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="c6b4d-105">在“添加 SSIS 连接管理器” \*\*\*\* 对话框中，选择“AzureResourceManager”\*\*\*\*，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6b4d-105">In the **Add SSIS Connection Manager** dialog box, select **AzureResourceManager**, and click **Add**.</span></span>
2. <span data-ttu-id="c6b4d-106">在“Azure 资源管理器连接管理器编辑器”\*\*\*\* 对话框中，为服务主体指定“应用程序 ID”\*\*\*\*、“应用程序密钥”\*\*\*\* 和“租户 ID”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6b4d-106">In the **Azure Resource Manager Connection Manager Editor** dialog box, specify the **Application ID**, **Application Key**, and **Tenant ID** for the service principal.</span></span> <span data-ttu-id="c6b4d-107">有关这些属性的详细信息，请参阅[这篇](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)文章。</span><span class="sxs-lookup"><span data-stu-id="c6b4d-107">For details about these properties, please refer to [this](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.</span></span>
3. <span data-ttu-id="c6b4d-108">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="c6b4d-108">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="c6b4d-109">你可以看到你在“属性” \*\*\*\* 窗口中创建的连接管理器的属性。</span><span class="sxs-lookup"><span data-stu-id="c6b4d-109">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
