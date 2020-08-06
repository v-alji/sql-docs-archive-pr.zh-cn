---
title: ODBC 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2bf5ee6f3eeaa38796e4fa41f3cc0634fd128cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578648"
---
# <a name="odbc-connection-type-ssrs"></a><span data-ttu-id="5b0f5-102">ODBC 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5b0f5-102">ODBC Connection Type (SSRS)</span></span>
  <span data-ttu-id="5b0f5-103">若要包含来自 ODBC 数据访问接口的数据，必须拥有一个基于类型为 ODBC 的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-103">To include data from an ODBC data provider, you must have a dataset that is based on a report data source of type ODBC.</span></span> <span data-ttu-id="5b0f5-104">此内置数据源类型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC 数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC data processing extension.</span></span>  
  
 <span data-ttu-id="5b0f5-105">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="5b0f5-106">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="5b0f5-107">连接字符串</span><span class="sxs-lookup"><span data-stu-id="5b0f5-107">Connection String</span></span>  
 <span data-ttu-id="5b0f5-108">用于 ODBC 数据处理扩展插件的连接字符串取决于您想要的 ODBC 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-108">The connection string for the ODBC data processing extension depends on the ODBC driver that you want.</span></span> <span data-ttu-id="5b0f5-109">典型的连接字符串包含驱动程序支持的名称/值对。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-109">A typical connection string contains name/value pairs that are supported by the driver.</span></span> <span data-ttu-id="5b0f5-110">例如，下面的连接字符串为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 AdventureWorks 数据库指定 ODBC 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-110">For example, the following connection string specifies the ODBC driver for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="5b0f5-111">凭据</span><span class="sxs-lookup"><span data-stu-id="5b0f5-111">Credentials</span></span>  
 <span data-ttu-id="5b0f5-112">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="5b0f5-113">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="5b0f5-114">如果将 ODBC 数据源配置为提示输入密码或在连接字符串中包含密码，并且用户输入了带有如标点符号之类特殊字符的密码，则某些基础数据源驱动程序无法验证这些特殊字符。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-114">If you configure your ODBC data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="5b0f5-115">处理报表时，可能会出现“密码无效”这一消息来指示此问题。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-115">When you process the report, the message "Not a valid password" might indicate this problem.</span></span> <span data-ttu-id="5b0f5-116">如果不能更改密码，则可以使用数据库管理员角色将相应的凭据作为系统 ODBC 数据源名称 (DSN) 的一部分存储在报表服务器中。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-116">If changing the password is impractical, you can work with your database administrator to store the appropriate credentials on the report server as part of a system ODBC data source name (DSN).</span></span> <span data-ttu-id="5b0f5-117">有关详细信息，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档中的“OdbcConnection.ConnectionString”。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-117">For more information, see "OdbcConnection.ConnectionString" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b0f5-118">建议您不要在连接字符串中添加登录信息（如密码）。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-118">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="5b0f5-119">报表生成器在 **“数据源”** 对话框中提供了一个用于输入凭据的单独选项卡。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-119">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
 <span data-ttu-id="5b0f5-120">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-120">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="5b0f5-121">注释</span><span class="sxs-lookup"><span data-stu-id="5b0f5-121">Remarks</span></span>  
 <span data-ttu-id="5b0f5-122">ODBC 是在 OLEDB 之前采用的一种早期数据访问技术。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-122">ODBC is an early data access technology that preceded OLEDB.</span></span> <span data-ttu-id="5b0f5-123">ODBC 只支持关系数据源。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-123">ODBC supports only relational data sources.</span></span> <span data-ttu-id="5b0f5-124">ODBC 数据访问接口称为“驱动程序”  。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-124">ODBC data providers are called *drivers*.</span></span> <span data-ttu-id="5b0f5-125">ODBC 驱动程序由 Microsoft 和第三方供应商提供。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-125">ODBC drivers are provided by Microsoft and third party vendors.</span></span> <span data-ttu-id="5b0f5-126">例如，Microsoft Office 安装了连接到 Office 文件格式的 ODBC 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-126">For example, Microsoft Office installs ODBC drivers that connect to Office file formats.</span></span>  
  
 <span data-ttu-id="5b0f5-127">必须先安装 ODBC 驱动程序并生成计算机或系统 DSN，才能生成 ODBC 连接字符串。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-127">Before you can build an ODBC connection string, you must have ODBC drivers installed and build a machine or system DSN.</span></span> <span data-ttu-id="5b0f5-128">若要成功检索到想要的数据，则必须提供驱动程序支持的查询语法。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-128">To successfully retrieve the data that you want, you must provide query syntax that is supported by the driver.</span></span> <span data-ttu-id="5b0f5-129">参数支持因驱动程序而异。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-129">Parameter support varies by driver.</span></span> <span data-ttu-id="5b0f5-130">有关详细信息，请参阅特定于所选驱动程序的主题，例如，[SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-130">For more information, see topics that are specific to the driver that you select, for example, [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="5b0f5-131">平台和版本信息</span><span class="sxs-lookup"><span data-stu-id="5b0f5-131">Platform and Version Information</span></span>  
 <span data-ttu-id="5b0f5-132">有关特定 ODBC 数据提供程序的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书 ](https://go.microsoft.com/fwlink/?linkid=121312) 中的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-132">For more information about specific ODBC data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="5b0f5-133">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="5b0f5-133">How-To Topics</span></span>  
 <span data-ttu-id="5b0f5-134">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-134">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="5b0f5-135">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5b0f5-135">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="5b0f5-136">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5b0f5-136">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="5b0f5-137">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5b0f5-137">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="5b0f5-138">相关章节</span><span class="sxs-lookup"><span data-stu-id="5b0f5-138">Related Sections</span></span>  
 <span data-ttu-id="5b0f5-139">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-139">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="5b0f5-140">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5b0f5-140">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="5b0f5-141">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-141">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="5b0f5-142">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="5b0f5-142">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="5b0f5-143">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-143">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="5b0f5-144">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5b0f5-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="5b0f5-145">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-145">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="5b0f5-146">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5b0f5-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="5b0f5-147">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-147">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="5b0f5-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-148">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="5b0f5-149">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5b0f5-149">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="5b0f5-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b0f5-150">See Also</span></span>  
 <span data-ttu-id="5b0f5-151">[报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="5b0f5-151">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="5b0f5-152">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5b0f5-152">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5b0f5-153">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5b0f5-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
