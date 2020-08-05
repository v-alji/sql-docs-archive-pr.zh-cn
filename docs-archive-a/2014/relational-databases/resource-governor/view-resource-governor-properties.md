---
title: 查看资源调控器属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties.f1
helpviewer_keywords:
- Resource Governor, properties
ms.assetid: de3510df-f792-4a9d-80fa-f198fd36cdc8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cd7af8f4f8eb3cd0531bc907011846f73f94f6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580662"
---
# <a name="view-resource-governor-properties"></a><span data-ttu-id="ac60c-102">查看 Resource Governor 属性</span><span class="sxs-lookup"><span data-stu-id="ac60c-102">View Resource Governor Properties</span></span>
  <span data-ttu-id="ac60c-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的“资源调控器属性”页创建或配置资源调控器实体（如资源池和工作负荷组）。</span><span class="sxs-lookup"><span data-stu-id="ac60c-103">You can create or configure Resource Governor entities, such as resource pools and workload groups, by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="ac60c-104">**开始之前：** [权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ac60c-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="ac60c-105">**若要查看资源调控器属性，使用：**  [资源调控器属性页](#ViewRGProp)</span><span class="sxs-lookup"><span data-stu-id="ac60c-105">**To view Resource Governor properties, using:**  [Resource Governor Properties page](#ViewRGProp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ac60c-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="ac60c-106">Before You Begin</span></span>  
 <span data-ttu-id="ac60c-107">除了查看资源调控器实体的属性外，还可以使用 **“资源调控器属性”** 页执行多个配置任务。</span><span class="sxs-lookup"><span data-stu-id="ac60c-107">In addition to viewing the properties of Resource Governor entities, you can perform several configuration tasks using the **Resource Governor Properties** page.</span></span> <span data-ttu-id="ac60c-108">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="ac60c-108">For more information, see these topics:</span></span>  
  
-   [<span data-ttu-id="ac60c-109">启用资源调控器</span><span class="sxs-lookup"><span data-stu-id="ac60c-109">Enable Resource Governor</span></span>](enable-resource-governor.md)  
  
-   [<span data-ttu-id="ac60c-110">禁用资源调控器</span><span class="sxs-lookup"><span data-stu-id="ac60c-110">Disable Resource Governor</span></span>](disable-resource-governor.md)  
  
-   [<span data-ttu-id="ac60c-111">创建资源池</span><span class="sxs-lookup"><span data-stu-id="ac60c-111">Create a Resource Pool</span></span>](create-a-resource-pool.md)  
  
-   [<span data-ttu-id="ac60c-112">创建工作负荷组</span><span class="sxs-lookup"><span data-stu-id="ac60c-112">Create a Workload Group</span></span>](create-a-workload-group.md)  
  
-   [<span data-ttu-id="ac60c-113">更改资源池设置</span><span class="sxs-lookup"><span data-stu-id="ac60c-113">Change Resource Pool Settings</span></span>](change-resource-pool-settings.md)  
  
-   [<span data-ttu-id="ac60c-114">更改工作负荷组设置</span><span class="sxs-lookup"><span data-stu-id="ac60c-114">Change Workload Group Settings</span></span>](change-workload-group-settings.md)  
  
-   [<span data-ttu-id="ac60c-115">移动工作负荷组</span><span class="sxs-lookup"><span data-stu-id="ac60c-115">Move a Workload Group</span></span>](move-a-workload-group.md)  
  
 <span data-ttu-id="ac60c-116">添加、删除或移动工作负荷组或资源池后，当单击 **“确定”** 时，将执行 ALTER RESOURCE GOVERNOR RECONFIGURE 语句。</span><span class="sxs-lookup"><span data-stu-id="ac60c-116">When you click **OK** after adding, deleting, or moving a workload group or resource pool, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
 <span data-ttu-id="ac60c-117">如果创建或重新配置工作负荷组或资源池的操作失败，错误消息摘要将显示在属性页标题下方。</span><span class="sxs-lookup"><span data-stu-id="ac60c-117">If the create or reconfigure operation for the resource pool or workload group fails, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="ac60c-118">若要查看详细的错误消息，请单击错误信息上的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="ac60c-118">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
 <span data-ttu-id="ac60c-119">可以通过查询 [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 动态管理视图来获取 is_configuration_pending 的当前状态以确定是否存在配置挂起。</span><span class="sxs-lookup"><span data-stu-id="ac60c-119">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ac60c-120">权限</span><span class="sxs-lookup"><span data-stu-id="ac60c-120">Permissions</span></span>  
 <span data-ttu-id="ac60c-121">查看资源调控器属性需要 VIEW SERVER STATER 权限。</span><span class="sxs-lookup"><span data-stu-id="ac60c-121">Viewing resource governor properties requires VIEW SERVER STATER permission.</span></span> <span data-ttu-id="ac60c-122">资源调控器配置任务需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="ac60c-122">The resource governor configuration tasks require CONTROL SERVER permission.</span></span>  
  
##  <a name="view-the-resource-governor-properties-page"></a><a name="ViewRGProp"></a><span data-ttu-id="ac60c-123">查看 Resource Governor 属性页</span><span class="sxs-lookup"><span data-stu-id="ac60c-123">View the Resource Governor Properties Page</span></span>  
 <span data-ttu-id="ac60c-124">**若要查看资源调控器属性，请使用资源调控器属性页 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="ac60c-124">**To view resource governor properties by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="ac60c-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至 **“资源调控器”** 。</span><span class="sxs-lookup"><span data-stu-id="ac60c-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="ac60c-126">右键单击“资源调控器”  ，然后单击“属性” ，这将打开“资源调控器属性”页  。</span><span class="sxs-lookup"><span data-stu-id="ac60c-126">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="ac60c-127">有关该页中的字段的说明，请参阅 [资源调控器属性](#RGProp)。</span><span class="sxs-lookup"><span data-stu-id="ac60c-127">For descriptions of the fields in the page, see [Resource Governor Properties](#RGProp).</span></span>  
  
4.  <span data-ttu-id="ac60c-128">若要保存任何更改，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ac60c-128">To save any changes, click **OK**.</span></span>  
  
##  <a name="resource-governor-properties"></a><a name="RGProp"></a><span data-ttu-id="ac60c-129">Resource Governor 属性</span><span class="sxs-lookup"><span data-stu-id="ac60c-129">Resource Governor Properties</span></span>  
 <span data-ttu-id="ac60c-130">**分类器函数名称**</span><span class="sxs-lookup"><span data-stu-id="ac60c-130">**Classifier function name**</span></span>  
 <span data-ttu-id="ac60c-131">通过从列表中选择来指定分类器函数。</span><span class="sxs-lookup"><span data-stu-id="ac60c-131">Specify the classifier function by selecting from the list.</span></span>  
  
 <span data-ttu-id="ac60c-132">**启用资源调控器**</span><span class="sxs-lookup"><span data-stu-id="ac60c-132">**Enable Resource Governor**</span></span>  
 <span data-ttu-id="ac60c-133">通过选中或清除复选框来启用或禁用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="ac60c-133">Enable or disable Resource Governor by selecting or clearing the check box.</span></span>  
  
 <span data-ttu-id="ac60c-134">**资源池**</span><span class="sxs-lookup"><span data-stu-id="ac60c-134">**Resource pools**</span></span>  
 <span data-ttu-id="ac60c-135">通过使用提供的网格创建或更改资源池配置。</span><span class="sxs-lookup"><span data-stu-id="ac60c-135">Create or change resource pool configuration by using the grid that is provided.</span></span> <span data-ttu-id="ac60c-136">此网格使用预定义的内部和默认池的信息进行填充。</span><span class="sxs-lookup"><span data-stu-id="ac60c-136">This grid is populated with information for the predefined internal and default pools.</span></span> <span data-ttu-id="ac60c-137">通过单击池中某行的第一列来选择要处理的池。</span><span class="sxs-lookup"><span data-stu-id="ac60c-137">Select a pool to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="ac60c-138">若要创建新的资源池，请单击带星号 (&#42;) 前缀的行。</span><span class="sxs-lookup"><span data-stu-id="ac60c-138">To create a new resource pool, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="ac60c-139">**名称**</span><span class="sxs-lookup"><span data-stu-id="ac60c-139">**Name**</span></span>  
 <span data-ttu-id="ac60c-140">指定资源池的名称。</span><span class="sxs-lookup"><span data-stu-id="ac60c-140">Specify the name of the resource pool.</span></span>  
  
 <span data-ttu-id="ac60c-141">**最低 CPU %**</span><span class="sxs-lookup"><span data-stu-id="ac60c-141">**Minimum CPU %**</span></span>  
 <span data-ttu-id="ac60c-142">指定出现 CPU 争用时资源池中的所有请求可获得的有保证的平均 CPU 带宽。</span><span class="sxs-lookup"><span data-stu-id="ac60c-142">Specify the guaranteed average CPU bandwidth for all requests in the resource pool when there is CPU contention.</span></span> <span data-ttu-id="ac60c-143">范围从 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-143">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="ac60c-144">**最高 CPU %**</span><span class="sxs-lookup"><span data-stu-id="ac60c-144">**Maximum CPU %**</span></span>  
 <span data-ttu-id="ac60c-145">指定出现 CPU 争用时，此资源池中的所有请求可获得的最大平均 CPU 带宽。</span><span class="sxs-lookup"><span data-stu-id="ac60c-145">Specify the maximum average CPU bandwidth that all requests in this resource pool will receive when there is CPU contention.</span></span> <span data-ttu-id="ac60c-146">范围从 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-146">Range is 0 to 100.</span></span> <span data-ttu-id="ac60c-147">默认设置为 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-147">The default setting is 100.</span></span>  
  
 <span data-ttu-id="ac60c-148">**最低内存 %**</span><span class="sxs-lookup"><span data-stu-id="ac60c-148">**Minimum Memory %**</span></span>  
 <span data-ttu-id="ac60c-149">指定为此资源池保留的不与其他资源池共享的最小内存量。</span><span class="sxs-lookup"><span data-stu-id="ac60c-149">Specify the minimum amount of memory reserved for this resource pool that can not be shared with other resource pools.</span></span> <span data-ttu-id="ac60c-150">范围从 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-150">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="ac60c-151">**最高内存 %**</span><span class="sxs-lookup"><span data-stu-id="ac60c-151">**Maximum Memory %**</span></span>  
 <span data-ttu-id="ac60c-152">指定此资源池中的请求可使用的总服务器内存。</span><span class="sxs-lookup"><span data-stu-id="ac60c-152">Specify the total server memory that can be used by requests in this resource pool.</span></span> <span data-ttu-id="ac60c-153">范围从 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-153">Range is 0 to 100.</span></span> <span data-ttu-id="ac60c-154">默认设置为 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-154">The default setting is 100.</span></span>  
  
 <span data-ttu-id="ac60c-155">有关详细信息，请参阅[CREATE RESOURCE POOL &#40;transact-sql&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac60c-155">For more information, see [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).</span></span>  
  
 <span data-ttu-id="ac60c-156">**资源池的工作负荷组**</span><span class="sxs-lookup"><span data-stu-id="ac60c-156">**Workload groups for resource pool**</span></span>  
 <span data-ttu-id="ac60c-157">通过使用提供的网格创建或更改工作负荷组配置。</span><span class="sxs-lookup"><span data-stu-id="ac60c-157">Create or change the workload group configuration by using the grid that is provided.</span></span> <span data-ttu-id="ac60c-158">此网格使用预定义的内部和默认组的信息进行填充。</span><span class="sxs-lookup"><span data-stu-id="ac60c-158">This grid is populated with information for the predefined internal and default groups.</span></span> <span data-ttu-id="ac60c-159">通过单击池中某行的第一列来选择要处理的组。</span><span class="sxs-lookup"><span data-stu-id="ac60c-159">Select a group to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="ac60c-160">若要创建新的工作组，请单击带星号 (&#42;) 前缀的行。</span><span class="sxs-lookup"><span data-stu-id="ac60c-160">To create a new workload group, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="ac60c-161">**名称**</span><span class="sxs-lookup"><span data-stu-id="ac60c-161">**Name**</span></span>  
 <span data-ttu-id="ac60c-162">指定工作负荷组的名称。</span><span class="sxs-lookup"><span data-stu-id="ac60c-162">Specify the name of the workload group.</span></span>  
  
 <span data-ttu-id="ac60c-163">**重要性**</span><span class="sxs-lookup"><span data-stu-id="ac60c-163">**Importance**</span></span>  
 <span data-ttu-id="ac60c-164">指定工作负荷组中的请求的相对重要性。</span><span class="sxs-lookup"><span data-stu-id="ac60c-164">Specify the relative importance of a request in the workload group.</span></span> <span data-ttu-id="ac60c-165">可用设置分为低、中和高三个级别。</span><span class="sxs-lookup"><span data-stu-id="ac60c-165">Available settings are Low, Medium, and High.</span></span>  
  
 <span data-ttu-id="ac60c-166">**最大请求数**</span><span class="sxs-lookup"><span data-stu-id="ac60c-166">**Maximum Requests**</span></span>  
 <span data-ttu-id="ac60c-167">指定允许在工作负荷组中同时执行的请求的最大数。</span><span class="sxs-lookup"><span data-stu-id="ac60c-167">Specify the maximum number of simultaneous requests that are allowed to execute in the workload group.</span></span> <span data-ttu-id="ac60c-168">必须是 0 或一个正整数。</span><span class="sxs-lookup"><span data-stu-id="ac60c-168">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="ac60c-169">**CPU 时间(秒)**</span><span class="sxs-lookup"><span data-stu-id="ac60c-169">**CPU Time (sec)**</span></span>  
 <span data-ttu-id="ac60c-170">指定请求可使用的最大 CPU 时间量。</span><span class="sxs-lookup"><span data-stu-id="ac60c-170">Specify the maximum amount of CPU time that a request can use.</span></span> <span data-ttu-id="ac60c-171">必须是 0 或一个正整数。</span><span class="sxs-lookup"><span data-stu-id="ac60c-171">Must be 0 or a positive integer.</span></span> <span data-ttu-id="ac60c-172">如果为 0，则时间没有限制。</span><span class="sxs-lookup"><span data-stu-id="ac60c-172">If 0, the time is unlimited.</span></span>  
  
 <span data-ttu-id="ac60c-173">**内存授予 %**</span><span class="sxs-lookup"><span data-stu-id="ac60c-173">**Memory Grant %**</span></span>  
 <span data-ttu-id="ac60c-174">指定单个请求可从池中获取的最大内存量。</span><span class="sxs-lookup"><span data-stu-id="ac60c-174">Specify the maximum amount of memory that a single request can take from the pool.</span></span> <span data-ttu-id="ac60c-175">范围从 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="ac60c-175">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="ac60c-176">**授予超时值(秒)**</span><span class="sxs-lookup"><span data-stu-id="ac60c-176">**Grant Time-out (sec)**</span></span>  
 <span data-ttu-id="ac60c-177">指定查询在失败之前等待资源变为可用的最长时间。</span><span class="sxs-lookup"><span data-stu-id="ac60c-177">Specify the maximum time that a query can wait for a resource to become available before the query fails.</span></span> <span data-ttu-id="ac60c-178">必须是 0 或一个正整数。</span><span class="sxs-lookup"><span data-stu-id="ac60c-178">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="ac60c-179">**并行度**</span><span class="sxs-lookup"><span data-stu-id="ac60c-179">**Degree of Parallelism**</span></span>  
 <span data-ttu-id="ac60c-180">指定并行请求的最大并行度 (DOP)。</span><span class="sxs-lookup"><span data-stu-id="ac60c-180">Specify the maximum degree of parallelism (DOP) for parallel requests.</span></span> <span data-ttu-id="ac60c-181">范围从 0 到 64。</span><span class="sxs-lookup"><span data-stu-id="ac60c-181">Range is 0 to 64.</span></span>  
  
 <span data-ttu-id="ac60c-182">有关详细信息，请参阅 [CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac60c-182">For more information, see [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql).</span></span>  
  
## <a name="view-resource-governor-properties-by-using-transact-sql"></a><span data-ttu-id="ac60c-183">使用 Transact-sql 查看 Resource Governor 属性</span><span class="sxs-lookup"><span data-stu-id="ac60c-183">View Resource Governor Properties by Using Transact-SQL</span></span>  
 <span data-ttu-id="ac60c-184">**使用 Transact-SQL 查看资源调控器属性**</span><span class="sxs-lookup"><span data-stu-id="ac60c-184">**View resource governor properties by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="ac60c-185">若要查看资源调控器实体的定义，请使用[资源调控器目录视图 (Transact-SQL)](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac60c-185">To view the definitions of resource governor entities, use the [Resource Governor Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql).</span></span>  
  
2.  <span data-ttu-id="ac60c-186">若要查看资源调控器实体的当前配置，请使用[与资源调控器相关的动态管理视图 (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac60c-186">To view the current configuration of resource governor entities, use the [Resource Governor Related Dynamic Management Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac60c-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac60c-187">See Also</span></span>  
 <span data-ttu-id="ac60c-188">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ac60c-188">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="ac60c-189">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ac60c-189">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="ac60c-190">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ac60c-190">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="ac60c-191">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="ac60c-191">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 [<span data-ttu-id="ac60c-192">资源调控器分类器函数</span><span class="sxs-lookup"><span data-stu-id="ac60c-192">Resource Governor Classifier Function</span></span>](resource-governor-classifier-function.md)  
  
  
