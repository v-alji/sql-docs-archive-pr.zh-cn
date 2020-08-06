---
title: " (SQLXML 4.0) 的客户端 XML 格式设置 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4a680d79a25d24ebdf779b41fd3be5a5d6a605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588408"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="7a247-102">客户端 XML 格式化 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7a247-102">Client-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="7a247-103">本主题提供了有关客户端 XML 格式化的信息。</span><span class="sxs-lookup"><span data-stu-id="7a247-103">This topic provides information about client-side XML formatting.</span></span> <span data-ttu-id="7a247-104">客户端格式化是指对中间层上的 XML 的格式化。</span><span class="sxs-lookup"><span data-stu-id="7a247-104">Client-side formatting refers to the formatting of XML on the middle tier.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a247-105">本主题提供了有关使用客户端上的 FOR XML 子句的其他信息，并假定您已熟悉 FOR XML 子句。</span><span class="sxs-lookup"><span data-stu-id="7a247-105">This topic provides additional information about using the FOR XML clause on the client side, and assumes you are already familiar with the FOR XML clause.</span></span> <span data-ttu-id="7a247-106">有关 FOR XML 的详细信息，请参阅[使用 FOR Xml 构造 XML](../../xml/for-xml-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7a247-106">For more information about FOR XML, see [Constructing XML Using FOR XML](../../xml/for-xml-sql-server.md).</span></span>  
  
 <span data-ttu-id="7a247-107">**重要提示**若要将客户端 FOR XML 功能与新的 `xml` 数据类型一起使用，客户端应始终使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT (SQLNCLI11) 数据提供程序，而不是 SQLOLEDB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="7a247-107">**Important** To use client-side FOR XML functionality with the new `xml` data type, clients should always use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) data provider instead of the SQLOLEDB provider.</span></span> <span data-ttu-id="7a247-108">SQLNCLI11 为 SQL Server 访问接口的最新版本，且完全识别 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7a247-108">SQLNCLI11 is the latest version of the SQL Server provider and fully understands data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="7a247-109">使用 SQLOLEDB 访问接口的客户端 FOR XML 的行为会将 `xml` 数据类型视为字符串。</span><span class="sxs-lookup"><span data-stu-id="7a247-109">The behavior for client side FOR XML with the SQLOLEDB provider will treat `xml` data types as strings.</span></span>  
  
## <a name="formatting-xml-documents-on-the-client-side"></a><span data-ttu-id="7a247-110">对客户端上的 XML 文档进行格式化</span><span class="sxs-lookup"><span data-stu-id="7a247-110">Formatting XML Documents on the Client Side</span></span>  
 <span data-ttu-id="7a247-111">当客户端应用程序执行以下查询时：</span><span class="sxs-lookup"><span data-stu-id="7a247-111">When a client application executes the following query:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 <span data-ttu-id="7a247-112">...仅此部分的查询发送到服务器：</span><span class="sxs-lookup"><span data-stu-id="7a247-112">...only this part of the query is sent to the server:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 <span data-ttu-id="7a247-113">服务器执行查询，并返回包含 LastNamecolumns 的行集和客户端)  (。</span><span class="sxs-lookup"><span data-stu-id="7a247-113">The server executes the query and returns a rowset (which contains FirstName and LastNamecolumns) to the client.</span></span> <span data-ttu-id="7a247-114">然后，中间层对行集应用 FOR XML 转换，并将 XML 格式返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="7a247-114">The middle tier then applies the FOR XML transformation to the rowset and returns XML formatting to the client.</span></span>  
  
 <span data-ttu-id="7a247-115">同样，在您执行 XPath 查询时，服务器将行集返回到客户端，并对客户端上的行集应用 FOR XML EXPLICIT 转换，从而生成所需的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="7a247-115">Similarly, when you execute an XPath query, the server returns the rowset to the client and the FOR XML EXPLICIT transformation is applied to the rowset on the client, generating the desired XML formatting.</span></span>  
  
 <span data-ttu-id="7a247-116">下表显示了可以使用客户端 FOR XML 指定的模式。</span><span class="sxs-lookup"><span data-stu-id="7a247-116">The following table shows the modes you can specify with client-side FOR XML.</span></span>  
  
|<span data-ttu-id="7a247-117">客户端 FOR XML 模式</span><span class="sxs-lookup"><span data-stu-id="7a247-117">Client-side FOR XML mode</span></span>|<span data-ttu-id="7a247-118">评论</span><span class="sxs-lookup"><span data-stu-id="7a247-118">Comment</span></span>|  
|-------------------------------|-------------|  
|<span data-ttu-id="7a247-119">RAW</span><span class="sxs-lookup"><span data-stu-id="7a247-119">RAW</span></span>|<span data-ttu-id="7a247-120">在客户端或服务器端 FOR XML 中指定时产生相同的结果。</span><span class="sxs-lookup"><span data-stu-id="7a247-120">Produces identical results when specified in client-side or server-side FOR XML.</span></span>|  
|<span data-ttu-id="7a247-121">NESTED</span><span class="sxs-lookup"><span data-stu-id="7a247-121">NESTED</span></span>|<span data-ttu-id="7a247-122">与服务器端上的 FOR XML AUTO 模式类似。</span><span class="sxs-lookup"><span data-stu-id="7a247-122">Is similar to FOR XML AUTO mode on the server-side.</span></span>|  
|<span data-ttu-id="7a247-123">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="7a247-123">EXPLICIT</span></span>|<span data-ttu-id="7a247-124">与服务器端 FOR XML EXPLICIT 模式类似。</span><span class="sxs-lookup"><span data-stu-id="7a247-124">Is similar to server-side FOR XML EXPLICIT mode.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7a247-125">如果指定 AUTO 模式并请求客户端 XML 格式化，则整个查询将发送到服务器；即在服务器上进行 XML 格式化。</span><span class="sxs-lookup"><span data-stu-id="7a247-125">If you specify AUTO mode and request client-side XML formatting, the entire query is sent to the server; that is, XML formatting occurs on the server.</span></span> <span data-ttu-id="7a247-126">为了方便起见，执行此操作，但请注意，NESTED 模式会返回基表名称作为生成的 XML 文档中的元素名称。</span><span class="sxs-lookup"><span data-stu-id="7a247-126">This is done for convenience, but note that the NESTED mode returns base table names as element names in the XML document that is generated.</span></span> <span data-ttu-id="7a247-127">编写的某些应用程序可能需要基表名称。</span><span class="sxs-lookup"><span data-stu-id="7a247-127">Some of the applications you write might require base table names.</span></span> <span data-ttu-id="7a247-128">例如，您可能会执行存储过程并在数据集中加载生成的数据（[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中），然后生成 DiffGram 以更新表中的数据。</span><span class="sxs-lookup"><span data-stu-id="7a247-128">For example, you might execute a stored procedure and load the resulting data in a Dataset (in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework), and then later generate a DiffGram to update data in the tables.</span></span> <span data-ttu-id="7a247-129">在这种情况下，您需要基表信息且必须使用 NESTED 模式。</span><span class="sxs-lookup"><span data-stu-id="7a247-129">In such a case, you would need the base table information and you would have to use the NESTED mode.</span></span>  
  
## <a name="benefits-of-client-side-xml-formatting"></a><span data-ttu-id="7a247-130">客户端 XML 格式化的优点</span><span class="sxs-lookup"><span data-stu-id="7a247-130">Benefits of Client-side XML formatting</span></span>  
 <span data-ttu-id="7a247-131">以下是在客户端上进行 XML 格式化的一些优点。</span><span class="sxs-lookup"><span data-stu-id="7a247-131">The following are some benefits of formatting XML on the client.</span></span>  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a><span data-ttu-id="7a247-132">如果您在服务器上具有可返回单个行集的存储过程，则可请求客户端 FOR XML 转换以生成 XML。</span><span class="sxs-lookup"><span data-stu-id="7a247-132">If you have stored procedures on the server that return a single rowset, you can request client-side FOR XML transformation to generate an XML.</span></span>  
 <span data-ttu-id="7a247-133">例如，请考虑以下存储过程。</span><span class="sxs-lookup"><span data-stu-id="7a247-133">For example, consider the following stored procedure.</span></span> <span data-ttu-id="7a247-134">此过程将返回 AdventureWorks 数据库的 Person.Contact 表中的雇员名字和姓氏：</span><span class="sxs-lookup"><span data-stu-id="7a247-134">This procedure returns the first and last names of employees from the Person.Contact table in the AdventureWorks database:</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 <span data-ttu-id="7a247-135">以下 XML 模板示例将执行此存储过程。</span><span class="sxs-lookup"><span data-stu-id="7a247-135">The following sample XML template executes the stored procedure.</span></span> <span data-ttu-id="7a247-136">FOR XML 子句在存储过程名称之后指定。</span><span class="sxs-lookup"><span data-stu-id="7a247-136">The FOR XML clause is specified after the stored procedure name.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="7a247-137">因为**客户端-xml**特性设置为 1 () 模板中的 true），则将在服务器上执行存储过程，并将服务器返回的两列行集转换为中间层上的 xml 并返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="7a247-137">Because the **client-side-xml** attribute is set to 1 (true) in the template, the stored procedure is executed on the server and the two-column rowset that is returned by the server is transformed into XML on the middle tier and returned to the client.</span></span> <span data-ttu-id="7a247-138">（此处仅显示部分结果。）</span><span class="sxs-lookup"><span data-stu-id="7a247-138">(Only a partial result is shown here.)</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7a247-139">使用 SQLXMLOLEDB 访问接口或 SQLXML 托管类时，您可以使用 `ClientSideXml` 属性来请求客户端 XML 格式化。</span><span class="sxs-lookup"><span data-stu-id="7a247-139">When you are using the SQLXMLOLEDB Provider or SQLXML Managed Classes, you can use the `ClientSideXml` property to request client-side XML formatting.</span></span>  
  
### <a name="the-workload-is-more-balanced"></a><span data-ttu-id="7a247-140">工作负荷更加均衡。</span><span class="sxs-lookup"><span data-stu-id="7a247-140">The workload is more balanced.</span></span>  
 <span data-ttu-id="7a247-141">由于客户端进行 XML 格式化，因此会在服务器与客户端之间均衡工作负荷，从而释放服务器执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="7a247-141">Because the client does the XML formatting, the workload is balanced between the server and client, freeing the server to do other things.</span></span>  
  
## <a name="supporting-client-side-xml-formatting"></a><span data-ttu-id="7a247-142">支持客户端 XML 格式化</span><span class="sxs-lookup"><span data-stu-id="7a247-142">Supporting Client-side XML Formatting</span></span>  
 <span data-ttu-id="7a247-143">为了支持客户端 XML 格式化功能，SQLXML 提供：</span><span class="sxs-lookup"><span data-stu-id="7a247-143">To support the client-side XML formatting functionality, SQLXML provides:</span></span>  
  
-   <span data-ttu-id="7a247-144">SQLXMLOLEDB 访问接口</span><span class="sxs-lookup"><span data-stu-id="7a247-144">SQLXMLOLEDB Provider</span></span>  
  
-   <span data-ttu-id="7a247-145">SQLXML 托管类</span><span class="sxs-lookup"><span data-stu-id="7a247-145">SQLXML Managed Classes</span></span>  
  
-   <span data-ttu-id="7a247-146">增强的 XML 模板支持</span><span class="sxs-lookup"><span data-stu-id="7a247-146">Enhanced XML template support</span></span>  
  
-   <span data-ttu-id="7a247-147">SqlXmlCommand. ClientSideXml 属性</span><span class="sxs-lookup"><span data-stu-id="7a247-147">SqlXmlCommand.ClientSideXml property</span></span>  
  
     <span data-ttu-id="7a247-148">通过将 SQLXML 托管类的此属性设置为 True，可指定客户端格式。</span><span class="sxs-lookup"><span data-stu-id="7a247-148">You can specify client-side formatting by setting this property of the SQLXML managed classes to true.</span></span>  
  
## <a name="enhanced-xml-template-support"></a><span data-ttu-id="7a247-149">增强的 XML 模板支持</span><span class="sxs-lookup"><span data-stu-id="7a247-149">Enhanced XML Template Support</span></span>  
 <span data-ttu-id="7a247-150">从开始 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ，中的 XML 模板已 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通过添加**客户端-xml**特性得以增强。</span><span class="sxs-lookup"><span data-stu-id="7a247-150">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the XML template in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been enhanced with the addition of the **client-side-xml** attribute.</span></span> <span data-ttu-id="7a247-151">如果此属性设置为 True，将在客户端上进行 XML 格式化。</span><span class="sxs-lookup"><span data-stu-id="7a247-151">If this attribute is set to true, XML is formatted on the client.</span></span> <span data-ttu-id="7a247-152">请注意，此模板特性在功能上与特定于 SQLXMLOLEDB 提供程序的 ClientSideXML 属性相同。</span><span class="sxs-lookup"><span data-stu-id="7a247-152">Note that this template attribute is identical in functionality to the SQLXMLOLEDB Provider-specific ClientSideXML property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a247-153">如果你在使用 SQLXMLOLEDB 提供程序的 ADO 应用程序中执行 XML 模板，并且在模板中同时指定了**客户端-XML**特性和 Provider ClientSideXML 属性，则模板中指定的值优先。</span><span class="sxs-lookup"><span data-stu-id="7a247-153">If you execute an XML template in an ADO application that is using the SQLXMLOLEDB Provider, and you specify both the **client-side-xml** attribute in the template and the provider ClientSideXML property, the value specified in the template takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a247-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a247-154">See Also</span></span>  
 <span data-ttu-id="7a247-155">[&#40;SQLXML 4.0&#41;的客户端和服务器端 XML 格式的体系结构](server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-155">[Architecture of Client-side and Server-side XML Formatting &#40;SQLXML 4.0&#41;](server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7a247-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span></span>  
 <span data-ttu-id="7a247-157">[有关 &#40;SQLXML 4.0 的 XML 安全注意事项&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-157">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7a247-158">[SQLXML 4.0 中的 xml 数据类型支持](../xml-data-type-support-in-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-158">[xml Data Type Support in SQLXML 4.0](../xml-data-type-support-in-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7a247-159">[SQLXML 托管类](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-159">[SQLXML Managed Classes](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 <span data-ttu-id="7a247-160">[客户端与服务器端 XML 格式 &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-160">[Client-side vs. Server-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="7a247-161">[SQLXML 托管类 &#40;的 SqlXmlCommand 对象&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span><span class="sxs-lookup"><span data-stu-id="7a247-161">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span></span>  
 [<span data-ttu-id="7a247-162">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7a247-162">XML Data &#40;SQL Server&#41;</span></span>](../../xml/xml-data-sql-server.md)  
  
  
