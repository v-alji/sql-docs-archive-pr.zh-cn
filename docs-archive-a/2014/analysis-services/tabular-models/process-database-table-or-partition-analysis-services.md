---
title: 处理数据库、表或分区 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
ms.openlocfilehash: b5d3840be43798536f1bb517007a7974a1e08728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683092"
---
# <a name="process-database-table-or-partition"></a><span data-ttu-id="e2090-102">处理数据库、表或分区</span><span class="sxs-lookup"><span data-stu-id="e2090-102">Process Database, Table, or Partition</span></span>
  <span data-ttu-id="e2090-103">本主题中的任务说明如何使用中的 "\*\*处理 \<object> \*\* " 对话框手动处理表格模型数据库、表或分区 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2090-103">The tasks in this topic describe how to process a tabular model database, table, or partitions manually by using the **Process \<object>** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e2090-104">有关表格模型处理的详细信息，请参阅[处理数据（SSAS 表格）](../process-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="e2090-104">For more information about tabular model processing, see [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
##  <a name="tasks"></a><a name="bkmk_process_tasks"></a><span data-ttu-id="e2090-105">任务</span><span class="sxs-lookup"><span data-stu-id="e2090-105">Tasks</span></span>  
  
###  <a name="to-process-a-database"></a><a name="bkmk_process_db"></a><span data-ttu-id="e2090-106">处理数据库</span><span class="sxs-lookup"><span data-stu-id="e2090-106">To process a database</span></span>  
  
1.  <span data-ttu-id="e2090-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击要处理的数据库，然后单击“处理数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e2090-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the database you want to process, and then click **Process Database**.</span></span>  
  
2.  <span data-ttu-id="e2090-108">在 **“处理数据库”** 对话框的 **“模式”** 列表框中，选择下列处理模式之一：</span><span class="sxs-lookup"><span data-stu-id="e2090-108">In the **Process Database** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="e2090-109">“模式”</span><span class="sxs-lookup"><span data-stu-id="e2090-109">Mode</span></span>|<span data-ttu-id="e2090-110">说明</span><span class="sxs-lookup"><span data-stu-id="e2090-110">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="e2090-111">**处理默认值**</span><span class="sxs-lookup"><span data-stu-id="e2090-111">**Process Default**</span></span>|<span data-ttu-id="e2090-112">检测数据库对象的处理状态，进行必要的处理，将未处理对象或部分处理的对象转变成为已完全处理的对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-112">Detects the process state of database objects, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="e2090-113">为空表和分区加载数据；生成或重新生成（重新计算）层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="e2090-113">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="e2090-114">**处理全部**</span><span class="sxs-lookup"><span data-stu-id="e2090-114">**Process Full**</span></span>|<span data-ttu-id="e2090-115">处理数据库及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-115">Processes a database and all the objects that it contains.</span></span> <span data-ttu-id="e2090-116">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-116">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="e2090-117">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="e2090-117">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="e2090-118">此选项需要的资源最多。</span><span class="sxs-lookup"><span data-stu-id="e2090-118">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="e2090-119">**处理清除**</span><span class="sxs-lookup"><span data-stu-id="e2090-119">**Process Clear**</span></span>|<span data-ttu-id="e2090-120">从数据库对象中删除所有数据。</span><span class="sxs-lookup"><span data-stu-id="e2090-120">Removes all data from database objects.</span></span>|  
    |<span data-ttu-id="e2090-121">**处理重新计算**</span><span class="sxs-lookup"><span data-stu-id="e2090-121">**Process Recalc**</span></span>|<span data-ttu-id="e2090-122">更新并重新计算层次结构、关系和计算列。</span><span class="sxs-lookup"><span data-stu-id="e2090-122">Updates and recalculates hierarchies, relationships, and calculated columns.</span></span>|  
  
3.  <span data-ttu-id="e2090-123">在 **“处理”** 复选框列中，选择要用所选模式处理的分区，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e2090-123">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
###  <a name="to-process-a-table"></a><a name="bkmk_process_table"></a><span data-ttu-id="e2090-124">处理表</span><span class="sxs-lookup"><span data-stu-id="e2090-124">To process a table</span></span>  
  
1.  <span data-ttu-id="e2090-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，在包含要处理的表的表格模型数据库中，展开“表”\*\*\*\* 节点，再右键单击要处理的表，然后单击“处理表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e2090-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in the tabular model database which contains the table you want to process, expand the **Tables** node, then right-click on the table you want to process, and then click **Process Table**.</span></span>  
  
2.  <span data-ttu-id="e2090-126">在 **“处理表”** 对话框的 **“模式”** 列表框中，选择下列处理模式之一：</span><span class="sxs-lookup"><span data-stu-id="e2090-126">In the **Process Table** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="e2090-127">“模式”</span><span class="sxs-lookup"><span data-stu-id="e2090-127">Mode</span></span>|<span data-ttu-id="e2090-128">说明</span><span class="sxs-lookup"><span data-stu-id="e2090-128">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="e2090-129">**处理默认值**</span><span class="sxs-lookup"><span data-stu-id="e2090-129">**Process Default**</span></span>|<span data-ttu-id="e2090-130">检测表对象的处理状态，进行必要的处理，将未处理对象或部分处理的对象转变成为已完全处理的对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-130">Detects the process state of a table object, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="e2090-131">为空表和分区加载数据；生成或重新生成（重新计算）层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="e2090-131">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="e2090-132">**处理全部**</span><span class="sxs-lookup"><span data-stu-id="e2090-132">**Process Full**</span></span>|<span data-ttu-id="e2090-133">处理表对象及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-133">Processes a table object and all the objects that it contains.</span></span> <span data-ttu-id="e2090-134">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-134">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="e2090-135">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="e2090-135">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="e2090-136">此选项需要的资源最多。</span><span class="sxs-lookup"><span data-stu-id="e2090-136">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="e2090-137">**处理数据**</span><span class="sxs-lookup"><span data-stu-id="e2090-137">**Process Data**</span></span>|<span data-ttu-id="e2090-138">将数据加载到表中，而无需重新生成层次结构或关系或重新计算计算列和度量值。</span><span class="sxs-lookup"><span data-stu-id="e2090-138">Load data into a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="e2090-139">**处理清除**</span><span class="sxs-lookup"><span data-stu-id="e2090-139">**Process Clear**</span></span>|<span data-ttu-id="e2090-140">从表和所有表分区中删除所有数据。</span><span class="sxs-lookup"><span data-stu-id="e2090-140">Removes all data from a table and any table partitions.</span></span>|  
    |<span data-ttu-id="e2090-141">**处理碎片整理**</span><span class="sxs-lookup"><span data-stu-id="e2090-141">**Process Defrag**</span></span>|<span data-ttu-id="e2090-142">对辅助表索引进行碎片整理。</span><span class="sxs-lookup"><span data-stu-id="e2090-142">Defragments the auxiliary table indexes.</span></span>|  
  
3.  <span data-ttu-id="e2090-143">在表复选框列中，确认表并（可选）选择要处理的任何其他表，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e2090-143">In the table checkbox column, verify the table and optionally select any additional tables you want to process, and then click **Ok**.</span></span>  
  
###  <a name="to-process-one-or-more-partitions"></a><a name="bkmk_process_partition"></a><span data-ttu-id="e2090-144">处理一个或多个分区</span><span class="sxs-lookup"><span data-stu-id="e2090-144">To process one or more partitions</span></span>  
  
1.  <span data-ttu-id="e2090-145">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击包含要处理的分区的表，然后单击“分区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e2090-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="e2090-146">在 **“分区”** 对话框的 **“分区”** 中，单击“处理”按钮。</span><span class="sxs-lookup"><span data-stu-id="e2090-146">In the **Partitions** dialog box, in **Partitions**, click the Process button.</span></span>  
  
3.  <span data-ttu-id="e2090-147">在 **“处理分区”** 对话框的 **“模式”** 列表框中，选择下列处理模式之一：</span><span class="sxs-lookup"><span data-stu-id="e2090-147">In the **Process Partition** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="e2090-148">“模式”</span><span class="sxs-lookup"><span data-stu-id="e2090-148">Mode</span></span>|<span data-ttu-id="e2090-149">说明</span><span class="sxs-lookup"><span data-stu-id="e2090-149">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="e2090-150">**处理默认值**</span><span class="sxs-lookup"><span data-stu-id="e2090-150">**Process Default**</span></span>|<span data-ttu-id="e2090-151">检测分区对象的处理状态，执行必要的处理，将未处理的分区对象或部分处理的分区对象交付为已完全处理的分区对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-151">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="e2090-152">为空表和分区加载数据；生成或重新生成（重新计算）层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="e2090-152">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="e2090-153">**处理全部**</span><span class="sxs-lookup"><span data-stu-id="e2090-153">**Process Full**</span></span>|<span data-ttu-id="e2090-154">处理分区对象及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-154">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="e2090-155">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="e2090-155">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="e2090-156">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="e2090-156">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="e2090-157">**处理数据**</span><span class="sxs-lookup"><span data-stu-id="e2090-157">**Process Data**</span></span>|<span data-ttu-id="e2090-158">将数据加载到分区或表中，而无需重新生成层次结构或关系或重新计算计算列和度量值。</span><span class="sxs-lookup"><span data-stu-id="e2090-158">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="e2090-159">**处理清除**</span><span class="sxs-lookup"><span data-stu-id="e2090-159">**Process Clear**</span></span>|<span data-ttu-id="e2090-160">删除分区中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="e2090-160">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="e2090-161">**处理添加**</span><span class="sxs-lookup"><span data-stu-id="e2090-161">**Process Add**</span></span>|<span data-ttu-id="e2090-162">以增量方式用新数据更新分区。</span><span class="sxs-lookup"><span data-stu-id="e2090-162">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="e2090-163">在 **“处理”** 复选框列中，选择要用所选模式处理的分区，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e2090-163">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2090-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2090-164">See Also</span></span>  
 <span data-ttu-id="e2090-165">[&#40;SSAS 表格&#41;的表格模型分区](tabular-model-partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="e2090-165">[Tabular Model Partitions &#40;SSAS Tabular&#41;](tabular-model-partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="e2090-166">创建和管理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="e2090-166">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
