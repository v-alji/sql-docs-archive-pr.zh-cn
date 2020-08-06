---
title: 移动工作负荷组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f73b48f0ec2255760b4ee55acfaf91dc02af7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689308"
---
# <a name="move-a-workload-group"></a><span data-ttu-id="2fff5-102">移动工作负荷组</span><span class="sxs-lookup"><span data-stu-id="2fff5-102">Move a Workload Group</span></span>
  <span data-ttu-id="2fff5-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 将资源调控器工作负荷组移动到其他资源池。</span><span class="sxs-lookup"><span data-stu-id="2fff5-103">You can move a Resource Governor workload group to a different resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="2fff5-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="2fff5-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="2fff5-105">若要移动工作负荷组，请使用：[SQL Server Management Studio](#MoveWGSSMS)、[Transact-SQL](#MoveWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="2fff5-105">**To move a workload group, using:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2fff5-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="2fff5-106">Before You Begin</span></span>  
 <span data-ttu-id="2fff5-107">如果存在挂起的资源调控器配置操作，则无法移动工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="2fff5-107">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="2fff5-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2fff5-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2fff5-109">如果存在挂起的资源调控器配置操作，则无法移动工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="2fff5-109">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span> <span data-ttu-id="2fff5-110">你可以通过查询 [sys.dm_resource_governor_configuration (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 动态管理视图来获取 is_configuration_pending 的当前状态以确定是否存在配置挂起。</span><span class="sxs-lookup"><span data-stu-id="2fff5-110">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2fff5-111">权限</span><span class="sxs-lookup"><span data-stu-id="2fff5-111">Permissions</span></span>  
 <span data-ttu-id="2fff5-112">移动工作负荷组需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="2fff5-112">Moving a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="move-a-workload-group-using-sql-server-management-studio"></a><a name="MoveWGSSMS"></a> <span data-ttu-id="2fff5-113">使用 SQL Server Management Studio 移动工作负荷组</span><span class="sxs-lookup"><span data-stu-id="2fff5-113">Move a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2fff5-114">**使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="2fff5-114">**To move a workload group by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span></span>  
  
1.  <span data-ttu-id="2fff5-115">在对象资源管理器中，依次逐步展开 **“管理”** 节点直至 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="2fff5-115">In Object Explorer, recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="2fff5-116">右键单击“资源调控器”  ，然后单击“属性” ，这将打开“资源调控器属性”页  。</span><span class="sxs-lookup"><span data-stu-id="2fff5-116">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="2fff5-117">在 **“资源池”** 窗口中，单击包含要移动的工作负荷组的资源池。</span><span class="sxs-lookup"><span data-stu-id="2fff5-117">In the **Resource Pools** window, click the resource pool containing the workload group to be moved.</span></span> <span data-ttu-id="2fff5-118">此时， **“工作负荷组”** 窗口会列出该资源池中的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="2fff5-118">The **Workload Groups** window now lists the workload groups in that resource pool.</span></span>  
  
4.  <span data-ttu-id="2fff5-119">在“工作负荷组”窗口中，右键单击要移动的工作负荷组左侧的向右箭头，然后单击“移到”。</span><span class="sxs-lookup"><span data-stu-id="2fff5-119">In the **Workload Groups** window, right-click the right arrow to the left of the workload group to be moved, and click **Move to**.</span></span> <span data-ttu-id="2fff5-120">这将显示 **“移动工作负荷组”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="2fff5-120">This displays a **Move Workload Group** window.</span></span>  
  
5.  <span data-ttu-id="2fff5-121">在窗口中显示可用的资源池。</span><span class="sxs-lookup"><span data-stu-id="2fff5-121">Available resource pools are displayed in the window.</span></span> <span data-ttu-id="2fff5-122">单击要将工作负荷组移动到的资源池的名称，然后单击 **“确定”** 执行此操作。</span><span class="sxs-lookup"><span data-stu-id="2fff5-122">Click the name of the resource pool that you want to move the workload group to, and then click **OK** to carry out this action.</span></span>  
  
6.  <span data-ttu-id="2fff5-123">只有在您单击 **“确定”** 之后，此操作才能完成。</span><span class="sxs-lookup"><span data-stu-id="2fff5-123">This action is not completed until after you click **OK**.</span></span> <span data-ttu-id="2fff5-124">单击 **“确定”** 后，将执行 ALTER RESOURCE GOVERNOR RECONFIGURE 语句。</span><span class="sxs-lookup"><span data-stu-id="2fff5-124">When you click **OK**, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
7.  <span data-ttu-id="2fff5-125">如果创建或重新配置资源池或工作负荷组的操作失败，错误消息摘要将显示在属性页标题下方。</span><span class="sxs-lookup"><span data-stu-id="2fff5-125">If the create or reconfigure operation fails for the resource pool or workload group, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="2fff5-126">若要查看详细的错误消息，请单击错误信息上的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="2fff5-126">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
##  <a name="move-a-workload-group-using-transact-sql"></a><a name="MoveWGTSQL"></a> <span data-ttu-id="2fff5-127">使用 Transact-SQL 移动工作负荷组</span><span class="sxs-lookup"><span data-stu-id="2fff5-127">Move a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="2fff5-128">**使用 Transact-SQL 移动工作负荷组**</span><span class="sxs-lookup"><span data-stu-id="2fff5-128">**To move a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="2fff5-129">运行 `ALTER WORKLOAD GROUP` 语句，该语句指定要移动的工作负荷组的名称以及该组应移到的资源池。</span><span class="sxs-lookup"><span data-stu-id="2fff5-129">Run the `ALTER WORKLOAD GROUP` statement specifying the name of the workload group to be moved and the resource pool to which it should be moved.</span></span>  
  
2.  <span data-ttu-id="2fff5-130">运行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 语句。</span><span class="sxs-lookup"><span data-stu-id="2fff5-130">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="2fff5-131">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2fff5-131">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="2fff5-132">以下示例将一个名为 `groupAdhoc` 的工作负荷组移动到默认资源池。</span><span class="sxs-lookup"><span data-stu-id="2fff5-132">The following example moves a workload group named `groupAdhoc` to the default resource pool.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fff5-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fff5-133">See Also</span></span>  
 <span data-ttu-id="2fff5-134">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="2fff5-134">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="2fff5-135">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="2fff5-135">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="2fff5-136">[创建资源池](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="2fff5-136">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="2fff5-137">[创建工作负荷组](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="2fff5-137">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="2fff5-138">[ALTER WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2fff5-138">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="2fff5-139">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2fff5-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
