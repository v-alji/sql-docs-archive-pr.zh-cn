---
title: " (SSAS 表格) 处理表格模型分区 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 496874707bd4030a98b1794fe7513d1d857390ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683087"
---
# <a name="process-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="a9ca3-102">处理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="a9ca3-102">Process Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="a9ca3-103">分区将表分成多个逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="a9ca3-104">然后，每个分区可独立于其他分区进行处理（刷新）。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="a9ca3-105">本主题中的任务说明如何使用 **中的** “处理分区” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]对话框在模型数据库中处理分区。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-105">The tasks in this topic describe how to process partitions in a model database by using the **Process Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="a9ca3-106">处理分区</span><span class="sxs-lookup"><span data-stu-id="a9ca3-106">To process a partition</span></span>  
  
1.  <span data-ttu-id="a9ca3-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击包含要处理的分区的表，然后单击“分区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="a9ca3-108">在 **“分区”** 对话框的 **“分区”** 中，单击“处理”按钮。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-108">In the **Partitions** dialog box, in **Partitions**, click on the Process button.</span></span>  
  
3.  <span data-ttu-id="a9ca3-109">在 "**处理分区 (s) \*\* " 对话框的 "**模式\*\*" 列表框中，选择以下处理模式之一：</span><span class="sxs-lookup"><span data-stu-id="a9ca3-109">In the **Process Partition(s)** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="a9ca3-110">“模式”</span><span class="sxs-lookup"><span data-stu-id="a9ca3-110">Mode</span></span>|<span data-ttu-id="a9ca3-111">说明</span><span class="sxs-lookup"><span data-stu-id="a9ca3-111">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="a9ca3-112">**处理默认值**</span><span class="sxs-lookup"><span data-stu-id="a9ca3-112">**Process Default**</span></span>|<span data-ttu-id="a9ca3-113">检测分区对象的处理状态，执行必要的处理，将未处理的分区对象或部分处理的分区对象交付为已完全处理的分区对象。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-113">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="a9ca3-114">为空表和分区加载数据；生成或重新生成层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-114">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="a9ca3-115">**处理全部**</span><span class="sxs-lookup"><span data-stu-id="a9ca3-115">**Process Full**</span></span>|<span data-ttu-id="a9ca3-116">处理分区对象及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-116">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="a9ca3-117">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-117">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="a9ca3-118">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-118">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="a9ca3-119">**处理数据**</span><span class="sxs-lookup"><span data-stu-id="a9ca3-119">**Process Data**</span></span>|<span data-ttu-id="a9ca3-120">将数据加载到分区或表中，而无需重新生成层次结构或关系或重新计算计算列和度量值。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-120">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="a9ca3-121">**处理清除**</span><span class="sxs-lookup"><span data-stu-id="a9ca3-121">**Process Clear**</span></span>|<span data-ttu-id="a9ca3-122">删除分区中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-122">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="a9ca3-123">**处理添加**</span><span class="sxs-lookup"><span data-stu-id="a9ca3-123">**Process Add**</span></span>|<span data-ttu-id="a9ca3-124">以增量方式用新数据更新分区。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-124">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="a9ca3-125">在 **“处理”** 复选框列中，选择要用所选模式处理的分区，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a9ca3-125">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ca3-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9ca3-126">See Also</span></span>  
 <span data-ttu-id="a9ca3-127">[&#40;SSAS 表格&#41;的表格模型分区](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a9ca3-127">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="a9ca3-128">创建和管理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="a9ca3-128">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
