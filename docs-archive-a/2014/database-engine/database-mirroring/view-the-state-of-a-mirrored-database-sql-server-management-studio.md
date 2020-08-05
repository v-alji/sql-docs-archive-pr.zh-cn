---
title: 查看镜像数据库的状态 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc691e8b746a816ab88448e3399aebad6d8844e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580868"
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a><span data-ttu-id="c0efc-102">查看镜像数据库的状态 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c0efc-102">View the State of a Mirrored Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="c0efc-103">在数据库镜像会话期间，可以在 **“数据库属性”** 对话框的 **“镜像”** 页查看数据库镜像会话的状态。</span><span class="sxs-lookup"><span data-stu-id="c0efc-103">During a database mirroring session, you can view the status on the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a><span data-ttu-id="c0efc-104">查看数据库镜像会话的状态</span><span class="sxs-lookup"><span data-stu-id="c0efc-104">To view the status of a database mirroring session</span></span>  
  
1.  <span data-ttu-id="c0efc-105">连接到主体服务器实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="c0efc-105">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c0efc-106">展开 **“数据库”** ，再选择要镜像的数据库。</span><span class="sxs-lookup"><span data-stu-id="c0efc-106">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="c0efc-107">右键单击数据库，选择 **“任务”** ，再单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="c0efc-107">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="c0efc-108">这样便可打开 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="c0efc-108">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="c0efc-109">镜像开始后， **“状态”** 窗格将显示您选择 **“镜像”** 页或单击 **“刷新”** 按钮时的数据库镜像会话的状态。</span><span class="sxs-lookup"><span data-stu-id="c0efc-109">After mirroring begins, the **Status** panel displays the status of the database mirroring session as of when you selected the **Mirroring** page or clicked the **Refresh** button.</span></span> <span data-ttu-id="c0efc-110">可能的状态如下：</span><span class="sxs-lookup"><span data-stu-id="c0efc-110">The possible states are as follows:</span></span>  
  
    |<span data-ttu-id="c0efc-111">状态</span><span class="sxs-lookup"><span data-stu-id="c0efc-111">States</span></span>|<span data-ttu-id="c0efc-112">说明</span><span class="sxs-lookup"><span data-stu-id="c0efc-112">Explanation</span></span>|  
    |------------|-----------------|  
    |\<blank>|<span data-ttu-id="c0efc-113">不存在数据库镜像会话，并且没有要在 **“镜像”** 页上报告的活动。</span><span class="sxs-lookup"><span data-stu-id="c0efc-113">No database mirroring session exists and there is no activity to report on the **Mirroring** page.</span></span>|  
    |<span data-ttu-id="c0efc-114">已暂停</span><span class="sxs-lookup"><span data-stu-id="c0efc-114">Paused</span></span>|<span data-ttu-id="c0efc-115">主体数据库正在运行，但没有向镜像服务器发送任何日志。</span><span class="sxs-lookup"><span data-stu-id="c0efc-115">The principal database is running but is not sending any logs to the mirror server.</span></span> <span data-ttu-id="c0efc-116">数据库的镜像副本不可用。</span><span class="sxs-lookup"><span data-stu-id="c0efc-116">The mirror copy of the database is not available.</span></span>|  
    |<span data-ttu-id="c0efc-117">无连接</span><span class="sxs-lookup"><span data-stu-id="c0efc-117">No connection</span></span>|<span data-ttu-id="c0efc-118">主体服务器实例无法连接到其伙伴实例或见证服务器实例（如果存在）</span><span class="sxs-lookup"><span data-stu-id="c0efc-118">The principal server instance cannot connect to its partner or to the witness server instance (if any)</span></span>|  
    |<span data-ttu-id="c0efc-119">正在同步</span><span class="sxs-lookup"><span data-stu-id="c0efc-119">Synchronizing</span></span>|<span data-ttu-id="c0efc-120">镜像数据库的内容滞后于主体数据库的内容。</span><span class="sxs-lookup"><span data-stu-id="c0efc-120">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="c0efc-121">主体服务器实例正在向镜像服务器实例发送日志记录，这会对镜像数据库应用更改，使其前滚。</span><span class="sxs-lookup"><span data-stu-id="c0efc-121">The principal server instance is sending log records to the mirror server instance, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="c0efc-122">在数据库镜像会话开始时，镜像数据库和主体数据库处于同步状态。</span><span class="sxs-lookup"><span data-stu-id="c0efc-122">At the start of a database mirroring session, the mirror and principal databases are in the synchronizing state.</span></span>|  
    |<span data-ttu-id="c0efc-123">故障转移</span><span class="sxs-lookup"><span data-stu-id="c0efc-123">Failover</span></span>|<span data-ttu-id="c0efc-124">在主体服务器实例上，手动故障转移（角色切换）已经开始，但镜像服务器实例尚未接受。</span><span class="sxs-lookup"><span data-stu-id="c0efc-124">On the principal server instance, a manual failover (role swap) has begun but has not yet accepted by the mirror.</span></span>|  
    |<span data-ttu-id="c0efc-125">已同步</span><span class="sxs-lookup"><span data-stu-id="c0efc-125">Synchronized</span></span>|<span data-ttu-id="c0efc-126">镜像数据库包含的数据与主体数据库相同。</span><span class="sxs-lookup"><span data-stu-id="c0efc-126">The mirror database contains the same data as the principal database.</span></span> <span data-ttu-id="c0efc-127">只有在同步状态下，才能进行手动和自动故障转移。 </span><span class="sxs-lookup"><span data-stu-id="c0efc-127">Manual and automatic failover are possible *only* in the synchronized state.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0efc-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0efc-128">See Also</span></span>  
 [<span data-ttu-id="c0efc-129">镜像状态 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c0efc-129">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  
