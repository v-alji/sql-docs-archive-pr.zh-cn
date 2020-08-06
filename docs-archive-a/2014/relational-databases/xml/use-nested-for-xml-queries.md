---
title: 使用嵌套 FOR XML 查询 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 60c4198697f8d19c9b2e5bc1b415e0787861d40a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692298"
---
# <a name="use-nested-for-xml-queries"></a><span data-ttu-id="290c7-102">使用嵌套 FOR XML 查询</span><span class="sxs-lookup"><span data-stu-id="290c7-102">Use Nested FOR XML Queries</span></span>
  <span data-ttu-id="290c7-103">`xml`数据类型和[for xml 查询中的 type 指令](type-directive-in-for-xml-queries.md)允许在服务器和客户端上处理由 for xml 查询返回的 xml。</span><span class="sxs-lookup"><span data-stu-id="290c7-103">The `xml` data type and the [TYPE directive in FOR XML queries](type-directive-in-for-xml-queries.md) enable the XML returned by the FOR XML queries to be processed on the server as well as on the client.</span></span>  
  
## <a name="processing-with-xml-type-variables"></a><span data-ttu-id="290c7-104">使用 xml 类型变量进行处理</span><span class="sxs-lookup"><span data-stu-id="290c7-104">Processing with xml Type Variables</span></span>  
 <span data-ttu-id="290c7-105">您可以将 FOR XML 查询结果分配给 `xml` 类型变量，或使用 XQuery 查询结果，将该结果分配给 `xml` 类型变量以进行进一步处理。</span><span class="sxs-lookup"><span data-stu-id="290c7-105">You can assign the FOR XML query result to an `xml` type variable, or use XQuery to query the result, and assign that result to an `xml` type variable for more processing.</span></span>  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 <span data-ttu-id="290c7-106">还可以使用 `xml` 数据类型方法之一，处理在变量 `@x` 中返回的 XML。</span><span class="sxs-lookup"><span data-stu-id="290c7-106">You can additionally process the XML returned in the variable, `@x`, by using one of the `xml` data type methods.</span></span> <span data-ttu-id="290c7-107">例如，可以使用 `ProductModelID` value() 方法 [检索](/sql/t-sql/xml/value-method-xml-data-type)属性值。</span><span class="sxs-lookup"><span data-stu-id="290c7-107">For example, you can retrieve the `ProductModelID` attribute value by using the [value() method](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 <span data-ttu-id="290c7-108">在以下示例中，`FOR XML` 查询结果将以 `xml` 类型返回，因为在 `TYPE` 子句中已指定了 `FOR XML` 指令。</span><span class="sxs-lookup"><span data-stu-id="290c7-108">In the following example, the `FOR XML` query result is returned as an `xml` type, because the `TYPE` directive is specified in the `FOR XML` clause.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 <span data-ttu-id="290c7-109">结果如下：</span><span class="sxs-lookup"><span data-stu-id="290c7-109">This is the result:</span></span>  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 <span data-ttu-id="290c7-110">由于结果为 `xml` 类型，因此可以对此 XML 直接指定 `xml` 数据类型方法之一，如以下查询所示。</span><span class="sxs-lookup"><span data-stu-id="290c7-110">Because the result is of `xml` type, you can specify one of the `xml` data type methods directly against this XML, as shown in the following query.</span></span> <span data-ttu-id="290c7-111">在此查询中，[query() 方法（xml 数据类型）](/sql/t-sql/xml/query-method-xml-data-type)用于检索 <`myRoot`> 元素的第一个 <`row`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="290c7-111">In the query, the [query() method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) is used to retrieve the first <`row`> element child of the <`myRoot`> element.</span></span>  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 <span data-ttu-id="290c7-112">结果如下：</span><span class="sxs-lookup"><span data-stu-id="290c7-112">This is the result:</span></span>  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a><span data-ttu-id="290c7-113">将内部 FOR XML 查询的结果以 xml 类型实例的形式返回到外部查询</span><span class="sxs-lookup"><span data-stu-id="290c7-113">Returning Inner FOR XML Query Results to Outer Queries as xml Type Instances</span></span>  
 <span data-ttu-id="290c7-114">您可以编写嵌套 `FOR XML` 查询，其中内部查询的结果将以 `xml` 类型返回到外部查询。</span><span class="sxs-lookup"><span data-stu-id="290c7-114">You can write nested `FOR XML` queries where the result of the inner query is returned as an `xml` type to the outer query.</span></span> <span data-ttu-id="290c7-115">例如：</span><span class="sxs-lookup"><span data-stu-id="290c7-115">For example:</span></span>  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="290c7-116">请注意上述查询的以下方面：</span><span class="sxs-lookup"><span data-stu-id="290c7-116">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="290c7-117">将由内部 `FOR XML` 查询生成的 XML 添加到由外部 `FOR XML`生成的 XML。</span><span class="sxs-lookup"><span data-stu-id="290c7-117">The XML generated by the inner `FOR XML` query is added to the XML generated by the outer `FOR XML`.</span></span>  
  
-   <span data-ttu-id="290c7-118">内部查询指定 `TYPE` 指令。</span><span class="sxs-lookup"><span data-stu-id="290c7-118">The inner query specifies the `TYPE` directive.</span></span> <span data-ttu-id="290c7-119">因此，由内部查询返回的 XML 数据为 `xml` 类型。</span><span class="sxs-lookup"><span data-stu-id="290c7-119">Therefore, the XML data returned by the inner query is of `xml` type.</span></span> <span data-ttu-id="290c7-120">如果未指定 TYPE 指令，则将内部 `FOR XML` 查询的结果作为 `nvarchar(max)` 返回并对 XML 数据进行实体化。</span><span class="sxs-lookup"><span data-stu-id="290c7-120">If the TYPE directive is not specified, the result of the inner `FOR XML` query is returned as `nvarchar(max)` and the XML data is entitized.</span></span>  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a><span data-ttu-id="290c7-121">控制生成的 XML 数据的外形</span><span class="sxs-lookup"><span data-stu-id="290c7-121">Controlling the Shape of Resulting XML Data</span></span>  
 <span data-ttu-id="290c7-122">通过嵌套 FOR XML 查询，您在定义生成的 XML 数据的外形时可以进行更好的控制。</span><span class="sxs-lookup"><span data-stu-id="290c7-122">Nested FOR XML queries give you more control in defining the shape of the resulting XML data.</span></span> <span data-ttu-id="290c7-123">可以使用嵌套 FOR XML 查询将 XML 构造为部分以属性为中心、部分以元素为中心。</span><span class="sxs-lookup"><span data-stu-id="290c7-123">You can use nested FOR XML queries to construct XML that is partly attribute-centric and partly element-centric.</span></span>  
  
 <span data-ttu-id="290c7-124">有关使用嵌套 FOR XML 查询指定以属性为中心和以元素为中心的 XML 的详细信息，请参阅 [FOR XML 查询与嵌套 FOR XML 查询的比较](../xml/for-xml-query-compared-to-nested-for-xml-query.md) 和 [使用嵌套的 FOR XML 查询形成 XML](../xml/shape-xml-with-nested-for-xml-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="290c7-124">For more information about specifying both attribute-centric and element-centric XML with nested FOR XML queries, see [FOR XML Query Compared to Nested FOR XML Query](../xml/for-xml-query-compared-to-nested-for-xml-query.md) and [Shape XML with Nested FOR XML Queries](../xml/shape-xml-with-nested-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="290c7-125">可以通过指定嵌套 AUTO 模式的 FOR XML 查询生成包含同级的 XML 层次结构。</span><span class="sxs-lookup"><span data-stu-id="290c7-125">You can generate XML hierarchies that include siblings by specifying nested AUTO mode FOR XML queries.</span></span> <span data-ttu-id="290c7-126">有关详细信息，请参阅 [使用嵌套 AUTO 模式查询生成同级](../xml/generate-siblings-with-a-nested-auto-mode-query.md)。</span><span class="sxs-lookup"><span data-stu-id="290c7-126">For more information, see [Generate Siblings with a Nested AUTO Mode Query](../xml/generate-siblings-with-a-nested-auto-mode-query.md).</span></span>  
  
 <span data-ttu-id="290c7-127">不管使用哪种模式，嵌套 FOR XML 查询均可对说明生成的 XML 的外形进行更好的控制。</span><span class="sxs-lookup"><span data-stu-id="290c7-127">Regardless of which mode you use, nested FOR XML queries provide more control in describing the shape of the resulting XML.</span></span> <span data-ttu-id="290c7-128">可以使用这些查询替代 EXPLICIT 模式查询。</span><span class="sxs-lookup"><span data-stu-id="290c7-128">They can be used in the place of EXPLICIT mode queries.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="290c7-129">示例</span><span class="sxs-lookup"><span data-stu-id="290c7-129">Examples</span></span>  
 <span data-ttu-id="290c7-130">下列主题提供嵌套 FOR XML 查询的示例。</span><span class="sxs-lookup"><span data-stu-id="290c7-130">The following topics provide examples of nested FOR XML queries.</span></span>  
  
 [<span data-ttu-id="290c7-131">FOR XML 查询与嵌套 FOR XML 查询的比较</span><span class="sxs-lookup"><span data-stu-id="290c7-131">FOR XML Query Compared to Nested FOR XML Query</span></span>](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 <span data-ttu-id="290c7-132">将单一级别的 FOR XML 查询与嵌套 FOR XML 查询进行了比较。</span><span class="sxs-lookup"><span data-stu-id="290c7-132">Compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="290c7-133">此示例包含有关如何使查询结果同时包含以属性为中心和以元素为中心的 XML 的说明。</span><span class="sxs-lookup"><span data-stu-id="290c7-133">This example includes a demonstration of how to specify both attribute-centric and element-centric XML as the result of the query.</span></span>  
  
 [<span data-ttu-id="290c7-134">使用嵌套 AUTO 模式查询生成同级</span><span class="sxs-lookup"><span data-stu-id="290c7-134">Generate Siblings with a Nested AUTO Mode Query</span></span>](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 <span data-ttu-id="290c7-135">显示如何使用嵌套 AUTO 模式查询生成同级</span><span class="sxs-lookup"><span data-stu-id="290c7-135">Shows how to generate siblings by using a nested AUTO mode query</span></span>  
  
 [<span data-ttu-id="290c7-136">在 ASP.NET 中使用嵌套 FOR XML 查询</span><span class="sxs-lookup"><span data-stu-id="290c7-136">Use Nested FOR XML Queries in ASP.NET</span></span>](use-nested-for-xml-queries-in-asp-net.md)  
 <span data-ttu-id="290c7-137">说明 ASPX 应用程序如何使用 FOR XML 从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返回 XML。</span><span class="sxs-lookup"><span data-stu-id="290c7-137">Demonstrates how an ASPX application can use FOR XML to return XML from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="290c7-138">使用嵌套的 FOR XML 查询形成 XML</span><span class="sxs-lookup"><span data-stu-id="290c7-138">Shape XML with Nested FOR XML Queries</span></span>](../xml/shape-xml-with-nested-for-xml-queries.md)  
 <span data-ttu-id="290c7-139">显示如何使用嵌套 FOR XML 查询来控制由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]创建的 XML 文档的结构。</span><span class="sxs-lookup"><span data-stu-id="290c7-139">Shows how to use nested FOR XML queries to control the structure of an XML document created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
