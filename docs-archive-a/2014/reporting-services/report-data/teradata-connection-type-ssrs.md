---
title: Teradata 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73e51c82a824bb607d75c2e78cfc9b0f37476e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588917"
---
# <a name="teradata-connection-type-ssrs"></a><span data-ttu-id="62b42-102">Teradata 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="62b42-102">Teradata Connection Type (SSRS)</span></span>
  <span data-ttu-id="62b42-103">若要在报表中包含来自 Teradata 关系数据库的数据，您必须拥有一个基于 Teradata 类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="62b42-103">To include data from a Teradata relational database in your report, you must have a dataset that is based on a report data source of type Teradata.</span></span> <span data-ttu-id="62b42-104">此内置数据源类型基于 .NET Managed Provider for Teradata 数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="62b42-104">This built-in data source type is based on the .NET Managed Provider for Teradata data processing extension.</span></span>  
  
 <span data-ttu-id="62b42-105">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="62b42-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="62b42-106">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="62b42-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="62b42-107">连接字符串</span><span class="sxs-lookup"><span data-stu-id="62b42-107">Connection String</span></span>  
 <span data-ttu-id="62b42-108">请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="62b42-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="62b42-109">下面的连接字符串示例指定使用 IP 地址指定的服务器上的 Teradata 数据库：</span><span class="sxs-lookup"><span data-stu-id="62b42-109">The following connection string example specifies a Teradata database on the server specified with an IP address:</span></span>  
  
```  
data source=<IP Address>  
```  
  
 <span data-ttu-id="62b42-110">有关更多连接字符串的示例，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="62b42-110">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="62b42-111">凭据</span><span class="sxs-lookup"><span data-stu-id="62b42-111">Credentials</span></span>  
 <span data-ttu-id="62b42-112">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="62b42-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="62b42-113">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="62b42-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="62b42-114">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="62b42-114">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  

##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="62b42-115">注释</span><span class="sxs-lookup"><span data-stu-id="62b42-115">Remarks</span></span>  
 <span data-ttu-id="62b42-116">在可以连接 Teradata 数据源之前，系统管理员必须已安装支持从 Teradata 数据库中检索数据的 .NET Data Provider for Teradata 版本。</span><span class="sxs-lookup"><span data-stu-id="62b42-116">Before you can connect a Teradata data source, the system administrator must have installed the version of the .NET Data Provider for Teradata that supports retrieving data from the Teradata database.</span></span> <span data-ttu-id="62b42-117">此数据访问接口必须与报表生成器安装在同一台计算机上，报表服务器上也是如此。</span><span class="sxs-lookup"><span data-stu-id="62b42-117">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="62b42-118">不是所有的报表传递模式都受到此数据访问接口的支持。</span><span class="sxs-lookup"><span data-stu-id="62b42-118">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="62b42-119">此数据处理扩展插件不支持通过数据驱动订阅传递报表。</span><span class="sxs-lookup"><span data-stu-id="62b42-119">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="62b42-120">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ 联机丛书 ](https://go.microsoft.com/fwlink/?linkid=121312) 中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的[使用外部数据源提供订阅方数据（数据驱动订阅）](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="62b42-120">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  

##  <a name="report-models"></a><a name="Models"></a> <span data-ttu-id="62b42-121">报表模型</span><span class="sxs-lookup"><span data-stu-id="62b42-121">Report Models</span></span>  
 <span data-ttu-id="62b42-122">若要从基于 Teradata 数据源的报表模型创建数据集，则必须在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的模型设计器中设计模型，并在报表服务器上发布。</span><span class="sxs-lookup"><span data-stu-id="62b42-122">To create a dataset from a report model that is based on a Teradata data source, the model must be designed in Model Designer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and published on a report server.</span></span>  

##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="62b42-123">相关章节</span><span class="sxs-lookup"><span data-stu-id="62b42-123">Related Sections</span></span>  
 <span data-ttu-id="62b42-124">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="62b42-124">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="62b42-125">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="62b42-125">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="62b42-126">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="62b42-126">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="62b42-127">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="62b42-127">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="62b42-128">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="62b42-128">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="62b42-129">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="62b42-129">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="62b42-130">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="62b42-130">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="62b42-131">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="62b42-131">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="62b42-132">提供有关数据集查询生成的字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="62b42-132">Provides information about the field collection that is generated by the dataset query.</span></span>  
  
 <span data-ttu-id="62b42-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="62b42-133">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="62b42-134">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="62b42-134">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 [<span data-ttu-id="62b42-135">将 SQL Server 2008 Reporting Services 与 .NET Framework Data Provider for Teradata 一起使用</span><span class="sxs-lookup"><span data-stu-id="62b42-135">Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata</span></span>](https://go.microsoft.com/fwlink/?LinkID=130848)  
 <span data-ttu-id="62b42-136">提供有关使用此数据扩展插件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="62b42-136">Provides detailed information about working with this data extension.</span></span>  

## <a name="see-also"></a><span data-ttu-id="62b42-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62b42-137">See Also</span></span>  
 <span data-ttu-id="62b42-138">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="62b42-138">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="62b42-139">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="62b42-139">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="62b42-140">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="62b42-140">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
