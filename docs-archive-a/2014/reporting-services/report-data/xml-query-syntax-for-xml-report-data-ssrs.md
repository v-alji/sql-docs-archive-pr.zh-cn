---
title: 用于 XML 报表数据的 XML 查询语法 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62dde2b3ab18b5edb5c3786d39173fea3a0854ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577299"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="0a3e5-102">用于 XML 报表数据的 XML 查询语法 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0a3e5-102">XML Query Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="0a3e5-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，可以为 XML 数据源创建数据集。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can create datasets for XML data sources.</span></span> <span data-ttu-id="0a3e5-104">定义数据源后，可以为数据集创建查询。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-104">After you define a data source, you create a query for the dataset.</span></span> <span data-ttu-id="0a3e5-105">根据数据源所指向的 XML 数据类型，可以通过包括 XML `Query` 或元素路径来创建数据集查询。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-105">Depending on the type of XML data pointed to by the data source, you create the dataset query by including an XML `Query` or an element path.</span></span> <span data-ttu-id="0a3e5-106">XML 以 `Query` **\<Query>** 标记开头，并包含因数据源而异的命名空间和 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-106">An XML `Query` starts with a **\<Query>** tag and includes namespaces and XML elements that vary depending on the data source.</span></span> <span data-ttu-id="0a3e5-107">元素路径与命名空间无关，它使用与 XPath 类似的语法指定要使用的来自基础 XML 数据的节点和节点属性。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-107">An element path is namespace-independent and specifies which nodes and node attributes to use from the underlying XML data with an XPath-like syntax.</span></span> <span data-ttu-id="0a3e5-108">有关元素路径的详细信息，请参阅[用于 XML 报表数据的元素路径语法 (SSRS)](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-108">For more information about element paths, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="0a3e5-109">可以为以下类型的 XML 数据创建 XML 数据源：</span><span class="sxs-lookup"><span data-stu-id="0a3e5-109">You can create an XML data source for the following types of XML data:</span></span>  
  
-   <span data-ttu-id="0a3e5-110">URL 使用 http 协议指向的 Xml 文档</span><span class="sxs-lookup"><span data-stu-id="0a3e5-110">Xml documents pointed to by a URL using http protocol</span></span>  
  
-   <span data-ttu-id="0a3e5-111">返回 XML 数据的 Web 服务端点</span><span class="sxs-lookup"><span data-stu-id="0a3e5-111">Web service endpoints that return XML data</span></span>  
  
-   <span data-ttu-id="0a3e5-112">嵌入的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="0a3e5-112">Embedded XML data</span></span>  
  
 <span data-ttu-id="0a3e5-113">指定 XML `Query` 或元素路径的方式取决于 XML 数据的类型。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-113">How you specify an XML `Query` or an element path depends on the type of XML data.</span></span>  
  
 <span data-ttu-id="0a3e5-114">对于 XML 文档，XML `Query` 是可选的。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-114">For an XML document, the XML `Query` is optional.</span></span> <span data-ttu-id="0a3e5-115">如果包括它，则它可以包含可选的 XML `ElementPath`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-115">If it is included, it can contain an optional XML `ElementPath`.</span></span> <span data-ttu-id="0a3e5-116">XML `ElementPath` 的值使用元素路径语法。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-116">The value of the XML `ElementPath` uses the element path syntax.</span></span> <span data-ttu-id="0a3e5-117">您可以包含 XML `Query` 和 XML `ElementPath`，以便当数据源中的 XML 数据需要命名空间时能正确处理该命名空间。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-117">You include the XML `Query` and XML `ElementPath` to process namespaces correctly when it is needed by the XML data from the data source.</span></span>  
  
 <span data-ttu-id="0a3e5-118">对于连接字符串 URL 指向的 Web 服务端点，XML `Query` 定义 Web 服务方法和/或 SOAP 操作。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-118">For a Web service endpoint pointed to by a connection string URL, the XML `Query` defines either the Web service method, the SOAP action, or both.</span></span> <span data-ttu-id="0a3e5-119">XML 数据提供程序将创建 Web 服务请求，以检索要用于报表的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-119">The XML data provider creates a Web service request that retrieves XML data to use for the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a3e5-120">当 Web 服务命名空间包括正斜杠 (`/)` 字符时，应同时包括 Web 服务方法和 SOAP 操作，以使 XML 数据处理扩展插件可以正确派生命名空间。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-120">When a Web service namespace includes a forward slash (`/)` character, include both the Web service method and the SOAP action so that the XML data processing extension can derive the namespace correctly.</span></span>  
  
 <span data-ttu-id="0a3e5-121">对于嵌入的 XML 文档，XML `Query` 定义要使用的嵌入 XML 数据、包括可选命名空间并包含可选的 XML `ElementPath`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-121">For an embedded XML document, the XML `Query` defines the embedded XML data to use, includes optional namespaces, and contains an optional XML `ElementPath`..</span></span>  
  
## <a name="specifying-query-parameters-for-xml-data"></a><span data-ttu-id="0a3e5-122">指定 XML 数据的查询参数</span><span class="sxs-lookup"><span data-stu-id="0a3e5-122">Specifying Query Parameters for XML Data</span></span>  
 <span data-ttu-id="0a3e5-123">可以为 XML 文档指定查询参数。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-123">You can specify query parameters for XML documents.</span></span>  
  
-   <span data-ttu-id="0a3e5-124">对于 URL 请求，查询参数以标准 URL 参数的形式包含在查询中。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-124">For URL requests, the query parameters are included as standard URL parameters.</span></span>  
  
-   <span data-ttu-id="0a3e5-125">对于 Web 服务请求，需要将查询参数传递给 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-125">For Web service requests, query parameters are passed to the Web service method.</span></span> <span data-ttu-id="0a3e5-126">若要定义查询参数，请使用 **“数据集属性”** 对话框的 **“参数”** 页。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-126">To define a query parameter, use the **Parameters** page of the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="0a3e5-127">有关详细信息，请参阅 [“数据集属性”对话框 - 参数](dataset-properties-dialog-box-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-127">For more information, see [Dataset Properties Dialog Box, Parameters](dataset-properties-dialog-box-parameters.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a3e5-128">示例</span><span class="sxs-lookup"><span data-stu-id="0a3e5-128">Example</span></span>  
 <span data-ttu-id="0a3e5-129">下表中的示例说明如何从报表服务器 Web 服务、XML 文档和嵌入的 XML 数据中检索数据。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-129">The examples in the following table illustrate how to retrieve data from the Report Server Web service, an XML document, and embedded XML data.</span></span>  
  
|<span data-ttu-id="0a3e5-130">XML 数据源</span><span class="sxs-lookup"><span data-stu-id="0a3e5-130">XML data source</span></span>|<span data-ttu-id="0a3e5-131">查询示例</span><span class="sxs-lookup"><span data-stu-id="0a3e5-131">Query example</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="0a3e5-132">使用 ListChildren 方法获得的 Web 服务 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-132">Web service XML data from ListChildren method.</span></span>|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="https://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|<span data-ttu-id="0a3e5-133">使用 SoapAction 获得的 Web 服务 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-133">Web service XML data from SoapAction.</span></span>|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|<span data-ttu-id="0a3e5-134">使用命名空间的 XML 文档或嵌入的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-134">XML Document or embedded XML data that uses namespaces.</span></span><br /><br /> <span data-ttu-id="0a3e5-135">为元素路径指定命名空间的查询元素。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-135">Query element specifying namespaces for an element path.</span></span>|`<Query xmlns:es="https://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="0a3e5-136">嵌入的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-136">Embedded XML document.</span></span>|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="0a3e5-137">使用默认值的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-137">XML document that uses default.</span></span>|<span data-ttu-id="0a3e5-138">*No query*。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-138">*No query*.</span></span><br /><br /> <span data-ttu-id="0a3e5-139">元素路径是从 XML 文档本身派生而来的，并且与命名空间无关。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-139">The element path is derived from the XML document itself and is namespace-independent.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="0a3e5-140">第一个 Web 服务示例列出了使用 <xref:ReportService2006.ReportingService2006.ListChildren%2A> 方法获得的 Web 服务 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-140">The first Web service example lists the contents of the report server that uses the <xref:ReportService2006.ReportingService2006.ListChildren%2A> method.</span></span> <span data-ttu-id="0a3e5-141">若要运行此查询，必须创建新的数据源并将连接字符串设置为 http://localhost/reportserver/reportservice2006.asmx。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-141">To run this query, you must create a new data source and set the connection string to http://localhost/reportserver/reportservice2006.asmx.</span></span> <span data-ttu-id="0a3e5-142"><xref:ReportService2006.ReportingService2006.ListChildren%2A> 方法有两个参数：`Item` 和 `Recursive`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-142">The <xref:ReportService2006.ReportingService2006.ListChildren%2A> method takes two parameters: `Item` and `Recursive`.</span></span> <span data-ttu-id="0a3e5-143">将 `Item` 的默认值设置为 `/` 并将 `Recursive` 设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-143">Set the default value for `Item` to `/` and `Recursive` to `1`.</span></span>  
  
## <a name="specifying-namespaces"></a><span data-ttu-id="0a3e5-144">指定命名空间</span><span class="sxs-lookup"><span data-stu-id="0a3e5-144">Specifying Namespaces</span></span>  
 <span data-ttu-id="0a3e5-145">使用 XML `Query` 元素可以指定在数据源的 XML 数据中使用的命名空间。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-145">Use the XML `Query` element to specify the namespaces that are used in the XML data from the data source.</span></span> <span data-ttu-id="0a3e5-146">下面的 XML 查询使用命名空间 `sales`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-146">The following XML query uses the namespace `sales`.</span></span> <span data-ttu-id="0a3e5-147">`sales:LineItems` 和 `sales:LineItem` 的 XML `ElementPath` 节点使用命名空间 `sales`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-147">The XML `ElementPath` nodes for `sales:LineItems` and `sales:LineItem` use the namespace `sales`.</span></span>  
  
```  
<Query xmlns:sales=  
"https://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      https://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 <span data-ttu-id="0a3e5-148">若要指定数据提供程序命名空间以使默认的命名空间保持为空，请使用 `xmldp`。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-148">To specify the data provider namespace so that the default namespace remains empty, use `xmldp`.</span></span> <span data-ttu-id="0a3e5-149">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-149">This is shown in the following example.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a3e5-150">示例</span><span class="sxs-lookup"><span data-stu-id="0a3e5-150">Example</span></span>  
 <span data-ttu-id="0a3e5-151">以下示例使用 XML 文档 DPNamespace.xml，该表之后提供了该文档以进行说明。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-151">The following examples use the XML document DPNamespace.xml, which is provided for illustration after the table.</span></span> <span data-ttu-id="0a3e5-152">此表显示了包括命名空间前缀的 XML ElementPath 语法的两个示例。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-152">This table shows two examples of XML ElementPath syntax that includes namespace prefixes.</span></span>  
  
|<span data-ttu-id="0a3e5-153">XML 查询元素</span><span class="sxs-lookup"><span data-stu-id="0a3e5-153">XML Query Element</span></span>|<span data-ttu-id="0a3e5-154">数据集中的结果字段</span><span class="sxs-lookup"><span data-stu-id="0a3e5-154">Resulting fields in the dataset</span></span>|  
|-----------------------|-------------------------------------|  
|\<Query/>|<span data-ttu-id="0a3e5-155">值 A： `https://schemas.microsoft.com/..` 。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-155">Value A: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="0a3e5-156">值 B： `https://schemas.microsoft.com/..` 。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-156">Value B: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="0a3e5-157">值 `https://schemas.microsoft.com/.` C：。。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-157">Value C: `https://schemas.microsoft.com/.`..</span></span>|  
|\<xmldp:Query xmlns:xmldp="https://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns="https://schemas.microsoft.com/..."><br /><br /> <span data-ttu-id="0a3e5-158">\<xmldp:ElementPath>Root {} /ns： Element2/Node\</xmldp:ElementPath></span><span class="sxs-lookup"><span data-stu-id="0a3e5-158">\<xmldp:ElementPath>Root {}/ns:Element2/Node\</xmldp:ElementPath></span></span><br /><br /> \</xmldp:Query>|<span data-ttu-id="0a3e5-159">值 D</span><span class="sxs-lookup"><span data-stu-id="0a3e5-159">Value D</span></span><br /><br /> <span data-ttu-id="0a3e5-160">值 E</span><span class="sxs-lookup"><span data-stu-id="0a3e5-160">Value E</span></span><br /><br /> <span data-ttu-id="0a3e5-161">值 F</span><span class="sxs-lookup"><span data-stu-id="0a3e5-161">Value F</span></span>|  
  
#### <a name="xml-document-dpnamespacexml"></a><span data-ttu-id="0a3e5-162">XML 文档：DPNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="0a3e5-162">XML document: DPNamespace.xml</span></span>  
 <span data-ttu-id="0a3e5-163">可以复制此 XML 并将其保存到报表设计器可访问的 URL 以用作 XML 数据源：例如 http://localhost/DPNamespace.xml。</span><span class="sxs-lookup"><span data-stu-id="0a3e5-163">You can copy this XML and save it to a URL available for Report Designer to use as an XML data source: for example, http://localhost/DPNamespace.xml.</span></span>  
  
```  
<Root xmlns:ns="https://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a3e5-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a3e5-164">See Also</span></span>  
 <span data-ttu-id="0a3e5-165">[XML 连接类型 &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a3e5-165">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="0a3e5-166">Reporting Services 教程 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0a3e5-166">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
