---
title: 启用资源调控器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b1b0f780457aa5a4d26cbb463c9f31a94185f0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689310"
---
# <a name="enable-resource-governor"></a><span data-ttu-id="e0aa2-102">启用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e0aa2-102">Enable Resource Governor</span></span>
  <span data-ttu-id="e0aa2-103">默认情况下，资源调控器处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-103">The Resource Governor is turned off by default.</span></span> <span data-ttu-id="e0aa2-104">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 启用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-104">You can enable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="e0aa2-105">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="e0aa2-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="e0aa2-106">若要启用 Resource Governor，请使用：[对象资源管理器](#RGOnObjEx)、[Resource Governor 属性](#RGOnProp)、[Transact-SQL](#RGOnTSQL)</span><span class="sxs-lookup"><span data-stu-id="e0aa2-106">**To enable Resource Governorn, using:**  [Object Explorer](#RGOnObjEx), [Resource Governor Properties](#RGOnProp), [Transact-SQL](#RGOnTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e0aa2-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="e0aa2-107">Before You Begin</span></span>  
 <span data-ttu-id="e0aa2-108">启用资源调控器会产生下列结果：</span><span class="sxs-lookup"><span data-stu-id="e0aa2-108">Enabling the resource governor has the following results:</span></span>  
  
-   <span data-ttu-id="e0aa2-109">为新连接运行分类器函数，以便可以将其工作负荷分配到工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-109">The classifier function is run for new connections so that their workloads can be assigned to workload groups.</span></span>  
  
-   <span data-ttu-id="e0aa2-110">遵守并强制执行资源调控器配置中指定的资源限制。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-110">The resource limits that are specified in the Resource Governor configuration are honored and enforced.</span></span>  
  
-   <span data-ttu-id="e0aa2-111">禁用资源调控器时所做的任何配置更改会影响在启用资源调控器之前就已存在的请求。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-111">Requests that existed before enabling Resource Governor are affected by any configuration changes that were made when the Resource Governor was disabled.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e0aa2-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e0aa2-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e0aa2-113">在用户事务中时，您不能使用 `ALTER RESOURCE GOVERNOR` 语句启用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-113">You cannot use the `ALTER RESOURCE GOVERNOR` statement to enable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e0aa2-114">权限</span><span class="sxs-lookup"><span data-stu-id="e0aa2-114">Permissions</span></span>  
 <span data-ttu-id="e0aa2-115">启用资源调控器需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-115">Enabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="enable-resource-governor-using-object-explorer"></a><a name="RGOnObjEx"></a> <span data-ttu-id="e0aa2-116">使用对象资源管理器启用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e0aa2-116">Enable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="e0aa2-117">**使用对象资源管理器启用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="e0aa2-117">**To enable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="e0aa2-118">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="e0aa2-119">右键单击“资源调控器” ，再单击“启用” 。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-119">Right-click **Resource Governor**, and then click **Enable**.</span></span>  
  
##  <a name="enable-resource-governor-using-resource-governor-properties"></a><a name="RGOnProp"></a> <span data-ttu-id="e0aa2-120">使用资源调控器属性启用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e0aa2-120">Enable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="e0aa2-121">**使用“资源调控器属性”页启用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="e0aa2-121">**To enable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="e0aa2-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="e0aa2-123">右键单击“资源调控器”  ，然后单击“属性” ，这将打开“资源调控器属性”页  。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-123">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="e0aa2-124">单击 **“启用资源调控器”** 复选框，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-124">Click the **Enable Resource Governor** check box, and then click **OK**.</span></span>  
  
##  <a name="enable-resource-governor-using-transact-sql"></a><a name="RGOnTSQL"></a> <span data-ttu-id="e0aa2-125">使用 Transact-SQL 启用资源调控器</span><span class="sxs-lookup"><span data-stu-id="e0aa2-125">Enable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="e0aa2-126">**使用 Transact-SQL 启用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="e0aa2-126">**To enable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="e0aa2-127">运行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 语句。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-127">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="e0aa2-128">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e0aa2-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="e0aa2-129">以下示例启用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-129">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0aa2-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0aa2-130">See Also</span></span>  
 <span data-ttu-id="e0aa2-131">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e0aa2-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="e0aa2-132">[禁用资源调控器](disable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e0aa2-132">[Disable Resource Governor](disable-resource-governor.md) </span></span>  
 <span data-ttu-id="e0aa2-133">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="e0aa2-133">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="e0aa2-134">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="e0aa2-134">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="e0aa2-135">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="e0aa2-135">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="e0aa2-136">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e0aa2-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
