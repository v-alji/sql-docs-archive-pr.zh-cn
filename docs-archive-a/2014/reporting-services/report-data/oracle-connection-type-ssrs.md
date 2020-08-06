---
title: Oracle 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e9bf19953c5d2dc2f818eddcacf445e641972d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586472"
---
# <a name="oracle-connection-type-ssrs"></a><span data-ttu-id="6f987-102">Oracle 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="6f987-102">Oracle Connection Type (SSRS)</span></span>
  <span data-ttu-id="6f987-103">若要在报表中使用来自 Oracle 数据库的数据，您必须拥有一个基于 Oracle 类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="6f987-103">To use data from an Oracle database in your report, you must you must have a dataset that is based on a report data source of type Oracle.</span></span> <span data-ttu-id="6f987-104">此内置数据源类型基于 .NET Framework Managed Provider for Oracle，并且需要 Oracle 客户端软件组件。</span><span class="sxs-lookup"><span data-stu-id="6f987-104">This built-in data source type is based on the .NET Framework Managed Provider for Oracle and requires an Oracle client software component.</span></span>  
  
 <span data-ttu-id="6f987-105">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="6f987-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="6f987-106">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="6f987-107">连接字符串</span><span class="sxs-lookup"><span data-stu-id="6f987-107">Connection String</span></span>  
 <span data-ttu-id="6f987-108">请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="6f987-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="6f987-109">下面的连接字符串示例指定使用 Unicode 的名为“Oracle9”的服务器上的 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="6f987-109">The following connection string example specifies an Oracle database on the server named "Oracle9" using Unicode.</span></span> <span data-ttu-id="6f987-110">服务器名称必须与 Tnsnames.ora 配置文件中定义的 Oracle 服务器实例名相匹配。</span><span class="sxs-lookup"><span data-stu-id="6f987-110">The server name must match what is defined in the Tnsnames.ora configuration file as the Oracle server instance name.</span></span>  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 <span data-ttu-id="6f987-111">有关连接字符串示例的详细信息，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-111">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="6f987-112">凭据</span><span class="sxs-lookup"><span data-stu-id="6f987-112">Credentials</span></span>  
 <span data-ttu-id="6f987-113">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="6f987-113">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="6f987-114">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="6f987-114">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="6f987-115">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-115">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  

  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="6f987-116">请求</span><span class="sxs-lookup"><span data-stu-id="6f987-116">Queries</span></span>  
 <span data-ttu-id="6f987-117">若要创建数据集，可以从下拉列表中选择存储过程，也可以创建一个 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="6f987-117">To create a dataset, you can either select a stored procedure from a drop-down list or create an SQL query.</span></span> <span data-ttu-id="6f987-118">若要生成一个查询，必须使用基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="6f987-118">To build a query, you must use the text-based query designer.</span></span> <span data-ttu-id="6f987-119">有关详细信息，请参阅[基于文本的查询设计器用户界面（报表生成器）](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-119">For more information, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="6f987-120">可以指定只返回一个结果集的存储过程。</span><span class="sxs-lookup"><span data-stu-id="6f987-120">You can specify stored procedures that return only one result set.</span></span> <span data-ttu-id="6f987-121">不支持使用基于游标的查询。</span><span class="sxs-lookup"><span data-stu-id="6f987-121">Using cursor-based queries are not supported.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="6f987-122">Parameters</span><span class="sxs-lookup"><span data-stu-id="6f987-122">Parameters</span></span>  
 <span data-ttu-id="6f987-123">如果查询包括查询变量，则将自动生成对应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="6f987-123">If the query includes query variables, corresponding report parameters are automatically generated.</span></span> <span data-ttu-id="6f987-124">此扩展插件支持命名参数。</span><span class="sxs-lookup"><span data-stu-id="6f987-124">Named parameters are supported by this extension.</span></span> <span data-ttu-id="6f987-125">对于 Oracle 版本 9 或更高版本而言，支持多值参数。</span><span class="sxs-lookup"><span data-stu-id="6f987-125">For Oracle version 9 or later, multivalue parameters are supported.</span></span>  
  
 <span data-ttu-id="6f987-126">报表参数是用可能需要修改的默认属性值创建的。</span><span class="sxs-lookup"><span data-stu-id="6f987-126">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="6f987-127">例如，每个报表参数的数据类型均为 **Text**。</span><span class="sxs-lookup"><span data-stu-id="6f987-127">For example, each report parameter is data type **Text**.</span></span> <span data-ttu-id="6f987-128">创建报表参数后，您可能需要更改默认值。</span><span class="sxs-lookup"><span data-stu-id="6f987-128">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="6f987-129">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6f987-129">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  

  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="6f987-130">注释</span><span class="sxs-lookup"><span data-stu-id="6f987-130">Remarks</span></span>  
 <span data-ttu-id="6f987-131">在可以连接 Oracle 数据源之前，系统管理员必须已安装支持从 Oracle 数据库中检索数据的 .NET Data Provider for Oracle 版本。</span><span class="sxs-lookup"><span data-stu-id="6f987-131">Before you can connect an Oracle data source, the system administrator must have installed the version of the .NET Data Provider for Oracle that supports retrieving data from the Oracle database.</span></span> <span data-ttu-id="6f987-132">此数据访问接口必须与报表生成器安装在同一台计算机上，报表服务器上也是如此。</span><span class="sxs-lookup"><span data-stu-id="6f987-132">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="6f987-133">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="6f987-133">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="6f987-134">msdn.microsoft.com 上的[Using the .NET Framework Data Provider for Oracle](https://go.microsoft.com/fwlink/?LinkId=112314) （使用用于 Oracle 的 .NET Framework 数据访问接口）。</span><span class="sxs-lookup"><span data-stu-id="6f987-134">[Using the .NET Framework Data Provider for Oracle](https://go.microsoft.com/fwlink/?LinkId=112314) on msdn.microsoft.com</span></span>  
  
-   [<span data-ttu-id="6f987-135">如何使用 Reporting Services 配置和访问 Oracle 数据源</span><span class="sxs-lookup"><span data-stu-id="6f987-135">How to use Reporting Services to configure and to access an Oracle data source</span></span>](https://support.microsoft.com/kb/834305)  
  
-   [<span data-ttu-id="6f987-136">如何为 NETWORK SERVICE 安全主体添加权限</span><span class="sxs-lookup"><span data-stu-id="6f987-136">How to add permissions for the NETWORK SERVICE security principal</span></span>](https://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a><span data-ttu-id="6f987-137">备用数据扩展插件</span><span class="sxs-lookup"><span data-stu-id="6f987-137">Alternate Data Extensions</span></span>  
 <span data-ttu-id="6f987-138">您还可以通过使用 OLE DB 数据源类型从 Oracle 数据库中检索数据。</span><span class="sxs-lookup"><span data-stu-id="6f987-138">You can also retrieve data from an Oracle database by using an OLE DB data source type.</span></span> <span data-ttu-id="6f987-139">有关详细信息，请参阅 [OLE DB 连接类型 (SSRS)](ole-db-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-139">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md).</span></span>  
  
###### <a name="report-models"></a><span data-ttu-id="6f987-140">报表模型</span><span class="sxs-lookup"><span data-stu-id="6f987-140">Report Models</span></span>  
 <span data-ttu-id="6f987-141">您还可以创建基于 Oracle 数据库的模型。</span><span class="sxs-lookup"><span data-stu-id="6f987-141">You can also create models based on an Oracle database.</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="6f987-142">平台和版本信息</span><span class="sxs-lookup"><span data-stu-id="6f987-142">Platform and Version Information</span></span>  
 <span data-ttu-id="6f987-143">有关平台和版本支持的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-143">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="6f987-144">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="6f987-144">How-To Topics</span></span>  
 <span data-ttu-id="6f987-145">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="6f987-145">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="6f987-146">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6f987-146">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="6f987-147">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6f987-147">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="6f987-148">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6f987-148">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 
  
##  <a name="related-sections"></a><a name="Related"></a><span data-ttu-id="6f987-149">相关部分</span><span class="sxs-lookup"><span data-stu-id="6f987-149">Related Sections</span></span>  
 <span data-ttu-id="6f987-150">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="6f987-150">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="6f987-151">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6f987-151">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="6f987-152">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="6f987-152">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="6f987-153">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="6f987-153">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="6f987-154">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="6f987-154">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="6f987-155">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6f987-155">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="6f987-156">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="6f987-156">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="6f987-157">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6f987-157">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="6f987-158">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="6f987-158">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="6f987-159">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="6f987-159">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="6f987-160">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6f987-160">Provides in-depth information about platform and version support for each data extension.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="6f987-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f987-161">See Also</span></span>  
 <span data-ttu-id="6f987-162">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="6f987-162">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="6f987-163">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6f987-163">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6f987-164">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6f987-164">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
