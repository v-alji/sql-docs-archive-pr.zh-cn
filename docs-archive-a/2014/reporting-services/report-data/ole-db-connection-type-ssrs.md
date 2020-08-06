---
title: OLE DB 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66d4074d6bf90a23814b13da8836fd0594e8cf1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694271"
---
# <a name="ole-db-connection-type-ssrs"></a><span data-ttu-id="97537-102">OLE DB 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="97537-102">OLE DB Connection Type (SSRS)</span></span>
  <span data-ttu-id="97537-103">若要包含来自 OLE DB 数据访问接口的数据，您必须具有一个基于 OLE DB 类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="97537-103">To include data from an OLE DB data provider, you must have a dataset that is based on a report data source of type OLE DB.</span></span> <span data-ttu-id="97537-104">此内置数据源类型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB 数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="97537-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB data processing extension.</span></span>  
  
 <span data-ttu-id="97537-105">OLE DB 是一项数据访问技术，客户端通过该技术可以连接到各种数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-105">OLE DB is a data access technology that enables clients to connect to a variety of data providers.</span></span> <span data-ttu-id="97537-106">在选择数据源类型 OLE DB 之后，您必须选择特定的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-106">After you select the data source type OLE DB, you must select a specific data provider.</span></span> <span data-ttu-id="97537-107">是否支持参数和凭据之类的功能取决于您所选择的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-107">Support for features such as parameters and credentials are dependent on the data provider that you select.</span></span>  
  
 <span data-ttu-id="97537-108">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="97537-108">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="97537-109">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="97537-109">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="97537-110">连接字符串</span><span class="sxs-lookup"><span data-stu-id="97537-110">Connection String</span></span>  
 <span data-ttu-id="97537-111">用于 OLE DB 数据处理扩展插件的连接字符串取决于您想要的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-111">The connection string for the OLE DB data processing extension depends on the data provider that you want.</span></span> <span data-ttu-id="97537-112">典型的连接字符串包含数据访问接口支持的名称/值对。</span><span class="sxs-lookup"><span data-stu-id="97537-112">A typical connection string contains name/value pairs that are supported by the data provider.</span></span> <span data-ttu-id="97537-113">例如，下面的连接字符串为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 AdventureWorks 数据库指定 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-113">For example, the following connection string specifies the OLE DB provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="97537-114">您使用的连接字符串取决于您所连接到的外部数据源。</span><span class="sxs-lookup"><span data-stu-id="97537-114">The connection string that you use depends on the external data source that you are connecting to.</span></span> <span data-ttu-id="97537-115">若要设置特定于数据访问接口的连接字符串属性，请在 **“数据源属性”** 对话框的 **“常规”** 页中，单击 **“生成”** 按钮以打开 **“连接属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="97537-115">To set connection string properties specific to a data provider, from the **General** page of the **Data Source Properties** dialog box, click the **Build** button to open the **Connection Properties** dialog box.</span></span> <span data-ttu-id="97537-116">通过 **“数据链接属性”** 对话框设置扩展数据源属性。</span><span class="sxs-lookup"><span data-stu-id="97537-116">Set extended data source properties through the **Data Link Properties** dialog box.</span></span>  
  
 <span data-ttu-id="97537-117">有关连接字符串的示例，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="97537-117">For examples of connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="97537-118">凭据</span><span class="sxs-lookup"><span data-stu-id="97537-118">Credentials</span></span>  
 <span data-ttu-id="97537-119">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="97537-119">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="97537-120">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="97537-120">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="97537-121">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="97537-121">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
###### <a name="special-characters-in-a-password"></a><span data-ttu-id="97537-122">密码中的特殊字符</span><span class="sxs-lookup"><span data-stu-id="97537-122">Special Characters in a Password</span></span>  
 <span data-ttu-id="97537-123">如果将 OLE DB 数据源配置为提示输入密码或在连接字符串中包含密码，并且用户输入了带有如标点符号之类特殊字符的密码，则某些基础数据源驱动程序无法验证这些特殊字符。</span><span class="sxs-lookup"><span data-stu-id="97537-123">If you configure the OLE DB data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="97537-124">处理报表时，可能会出现“密码无效”这一消息来指示此问题。</span><span class="sxs-lookup"><span data-stu-id="97537-124">When you process the report, the message "Not a valid password" may indicate this problem.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97537-125">建议您不要在连接字符串中添加登录信息（如密码）。</span><span class="sxs-lookup"><span data-stu-id="97537-125">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="97537-126">报表生成器在 **“数据源”** 对话框中提供了一个用于输入凭据的单独选项卡。</span><span class="sxs-lookup"><span data-stu-id="97537-126">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="97537-127">Parameters</span><span class="sxs-lookup"><span data-stu-id="97537-127">Parameters</span></span>  
 <span data-ttu-id="97537-128">某些 OLE DB 访问接口支持未命名参数，而不支持命名参数。</span><span class="sxs-lookup"><span data-stu-id="97537-128">Some OLE DB providers support unnamed parameters and not named parameters.</span></span> <span data-ttu-id="97537-129">通过在查询中使用占位符按位置传递参数。</span><span class="sxs-lookup"><span data-stu-id="97537-129">Parameters are passed by position by using a placeholder in the query.</span></span> <span data-ttu-id="97537-130">占位字符由数据访问接口所支持的语法确定。</span><span class="sxs-lookup"><span data-stu-id="97537-130">The placeholder character is determined by the syntax that is supported by the data provider.</span></span>  
  
 
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="97537-131">注释</span><span class="sxs-lookup"><span data-stu-id="97537-131">Remarks</span></span>  
 <span data-ttu-id="97537-132">OLEDB 是一项用于为特定数据源生成数据访问接口的本机技术。</span><span class="sxs-lookup"><span data-stu-id="97537-132">OLEDB is a native technology for building data providers for specific data sources.</span></span> <span data-ttu-id="97537-133">OLEDB 基于 COM（组件对象模型）接口。</span><span class="sxs-lookup"><span data-stu-id="97537-133">OLEDB is based on COM (Component Object Model) interfaces.</span></span> <span data-ttu-id="97537-134">OLEDB 这项技术晚于 ODBC、早于 ADO.NET 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-134">OLEDB is a later technology than ODBC and earlier than ADO.NET data providers.</span></span> <span data-ttu-id="97537-135">与任何其他 COM 组件一样，OLEDB 数据访问接口注册到操作系统。</span><span class="sxs-lookup"><span data-stu-id="97537-135">OLEDB data providers are registered with the operating system like any other COM component.</span></span> <span data-ttu-id="97537-136">OLEDB 数据访问接口可从 Microsoft 和第三方供应商那里获得。</span><span class="sxs-lookup"><span data-stu-id="97537-136">OLEDB data providers are available from Microsoft and third party vendors.</span></span> <span data-ttu-id="97537-137">Microsoft 还提供 MSDASQL，即架起与 ODBC 驱动程序的通信桥梁的 OLEDB 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="97537-137">Microsoft also provides MSDASQL, an OLEDB data provider that bridges communication to ODBC drivers.</span></span> <span data-ttu-id="97537-138">有关详细信息，请参阅 [ODBC 连接类型 (SSRS)](odbc-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="97537-138">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
 <span data-ttu-id="97537-139">若要成功检索到想要的数据，则必须提供数据访问接口支持的查询语法。</span><span class="sxs-lookup"><span data-stu-id="97537-139">To successfully retrieve the data that you want, you must provide query syntax that is supported by the data provider.</span></span> <span data-ttu-id="97537-140">参数支持因数据访问接口而异。</span><span class="sxs-lookup"><span data-stu-id="97537-140">Parameter support varies by data provider.</span></span> <span data-ttu-id="97537-141">有关详细信息，请参阅针对所选数据访问接口的主题。</span><span class="sxs-lookup"><span data-stu-id="97537-141">For more information, see topics that are specific to the data provider that you select.</span></span> <span data-ttu-id="97537-142">例如：</span><span class="sxs-lookup"><span data-stu-id="97537-142">For example:</span></span>  
  
-   [<span data-ttu-id="97537-143">Analysis Services OLE DB 提供程序（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="97537-143">Analysis Services OLE DB Provider &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../analysis-services/dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md)  
  
-   [<span data-ttu-id="97537-144">使用 .NET Framework Data Provider for Oracle</span><span class="sxs-lookup"><span data-stu-id="97537-144">Using the .NET Framework Data Provider for Oracle</span></span>](https://go.microsoft.com/fwlink/?LinkId=112314)  
  
-   [<span data-ttu-id="97537-145">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="97537-145">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 <span data-ttu-id="97537-146">有关特定 OLE DB 数据提供程序的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="97537-146">For more information about specific OLE DB data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="97537-147">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="97537-147">How-To Topics</span></span>  
 <span data-ttu-id="97537-148">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="97537-148">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="97537-149">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="97537-149">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="97537-150">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97537-150">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="97537-151">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97537-151">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a><span data-ttu-id="97537-152">相关部分</span><span class="sxs-lookup"><span data-stu-id="97537-152">Related Sections</span></span>  
 <span data-ttu-id="97537-153">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="97537-153">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="97537-154">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="97537-154">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="97537-155">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="97537-155">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="97537-156">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="97537-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="97537-157">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="97537-157">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="97537-158">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97537-158">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="97537-159">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="97537-159">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="97537-160">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97537-160">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="97537-161">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="97537-161">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="97537-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="97537-162">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="97537-163">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="97537-163">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="97537-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97537-164">See Also</span></span>  
 <span data-ttu-id="97537-165">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="97537-165">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="97537-166">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97537-166">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="97537-167">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97537-167">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
