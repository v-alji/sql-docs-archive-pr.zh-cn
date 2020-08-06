---
title: 禁用资源调控器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 172f01bdde0f792cd9ed72ad371e5811b8de8885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689312"
---
# <a name="disable-resource-governor"></a><span data-ttu-id="e71d2-102">禁用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e71d2-102">Disable Resource Governor</span></span>
  <span data-ttu-id="e71d2-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 禁用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="e71d2-103">You can disable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="e71d2-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="e71d2-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="e71d2-105">**若要禁用 Resource Governor，请使用：** [对象资源管理器](#RGOffObjEx)、[Resource Governor 属性](#RGOffProp)、[Transact-SQL](#RGOffTSQL)</span><span class="sxs-lookup"><span data-stu-id="e71d2-105">**To disable Resource Governorn, using:**  [Object Explorer](#RGOffObjEx), [Resource Governor Properties](#RGOffProp), [Transact-SQL](#RGOffTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e71d2-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="e71d2-106">Before You Begin</span></span>  
 <span data-ttu-id="e71d2-107">禁用资源调控器会产生下列结果：</span><span class="sxs-lookup"><span data-stu-id="e71d2-107">Disabling the Resource Governor has the following results:</span></span>  
  
-   <span data-ttu-id="e71d2-108">不运行分类器函数。</span><span class="sxs-lookup"><span data-stu-id="e71d2-108">The classifier function is not run.</span></span>  
  
-   <span data-ttu-id="e71d2-109">所有新连接被自动分类到默认工作负荷组中。</span><span class="sxs-lookup"><span data-stu-id="e71d2-109">All new connections are automatically classified into the default workload group.</span></span>  
  
-   <span data-ttu-id="e71d2-110">系统发起的请求被分类到内部工作负荷组中。</span><span class="sxs-lookup"><span data-stu-id="e71d2-110">System-initiated requests are classified into the internal workload group.</span></span>  
  
-   <span data-ttu-id="e71d2-111">所有现有的工作负荷组和资源池设置被重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="e71d2-111">All existing workload group and resource pool settings are reset to their default values.</span></span> <span data-ttu-id="e71d2-112">在这种情况下，到达限制时不触发任何事件。</span><span class="sxs-lookup"><span data-stu-id="e71d2-112">In this case, no events are fired when limits are reached.</span></span>  
  
-   <span data-ttu-id="e71d2-113">正常的系统监视不受影响。</span><span class="sxs-lookup"><span data-stu-id="e71d2-113">Normal system monitoring is not affected.</span></span>  
  
-   <span data-ttu-id="e71d2-114">可以进行配置更改，但是这些更改直到启用资源调控器之后才会生效。</span><span class="sxs-lookup"><span data-stu-id="e71d2-114">Configuration changes can be made, but the changes do not take effect until the Resource Governor is enabled.</span></span>  
  
-   <span data-ttu-id="e71d2-115">在重新启动 SQL Server 时，资源调控器不会加载其配置，而是只具有默认的和内部的工作负荷组和资源池。</span><span class="sxs-lookup"><span data-stu-id="e71d2-115">Upon restarting SQL Server, the Resource Governor will not load its configuration, but instead will have only the default and internal workload groups and resource pools.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e71d2-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e71d2-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e71d2-117">在用户事务中时，您不能使用 `ALTER RESOURCE GOVERNOR` 语句禁用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="e71d2-117">You cannot use the `ALTER RESOURCE GOVERNOR` statement to disable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e71d2-118">权限</span><span class="sxs-lookup"><span data-stu-id="e71d2-118">Permissions</span></span>  
 <span data-ttu-id="e71d2-119">禁用资源调控器需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="e71d2-119">Disabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="disable-resource-governor-using-object-explorer"></a><a name="RGOffObjEx"></a> <span data-ttu-id="e71d2-120">使用对象资源管理器禁用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e71d2-120">Disable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="e71d2-121">**使用对象资源管理器禁用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="e71d2-121">**To disable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="e71d2-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="e71d2-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="e71d2-123">右键单击“资源调控器”，再单击“禁用”。</span><span class="sxs-lookup"><span data-stu-id="e71d2-123">Right-click **Resource Governor**, and then click **Disable**.</span></span>  
  
##  <a name="disable-resource-governor-using-resource-governor-properties"></a><a name="RGOffProp"></a> <span data-ttu-id="e71d2-124">使用资源调控器属性禁用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e71d2-124">Disable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="e71d2-125">**使用“资源调控器属性”页禁用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="e71d2-125">**To disable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="e71d2-126">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="e71d2-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="e71d2-127">右键单击“资源调控器”  ，然后单击“属性” ，这将打开“资源调控器属性”页  。</span><span class="sxs-lookup"><span data-stu-id="e71d2-127">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="e71d2-128">单击 **“启用资源调控器”** 复选框，确保未选中该框，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e71d2-128">Click the **Enable Resource Governor** check box, ensure that the box is not selected, and then click **OK**.</span></span>  
  
##  <a name="disable-resource-governor-using-transact-sql"></a><a name="RGOffTSQL"></a> <span data-ttu-id="e71d2-129">使用 Transact-SQL 禁用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e71d2-129">Disable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="e71d2-130">**使用 Transact-SQL 禁用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="e71d2-130">**To disable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="e71d2-131">运行 **ALTER RESOURCE GOVERNOR DISABLE** 语句。</span><span class="sxs-lookup"><span data-stu-id="e71d2-131">Run the **ALTER RESOURCE GOVERNOR DISABLE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="e71d2-132">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e71d2-132">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="e71d2-133">以下示例启用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="e71d2-133">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e71d2-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e71d2-134">See Also</span></span>  
 <span data-ttu-id="e71d2-135">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e71d2-135">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="e71d2-136">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e71d2-136">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="e71d2-137">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="e71d2-137">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="e71d2-138">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="e71d2-138">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="e71d2-139">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="e71d2-139">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="e71d2-140">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e71d2-140">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
