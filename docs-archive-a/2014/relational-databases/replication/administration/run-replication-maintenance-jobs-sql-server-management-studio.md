---
title: 运行复制维护作业 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691698"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a><span data-ttu-id="0031f-102">执行复制维护作业 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0031f-102">Run Replication Maintenance Jobs (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0031f-103">复制使用下列维护作业：</span><span class="sxs-lookup"><span data-stu-id="0031f-103">Replication uses the following maintenance jobs:</span></span>  
  
-   <span data-ttu-id="0031f-104">**重新初始化数据验证失败的订阅**</span><span class="sxs-lookup"><span data-stu-id="0031f-104">**Reinitialize subscriptions having data validation failures**</span></span>
-   <span data-ttu-id="0031f-105">**代理历史记录清除：分发**</span><span class="sxs-lookup"><span data-stu-id="0031f-105">**Agent history clean up: distribution**</span></span>
-   <span data-ttu-id="0031f-106">**分发的复制监视刷新器。**</span><span class="sxs-lookup"><span data-stu-id="0031f-106">**Replication monitoring refresher for distribution.**</span></span>
-   <span data-ttu-id="0031f-107">**复制代理检查**</span><span class="sxs-lookup"><span data-stu-id="0031f-107">**Replication agents checkup**</span></span>
-   <span data-ttu-id="0031f-108">**分发清除：分发**</span><span class="sxs-lookup"><span data-stu-id="0031f-108">**Distribution clean up: distribution**</span></span>
-   <span data-ttu-id="0031f-109">**过期订阅清除**</span><span class="sxs-lookup"><span data-stu-id="0031f-109">**Expired subscription clean up**</span></span>  
  
 <span data-ttu-id="0031f-110">从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的“作业”文件夹和复制监视器的“代理”选项卡启动和停止这些作业 。</span><span class="sxs-lookup"><span data-stu-id="0031f-110">Start and stop these jobs from the **Jobs** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="0031f-111">有关启动复制监视器的信息，请参阅[启动复制监视器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="0031f-111">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="0031f-112">在“作业属性 - \<Job>”对话框中查看和修改每个作业的属性，可从同一文件夹和选项卡中访问此对话框。</span><span class="sxs-lookup"><span data-stu-id="0031f-112">View and modify properties for each job in the **Job Properties - \<Job>** dialog box, which is available from the same folder and tab.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="0031f-113">在 Management Studio 中启动或停止复制维护作业</span><span class="sxs-lookup"><span data-stu-id="0031f-113">To start or stop a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="0031f-114">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="0031f-114">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0031f-115">展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0031f-115">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="0031f-116">右键单击一个作业，然后单击 **“启动作业”** 或 **“停止作业”** 。</span><span class="sxs-lookup"><span data-stu-id="0031f-116">Right-click a job, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="0031f-117">在复制监视器中启动或停止复制维护作业</span><span class="sxs-lookup"><span data-stu-id="0031f-117">To start or stop a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0031f-118">在复制监视器中，展开发布服务器组，然后选择一个发布服务器。</span><span class="sxs-lookup"><span data-stu-id="0031f-118">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="0031f-119">单击 **“代理”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0031f-119">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="0031f-120">在网格中右键单击一个作业，然后单击 **“启动作业”** 或 **“停止作业”** 。</span><span class="sxs-lookup"><span data-stu-id="0031f-120">Right-click a job in the grid, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="0031f-121">在 Management Studio 中查看和修改复制维护作业的属性</span><span class="sxs-lookup"><span data-stu-id="0031f-121">To view and modify properties for a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="0031f-122">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="0031f-122">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0031f-123">展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0031f-123">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="0031f-124">右键单击一个作业，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="0031f-124">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0031f-125">在“作业属性 - \<Job>”对话框中，根据需要修改任意属性，然后单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="0031f-125">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="0031f-126">在复制监视器中查看和修改复制维护作业的属性</span><span class="sxs-lookup"><span data-stu-id="0031f-126">To view and modify properties for a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0031f-127">在复制监视器中，展开发布服务器组，然后选择一个发布服务器。</span><span class="sxs-lookup"><span data-stu-id="0031f-127">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="0031f-128">单击 **“代理”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0031f-128">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="0031f-129">在网格中右键单击一个作业，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="0031f-129">Right-click a job in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0031f-130">在“作业属性 - \<Job>”对话框中，根据需要修改任意属性，然后单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="0031f-130">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0031f-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0031f-131">See Also</span></span>  
 <span data-ttu-id="0031f-132">[启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="0031f-132">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="0031f-133">[使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0031f-133">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="0031f-134">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="0031f-134">Replication Agent Administration</span></span>](../agents/replication-agent-administration.md)  
  
  
