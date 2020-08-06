---
title: 删除资源池 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a67b0e2262fa3007597091b6087cc937bb0f3276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689313"
---
# <a name="delete-a-resource-pool"></a><span data-ttu-id="427e9-102">删除资源池</span><span class="sxs-lookup"><span data-stu-id="427e9-102">Delete a Resource Pool</span></span>
  <span data-ttu-id="427e9-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 删除资源池。</span><span class="sxs-lookup"><span data-stu-id="427e9-103">You can delete a resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="427e9-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="427e9-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="427e9-105">**若要删除资源池，请使用：** [SQL Server Management Studio](#DelRPSSMS)、[Transact-SQL](#DelRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="427e9-105">**To delete a resource pool, using:** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="427e9-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="427e9-106">Before You Begin</span></span>  
 <span data-ttu-id="427e9-107">如果资源池中包含工作负荷组，则不能删除该池。</span><span class="sxs-lookup"><span data-stu-id="427e9-107">You cannot delete a resource pool if it contains workload groups.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="427e9-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="427e9-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="427e9-109">不能删除资源调控器默认资源池或内部资源池。</span><span class="sxs-lookup"><span data-stu-id="427e9-109">You cannot delete the Resource Governor default or internal resource pools.</span></span> <span data-ttu-id="427e9-110">如果资源池中包含工作负荷组，则不能删除该池。</span><span class="sxs-lookup"><span data-stu-id="427e9-110">You cannot delete a resource pool if it contains workload groups.</span></span> <span data-ttu-id="427e9-111">有关详细信息，请参阅 [Delete a Workload Group](delete-a-workload-group.md)。</span><span class="sxs-lookup"><span data-stu-id="427e9-111">For more information, see [Delete a Workload Group](delete-a-workload-group.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="427e9-112">权限</span><span class="sxs-lookup"><span data-stu-id="427e9-112">Permissions</span></span>  
 <span data-ttu-id="427e9-113">删除资源池需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="427e9-113">Deleting a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-resource-pool-using-object-explorer"></a><a name="DelRPSSMS"></a> <span data-ttu-id="427e9-114">使用对象资源管理器删除资源池</span><span class="sxs-lookup"><span data-stu-id="427e9-114">Delete a Resource Pool Using Object Explorer</span></span>  
 <span data-ttu-id="427e9-115">**使用 SQL Server Management Studio 删除资源池**</span><span class="sxs-lookup"><span data-stu-id="427e9-115">**To delete a resource pool by using SQL Server Management Studio**</span></span>  
  
1.  <span data-ttu-id="427e9-116">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至其中并包含 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="427e9-116">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="427e9-117">右键单击要删除的资源池，然后单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="427e9-117">Right-click the resource pool to be deleted, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="427e9-118">在 **“删除对象”** 窗口的 **“要删除的对象”** 列表中，将列出资源池。</span><span class="sxs-lookup"><span data-stu-id="427e9-118">In the **Delete Object** window, the resource pool is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="427e9-119">若要删除资源池，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="427e9-119">To delete the resource pool, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="427e9-120">如果尝试删除的资源池中包含工作负荷组，则此操作将失败。</span><span class="sxs-lookup"><span data-stu-id="427e9-120">If the resource pool that you are trying to delete contains a workload group, this action will fail.</span></span>  
  
##  <a name="delete-a-resource-pool-using-transact-sql"></a><a name="DelRPTSQL"></a> <span data-ttu-id="427e9-121">使用 Transact-SQL 删除资源池</span><span class="sxs-lookup"><span data-stu-id="427e9-121">Delete a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="427e9-122">**使用 Transact-SQL 删除资源池**</span><span class="sxs-lookup"><span data-stu-id="427e9-122">**To delete a resource pool by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="427e9-123">运行 `DROP RESOURCE POOL` 语句，该语句指定要删除的资源池的名称。</span><span class="sxs-lookup"><span data-stu-id="427e9-123">Run the `DROP RESOURCE POOL` statement specifying the name of the resource pool to delete.</span></span>  
  
2.  <span data-ttu-id="427e9-124">运行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 语句。</span><span class="sxs-lookup"><span data-stu-id="427e9-124">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="427e9-125">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="427e9-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="427e9-126">下面的示例删除名为 `poolAdhoc`的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="427e9-126">The following example drops a workload group named `poolAdhoc`.</span></span>  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="427e9-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="427e9-127">See Also</span></span>  
 <span data-ttu-id="427e9-128">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="427e9-128">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="427e9-129">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="427e9-129">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="427e9-130">[创建资源池](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="427e9-130">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="427e9-131">[更改资源池设置](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="427e9-131">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="427e9-132">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="427e9-132">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="427e9-133">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="427e9-133">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="427e9-134">[DROP WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="427e9-134">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="427e9-135">[DROP RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="427e9-135">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="427e9-136">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="427e9-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
