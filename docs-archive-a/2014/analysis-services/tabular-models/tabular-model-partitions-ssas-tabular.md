---
title: " (SSAS 表格) 的表格模型分区 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.partitions.partitionmgr.imbi.f1
ms.assetid: 041c269f-a229-4a41-8794-6ba4b014ef83
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58712523c3a47bffa7db9d5b32b62f8bef15166c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692546"
---
# <a name="tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="ebe50-102">表格模型分区 (SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ebe50-102">Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="ebe50-103">分区将表分成多个逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="ebe50-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="ebe50-104">然后，每个分区可独立于其他分区进行处理（刷新）。</span><span class="sxs-lookup"><span data-stu-id="ebe50-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="ebe50-105">在已部署的模型中将重复在模型创作过程中为模型定义的分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-105">Partitions defined for a model during model authoring are duplicated in a deployed model.</span></span> <span data-ttu-id="ebe50-106">部署完成后，您可以通过使用 **中的** “分区” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对话框或使用脚本来管理这些分区和创建新分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-106">Once deployed, you can manage those partitions and create new partitions by using the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by using a script.</span></span> <span data-ttu-id="ebe50-107">本主题提供的信息描述已部署的表格模型数据库中的分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-107">Information provided in this topic describes partitions in a deployed tabular model database.</span></span> <span data-ttu-id="ebe50-108">有关模型创作期间创建和管理分区的详细信息，请参阅[分区（SSAS 表格）](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe50-108">For more information about creating and managing partitions during model authoring, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="ebe50-109">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="ebe50-109">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="ebe50-110">优点</span><span class="sxs-lookup"><span data-stu-id="ebe50-110">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="ebe50-111">权限</span><span class="sxs-lookup"><span data-stu-id="ebe50-111">Permissions</span></span>](#bkmk_permissions)  
  
-   [<span data-ttu-id="ebe50-112">处理分区</span><span class="sxs-lookup"><span data-stu-id="ebe50-112">Process Partitions</span></span>](#bkmk_process_partitions)  
  
-   [<span data-ttu-id="ebe50-113">相关任务</span><span class="sxs-lookup"><span data-stu-id="ebe50-113">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="ebe50-114">优势</span><span class="sxs-lookup"><span data-stu-id="ebe50-114">Benefits</span></span>  
 <span data-ttu-id="ebe50-115">有效的模型设计利用分区来消除 Analysis Services 服务器上不必要的处理和后续处理器负载，而同时可确保以足够的频率处理和刷新数据，以反映数据源中最新的数据。</span><span class="sxs-lookup"><span data-stu-id="ebe50-115">Effective model design utilizes partitions to eliminate unnecessary processing and subsequent processor load on Analysis Services servers, while at the same time, making certain that data is processed and refreshed often enough to reflect the most recent data from data sources.</span></span>  
  
 <span data-ttu-id="ebe50-116">例如，表格模型可具有一个 Sales 表，该表包含当前 2011 会计年度和之前每一个会计年度的销售数据。</span><span class="sxs-lookup"><span data-stu-id="ebe50-116">For example, a tabular model can have a Sales table which includes sales data for the current 2011 fiscal year and each of the previous fiscal years.</span></span> <span data-ttu-id="ebe50-117">模型的 Sales 表具有以下三个分区：</span><span class="sxs-lookup"><span data-stu-id="ebe50-117">The model's Sales table has the following three partitions:</span></span>  
  
|<span data-ttu-id="ebe50-118">分区</span><span class="sxs-lookup"><span data-stu-id="ebe50-118">Partition</span></span>|<span data-ttu-id="ebe50-119">数据来源</span><span class="sxs-lookup"><span data-stu-id="ebe50-119">Data from</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="ebe50-120">Sales2011</span><span class="sxs-lookup"><span data-stu-id="ebe50-120">Sales2011</span></span>|<span data-ttu-id="ebe50-121">当前会计年度</span><span class="sxs-lookup"><span data-stu-id="ebe50-121">Current fiscal year</span></span>|  
|<span data-ttu-id="ebe50-122">Sales2010-2001</span><span class="sxs-lookup"><span data-stu-id="ebe50-122">Sales2010-2001</span></span>|<span data-ttu-id="ebe50-123">会计年度 2001、2002、2003、2004、2005、2006。</span><span class="sxs-lookup"><span data-stu-id="ebe50-123">Fiscal years 2001, 2002, 2003, 2004, 2005, 2006.</span></span> <span data-ttu-id="ebe50-124">2007, 2008, 2009, 2010</span><span class="sxs-lookup"><span data-stu-id="ebe50-124">2007, 2008, 2009, 2010</span></span>|  
|<span data-ttu-id="ebe50-125">SalesOld</span><span class="sxs-lookup"><span data-stu-id="ebe50-125">SalesOld</span></span>|<span data-ttu-id="ebe50-126">过去十年之前的所有会计年度。</span><span class="sxs-lookup"><span data-stu-id="ebe50-126">All fiscal years prior to the last ten years.</span></span>|  
  
 <span data-ttu-id="ebe50-127">当为当前 2011 会计年度添加新的销售数据时；该数据必须每天进行处理，以便在当前会计年度销售数据分析中准确得以反映，这样，将每晚处理 Sales2011 分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-127">As new sales data is added for the current 2011 fiscal year; that data must be processed daily to accurately be reflected in current fiscal year sales data analysis, thus the Sales2011 partition is processed nightly.</span></span>  
  
 <span data-ttu-id="ebe50-128">无需每晚处理 Sales2010-2001 分区中的数据；但是，因为之前十个会计年度的销售数据仍偶尔会因为产品退货和其他调整而发生更改，所以还必须定期进行处理，这样，将每月处理 Sales2010-2001 分区中的数据。</span><span class="sxs-lookup"><span data-stu-id="ebe50-128">There is no need to process data in the Sales2010-2001 partition nightly; however, because sales data for the previous ten fiscal years can still occasionally change because of product returns and other adjustments, it must still be processed regularly, thus data in the Sales2010-2001 partition is processed monthly.</span></span> <span data-ttu-id="ebe50-129">SalesOld 分区中的数据从不会发生变化，因此只是每年处理一次。</span><span class="sxs-lookup"><span data-stu-id="ebe50-129">Data in the SalesOld partition never changes therefore only processed annually.</span></span>  
  
 <span data-ttu-id="ebe50-130">输入2012会计年度时，新的 Sales2012 分区将添加到该模式的 Sales 表。</span><span class="sxs-lookup"><span data-stu-id="ebe50-130">When entering the 2012 fiscal year, a new Sales2012 partition is added to the mode's Sales table.</span></span> <span data-ttu-id="ebe50-131">然后，Sales2011 分区可以与 Sales2010-2001 分区合并，并重命名为 Sales2011-2002。</span><span class="sxs-lookup"><span data-stu-id="ebe50-131">The Sales2011 partition can then be merged with the Sales2010-2001 partition and renamed to Sales2011-2002.</span></span> <span data-ttu-id="ebe50-132">从新的 Sales2011-2002 分区中删除 2001 会计年度中的数据，并移入到 SalesOld 分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-132">Data from the 2001 fiscal year is eliminated from the new Sales2011-2002 partition and moved into the SalesOld partition.</span></span> <span data-ttu-id="ebe50-133">然后，处理所有分区以反映数据更改。</span><span class="sxs-lookup"><span data-stu-id="ebe50-133">All partitions are then processed to reflect changes.</span></span>  
  
 <span data-ttu-id="ebe50-134">如何实现组织的表格模型的分区策略在很大程度上取决于特定模型数据处理需求和可用资源。</span><span class="sxs-lookup"><span data-stu-id="ebe50-134">How you implement a partition strategy for your organization's tabular models will largely be dependent on your particular model data processing needs and available resources.</span></span>  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> <span data-ttu-id="ebe50-135">权限</span><span class="sxs-lookup"><span data-stu-id="ebe50-135">Permissions</span></span>  
 <span data-ttu-id="ebe50-136">为了在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中创建、管理和处理分区，您必须具有在安全角色中定义的适当的 Analysis Services 权限。</span><span class="sxs-lookup"><span data-stu-id="ebe50-136">In order to create, manage, and process partitions in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must have the appropriate Analysis Services permissions defined in a security role.</span></span> <span data-ttu-id="ebe50-137">每个安全角色都具有以下权限之一：</span><span class="sxs-lookup"><span data-stu-id="ebe50-137">Each security role has one of the following permissions:</span></span>  
  
|<span data-ttu-id="ebe50-138">权限</span><span class="sxs-lookup"><span data-stu-id="ebe50-138">Permission</span></span>|<span data-ttu-id="ebe50-139">操作</span><span class="sxs-lookup"><span data-stu-id="ebe50-139">Actions</span></span>|  
|----------------|-------------|  
|<span data-ttu-id="ebe50-140">管理员</span><span class="sxs-lookup"><span data-stu-id="ebe50-140">Administrator</span></span>|<span data-ttu-id="ebe50-141">读取、处理、创建、复制、合并、删除</span><span class="sxs-lookup"><span data-stu-id="ebe50-141">Read, process, create, copy, merge, delete</span></span>|  
|<span data-ttu-id="ebe50-142">进程</span><span class="sxs-lookup"><span data-stu-id="ebe50-142">Process</span></span>|<span data-ttu-id="ebe50-143">读取、处理</span><span class="sxs-lookup"><span data-stu-id="ebe50-143">Read, process</span></span>|  
|<span data-ttu-id="ebe50-144">只读</span><span class="sxs-lookup"><span data-stu-id="ebe50-144">Read Only</span></span>|<span data-ttu-id="ebe50-145">读取</span><span class="sxs-lookup"><span data-stu-id="ebe50-145">Read</span></span>|  
  
 <span data-ttu-id="ebe50-146">若要了解有关使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 在模型创作期间创建角色的详细信息，请参阅[角色（SSAS 表格）](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe50-146">To learn more about creating roles during model authoring by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span> <span data-ttu-id="ebe50-147">若要了解有关使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 管理已部署表格模型角色的角色成员的详细信息，请参阅[表格模型角色（SSAS 表格）](tabular-model-roles-ssas-tabular.md)</span><span class="sxs-lookup"><span data-stu-id="ebe50-147">To learn more about managing role members for deployed tabular model roles by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Tabular Model Roles &#40;SSAS Tabular&#41;](tabular-model-roles-ssas-tabular.md).</span></span>  
  
##  <a name="process-partitions"></a><a name="bkmk_process_partitions"></a><span data-ttu-id="ebe50-148">处理分区</span><span class="sxs-lookup"><span data-stu-id="ebe50-148">Process Partitions</span></span>  
 <span data-ttu-id="ebe50-149">可以通过使用 **中的** “分区” [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 对话框或使用脚本独立于其他分区处理（刷新）分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-149">Partitions can be processed (refreshed) independent of other partitions by using the **Partitions** dialog box in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or by using a script.</span></span> <span data-ttu-id="ebe50-150">处理具有以下选项：</span><span class="sxs-lookup"><span data-stu-id="ebe50-150">Processing has the following options:</span></span>  
  
|<span data-ttu-id="ebe50-151">“模式”</span><span class="sxs-lookup"><span data-stu-id="ebe50-151">Mode</span></span>|<span data-ttu-id="ebe50-152">说明</span><span class="sxs-lookup"><span data-stu-id="ebe50-152">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ebe50-153">处理默认值</span><span class="sxs-lookup"><span data-stu-id="ebe50-153">Process Default</span></span>|<span data-ttu-id="ebe50-154">检测分区对象的处理状态，执行必要的处理，将未处理的分区对象或部分处理的分区对象交付为已完全处理的分区对象。</span><span class="sxs-lookup"><span data-stu-id="ebe50-154">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="ebe50-155">为空表和分区加载数据；生成或重新生成层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="ebe50-155">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
|<span data-ttu-id="ebe50-156">处理全部</span><span class="sxs-lookup"><span data-stu-id="ebe50-156">Process Full</span></span>|<span data-ttu-id="ebe50-157">处理分区对象及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="ebe50-157">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="ebe50-158">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="ebe50-158">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="ebe50-159">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="ebe50-159">This kind of processing is required when a structural change has been made to an object.</span></span>|  
|<span data-ttu-id="ebe50-160">处理数据</span><span class="sxs-lookup"><span data-stu-id="ebe50-160">Process Data</span></span>|<span data-ttu-id="ebe50-161">将数据加载到分区或表中，而无需重新生成层次结构或关系或重新计算计算列和度量值。</span><span class="sxs-lookup"><span data-stu-id="ebe50-161">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
|<span data-ttu-id="ebe50-162">处理清除</span><span class="sxs-lookup"><span data-stu-id="ebe50-162">Process Clear</span></span>|<span data-ttu-id="ebe50-163">删除分区中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="ebe50-163">Removes all data from a partition.</span></span>|  
|<span data-ttu-id="ebe50-164">处理添加</span><span class="sxs-lookup"><span data-stu-id="ebe50-164">Process Add</span></span>|<span data-ttu-id="ebe50-165">以增量方式用新数据更新分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-165">Incrementally update partition with new data.</span></span>|  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="ebe50-166">相关任务</span><span class="sxs-lookup"><span data-stu-id="ebe50-166">Related Tasks</span></span>  
  
|<span data-ttu-id="ebe50-167">任务</span><span class="sxs-lookup"><span data-stu-id="ebe50-167">Task</span></span>|<span data-ttu-id="ebe50-168">说明</span><span class="sxs-lookup"><span data-stu-id="ebe50-168">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="ebe50-169">创建和管理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ebe50-169">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)|<span data-ttu-id="ebe50-170">描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]在已部署的表格模型中创建和管理分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-170">Describes how to create and manage partitions in a deployed tabular model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|  
|[<span data-ttu-id="ebe50-171">处理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ebe50-171">Process Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](process-tabular-model-partitions-ssas-tabular.md)|<span data-ttu-id="ebe50-172">描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]在已部署的表格模型中处理分区。</span><span class="sxs-lookup"><span data-stu-id="ebe50-172">Describes how to process partitions in a deployed tabular model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|  
  
  
