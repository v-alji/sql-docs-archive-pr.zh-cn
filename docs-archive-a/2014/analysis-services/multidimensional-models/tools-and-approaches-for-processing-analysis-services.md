---
title: 处理 (Analysis Services) 的工具和方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- process [Analysis Services]
- processing [Analysis Services]
ms.assetid: 82347a16-4145-4655-8adf-2a300f1fdf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2b28ecf29adc8240f76ec9888f9d4cb06dda887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587050"
---
# <a name="tools-and-approaches-for-processing-analysis-services"></a><span data-ttu-id="4e726-102">用于处理的工具和方法 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4e726-102">Tools and Approaches for Processing (Analysis Services)</span></span>
  <span data-ttu-id="4e726-103">处理是指这样一项操作：Analysis Services 查询关系数据源并使用该数据填充 Analysis Services 对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-103">Processing is an operation in which Analysis Services queries a relational data source and populates Analysis Services objects using that data.</span></span>  
  
 <span data-ttu-id="4e726-104">作为 Analysis Services 系统管理员，您可以使用以下方法执行并监视 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的处理：</span><span class="sxs-lookup"><span data-stu-id="4e726-104">As an Analysis Services system administrator, you can execute and monitor the processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects using these approaches:</span></span>  
  
-   <span data-ttu-id="4e726-105">运行影响分析，了解对象依赖关系和操作的作用域</span><span class="sxs-lookup"><span data-stu-id="4e726-105">Run Impact Analysis to understand object dependencies and scope of operations</span></span>  
  
-   <span data-ttu-id="4e726-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e726-106">Process individual objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="4e726-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e726-107">Process individual or multiple objects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="4e726-108">运行影响分析，检查由于当前操作而不会处理的相关对象的列表。</span><span class="sxs-lookup"><span data-stu-id="4e726-108">Run Impact Analysis to review a list of related objects that will be unprocessed as result of the current action.</span></span>  
  
-   <span data-ttu-id="4e726-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] XMLA 查询窗口中生成并运行脚本，以便处理单个或多个对象</span><span class="sxs-lookup"><span data-stu-id="4e726-109">Generate and run a script in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to process individual or multiple objects</span></span>  
  
-   <span data-ttu-id="4e726-110">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e726-110">Use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell cmdlets</span></span>  
  
-   <span data-ttu-id="4e726-111">使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包中的控制流和任务</span><span class="sxs-lookup"><span data-stu-id="4e726-111">Use control flows and tasks in [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages</span></span>  
  
-   <span data-ttu-id="4e726-112">使用 SQL Server Profiler 监视处理</span><span class="sxs-lookup"><span data-stu-id="4e726-112">Monitor processing with SQL Server Profiler</span></span>  
  
-   <span data-ttu-id="4e726-113">使用 AMO 对自定义解决方案编程。</span><span class="sxs-lookup"><span data-stu-id="4e726-113">Program a custom solution using AMO.</span></span> <span data-ttu-id="4e726-114">有关详细信息，请参阅 [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)。</span><span class="sxs-lookup"><span data-stu-id="4e726-114">For more information, see [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects).</span></span>  
  
 <span data-ttu-id="4e726-115">处理是由一组处理选项控制的高度可配置操作，这些选项决定在对象级别执行完全处理还是增量处理。</span><span class="sxs-lookup"><span data-stu-id="4e726-115">Processing is a highly configurable operation, controlled by a set of processing options that determine whether full or incremental processing occurs at the object level.</span></span> <span data-ttu-id="4e726-116">有关处理选项和对象的详细信息，请参阅[处理选项和设置 (Analysis Services)](processing-options-and-settings-analysis-services.md) 和[处理 Analysis Services 对象](processing-analysis-services-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-116">For more information about processing options and objects, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) and [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e726-117">本主题介绍用于处理多维模型的工具和方法。</span><span class="sxs-lookup"><span data-stu-id="4e726-117">This topic describes the tools and approaches for processing multidimensional models.</span></span> <span data-ttu-id="4e726-118">有关处理表格模型的详细信息，请参阅[处理数据库、表或分区](../tabular-models/process-database-table-or-partition-analysis-services.md)并[处理数据 &#40;SSAS 表格&#41;](../process-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-118">For more information about processing tabular models, see [Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) and [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
### <a name="processing-objects-in-sql-server-management-studio"></a><span data-ttu-id="4e726-119">在 SQL Server Management Studio 中处理对象</span><span class="sxs-lookup"><span data-stu-id="4e726-119">Processing objects in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="4e726-120">启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并连接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="4e726-120">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="4e726-121">右键单击要处理的 Analysis Services 对象，然后单击“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e726-121">Right-click the Analysis Services object you want to process and then click **Process**.</span></span> <span data-ttu-id="4e726-122">可以在以下任何级别处理数据：</span><span class="sxs-lookup"><span data-stu-id="4e726-122">You can process data at any of these levels:</span></span>  
  
    -   <span data-ttu-id="4e726-123">数据库</span><span class="sxs-lookup"><span data-stu-id="4e726-123">Databases</span></span>  
  
    -   <span data-ttu-id="4e726-124">多维数据集</span><span class="sxs-lookup"><span data-stu-id="4e726-124">Cubes</span></span>  
  
    -   <span data-ttu-id="4e726-125">度量值组或度量值组中的各个分区</span><span class="sxs-lookup"><span data-stu-id="4e726-125">Measure Groups or individual partitions in the measure group</span></span>  
  
    -   <span data-ttu-id="4e726-126">维度</span><span class="sxs-lookup"><span data-stu-id="4e726-126">Dimensions</span></span>  
  
    -   <span data-ttu-id="4e726-127">挖掘模型</span><span class="sxs-lookup"><span data-stu-id="4e726-127">Mining Models</span></span>  
  
    -   <span data-ttu-id="4e726-128">挖掘结构</span><span class="sxs-lookup"><span data-stu-id="4e726-128">Mining Structures</span></span>  
  
     <span data-ttu-id="4e726-129">Analysis Services 对象具有层次结构。</span><span class="sxs-lookup"><span data-stu-id="4e726-129">Analysis Services objects are hierarchical.</span></span> <span data-ttu-id="4e726-130">如果选择数据库，则可能处理该数据库中包含的所有对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-130">If you choose database, processing can occur for all of the objects contained in the database.</span></span> <span data-ttu-id="4e726-131">是否实际进行处理将根据您选择的处理选项和对象的状态而有所不同。</span><span class="sxs-lookup"><span data-stu-id="4e726-131">Whether processing actually occurs will vary depending on the process option you select and the state of the object.</span></span> <span data-ttu-id="4e726-132">具体而言，如果某个对象尚未处理，则处理其父级将导致处理该对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-132">Specifically, if an object is unprocessed, processing its parent will result in that object getting processed.</span></span> <span data-ttu-id="4e726-133">有关对象依赖关系的详细信息，请参阅 [Processing Analysis Services Objects](processing-analysis-services-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-133">For more information about object dependencies, see [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
3.  <span data-ttu-id="4e726-134">在 **“处理”** 对话框中的 **“处理选项”** 中，使用提供的默认值或从列表中选择一个不同的选项。</span><span class="sxs-lookup"><span data-stu-id="4e726-134">In the **Process** dialog box, in **Process Options**, use the default value provided or select a different option from the list.</span></span> <span data-ttu-id="4e726-135">有关每个选项的详细信息，请参阅[处理选项和设置 (Analysis Services)](processing-options-and-settings-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-135">For more information about each option, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="4e726-136">如果“处理”对话框中列出的对象已处理，则单击 **“影响分析”** 可以标识受影响的依赖对象，并且根据需要处理这些依赖对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-136">Click **Impact Analysis** to identify and optionally process dependent objects that are affected if the objects listed in the Process dialog box are processed.</span></span>  
  
5.  <span data-ttu-id="4e726-137">还可以单击 **“更改设置”** 来修改处理顺序、与特定类型的错误相关的处理行为或其他设置。</span><span class="sxs-lookup"><span data-stu-id="4e726-137">Optionally, click **Change Settings** to modify the processing order, processing behavior relative to specific types of errors, and other settings.</span></span>  
  
6.  <span data-ttu-id="4e726-138">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="4e726-138">Click **OK**.</span></span>  
  
     <span data-ttu-id="4e726-139">“处理进度”对话框为每个命令提供当前状态。</span><span class="sxs-lookup"><span data-stu-id="4e726-139">The Process Progress dialog box provides ongoing status for each command.</span></span> <span data-ttu-id="4e726-140">如果状态消息被截断，则可以单击 **“查看详细信息”** 来读取完整消息。</span><span class="sxs-lookup"><span data-stu-id="4e726-140">If a status message is truncated, you can click **View Details** to read the entire message.</span></span>  
  
### <a name="processing-objects-in-sql-server-data-tools"></a><span data-ttu-id="4e726-141">在 SQL Server Data Tools 中处理对象</span><span class="sxs-lookup"><span data-stu-id="4e726-141">Processing Objects in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="4e726-142">启动 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 并打开已部署的项目。</span><span class="sxs-lookup"><span data-stu-id="4e726-142">Start [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open a project that has been deployed.</span></span>  
  
2.  <span data-ttu-id="4e726-143">在解决方案资源管理器中，在已部署项目下，展开 **“维度”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4e726-143">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
3.  <span data-ttu-id="4e726-144">右键单击某个维度，然后单击“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e726-144">Right-click a dimension, and then click **Process**.</span></span> <span data-ttu-id="4e726-145">您可以右键单击多个维度，以便一次处理多个对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-145">You can right-click multiple dimensions to process multiple objects at once.</span></span> <span data-ttu-id="4e726-146">有关详细信息，请参阅 [批处理 (Analysis Services)](batch-processing-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-146">For more information, see [Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="4e726-147">在 **“处理维度”** 对话框的 **“对象列表”** 下的 **“处理选项”** 列中，验证此列的选项是否为 **“处理全部”**。</span><span class="sxs-lookup"><span data-stu-id="4e726-147">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="4e726-148">如果不是，则在“处理选项”中单击选项，并从下拉列表中选择“处理全部”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e726-148">If it is not, under **Process Options**, click the option, and select **Process Full** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="4e726-149">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="4e726-149">Click **Run**.</span></span>  
  
6.  <span data-ttu-id="4e726-150">处理结束时，单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="4e726-150">When processing is finished, click **Close**.</span></span>  
  
##  <a name="run-impact-analysis-to-identify-object-dependencies-and-scope-of-operations"></a><a name="bkmk_impactanalysis"></a><span data-ttu-id="4e726-151">运行影响分析，以确定对象依赖关系和操作的作用域</span><span class="sxs-lookup"><span data-stu-id="4e726-151">Run Impact Analysis to identify object dependencies and scope of operations</span></span>  
  
1.  <span data-ttu-id="4e726-152">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中处理 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]对象之前，可以通过单击 **“处理对象”** 对话框之一中的 **“影响分析”** 来分析对相关对象的影响。</span><span class="sxs-lookup"><span data-stu-id="4e726-152">Before you process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in either [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can analyze the effect on related objects by clicking **Impact Analysis** in one of the **Process Objects** dialog boxes.</span></span>  
  
2.  <span data-ttu-id="4e726-153">右键单击某个维度、多维数据集、度量值组或分区，打开“处理对象”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="4e726-153">Right-click a dimension, cube, measure group, or partition to open a **Process Objects** dialog box.</span></span>  
  
3.  <span data-ttu-id="4e726-154">单击 **“影响分析”**。</span><span class="sxs-lookup"><span data-stu-id="4e726-154">Click **Impact Analysis**.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="4e726-155">将为与选定要处理的对象相关的对象扫描模型并报告重新处理要求。</span><span class="sxs-lookup"><span data-stu-id="4e726-155">scans the model and reports on reprocessing requirements for objects that are related to the one you selected for processing.</span></span>  
  
### <a name="processing-objects-using-xmla"></a><span data-ttu-id="4e726-156">使用 XMLA 处理对象</span><span class="sxs-lookup"><span data-stu-id="4e726-156">Processing objects using XMLA</span></span>  
  
1.  <span data-ttu-id="4e726-157">启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并连接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="4e726-157">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="4e726-158">右键单击待处理的对象，然后单击“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e726-158">Right-click the object to be processed and then click **Process**.</span></span>  
  
3.  <span data-ttu-id="4e726-159">在 **“处理”** 对话框中，选择要使用的处理选项。</span><span class="sxs-lookup"><span data-stu-id="4e726-159">In the **Process** dialog box, select the process option you want to use.</span></span> <span data-ttu-id="4e726-160">修改任何其他设置。</span><span class="sxs-lookup"><span data-stu-id="4e726-160">Modify any other settings.</span></span> <span data-ttu-id="4e726-161">运行“影响分析”以标识您可能需要进行的任何更改。</span><span class="sxs-lookup"><span data-stu-id="4e726-161">Run Impact Analysis to identify any changes you might need to make.</span></span>  
  
4.  <span data-ttu-id="4e726-162">单击 **“处理对象”** 屏幕上的 **“脚本”** 。</span><span class="sxs-lookup"><span data-stu-id="4e726-162">Click **Script** on the **Process Objects** screen.</span></span>  
  
     <span data-ttu-id="4e726-163">这将生成一个 XMLA 脚本并打开一个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA 查询窗口。</span><span class="sxs-lookup"><span data-stu-id="4e726-163">This generates an XMLA script and opens an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window.</span></span>  
  
5.  <span data-ttu-id="4e726-164">关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="4e726-164">Close the dialog box.</span></span> <span data-ttu-id="4e726-165">该脚本包含在该对话框中指定的处理命令和选项。</span><span class="sxs-lookup"><span data-stu-id="4e726-165">The script contains the processing command and options that were specified in the dialog box.</span></span>  
  
6.  <span data-ttu-id="4e726-166">或者，如果您要在同一批中处理其他对象，则可以继续向该脚本添加对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-166">Optionally, you can continue adding to the script if you want to process additional objects in the same batch.</span></span> <span data-ttu-id="4e726-167">若要继续操作，请重复之前的步骤，追加生成的脚本，这样您可以在一个脚本中包含所有要处理的操作。</span><span class="sxs-lookup"><span data-stu-id="4e726-167">To continue, repeat the previous steps, appending the generated script so that you have a single script for all processing operations.</span></span> <span data-ttu-id="4e726-168">若要查看示例，请参阅 [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-168">To view an example, see [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md).</span></span>  
  
7.  <span data-ttu-id="4e726-169">在菜单栏中，单击 **“查询”**，然后单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="4e726-169">From the menu bar, click **Query**, and then click **Execute**.</span></span>  
  
### <a name="processing-objects-using-powershell"></a><span data-ttu-id="4e726-170">使用 PowerShell 处理对象</span><span class="sxs-lookup"><span data-stu-id="4e726-170">Processing objects using PowerShell</span></span>  
  
1.  <span data-ttu-id="4e726-171">从本版本的 SQL Server 开始，您可以使用 Analysis Services PowerShell cmdlet 来处理对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-171">Starting in this release of SQL Server, you can use Analysis Services PowerShell cmdlets to process objects.</span></span> <span data-ttu-id="4e726-172">可以通过交互方式或在脚本中运行以下 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="4e726-172">The following cmdlets can be run interactively or in script:</span></span>  
  
    -   [<span data-ttu-id="4e726-173">Invoke-ProcessCube cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e726-173">Invoke-ProcessCube cmdlet</span></span>](/powershell/module/sqlserver/invoke-processcube)  
  
    -   [<span data-ttu-id="4e726-174">Invoke-ProcessDimension cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e726-174">Invoke-ProcessDimension cmdlet</span></span>](/powershell/module/sqlserver/invoke-processdimension)  
  
    -   [<span data-ttu-id="4e726-175">Invoke-ProcessPartition cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e726-175">Invoke-ProcessPartition cmdlet</span></span>](/powershell/module/sqlserver/invoke-processpartition)  
  
    -   <span data-ttu-id="4e726-176">[Invoke-ASCmd cmdlet](/powershell/module/sqlserver/invoke-ascmd)可用于执行包含处理命令的 XMLA、MDX 或 DMX 脚本。</span><span class="sxs-lookup"><span data-stu-id="4e726-176">[Invoke-ASCmd cmdlet](/powershell/module/sqlserver/invoke-ascmd), which can be used to execute XMLA, MDX, or DMX script that includes processing commands.</span></span>  
  
### <a name="monitoring-object-processing-using-sql-server-profiler"></a><span data-ttu-id="4e726-177">使用 SQL Server Profiler 监视对象处理</span><span class="sxs-lookup"><span data-stu-id="4e726-177">Monitoring object processing using SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="4e726-178">在 SQL Server Profiler 中，连接到 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="4e726-178">Connect to an Analysis Services instance in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="4e726-179">在“事件选择”中，单击 **“显示所有事件”** ，将所有事件添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="4e726-179">In Events Selection, click **Show all events** to add all events to the list.</span></span>  
  
3.  <span data-ttu-id="4e726-180">选择以下事件：</span><span class="sxs-lookup"><span data-stu-id="4e726-180">Choose the following events:</span></span>  
  
    -   <span data-ttu-id="4e726-181">**“命令开始”** 和 **“命令结束”** ，显示处理启动和停止的时间</span><span class="sxs-lookup"><span data-stu-id="4e726-181">**Command Begin** and **Command End** to show when processing starts and stops</span></span>  
  
    -   <span data-ttu-id="4e726-182">**“错误”** ，捕获任何错误</span><span class="sxs-lookup"><span data-stu-id="4e726-182">**Error** to capture any errors</span></span>  
  
    -   <span data-ttu-id="4e726-183">**“进度报告开始”**、 **“进度报告当前状态”** 和 **“进度报告结束”** ，报告处理状态并显示用于检索数据的 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="4e726-183">**Progress Report Begin**, **Progress Report Current**, and **Progress Report End** to report on process status and show the SQL queries used to retrieve the data</span></span>  
  
    -   <span data-ttu-id="4e726-184">**“开始执行 MDX 脚本”** 和 **“结束执行 MDX 脚本”** ，显示多维数据集的计算</span><span class="sxs-lookup"><span data-stu-id="4e726-184">**Execute MDX Script Begin** and **Execute MDX Script End** to show the cube calculations</span></span>  
  
    -   <span data-ttu-id="4e726-185">或者，如果您在诊断与处理相关的性能问题，则可以添加锁事件</span><span class="sxs-lookup"><span data-stu-id="4e726-185">Optionally, add lock events if you are diagnosing performance problems related to processing</span></span>  
  
### <a name="process-analysis-services-objects-using-integration-services"></a><span data-ttu-id="4e726-186">使用 Integration Services 处理 Analysis Services 对象</span><span class="sxs-lookup"><span data-stu-id="4e726-186">Process Analysis Services objects using Integration Services</span></span>  
  
1.  <span data-ttu-id="4e726-187">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，创建一个使用 Analysis Services 处理任务的包，以便在对源关系数据库进行定期更新时使用新数据自动填充对象。</span><span class="sxs-lookup"><span data-stu-id="4e726-187">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], create a package that uses the Analysis Services Processing Task to automatically populate objects with new data when you make regular updates to your source relational database.</span></span>  
  
2.  <span data-ttu-id="4e726-188">在“SSIS 工具箱”中，双击“Analysis Services 处理”将其添加到包中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e726-188">In the **SSIS Toolbox**, double-click **Analysis Services Processing** to add it to the package.</span></span>  
  
3.  <span data-ttu-id="4e726-189">编辑该任务，指定与数据库的连接、处理哪些对象以及处理选项。</span><span class="sxs-lookup"><span data-stu-id="4e726-189">Edit the task to specify a connection to the database, which objects to process, and the process option.</span></span> <span data-ttu-id="4e726-190">有关如何执行此任务的详细信息，请参阅 [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md)。</span><span class="sxs-lookup"><span data-stu-id="4e726-190">For more information about how to implement this task, see [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e726-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e726-191">See Also</span></span>  
 [<span data-ttu-id="4e726-192">多维模型对象处理</span><span class="sxs-lookup"><span data-stu-id="4e726-192">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
