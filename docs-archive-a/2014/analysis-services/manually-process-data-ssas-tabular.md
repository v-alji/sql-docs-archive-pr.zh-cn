---
title: 手动处理 (SSAS 表格) 的数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51bdb1b9535685db4fc35dbdd791e6b4d9bed1b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589325"
---
# <a name="manually-process-data-ssas-tabular"></a><span data-ttu-id="9ca3b-102">手动处理数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="9ca3b-102">Manually Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="9ca3b-103">本主题说明如何手动处理 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中的工作区数据。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-103">This topic describes how to manually process workspace data in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="9ca3b-104">如果您创作表格模型时使用了外部数据，则可以使用“处理”命令手动刷新这些数据。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-104">When you author a tabular model that uses external data, you can manually refresh the data by using the Process command.</span></span> <span data-ttu-id="9ca3b-105">您可以处理单个表、模型中的所有表或一个或多个分区。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-105">You can process a single table, all tables in the model, or one or more partitions.</span></span> <span data-ttu-id="9ca3b-106">只要处理数据，就还可能需要重新计算数据。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-106">Whenever you process data, you may also need to recalculate data.</span></span>  <span data-ttu-id="9ca3b-107">处理数据意味着从外部源中获取最新的数据。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-107">Processing data means getting the latest data from external sources.</span></span> <span data-ttu-id="9ca3b-108">“重新计算”意味着更新使用数据的任何公式的结果。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-108">Recalculating means updating the result of any formula that uses the data.</span></span>  
  
 <span data-ttu-id="9ca3b-109">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="9ca3b-109">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="9ca3b-110">手动处理数据</span><span class="sxs-lookup"><span data-stu-id="9ca3b-110">Manually Process Data</span></span>](#bkmk_mahually_process)  
  
-   [<span data-ttu-id="9ca3b-111">数据处理进度</span><span class="sxs-lookup"><span data-stu-id="9ca3b-111">Data Process Progress</span></span>](#bkmk_data_process_progress)  
  
##  <a name="manually-process-data"></a><a name="bkmk_mahually_process"></a><span data-ttu-id="9ca3b-112">手动处理数据</span><span class="sxs-lookup"><span data-stu-id="9ca3b-112">Manually Process Data</span></span>  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a><span data-ttu-id="9ca3b-113">处理模型中单个表或者所有表的数据</span><span class="sxs-lookup"><span data-stu-id="9ca3b-113">To process data for a single table or all tables in a model</span></span>  
  
1.  <span data-ttu-id="9ca3b-114">在模型设计器中，单击要处理的表。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-114">In the model designer, click the table you want to process.</span></span>  
  
2.  <span data-ttu-id="9ca3b-115">单击 **“模型”** 菜单，然后单击 **“处理”**，再单击 **“处理”** 或 **“全部处理”**。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-115">Click on the **Model** menu, then click **Process**, and then click **Process** or **Process All**.</span></span>  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a><span data-ttu-id="9ca3b-116">处理使用相同连接的所有表的数据</span><span class="sxs-lookup"><span data-stu-id="9ca3b-116">To process data for all tables using the same connection</span></span>  
  
1.  <span data-ttu-id="9ca3b-117">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="9ca3b-118">在 **“现有连接”** 对话框中，选择某一连接，然后单击 **“处理”**。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-118">In the **Existing Connections** dialog box, select a connection, and then click **Process**.</span></span>  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a><span data-ttu-id="9ca3b-119">处理一个或多个分区的数据</span><span class="sxs-lookup"><span data-stu-id="9ca3b-119">To process data for one or more partitions</span></span>  
  
1.  <span data-ttu-id="9ca3b-120">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后指向 **“处理”**，再单击 **“处理分区”**。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-120">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Process**, and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="9ca3b-121">在 **“处理分区”** 对话框的 **“模式”** 中，选择下列处理模式之一：</span><span class="sxs-lookup"><span data-stu-id="9ca3b-121">In the **Process Partitions** dialog box, in **Mode**, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="9ca3b-122">“模式”</span><span class="sxs-lookup"><span data-stu-id="9ca3b-122">Mode</span></span>|<span data-ttu-id="9ca3b-123">说明</span><span class="sxs-lookup"><span data-stu-id="9ca3b-123">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="9ca3b-124">**处理默认值**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-124">**Process Default**</span></span>|<span data-ttu-id="9ca3b-125">检测分区对象的处理状态，执行必要的处理，将未处理的分区对象或部分处理的分区对象交付为已完全处理的分区对象。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-125">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="9ca3b-126">为空表和分区加载数据；生成或重新生成层次结构、计算列和关系。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-126">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="9ca3b-127">**处理全部**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-127">**Process Full**</span></span>|<span data-ttu-id="9ca3b-128">处理分区对象及其包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-128">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="9ca3b-129">对已处理的对象运行“处理全部”时， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将删除该对象中的所有数据，然后再处理该对象。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-129">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="9ca3b-130">在对对象进行结构更改后，需要这种类型的处理。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-130">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="9ca3b-131">**处理数据**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-131">**Process Data**</span></span>|<span data-ttu-id="9ca3b-132">将数据加载到分区或表中，而无需重新生成层次结构或关系或重新计算计算列和度量值。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-132">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="9ca3b-133">**处理清除**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-133">**Process Clear**</span></span>|<span data-ttu-id="9ca3b-134">删除分区中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-134">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="9ca3b-135">**处理添加**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-135">**Process Add**</span></span>|<span data-ttu-id="9ca3b-136">以增量方式用新数据更新分区。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-136">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="9ca3b-137">在分区列表中，选择要处理的分区，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-137">In the partitions list, select the partitions you want to process, and then click **OK**.</span></span>  
  
##  <a name="data-process-progress"></a><a name="bkmk_data_process_progress"></a><span data-ttu-id="9ca3b-138">数据处理进度</span><span class="sxs-lookup"><span data-stu-id="9ca3b-138">Data Process Progress</span></span>  
 <span data-ttu-id="9ca3b-139">**“数据处理进度”** 对话框可用于监视从外部数据源导入到模型中的数据的处理。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-139">The **Data Process Progress** dialog box enables you to monitor the processing of data that you have imported into the model from an external source.</span></span> <span data-ttu-id="9ca3b-140">若要访问此对话框，请依次单击 **“模型”** 菜单、 **“处理分区”**、 **“处理表”** 或 **“全部处理”**。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-140">To access this dialog box, click on the **Model** menu, and then click **Process Partitions**, **Process Table** or **Process All**.</span></span>  
  
 <span data-ttu-id="9ca3b-141">**Status**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-141">**Status**</span></span>  
 <span data-ttu-id="9ca3b-142">指示处理操作是否成功。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-142">Indicates whether the process operation was successful or not.</span></span>  
  
 <span data-ttu-id="9ca3b-143">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-143">**Details**</span></span>  
 <span data-ttu-id="9ca3b-144">列出导入的表和视图，导入的行数，并提供一个指向任何问题报告的链接。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-144">Lists the tables and views that were imported, the number of rows that were imported, and provides a link to a report of any issues.</span></span>  
  
 <span data-ttu-id="9ca3b-145">**停止刷新**</span><span class="sxs-lookup"><span data-stu-id="9ca3b-145">**Stop Refresh**</span></span>  
 <span data-ttu-id="9ca3b-146">单击此选项可以暂停处理操作。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-146">Click to halt the process operation.</span></span> <span data-ttu-id="9ca3b-147">如果操作用时过长或出现太多错误，则此选项很有用。</span><span class="sxs-lookup"><span data-stu-id="9ca3b-147">This option is useful if the operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca3b-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ca3b-148">See Also</span></span>  
 <span data-ttu-id="9ca3b-149">[&#40;SSAS 表格&#41;处理数据](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="9ca3b-149">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="9ca3b-150">数据处理故障排除（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="9ca3b-150">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)  
  
  
