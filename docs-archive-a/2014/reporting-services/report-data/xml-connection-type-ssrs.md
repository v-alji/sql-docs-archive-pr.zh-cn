---
title: XML 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b55fff2-1b15-4156-83ef-15ad9cf9f509
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 141f6449e0493ba7a12e9270bedab967b7795ee0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692745"
---
# <a name="xml-connection-type-ssrs"></a><span data-ttu-id="9136f-102">XML 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="9136f-102">XML Connection Type (SSRS)</span></span>
  <span data-ttu-id="9136f-103">若要在报表中包含来自 XML 数据源的数据，则必须拥有一个基于 XML 类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="9136f-103">To include data from an XML data source in your report, you must have a dataset that is based on a report data source of type XML.</span></span> <span data-ttu-id="9136f-104">此内置数据源类型基于 XML 数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="9136f-104">This built-in data source type is based on the XML data extension.</span></span> <span data-ttu-id="9136f-105">使用此数据源类型可连接到 XML 文档、Web 服务、或查询中嵌入的 XML 并从中检索数据。</span><span class="sxs-lookup"><span data-stu-id="9136f-105">Use this data source type to connect to and retrieve data from XML documents, Web services, or XML that is embedded in the query.</span></span>  
  
 <span data-ttu-id="9136f-106">此数据扩展插件支持参数和与连接字符串分开管理的凭据。</span><span class="sxs-lookup"><span data-stu-id="9136f-106">This data extension supports parameters and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="9136f-107">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="9136f-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="9136f-108">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="9136f-109">连接字符串</span><span class="sxs-lookup"><span data-stu-id="9136f-109">Connection String</span></span>  
 <span data-ttu-id="9136f-110">连接字符串必须为指向 Web 服务、基于 Web 的应用程序或可通过 HTTP 使用的 XML 文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="9136f-110">The connection string must be a URL that points to the Web service, Web-based application, or XML document available through HTTP.</span></span> <span data-ttu-id="9136f-111">XML 文档必须具有 XML 扩展名。</span><span class="sxs-lookup"><span data-stu-id="9136f-111">XML documents must have the XML extension.</span></span> <span data-ttu-id="9136f-112">还可以对数据集查询中嵌入的 XML 数据使用空连接字符串。</span><span class="sxs-lookup"><span data-stu-id="9136f-112">You can also use an empty connection string for XML data embedded in the dataset query.</span></span>  
  
 <span data-ttu-id="9136f-113">下面的示例对 Web 服务器和 XML 文档的连接字符串语法分别进行了说明。</span><span class="sxs-lookup"><span data-stu-id="9136f-113">The following examples illustrate the connection string syntax for a Web service and XML document, respectively.</span></span> <span data-ttu-id="9136f-114">不支持 `file://` 协议。</span><span class="sxs-lookup"><span data-stu-id="9136f-114">The `file://` protocol is not supported.</span></span>  
  
|<span data-ttu-id="9136f-115">XML 文档类型</span><span class="sxs-lookup"><span data-stu-id="9136f-115">XML document type</span></span>|<span data-ttu-id="9136f-116">连接字符串示例</span><span class="sxs-lookup"><span data-stu-id="9136f-116">Connection String Example</span></span>|  
|-----------------------|-------------------------------|  
|<span data-ttu-id="9136f-117">Web 服务</span><span class="sxs-lookup"><span data-stu-id="9136f-117">Web service</span></span>|`http://adventure-works.com/results.aspx`|  
|<span data-ttu-id="9136f-118">XML 文档</span><span class="sxs-lookup"><span data-stu-id="9136f-118">XML document</span></span>|`http://localhost/XML/Customers.xml`|  
|<span data-ttu-id="9136f-119">嵌入的 XML 文档</span><span class="sxs-lookup"><span data-stu-id="9136f-119">Embedded XML document</span></span>|<span data-ttu-id="9136f-120">*Empty*</span><span class="sxs-lookup"><span data-stu-id="9136f-120">*Empty*</span></span>|  
  
 <span data-ttu-id="9136f-121">有关更多连接字符串的示例，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-121">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="9136f-122">凭据</span><span class="sxs-lookup"><span data-stu-id="9136f-122">Credentials</span></span>  
 <span data-ttu-id="9136f-123">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="9136f-123">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="9136f-124">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="9136f-124">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="9136f-125">在报表创作客户端，可以使用下列选项指定凭据：</span><span class="sxs-lookup"><span data-stu-id="9136f-125">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="9136f-126">当前 Windows 用户（也称为集成安全性）。</span><span class="sxs-lookup"><span data-stu-id="9136f-126">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="9136f-127">不需要提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="9136f-127">No credentials are required.</span></span> <span data-ttu-id="9136f-128">如果选择不使用任何凭据，则将使用匿名访问。</span><span class="sxs-lookup"><span data-stu-id="9136f-128">If you select no credentials, Anonymous access is used.</span></span> <span data-ttu-id="9136f-129">请确保您已为报表服务器定义了无人参与的执行帐户以连接到外部数据源。</span><span class="sxs-lookup"><span data-stu-id="9136f-129">Make sure that you have defined the unattended execution account for the report server to connect to an external data source.</span></span> <span data-ttu-id="9136f-130">XML 数据处理扩展插件不会将凭据传递到目标 URL 或 Web 服务；只有在定义了无人参与的执行帐户之后，连接才会成功。</span><span class="sxs-lookup"><span data-stu-id="9136f-130">The XML data processing extension does not pass credentials to the target URL or the Web service; the connection will be unsuccessful unless you have defined the unattended execution account.</span></span> <span data-ttu-id="9136f-131">有关详细信息，请参阅 msdn.microsoft.com 上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-131">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="9136f-132">不支持存储的凭据和提示的凭据。</span><span class="sxs-lookup"><span data-stu-id="9136f-132">Stored and prompted credentials are not supported.</span></span> <span data-ttu-id="9136f-133">注意，如果禁用 Windows 集成安全性，则无法使用它来检索数据。</span><span class="sxs-lookup"><span data-stu-id="9136f-133">Remember that if you disable Windows integrated security, you cannot use it to retrieve data.</span></span> <span data-ttu-id="9136f-134">如果指定了存储凭据或提示凭据，则会在执行时发生错误。</span><span class="sxs-lookup"><span data-stu-id="9136f-134">If you specify stored or prompted credentials, an error will occur at run time.</span></span>  
  
 <span data-ttu-id="9136f-135">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-135">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="9136f-136">查询</span><span class="sxs-lookup"><span data-stu-id="9136f-136">Queries</span></span>  
 <span data-ttu-id="9136f-137">查询指定了要为报表数据集检索哪些数据。</span><span class="sxs-lookup"><span data-stu-id="9136f-137">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="9136f-138">查询的结果集中的列填充数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="9136f-138">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="9136f-139">报表仅处理查询检索的第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="9136f-139">A report processes only the first result set retrieved by a query.</span></span>  
  
 <span data-ttu-id="9136f-140">必须使用基于文本的查询设计器创建查询。</span><span class="sxs-lookup"><span data-stu-id="9136f-140">You must use the text-based query designer to create the query.</span></span> <span data-ttu-id="9136f-141">查询必须返回 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="9136f-141">The query must return XML data.</span></span>  
  
 <span data-ttu-id="9136f-142">有关基于文本的查询设计器的详细信息，请参阅[基于文本的查询设计器用户界面（报表生成器）](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-142">For more information about the text-based query designer, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="9136f-143">下面显示当数据源为 XML 类型时数据集查询的可能值。</span><span class="sxs-lookup"><span data-stu-id="9136f-143">The possible values for a dataset query for a data source that is type XML are shown below.</span></span>  
  
-   <span data-ttu-id="9136f-144">*空*：使用空查询创建默认结果集。</span><span class="sxs-lookup"><span data-stu-id="9136f-144">*Empty*: Use an empty query to create a default result set.</span></span> <span data-ttu-id="9136f-145">默认查询是通过读取数据源并遍历到 XML 节点层次结构的第一个叶集合来创建的。</span><span class="sxs-lookup"><span data-stu-id="9136f-145">The default query is created by reading the data source and traversing the XML node hierarchy to the first leaf collection.</span></span> <span data-ttu-id="9136f-146">结果集包括具有文本值的所有节点以及沿该路径的所有节点属性。</span><span class="sxs-lookup"><span data-stu-id="9136f-146">The result set includes all nodes with text values and all node attributes along that path.</span></span> <span data-ttu-id="9136f-147">结果集中的列将映射到数据集的字段。</span><span class="sxs-lookup"><span data-stu-id="9136f-147">Columns in the result set are mapped to fields for the dataset.</span></span>  
  
-   <span data-ttu-id="9136f-148">元素路径：指定从数据源中检索 XML 数据时要使用的节点序列。</span><span class="sxs-lookup"><span data-stu-id="9136f-148">An element path: Specifies the sequence of nodes to use when retrieving XML data from the data source.</span></span>  
  
-   <span data-ttu-id="9136f-149">XML 查询元素：具有以下可选元素的 XML 查询规范：</span><span class="sxs-lookup"><span data-stu-id="9136f-149">An XML Query element: An XML query specification with the following optional elements:</span></span>  
  
    -   <span data-ttu-id="9136f-150">**对于 Web 服务：**</span><span class="sxs-lookup"><span data-stu-id="9136f-150">**For a Web service:**</span></span>  
  
         <span data-ttu-id="9136f-151">必需的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="9136f-151">Required XML Elements:</span></span>  
  
         <span data-ttu-id="9136f-152">`<Method Namespace=`*"namespace"*  `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="9136f-152">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="9136f-153">`<SoapAction>` *soap action* `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="9136f-153">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
         <span data-ttu-id="9136f-154">可选的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="9136f-154">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="9136f-155">`<ElementPath>`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="9136f-155">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         <span data-ttu-id="9136f-156">`<Method Namespace=`*"namespace"*  `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="9136f-156">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="9136f-157">`<SoapAction>` *soap action* `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="9136f-157">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
    -   <span data-ttu-id="9136f-158">**对于 XML 文档：**</span><span class="sxs-lookup"><span data-stu-id="9136f-158">**For an XML document:**</span></span>  
  
         <span data-ttu-id="9136f-159">可选的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="9136f-159">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="9136f-160">`<ElementPath>`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="9136f-160">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
    -   <span data-ttu-id="9136f-161">**对于嵌入的 XML 文档：**</span><span class="sxs-lookup"><span data-stu-id="9136f-161">**For an embedded XML document:**</span></span>  
  
         <span data-ttu-id="9136f-162">必需的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="9136f-162">Required XML Elements:</span></span>  
  
         <span data-ttu-id="9136f-163">`<XmlData>` 内部 XML `</XmlData>`</span><span class="sxs-lookup"><span data-stu-id="9136f-163">`<XmlData>` inner XML `</XmlData>`</span></span>  
  
         <span data-ttu-id="9136f-164">可选的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="9136f-164">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="9136f-165">`<ElementPath>`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="9136f-165">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="9136f-166">`<ElementPath IgnoreNamespaces="true">`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="9136f-166">`<ElementPath IgnoreNamespaces="true">`  *element path*  `</ElementPath>`</span></span>  
  
 <span data-ttu-id="9136f-167">有关查询语法的详细信息，请参阅 msdn.microsoft.com 上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的[用于 XML 报表数据的 XML 查询语法 (SSRS)](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-167">For more information about query syntax, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="9136f-168">有关示例，请参阅 [Reporting Services: Using XML and Web Service Data Sources（Reporting Services：使用 XML 和 Web 服务数据源）](https://go.microsoft.com/fwlink/?LinkId=81654)。</span><span class="sxs-lookup"><span data-stu-id="9136f-168">For examples, see [Reporting Services: Using XML and Web Service Data Sources](https://go.microsoft.com/fwlink/?LinkId=81654).</span></span>  
  
### <a name="requirements-for-retrieving-xml-web-service-data"></a><span data-ttu-id="9136f-169">检索 XML Web 服务数据的要求</span><span class="sxs-lookup"><span data-stu-id="9136f-169">Requirements for Retrieving XML Web Service Data</span></span>  
 <span data-ttu-id="9136f-170">XML 数据处理扩展插件不能检测架构。</span><span class="sxs-lookup"><span data-stu-id="9136f-170">The XML data processing extension does not detect the schema for you.</span></span> <span data-ttu-id="9136f-171">因此，您必须通过某种方式来发现哪些 SOAP 方法将检索所需数据。</span><span class="sxs-lookup"><span data-stu-id="9136f-171">Therefore, you must have some way of discovering which SOAP methods will retrieve the data that you want.</span></span> <span data-ttu-id="9136f-172">您还必须了解 Web 服务用于其数据的寻址方案或命名空间。</span><span class="sxs-lookup"><span data-stu-id="9136f-172">You must also understand the addressing scheme or namespace that the Web service uses for its data.</span></span>  
  
 <span data-ttu-id="9136f-173">对于 Web 服务，可以提供一个 <`Query`> 元素来指定要调用的方法或 SOAP 操作。</span><span class="sxs-lookup"><span data-stu-id="9136f-173">For a Web service, you can provide a <`Query`> element that specifies a method to call or SOAP action.</span></span> <span data-ttu-id="9136f-174">如果 XML 数据源具有可产生要用于报表的数据的层次结构，则可以将查询留空并使用默认查询。</span><span class="sxs-lookup"><span data-stu-id="9136f-174">You can leave the query empty and use the default query if the XML data source has a hierarchical structure that produces the data that you want to use for your report.</span></span> <span data-ttu-id="9136f-175">查询运行时检索的 XML 元素节点值和属性将映射到在报表中使用的数据集字段。</span><span class="sxs-lookup"><span data-stu-id="9136f-175">XML element node values and attributes retrieved when the query runs map to the dataset fields you use in your report.</span></span>  
  
### <a name="requirements-for-retrieving-xml-document-data"></a><span data-ttu-id="9136f-176">检索 XML 文档数据的要求</span><span class="sxs-lookup"><span data-stu-id="9136f-176">Requirements for Retrieving XML Document Data</span></span>  
 <span data-ttu-id="9136f-177">使用 http 协议时，服务器必须返回 XML 数据，或者 XML 数据必须嵌入 XML `Query` 元素中。</span><span class="sxs-lookup"><span data-stu-id="9136f-177">Using the http protocol, the server must return XML data or the XML data must be embedded in the XML `Query` element.</span></span> <span data-ttu-id="9136f-178">如果您使用 http 协议直接引用 XML 文档，则文档的扩展名必须为 .xml。</span><span class="sxs-lookup"><span data-stu-id="9136f-178">If you refer to an XML document directly using the http protocol, the extension must be .xml.</span></span>  
  
 <span data-ttu-id="9136f-179">您必须了解如何创建 XML 查询来检索所需的所有数据。</span><span class="sxs-lookup"><span data-stu-id="9136f-179">You must know how to create an XML query that retrieves all the data you need.</span></span> <span data-ttu-id="9136f-180">如果不指定元素路径，则默认的 XML 文档分析行为是选择 XML 文档中指向叶节点集合的第一个可用路径。</span><span class="sxs-lookup"><span data-stu-id="9136f-180">If you do not specify an element path, the default behavior for parsing an XML document is to select the first available path to a leaf-node collection in the XML document.</span></span> <span data-ttu-id="9136f-181">如果 XML 文档包括指向其他同级叶节点集合的其他路径，则除非在查询中指定一个路径，否则将忽略这些节点。</span><span class="sxs-lookup"><span data-stu-id="9136f-181">If the XML document includes additional paths to other sibling leaf-node collections, those nodes will be ignored unless you specify a path in your query.</span></span>  
  
 <span data-ttu-id="9136f-182">可以使用与 XQuery 类似的 XML 语法提供元素路径。</span><span class="sxs-lookup"><span data-stu-id="9136f-182">You can provide an element path using XML syntax similar to XQuery.</span></span>  
  
 <span data-ttu-id="9136f-183">有关详细信息，请参阅 msdn.microsoft.com 上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的[用于 XML 报表数据的元素路径语法 (SSRS)](element-path-syntax-for-xml-report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-183">For more information, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](element-path-syntax-for-xml-report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="9136f-184">Parameters</span><span class="sxs-lookup"><span data-stu-id="9136f-184">Parameters</span></span>  
 <span data-ttu-id="9136f-185">系统不会对查询进行分析以标识参数。</span><span class="sxs-lookup"><span data-stu-id="9136f-185">The query is not analyzed to identify parameters.</span></span>  
  
 <span data-ttu-id="9136f-186">若要添加参数，必须通过“ **数据集属性** ”对话框中的 [“参数”](../dataset-properties-dialog-box-parameters-report-builder.md) 页手动创建参数。</span><span class="sxs-lookup"><span data-stu-id="9136f-186">To add parameters, you must create them manually through the **Parameter** page on the [Dataset Properties](../dataset-properties-dialog-box-parameters-report-builder.md) dialog box.</span></span>  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="9136f-187">注释</span><span class="sxs-lookup"><span data-stu-id="9136f-187">Remarks</span></span>  
 <span data-ttu-id="9136f-188">XML 数据扩展插件支持基于 XML 数据（表格格式且不分层）生成报表。</span><span class="sxs-lookup"><span data-stu-id="9136f-188">The XML data extension supports reporting from XML data that is tabular and not hierarchical.</span></span> <span data-ttu-id="9136f-189">有关详细信息，请参阅[从外部数据源中添加数据 (SSRS)](add-data-from-external-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-189">For more information, see [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="9136f-190">不提供从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库检索 XML 文档的内置支持。</span><span class="sxs-lookup"><span data-stu-id="9136f-190">There is no built-in support for retrieving XML documents from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="9136f-191">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="9136f-191">How-To Topics</span></span>  
 <span data-ttu-id="9136f-192">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="9136f-192">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="9136f-193">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9136f-193">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="9136f-194">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9136f-194">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="9136f-195">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9136f-195">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
##  <a name="related-sections"></a><a name="Related"></a><span data-ttu-id="9136f-196">相关部分</span><span class="sxs-lookup"><span data-stu-id="9136f-196">Related Sections</span></span>  
 <span data-ttu-id="9136f-197">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="9136f-197">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="9136f-198">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9136f-198">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="9136f-199">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="9136f-199">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="9136f-200">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="9136f-200">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="9136f-201">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="9136f-201">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="9136f-202">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9136f-202">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="9136f-203">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="9136f-203">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="9136f-204">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9136f-204">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="9136f-205">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="9136f-205">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="9136f-206">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="9136f-206">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="9136f-207">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9136f-207">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9136f-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9136f-208">See Also</span></span>  
 <span data-ttu-id="9136f-209">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="9136f-209">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="9136f-210">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9136f-210">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9136f-211">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9136f-211">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
