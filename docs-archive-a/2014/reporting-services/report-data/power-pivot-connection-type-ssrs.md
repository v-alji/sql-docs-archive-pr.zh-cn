---
title: PowerPivot 连接类型 (SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08ce995afa7d458e8ce3ae50a9f572a086a3c697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694268"
---
# <a name="powerpivot-connection-type-ssrs"></a><span data-ttu-id="23d76-102">PowerPivot 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="23d76-102">PowerPivot Connection Type (SSRS)</span></span>
  <span data-ttu-id="23d76-103">可以使用 SQL Server Analysis Services 数据处理扩展插件从在 SharePoint PowerPivot 库中发布的 PowerPivot 工作簿检索数据。</span><span class="sxs-lookup"><span data-stu-id="23d76-103">You can use SQL Server Analysis Services data processing extension to retrieve data from a PowerPivot workbook that is published in a SharePoint PowerPivot Gallery.</span></span>  
  
 <span data-ttu-id="23d76-104">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="23d76-104">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="23d76-105">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="23d76-105">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="23d76-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="23d76-106">Prerequisites</span></span>  
 <span data-ttu-id="23d76-107">PowerPivot 数据源必须发布在 SharePoint 站点上的 PowerPivot 库中。</span><span class="sxs-lookup"><span data-stu-id="23d76-107">The PowerPivot data source must be published in a PowerPivot Gallery on a SharePoint site.</span></span>  
  
 <span data-ttu-id="23d76-108">为了支持从报表生成器到 PowerPivot 工作簿的连接，您在工作站计算机上必须具有 SQL Server 2008 R2 ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="23d76-108">To support connections from Report Builder to a PowerPivot workbook, you must have SQL Server 2008 R2 ADOMD.NET on your workstation computer.</span></span> <span data-ttu-id="23d76-109">此客户端库与 PowerPivot for Excel 一起安装，但如果您使用的计算机没有此应用程序，则必须从[SQL Server 2008 R2 功能包](https://www.microsoft.com/download/details.aspx?id=44272)下载和安装 ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="23d76-109">This client library is installed with PowerPivot for Excel, but if you are using a computer that does not have this application, you must download and install ADOMD.NET from the [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
## <a name="data-source-type"></a><span data-ttu-id="23d76-110">数据源类型</span><span class="sxs-lookup"><span data-stu-id="23d76-110">Data Source Type</span></span>  
 <span data-ttu-id="23d76-111">使用报表数据源类型： **Microsoft SQL Server Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="23d76-111">Use report data source type **Microsoft SQL Server Analysis Services**.</span></span>  
  
## <a name="connection-string"></a><span data-ttu-id="23d76-112">连接字符串</span><span class="sxs-lookup"><span data-stu-id="23d76-112">Connection String</span></span>  
 <span data-ttu-id="23d76-113">连接字符串是在 PowerPivot 库或其他库中的 SharePoint 上发布的 PowerPivot 工作簿的 URL，例如 http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx 。</span><span class="sxs-lookup"><span data-stu-id="23d76-113">The connection string is the URL to PowerPivot workbook published on SharePoint in the PowerPivot Gallery or other library, for example, http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx.</span></span>  
  
## <a name="credentials"></a><span data-ttu-id="23d76-114">凭据</span><span class="sxs-lookup"><span data-stu-id="23d76-114">Credentials</span></span>  
 <span data-ttu-id="23d76-115">指定您访问 PowerPivot 工作簿和 SharePoint 站点所需的凭据，例如 Windows 身份验证（集成安全性）。</span><span class="sxs-lookup"><span data-stu-id="23d76-115">Specify the credentials that you need to access the PowerPivot workbook and SharePoint site, for example, Windows Authentication (Integrated Security).</span></span> <span data-ttu-id="23d76-116">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="23d76-116">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="queries"></a><span data-ttu-id="23d76-117">查询</span><span class="sxs-lookup"><span data-stu-id="23d76-117">Queries</span></span>  
 <span data-ttu-id="23d76-118">在连接到 PowerPivot 数据源之后，使用 MDX 图形查询，通过从基础数据结构中浏览并进行选择来生成查询。</span><span class="sxs-lookup"><span data-stu-id="23d76-118">After you connect to the PowerPivot data source, use the MDX graphical query to build a query by browsing and selecting from the underlying data structures.</span></span> <span data-ttu-id="23d76-119">生成查询后，运行该查询在“结果”窗格中查看示例数据。</span><span class="sxs-lookup"><span data-stu-id="23d76-119">After you build a query, run the query to see sample data in the results pane.</span></span>  
  
 <span data-ttu-id="23d76-120">查询设计器将对查询进行分析，以确定数据集字段。</span><span class="sxs-lookup"><span data-stu-id="23d76-120">The query designer analyzes the query to determine the dataset fields.</span></span> <span data-ttu-id="23d76-121">您也可以在 **“报表数据”** 窗格中手动编辑数据集字段集合。</span><span class="sxs-lookup"><span data-stu-id="23d76-121">You can also manually edit the dataset field collection in the **Report Data** pane.</span></span> <span data-ttu-id="23d76-122">有关详细信息，请参阅[在“报表数据”窗格中添加、编辑和刷新字段（报表生成器和 SSRS）](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="23d76-122">For more information, see [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
## <a name="filters"></a><span data-ttu-id="23d76-123">筛选器</span><span class="sxs-lookup"><span data-stu-id="23d76-123">Filters</span></span>  
 <span data-ttu-id="23d76-124">在“筛选器”窗格中，指定要在查询结果中排除或包含的维度和成员。</span><span class="sxs-lookup"><span data-stu-id="23d76-124">In the Filters pane, specify dimensions and members to filter out or to include in the query results.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="23d76-125">parameters</span><span class="sxs-lookup"><span data-stu-id="23d76-125">Parameters</span></span>  
 <span data-ttu-id="23d76-126">在“筛选器”窗格中，针对某个筛选器选择 **“参数”** 选项，以便自动使用与所选筛选器对应的可用值创建报表参数。</span><span class="sxs-lookup"><span data-stu-id="23d76-126">In the Filters pane, select the **Parameters** option for a filter to automatically create a report parameter with available values that correspond to the filter selections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23d76-127">备注</span><span class="sxs-lookup"><span data-stu-id="23d76-127">Remarks</span></span>  
 <span data-ttu-id="23d76-128">如果您从 PowerPivot 库中的 PowerPivot 工作簿打开报表生成器，则不会在报表中重新创建 PowerPivot 工作簿中的数据透视表、数据透视图、切片器以及其他布局和分析功能。</span><span class="sxs-lookup"><span data-stu-id="23d76-128">If you open Report Builder from the PowerPivot workbook in a PowerPivot Gallery, the PivotTables, PivotCharts, slicers, and other layout and analytical features from the PowerPivot workbook are not re-created in the report.</span></span> <span data-ttu-id="23d76-129">而是生成一个空报表，其中包含一个预配置的数据源，该数据源指向 PowerPivot 工作簿中的数据。</span><span class="sxs-lookup"><span data-stu-id="23d76-129">Instead, the blank report includes a preconfigured data source that points to the data in the PowerPivot workbook.</span></span> <span data-ttu-id="23d76-130">基于 PowerPivot 工作簿设计报表可能很费时费力，具体取决于您要在报表中重新创建的切片器、筛选器以及表或图表的数量。</span><span class="sxs-lookup"><span data-stu-id="23d76-130">Designing reports based on a PowerPivot workbook can be labor-intensive and time-consuming depending on the number of slicers, filters, and tables or charts that you want to re-create in the report.</span></span> <span data-ttu-id="23d76-131">一个更好的方法是独立于 PowerPivot 设计构思您要包含在报表中的数据的显示格式。</span><span class="sxs-lookup"><span data-stu-id="23d76-131">A better approach is to envision the presentation of the data that you want in a report independently from the PowerPivot design.</span></span>  
  
 <span data-ttu-id="23d76-132">PowerPivot 工作簿中的数据经过高度压缩；而从 PowerPivot 工作簿中为报表检索的数据未经压缩。</span><span class="sxs-lookup"><span data-stu-id="23d76-132">The data in a PowerPivot workbook is highly compressed; data retrieved from the PowerPivot workbook for a report is not compressed.</span></span> <span data-ttu-id="23d76-133">使用查询设计器可指定筛选器和参数，以便将数据限制为仅是报表中所需的数据。</span><span class="sxs-lookup"><span data-stu-id="23d76-133">Use the query designer to specify filters and parameters to limit the data to just what is needed in the report.</span></span>  
  
 <span data-ttu-id="23d76-134">与连接到 Analysis Services 多维数据集不同，PowerPivot 模型没有层次结构。</span><span class="sxs-lookup"><span data-stu-id="23d76-134">Unlike connecting to an Analysis Services cube, a PowerPivot model has no hierarchies.</span></span> <span data-ttu-id="23d76-135">为了向工作簿中的相关切片器提供类似功能，您必须在报表中创建级联参数。</span><span class="sxs-lookup"><span data-stu-id="23d76-135">To provide similar functionality to related slicers in the workbook, you must create cascading parameters in the report.</span></span> <span data-ttu-id="23d76-136">有关详细信息，请参阅 [向报表添加级联参数（报表生成器和 SSRS）](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)中所创建的移动报表中使用。</span><span class="sxs-lookup"><span data-stu-id="23d76-136">For more information, see [Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="23d76-137">在某些情况下，您可能需要调整表达式，以容纳 PowerPivot 模型中的基础数据值。</span><span class="sxs-lookup"><span data-stu-id="23d76-137">In some cases, you might need to adjust expressions to accommodate the underlying data values from the PowerPivot model.</span></span> <span data-ttu-id="23d76-138">您可能需要修改表达式，以便将数据转换为正确的数据类型，或者添加或删除聚合函数。</span><span class="sxs-lookup"><span data-stu-id="23d76-138">You might need to modify expressions to convert data to the right data type or to add or remove an aggregate function.</span></span> <span data-ttu-id="23d76-139">例如，要将数据类型从 String 转换为 Integer，请使用 `=CInt`。</span><span class="sxs-lookup"><span data-stu-id="23d76-139">For example, to convert data type from String to Integer, use `=CInt`.</span></span> <span data-ttu-id="23d76-140">请始终在发布报表之前，验证报表从 PowerPivot 模型中的数据显示预期的值。</span><span class="sxs-lookup"><span data-stu-id="23d76-140">Always verify that the report displays the expected values from the data in the PowerPivot model before you publish the report.</span></span>  
  
 <span data-ttu-id="23d76-141">仅当满足以下条件时，才能生成 PowerPivot 库中报表的预览图像：</span><span class="sxs-lookup"><span data-stu-id="23d76-141">Preview images of a report in a PowerPivot Gallery are generated only if the following conditions are met:</span></span>  
  
-   <span data-ttu-id="23d76-142">提供数据的报表和 PowerPivot 工作簿必须一起存储在同一 PowerPivot 库中。</span><span class="sxs-lookup"><span data-stu-id="23d76-142">The report and the PowerPivot workbook that provides the data must be stored together in the same PowerPivot Gallery.</span></span>  
  
-   <span data-ttu-id="23d76-143">报表仅包含来自 PowerPivot 数据源的 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="23d76-143">The report contains only PowerPivot data from a PowerPivot data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d76-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23d76-144">See Also</span></span>  
 <span data-ttu-id="23d76-145">[Analysis Services MDX 查询设计器用户界面（报表生成器）](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="23d76-145">[Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span></span>  
 [<span data-ttu-id="23d76-146">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="23d76-146">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
