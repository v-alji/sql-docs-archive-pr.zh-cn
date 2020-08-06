---
title: 排查 (SSAS 表格) 的过程数据问题 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 678f523c-e181-4456-9a54-7b7bf044b8d2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6962f5452f9b16472a59914f557e6949ebb4ed05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585994"
---
# <a name="troubleshoot-process-data-ssas-tabular"></a><span data-ttu-id="fc19e-102">数据处理故障排除（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="fc19e-102">Troubleshoot Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="fc19e-103">本主题提供有关在使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]创建模型时处理（刷新）模型数据的信息。</span><span class="sxs-lookup"><span data-stu-id="fc19e-103">This topic provides information about processing (refresh) model data when authoring a model by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="fc19e-104">它不提供有关处理已部署到 Analysis Services 服务器实例的模型中的数据的信息。</span><span class="sxs-lookup"><span data-stu-id="fc19e-104">This topic does not provide information about processing data in models that has been deployed to an Analysis Services server instance.</span></span> <span data-ttu-id="fc19e-105">有关处理已部署的模型中的数据的详细信息，请参阅 [在 Analysis Services 中编写管理任务脚本](script-administrative-tasks-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fc19e-105">For more information about processing data in a deployed model, see [Script Administrative Tasks in Analysis Services](script-administrative-tasks-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="fc19e-106">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="fc19e-106">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="fc19e-107">数据处理的工作原理</span><span class="sxs-lookup"><span data-stu-id="fc19e-107">How Data Processing Works</span></span>](#bkmk_how_df_works)  
  
-   [<span data-ttu-id="fc19e-108">数据处理的影响</span><span class="sxs-lookup"><span data-stu-id="fc19e-108">Impact of Data Processing</span></span>](#bkmk_impact_of_df)  
  
-   [<span data-ttu-id="fc19e-109">确定数据源</span><span class="sxs-lookup"><span data-stu-id="fc19e-109">Determining the Source of Data</span></span>](#bkmk_det_source)  
  
-   [<span data-ttu-id="fc19e-110">确定最后刷新数据的时间</span><span class="sxs-lookup"><span data-stu-id="fc19e-110">Determining When Data was Last Refreshed</span></span>](#bkmk_det_last_ref)  
  
-   [<span data-ttu-id="fc19e-111">对可刷新数据源的限制</span><span class="sxs-lookup"><span data-stu-id="fc19e-111">Restrictions on Refreshable Data Sources</span></span>](#bkmk_restrictions)  
  
-   [<span data-ttu-id="fc19e-112">对数据源的更改的限制</span><span class="sxs-lookup"><span data-stu-id="fc19e-112">Restrictions on Changes to a Data Source</span></span>](#bkmk_rest_changes)  
  
##  <a name="how-data-processing-works"></a><a name="bkmk_how_df_works"></a><span data-ttu-id="fc19e-113">数据处理的工作原理</span><span class="sxs-lookup"><span data-stu-id="fc19e-113">How Data Processing Works</span></span>  
 <span data-ttu-id="fc19e-114">处理数据时，模型设计器中的数据将替换为新数据。</span><span class="sxs-lookup"><span data-stu-id="fc19e-114">When you process data, the data in the model designer is replaced with new data.</span></span> <span data-ttu-id="fc19e-115">不能只导入新数据行或更改的数据。</span><span class="sxs-lookup"><span data-stu-id="fc19e-115">You cannot import just new rows of data or just changed data.</span></span> <span data-ttu-id="fc19e-116">模型设计器不跟踪之前添加了哪些行。</span><span class="sxs-lookup"><span data-stu-id="fc19e-116">The model designer does not track which rows were added previously.</span></span>  
  
 <span data-ttu-id="fc19e-117">数据处理以事务形式执行。</span><span class="sxs-lookup"><span data-stu-id="fc19e-117">Processing of data takes place as a transaction.</span></span> <span data-ttu-id="fc19e-118">这意味着一旦开始更新数据，整个更新不是失败就是成功；绝不会出现部分数据正确的情况。</span><span class="sxs-lookup"><span data-stu-id="fc19e-118">This means that once you begin updating data, the entire update must either fail or succeed; you will never have data that is partly correct.</span></span>  
  
 <span data-ttu-id="fc19e-119">从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]启动的手动数据处理由 Analysis Services 的本地内存中实例来处理。</span><span class="sxs-lookup"><span data-stu-id="fc19e-119">Manual data process, which you initiate from [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], is handled by the local in-memory instance of Analysis Services.</span></span> <span data-ttu-id="fc19e-120">因此，数据处理操作会对计算机中其他任务的性能产生影响。</span><span class="sxs-lookup"><span data-stu-id="fc19e-120">Therefore, the data process operation can affect the performance of other tasks on your computer.</span></span> <span data-ttu-id="fc19e-121">但是，如果你使用脚本在已部署的模型中安排数据的自动处理，该 Analysis Services 实例将管理导入过程及其时间。</span><span class="sxs-lookup"><span data-stu-id="fc19e-121">However, if you schedule automatic process of data in a deployed model by using a script, the instance of Analysis Services manages the import process and its timing.</span></span>  
  
##  <a name="impact-of-data-processing"></a><a name="bkmk_impact_of_df"></a> <span data-ttu-id="fc19e-122">数据处理的影响</span><span class="sxs-lookup"><span data-stu-id="fc19e-122">Impact of Data Processing</span></span>  
 <span data-ttu-id="fc19e-123">数据的处理通常会触发数据的重新计算。</span><span class="sxs-lookup"><span data-stu-id="fc19e-123">A process of data usually triggers recalculation of data.</span></span>  <span data-ttu-id="fc19e-124">处理数据意味着从外部源获取最新数据；重新计算意味着更新使用已更改数据的所有公式的结果。</span><span class="sxs-lookup"><span data-stu-id="fc19e-124">Processing data means getting the latest data from the external sources;  recalculating means updating the result of all formulas that use data that has changed.</span></span> <span data-ttu-id="fc19e-125">处理操作通常会触发重新计算。</span><span class="sxs-lookup"><span data-stu-id="fc19e-125">A process operation usually triggers recalculation.</span></span>  
  
 <span data-ttu-id="fc19e-126">因此，在更改数据源或处理从数据源中获取的数据之前，您应该始终注意潜在影响，还要考虑以下潜在后果：</span><span class="sxs-lookup"><span data-stu-id="fc19e-126">Therefore you should always be mindful of the potential impact before you change data sources or process the data that is obtained from the data source, and consider these potential consequences:</span></span>  
  
-   <span data-ttu-id="fc19e-127">模型数据的某些部分可能由于数据源中的更改而被破坏。</span><span class="sxs-lookup"><span data-stu-id="fc19e-127">Some parts of the model data may be broken as a result of changes in the data source.</span></span> <span data-ttu-id="fc19e-128">如果并非所有列都可从数据源中进行检索（例如，如果这些列已被删除或更改），那么处理将失败，您必须更新源数据与模型数据之间的映射。</span><span class="sxs-lookup"><span data-stu-id="fc19e-128">If not all of the columns can be retrieved from the data source (for example, if they have been deleted or changed), process will fail, and you must update the mappings between the source data and the model data.</span></span> <span data-ttu-id="fc19e-129">有关详细信息，请参阅 [编辑现有数据源连接（SSAS 表格）](edit-an-existing-data-source-connection-ssas-tabular.md)创建模型时处理（刷新）模型数据的信息。</span><span class="sxs-lookup"><span data-stu-id="fc19e-129">For more information, see [Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;](edit-an-existing-data-source-connection-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="fc19e-130">在处理后，某些列可能被标记为包含错误。</span><span class="sxs-lookup"><span data-stu-id="fc19e-130">After processing, some columns might be flagged as containing an error.</span></span> <span data-ttu-id="fc19e-131">发生此情况的原因是：列中的 DAX 公式使用的数据在您进行处理时变得不可用、列的数据类型发生更改或向外部数据中添加了无效值。</span><span class="sxs-lookup"><span data-stu-id="fc19e-131">This can happen because the DAX formula in the column uses data that became unavailable when you processed, the data type of a column changed, or an invalid value was added to the external data.</span></span> <span data-ttu-id="fc19e-132">若要解决此问题，您可以编辑该公式或删除该列（如果它基于不再可用的数据）。</span><span class="sxs-lookup"><span data-stu-id="fc19e-132">To resolve the issue, you can edit the formula, or you can delete the column if it is based on data that is no longer available.</span></span>  
  
-   <span data-ttu-id="fc19e-133">将需要重新计算使用更新的数据的公式。</span><span class="sxs-lookup"><span data-stu-id="fc19e-133">Formulas that use the updated data will need to be recalculated.</span></span> <span data-ttu-id="fc19e-134">根据模型的大小，这一重新计算可能花费一些时间。</span><span class="sxs-lookup"><span data-stu-id="fc19e-134">Depending on the size of the model, this can take some time.</span></span>  
  
-   <span data-ttu-id="fc19e-135">如果您的模型包含多个数据源，那么即使只有一个外部数据源发生了更改，您也可能需要处理整个模型（“全部处理”）。</span><span class="sxs-lookup"><span data-stu-id="fc19e-135">If your model contains multiple data sources, you might need to process the entire model (Process All) even if only one external data source has changed.</span></span> <span data-ttu-id="fc19e-136">例如，如果您创建依赖于计算列的度量值，并且这些计算列使用其他计算列中的值，则模型设计器将首先分析依赖关系，然后按顺序处理相关对象的整个链。</span><span class="sxs-lookup"><span data-stu-id="fc19e-136">For example, if you create measures that rely on calculated columns, and those calculated columns use values from other calculated columns, the model designer first analyzes the dependencies and then processes the entire chain of related objects in order.</span></span> <span data-ttu-id="fc19e-137">根据依赖关系的复杂程度，此操作可能会花费较长时间。</span><span class="sxs-lookup"><span data-stu-id="fc19e-137">Depending on the complexity of the dependencies, this can take a long time.</span></span>  
  
-   <span data-ttu-id="fc19e-138">更改筛选器时，必须重新计算整个模型。</span><span class="sxs-lookup"><span data-stu-id="fc19e-138">When you change a filter, the entire model must be recalculated.</span></span>  
  
##  <a name="determining-the-source-of-data"></a><a name="bkmk_det_source"></a><span data-ttu-id="fc19e-139">确定数据源</span><span class="sxs-lookup"><span data-stu-id="fc19e-139">Determining the Source of Data</span></span>  
 <span data-ttu-id="fc19e-140">如果您不确定模型中数据的来源，可以使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的工具获取详细信息，包括源文件的名称和路径。</span><span class="sxs-lookup"><span data-stu-id="fc19e-140">If you are not sure where the data in your model came from, you can use the tools in the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to get the details, including the source file name and path.</span></span>  
  
#### <a name="to-find-the-source-of-existing-data"></a><span data-ttu-id="fc19e-141">查找现有数据的源</span><span class="sxs-lookup"><span data-stu-id="fc19e-141">To find the source of existing data</span></span>  
  
1.  <span data-ttu-id="fc19e-142">在模型设计器中，选择包含要了解其源的数据的表。</span><span class="sxs-lookup"><span data-stu-id="fc19e-142">In the model designer, select the table that contains the data for which you want to know the source.</span></span>  
  
2.  <span data-ttu-id="fc19e-143">单击 **“表”** 菜单，然后单击 **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="fc19e-143">Click on the **Table** menu, and the click **Table Properties**.</span></span>  
  
3.  <span data-ttu-id="fc19e-144">在 **“编辑表属性”** 对话框中，记下为 **“连接名称”** 列出的值。</span><span class="sxs-lookup"><span data-stu-id="fc19e-144">In the **Edit Table Properties** dialog box, make note of the value listed for **Connection Name**.</span></span>  
  
4.  <span data-ttu-id="fc19e-145">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]的 **“模型”** 菜单上，单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="fc19e-145">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Existing Connections**.</span></span>  
  
5.  <span data-ttu-id="fc19e-146">在 **“现有连接”** 对话框中，选择具有您在步骤 3 中找到的名称的数据源，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="fc19e-146">In the **Existing Connections** dialog box, select the data source with the name you found in step 3, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="fc19e-147">在 **“编辑连接”** 对话框中查看连接信息，如数据库名称、文件路径或报表路径。</span><span class="sxs-lookup"><span data-stu-id="fc19e-147">In the **Edit Connections** dialog box, view the connection information, such as the database name, file path, or report path.</span></span>  
  
##  <a name="determining-when-data-was-last-refreshed"></a><a name="bkmk_det_last_ref"></a> <span data-ttu-id="fc19e-148">确定最后刷新数据的时间</span><span class="sxs-lookup"><span data-stu-id="fc19e-148">Determining When Data was Last Refreshed</span></span>  
 <span data-ttu-id="fc19e-149">可以使用“表属性”确定最后刷新数据的时间。</span><span class="sxs-lookup"><span data-stu-id="fc19e-149">You can use the Table Properties to determine when the data was last refreshed.</span></span>  
  
#### <a name="to-find-the-date-and-time-that-a-table-was-last-processed"></a><span data-ttu-id="fc19e-150">查找最后处理表的日期和时间</span><span class="sxs-lookup"><span data-stu-id="fc19e-150">To find the date and time that a table was last processed</span></span>  
  
1.  <span data-ttu-id="fc19e-151">在模型设计器中，选择包含要了解其刷新日期的数据的表。</span><span class="sxs-lookup"><span data-stu-id="fc19e-151">In the model designer, select the table that contains the data for which you want to know the refresh date.</span></span>  
  
2.  <span data-ttu-id="fc19e-152">单击 **“表”** 菜单，然后单击 **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="fc19e-152">Click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
3.  <span data-ttu-id="fc19e-153">在 **“编辑表属性”** 对话框中， **“最后刷新时间”** 显示刷新表的最后日期。</span><span class="sxs-lookup"><span data-stu-id="fc19e-153">In the **Edit Table Properties** dialog box, **Last Refreshed** shows the last date that the table was refreshed.</span></span>  
  
##  <a name="restrictions-on-refreshable-data-sources"></a><a name="bkmk_restrictions"></a><span data-ttu-id="fc19e-154">对可刷新数据源的限制</span><span class="sxs-lookup"><span data-stu-id="fc19e-154">Restrictions on Refreshable Data Sources</span></span>  
 <span data-ttu-id="fc19e-155">对于可从 Analysis Services 实例上已部署的模型进行自动处理的数据源，存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="fc19e-155">Some restrictions apply to the data sources that can be automatically processed from a deployed model on an Analysis Services instance.</span></span> <span data-ttu-id="fc19e-156">请务必仅选择满足以下条件的那些数据源：</span><span class="sxs-lookup"><span data-stu-id="fc19e-156">Be sure to select only those data sources that meet the following criteria:</span></span>  
  
-   <span data-ttu-id="fc19e-157">该数据源必须在进行数据处理时可用，并且还必须在规定的位置上可用。</span><span class="sxs-lookup"><span data-stu-id="fc19e-157">The data source must be available at the time that data process occurs and available at the stated location.</span></span> <span data-ttu-id="fc19e-158">如果原始数据源处于创建此模型的用户的本地磁盘驱动器上，则必须或者从数据处理操作中排除该数据源，或者确定一种方法来将该数据源发布到可通过网络连接访问的位置。</span><span class="sxs-lookup"><span data-stu-id="fc19e-158">If the original data source is on a local disk drive of the user who authored the model, you must either exclude that data source from the data process operation, or find a way to publish that data source to a location that is accessible through a network connection.</span></span> <span data-ttu-id="fc19e-159">如果您将某一数据源移到一个网络位置，请确保在模型设计器中打开模型并且重复数据检索步骤。</span><span class="sxs-lookup"><span data-stu-id="fc19e-159">If you move a data source to a network location, be sure to open the model in the model designer and repeat the data retrieval steps.</span></span> <span data-ttu-id="fc19e-160">这是重新建立数据源连接属性中存储的连接信息所必需的。</span><span class="sxs-lookup"><span data-stu-id="fc19e-160">This is necessary to re-establish the connection information that is stored in the data source connection properties.</span></span>  
  
-   <span data-ttu-id="fc19e-161">必须使用在数据源连接中嵌入的凭据来访问数据源。</span><span class="sxs-lookup"><span data-stu-id="fc19e-161">The data source must be accessed using the credentials that are embedded in the data source connection.</span></span> <span data-ttu-id="fc19e-162">当您连接到外部数据源时，在数据源连接中创建嵌入的凭据。</span><span class="sxs-lookup"><span data-stu-id="fc19e-162">Embedded credentials are created in the data source connection when you connect to the external data source.</span></span>  
  
-   <span data-ttu-id="fc19e-163">数据处理必须对您指定的所有数据源均成功。</span><span class="sxs-lookup"><span data-stu-id="fc19e-163">Data process must succeed for all of the data sources that you specify.</span></span> <span data-ttu-id="fc19e-164">否则，处理的数据将被放弃，只会留下最后保存的模型版本。</span><span class="sxs-lookup"><span data-stu-id="fc19e-164">Otherwise, the processed data is discarded, leaving you with the last saved version of the model.</span></span> <span data-ttu-id="fc19e-165">因此，请排除您不确定的任何数据源。</span><span class="sxs-lookup"><span data-stu-id="fc19e-165">Exclude any data sources that you are not sure about.</span></span>  
  
-   <span data-ttu-id="fc19e-166">数据处理不得使模型中的其他数据失效。</span><span class="sxs-lookup"><span data-stu-id="fc19e-166">Data process must not invalidate other data in your model.</span></span> <span data-ttu-id="fc19e-167">在处理您的数据子集时，请务必了解在较新的数据与不是来自同一时间段的静态数据进行聚合后模型是否仍有效。</span><span class="sxs-lookup"><span data-stu-id="fc19e-167">When you process a subset of your data, it is important that you understand whether the model is still valid once newer data is aggregated with static data that is not from the same time period.</span></span> <span data-ttu-id="fc19e-168">作为模型设计者，您要知道您的数据依赖关系并确保数据处理适合于模型本身。</span><span class="sxs-lookup"><span data-stu-id="fc19e-168">As a model designer, it is up to you to know your data dependencies and ensure that data process is appropriate for the model itself.</span></span>  
  
     <span data-ttu-id="fc19e-169">外部数据源通过您在使用表导入向导将原始数据导入到模型时指定的嵌入连接字符串、URL 或 UNC 路径来访问。</span><span class="sxs-lookup"><span data-stu-id="fc19e-169">An external data source is accessed through an embedded connection string, URL, or UNC path that you specified when you imported the original data into the model using the Table Import Wizard.</span></span> <span data-ttu-id="fc19e-170">在后续的数据刷新操作中将重用在数据源连接中存储的原始连接信息。</span><span class="sxs-lookup"><span data-stu-id="fc19e-170">Original connection information that is stored in the data source connection is reused for subsequent data refresh operations.</span></span> <span data-ttu-id="fc19e-171">没有专为进行数据处理而创建和管理单独的连接信息；而只使用现有连接信息。</span><span class="sxs-lookup"><span data-stu-id="fc19e-171">There is no separate connection information that is created and managed for data process purposes; only existing connection information is used.</span></span>  
  
##  <a name="restrictions-on-changes-to-a-data-source"></a><a name="bkmk_rest_changes"></a> <span data-ttu-id="fc19e-172">对数据源的更改限制</span><span class="sxs-lookup"><span data-stu-id="fc19e-172">Restrictions on Changes to a Data Source</span></span>  
 <span data-ttu-id="fc19e-173">对于您可以对数据源进行的更改，存在一些限制：</span><span class="sxs-lookup"><span data-stu-id="fc19e-173">There are some restrictions on the changes that you can make to a data source:</span></span>  
  
-   <span data-ttu-id="fc19e-174">列的数据类型只能更改为兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fc19e-174">The data types of a column can only be changed to a compatible data type.</span></span> <span data-ttu-id="fc19e-175">例如，如果列中的数据中包含小数，则您无法将该数据类型更改为整数。</span><span class="sxs-lookup"><span data-stu-id="fc19e-175">For example, if the data in the column includes decimal numbers, you cannot change the data type to an integer.</span></span> <span data-ttu-id="fc19e-176">但是，您可以将数字数据更改为文本。</span><span class="sxs-lookup"><span data-stu-id="fc19e-176">However, you can change numeric data to text.</span></span> <span data-ttu-id="fc19e-177">有关数据类型的详细信息，请参阅[支持的数据类型（SSAS 表格）](tabular-models/data-types-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="fc19e-177">For more information about data types, see [Data Types Supported &#40;SSAS Tabular&#41;](tabular-models/data-types-supported-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="fc19e-178">不能在不同表中多选列和更改列属性。</span><span class="sxs-lookup"><span data-stu-id="fc19e-178">You cannot multi-select columns in different tables and change properties of the columns.</span></span> <span data-ttu-id="fc19e-179">您一次只能使用一个表或视图。</span><span class="sxs-lookup"><span data-stu-id="fc19e-179">You can work with only one table or view at a time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc19e-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc19e-180">See Also</span></span>  
 <span data-ttu-id="fc19e-181">[手动处理 &#40;SSAS 表格&#41;的数据](manually-process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fc19e-181">[Manually Process Data &#40;SSAS Tabular&#41;](manually-process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="fc19e-182">编辑现有数据源连接（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="fc19e-182">Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;</span></span>](edit-an-existing-data-source-connection-ssas-tabular.md)  
  
  
