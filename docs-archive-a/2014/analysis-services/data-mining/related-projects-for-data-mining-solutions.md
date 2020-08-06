---
title: 数据挖掘解决方案的相关项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dc26489a-4c27-4b89-8215-6d245427c350
author: minewiskan
ms.author: owend
ms.openlocfilehash: fc0f235871607363b436867d44affd561876bf1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590993"
---
# <a name="related-projects-for-data-mining-solutions"></a><span data-ttu-id="b05af-102">数据挖掘解决方案的相关项目</span><span class="sxs-lookup"><span data-stu-id="b05af-102">Related Projects for Data Mining Solutions</span></span>
  <span data-ttu-id="b05af-103">数据挖掘解决方案中至少要包含数据挖掘项目，该项目定义了数据源、数据源视图、挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="b05af-103">The minimum that is required for a data mining solution is the data mining project, which defines data sources, data source views, mining structures and mining models.</span></span> <span data-ttu-id="b05af-104">但是，在使用数据挖掘模型做出日常决策时，将数据挖掘与预测分析解决方案的其他部分集成非常重要，其中可包含以下过程和组成部分：</span><span class="sxs-lookup"><span data-stu-id="b05af-104">However, when data mining models are used in daily decision making, it is important that data mining be integrated with other part of a predictive analytics solution, which can include these processes and components:</span></span>  
  
-   <span data-ttu-id="b05af-105">准备和选择数据和变量。</span><span class="sxs-lookup"><span data-stu-id="b05af-105">Preparation and selection of data and of variables.</span></span> <span data-ttu-id="b05af-106">这一过程包括数据清除、元数据管理和多个数据源的集成，以及数据的转换、合并和数据到数据仓库的上载。</span><span class="sxs-lookup"><span data-stu-id="b05af-106">Includes data cleansing, metadata management and integration of multiple data sources, and the conversion, merging, and uploading of data into a data warehouse.</span></span>  
  
-   <span data-ttu-id="b05af-107">报告分析、呈现预测和审核/跟踪数据挖掘活动。</span><span class="sxs-lookup"><span data-stu-id="b05af-107">Reporting of analysis, presentation of predictions, and auditing/tracking of data mining activities.</span></span>  
  
-   <span data-ttu-id="b05af-108">使用多维模型或表格模型浏览发现的内容。</span><span class="sxs-lookup"><span data-stu-id="b05af-108">Using multidimensional models or tabular models to explore findings.</span></span>  
  
-   <span data-ttu-id="b05af-109">优化数据挖掘解决方案以支持新数据或根据当前分析在支持基础结构中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="b05af-109">Refinement of the data mining solution to support new data, or changes in the support infrastructure driven by current analysis.</span></span>  
  
 <span data-ttu-id="b05af-110">本主题介绍了 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的其他功能，这些功能通常是预测分析解决方案的一部分，用于支持数据准备和数据挖掘过程，或用于通过提供分析和操作工具为用户提供支持。</span><span class="sxs-lookup"><span data-stu-id="b05af-110">This topic describes the other features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are often part of a predictive analytics solution, either to support the processes of data preparation and data mining, or to support users by providing tools for analysis and action.</span></span>  
  
 [<span data-ttu-id="b05af-111">Integration Services</span><span class="sxs-lookup"><span data-stu-id="b05af-111">Integration Services</span></span>](#bkmk_SSIS)  
  
 [<span data-ttu-id="b05af-112">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b05af-112">Reporting Services</span></span>](#bkmk_SSRS)  
  
 [<span data-ttu-id="b05af-113">Data Quality Service</span><span class="sxs-lookup"><span data-stu-id="b05af-113">Data Quality Service</span></span>](#bkmk_DQSetc)  
  
 [<span data-ttu-id="b05af-114">全文搜索</span><span class="sxs-lookup"><span data-stu-id="b05af-114">Full-Text Search</span></span>](#bkmk_FTSetc)  
  
 [<span data-ttu-id="b05af-115">语义索引</span><span class="sxs-lookup"><span data-stu-id="b05af-115">Semantic Indexing</span></span>](#bkmk_SemSearch)  
  
##  <a name="sql-server-integration-services"></a><a name="bkmk_SSIS"></a><span data-ttu-id="b05af-116">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="b05af-116">SQL Server Integration Services</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="b05af-117">提供数据挖掘项目的数据准备和定型阶段所需的组件和功能。</span><span class="sxs-lookup"><span data-stu-id="b05af-117">provides components and features that are required for the data preparation and training phases of a data mining project.</span></span> <span data-ttu-id="b05af-118">虽然您可使用其他工具（如脚本）执行很多数据清除或准备任务，但 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 在数据挖掘方面具有众多优势：</span><span class="sxs-lookup"><span data-stu-id="b05af-118">Although you can perform many data cleansing or preparation tasks by using other tools, such as scripts, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] has numerous advantages for data mining:</span></span>  
  
-   <span data-ttu-id="b05af-119">将任务表示为工作流的一部分，可对其进行重复、自动化、分支或扩展。</span><span class="sxs-lookup"><span data-stu-id="b05af-119">Represents tasks as part of a workflow, which can be repeated, automated, branched, and extended.</span></span>  
  
-   <span data-ttu-id="b05af-120">为审核提供了广泛支持，还为捕获错误和记录事件提供了多种方式。</span><span class="sxs-lookup"><span data-stu-id="b05af-120">Provides extensive support for auditing and multiple ways of capturing errors and logging events.</span></span>  
  
     <span data-ttu-id="b05af-121">除了捕获数据沿袭，还可通过数据转换管道监视数据的更改。</span><span class="sxs-lookup"><span data-stu-id="b05af-121">In addition to capturing data lineage, you can monitor changes to the data throughout the data transformation pipeline.</span></span>  
  
     <span data-ttu-id="b05af-122">还可将 SSIS 工作流与支持变更数据捕获功能的 SQL Server 功能集成。</span><span class="sxs-lookup"><span data-stu-id="b05af-122">You can also integrate your SSIS workflows with the features that support Change Data Capture functionality in SQL Server.</span></span>  
  
-   <span data-ttu-id="b05af-123">可将数据挖掘合并到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 工作流中，以将传入数据合理地分离到多个表中。</span><span class="sxs-lookup"><span data-stu-id="b05af-123">Data mining can be incorporated in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] workflow, to intelligently separate incoming data into multiple tables.</span></span> <span data-ttu-id="b05af-124">例如，您可使用预测查询将新客户拆分为不同的组以在邮递活动中设定目标。</span><span class="sxs-lookup"><span data-stu-id="b05af-124">For example, you could use a prediction query to split new customers into different groups for targeting in a mailing campaign.</span></span>  
  
 <span data-ttu-id="b05af-125">以下列表提供了指向 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件的链接，这些组件广泛用于支持数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="b05af-125">The following lists provide links to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that are most widely used in support of data mining.</span></span>  
  
 <span data-ttu-id="b05af-126">**控制流组件**</span><span class="sxs-lookup"><span data-stu-id="b05af-126">**Control Flow Components**</span></span>  
  
-   [<span data-ttu-id="b05af-127">Analysis Services 执行 DDL 任务</span><span class="sxs-lookup"><span data-stu-id="b05af-127">Analysis Services Execute DDL Task</span></span>](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="b05af-128">Analysis Services 处理任务</span><span class="sxs-lookup"><span data-stu-id="b05af-128">Analysis Services Processing Task</span></span>](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="b05af-129">CDC Control Task</span><span class="sxs-lookup"><span data-stu-id="b05af-129">CDC Control Task</span></span>](../../integration-services/control-flow/cdc-control-task.md)  
  
-   [<span data-ttu-id="b05af-130">数据清理</span><span class="sxs-lookup"><span data-stu-id="b05af-130">Data Cleansing</span></span>](../../data-quality-services/data-cleansing.md)  
  
-   [<span data-ttu-id="b05af-131">数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="b05af-131">Data Mining Query Task</span></span>](../../integration-services/control-flow/data-mining-query-task.md)  
  
-   [<span data-ttu-id="b05af-132">数据事件探查任务</span><span class="sxs-lookup"><span data-stu-id="b05af-132">Data Profiling Task</span></span>](../../integration-services/control-flow/data-profiling-task.md)  
  
 <span data-ttu-id="b05af-133">**数据流组件**</span><span class="sxs-lookup"><span data-stu-id="b05af-133">**Data Flow Components**</span></span>  
  
-   [<span data-ttu-id="b05af-134">CDC 流组件</span><span class="sxs-lookup"><span data-stu-id="b05af-134">CDC Flow Components</span></span>](../../integration-services/data-flow/cdc-flow-components.md)  
  
-   [<span data-ttu-id="b05af-135">有条件拆分转换</span><span class="sxs-lookup"><span data-stu-id="b05af-135">Conditional Split Transformation</span></span>](../../integration-services/data-flow/transformations/conditional-split-transformation.md)  
  
-   [<span data-ttu-id="b05af-136">数据转换</span><span class="sxs-lookup"><span data-stu-id="b05af-136">Data Conversion Transformation</span></span>](../../integration-services/data-flow/transformations/data-conversion-transformation.md)  
  
-   [<span data-ttu-id="b05af-137">数据挖掘模型定型目标</span><span class="sxs-lookup"><span data-stu-id="b05af-137">Data Mining Model Training Destination</span></span>](../../integration-services/data-flow/data-mining-model-training-destination.md)  
  
-   [<span data-ttu-id="b05af-138">数据挖掘查询转换</span><span class="sxs-lookup"><span data-stu-id="b05af-138">Data Mining Query Transformation</span></span>](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)  
  
-   [<span data-ttu-id="b05af-139">派生列转换</span><span class="sxs-lookup"><span data-stu-id="b05af-139">Derived Column Transformation</span></span>](../../integration-services/data-flow/transformations/derived-column-transformation.md)  
  
-   [<span data-ttu-id="b05af-140">百分比抽样转换</span><span class="sxs-lookup"><span data-stu-id="b05af-140">Percentage Sampling Transformation</span></span>](../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
-   [<span data-ttu-id="b05af-141">字词提取转换</span><span class="sxs-lookup"><span data-stu-id="b05af-141">Term Extraction Transformation</span></span>](../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
-   [<span data-ttu-id="b05af-142">字词查找转换</span><span class="sxs-lookup"><span data-stu-id="b05af-142">Term Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
##  <a name="sql-server-reporting-services"></a><a name="bkmk_SSRS"></a> <span data-ttu-id="b05af-143">SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b05af-143">SQL Server Reporting Services</span></span>  
 <span data-ttu-id="b05af-144">虽然 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 通常不会被视为数据挖掘解决方案的重要组件，但它提供的以下功能对演示数据挖掘解决方案很有用。</span><span class="sxs-lookup"><span data-stu-id="b05af-144">Although [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is typically not seen as a critical component of data mining solutions, it provides the following features that are useful for presentation of data mining solutions.</span></span>  
  
-   <span data-ttu-id="b05af-145">在复杂报表中集成来自多个源的数据。</span><span class="sxs-lookup"><span data-stu-id="b05af-145">Integration of data from multiple sources in complex reports.</span></span> <span data-ttu-id="b05af-146">为分析人员创建对模型内容的查询，并创建为最终用户显示预测和趋势的报表。</span><span class="sxs-lookup"><span data-stu-id="b05af-146">Create queries against the model content for analysts, and reports that show predictions and trends for end users.</span></span>  
  
-   <span data-ttu-id="b05af-147">用于创建可让用户直接对现有挖掘模型进行查询的报表的功能。</span><span class="sxs-lookup"><span data-stu-id="b05af-147">The ability to create a report that lets users directly query against an existing mining model.</span></span>  
  
-   <span data-ttu-id="b05af-148">与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]集成，以支持对从 OLAP 模型创建的数据挖掘维度和数据挖掘多维数据集的钻取和浏览。</span><span class="sxs-lookup"><span data-stu-id="b05af-148">Integration with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], to support drillthrough and exploration of data mining dimensions and data mining cubes created from OLAP models.</span></span>  
  
-   <span data-ttu-id="b05af-149">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中可用的参数化和格式化功能。</span><span class="sxs-lookup"><span data-stu-id="b05af-149">parameterization and formatting features that are available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b05af-150">有关如何将 Reporting Services 作为数据源与 DMX 查询一起使用的详细信息，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="b05af-150">For more information about how to use Reporting Services with DMX queries as a data source, see these links:</span></span>  
  
 [<span data-ttu-id="b05af-151">从数据挖掘模型检索数据 (DMX) (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b05af-151">Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md)  
  
 [<span data-ttu-id="b05af-152">Analysis Services DMX 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="b05af-152">Analysis Services DMX Query Designer User Interface</span></span>](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
 [<span data-ttu-id="b05af-153">针对 DMX 的 Analysis Services 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b05af-153">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)  
  
 <span data-ttu-id="b05af-154">但是，不需要将 DMX 用作数据源。</span><span class="sxs-lookup"><span data-stu-id="b05af-154">However, it is not necessary to use DMX as the data source.</span></span> <span data-ttu-id="b05af-155">用于数据挖掘的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件还支持将预测查询的结果保存到关系数据库中。</span><span class="sxs-lookup"><span data-stu-id="b05af-155">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components for data mining also support saving the results of a prediction query to a relational database.</span></span> <span data-ttu-id="b05af-156">如果已建立用于使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]更新模型的工作流，则将预测和其他数据挖掘查询结果保存到 SQL Server 可使您能够使用 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 进行报告，并能使用其他不与 DMX 建立接口连接的工具。</span><span class="sxs-lookup"><span data-stu-id="b05af-156">If you have an established workflow for updating models using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], persisting predictions and other data mining query results to SQL Server enable you to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] for reporting, as well as other tools that do not interface with DMX.</span></span>  
  
 <span data-ttu-id="b05af-157">有关将 Reporting Services 用作数据源的表示层的详细信息，请参阅 [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-157">For more information about using Reporting Services as the presentation layer for data sources, see [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md).</span></span>  
  
##  <a name="data-quality-services"></a><a name="bkmk_DQSetc"></a><span data-ttu-id="b05af-158">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="b05af-158">Data Quality Services</span></span>  
 <span data-ttu-id="b05af-159">Data Quality Services (DQS) 是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的新增功能。</span><span class="sxs-lookup"><span data-stu-id="b05af-159">Data Quality Services (DQS) is new in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b05af-160">由于数据问题会导致无法进行数据挖掘，因此执行重复分析或在具有复杂数据源的大型组织中工作的数据挖掘人员应会发现，使用 DQS 的规划良好的数据项目是一种支持数据挖掘的解决方案，它比使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或其他脚本的即席数据清除更为可靠。</span><span class="sxs-lookup"><span data-stu-id="b05af-160">Because data problems can make data mining impossible, data miners who perform repeated analysis or who work in large organizations with complex data sources are expected to find that a well-planned data project using DQS is a more reliable solution for support of data mining than ad hoc cleansing of data using [!INCLUDE[tsql](../../includes/tsql-md.md)] or other scripts.</span></span>  
  
 <span data-ttu-id="b05af-161">应考虑将以下 DQS 功能用于数据挖掘解决方案中的数据准备和数据集成。</span><span class="sxs-lookup"><span data-stu-id="b05af-161">The following features of DQS should be considered for data preparation and data integrity in a data mining solution.</span></span>  
  
 <span data-ttu-id="b05af-162">**计算机辅助的数据清除过程，该过程可分析源数据并提出更改建议。**</span><span class="sxs-lookup"><span data-stu-id="b05af-162">**A computer-assisted data cleansing process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="b05af-163">DQS 会将源数据与数据质量提供程序维护和保护的基于云的引用数据进行比较。</span><span class="sxs-lookup"><span data-stu-id="b05af-163">DQS can compare source data with cloud-based reference data maintained and guaranteed by data quality providers.</span></span>  
  
 <span data-ttu-id="b05af-164">DQS 还会分析原始源数据并从用户数据中创建知识库。</span><span class="sxs-lookup"><span data-stu-id="b05af-164">DQS can also analyze raw source data and create a knowledge base from user data.</span></span> <span data-ttu-id="b05af-165">将对处理后的数据进行分类，然后向用户显示以供进一步处理。</span><span class="sxs-lookup"><span data-stu-id="b05af-165">The processed data is categorized and then displayed to the user for further processing.</span></span> <span data-ttu-id="b05af-166">清除过程是交互式的，意味着数据专员可批准、拒绝或修改计算机辅助的数据清除过程建议的数据。</span><span class="sxs-lookup"><span data-stu-id="b05af-166">The cleansing process is interactive, meaning the data steward can approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="b05af-167">可通过此过程获得一个知识库，可以持续改进该知识库或在多个数据增强阶段中重复使用它。</span><span class="sxs-lookup"><span data-stu-id="b05af-167">The outcome of the process is a knowledge base that you can continuously improve, or reuse in multiple data-enhancement phases.</span></span>  
  
 <span data-ttu-id="b05af-168">有关详细信息，请参阅 [Data Cleansing](../../data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-168">For more information, see [Data Cleansing](../../data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="b05af-169">**计算机辅助的匹配过程，该过程可分析源数据并提出更改建议。**</span><span class="sxs-lookup"><span data-stu-id="b05af-169">**A computer-assisted matching process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="b05af-170">若要防止数据重复，您可对数据源执行额外清除，以标识精确匹配项和近似匹配项。</span><span class="sxs-lookup"><span data-stu-id="b05af-170">To prevent data duplication, you can perform addition cleansing of the data source, to identify exact and approximate matches.</span></span> <span data-ttu-id="b05af-171">利用这些组件，您可指定匹配规则和应用规则的阈值。</span><span class="sxs-lookup"><span data-stu-id="b05af-171">These components let you specify the matching rules, and the thresholds at which to apply them.</span></span>  
  
 <span data-ttu-id="b05af-172">通过查找数据匹配项，您可删除重复项，从而解决这一数据挖掘问题。</span><span class="sxs-lookup"><span data-stu-id="b05af-172">By finding data matches, you can remove duplicates, which can be a problem for data mining.</span></span> <span data-ttu-id="b05af-173">消除数据重复不会自动进行；数据专员和 IT 专业人员必须对知识库中的知识和要对数据进行的更改进行验证。</span><span class="sxs-lookup"><span data-stu-id="b05af-173">Data de-duplication is not automatic; the data steward or IT professional must verify both the knowledge in the knowledge base and the changes to be made to the data.</span></span>  
  
 <span data-ttu-id="b05af-174">创建初始 DQS 项目之后，可使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件实现许多任务的自动化。</span><span class="sxs-lookup"><span data-stu-id="b05af-174">After you have created the initial DQS project, you can automate many of the tasks by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>  
  
 <span data-ttu-id="b05af-175">有关详细信息，请参阅 [Data Matching](../../data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-175">For more information, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
 <span data-ttu-id="b05af-176">在数据质量项目中执行清除和匹配活动时，可获得与 DQS 处理的数据有关的实时统计信息和其他信息。</span><span class="sxs-lookup"><span data-stu-id="b05af-176">While performing cleansing and matching activities in a data quality project, you can get real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="b05af-177">数据事件探查可帮助您评估数据清除或数据匹配在多大程度上帮助提高数据质量，并理解已做的更改。</span><span class="sxs-lookup"><span data-stu-id="b05af-177">Data profiling helps you assess the extent to which data cleansing or matching helped improve the data quality, and understand the changes that were made.</span></span> <span data-ttu-id="b05af-178">有关数据事件探查和通知的信息，请参阅 [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-178">For information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
 <span data-ttu-id="b05af-179">**一个表示以下三种类型的知识的知识库：现有知识、DQS 服务器生成的知识和用户生成的知识。**</span><span class="sxs-lookup"><span data-stu-id="b05af-179">**A knowledge base that represents three types of knowledge: out-of-the-box knowledge, knowledge generated by the DQS server, and knowledge generated by the user.**</span></span>  
 <span data-ttu-id="b05af-180">创建知识库之后，您可使用它反复清除和验证其他数据。</span><span class="sxs-lookup"><span data-stu-id="b05af-180">Once you have created a knowledge base, you can use it iteratively to cleanse and verify other data.</span></span>  
  
 <span data-ttu-id="b05af-181">您可将来自多个源的新数据导入知识库中，这些数据是来自引用提供程序的已知干净数据，或与知识库中现有数据匹配的原始数据。</span><span class="sxs-lookup"><span data-stu-id="b05af-181">You can import new data into the knowledge base data from multiple sources, either known clean data from reference providers, or raw data that is matched to existing data in the knowledge base.</span></span>  
  
 <span data-ttu-id="b05af-182">有关数据质量项目中的清除活动的详细信息，请参阅数据清除 (DQS)。</span><span class="sxs-lookup"><span data-stu-id="b05af-182">For detailed information about the cleansing activity in a data quality project, see Data Cleansing (DQS).</span></span>  
  
 <span data-ttu-id="b05af-183">还可将知识库中的知识应用于其他源，以在其他进程中执行数据清除。</span><span class="sxs-lookup"><span data-stu-id="b05af-183">You can also apply the knowledge in the knowledge base to other sources, to perform data cleansing within other processes.</span></span> <span data-ttu-id="b05af-184">此类数据清除可帮助标识用户输入错误、传输或存储过程中的数据损坏或不匹配的数据字典定义。</span><span class="sxs-lookup"><span data-stu-id="b05af-184">Such data cleansing can help identify user entry errors, corruption in transmission or storage, or mismatched data dictionary definitions.</span></span>  
  
 <span data-ttu-id="b05af-185">有关详细信息，请参阅 [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-185">For more information, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
##  <a name="full-text-search"></a><a name="bkmk_FTSetc"></a><span data-ttu-id="b05af-186">全文搜索</span><span class="sxs-lookup"><span data-stu-id="b05af-186">Full-Text Search</span></span>  
 <span data-ttu-id="b05af-187">SQL Server 中的全文搜索为应用程序和用户提供了对 SQL Server 表中基于字符的数据运行全文查询的功能。</span><span class="sxs-lookup"><span data-stu-id="b05af-187">Full-Text Search in SQL Server lets applications and users run full-text queries against character-based data in SQL Server tables.</span></span> <span data-ttu-id="b05af-188">启用全文搜索后，可对由有关多种形式的词或短语的语言特定的规则增强的文本数据执行搜索。</span><span class="sxs-lookup"><span data-stu-id="b05af-188">When full-text search is enabled, you can perform searches against text data that are enhanced by language-specific rules about the multiple forms of a word or phrase.</span></span> <span data-ttu-id="b05af-189">还可配置搜索条件（如多个字词之间的距离），使用函数约束按可能性顺序返回的结果。</span><span class="sxs-lookup"><span data-stu-id="b05af-189">You can also configure search conditions, such as the distance between multiple terms, and use functions to constrain the results that are returned in order of likelihood.</span></span>  
  
 <span data-ttu-id="b05af-190">由于全文查询是 SQL Server 引擎所提供的一项功能，因此，您可对文本数据源使用全文搜索来创建参数化查询、生成自定义数据集或字词向量，并在数据挖掘中使用这些源。</span><span class="sxs-lookup"><span data-stu-id="b05af-190">Because full-text queries are a feature provided by the SQL Server engine, you can create parameterized queries, generate custom data sets or term vectors by using full-text search features on a text data source, and use these sources in data mining.</span></span>  
  
 <span data-ttu-id="b05af-191">有关如何将全文查询用于全文检索的详细信息，请参阅 [使用全文搜索查询](../../relational-databases/search/query-with-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-191">For more information about how full-text queries interact with the full-text index, see [Query with Full-Text Search](../../relational-databases/search/query-with-full-text-search.md).</span></span>  
  
 <span data-ttu-id="b05af-192">使用 SQL Server 全文搜索功能的好处是，您可利用所有 SQL Server 语言附带的断字符和词干分析器中包含的语言智能。</span><span class="sxs-lookup"><span data-stu-id="b05af-192">An advantage of using the full-text search features of SQL Server is that you can leverage the linguistic intelligence that is contained in the word breakers and stemmers shipped for all SQL Server languages.</span></span> <span data-ttu-id="b05af-193">通过使用提供的断字符和词干分析器，您可确保使用适用于每种语言的字符分隔字词，并且不会忽略基于标注字符或拼字变体（如日语中的多种数字格式）的同义词。</span><span class="sxs-lookup"><span data-stu-id="b05af-193">By using the supplied word breakers and stemmers, you can ensure that words are separated using the characters appropriate for each language, and that synonyms based on diacritics or orthographic variations (such as the multiple number formats in Japanese) are not overlooked.</span></span>  
  
 <span data-ttu-id="b05af-194">除了控制词边界的语言智能之外，每种语言的词干分析器还可基于对应语言中的语态和拼字变体规则的知识，将词的变体减少至单个字词。</span><span class="sxs-lookup"><span data-stu-id="b05af-194">In addition to linguistic intelligence that governs word boundaries, the stemmers for each language can reduce variants of a word to a single term, based on knowledge of the rules for conjugation and orthographic variation in that language.</span></span> <span data-ttu-id="b05af-195">每种语言的语言分析规则各不相同，这些规则是根据对实际公司所做的大量调研来制定的。</span><span class="sxs-lookup"><span data-stu-id="b05af-195">The rules for linguistic analysis differ for each language and are developed based on extensive research on real-life corpora.</span></span>  
  
 <span data-ttu-id="b05af-196">有关详细信息，请参阅 [配置和管理断字符和词干分析器以便搜索](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-196">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
 <span data-ttu-id="b05af-197">全文检索后存储的词的版本是一个压缩格式的标记。</span><span class="sxs-lookup"><span data-stu-id="b05af-197">The version of a word that is stored after full-text indexing is a token in compressed form.</span></span> <span data-ttu-id="b05af-198">对全文检索进行的后续查询将基于相应的语言规则生成特定词的多种变形形式，以确保生成所有可能的匹配项。</span><span class="sxs-lookup"><span data-stu-id="b05af-198">Subsequent queries to the full-text index generate multiple inflectional forms of a particular word based on the rules of that language, to ensure that all probable matches are made.</span></span> <span data-ttu-id="b05af-199">例如，尽管存储的标记可能为 "run"，查询引擎也会查找术语 "正在运行"、"已运行" 和 "运行程序"，因为这些术语是语形学的根词 "run" 的变体。</span><span class="sxs-lookup"><span data-stu-id="b05af-199">For example, although the token that is stored might be "run", the query engine also looks for the terms "running", "ran", and "runner," because these are regularly derived morphological variations of the root word "run".</span></span>  
  
 <span data-ttu-id="b05af-200">还可以创建和生成用户同义词库以存储同义词并获得更佳搜索结果，或对字词进行分类。</span><span class="sxs-lookup"><span data-stu-id="b05af-200">You can also create and build a user thesaurus to store synonyms and enable better search results, or categorization of terms.</span></span> <span data-ttu-id="b05af-201">通过开发针对全文数据定制的同义词库，您可以有效地扩大对这些数据的全文查询的范围。</span><span class="sxs-lookup"><span data-stu-id="b05af-201">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="b05af-202">有关详细信息，请参阅 [为全文搜索配置和管理同义词库文件](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-202">For more information, see [Configure and Manage Thesaurus Files for Full-Text Search](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="b05af-203">使用全文搜索的要求包括：</span><span class="sxs-lookup"><span data-stu-id="b05af-203">Requirements for using full-text search include the following:</span></span>  
  
-   <span data-ttu-id="b05af-204">数据库管理员必须对表创建全文检索。</span><span class="sxs-lookup"><span data-stu-id="b05af-204">The database administrator must create a full-text index on the table.</span></span>  
  
-   <span data-ttu-id="b05af-205">每个表只允许有一个全文索引。</span><span class="sxs-lookup"><span data-stu-id="b05af-205">Only one full-text index is allowed per table.</span></span>  
  
-   <span data-ttu-id="b05af-206">您为其编制索引的每个列均必须有一个唯一键。</span><span class="sxs-lookup"><span data-stu-id="b05af-206">Each column that you index must have a unique key.</span></span>  
  
-   <span data-ttu-id="b05af-207">仅包含以下数据类型的列支持全文检索：char、varchar、nchar、nvarchar、text、ntext、image、xml、varbinary 和 varbinary(max)。</span><span class="sxs-lookup"><span data-stu-id="b05af-207">Full-text indexing is supported only for columns with these data types: char, varchar, nchar, nvarchar, text, ntext, image, xml, varbinary, and varbinary(max).</span></span> <span data-ttu-id="b05af-208">如果列为 varbinary、varbinary(max)、image 或 xml，则您必须在单独的类型列中指定可编制索引的文档的文件扩展名（.doc、.pdf、.xls 等）。</span><span class="sxs-lookup"><span data-stu-id="b05af-208">If the column is varbinary, varbinary(max), image, or xml, you must specify the file extension of the indexable document (.doc, .pdf, .xls, and so forth), in a separate type column.</span></span>  
  
##  <a name="semantic-indexing"></a><a name="bkmk_SemSearch"></a><span data-ttu-id="b05af-209">语义索引</span><span class="sxs-lookup"><span data-stu-id="b05af-209">Semantic Indexing</span></span>  
 <span data-ttu-id="b05af-210">语义搜索以 SQL Server 中现有的全文搜索功能为基础，但使用其他功能和统计信息来启用方案（如相关文档的自动关键字提取和发现）。</span><span class="sxs-lookup"><span data-stu-id="b05af-210">Semantic search builds upon the existing full-text search features in SQL Server, but uses additional capabilities and statistics to enable scenarios such as automatic keyword extraction and discovery of related documents.</span></span> <span data-ttu-id="b05af-211">例如，您可以使用语义搜索来建立一个组织的基本分类，或对文档集进行分类。</span><span class="sxs-lookup"><span data-stu-id="b05af-211">For example, you might use semantic search to build a base taxonomy for an organization, or classify a corpus of documents.</span></span> <span data-ttu-id="b05af-212">您也可在聚类分析或决策树模型中将提取的字词和文档相似性得分组合使用。</span><span class="sxs-lookup"><span data-stu-id="b05af-212">Or, you could use the combination of extracted terms and document similarity scores in clustering or decision tree models.</span></span>  
  
 <span data-ttu-id="b05af-213">在成功启用语义搜索并为数据列编制索引后，您可将本机提供的函数与语义索引一起使用来执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b05af-213">After you have enabled semantic search successfully, and indexed your data columns, you can use the functions that are provided natively with semantic indexing to do the following:</span></span>  
  
-   <span data-ttu-id="b05af-214">返回单个词关键短语及其得分。</span><span class="sxs-lookup"><span data-stu-id="b05af-214">Return single-word key phrases with their score.</span></span>  
  
-   <span data-ttu-id="b05af-215">返回包含指定的关键词短语的文档。</span><span class="sxs-lookup"><span data-stu-id="b05af-215">Return documents that contain a specified key phrase.</span></span>  
  
-   <span data-ttu-id="b05af-216">返回相似性得分和影响得分的词语。</span><span class="sxs-lookup"><span data-stu-id="b05af-216">Return similarity scores, and the terms that contribute to the score.</span></span>  
  
 <span data-ttu-id="b05af-217">有关详细信息，请参阅 [使用语义搜索在文档中查找关键短语](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) 和 [使用语义搜索查找相似和相关文档](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-217">For more information, see [Find Key Phrases in Documents with Semantic Search](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
 <span data-ttu-id="b05af-218">有关支持语义索引的数据库对象的详细信息，请参阅 [对表和列启用语义搜索](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="b05af-218">For more information about the database objects that support semantic indexing, see [Enable Semantic Search on Tables and Columns](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md).</span></span>  
  
 <span data-ttu-id="b05af-219">使用语义搜索的要求包括：</span><span class="sxs-lookup"><span data-stu-id="b05af-219">Requirements for using semantic search include the following:</span></span>  
  
-   <span data-ttu-id="b05af-220">同时启用全文搜索。</span><span class="sxs-lookup"><span data-stu-id="b05af-220">Full-text search also be enabled.</span></span>  
  
-   <span data-ttu-id="b05af-221">安装语义搜索组件还会创建特殊系统数据库，不能重命名、更改或替换该数据库。</span><span class="sxs-lookup"><span data-stu-id="b05af-221">Installation of the semantic search components also creates a special system database, which cannot be renamed, altered, or replaced.</span></span>  
  
-   <span data-ttu-id="b05af-222">使用该服务编制索引的文档必须存储到 SQL Server 上的支持全文检索（包括表和索引视图）的任何数据库对象中。</span><span class="sxs-lookup"><span data-stu-id="b05af-222">Documents that you index using the service must be stored in SQL Server, in any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="b05af-223">不是所有的全文语言都支持语义索引。</span><span class="sxs-lookup"><span data-stu-id="b05af-223">Not all of the full-text languages support semantic indexing.</span></span> <span data-ttu-id="b05af-224">有关支持的语言的列表，请参阅 [sys.fulltext_semantic_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b05af-224">For a list of supported languages, see [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05af-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b05af-225">See Also</span></span>  
 <span data-ttu-id="b05af-226">[&#40;SSAS&#41;的多维模型解决方案](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="b05af-226">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="b05af-227">表格模型解决方案（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="b05af-227">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
  
