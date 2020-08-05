---
title: “报表数据”窗格
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fc09c100cc8391bb1fd025b4bb5ac5f3b5e4379a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577307"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="7ee7d-102">SQL Server Reporting Services (SSRS) 中的报表数据窗格</span><span class="sxs-lookup"><span data-stu-id="7ee7d-102">Report Data pane in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="7ee7d-103">使用 **“报表数据”** 窗格可以查看报表中当前定义的参数、数据源、数据集、字段集合和图像。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-103">Use the **Report Data** pane to view the currently defined parameters, data sources, datasets, field collections, and images in your report.</span></span> <span data-ttu-id="7ee7d-104">该窗格会显示表示报表中数据的项的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-104">The Report Dane displays a hierarchical view of the items that represent data in your report.</span></span> <span data-ttu-id="7ee7d-105">顶级节点表示内置字段、参数、图像和数据源引用。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-105">The top level nodes represent built-in fields, parameters, images, and data source references.</span></span> <span data-ttu-id="7ee7d-106">展开每个节点可以查看各数据项。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-106">Expand each node to view the data items.</span></span> <span data-ttu-id="7ee7d-107">例如，展开某个数据源节点时，会显示为该数据源定义的数据集。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-107">For example, when you expand a data source node, the datasets defined for that data source appear.</span></span> <span data-ttu-id="7ee7d-108">展开数据集时，会显示其字段集合。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-108">When you expand a dataset, its field collection appears.</span></span> <span data-ttu-id="7ee7d-109">将这些数据项拖放到报表设计图面可将数据与报表页中的报表项链接。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-109">Drag items to the report design surface to link data with report items on the report page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7ee7d-110">选项</span><span class="sxs-lookup"><span data-stu-id="7ee7d-110">Options</span></span>

 <span data-ttu-id="7ee7d-111">**内置字段**</span><span class="sxs-lookup"><span data-stu-id="7ee7d-111">**Built-in Fields**</span></span>  
 <span data-ttu-id="7ee7d-112">表示 Reporting Services 提供的在报表中常用的字段，例如报表名称或页码。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-112">Represents fields provided by Reporting Services that are commonly used in a report, such as the report name or page number.</span></span> <span data-ttu-id="7ee7d-113">有关详细信息，请参阅[表达式中的内置集合（报表生成器和 SSRS）](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-113">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="7ee7d-114">**参数**</span><span class="sxs-lookup"><span data-stu-id="7ee7d-114">**Parameters**</span></span>  
 <span data-ttu-id="7ee7d-115">表示报表参数的集合，每个参数都可为单值或多值参数。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-115">Represents the collection of report parameters, each of which can be single-valued or multivalued.</span></span> <span data-ttu-id="7ee7d-116">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-116">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="7ee7d-117">**映像**</span><span class="sxs-lookup"><span data-stu-id="7ee7d-117">**Images**</span></span>  
 <span data-ttu-id="7ee7d-118">表示报表中使用的图像集。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-118">Represents the set of images used in the report.</span></span> <span data-ttu-id="7ee7d-119">有关详细信息，请参阅[图像（报表生成器和 SSRS）](../report-design/images-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-119">For more information, see [Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="7ee7d-120">**数据源**</span><span class="sxs-lookup"><span data-stu-id="7ee7d-120">**Data source**</span></span>  
 <span data-ttu-id="7ee7d-121">表示对嵌入数据源或共享数据源的单个数据源引用。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-121">Represents a single data source reference to an embedded data source or to a shared data source.</span></span> <span data-ttu-id="7ee7d-122">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，共享数据源显示在“共享数据源”文件夹下的解决方案资源管理器中。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], shared data sources appear in Solution Explorer under the Shared Data Sources folder.</span></span> <span data-ttu-id="7ee7d-123">数据源会指定 Reporting Services 支持的一种数据源类型。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-123">A data source specifies one of the data source types supported by Reporting Services.</span></span> <span data-ttu-id="7ee7d-124">数据源是基于其的数据集集合的父节点。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-124">A data source is the parent node for the collection of datasets based on it.</span></span> <span data-ttu-id="7ee7d-125">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-125">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) .</span></span>  
  
 <span data-ttu-id="7ee7d-126">**数据集**</span><span class="sxs-lookup"><span data-stu-id="7ee7d-126">**Dataset**</span></span>  
 <span data-ttu-id="7ee7d-127">表示单个数据集。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-127">Represents a single dataset.</span></span> <span data-ttu-id="7ee7d-128">数据集是查询指定的字段集合的父节点，包括所有计算字段。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-128">A dataset is the parent node for the collection of fields specified by the query and including any calculated fields.</span></span> <span data-ttu-id="7ee7d-129">Reporting Services 支持查询设计器，这将有助于您指定查询。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-129">Reporting Services supports query designers to help you specify a query.</span></span> <span data-ttu-id="7ee7d-130">有关详细信息，请参阅[将数据添加到报表中 &#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md)和[查询设计工具 in 报表设计器 SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee7d-130">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) and [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7ee7d-131">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7ee7d-131">Next steps</span></span>

 - [<span data-ttu-id="7ee7d-132">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7ee7d-132">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)
 - [<span data-ttu-id="7ee7d-133">“分组”窗格</span><span class="sxs-lookup"><span data-stu-id="7ee7d-133">Grouping Pane</span></span>](../tools/grouping-pane.md)