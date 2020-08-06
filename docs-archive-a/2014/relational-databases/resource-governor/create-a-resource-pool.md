---
title: 创建资源池 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5abd2e60f4f9bb5290b47f95349782f8b26ad8bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591227"
---
# <a name="create-a-resource-pool"></a><span data-ttu-id="ea0df-102">创建资源池</span><span class="sxs-lookup"><span data-stu-id="ea0df-102">Create a Resource Pool</span></span>
  <span data-ttu-id="ea0df-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]创建资源池。</span><span class="sxs-lookup"><span data-stu-id="ea0df-103">You can create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="ea0df-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ea0df-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="ea0df-105">**要创建资源池，请使用：** [SQL Server Management Studio](#CreRPProp)、[Transact-SQL](#CreRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="ea0df-105">**To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ea0df-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="ea0df-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="ea0df-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ea0df-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ea0df-108">最大 CPU 百分比必须大于或等于最小 CPU 百分比。</span><span class="sxs-lookup"><span data-stu-id="ea0df-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="ea0df-109">最大内存百分比必须大于或等于最小内存百分比。</span><span class="sxs-lookup"><span data-stu-id="ea0df-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="ea0df-110">所有资源池的最小 CPU 百分比和最小内存百分比的总和不得超过 100。</span><span class="sxs-lookup"><span data-stu-id="ea0df-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea0df-111">权限</span><span class="sxs-lookup"><span data-stu-id="ea0df-111">Permissions</span></span>  
 <span data-ttu-id="ea0df-112">创建资源池需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="ea0df-112">Creating a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> <span data-ttu-id="ea0df-113">使用 SQL Server Management Studio 创建资源池</span><span class="sxs-lookup"><span data-stu-id="ea0df-113">Create a Resource Pool Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ea0df-114">**使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="ea0df-114">**To create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="ea0df-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至其中并包含 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="ea0df-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="ea0df-116">右键单击“Resource Governor”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="ea0df-116">Right-click **Resource Governor**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ea0df-117">在 **“资源池”** 网格中，单击空行中的第一列。</span><span class="sxs-lookup"><span data-stu-id="ea0df-117">In the **Resource pools** grid, click the first column in the empty row.</span></span> <span data-ttu-id="ea0df-118">此列标记有星号 (\*)。</span><span class="sxs-lookup"><span data-stu-id="ea0df-118">This column is labeled with an asterisk (\*).</span></span>  
  
4.  <span data-ttu-id="ea0df-119">双击“名称”列中的空单元格。</span><span class="sxs-lookup"><span data-stu-id="ea0df-119">Double-click the empty cell in the **Name** column.</span></span> <span data-ttu-id="ea0df-120">键入要用于该资源池的名称。</span><span class="sxs-lookup"><span data-stu-id="ea0df-120">Type in the name that you want to use for the resource pool.</span></span>  
  
5.  <span data-ttu-id="ea0df-121">在行中单击或双击要更改的任何其他单元，然后输入新值。</span><span class="sxs-lookup"><span data-stu-id="ea0df-121">Click or double-click any other cells in the row you want to change, and enter the new values.</span></span>  
  
6.  <span data-ttu-id="ea0df-122">若要保存更改，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ea0df-122">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a> <span data-ttu-id="ea0df-123">使用 Transact-SQL 创建资源池</span><span class="sxs-lookup"><span data-stu-id="ea0df-123">Create a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="ea0df-124">**使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="ea0df-124">**To create a resource pool by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="ea0df-125">运行指定要设置的属性值的 `CREATE RESOURCE POOL` 语句。</span><span class="sxs-lookup"><span data-stu-id="ea0df-125">Run the `CREATE RESOURCE POOL` statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="ea0df-126">运行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 语句。</span><span class="sxs-lookup"><span data-stu-id="ea0df-126">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="ea0df-127">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ea0df-127">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="ea0df-128">下面的示例创建名为 `poolAdhoc`的资源池。</span><span class="sxs-lookup"><span data-stu-id="ea0df-128">The following example creates a resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea0df-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea0df-129">See Also</span></span>  
 <span data-ttu-id="ea0df-130">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-130">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="ea0df-131">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-131">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="ea0df-132">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-132">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="ea0df-133">[更改资源池设置](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-133">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="ea0df-134">[删除资源池](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-134">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="ea0df-135">[使用模板配置资源调控器](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-135">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="ea0df-136">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-136">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="ea0df-137">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="ea0df-137">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="ea0df-138">[CREATE RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ea0df-138">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="ea0df-139">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ea0df-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
