---
title: 缓存刷新选项 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 83b2ef4396c774f3ac344704756cd1c7e90d4e04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586511"
---
# <a name="cache-refresh-options-report-manager"></a><span data-ttu-id="dc427-102">缓存刷新选项（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="dc427-102">Cache Refresh Options (Report Manager)</span></span>
  <span data-ttu-id="dc427-103">使用“缓存刷新选项”页可以创建使用报表或共享数据集数据的临时副本预加载缓存的计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-103">Use the Cache Refresh options page to create schedules for preloading the cache with temporary copies of data for a report or for a shared dataset.</span></span> <span data-ttu-id="dc427-104">刷新计划包括计划和指定或覆盖参数值的选项。</span><span class="sxs-lookup"><span data-stu-id="dc427-104">A refresh plan includes a schedule and the option to specify or override values for parameters.</span></span> <span data-ttu-id="dc427-105">对于共享数据集，不能覆盖标记为只读的参数值。</span><span class="sxs-lookup"><span data-stu-id="dc427-105">For a shared dataset, you cannot override values for parameters that are marked read-only.</span></span> <span data-ttu-id="dc427-106">在刷新选项页中，可以创建和使用多个刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-106">You can create and use more than one refresh plan as part of the refresh options page.</span></span>  
  
 <span data-ttu-id="dc427-107">通过“内容管理员”、“我的报表”和“发布者”默认角色分配，您可以添加、删除、更改和查看缓存刷新计划的相关报表和共享数据集。</span><span class="sxs-lookup"><span data-stu-id="dc427-107">Default role assignments that enable you to add, delete, change, and view related reports and shared datasets for cache refresh plans are Content Manager, My Reports, and Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc427-108">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="dc427-108">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dc427-109">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="dc427-109">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a><span data-ttu-id="dc427-110">打开报表或共享数据集的“缓存刷新计划”属性页</span><span class="sxs-lookup"><span data-stu-id="dc427-110">To open the Cache Refresh Plan properties page for a report or shared dataset</span></span>  
  
1.  <span data-ttu-id="dc427-111">打开报表管理器，找到您要配置缓存刷新计划属性的报表或共享数据集。</span><span class="sxs-lookup"><span data-stu-id="dc427-111">Open Report Manager, and locate the report or shared dataset for which you want to configure cache refresh plan properties.</span></span>  
  
2.  <span data-ttu-id="dc427-112">悬停在该报表或共享数据集之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="dc427-112">Hover over the report or shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="dc427-113">在下拉列表中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="dc427-113">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="dc427-114">此时将打开 "**常规属性**" 页。</span><span class="sxs-lookup"><span data-stu-id="dc427-114">The **General properties** page opens.</span></span>  
  
4.  <span data-ttu-id="dc427-115">单击 **“缓存刷新计划”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dc427-115">Click the **Cache Refresh Plan** tab.</span></span>  
  
5.  <span data-ttu-id="dc427-116">若要创建新的缓存计划，请单击 **“新建缓存刷新计划”**。</span><span class="sxs-lookup"><span data-stu-id="dc427-116">To create a new cache plan, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc427-117">必须启用并启动 SQL Server 代理服务，才能创建缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-117">You must enable and start the SQL Server Agent service to create a cache refresh plan.</span></span>  
  
6.  <span data-ttu-id="dc427-118">若要创建缓存计划的副本然后对其自定义，请单击 **“根据现有内容新建”**。</span><span class="sxs-lookup"><span data-stu-id="dc427-118">To create a copy of a cache plan and then customize it, click **New from Existing**.</span></span>  
  
## <a name="cache-refresh-options"></a><span data-ttu-id="dc427-119">缓存刷新选项</span><span class="sxs-lookup"><span data-stu-id="dc427-119">Cache Refresh Options</span></span>  
 <span data-ttu-id="dc427-120">**删除**</span><span class="sxs-lookup"><span data-stu-id="dc427-120">**Delete**</span></span>  
 <span data-ttu-id="dc427-121">删除所有当前所选的刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-121">Deletes all of the currently selected refresh plans.</span></span>  
  
 <span data-ttu-id="dc427-122">**“根据现有内容新建”**</span><span class="sxs-lookup"><span data-stu-id="dc427-122">**New from existing**</span></span>  
 <span data-ttu-id="dc427-123">仅当选择一个缓存刷新计划时启用此选项。</span><span class="sxs-lookup"><span data-stu-id="dc427-123">This option is enabled when one and only one cache refresh plan is selected.</span></span> <span data-ttu-id="dc427-124">此选项将创建一个新的刷新计划，该计划是从原始计划复制而来。</span><span class="sxs-lookup"><span data-stu-id="dc427-124">This option will create a new refresh plan which is copied from the original plan.</span></span> <span data-ttu-id="dc427-125">将打开缓存刷新计划页，其中预先填充了所选计划的详细信息。</span><span class="sxs-lookup"><span data-stu-id="dc427-125">The cache refresh plan page opens pre-populated with details from the plan that was selected.</span></span> <span data-ttu-id="dc427-126">然后，您可以修改刷新计划选项并用新说明保存该计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-126">You can then modify the refresh plan options and save the plan with a new description.</span></span>  
  
 <span data-ttu-id="dc427-127">**“新建缓存刷新计划”**</span><span class="sxs-lookup"><span data-stu-id="dc427-127">**New cache refresh plan**</span></span>  
 <span data-ttu-id="dc427-128">单击以创建要在当前缓存刷新选项中使用的新刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-128">Click to create a new refresh plan to be used in the current cache refresh options.</span></span>  
  
 <span data-ttu-id="dc427-129">**编辑**</span><span class="sxs-lookup"><span data-stu-id="dc427-129">**Edit**</span></span>  
 <span data-ttu-id="dc427-130">选择此选项可以编辑当前刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-130">Select this option to edit the current refresh plan.</span></span>  
  
## <a name="cache-refresh-plan-options"></a><span data-ttu-id="dc427-131">缓存刷新计划选项</span><span class="sxs-lookup"><span data-stu-id="dc427-131">Cache Refresh Plan Options</span></span>  
 <span data-ttu-id="dc427-132">**说明**</span><span class="sxs-lookup"><span data-stu-id="dc427-132">**Description**</span></span>  
 <span data-ttu-id="dc427-133">指定缓存刷新计划的说明。</span><span class="sxs-lookup"><span data-stu-id="dc427-133">Specify a description for the cache refresh plan.</span></span>  
  
 <span data-ttu-id="dc427-134">**项特定的计划**</span><span class="sxs-lookup"><span data-stu-id="dc427-134">**Item-specific schedule**</span></span>  
 <span data-ttu-id="dc427-135">选择此选项可以创建仅供此项使用的计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-135">Select this option to create a schedule that is used only by this item.</span></span>  
  
 <span data-ttu-id="dc427-136">**将“报表”**</span><span class="sxs-lookup"><span data-stu-id="dc427-136">**Configure**</span></span>  
 <span data-ttu-id="dc427-137">单击此选项可打开用于指定频率信息的“计划”页。</span><span class="sxs-lookup"><span data-stu-id="dc427-137">Click to open the Schedule page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="dc427-138">有关详细信息，请参阅 "[新建计划：编辑计划" 页 &#40;报表管理器&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="dc427-138">For more information, see [New Schedule: Edit Schedule Page &#40;Report Manager&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="dc427-139">**共享计划**</span><span class="sxs-lookup"><span data-stu-id="dc427-139">**Shared schedule**</span></span>  
 <span data-ttu-id="dc427-140">选择此选项可以选择现有计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-140">Select this option to select an existing schedule.</span></span>  
  
 <span data-ttu-id="dc427-141">有关详细信息，请参阅 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="dc427-141">For more information, see [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md).</span></span>  
  
 **@\<** *Parameter* **>**  
 <span data-ttu-id="dc427-142">指定参数值的一个组合。</span><span class="sxs-lookup"><span data-stu-id="dc427-142">Specify one combination of parameter values.</span></span> <span data-ttu-id="dc427-143">只有在当前数据集或报表有参数时，才会显示此部分。</span><span class="sxs-lookup"><span data-stu-id="dc427-143">This section appears only if the current dataset or report has parameters.</span></span>  
  
 <span data-ttu-id="dc427-144">请参阅下一节中的 [指定参数](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="dc427-144">See [Specifying Parameters](#Parameters) in the next section.</span></span>  
  
 <span data-ttu-id="dc427-145">**使用默认值**</span><span class="sxs-lookup"><span data-stu-id="dc427-145">**Use Default**</span></span>  
 <span data-ttu-id="dc427-146">选择此选项可以使用此参数的预定义默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-146">Select this option to use the predefined default value for this parameter.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="dc427-147">指定参数</span><span class="sxs-lookup"><span data-stu-id="dc427-147">Specifying Parameters</span></span>  
 <span data-ttu-id="dc427-148">若要创建缓存刷新计划，每个报表或共享数据集参数必须赋值。</span><span class="sxs-lookup"><span data-stu-id="dc427-148">To create a cache refresh plan, each report or shared dataset parameter must have a value.</span></span> <span data-ttu-id="dc427-149">如果报表或共享数据集项在定义中未指定默认值，您必须指定一个值。</span><span class="sxs-lookup"><span data-stu-id="dc427-149">If the report or shared dataset item does not have a default value specified in the definition, you must specify a value.</span></span> <span data-ttu-id="dc427-150">如果默认值存在，则不需要在此处提供值。</span><span class="sxs-lookup"><span data-stu-id="dc427-150">If a default value exists, you do not need to provide one here.</span></span> <span data-ttu-id="dc427-151">如果提供了值，该值将覆盖默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-151">If you do provide a value, the value overrides the default value.</span></span>  
  
 <span data-ttu-id="dc427-152">若要指定参数值的多个组合，请为每个组合创建单独的缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-152">To specify multiple combinations of parameter values, create a separate cache refresh plan for each combination.</span></span>  
  
 <span data-ttu-id="dc427-153">如果对报表或共享数据集的参数进行添加、更改和删除，将会影响缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="dc427-153">Additions, changes, and deletions made to parameters on a report or shared dataset can affect the cache refresh plan.</span></span> <span data-ttu-id="dc427-154">如果为报表添加具有默认值的参数、删除参数或更改共享数据集参数的数据类型或只读选项，所做的更改将在下次处理缓存刷新计划时生效。</span><span class="sxs-lookup"><span data-stu-id="dc427-154">If you add a parameter with a default value for a report, remove a parameter, or change the data type or the read-only option for a shared dataset parameter, the changes take affect the next time the cache refresh plan is processed.</span></span>  
  
### <a name="shared-dataset-parameters"></a><span data-ttu-id="dc427-155">共享数据集参数</span><span class="sxs-lookup"><span data-stu-id="dc427-155">Shared Dataset Parameters</span></span>  
 <span data-ttu-id="dc427-156">对于共享数据集，以下信息是从共享数据集定义派生的：</span><span class="sxs-lookup"><span data-stu-id="dc427-156">For a shared dataset, the following information is derived from the shared dataset definition:</span></span>  
  
-   <span data-ttu-id="dc427-157">**名称** ：指定查询参数的名称。</span><span class="sxs-lookup"><span data-stu-id="dc427-157">**Name** Specifies the name of the query parameter.</span></span>  
  
-   <span data-ttu-id="dc427-158">**类型** ：指定查询参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="dc427-158">**Type** Specifies the data type of the query parameter.</span></span> <span data-ttu-id="dc427-159">由于此数据类型在数据访问接口处理数据集查询前是未知的，直到处理共享数据集时才进行数据类型验证。</span><span class="sxs-lookup"><span data-stu-id="dc427-159">Because this data type is unknown until the data provider processes the dataset query, data type validation cannot occur until the shared dataset is processed.</span></span>  
  
-   <span data-ttu-id="dc427-160">**可以为 Null** ：指定 NULL 是否是有效值。</span><span class="sxs-lookup"><span data-stu-id="dc427-160">**Nullable** Specifies whether NULL is a valid value.</span></span>  
  
-   <span data-ttu-id="dc427-161">**只读** ：指定此参数是否在共享数据集定义中被标记为只读。</span><span class="sxs-lookup"><span data-stu-id="dc427-161">**ReadOnly** Specifies whether this parameter is marked read-only in the shared dataset definition.</span></span> <span data-ttu-id="dc427-162">只读参数不会出现在缓存刷新选项的参数列表中，在共享数据集定义中必须为其指定默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-162">Read only parameters do not appear in the parameter list for cache refresh options and must have a default specified as part of the shared dataset definition.</span></span>  
  
-   <span data-ttu-id="dc427-163">**默认值** ：在共享数据集定义中指定的默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-163">**DefaultValues** Default values that have been specified in the shared dataset definition.</span></span> <span data-ttu-id="dc427-164">查询参数可以是多值的。</span><span class="sxs-lookup"><span data-stu-id="dc427-164">Query parameters can be multivalued.</span></span> <span data-ttu-id="dc427-165">若要覆盖默认值，请在文本框提示区域中键入新值。</span><span class="sxs-lookup"><span data-stu-id="dc427-165">To override the default values, type new values in the text box prompt areas.</span></span>  
  
 <span data-ttu-id="dc427-166">如果共享数据集定义中为参数指定了 **“从查询中省略”** 选项，则不必提供默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-166">If the shared dataset definition specifies the option **Omit from query** for a parameter, you do not need to provide a default value.</span></span> <span data-ttu-id="dc427-167">此标志表示不在查询中使用数据集参数。</span><span class="sxs-lookup"><span data-stu-id="dc427-167">This flag indicates that the dataset parameter is not used in the query.</span></span> <span data-ttu-id="dc427-168">例如，该参数出现在共享数据集定义中，因为它是仅在数据集筛选器中使用的报表参数。</span><span class="sxs-lookup"><span data-stu-id="dc427-168">For example, the parameter appears in the shared dataset definition because it is a report parameter that is used in the dataset filter only.</span></span>  
  
 <span data-ttu-id="dc427-169">若要查看或更改数据集参数选项，必须编辑共享数据集定义。</span><span class="sxs-lookup"><span data-stu-id="dc427-169">To view or change dataset parameter options, you must edit the shared dataset definition.</span></span> <span data-ttu-id="dc427-170">有关详细信息，请参阅 [管理共享数据集](report-data/manage-shared-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="dc427-170">For more information, see [Manage Shared Datasets](report-data/manage-shared-datasets.md).</span></span>  
  
### <a name="report-parameters"></a><span data-ttu-id="dc427-171">报表参数</span><span class="sxs-lookup"><span data-stu-id="dc427-171">Report Parameters</span></span>  
 <span data-ttu-id="dc427-172">对于报表，在成功创建一个缓存刷新计划前，每个参数值必须是有效的。</span><span class="sxs-lookup"><span data-stu-id="dc427-172">For a report, each parameter value must be valid before you can successfully create a cache refresh plan.</span></span> <span data-ttu-id="dc427-173">必须键入或选择每个报表参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-173">You must type or select a default value for each report parameter.</span></span> <span data-ttu-id="dc427-174">您设置的值将覆盖在报表服务器上定义的报表参数默认值。</span><span class="sxs-lookup"><span data-stu-id="dc427-174">The value that you set overrides the default value that is defined for the report parameter on the report server.</span></span>  
  
 <span data-ttu-id="dc427-175">参数必须符合在报表服务器上的参数属性中指定的要求。</span><span class="sxs-lookup"><span data-stu-id="dc427-175">Parameters must conform to the requirements specified in the parameter properties on the report server.</span></span> <span data-ttu-id="dc427-176">例如，如果报表参数的属性 AllowBlank 为 false，则空字符串不是有效的值。</span><span class="sxs-lookup"><span data-stu-id="dc427-176">For example, if the property AllowBlank is false for a report parameter, an empty string is not a valid value.</span></span>  
  
 <span data-ttu-id="dc427-177">若要查看或更改报表参数选项，必须在报表中编辑报表参数，或在报表服务器上独立编辑。</span><span class="sxs-lookup"><span data-stu-id="dc427-177">To view or change report parameter options, you must edit the report parameters in the report, or independently, on the report server.</span></span> <span data-ttu-id="dc427-178">有关详细信息，请参阅[报表参数概念 &#40;报表生成器和 SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dc427-178">For more information, see [Report Parameters Concept &#40;Report Builder and SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md).</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a><span data-ttu-id="dc427-179">导致缓存刷新计划处于非活动状态的情况</span><span class="sxs-lookup"><span data-stu-id="dc427-179">Conditions that Cause a Cache Refresh Plan to be Inactive</span></span>  
 <span data-ttu-id="dc427-180">下列情况可能导致共享数据集或报表缓存刷新计划处于非活动状态。</span><span class="sxs-lookup"><span data-stu-id="dc427-180">The following conditions can cause a shared dataset or report cache refresh plan to become inactive.</span></span>  
  
-   <span data-ttu-id="dc427-181">共享数据集缓存或报表缓存选项被禁用。</span><span class="sxs-lookup"><span data-stu-id="dc427-181">The shared dataset cache or report cache option is disabled.</span></span>  
  
-   <span data-ttu-id="dc427-182">所需的参数值没有定义、无效或缺失。</span><span class="sxs-lookup"><span data-stu-id="dc427-182">The required parameter values are not defined, not valid, or missing.</span></span> <span data-ttu-id="dc427-183">在处理报表前，报表的所有查询都必须有效。</span><span class="sxs-lookup"><span data-stu-id="dc427-183">All queries for a report must be valid before the report will be processed.</span></span> <span data-ttu-id="dc427-184">对于具有子报表的报表，首先处理所有数据集查询（包括子报表的数据集）。</span><span class="sxs-lookup"><span data-stu-id="dc427-184">For a report that has subreports, all dataset queries, including datasets for the subreport, are processed first.</span></span> <span data-ttu-id="dc427-185">如果存在无法成功处理的数据集，报表将无法运行。</span><span class="sxs-lookup"><span data-stu-id="dc427-185">If any dataset cannot be successfully processed, the report cannot run.</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a><span data-ttu-id="dc427-186">导致缓存刷新计划重新激活的情况</span><span class="sxs-lookup"><span data-stu-id="dc427-186">Conditions that Cause a Cache Refresh Plan to be Reactivated</span></span>  
 <span data-ttu-id="dc427-187">计划处于非活动状态后，执行以下操作之一可以触发缓存刷新计划的评估：</span><span class="sxs-lookup"><span data-stu-id="dc427-187">After a plan is inactive, do one of the following to trigger evaluation of a cache refresh plan:</span></span>  
  
-   <span data-ttu-id="dc427-188">更改计划的选项。</span><span class="sxs-lookup"><span data-stu-id="dc427-188">Change an option for the plan.</span></span>  
  
-   <span data-ttu-id="dc427-189">启用与刷新计划关联的共享数据集或报表的缓存。</span><span class="sxs-lookup"><span data-stu-id="dc427-189">Enable caching for a shared dataset or report that is associated with the refresh plan.</span></span>  
  
-   <span data-ttu-id="dc427-190">清除或选择与刷新计划关联的数据集查询参数的只读选项，然后将新的定义保存到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="dc427-190">Clear or select the read-only option for a dataset query parameter associated with the refresh plan, and then save the new definition to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc427-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc427-191">See Also</span></span>  
 <span data-ttu-id="dc427-192">[项级任务](security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="dc427-192">[Item-Level Tasks](security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="dc427-193">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="dc427-193">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="dc427-194">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="dc427-194">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="dc427-195">[缓存报表 (SSRS)](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc427-195">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="dc427-196">管理共享数据集</span><span class="sxs-lookup"><span data-stu-id="dc427-196">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
  
