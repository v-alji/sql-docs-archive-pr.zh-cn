---
title: 管理 CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manSer
ms.assetid: 645ae53f-f352-4d6a-9eb0-264e53a93a18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d630392216e51efd9ea64116d57b388202061ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683008"
---
# <a name="manage-a-cdc-service"></a><span data-ttu-id="a788b-102">管理 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="a788b-102">Manage a CDC Service</span></span>
  <span data-ttu-id="a788b-103">您可以使用 CDC 设计器控制台查看通过 CDC 服务配置控制台创建的服务并且管理 Oracle CDC 服务中的所有实例。</span><span class="sxs-lookup"><span data-stu-id="a788b-103">You can use the CDC Designer Console to view the services you created with the CDC Service Configuration Console and manage all of the instances in the Oracle CDC Service.</span></span>  
  
 <span data-ttu-id="a788b-104">在左侧窗格中单击服务的名称可显示与该服务有关的信息并且对其进行管理。</span><span class="sxs-lookup"><span data-stu-id="a788b-104">Click the name of the service in the left pane to display information about the service and to manage it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a788b-105">您必须首先使用 CDC 服务配置控制台创建一个服务以便向该列表中添加服务。</span><span class="sxs-lookup"><span data-stu-id="a788b-105">You must first create a service using the CDC Service Configuration Console to add services to this list.</span></span> <span data-ttu-id="a788b-106">有关如何创建服务的信息，请参阅随 CDC 服务配置控制台一起提供的联机帮助。</span><span class="sxs-lookup"><span data-stu-id="a788b-106">For information on how to create a service, see the online help provided with the CDC Service Configuration Console.</span></span>  
  
## <a name="what-you-can-do-when-you-display-the-cdc-service-information"></a><span data-ttu-id="a788b-107">在显示 CDC 服务信息时您可以执行的操作</span><span class="sxs-lookup"><span data-stu-id="a788b-107">What you can do when you display the CDC service information</span></span>  
 <span data-ttu-id="a788b-108">在显示与服务有关的信息时您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a788b-108">You can do the following when you display information about a service:</span></span>  
  
 <span data-ttu-id="a788b-109">**为所选服务创建一个新的 CDC 实例**</span><span class="sxs-lookup"><span data-stu-id="a788b-109">**Create a new CDC instance for the selected service**</span></span>  
  
 <span data-ttu-id="a788b-110">单击 **“新建 Oracle CDC 实例”** ，在右侧窗格中为该服务创建一个新的实例。</span><span class="sxs-lookup"><span data-stu-id="a788b-110">Click **New Oracle CDC Instance** in the right pane to create a new instance for that service.</span></span> <span data-ttu-id="a788b-111">新建实例向导将打开以便创建该实例。</span><span class="sxs-lookup"><span data-stu-id="a788b-111">The New Instance wizard opens to create the instance.</span></span> <span data-ttu-id="a788b-112">有关新建实例向导的详细信息，请参阅 [Use the New Instance Wizard](use-the-new-instance-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a788b-112">For more information about the New Instance wizard, see [Use the New Instance Wizard](use-the-new-instance-wizard.md).</span></span>  
  
 <span data-ttu-id="a788b-113">**启动服务中的所有 CDC 实例**</span><span class="sxs-lookup"><span data-stu-id="a788b-113">**Start all CDC instances in the service**</span></span>  
  
 <span data-ttu-id="a788b-114">在右侧窗格中单击 **“启动所有实例”** 可开始从服务中定义的所有实例捕获数据。</span><span class="sxs-lookup"><span data-stu-id="a788b-114">Click **Start All Instances** in the right pane to begin capturing data from all the defined instances in the service.</span></span>  
  
 <span data-ttu-id="a788b-115">**停止服务中的所有 CDC 实例**</span><span class="sxs-lookup"><span data-stu-id="a788b-115">**Stop all CDC instances in the service**</span></span>  
  
 <span data-ttu-id="a788b-116">单击 **“停止所有实例”** 可停止服务中所有实例的变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="a788b-116">Click **Stop All Instances** to stop the change data capture for all instances in the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a788b-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a788b-117">See Also</span></span>  
 <span data-ttu-id="a788b-118">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="a788b-118">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="a788b-119">[如何从 CDC 设计器控制台管理 CDC 服务](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="a788b-119">[How to Manage a CDC Service from the CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="a788b-120">使用新建实例向导</span><span class="sxs-lookup"><span data-stu-id="a788b-120">Use the New Instance Wizard</span></span>](use-the-new-instance-wizard.md)  
  
  
