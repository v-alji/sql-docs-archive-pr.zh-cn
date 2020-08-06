---
title: 删除工作负荷组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 801a731db6c5b31bc479d1a3f6079c45ad9a7c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689317"
---
# <a name="delete-a-workload-group"></a><span data-ttu-id="3da34-102">删除工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3da34-102">Delete a Workload Group</span></span>
  <span data-ttu-id="3da34-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 删除工作负荷组或资源池。</span><span class="sxs-lookup"><span data-stu-id="3da34-103">You can delete a workload group or resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="3da34-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="3da34-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="3da34-105">**若要删除工作负荷组，请使用：** [对象资源管理器](#DelWGObjEx)、[Resource Governor 属性](#DelWGRGProp)、[Transact-SQL](#DelWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="3da34-105">**To delete a workload group, using:**  [Object Explorer](#DelWGObjEx), [Resource Governor Properties](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3da34-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="3da34-106">Before You Begin</span></span>  
 <span data-ttu-id="3da34-107">如果工作负荷组中包含活动会话，则不能删除该组。</span><span class="sxs-lookup"><span data-stu-id="3da34-107">You cannot delete a workload group if it contains active sessions.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="3da34-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3da34-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3da34-109">如果工作负荷组包含活动会话，则在调用 ALTER RESOURCE GOVERNOR RECONFIGURE 语句应用更改时，删除工作负荷组或将其移至其他资源池中会失败。</span><span class="sxs-lookup"><span data-stu-id="3da34-109">If a workload group contains active sessions, deleting or moving the workload group to a different resource pool will fail when the ALTER RESOURCE GOVERNOR RECONFIGURE statement is called to apply the change.</span></span> <span data-ttu-id="3da34-110">若要避免此问题，可以执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="3da34-110">To avoid this problem, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="3da34-111">等待受影响组的所有会话均断开连接，然后重新运行 ALTER RESOURCE GOVERNOR RECONFIGURE 语句。</span><span class="sxs-lookup"><span data-stu-id="3da34-111">Wait until all the sessions from the affected group have disconnected, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
-   <span data-ttu-id="3da34-112">使用 KILL 命令显式停止受影响的组中的会话，然后重新运行 ALTER RESOURCE GOVERNOR RECONFIGURE 语句。</span><span class="sxs-lookup"><span data-stu-id="3da34-112">Explicitly stop sessions in the affected group by using the KILL command, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span> <span data-ttu-id="3da34-113">如果决定不打算在使用“删除”之后同时在停止活动会话之前显式停止会话，请使用原始名称重新创建组并将组移至原始资源池。</span><span class="sxs-lookup"><span data-stu-id="3da34-113">If you decide that you do not want to explicitly stop sessions after you use **Delete** but before you stop active sessions, re-create the group by using the original name and move the group to the original resource pool.</span></span>  
  
-   <span data-ttu-id="3da34-114">重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="3da34-114">Restart the server.</span></span> <span data-ttu-id="3da34-115">完成重新启动过程后，将不会创建已删除的组，并且已移动的组将使用新分配的资源池。</span><span class="sxs-lookup"><span data-stu-id="3da34-115">After the restart process is completed, the deleted group will not be created, and a moved group will use the new resource pool assignment.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3da34-116">权限</span><span class="sxs-lookup"><span data-stu-id="3da34-116">Permissions</span></span>  
 <span data-ttu-id="3da34-117">删除工作负荷组需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="3da34-117">Deleting a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-workload-group-using-object-explorer"></a><a name="DelWGObjEx"></a> <span data-ttu-id="3da34-118">使用对象资源管理器删除工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3da34-118">Delete a Workload Group Using Object Explorer</span></span>  
 <span data-ttu-id="3da34-119">**使用对象资源管理器删除工作负荷组**</span><span class="sxs-lookup"><span data-stu-id="3da34-119">**To delete a workload group by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="3da34-120">在[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至其中包含 **“资源池”** 。</span><span class="sxs-lookup"><span data-stu-id="3da34-120">In[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="3da34-121">在包含要删除的工作负荷组的资源池中，依次逐步展开 **“资源池”** 节点直至其中包含 **“工作负荷组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="3da34-121">Recursively expand **Resource Pools** down to and including the **Workload Groups** node in the resource pool that contains the workload group to be deleted.</span></span>  
  
3.  <span data-ttu-id="3da34-122">右键单击工作负荷组，然后单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="3da34-122">Right-click the workload group, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="3da34-123">在 **“删除对象”** 窗口的 **“要删除的对象”** 列表中，将列出工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="3da34-123">In the **Delete Object** window, the workload group is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="3da34-124">若要删除工作负荷组，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3da34-124">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-resource-governor-properties"></a><a name="DelWGRGProp"></a> <span data-ttu-id="3da34-125">使用资源调控器属性删除工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3da34-125">Delete a Workload Group Using Resource Governor Properties</span></span>  
 <span data-ttu-id="3da34-126">**使用“资源调控器属性”页删除工作负荷组**</span><span class="sxs-lookup"><span data-stu-id="3da34-126">**To delete a workload group by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="3da34-127">在对象资源管理器中，依次向下展开 **“管理”** 节点直至其中包括 **“资源池”** 。</span><span class="sxs-lookup"><span data-stu-id="3da34-127">In Object Explorer, recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="3da34-128">右键单击包含要删除的工作负荷组的资源池，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="3da34-128">Right-click the resource pool that contains the workload group to be deleted, and then click **Properties**.</span></span> <span data-ttu-id="3da34-129">这将打开 **“资源调控器属性”** 页。</span><span class="sxs-lookup"><span data-stu-id="3da34-129">This opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="3da34-130">在 **“资源池的工作负荷组”** 窗口中，单击要删除的工作负荷组所在的行，再右键单击该行左侧的向右箭头，然后单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="3da34-130">In the **Workload groups for resource pool** window, click the line for the workload group to be deleted, then right-click the right arrow on the left side of the line, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="3da34-131">若要删除工作负荷组，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3da34-131">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-transact-sql"></a><a name="DelWGTSQL"></a> <span data-ttu-id="3da34-132">使用 Transact-SQL 删除工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3da34-132">Delete a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="3da34-133">**使用 Transact-SQL 删除工作负荷组**</span><span class="sxs-lookup"><span data-stu-id="3da34-133">**To delete a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="3da34-134">运行 `DROP WORKLOAD GROUP` 语句，该语句指定要删除的工作负荷组的名称。</span><span class="sxs-lookup"><span data-stu-id="3da34-134">Run the `DROP WORKLOAD GROUP` statement specifying the name of the workload group to delete.</span></span>  
  
2.  <span data-ttu-id="3da34-135">在发出 `ALTER RESOURCE GOVERNOR RECONFIGURE` 语句之前，请确认要删除的工作负荷组中没有活动请求。</span><span class="sxs-lookup"><span data-stu-id="3da34-135">Before you issue the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement, verify that there are no active requests in the workload group being deleted.</span></span> <span data-ttu-id="3da34-136">如果有活动请求，则 `ALTER RESOURCE GOVERNOR` 将失败。</span><span class="sxs-lookup"><span data-stu-id="3da34-136">If there are active requests, `ALTER RESOURCE GOVERNOR` will fail.</span></span> <span data-ttu-id="3da34-137">若要避免此问题，您可以执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="3da34-137">To avoid this issue, you can take one of the following actions:</span></span>  
  
    -   <span data-ttu-id="3da34-138">等待工作负荷组中的所有会话都断开连接。</span><span class="sxs-lookup"><span data-stu-id="3da34-138">Wait until all the sessions from the workload group have disconnected.</span></span>  
  
    -   <span data-ttu-id="3da34-139">通过使用 `KILL` 命令显式停止工作负荷组中的会话。</span><span class="sxs-lookup"><span data-stu-id="3da34-139">Explicitly stop sessions in the workload group by using the `KILL` command.</span></span>  
  
    -   <span data-ttu-id="3da34-140">重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="3da34-140">Restart the server.</span></span> <span data-ttu-id="3da34-141">工作负荷组将不会重新创建。</span><span class="sxs-lookup"><span data-stu-id="3da34-141">The workload group will not be re-created.</span></span>  
  
    -   <span data-ttu-id="3da34-142">在已发出 `DROP WORKLOAD GROUP` 语句但决定不打算显式停止会话以应用更改的情况下，您可以使用在发出 DROP 语句之前组的名称来重新创建组，然后将该组移动到原始资源池。</span><span class="sxs-lookup"><span data-stu-id="3da34-142">In a scenario in which you have issued the `DROP WORKLOAD GROUP` statement but decide that you do not want to explicitly stop sessions to apply the change, you can re-create the group by using the same name that it had before you issued the DROP statement, and then move the group to the original resource pool.</span></span>  
  
3.  <span data-ttu-id="3da34-143">运行 `ALTER RESOURCE GOVERNOR RECONFIGURE` 语句。</span><span class="sxs-lookup"><span data-stu-id="3da34-143">Run the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="3da34-144">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3da34-144">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="3da34-145">下面的示例删除名为 `groupAdhoc`的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="3da34-145">The following example drops a workload group named `groupAdhoc`.</span></span>  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3da34-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3da34-146">See Also</span></span>  
 <span data-ttu-id="3da34-147">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="3da34-147">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="3da34-148">[创建资源池](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="3da34-148">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="3da34-149">[创建工作负荷组](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="3da34-149">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="3da34-150">[删除资源池](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="3da34-150">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="3da34-151">[DROP WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3da34-151">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="3da34-152">[DROP RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3da34-152">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="3da34-153">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3da34-153">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
