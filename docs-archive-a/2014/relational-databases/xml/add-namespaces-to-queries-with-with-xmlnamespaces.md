---
title: 使用 WITH XMLNAMESPACES 将命名空间添加到查询 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTS XSINIL directive
- adding namespaces
- XSINIL directive
- default namespaces
- queries [XML in SQL Server], WITH XMLNAMESPACES clause
- predefined namespaces [XML in SQL Server]
- FOR XML clause, WITH XMLNAMESPACES clause
- namespaces [XML in SQL Server]
- xml data type [SQL Server], WITH XMLNAMESPACES clause
- WITH XMLNAMESPACES clause
ms.assetid: 2189cb5e-4460-46c5-a254-20c833ebbfec
author: rothja
ms.author: jroth
ms.openlocfilehash: ed5d719a845996215fffc18af64401779f848cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577443"
---
# <a name="add-namespaces-to-queries-with-with-xmlnamespaces"></a><span data-ttu-id="81f95-102">使用 WITH XMLNAMESPACES 将命名空间添加到查询</span><span class="sxs-lookup"><span data-stu-id="81f95-102">Add Namespaces to Queries with WITH XMLNAMESPACES</span></span>
  <span data-ttu-id="81f95-103">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) 按以下方式提供对命名空间 URI 支持：</span><span class="sxs-lookup"><span data-stu-id="81f95-103">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) provides namespace URI support in the following way:</span></span>  
  
-   <span data-ttu-id="81f95-104">在 [使用 FOR XML 查询构造 XML](for-xml-sql-server.md) 时，它可以使命名空间前缀到 URI 的映射可用。</span><span class="sxs-lookup"><span data-stu-id="81f95-104">It makes the namespace prefix to URI mapping available when [Constructing XML Using FOR XML](for-xml-sql-server.md) queries.</span></span>  
  
-   <span data-ttu-id="81f95-105">它使命名空间到 URI 的映射对 [xml 数据类型方法](/sql/t-sql/xml/xml-data-type-methods)的静态命名空间上下文可用。</span><span class="sxs-lookup"><span data-stu-id="81f95-105">It makes the namespace to URI mapping available to the static namespace context of the [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span>  
  
## <a name="using-with-xmlnamespaces-in-the-for-xml-queries"></a><span data-ttu-id="81f95-106">在 FOR XML 查询中使用 WITH XMLNAMESPACES</span><span class="sxs-lookup"><span data-stu-id="81f95-106">Using WITH XMLNAMESPACES in the FOR XML Queries</span></span>  
 <span data-ttu-id="81f95-107">WITH XMLNAMESPACES 允许您在 FOR XML 查询中包含 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="81f95-107">WITH XMLNAMESPACES lets you include XML namespaces in FOR XML queries.</span></span> <span data-ttu-id="81f95-108">例如，考虑下列 FOR XML 查询：</span><span class="sxs-lookup"><span data-stu-id="81f95-108">For example, consider the following FOR XML query:</span></span>  
  
```  
SELECT ProductID, Name, Color  
FROM   Production.Product  
WHERE  ProductID=316 or ProductID=317  
FOR XML RAW  
```  
  
 <span data-ttu-id="81f95-109">结果如下：</span><span class="sxs-lookup"><span data-stu-id="81f95-109">This is the result:</span></span>  
  
```  
<row ProductID="316" Name="Blade" />  
<row ProductID="317" Name="LL Crankarm" Color="Black" />  
  
```  
  
 <span data-ttu-id="81f95-110">若要向 FOR XML 查询构造的 XML 添加命名空间，请先使用 WITH NAMESPACES 子句指定命名空间前缀到 URI 的映射。</span><span class="sxs-lookup"><span data-stu-id="81f95-110">To add namespaces to the XML constructed by the FOR XML query, first specify the namespace prefix to URI mappings by using the WITH NAMESPACES clause.</span></span> <span data-ttu-id="81f95-111">然后，使用命名空间前缀在查询中指定名称，如下列修改的查询所示。</span><span class="sxs-lookup"><span data-stu-id="81f95-111">Then, use the namespace prefixes in specifying the names in the query as shown in the following modified query.</span></span> <span data-ttu-id="81f95-112">请注意，WITH XMLNAMESPACES 子句指定命名空间前缀 (`ns1`) 到 URI (`uri`) 的映射。</span><span class="sxs-lookup"><span data-stu-id="81f95-112">Note that the WITH XMLNAMESPACES clause specifies the namespace prefix (`ns1`) to URI (`uri`) mapping.</span></span> <span data-ttu-id="81f95-113">然后 `ns1` 前缀用来指定 FOR XML 查询要构造的元素名称和属性名称。</span><span class="sxs-lookup"><span data-stu-id="81f95-113">The `ns1` prefix is then used in specifying the element and attribute names to be constructed by the FOR XML query.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Prod'), ELEMENTS  
  
```  
  
 <span data-ttu-id="81f95-114">XML 结果包含命名空间前缀：</span><span class="sxs-lookup"><span data-stu-id="81f95-114">The XML result includes the namespace prefixes:</span></span>  
  
```  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
</ns1:Prod>  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>317</ns1:ProductID>  
  <ns1:Name>LL Crankarm</ns1:Name>  
  <ns1:Color>Black</ns1:Color>  
</ns1:Prod>  
  
```  
  
 <span data-ttu-id="81f95-115">下列内容适用于 WITH XMLNAME 子句：</span><span class="sxs-lookup"><span data-stu-id="81f95-115">The following applies to the WITH XMLNAMESPACES clause:</span></span>  
  
-   <span data-ttu-id="81f95-116">只有在 FOR XML 查询的 RAW、AUTO 和 PATH 模式中才支持该子句。</span><span class="sxs-lookup"><span data-stu-id="81f95-116">It is supported only on the RAW, AUTO, and PATH modes of the FOR XML queries.</span></span> <span data-ttu-id="81f95-117">EXPLICIT 模式不支持该子句。</span><span class="sxs-lookup"><span data-stu-id="81f95-117">The EXPLICIT mode is not supported.</span></span>  
  
-   <span data-ttu-id="81f95-118">该子句仅影响 FOR XML 查询的命名空间前缀和 **xml** 数据类型方法，而不影响 XML 分析器。</span><span class="sxs-lookup"><span data-stu-id="81f95-118">It only affects the namespace prefixes of FOR XML queries and the **xml** data type methods, but not the XML parser.</span></span> <span data-ttu-id="81f95-119">例如，下列查询将返回一个错误，因为 XML 文档没有为 myNS 前缀声明命名空间。</span><span class="sxs-lookup"><span data-stu-id="81f95-119">For example, the following query returns an error, because the XML document has no namespace declaration for the myNS prefix.</span></span>  
  
-   <span data-ttu-id="81f95-120">使用 WITH XMLNAMESPACES 子句时，不能使用 FOR XML 指令 XMLSCHEMA 和 XMLDATA。</span><span class="sxs-lookup"><span data-stu-id="81f95-120">The FOR XML directives, XMLSCHEMA and XMLDATA cannot be used when a WITH XMLNAMESPACES clause is being used.</span></span>  
  
    ```  
    CREATE TABLE T (x xml)  
    go  
    WITH XMLNAMESPACES ('http://abc' as myNS )  
    INSERT INTO T VALUES('<myNS:root/>')  
    ```  
  
## <a name="using-the-xsinil-directive"></a><span data-ttu-id="81f95-121">使用 XSINIL 指令</span><span class="sxs-lookup"><span data-stu-id="81f95-121">Using the XSINIL Directive</span></span>  
 <span data-ttu-id="81f95-122">如果使用的是 ELEMENTS XSINI 指令，则无法在 WITH XMLNAMESPACES 子句中定义 xsi 前缀。</span><span class="sxs-lookup"><span data-stu-id="81f95-122">You cannot define the xsi prefix in the WITH XMLNAMESPACES clause if you are using the ELEMENTS XSINIL directive.</span></span> <span data-ttu-id="81f95-123">但是，在使用 ELEMENTS XSINIL 时会自动添加该前缀。</span><span class="sxs-lookup"><span data-stu-id="81f95-123">Instead, it is added automatically when you use ELEMENTS XSINIL.</span></span> <span data-ttu-id="81f95-124">下列查询使用了生成以元素为中心的 XML 的 ELEMENTS XSINIL 指令，在此 XML 中 Null 值映射到将 **xsi:nil** 属性设置为 True 的元素。</span><span class="sxs-lookup"><span data-stu-id="81f95-124">The following query uses ELEMENTS XSINIL that generates element-centric XML where null values are mapped to elements that have the **xsi:nil** attribute set to True.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316   
FOR XML RAW, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="81f95-125">结果如下：</span><span class="sxs-lookup"><span data-stu-id="81f95-125">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
  <ns1:Color xsi:nil="true" />  
</row>  
```  
  
## <a name="specifying-default-namespaces"></a><span data-ttu-id="81f95-126">指定默认的命名空间</span><span class="sxs-lookup"><span data-stu-id="81f95-126">Specifying Default Namespaces</span></span>  
 <span data-ttu-id="81f95-127">可以使用 DEFAULT 关键字声明默认的命名空间来代替声明命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="81f95-127">Instead of declaring a namespace prefix, you can declare a default namespace by using a DEFAULT keyword.</span></span> <span data-ttu-id="81f95-128">在 FOR XML 查询中，这会将默认的命名空间绑定到所得到的 XML 中的 XML 节点。</span><span class="sxs-lookup"><span data-stu-id="81f95-128">In the FOR XML query, it will bind the default namespace to XML nodes in the resulting XML.</span></span> <span data-ttu-id="81f95-129">在下列示例中，WITH XMLNAMESPA 定义了两个和默认的命名空间一起定义的命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="81f95-129">In the following example, the WITH XMLNAMESPACES defines two namespace prefixes that are defined together with a default namespace.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,   
                    'uri2' as ns2,  
                    DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product   
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Product'), ROOT('ns2:root'), ELEMENTS  
```  
  
 <span data-ttu-id="81f95-130">FOR XML 查询生成以元素为中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="81f95-130">The FOR XML query generates element-centric XML.</span></span> <span data-ttu-id="81f95-131">请注意，此查询使用两个命名空间前缀来命名节点。</span><span class="sxs-lookup"><span data-stu-id="81f95-131">Note that the query uses both the namespace prefixes in naming nodes.</span></span> <span data-ttu-id="81f95-132">在 SELECT 子句中，ProductID、Name 和 Color 不指定带有任何前缀的名称。</span><span class="sxs-lookup"><span data-stu-id="81f95-132">In the SELECT clause, the ProductID, Name, and Color do not specify a name with any prefix.</span></span> <span data-ttu-id="81f95-133">因此，所得到的 XML 中的相应元素属于默认的命名空间。</span><span class="sxs-lookup"><span data-stu-id="81f95-133">Therefore, the corresponding elements in the resulting XML belong to the default namespace.</span></span>  
  
```  
<ns2:root xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">  
  <ns1:Product>  
    <ProductID>316</ProductID>  
    <Name>Blade</Name>  
  </ns1:Product>  
  <ns1:Product>  
    <ProductID>317</ProductID>  
    <Name>LL Crankarm</Name>  
    <Color>Black</Color>  
  </ns1:Product>  
</ns2:root>  
```  
  
 <span data-ttu-id="81f95-134">下列查询与前一个查询类似，只是指定了 FOR XML AUTO 模式。</span><span class="sxs-lookup"><span data-stu-id="81f95-134">The following query is similar to the previous one, except that the FOR XML AUTO mode is specified.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,  'uri2' as ns2,DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product as "ns1:Product"  
WHERE ProductID=316 or ProductID=317  
FOR XML AUTO, ROOT('ns2:root'), ELEMENTS  
```  
  
## <a name="using-predefined-namespaces"></a><span data-ttu-id="81f95-135">使用预定义的命名空间</span><span class="sxs-lookup"><span data-stu-id="81f95-135">Using Predefined Namespaces</span></span>  
 <span data-ttu-id="81f95-136">当使用预定义命名空间时（若 ELEMENTS XSINIL 时，则不包括 xml 命名空间和 xsi 命名空间），必须使用 WITH XMLNAMESPAC 显式指定命名空间绑定。</span><span class="sxs-lookup"><span data-stu-id="81f95-136">When you use predefined namespaces, except the xml namespace and the xsi namespace when ELEMENTS XSINIL is used, you must explicitly specify the namespace binding by using WITH XMLNAMESPACES.</span></span> <span data-ttu-id="81f95-137">下列查询为预定义命名空间 (`urn:schemas-microsoft-com:xml-sql`) 显式定义了命名空间前缀到 URI 的绑定。</span><span class="sxs-lookup"><span data-stu-id="81f95-137">The following query explicitly defines the namespace prefix to URI binding for the predefined namespace (`urn:schemas-microsoft-com:xml-sql`).</span></span>  
  
```  
WITH XMLNAMESPACES ('urn:schemas-microsoft-com:xml-sql' as sql)  
SELECT 'SELECT * FROM Customers FOR XML AUTO, ROOT("a")' AS "sql:query"  
FOR XML PATH('sql:root')  
```  
  
 <span data-ttu-id="81f95-138">结果如下：</span><span class="sxs-lookup"><span data-stu-id="81f95-138">This is the result.</span></span> <span data-ttu-id="81f95-139">SQLXML 用户熟悉此 XML 模板。</span><span class="sxs-lookup"><span data-stu-id="81f95-139">SQLXML users are familiar with this XML template.</span></span> <span data-ttu-id="81f95-140">有关详细信息，请参阅 [SQLXML 4.0 编程概念](../sqlxml/sqlxml-4-0-programming-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="81f95-140">For more information, see [SQLXML 4.0 Programming Concepts](../sqlxml/sqlxml-4-0-programming-concepts.md).</span></span>  
  
```  
<sql:root xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>SELECT * FROM Customers FOR XML AUTO, ROOT("a")</sql:query>  
</sql:root>  
```  
  
 <span data-ttu-id="81f95-141">只有 xml 命名空间无须在 WITH XMLNAMESPAC 中显式定义即可使用，如下列 PATH 模式查询所示。</span><span class="sxs-lookup"><span data-stu-id="81f95-141">Only the xml namespace prefix can be used without explicitly defining it in WITH XMLNAMESPACES, as shown in the following PATH mode query.</span></span> <span data-ttu-id="81f95-142">此外，如果声明了前缀，则前缀必须绑定到命名空间 http://www.w3.org/XML/1998/namespace 。</span><span class="sxs-lookup"><span data-stu-id="81f95-142">Also, if the prefix is declared, it has to be bound to the namespace http://www.w3.org/XML/1998/namespace.</span></span> <span data-ttu-id="81f95-143">在 SELECT 子句中指定的名称将引用未使用 WITH XMLNAMESPACES 进行显式定义的 xml 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="81f95-143">The names specified in the SELECT clause refer to the xml namespace prefix that is not explicitly defined by using WITH XMLNAMESPACES.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
go  
```  
  
 <span data-ttu-id="81f95-144">@xml:lang 属性使用预定义的 xml 命名空间。</span><span class="sxs-lookup"><span data-stu-id="81f95-144">The @xml:lang attributes use the predefined xml namespace.</span></span> <span data-ttu-id="81f95-145">由于 1.0 版的 XML 不需要显式声明 xml 命名空间绑定，因此结果中将不包命名空间绑定的显式声明。</span><span class="sxs-lookup"><span data-stu-id="81f95-145">Because XML version 1.0 does not require the explicit declaration of the xml namespace binding, the result will not include an explicit declaration of the namespace binding.</span></span>  
  
 <span data-ttu-id="81f95-146">结果如下：</span><span class="sxs-lookup"><span data-stu-id="81f95-146">This is the result:</span></span>  
  
```  
<Translation>  
  <English xml:lang="en">food</English>  
  <German xml:lang="ger">Essen</German>  
</Translation>  
```  
  
## <a name="using-with-xmlnamespaces-with-the-xml-data-type-methods"></a><span data-ttu-id="81f95-147">将 WITH XMLNAMESPACES 与 xml 数据类型方法结合使用</span><span class="sxs-lookup"><span data-stu-id="81f95-147">Using WITH XMLNAMESPACES with the xml Data Type Methods</span></span>  
 <span data-ttu-id="81f95-148">所有在 SELECT 查询中或在 UPDATE 中（当使用 [modify()](/sql/t-sql/xml/xml-data-type-methods) 方法时）指定的 **xml 数据类型方法** 都必须在它们的 prolog 中重复命名空间的声明。</span><span class="sxs-lookup"><span data-stu-id="81f95-148">The [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) specified in a SELECT query, or in UPDATE when it is the **modify()** method, all have to repeat the namespace declaration in their prolog.</span></span> <span data-ttu-id="81f95-149">这可能要花很长时间。</span><span class="sxs-lookup"><span data-stu-id="81f95-149">This can be time-consuming.</span></span> <span data-ttu-id="81f95-150">例如，下列查询将检索目录说明中确实包含规范的产品型号 ID。</span><span class="sxs-lookup"><span data-stu-id="81f95-150">For example, the following query retrieves product model IDs whose catalog descriptions do include specification.</span></span> <span data-ttu-id="81f95-151">即存在 <`Specifications`> 元素。</span><span class="sxs-lookup"><span data-stu-id="81f95-151">That is, the <`Specifications`> element exists.</span></span>  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
```  
  
 <span data-ttu-id="81f95-152">在前一个查询中， **query()** 和 **exist()** 方法在它们的 prolog 中声明了相同的命名空间。</span><span class="sxs-lookup"><span data-stu-id="81f95-152">In the previous query, both the **query()** and **exist()** methods declare the same namespace in their prolog.</span></span> <span data-ttu-id="81f95-153">例如：</span><span class="sxs-lookup"><span data-stu-id="81f95-153">For example:</span></span>  
  
```  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
```  
  
 <span data-ttu-id="81f95-154">此外，您也可以先声明 WITH XMLNAMESPACE，然后在查询中使用命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="81f95-154">Alternatively, you can declare WITH XMLNAMESPACES first and use the namespace prefixes in the query.</span></span> <span data-ttu-id="81f95-155">这样， **query()** 和 **exist()** 方法便不必在它们的 prolog 中包含命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="81f95-155">In this case, the **query()** and **exist()** methods  do not have to include namespace declarations in their prolog.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' as pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
Go  
```  
  
 <span data-ttu-id="81f95-156">请注意，XQuery prolog 中的显式声明可覆盖在 WITH 子句中定义的命名空间前缀和默认的元素命名空间。</span><span class="sxs-lookup"><span data-stu-id="81f95-156">Note that an explicit declaration in the XQuery prolog overrides the namespace prefix and the default element namespace that are defined in the WITH clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f95-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81f95-157">See Also</span></span>  
 <span data-ttu-id="81f95-158">[xml 数据类型方法](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="81f95-158">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="81f95-159">[XQuery 语言参考 (SQL Server)](/sql/xquery/xquery-language-reference-sql-server) </span><span class="sxs-lookup"><span data-stu-id="81f95-159">[XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span></span>  
 <span data-ttu-id="81f95-160">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) </span><span class="sxs-lookup"><span data-stu-id="81f95-160">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span></span>  
 [<span data-ttu-id="81f95-161">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="81f95-161">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
