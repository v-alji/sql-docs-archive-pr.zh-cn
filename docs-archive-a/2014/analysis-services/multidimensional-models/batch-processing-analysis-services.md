---
title: 批处理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- batches [Analysis Services]
ms.assetid: ba4dcf72-0667-41d0-816b-ab8ff9a7d9cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: c777339f41f5f9029e4d03d47cc7f682e00032b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577895"
---
# <a name="batch-processing-analysis-services"></a><span data-ttu-id="fbf9f-102">批处理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="fbf9f-102">Batch Processing (Analysis Services)</span></span>
  <span data-ttu-id="fbf9f-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，可以使用批处理命令在单个请求中向服务器发送多个处理命令。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Batch command to send multiple processing commands to the server in a single request.</span></span> <span data-ttu-id="fbf9f-104">通过批处理，您可以控制以什么顺序来处理哪些对象。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-104">Batch processing gives you a way to control which objects are to be processed, and in what order.</span></span> <span data-ttu-id="fbf9f-105">此外，批可以作为一系列独立作业运行，也可以作为一个事务运行，如果事务中的某个进程失败，则会导致整批回滚。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-105">Also, a batch can run as a series of stand-alone jobs, or as a transaction in which the failure of one process causes a rollback of the complete batch.</span></span>  
  
 <span data-ttu-id="fbf9f-106">批处理通过合并和减少提交更改所用的时间，最大限度地提高数据可用性。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-106">Batch processing maximizes data availability by consolidating and reducing the amount of time taken to commit changes.</span></span> <span data-ttu-id="fbf9f-107">在完全处理一个维度时，任何使用该维度的分区都会标记为未处理。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-107">When you fully process a dimension, any partition using that dimension is marked as unprocessed.</span></span> <span data-ttu-id="fbf9f-108">因此，包含未处理分区的多维数据集不可用于浏览。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-108">As a result, cubes that contain the unprocessed partitions are unavailable for browsing.</span></span> <span data-ttu-id="fbf9f-109">可以通过批处理作业将维度和受影响的分区一起处理来解决该问题。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-109">You can address this with a batch processing job by processing the dimensions together with the affected partitions.</span></span> <span data-ttu-id="fbf9f-110">将批处理作业作为事务来运行，可确保该事务中包括的所有对象在处理完成前仍可用于查询。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-110">Running the batch processing job as a transaction makes sure that all objects included in the transaction remain available for queries until all processing is completed.</span></span> <span data-ttu-id="fbf9f-111">由于事务提交更改时，会对受影响的对象放置锁，因此会使这些对象暂时不可用；但是，用于提交更改的总时间比单独处理对象的时间要短。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-111">As the transaction commits the changes, locks are put on the affected objects, making the objects temporarily unavailable, but overall the amount of time used to commit the changes is less than if you processed objects individually.</span></span>  
  
 <span data-ttu-id="fbf9f-112">本主题中的过程展示了完全处理维度和分区的步骤。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-112">The procedures in this topic show the steps for fully processing dimensions and partitions.</span></span> <span data-ttu-id="fbf9f-113">批处理还包括其他处理选项，例如增量处理。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-113">Batch processing can also include other processing options, such as incremental processing.</span></span> <span data-ttu-id="fbf9f-114">若要这些过程能够正常工作，应使用至少包括两个维度和一个分区的现有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-114">For these procedures to work correctly, you should use an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains at least two dimensions and one partition.</span></span>  
  
 <span data-ttu-id="fbf9f-115">本主题包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="fbf9f-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="fbf9f-116">SQL Server Data Tools 中的批处理</span><span class="sxs-lookup"><span data-stu-id="fbf9f-116">Batch Processing in SQL Server Data Tools</span></span>](#bkmk_ssdt)  
  
 [<span data-ttu-id="fbf9f-117">在 Management Studio 中使用 XMLA 执行批处理</span><span class="sxs-lookup"><span data-stu-id="fbf9f-117">Batch Processing using XMLA in Management Studio</span></span>](#bkmk_xmla)  
  
##  <a name="batch-processing-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a> <span data-ttu-id="fbf9f-118">在 SQL Server Data Tools 中执行批处理</span><span class="sxs-lookup"><span data-stu-id="fbf9f-118">Batch Processing in SQL Server Data Tools</span></span>  
 <span data-ttu-id="fbf9f-119">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中处理对象前，必须部署包含对象的项目。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-119">Before objects can be processed in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], the project that contains the objects must be deployed.</span></span> <span data-ttu-id="fbf9f-120">有关详细信息，请参阅[部署 Analysis Services 项目 (SSDT)](deploy-analysis-services-projects-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-120">For more information, see [Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).</span></span>  
  
1.  <span data-ttu-id="fbf9f-121">打开 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-121">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="fbf9f-122">打开已部署的项目。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-122">Open a project that has been deployed.</span></span>  
  
3.  <span data-ttu-id="fbf9f-123">在解决方案资源管理器中，在已部署项目下，展开 **“维度”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-123">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
4.  <span data-ttu-id="fbf9f-124">按住 Ctrl 键，单击 **“维度”** 文件夹中列出的每个维度。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-124">Holding the Ctrl key, click each dimension listed in the **Dimensions** folder.</span></span>  
  
5.  <span data-ttu-id="fbf9f-125">右键单击所选维度，再单击“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-125">Right-click the selected dimensions, and then click **Process**.</span></span>  
  
6.  <span data-ttu-id="fbf9f-126">按住 Ctrl 键，单击 **“对象列表”** 中列出的每个维度。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-126">Holding the Ctrl key, click each dimension listed in the **Object list**.</span></span>  
  
7.  <span data-ttu-id="fbf9f-127">右键单击所选的维度并选择“处理全部”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-127">Right-click the selected dimensions and select **Process Full**.</span></span>  
  
8.  <span data-ttu-id="fbf9f-128">若要自定义批处理作业，请单击 **“更改设置”**。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-128">To customize the batch process job, click **Change Settings.**</span></span>  
  
9. <span data-ttu-id="fbf9f-129">在 **“处理选项”** 下，进行下列设置：</span><span class="sxs-lookup"><span data-stu-id="fbf9f-129">Under **Processing options**, mark the following settings:</span></span>  
  
    -   <span data-ttu-id="fbf9f-130">将 **“处理顺序”** 设置为 **“按顺序”**，将 **“事务模式”** 设置为 **“一项事务”**。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-130">**Processing Order** is set to **Sequential**, and **Transaction mode** is set to **One Transaction**.</span></span>  
  
    -   <span data-ttu-id="fbf9f-131">**“写回表选项”** 设置为 **“使用现有的”**。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-131">**Writeback Table Option** is set to **Use existing**.</span></span>  
  
    -   <span data-ttu-id="fbf9f-132">在 **“受影响的对象”** 下，选中 **“处理受影响的对象”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-132">Under **Affected Objects**, select the **Process affected objects** check box.</span></span>  
  
10. <span data-ttu-id="fbf9f-133">单击 "**维度键错误**" 选项卡。确认已选中 "**使用默认错误配置**"。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-133">Click the **Dimension key errors** tab. Verify that **Use default error configuration** is selected.</span></span>  
  
11. <span data-ttu-id="fbf9f-134">单击 **“确定”** 以关闭 **“更改设置”** 屏幕。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-134">Click **OK** to close the **Change Settings** screen.</span></span>  
  
12. <span data-ttu-id="fbf9f-135">在 **“处理对象”** 屏幕内单击 **“运行”** 以启动处理作业。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-135">Click **Run** in the **Process Objects** screen to start the processing job.</span></span>  
  
13. <span data-ttu-id="fbf9f-136">当 **“状态”** 框显示 **“处理已成功”** 时，单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-136">When the **Status** box shows **Process succeeded**, click **Close**.</span></span>  
  
14. <span data-ttu-id="fbf9f-137">单击 **“处理对象”** 屏幕上的 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-137">Click **Close** on the **Process Objects** screen.</span></span>  
  
##  <a name="batch-processing-using-xmla-in-management-studio"></a><a name="bkmk_xmla"></a><span data-ttu-id="fbf9f-138">在 Management Studio 中使用 XMLA 进行批处理</span><span class="sxs-lookup"><span data-stu-id="fbf9f-138">Batch Processing using XMLA in Management Studio</span></span>  
 <span data-ttu-id="fbf9f-139">您可以创建一个执行批处理的 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-139">You can create an XMLA script that performs batch processing.</span></span> <span data-ttu-id="fbf9f-140">首先在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中为每个对象生成一个 XMLA 脚本，然后将这些脚本并入以交互方式运行或在计划任务内运行的一个 XMLA 查询。</span><span class="sxs-lookup"><span data-stu-id="fbf9f-140">Start by generating an XMLA script in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] for each object, and then combine them into a single XMLA Query that you run interactively or inside a scheduled task.</span></span>  
  
 <span data-ttu-id="fbf9f-141">有关分步说明，请参阅 **使用 SQL Server 代理来计划 SSAS 管理任务** 中的 [示例 2](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)</span><span class="sxs-lookup"><span data-stu-id="fbf9f-141">For step by step instructions, see **Example 2** in [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf9f-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbf9f-142">See Also</span></span>  
 [<span data-ttu-id="fbf9f-143">多维模型对象处理</span><span class="sxs-lookup"><span data-stu-id="fbf9f-143">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
