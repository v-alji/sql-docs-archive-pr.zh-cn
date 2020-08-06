---
title: 共享数据集设计视图（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47c502da-d163-45d9-bf04-0849e5ba7929
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a3c34b984ab3aca5bbd6313d088695f22ef2255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579508"
---
# <a name="shared-dataset-design-view-report-builder"></a><span data-ttu-id="fd9b3-102">共享数据集设计视图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="fd9b3-102">Shared Dataset Design View (Report Builder)</span></span>
  <span data-ttu-id="fd9b3-103">共享数据集设计窗口有助于您创建可与他人共享的数据集查询。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-103">The Shared Dataset Design window helps you create a dataset query that you can share with others.</span></span> <span data-ttu-id="fd9b3-104">通过该窗口，您可以选择共享数据源，指定共享数据集的属性，在查询设计器中创建查询。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-104">The window lets you select a shared data source, specify properties for the shared dataset, and create a query in the query designer.</span></span>  
  
 <span data-ttu-id="fd9b3-105">![rs_SharedDatasetDesignMode](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")</span><span class="sxs-lookup"><span data-stu-id="fd9b3-105">![rs_SharedDatasetDesignMode](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")</span></span>  
  
 <span data-ttu-id="fd9b3-106">有关使用报表中的数据的详细信息，请参阅[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-106">For more information about working with data in a report, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
##  <a name="the-ribbon"></a><a name="Ribbon"></a><span data-ttu-id="fd9b3-107">功能区</span><span class="sxs-lookup"><span data-stu-id="fd9b3-107">The Ribbon</span></span>  
 <span data-ttu-id="fd9b3-108">功能区可帮助您快速查找完成任务所需的命令。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-108">The Ribbon helps you quickly find the commands that you need to complete a task.</span></span> <span data-ttu-id="fd9b3-109">命令通过以下逻辑组进行组织：连接、数据集和查询设计器。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-109">Commands are organized into the following logical groups: Connection, Dataset, and Query Designer.</span></span>  
  
### <a name="connection"></a><span data-ttu-id="fd9b3-110">连接</span><span class="sxs-lookup"><span data-stu-id="fd9b3-110">Connection</span></span>  
 <span data-ttu-id="fd9b3-111">在“连接”组中使用 **“选择”** 按钮可以选择报表中的共享数据源，或浏览到报表服务器上的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-111">Use the **Select** button in the Connection group to select a shared data source in your report, or browse to a shared data source on the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd9b3-112">共享数据集必须基于共享数据源。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-112">A shared dataset must be based on a shared data source.</span></span> <span data-ttu-id="fd9b3-113">如果您需要的数据源不可用，那么您必须在报表服务器上创建一个数据源。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-113">If the data source that you need is not available, you must create one on the report server.</span></span> <span data-ttu-id="fd9b3-114">有关详细信息，请参阅联机丛书中的 Reporting Services 文档中的[创建、删除或修改共享数据源 &#40;报表管理器&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="fd9b3-115">有关详细信息，请参阅 [数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-115">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
### <a name="dataset"></a><span data-ttu-id="fd9b3-116">数据集</span><span class="sxs-lookup"><span data-stu-id="fd9b3-116">Dataset</span></span>  
 <span data-ttu-id="fd9b3-117">使用 **“Set 选项”** 按钮可以设置共享数据集属性。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-117">Use the **Set Options** button to set shared dataset properties.</span></span> <span data-ttu-id="fd9b3-118">其中包括：</span><span class="sxs-lookup"><span data-stu-id="fd9b3-118">These include the following:</span></span>  
  
-   <span data-ttu-id="fd9b3-119">字段。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-119">Fields.</span></span> <span data-ttu-id="fd9b3-120">可以向字段集合添加字段，或编辑其中的字段。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-120">You can add a field or edit a field in the field collection.</span></span>  
  
-   <span data-ttu-id="fd9b3-121">数据选项。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-121">Data options.</span></span> <span data-ttu-id="fd9b3-122">可以设置影响匹配条件和排序顺序的选项（例如区分大小写和排序规则）。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-122">You can set options that affect match criteria and sort order, such as case sensitivity and collation.</span></span>  
  
-   <span data-ttu-id="fd9b3-123">筛选器。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-123">Filters.</span></span> <span data-ttu-id="fd9b3-124">可以定义在从数据连接检索报表数据后限制这些数据的筛选器。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-124">You can define filters that limit the data in a report after it is retrieved from the data connection.</span></span>  
  
-   <span data-ttu-id="fd9b3-125">参数。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-125">Parameters.</span></span> <span data-ttu-id="fd9b3-126">可以添加参数或编辑参数选项。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-126">You can add a parameter or edit parameter options.</span></span> <span data-ttu-id="fd9b3-127">例如，您可以为每个参数指定默认值，以便能够在报表服务器上为这一共享数据集创建缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-127">For example, you can specify a default value for each parameter so that you can create a cache refresh plan for this shared dataset on the report server.</span></span>  
  
 <span data-ttu-id="fd9b3-128">您设置的值将成为共享数据集在报表服务器上的定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-128">The values that you set become part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="fd9b3-129">如果报表作者将此共享数据集包括在报表中，您指定的选项将应用于该数据集实例。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-129">When a report author includes this shared dataset in a report, the options that you specify apply to that dataset instance.</span></span>  
  
 <span data-ttu-id="fd9b3-130">在将共享数据集添加到报表后，报表作者可以覆盖以下选项：排序规则、区分大小写、区分重音、区分假名类型、区分全半角、小计。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-130">After a shared dataset is added to a report, a report author can override the following options: collation, case sensitivity, accent sensitivity, kanatype sensitivity, width sensitivity, subtotals.</span></span> <span data-ttu-id="fd9b3-131">他们还可以创建其他数据集筛选器来限制报表中的数据。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-131">They can also create additional dataset filters to limit the data in the report.</span></span>  
  
 <span data-ttu-id="fd9b3-132">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-132">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="fd9b3-133">有关缓存刷新计划的详细信息，请参阅联机丛书中 Reporting Services 文档中的[&#40;SSRS&#41;缓存共享数据集](../report-server/cache-shared-datasets-ssrs.md) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-133">For more information about cache refresh plans, see [Cache Shared Datasets &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
### <a name="query-designer"></a><span data-ttu-id="fd9b3-134">查询设计器</span><span class="sxs-lookup"><span data-stu-id="fd9b3-134">Query Designer</span></span>  
 <span data-ttu-id="fd9b3-135">使用查询设计器工具栏可以帮助您生成用于指定要通过数据连接检索的数据的查询。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-135">Use the query designer toolbar to help build a query that specifies which data to retrieve from the data connection.</span></span> <span data-ttu-id="fd9b3-136">您看到的工具栏取决于与通过数据连接获得的数据源类型相关联的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-136">The toolbar that you see depends on the query designer that is associated with the data source type from the data connection.</span></span>  
  
 <span data-ttu-id="fd9b3-137">有关详细信息，请参阅[从外部数据源添加数据 &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md)和[查询设计器 &#40;报表生成器&#41;](../query-designers-report-builder.md)中对应于数据源类型的主题。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-137">For more information, see the topic that corresponds to the data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) and [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md).</span></span>  
  

  
##  <a name="the-query-designer-surface"></a><a name="DesignSurface"></a><span data-ttu-id="fd9b3-138">查询设计器图面</span><span class="sxs-lookup"><span data-stu-id="fd9b3-138">The Query Designer Surface</span></span>  
 <span data-ttu-id="fd9b3-139">查询设计器可帮助您使用外部数据源所要求的语法来生成查询。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-139">A query designer helps you to build a query in the syntax that is required by the external data source.</span></span>  
  
 <span data-ttu-id="fd9b3-140">有些数据源类型提供了图形查询设计器，您可以使用这些设计器来浏览外部数据源中的元数据。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-140">Some data source types provide a graphical query designer that you can use to explore the metadata on an external data source.</span></span> <span data-ttu-id="fd9b3-141">您还可以通过互动方式将名称从元数据窗格拖动到查询设计图面，或通过互动方式选择要使用的名称。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-141">You can interactively drag names from the metadata pane to the query design surface, or interactively select the names to use.</span></span>  
  
 <span data-ttu-id="fd9b3-142">有些数据源类型支持基于文本的查询设计器，你可以使用此类查询设计器粘贴已在其他工具（例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]）中创建的查询。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-142">Some data source types support a text-based query designer that you can use to paste in queries that you have created in other tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="fd9b3-143">每种数据源类型都对将针对外部数据源进行的查询有特定的要求。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-143">Each data source type has specific requirements for the query that will work against the external data source.</span></span> <span data-ttu-id="fd9b3-144">有关详细信息，请参阅联机丛书中的 "&#41;" 文档中的 "[从外部数据源添加数据" 中 &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md)和[&#40;Reporting Services 支持的数据源](../create-deploy-and-manage-mobile-and-paginated-reports.md)"中的数据源类型对应的主题 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-144">For more information, see the topic that corresponds to the data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) and [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  

  
##  <a name="viewing-query-results"></a><a name="Results"></a><span data-ttu-id="fd9b3-145">查看查询结果</span><span class="sxs-lookup"><span data-stu-id="fd9b3-145">Viewing Query Results</span></span>  
 <span data-ttu-id="fd9b3-146">在共享数据集设计视图中，您要生成一个将在处理报表时通过数据连接检索数据的查询。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-146">In shared dataset design view, you are building a query that will retrieve data from the data connection when the report is processed.</span></span>  
  
 <span data-ttu-id="fd9b3-147">运行此查询可查看通过数据连接获取的示例数据，从而验证该查询是否返回您需要的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-147">Run the query to see example data from the data connection to verify that the query returns the type of data that you expect.</span></span> <span data-ttu-id="fd9b3-148">结果集中的列来自通过数据连接获取的数据架构的元数据。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-148">The columns in the result set come from the metadata for data schemas from the data connection.</span></span> <span data-ttu-id="fd9b3-149">列名成为数据集字段集合。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-149">The column names become the dataset field collection.</span></span> <span data-ttu-id="fd9b3-150">您在查询结果集中看到的数据值是设计时数据。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-150">The values of the data that you see in the query result set is design time data.</span></span> <span data-ttu-id="fd9b3-151">在将共享数据集另存为报表服务器上的共享数据集定义后，仅查询文本得到保存。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-151">After you save the shared dataset as a shared dataset definition on the report server, only the query text is saved.</span></span> <span data-ttu-id="fd9b3-152">查询结果集中的数据不会被保存。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-152">The data in the query result set is not saved.</span></span>  
  
 <span data-ttu-id="fd9b3-153">当报表作者将此共享数据集添加到报表中时，系统将在报表服务器上添加一个指向该数据集定义的指针。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-153">When a report author adds this shared dataset to a report, a pointer to the dataset definition on the report server is added.</span></span> <span data-ttu-id="fd9b3-154">在报表中，数据集字段集合显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-154">In the report, the dataset field collection appears in the Report Data pane.</span></span> <span data-ttu-id="fd9b3-155">查询文本不可用。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-155">The query text is not available.</span></span>  
  
 <span data-ttu-id="fd9b3-156">用于运行查询的凭据与用于从报表服务器预览报表或运行报表的凭据是分开的。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-156">The credentials that you use to run a query are separate from the credentials that are used to preview a report or to run a report from the report server.</span></span> <span data-ttu-id="fd9b3-157">有关详细信息，请参阅 [在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-157">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
### <a name="running-a-report-with-parameters"></a><span data-ttu-id="fd9b3-158">使用参数运行报表</span><span class="sxs-lookup"><span data-stu-id="fd9b3-158">Running a Report with Parameters</span></span>  
 <span data-ttu-id="fd9b3-159">如果查询包括查询变量，则系统将自动为您创建数据集参数。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-159">When your query includes query variables, dataset parameters are created automatically for you.</span></span> <span data-ttu-id="fd9b3-160">随后，在您生成了数据集查询后，系统将自动创建设置为数据集参数的报表参数。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-160">In turn, when you finish building the dataset query, report parameters that are set to dataset parameters are created automatically.</span></span>  
  
 <span data-ttu-id="fd9b3-161">如果报表中包含参数，则只有在所有参数都具有默认值的情况下，该报表才能自动运行。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-161">If a report contains parameters, all the parameters must have default values before the report can run automatically.</span></span> <span data-ttu-id="fd9b3-162">如果某个参数没有默认值，当运行报表时，必须为该参数选择一个值，然后在 **“运行”** 选项卡上单击 **“查看报表”** 。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-162">If a parameter does not have a default value, when you run the report you must choose a value for the parameter, and then click **View Report** on the **Run** tab.</span></span>  
  
 <span data-ttu-id="fd9b3-163">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-163">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  

  
##  <a name="saving-the-shared-dataset"></a><a name="Save"></a><span data-ttu-id="fd9b3-164">保存共享数据集</span><span class="sxs-lookup"><span data-stu-id="fd9b3-164">Saving the Shared Dataset</span></span>  
 <span data-ttu-id="fd9b3-165">若要保存生成的查询，请在 **“报表生成器”** 按钮上单击 **“保存”** 或 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-165">To save the query that you built, on the **Report Builder** button, click **Save** or **Save As**.</span></span> <span data-ttu-id="fd9b3-166">导航到报表服务器上的相应文件夹，然后保存共享数据集定义。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-166">Navigate to the appropriate folder on the report server and save the shared dataset definition.</span></span> <span data-ttu-id="fd9b3-167">在您将共享数据集保存到报表服务器后，其他用户才能使用此共享数据集。</span><span class="sxs-lookup"><span data-stu-id="fd9b3-167">The shared dataset is not available to others until you save it to the report server.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="fd9b3-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd9b3-168">See Also</span></span>  
 <span data-ttu-id="fd9b3-169">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fd9b3-169">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="fd9b3-170">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fd9b3-170">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fd9b3-171">报表参数（报表生成器和报表设计器）</span><span class="sxs-lookup"><span data-stu-id="fd9b3-171">Report Parameters &#40;Report Builder and Report Designer&#41;</span></span>](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
  
