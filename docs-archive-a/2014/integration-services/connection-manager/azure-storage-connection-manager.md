---
title: Azure 存储连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47580d8d1d961df9fbcbed0bd7164f1c54792b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586927"
---
# <a name="azure-storage-connection-manager"></a><span data-ttu-id="b53da-102">Azure 存储连接管理器</span><span class="sxs-lookup"><span data-stu-id="b53da-102">Azure Storage Connection Manager</span></span>
  <span data-ttu-id="b53da-103">Azure 存储连接管理器使一个 SSIS 包可使用你指定的属性值连接到 Azure 存储帐户：存储帐户名称和帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="b53da-103">The Azure Storage connection manager enables an SSIS package to connect to an Azure Storage account by using the values you specify for the properties: Storage Account Name and Account Key.</span></span>  
  
1.  <span data-ttu-id="b53da-104">在“添加 SSIS 连接管理器” \*\*\*\* 对话框中，选择“AzureStorage” \*\*\*\*，然后单击“添加” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b53da-104">In the **Add SSIS Connection Manager** dialog box, select **AzureStorage**, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="b53da-105">在“Azure 存储连接管理器编辑器”对话框中，选择“使用 Azure 帐户” \*\*\*\* 以通过 Internet 连接到 Azure 存储服务，或选择“使用本地开发人员帐户” \*\*\*\* 以连接到 Azure 存储模拟器承载的本地服务。</span><span class="sxs-lookup"><span data-stu-id="b53da-105">In the Azure Storage Connection Manager Editor dialog box, choose **Use Azure account** to connect to an Azure Storage Service via internet or choose **Use local developer account** to connect to the local service hosted by the Azure Storage Emulator.</span></span>  
  
3.  <span data-ttu-id="b53da-106">如果选择了“使用 Azure 帐户” \*\*\*\* 选项，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b53da-106">If you selected **Use Azure account** option, do the following:</span></span>  
  
    1.  <span data-ttu-id="b53da-107">为“存储帐户名称” \*\*\*\* 和“帐户密钥” \*\*\*\* 字段指定值。</span><span class="sxs-lookup"><span data-stu-id="b53da-107">Specify values for the **Storage account name** and **Account key** field.</span></span> <span data-ttu-id="b53da-108">这些值将存储为 SSIS 包中的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="b53da-108">These values will be stored as sensitive data in SSIS package.</span></span>  
  
    2.  <span data-ttu-id="b53da-109">如果你想要使用 HTTPS 而不是 HTTP 来连接到 Azure 存储服务，请选择“使用 HTTPS” \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="b53da-109">Select **Use HTTPS** if you want to use HTTPS instead of HTTP to connect to the Azure Storage Service.</span></span>  
  
4.  <span data-ttu-id="b53da-110">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="b53da-110">Click **OK** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="b53da-111">你可以看到你在“属性” \*\*\*\* 窗口中创建的连接管理器的属性。</span><span class="sxs-lookup"><span data-stu-id="b53da-111">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
