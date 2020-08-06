---
title: 管理 Oracle CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5fbe769980297a06b7958ecad04bfed85b9b714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683006"
---
# <a name="manage-an-oracle-cdc-service"></a><span data-ttu-id="08888-102">Manage an Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="08888-102">Manage an Oracle CDC Service</span></span>
  <span data-ttu-id="08888-103">您可以使用 CDC 服务配置控制台管理特定的 CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="08888-103">You can use the CDC Service Configuration Console to manage a specific CDC Service.</span></span>  
  
 <span data-ttu-id="08888-104">**选择要使用的 CDC 服务**</span><span class="sxs-lookup"><span data-stu-id="08888-104">**To select the CDC service you want to work with**</span></span>  
  
1.  <span data-ttu-id="08888-105">从 CDC 服务配置控制台的左侧窗格中，展开 **“本地 CDC 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="08888-105">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
2.  <span data-ttu-id="08888-106">选择要使用的 CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="08888-106">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="08888-107">也可以右键单击要使用的 CDC 服务，然后选择所需操作。</span><span class="sxs-lookup"><span data-stu-id="08888-107">You can also right-click the CDC service you want to work with and select the desired action.</span></span> <span data-ttu-id="08888-108">请参阅 [你可以做什么与 CDC 服务](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)。</span><span class="sxs-lookup"><span data-stu-id="08888-108">See [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).</span></span>  
  
 <span data-ttu-id="08888-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="08888-109">**OR**</span></span>  
  
1.  <span data-ttu-id="08888-110">从 CDC 服务配置控制台的左侧窗格中选择 **“本地 CDC 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="08888-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console.</span></span>  
  
2.  <span data-ttu-id="08888-111">从 CDC 服务配置控制台的中间部分，选择您要使用的服务。</span><span class="sxs-lookup"><span data-stu-id="08888-111">From the middle section of the CDC Service Configuration Console, select the service you want to work with.</span></span>  
  
     <span data-ttu-id="08888-112">也可以右键单击要使用的 CDC 服务，然后选择所需操作。</span><span class="sxs-lookup"><span data-stu-id="08888-112">You can also right-click the CDC service you want to work with and select the desired action.</span></span> <span data-ttu-id="08888-113">请参阅 [你可以做什么与 CDC 服务](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)。</span><span class="sxs-lookup"><span data-stu-id="08888-113">See [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).</span></span>  
  
##  <a name="what-can-you-do-with-a-cdc-service"></a><a name="BKMK_WhatcandowithCDCService"></a> <span data-ttu-id="08888-114">使用 CDC 服务可以做什么</span><span class="sxs-lookup"><span data-stu-id="08888-114">What can you do with a CDC Service</span></span>  
 <span data-ttu-id="08888-115">您可在使用 CDC 服务时执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="08888-115">You can carry out the following actions when working with a CDC service.</span></span>  
  
### <a name="delete-the-service"></a><span data-ttu-id="08888-116">删除服务</span><span class="sxs-lookup"><span data-stu-id="08888-116">Delete the service</span></span>  
 <span data-ttu-id="08888-117">从 CDC 服务配置控制台右侧的 **“操作”** 窗格，单击 **“删除”** 以便删除服务。</span><span class="sxs-lookup"><span data-stu-id="08888-117">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
 <span data-ttu-id="08888-118">也可以右键单击要删除的 CDC 服务，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="08888-118">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
 <span data-ttu-id="08888-119">**注意**：如果在删除服务时该服务正在运行，则该服务将在被删除前停止。</span><span class="sxs-lookup"><span data-stu-id="08888-119">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
 <span data-ttu-id="08888-120">若要删除 Oracle CDC Windows 服务定义，程序需要对关联的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的 MSXDBCDC 数据库具有更新访问权限。</span><span class="sxs-lookup"><span data-stu-id="08888-120">To delete the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="08888-121">在您单击“确定”删除该服务后，程序将尝试在 MSXDBCDC 数据库中删除 Oracle CDC 服务注册。</span><span class="sxs-lookup"><span data-stu-id="08888-121">When you click OK to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="08888-122">如果程序由于没有正确的权限而无法删除 Oracle CDC 服务注册，则系统将会提示用户输入具有对 MSXDBCDC 数据库的更新权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="08888-122">If the program cannot delete the Oracle CDC Service registration because it does not have the proper permissions, it prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with update permissions to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="08888-123">有关必须在“连接到 SQL Server”对话框中输入的数据的信息，请参阅 [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)。</span><span class="sxs-lookup"><span data-stu-id="08888-123">For information about the data you must enter in the Connect to SQL Server dialog box, see [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
### <a name="edit-the-cdc-service-properties"></a><span data-ttu-id="08888-124">编辑 CDC 服务属性</span><span class="sxs-lookup"><span data-stu-id="08888-124">Edit the CDC Service Properties</span></span>  
 <span data-ttu-id="08888-125">从 CDC 服务配置控制台右侧的 **“操作”** 窗格中，单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="08888-125">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
 <span data-ttu-id="08888-126">也可以右键单击要编辑其属性的 CDC 服务，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="08888-126">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08888-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08888-127">See Also</span></span>  
 [<span data-ttu-id="08888-128">如何管理本地 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="08888-128">How to Manage a Local CDC Service</span></span>](how-to-manage-a-local-cdc-service.md)  
