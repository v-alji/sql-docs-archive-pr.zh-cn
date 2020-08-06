---
title: 工具栏 (分区选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7225064a-4f6c-40d3-a026-34e757a966da
author: minewiskan
ms.author: owend
ms.openlocfilehash: f0d49f9fe2ca7fa54e4314cd2e412b8d9e31f126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578485"
---
# <a name="toolbar-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="34d90-102">工具栏（“分区”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="34d90-102">Toolbar (Partitions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="34d90-103">可以使用 **“工具栏”** 窗格执行多维数据集设计器的 **“分区”** 选项卡上的常规操作。</span><span class="sxs-lookup"><span data-stu-id="34d90-103">Use the **Toolbar** pane to perform common actions on the **Partitions** tab in Cube Designer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="34d90-104">选项</span><span class="sxs-lookup"><span data-stu-id="34d90-104">Options</span></span>  
  
|<span data-ttu-id="34d90-105">选项</span><span class="sxs-lookup"><span data-stu-id="34d90-105">Option</span></span>|<span data-ttu-id="34d90-106">说明</span><span class="sxs-lookup"><span data-stu-id="34d90-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34d90-107">**添加商业智能**</span><span class="sxs-lookup"><span data-stu-id="34d90-107">**Add Business Intelligence**</span></span>|<span data-ttu-id="34d90-108">单击此项可显示 **“商业智能向导”** ，并向多维数据集添加商业智能功能。</span><span class="sxs-lookup"><span data-stu-id="34d90-108">Click to display the **Business Intelligence Wizard** and add business intelligence features to the cube.</span></span>|  
|<span data-ttu-id="34d90-109">**Process**</span><span class="sxs-lookup"><span data-stu-id="34d90-109">**Process**</span></span>|<span data-ttu-id="34d90-110">单击此项可以显示 **“处理”** 对话框，以便处理所选度量值组或分区。</span><span class="sxs-lookup"><span data-stu-id="34d90-110">Click to display the **Process** dialog box and process the selected measure group or partition.</span></span>|  
|<span data-ttu-id="34d90-111">**新建分区**</span><span class="sxs-lookup"><span data-stu-id="34d90-111">**New Partition**</span></span>|<span data-ttu-id="34d90-112">单击此项可显示 **“分区向导”** ，并在所选度量值组中创建新的分区。</span><span class="sxs-lookup"><span data-stu-id="34d90-112">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>|  
|<span data-ttu-id="34d90-113">**重命名**</span><span class="sxs-lookup"><span data-stu-id="34d90-113">**Rename**</span></span>|<span data-ttu-id="34d90-114">单击此项可以重命名所选分区。</span><span class="sxs-lookup"><span data-stu-id="34d90-114">Click to rename the selected partition.</span></span><br /><br /> <span data-ttu-id="34d90-115">注意：只有在“度量值组” \*\*\*\* 窗格中，在度量值组的“分区” \*\*\*\* 网格中选择分区的任意单元时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-115">Note: This option is enabled only if any cell of a partition is selected in the **Partitions** grid of a measure group in the **Measure Groups** pane.</span></span>|  
|<span data-ttu-id="34d90-116">**删除**</span><span class="sxs-lookup"><span data-stu-id="34d90-116">**Delete**</span></span>|<span data-ttu-id="34d90-117">单击此项可显示 **“删除对象”** 对话框，并删除所选操作。</span><span class="sxs-lookup"><span data-stu-id="34d90-117">Click to display the **Delete Objects** dialog box and delete the selected action.</span></span><br /><br /> <span data-ttu-id="34d90-118">注意：只有在“度量值组” \*\*\*\* 窗格中，在度量值组的“分区” \*\*\*\* 网格中选择分区的整行时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-118">Note: This option is enabled only if the entire row of a partition is selected in the **Partitions** grid of a measure group in the **Measure Groups** pane.</span></span><br /><br /> <span data-ttu-id="34d90-119">注意：如果选择了写回分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-119">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="34d90-120">**设计聚合**</span><span class="sxs-lookup"><span data-stu-id="34d90-120">**Design Aggregations**</span></span>|<span data-ttu-id="34d90-121">单击此项可显示 **聚合设计向导** ，为所选的分区创建聚合设计。</span><span class="sxs-lookup"><span data-stu-id="34d90-121">Click to display the **Aggregation Design Wizard** and create an aggregation design for the selected partition.</span></span><br /><br /> <span data-ttu-id="34d90-122">注意：只有在“度量值组” \*\*\*\* 窗格中，在度量值组的“分区” \*\*\*\* 网格中选择分区的任意单元时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-122">Note: This option is enabled only if any cell of a partition is selected in the **Partitions** grid of a measure group in the **Measure Groups** pane.</span></span><br /><br /> <span data-ttu-id="34d90-123">注意：如果选择了写回分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-123">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="34d90-124">**基于使用情况的优化**</span><span class="sxs-lookup"><span data-stu-id="34d90-124">**Usage Based Optimization**</span></span>|<span data-ttu-id="34d90-125">单击此项可显示 **基于使用情况的优化向导** ，并基于现有使用模式为所选分区创建聚合设计。</span><span class="sxs-lookup"><span data-stu-id="34d90-125">Click to display the **Usage-Based Optimization Wizard** and create an aggregation design based on existing usage patterns for the selected partition.</span></span><br /><br /> <span data-ttu-id="34d90-126">注意：只有在“度量值组” \*\*\*\* 窗格中，在度量值组的“分区” \*\*\*\* 网格中选择分区的任意单元时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-126">Note: This option is enabled only if any cell of a partition is selected in the **Partitions** grid of a measure group in the **Measure Groups** pane.</span></span><br /><br /> <span data-ttu-id="34d90-127">另请注意，如果选择了写回分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-127">Also note that this option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="34d90-128">**存储设置**</span><span class="sxs-lookup"><span data-stu-id="34d90-128">**Storage Settings**</span></span>|<span data-ttu-id="34d90-129">单击此项可显示 **“存储设置”** 对话框，并可以为所选分区指定存储模式、主动缓存和通知设置。</span><span class="sxs-lookup"><span data-stu-id="34d90-129">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span><br /><br /> <span data-ttu-id="34d90-130">注意：只有在“度量值组” \*\*\*\* 窗格中，在度量值组的“分区” \*\*\*\* 网格中选择分区的任意单元时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="34d90-130">Note: This option is enabled only if any cell of a partition is selected in the **Partitions** grid of a measure group in the **Measure Groups** pane.</span></span>|  
  
  
