---
title: " (SSAS 表格) 中处理工作区数据库中的分区 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4a996e90b30794882535327ea3192d7e72818422
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683090"
---
# <a name="process-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="96598-102"> (SSAS 表格中处理工作区数据库中的分区) </span><span class="sxs-lookup"><span data-stu-id="96598-102">Process Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="96598-103">分区将表分成多个逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="96598-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="96598-104">然后，每个分区可独立于其他分区进行处理（刷新）。</span><span class="sxs-lookup"><span data-stu-id="96598-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="96598-105">本主题中的任务说明如何使用 **中的** “处理分区” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]对话框在模型工作区数据库中处理分区。</span><span class="sxs-lookup"><span data-stu-id="96598-105">The tasks in this topic describe how to process partitions in the model workspace database by using the **Process Partitions** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="96598-106">在将模型部署到其他 Analysis Services 实例后，数据库管理员可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、脚本或 IS 包在（已部署）模型中创建和管理分区。</span><span class="sxs-lookup"><span data-stu-id="96598-106">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], by script, or by using an IS package.</span></span> <span data-ttu-id="96598-107">有关详细信息，请参阅[创建和管理表格模型分区（SSAS 表格）](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="96598-107">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="96598-108">处理分区</span><span class="sxs-lookup"><span data-stu-id="96598-108">To process a partition</span></span>  
  
1.  <span data-ttu-id="96598-109">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中，依次单击“模型”菜单、“处理”（“刷新”）和“处理分区”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="96598-109">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="96598-110">在 **“模式”** 列表框中，选择以下处理模式之一：</span><span class="sxs-lookup"><span data-stu-id="96598-110">In the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="96598-111">“模式”</span><span class="sxs-lookup"><span data-stu-id="96598-111">Mode</span></span>|<span data-ttu-id="96598-112">说明</span><span class="sxs-lookup"><span data-stu-id="96598-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="96598-113">**处理默认值**</span><span class="sxs-lookup"><span data-stu-id="96598-113">**Process Default**</span></span>|<span data-ttu-id="96598-114">检测分区对象的处理状态，执行必要的处理，将未处理的分区对象或部分处理的分区对象交付为已完全处理的分区对象。</span><span class="sxs-lookup"><span data-stu-id="96598-114">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="96598-115">为空表和分区加载数据；生成或重新生成层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="96598-115">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="96598-116">**处理全部**</span><span class="sxs-lookup"><span data-stu-id="96598-116">**Process Full**</span></span>|<span data-ttu-id="96598-117">处理分区对象及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="96598-117">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="96598-118">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="96598-118">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="96598-119">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="96598-119">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="96598-120">**处理数据**</span><span class="sxs-lookup"><span data-stu-id="96598-120">**Process Data**</span></span>|<span data-ttu-id="96598-121">将数据加载到分区或表中，而无需重新生成层次结构或关系或重新计算计算列和度量值。</span><span class="sxs-lookup"><span data-stu-id="96598-121">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="96598-122">**处理清除**</span><span class="sxs-lookup"><span data-stu-id="96598-122">**Process Clear**</span></span>|<span data-ttu-id="96598-123">删除分区中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="96598-123">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="96598-124">**处理添加**</span><span class="sxs-lookup"><span data-stu-id="96598-124">**Process Add**</span></span>|<span data-ttu-id="96598-125">以增量方式用新数据更新分区。</span><span class="sxs-lookup"><span data-stu-id="96598-125">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="96598-126">在 **“处理”** 复选框列中，选择要用所选模式处理的分区，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="96598-126">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96598-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96598-127">See Also</span></span>  
 <span data-ttu-id="96598-128">[&#40;SSAS 表格&#41;分区](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="96598-128">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="96598-129">创建和管理工作区数据库中的分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="96598-129">Create and Manage Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](workspace-database-ssas-tabular.md)  
  
  
