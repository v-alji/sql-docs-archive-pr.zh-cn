---
title: 创建工作负荷组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 144bcef57b3d6e191b03b1539e9e7382a9085c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580666"
---
# <a name="create-a-workload-group"></a><span data-ttu-id="3f087-102">创建工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3f087-102">Create a Workload Group</span></span>
  <span data-ttu-id="3f087-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]创建工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="3f087-103">You can create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="3f087-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="3f087-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="3f087-105">若要创建工作负荷组，请使用：[SQL Server Management Studio](#CreWGProp)、[Transact-SQL](#CreWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="3f087-105">**To create a workload group, using:**  [SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3f087-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="3f087-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="3f087-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3f087-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3f087-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="3f087-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="3f087-109">对非对齐的分区表创建索引所占用的内存与涉及的分区数成正比。</span><span class="sxs-lookup"><span data-stu-id="3f087-109">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="3f087-110">如果所需的内存总量超过工作负荷组设置为每个查询设定的限制 (REQUEST_MAX_MEMORY_GRANT_PERCENT)，则这种索引创建可能会失败。</span><span class="sxs-lookup"><span data-stu-id="3f087-110">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="3f087-111">由于默认工作负荷组允许查询超过每个查询的限制，并在开始时使用所需的最低内存以便与 SQL Server 2005 保持兼容，因此，如果默认资源池配置了足够多的内存总量以运行此类查询，则用户或许能够在默认工作负荷组中运行相同的索引创建。</span><span class="sxs-lookup"><span data-stu-id="3f087-111">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="3f087-112">允许索引创建操作使用比最初授予的工作区内存多的工作区内存，以便提高性能。</span><span class="sxs-lookup"><span data-stu-id="3f087-112">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="3f087-113">这个特别处理由资源调控器支持，然而，最初授予及任何其他内存授予都受工作负荷组和资源池设置的限制。</span><span class="sxs-lookup"><span data-stu-id="3f087-113">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3f087-114">权限</span><span class="sxs-lookup"><span data-stu-id="3f087-114">Permissions</span></span>  
 <span data-ttu-id="3f087-115">创建工作负荷组需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="3f087-115">Creating a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreWGProp"></a> <span data-ttu-id="3f087-116">使用 SQL Server Management Studio 创建工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3f087-116">Create a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3f087-117">**使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="3f087-117">**To create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="3f087-118">在对象资源管理器中，依次逐步展开 **“管理”** 节点直至其中包含要修改的工作负荷组的资源池。</span><span class="sxs-lookup"><span data-stu-id="3f087-118">In Object Explorer, recursively expand the **Management** node down to and including the resource pool that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="3f087-119">右键单击“工作负荷组”文件夹，然后单击“新建工作负荷组”。</span><span class="sxs-lookup"><span data-stu-id="3f087-119">Right-click the **Workload Groups** folder, and then click **New Workload Group**.</span></span>  
  
3.  <span data-ttu-id="3f087-120">在 **“资源池”** 网格中，确保突出显示要添加工作负荷组的资源池。</span><span class="sxs-lookup"><span data-stu-id="3f087-120">In the **Resource pools** grid, ensure the resource pool where you want to add the workload group is highlighted.</span></span>  
  
4.  <span data-ttu-id="3f087-121">**“资源池的工作负荷组”** 网格将具有一个新行，其中包含一个空名称和其他列中的默认值。</span><span class="sxs-lookup"><span data-stu-id="3f087-121">The **Workload groups for resource pool** grid will have a new line with a blank name and default values in the other columns.</span></span>  
  
5.  <span data-ttu-id="3f087-122">单击 **“名称”** 单元，然后输入工作负荷组的名称。</span><span class="sxs-lookup"><span data-stu-id="3f087-122">Click the **Name** cell and enter a name for the workload group.</span></span>  
  
6.  <span data-ttu-id="3f087-123">在行中单击或双击要更改其默认设置的任何其他单元，然后输入新值。</span><span class="sxs-lookup"><span data-stu-id="3f087-123">Click or double-click any other cells in the row you want to change from their default settings, and enter the new values.</span></span>  
  
7.  <span data-ttu-id="3f087-124">若要保存更改，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3f087-124">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreWGTSQL"></a> <span data-ttu-id="3f087-125">使用 Transact-SQL 创建工作负荷组</span><span class="sxs-lookup"><span data-stu-id="3f087-125">Create a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="3f087-126">**使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="3f087-126">**To create a workload group by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="3f087-127">运行 CREATE WORKLOAD GROUP 语句，指定要设置的属性值。</span><span class="sxs-lookup"><span data-stu-id="3f087-127">Run the CREATE WORKLOAD GROUP statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="3f087-128">运行 ALTER RESOURCE GOVERNOR RECONFIGURE 语句。</span><span class="sxs-lookup"><span data-stu-id="3f087-128">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="3f087-129">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3f087-129">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="3f087-130">以下示例创建一个名为 `groupAdhoc` 的工作负荷组，该组位于名为 `poolAdhoc`的资源池中。</span><span class="sxs-lookup"><span data-stu-id="3f087-130">The following example creates a workload group named `groupAdhoc` in the resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f087-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f087-131">See Also</span></span>  
 <span data-ttu-id="3f087-132">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="3f087-132">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="3f087-133">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="3f087-133">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="3f087-134">[创建资源池](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="3f087-134">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="3f087-135">[更改工作负荷组设置](change-workload-group-settings.md) </span><span class="sxs-lookup"><span data-stu-id="3f087-135">[Change Workload Group Settings](change-workload-group-settings.md) </span></span>  
 <span data-ttu-id="3f087-136">[创建和测试分类器用户定义函数](create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="3f087-136">[Create and Test a Classifier User-Defined Function](create-and-test-a-classifier-user-defined-function.md) </span></span>  
 <span data-ttu-id="3f087-137">[CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f087-137">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="3f087-138">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3f087-138">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
