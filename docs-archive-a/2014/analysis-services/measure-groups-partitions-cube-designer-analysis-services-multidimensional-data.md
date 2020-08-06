---
title: 度量值组 (分区选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionspane.measuregroupdetail.f1
ms.assetid: 58e44b24-cfcd-4908-b445-d4374b961b98
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b73b77bd62c38881be20450f0b7506917014461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693572"
---
# <a name="measure-groups-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="8599a-102">度量值组（“分区”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="8599a-102">Measure Groups (Partitions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8599a-103">可以使用多维数据集设计器中的 **“分区”** 选项卡上的 **“度量值组”** 窗格，管理与多维数据集中的各个度量值组关联的分区。</span><span class="sxs-lookup"><span data-stu-id="8599a-103">Use the **Measure Groups** pane on the **Partitions** tab in Cube Designer to manage the partitions associated with each measure group in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8599a-104">选项</span><span class="sxs-lookup"><span data-stu-id="8599a-104">Options</span></span>  
 <span data-ttu-id="8599a-105">**分区**</span><span class="sxs-lookup"><span data-stu-id="8599a-105">**Partitions**</span></span>  
 <span data-ttu-id="8599a-106">显示包含支持所选度量值组的一系列分区的网格。</span><span class="sxs-lookup"><span data-stu-id="8599a-106">Displays a grid containing the list of partitions that support the selected measure group.</span></span> <span data-ttu-id="8599a-107">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="8599a-107">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="8599a-108">**序号)  (**</span><span class="sxs-lookup"><span data-stu-id="8599a-108">**(Ordinal)**</span></span>  
 <span data-ttu-id="8599a-109">显示分区在度量值组中的序号位置。</span><span class="sxs-lookup"><span data-stu-id="8599a-109">Displays the ordinal position of the partition within the measure group.</span></span>  
  
 <span data-ttu-id="8599a-110">单击此项可以选择分区的整行。</span><span class="sxs-lookup"><span data-stu-id="8599a-110">Click to select the entire row for the partition.</span></span>  
  
 <span data-ttu-id="8599a-111">**分区名称**</span><span class="sxs-lookup"><span data-stu-id="8599a-111">**Partition Name**</span></span>  
 <span data-ttu-id="8599a-112">键入所选分区的名称。</span><span class="sxs-lookup"><span data-stu-id="8599a-112">Type the name of the selected partition.</span></span>  
  
 <span data-ttu-id="8599a-113">**数据源**</span><span class="sxs-lookup"><span data-stu-id="8599a-113">**Source**</span></span>  
 <span data-ttu-id="8599a-114">键入为所选分区提供事实数据表数据的表名称（对于表绑定）或查询（对于查询绑定）。</span><span class="sxs-lookup"><span data-stu-id="8599a-114">Type the table name (for table binding) or query (for query binding) that provides the fact table data for the selected partition.</span></span>  
  
 <span data-ttu-id="8599a-115">单击 **...** 按钮可以显示 **“分区源”** 对话框并定义所选分区的源。</span><span class="sxs-lookup"><span data-stu-id="8599a-115">Click the **...** button to display the **Partition Source** dialog box and define the source for the selected partition.</span></span>  
  
 <span data-ttu-id="8599a-116">**聚合**</span><span class="sxs-lookup"><span data-stu-id="8599a-116">**Aggregation**</span></span>  
 <span data-ttu-id="8599a-117">显示分区的聚合模式和存储模式。</span><span class="sxs-lookup"><span data-stu-id="8599a-117">Displays the aggregation mode and the storage mode of the partition.</span></span> <span data-ttu-id="8599a-118">首先显示存储模式：关系联机分析处理 (ROLAP)、多维联机分析处理 (MOLAP) 或混合联机分析处理 (HOLAP)。</span><span class="sxs-lookup"><span data-stu-id="8599a-118">The storage mode is displayed first: relational online analytical processing (ROLAP), multidimensional online analytical processing (MOLAP), or hybrid online analytical processing (HOLAP).</span></span> <span data-ttu-id="8599a-119">聚合模式显示为：所请求的优化百分比、所请求或使用空间的度量值或所创建聚合的数目。</span><span class="sxs-lookup"><span data-stu-id="8599a-119">The aggregation mode is displayed as a percentage of optimization requested, as a measure of space requested or used, or as the number of aggregations created.</span></span> <span data-ttu-id="8599a-120">单击 **...** 按钮可以显示 **聚合设计向导** 并定义指定分区的聚合设计。</span><span class="sxs-lookup"><span data-stu-id="8599a-120">Click the **...** button to display the **Aggregation Design Wizard** and define the aggregation design for the specified partition.</span></span>  
  
 <span data-ttu-id="8599a-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="8599a-121">**Description**</span></span>  
 <span data-ttu-id="8599a-122">键入分区的可选说明。</span><span class="sxs-lookup"><span data-stu-id="8599a-122">Type the optional description of the partition.</span></span>  
  
 <span data-ttu-id="8599a-123">**新建分区...**</span><span class="sxs-lookup"><span data-stu-id="8599a-123">**New Partition...**</span></span>  
 <span data-ttu-id="8599a-124">单击此项可显示 **“分区向导”** ，并在所选度量值组中创建新的分区。</span><span class="sxs-lookup"><span data-stu-id="8599a-124">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>  
  
 <span data-ttu-id="8599a-125">**存储设置 .。。**</span><span class="sxs-lookup"><span data-stu-id="8599a-125">**Storage settings...**</span></span>  
 <span data-ttu-id="8599a-126">单击此项可显示 **“存储设置”** 对话框，并可以为所选分区指定存储模式、主动缓存和通知设置。</span><span class="sxs-lookup"><span data-stu-id="8599a-126">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8599a-127">只有在所选度量值组的“分区”\*\*\*\* 网格中选择某分区单元时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="8599a-127">This option is enabled only if any cell of a partition is selected in the **Partitions** grid of the selected measure group.</span></span>  
  
 <span data-ttu-id="8599a-128">**写回设置...**</span><span class="sxs-lookup"><span data-stu-id="8599a-128">**Writeback settings...**</span></span>  
 <span data-ttu-id="8599a-129">单击此项可以显示“启用/禁用写回”\*\*\*\* 对话框，以便指定所选度量值组的写回设置。</span><span class="sxs-lookup"><span data-stu-id="8599a-129">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the selected measure group.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="8599a-130">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="8599a-130">Context Menu</span></span>  
 <span data-ttu-id="8599a-131">右键单击所选度量值组的“分区”\*\*\*\* 网格中的行之后，所显示的上下文菜单中提供有以下选项：</span><span class="sxs-lookup"><span data-stu-id="8599a-131">The following options are available in the context menu displayed by right-clicking a row in the **Partitions** grid of a selected measure group:</span></span>  
  
|<span data-ttu-id="8599a-132">选项</span><span class="sxs-lookup"><span data-stu-id="8599a-132">Option</span></span>|<span data-ttu-id="8599a-133">定义</span><span class="sxs-lookup"><span data-stu-id="8599a-133">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="8599a-134">**添加商业智能**</span><span class="sxs-lookup"><span data-stu-id="8599a-134">**Add Business Intelligence**</span></span>|<span data-ttu-id="8599a-135">单击此项可显示 **“商业智能向导”** ，并向多维数据集添加商业智能功能。</span><span class="sxs-lookup"><span data-stu-id="8599a-135">Click to display the **Business Intelligence Wizard** and add business intelligence features to the cube.</span></span> <span data-ttu-id="8599a-136">有关“商业智能向导”\*\*\*\* 的详细信息，请参阅[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="8599a-136">For more information about the **Business Intelligence Wizard**, see [Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="8599a-137">**新建分区**</span><span class="sxs-lookup"><span data-stu-id="8599a-137">**New Partition**</span></span>|<span data-ttu-id="8599a-138">单击此项可显示 **“分区向导”** ，并在所选度量值组中创建新的分区。</span><span class="sxs-lookup"><span data-stu-id="8599a-138">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>|  
|<span data-ttu-id="8599a-139">**重命名分区**</span><span class="sxs-lookup"><span data-stu-id="8599a-139">**Rename Partition**</span></span>|<span data-ttu-id="8599a-140">选择此项可以重命名所选分区。</span><span class="sxs-lookup"><span data-stu-id="8599a-140">Select to rename the selected partition.</span></span>|  
|<span data-ttu-id="8599a-141">**删除**</span><span class="sxs-lookup"><span data-stu-id="8599a-141">**Delete**</span></span>|<span data-ttu-id="8599a-142">单击此项可显示 **“删除对象”** 对话框，并删除所选操作。</span><span class="sxs-lookup"><span data-stu-id="8599a-142">Click to display the **Delete Objects** dialog box and delete the selected action.</span></span><br /><br /> <span data-ttu-id="8599a-143">注意：如果选择了写回分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="8599a-143">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="8599a-144">**设计聚合**</span><span class="sxs-lookup"><span data-stu-id="8599a-144">**Design Aggregations**</span></span>|<span data-ttu-id="8599a-145">单击此项可显示 **聚合设计向导** ，为所选的分区创建聚合设计。</span><span class="sxs-lookup"><span data-stu-id="8599a-145">Click to display the **Aggregation Design Wizard** and create an aggregation design for the selected partition.</span></span><br /><br /> <span data-ttu-id="8599a-146">注意：如果选择了写回分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="8599a-146">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="8599a-147">**存储设置**</span><span class="sxs-lookup"><span data-stu-id="8599a-147">**Storage Settings**</span></span>|<span data-ttu-id="8599a-148">单击此项可显示 **“存储设置”** 对话框，并可以为所选分区指定存储模式、主动缓存和通知设置。</span><span class="sxs-lookup"><span data-stu-id="8599a-148">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>|  
|<span data-ttu-id="8599a-149">**写回设置**</span><span class="sxs-lookup"><span data-stu-id="8599a-149">**Writeback Settings**</span></span>|<span data-ttu-id="8599a-150">单击此项可以显示“启用/禁用写回”\*\*\*\* 对话框，以便指定包含所选分区的度量值组的写回设置。</span><span class="sxs-lookup"><span data-stu-id="8599a-150">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the measure group containing the selected partition.</span></span>|  
|<span data-ttu-id="8599a-151">**基于使用情况的优化**</span><span class="sxs-lookup"><span data-stu-id="8599a-151">**Usage Based Optimization**</span></span>|<span data-ttu-id="8599a-152">单击此项可显示 **基于使用情况的优化向导** ，并基于现有使用模式为所选分区创建聚合设计。</span><span class="sxs-lookup"><span data-stu-id="8599a-152">Click to display the **Usage-Based Optimization Wizard** and create an aggregation design based on existing usage patterns for the selected partition.</span></span><br /><br /> <span data-ttu-id="8599a-153">注意：如果选择了写回分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="8599a-153">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="8599a-154">**Process**</span><span class="sxs-lookup"><span data-stu-id="8599a-154">**Process**</span></span>|<span data-ttu-id="8599a-155">单击此项可以显示 **“处理”** 对话框，以便处理所选分区。</span><span class="sxs-lookup"><span data-stu-id="8599a-155">Click to display the **Process** dialog box and process the selected partition.</span></span>|  
|<span data-ttu-id="8599a-156">**复制**</span><span class="sxs-lookup"><span data-stu-id="8599a-156">**Copy**</span></span>|<span data-ttu-id="8599a-157">此选项已禁用。</span><span class="sxs-lookup"><span data-stu-id="8599a-157">This option is disabled.</span></span>|  
|<span data-ttu-id="8599a-158">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="8599a-158">**Paste**</span></span>|<span data-ttu-id="8599a-159">此选项已禁用。</span><span class="sxs-lookup"><span data-stu-id="8599a-159">This option is disabled.</span></span>|  
|<span data-ttu-id="8599a-160">**属性**</span><span class="sxs-lookup"><span data-stu-id="8599a-160">**Properties**</span></span>|<span data-ttu-id="8599a-161">选择此项可以在 **中显示所选分区的** “属性” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 窗口。</span><span class="sxs-lookup"><span data-stu-id="8599a-161">Select to display the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected partition.</span></span>|  
  
  
