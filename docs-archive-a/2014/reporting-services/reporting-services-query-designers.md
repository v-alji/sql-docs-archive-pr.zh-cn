---
title: Reporting Services 查询设计器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4febd0b0e0bf028d16aa3ef13ce4294feb930072
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691049"
---
# <a name="reporting-services-query-designers"></a><span data-ttu-id="f7f5b-102">Reporting Services 查询设计器</span><span class="sxs-lookup"><span data-stu-id="f7f5b-102">Reporting Services Query Designers</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="f7f5b-103">提供了有助于为报表中的每种数据源类型生成查询的图形查询设计器和基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-103">provides graphical and text-based query designers to help you build queries for each data source type in your report.</span></span>  
  
 <span data-ttu-id="f7f5b-104">某些数据源支持以交互方式生成查询的图形设计器。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-104">Some data sources support graphical designers that help you build a query interactively.</span></span> <span data-ttu-id="f7f5b-105">其他数据源使用基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-105">Other data sources use a text-based query designer.</span></span> <span data-ttu-id="f7f5b-106">使用图形查询设计器，可以将表示数据源中基础数据的元数据项拖到查询设计图面上。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-106">By using a graphical query designer, you can drag metadata items that represent the underlying data on a data source to the query design surface.</span></span> <span data-ttu-id="f7f5b-107">使用基于文本的查询设计器，可以在查询窗格中键入命令文本。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-107">By using a text-based query designer, you can type command text into a query pane.</span></span> <span data-ttu-id="f7f5b-108">单击工具栏上的基于文本的查询设计器图标，即可从图形查询设计器更改为基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-108">You can change from a graphical query designer to a text-based query designer by clicking the text-based query designer icon on the toolbar.</span></span>  
  
 <span data-ttu-id="f7f5b-109">在您的报表中可用的数据源类型由在您的客户端或报表服务器上安装的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 数据扩展插件决定。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-109">The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data extensions installed on your client or report server.</span></span> <span data-ttu-id="f7f5b-110">有关详细信息，请参阅[Rsreportdesigner.config 配置文件](report-server/rsreportdesigner-configuration-file.md)和[rsreportserver.config 配置文件](report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-110">For more information, see [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) and [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="f7f5b-111">数据处理扩展插件及其关联的查询设计器在对数据源的支持上在以下方式上可能会不同：</span><span class="sxs-lookup"><span data-stu-id="f7f5b-111">A data processing extension and its associated query designer can differ in support for data sources in the following ways:</span></span>  
  
-   <span data-ttu-id="f7f5b-112">**查询设计器类型。**</span><span class="sxs-lookup"><span data-stu-id="f7f5b-112">**By query designer type.**</span></span> <span data-ttu-id="f7f5b-113">例如， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据源同时支持图形查询设计器和基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-113">For example, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source supports both the graphical and text-based query designers.</span></span>  
  
-   <span data-ttu-id="f7f5b-114">**查询语言变化。**</span><span class="sxs-lookup"><span data-stu-id="f7f5b-114">**By query language variation.**</span></span> <span data-ttu-id="f7f5b-115">例如，像 [!INCLUDE[tsql](../includes/tsql-md.md)] 这样的查询语言在语法上可能有所不同，具体情况取决于数据源类型。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-115">For example, a query language such as [!INCLUDE[tsql](../includes/tsql-md.md)] can differ in syntax depending on the data source type.</span></span> <span data-ttu-id="f7f5b-116">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] 语言和 Oracle SQL 语言在查询命令的语法上有一些变化。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-116">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] language and the Oracle SQL language have some variation in syntax for a query command.</span></span>  
  
-   <span data-ttu-id="f7f5b-117">**对数据库对象名的架构部分的支持。**</span><span class="sxs-lookup"><span data-stu-id="f7f5b-117">**By support for the schema part of a database object name.**</span></span> <span data-ttu-id="f7f5b-118">当数据源使用架构作为数据库对象标识符的一部分时，对于不使用默认架构的任何名称而言，必须将架构名作为查询的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-118">When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema.</span></span> <span data-ttu-id="f7f5b-119">例如 `SELECT FirstName, LastName FROM [Person].[Person]`。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-119">For example, `SELECT FirstName, LastName FROM [Person].[Person]`.</span></span>  
  
-   <span data-ttu-id="f7f5b-120">**对查询参数的支持。**</span><span class="sxs-lookup"><span data-stu-id="f7f5b-120">**By support for query parameters.**</span></span> <span data-ttu-id="f7f5b-121">数据访问接口在为参数提供支持方面存在差异。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-121">Data providers differ in support for parameters.</span></span> <span data-ttu-id="f7f5b-122">某些数据访问接口支持命名参数；例如， `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-122">Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`.</span></span> <span data-ttu-id="f7f5b-123">某些数据访问接口支持未命名参数；例如， `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-123">Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`.</span></span> <span data-ttu-id="f7f5b-124">参数标识符可能因数据提供程序不同而不同；例如， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用“at”(@) 符号，而 Oracle 则使用冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-124">The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses the "at" (@) symbol, Oracle uses the colon (:).</span></span> <span data-ttu-id="f7f5b-125">某些数据访问接口不支持参数。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-125">Some data providers do not support parameters.</span></span>  
  
-   <span data-ttu-id="f7f5b-126">**能否导入查询。**</span><span class="sxs-lookup"><span data-stu-id="f7f5b-126">**By ability to import queries.**</span></span> <span data-ttu-id="f7f5b-127">例如，对于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据源，可从报表定义文件 (.rdl) 或 .sql 文件中导入现有查询。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-127">For example, for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source, you can import a query from a report definition file (.rdl) or from a .sql file.</span></span>  
  
## <a name="query-designers"></a><span data-ttu-id="f7f5b-128">查询设计器</span><span class="sxs-lookup"><span data-stu-id="f7f5b-128">Query Designers</span></span>  
 <span data-ttu-id="f7f5b-129">下面的主题将介绍每种查询设计器的用户界面。</span><span class="sxs-lookup"><span data-stu-id="f7f5b-129">The following topics describe the user interface for each query designer.</span></span>  
  
-   [<span data-ttu-id="f7f5b-130">Analysis Services MDX 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-130">Analysis Services MDX Query Designer User Interface</span></span>](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-131">Analysis Services DMX 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-131">Analysis Services DMX Query Designer User Interface</span></span>](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-132">图形查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-132">Graphical Query Designer User Interface</span></span>](report-data/graphical-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-133">关系查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-133">Relational Query Designer User Interface</span></span>](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-134">Hyperion Essbase 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-134">Hyperion Essbase Query Designer User Interface</span></span>](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-135">报表模型查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-135">Report Model Query Designer User Interface</span></span>](report-data/report-model-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-136">SAP NetWeaver BI 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-136">SAP NetWeaver BI Query Designer User Interface</span></span>](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="f7f5b-137">SharePoint 列表查询设计器</span><span class="sxs-lookup"><span data-stu-id="f7f5b-137">SharePoint List Query Designer</span></span>](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [<span data-ttu-id="f7f5b-138">基于文本的查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f7f5b-138">Text-based Query Designer User Interface</span></span>](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7f5b-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7f5b-139">See Also</span></span>  
 <span data-ttu-id="f7f5b-140">[Reporting Services &#40;SSRS 支持的数据源&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="f7f5b-140">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="f7f5b-141">[从外部数据源添加数据 &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7f5b-141">[Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="f7f5b-142">[.NET Framework 的数据处理扩展插件和数据访问接口 &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7f5b-142">[Data Processing Extensions and .NET Framework Data Providers &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span></span>  
 [<span data-ttu-id="f7f5b-143">扩展插件 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="f7f5b-143">Extensions &#40;SSRS&#41;</span></span>](extensions-ssrs.md)  
  
  
