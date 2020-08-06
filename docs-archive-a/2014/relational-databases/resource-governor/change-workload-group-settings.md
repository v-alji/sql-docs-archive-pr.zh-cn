---
title: 更改工作负荷组设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 579aad71d32a629d75f1eecd76e7dacfe32d94f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576621"
---
# <a name="change-workload-group-settings"></a><span data-ttu-id="f7a10-102">更改工作负荷组设置</span><span class="sxs-lookup"><span data-stu-id="f7a10-102">Change Workload Group Settings</span></span>
  <span data-ttu-id="f7a10-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]更改工作负荷组设置。</span><span class="sxs-lookup"><span data-stu-id="f7a10-103">You can change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="f7a10-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="f7a10-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="f7a10-105">**若要更改工作负荷组的设置，请使用：** [SQL Server Management Studio](#ChgWGProp)、[Transact-SQL](#ChgWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="f7a10-105">**To change the settings for a workload group, using:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="f7a10-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="f7a10-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="f7a10-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f7a10-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f7a10-108">您可以更改默认工作负荷组和用户定义的工作负载组的设置。</span><span class="sxs-lookup"><span data-stu-id="f7a10-108">You can change the settings of the default workload group and user-defined workload groups.</span></span>  
  
 <span data-ttu-id="f7a10-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="f7a10-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="f7a10-110">对非对齐的分区表创建索引所占用的内存与涉及的分区数成正比。</span><span class="sxs-lookup"><span data-stu-id="f7a10-110">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="f7a10-111">如果所需的内存总量超过工作负荷组设置为每个查询设定的限制 (REQUEST_MAX_MEMORY_GRANT_PERCENT)，则这种索引创建可能会失败。</span><span class="sxs-lookup"><span data-stu-id="f7a10-111">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="f7a10-112">由于默认工作负荷组允许查询超过每个查询的限制，并在开始时使用所需的最低内存以便与 SQL Server 2005 保持兼容，因此，如果默认资源池配置了足够多的内存总量以运行此类查询，则用户或许能够在默认工作负荷组中运行相同的索引创建。</span><span class="sxs-lookup"><span data-stu-id="f7a10-112">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="f7a10-113">允许索引创建操作使用比最初授予的工作区内存多的工作区内存，以便提高性能。</span><span class="sxs-lookup"><span data-stu-id="f7a10-113">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="f7a10-114">这个特别处理由资源调控器支持，然而，最初授予及任何其他内存授予都受工作负荷组和资源池设置的限制。</span><span class="sxs-lookup"><span data-stu-id="f7a10-114">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f7a10-115">权限</span><span class="sxs-lookup"><span data-stu-id="f7a10-115">Permissions</span></span>  
 <span data-ttu-id="f7a10-116">更改工作负荷组设置需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="f7a10-116">Changing workload group settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-workload-group-settings-using-sql-server-management-studio"></a><a name="ChgWGProp"></a> <span data-ttu-id="f7a10-117">使用 SQL Server Management Studio 更改工作负荷组设置</span><span class="sxs-lookup"><span data-stu-id="f7a10-117">Change Workload Group Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f7a10-118">**使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="f7a10-118">**To change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="f7a10-119">在对象资源管理器中，依次逐步展开 **“管理”** 节点直至其中包含要修改的工作负荷组的 **“工作负荷组”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f7a10-119">In Object Explorer, recursively expand the **Management** node down to and including the **Workload Groups** folder that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="f7a10-120">右键单击要修改的工作负荷组，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="f7a10-120">Right-click the workload group to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="f7a10-121">在 **“资源调控器属性”** 页中，如果工作负荷组所在的行未自动选中，则在 **“资源池的工作负荷组”** 网格内将其选中。</span><span class="sxs-lookup"><span data-stu-id="f7a10-121">In the **Resource Governor Properties** page, select the row for the workload group in the **Workload groups for resource pool** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="f7a10-122">在行中单击或双击要更改的单元，然后输入新值。</span><span class="sxs-lookup"><span data-stu-id="f7a10-122">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="f7a10-123">若要保存更改，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="f7a10-123">To save the changes, click **OK**</span></span>  
  
##  <a name="change-workload-group-settings-using-transact-sql"></a><a name="ChgWGTSQL"></a> <span data-ttu-id="f7a10-124">使用 Transact-SQL 更改工作负荷组设置</span><span class="sxs-lookup"><span data-stu-id="f7a10-124">Change Workload Group Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="f7a10-125">**使用 Transact-SQL 更改工作负荷组设置**</span><span class="sxs-lookup"><span data-stu-id="f7a10-125">**To change workload group settings by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="f7a10-126">运行 ALTER WORKLOAD GROUP 语句，指定要更改的属性值。</span><span class="sxs-lookup"><span data-stu-id="f7a10-126">Run the ALTER WORKLOAD GROUP statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="f7a10-127">运行 ALTER RESOURCE GOVERNOR RECONFIGURE 语句。</span><span class="sxs-lookup"><span data-stu-id="f7a10-127">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="f7a10-128">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f7a10-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f7a10-129">以下示例更改名为 `groupAdhoc`的工作负荷组的最大内存授予百分比设置。</span><span class="sxs-lookup"><span data-stu-id="f7a10-129">The following example changes the max memory grant percent setting for the workload group named `groupAdhoc`.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7a10-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7a10-130">See Also</span></span>  
 <span data-ttu-id="f7a10-131">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="f7a10-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="f7a10-132">[创建工作负荷组](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="f7a10-132">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="f7a10-133">[创建资源池](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="f7a10-133">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="f7a10-134">[更改资源池设置](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="f7a10-134">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="f7a10-135">[ALTER WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f7a10-135">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="f7a10-136">[ALTER RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f7a10-136">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="f7a10-137">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f7a10-137">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
