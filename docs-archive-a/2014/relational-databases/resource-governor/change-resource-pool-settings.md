---
title: 更改资源池设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2183cceaaf8a3e183d96c154075f9a922942c2c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688804"
---
# <a name="change-resource-pool-settings"></a><span data-ttu-id="0348d-102">更改资源池设置</span><span class="sxs-lookup"><span data-stu-id="0348d-102">Change Resource Pool Settings</span></span>
  <span data-ttu-id="0348d-103">可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]更改资源池设置。</span><span class="sxs-lookup"><span data-stu-id="0348d-103">You can change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="0348d-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="0348d-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="0348d-105">若要更改资源池的设置，请使用：[SQL Server Management Studio](#ChgRPProp)、[Transact-SQL](#ChgRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="0348d-105">**To change the settings for a resource pool, using:**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0348d-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="0348d-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="0348d-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0348d-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0348d-108">最大 CPU 百分比必须大于或等于最小 CPU 百分比。</span><span class="sxs-lookup"><span data-stu-id="0348d-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="0348d-109">最大内存百分比必须大于或等于最小内存百分比。</span><span class="sxs-lookup"><span data-stu-id="0348d-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="0348d-110">所有资源池的最小 CPU 百分比和最小内存百分比的总和不得超过 100。</span><span class="sxs-lookup"><span data-stu-id="0348d-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0348d-111">权限</span><span class="sxs-lookup"><span data-stu-id="0348d-111">Permissions</span></span>  
 <span data-ttu-id="0348d-112">更改资源池设置需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="0348d-112">Changing resource pool settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-resource-pool-settings-using-sql-server-management-studio"></a><a name="ChgRPProp"></a> <span data-ttu-id="0348d-113">使用 SQL Server Management Studio 更改资源池设置</span><span class="sxs-lookup"><span data-stu-id="0348d-113">Change Resource Pool Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0348d-114">**使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="0348d-114">**To change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="0348d-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开对象资源管理器，然后依次逐步展开“管理”  节点直至其中包含“资源池” 。</span><span class="sxs-lookup"><span data-stu-id="0348d-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="0348d-116">右键单击要修改的资源池，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="0348d-116">Right-click the resource pool to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0348d-117">在 **“资源调控器属性”** 页中，如果资源池所在的行未自动选中，则在 **“资源池”** 网格内将其选中。</span><span class="sxs-lookup"><span data-stu-id="0348d-117">In the **Resource Governor Properties** page, select the row for the resource pool in the **Resource pools** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="0348d-118">在行中单击或双击要更改的单元，然后输入新值。</span><span class="sxs-lookup"><span data-stu-id="0348d-118">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="0348d-119">若要保存更改，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0348d-119">To save the changes, click **OK**</span></span>  
  
##  <a name="change-resource-pool-settings-using-transact-sql"></a><a name="ChgRPTSQL"></a> <span data-ttu-id="0348d-120">使用 Transact-SQL 更改资源池设置</span><span class="sxs-lookup"><span data-stu-id="0348d-120">Change Resource Pool Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="0348d-121">**使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="0348d-121">**To change resource pool settings by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="0348d-122">运行指定要更改的属性值的 `ALTER RESOURCE POOL` 语句。</span><span class="sxs-lookup"><span data-stu-id="0348d-122">Run the `ALTER RESOURCE POOL` statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="0348d-123">运行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 语句。</span><span class="sxs-lookup"><span data-stu-id="0348d-123">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="0348d-124">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0348d-124">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="0348d-125">以下示例更改名为 `poolAdhoc`的资源池的最大 CPU 百分比设置。</span><span class="sxs-lookup"><span data-stu-id="0348d-125">The following example changes the max CPU percentage setting for the resource pool named `poolAdhoc`.</span></span>  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0348d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0348d-126">See Also</span></span>  
 <span data-ttu-id="0348d-127">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="0348d-127">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="0348d-128">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="0348d-128">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="0348d-129">[创建资源池](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="0348d-129">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="0348d-130">[删除资源池](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="0348d-130">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="0348d-131">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="0348d-131">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="0348d-132">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="0348d-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="0348d-133">[ALTER RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0348d-133">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="0348d-134">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0348d-134">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
