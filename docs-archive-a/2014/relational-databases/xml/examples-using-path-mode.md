---
title: 示例：使用 PATH 模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, examples
ms.assetid: 3564e13b-9b97-49ef-8cf9-6a78677b09a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0876d93ffe246b6129a3838f8dbae47f3be7ffaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694389"
---
# <a name="examples-using-path-mode"></a><span data-ttu-id="146d1-102">示例：使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="146d1-102">Examples: Using PATH Mode</span></span>
  <span data-ttu-id="146d1-103">下面的示例演示如何使用 PATH 模式通过 SELECT 查询生成 XML。</span><span class="sxs-lookup"><span data-stu-id="146d1-103">The following examples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="146d1-104">这些查询中有许多都是针对 ProductModel 表的 Instructions 列中存储的自行车生产说明 XML 文档指定的。</span><span class="sxs-lookup"><span data-stu-id="146d1-104">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="specifying-a-simple-path-mode-query"></a><span data-ttu-id="146d1-105">指定简单的 PATH 模式查询</span><span class="sxs-lookup"><span data-stu-id="146d1-105">Specifying a simple PATH mode query</span></span>  
 <span data-ttu-id="146d1-106">下面的查询指定了一个 FOR XML PATH 模式。</span><span class="sxs-lookup"><span data-stu-id="146d1-106">This query specifies a FOR XML PATH mode.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   
       ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH;  
GO  
```  
  
 <span data-ttu-id="146d1-107">以下结果是以元素为中心的 XML，在该 XML 中，生成的行集中的每个列值都包在元素中。</span><span class="sxs-lookup"><span data-stu-id="146d1-107">The following result is element-centric XML where each column value in the resulting rowset is wrapped in an element.</span></span> <span data-ttu-id="146d1-108">由于 `SELECT` 子句未指定任何列名别名，因此生成的子元素名称与 `SELECT` 子句中相应的列名相同。</span><span class="sxs-lookup"><span data-stu-id="146d1-108">Because the `SELECT` clause does not specify any aliases for the column names, the child element names generated are the same as the corresponding column names in the `SELECT` clause.</span></span> <span data-ttu-id="146d1-109">针对行集中的每一行，将添加一个 <`row`> 标记。</span><span class="sxs-lookup"><span data-stu-id="146d1-109">For each row in the rowset a <`row`> tag is added.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</row>`  
  
 `<row>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</row>`  
  
 <span data-ttu-id="146d1-110">以下结果与指定 `RAW` 选项的 `ELEMENTS` 模式查询的结果相同。</span><span class="sxs-lookup"><span data-stu-id="146d1-110">The following result is the same as the `RAW` mode query with the `ELEMENTS` option specified.</span></span> <span data-ttu-id="146d1-111">它将返回以元素为中心的 XML，在该 XML 中，结果集中的每一行都有一个相应的默认 <`row`> 元素。</span><span class="sxs-lookup"><span data-stu-id="146d1-111">It returns element-centric XML with a default <`row`> element for each row in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML RAW, ELEMENTS;  
```  
  
 <span data-ttu-id="146d1-112">您可以选择指定行元素名称，以覆盖默认的 <`row`>。</span><span class="sxs-lookup"><span data-stu-id="146d1-112">You can optionally specify the row element name to overwrite the default <`row`>.</span></span> <span data-ttu-id="146d1-113">例如，以下查询将针对行集中的每一行返回相应的 <`ProductModel`> 元素。</span><span class="sxs-lookup"><span data-stu-id="146d1-113">For example, the following query returns the <`ProductModel`> element for each row in the rowset.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModel');  
GO  
```  
  
 <span data-ttu-id="146d1-114">生成的 XML 将包含指定的行元素名称。</span><span class="sxs-lookup"><span data-stu-id="146d1-114">The resulting XML will have a specified row element name.</span></span>  
  
 `<ProductModel>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ProductModel>`  
  
 `<ProductModel>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ProductModel>`  
  
 <span data-ttu-id="146d1-115">如果指定零长度字符串，则将不生成包装元素。</span><span class="sxs-lookup"><span data-stu-id="146d1-115">If you specify a zero-length string, the wrapping element is not produced.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('');  
GO  
```  
  
 <span data-ttu-id="146d1-116">结果如下：</span><span class="sxs-lookup"><span data-stu-id="146d1-116">This is the result:</span></span>  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
## <a name="specifying-xpath-like-column-names"></a><span data-ttu-id="146d1-117">指定类似 XPath 的列名</span><span class="sxs-lookup"><span data-stu-id="146d1-117">Specifying XPath-like column names</span></span>  
 <span data-ttu-id="146d1-118">在下面的查询中，指定的 `ProductModelID` 列名以“\@”开头，且不包含斜线标记（“/”）。</span><span class="sxs-lookup"><span data-stu-id="146d1-118">In the following query the `ProductModelID` column name specified starts with '\@' and does not contain a slash mark ('/').</span></span> <span data-ttu-id="146d1-119">因此，在生成的 XML 中，将创建包含相应列值的 <`row`> 元素的属性。</span><span class="sxs-lookup"><span data-stu-id="146d1-119">Therefore, an attribute of the <`row`> element that has the corresponding column value is created in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('ProductModelData');  
GO  
```  
  
 <span data-ttu-id="146d1-120">结果如下：</span><span class="sxs-lookup"><span data-stu-id="146d1-120">This is the result:</span></span>  
  
 `< ProductModelData id="122">`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ ProductModelData >`  
  
 `< ProductModelData id="119">`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ ProductModelData >`  
  
 <span data-ttu-id="146d1-121">可以通过在 `root` 中指定 `FOR XML`选项来添加单个顶级元素。</span><span class="sxs-lookup"><span data-stu-id="146d1-121">You can add a single top-level element by specifying the `root` option in `FOR XML`.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="146d1-122">若要生成层次结构，可以包含类似 PATH 的语法。</span><span class="sxs-lookup"><span data-stu-id="146d1-122">To generate a hierarchy, you can include PATH-like syntax.</span></span> <span data-ttu-id="146d1-123">例如，将 `Name` 列的列名改为“SomeChild/ModelName”，就会获得具有层次结构的 XML，如以下结果所示：</span><span class="sxs-lookup"><span data-stu-id="146d1-123">For example, change the column name for the `Name` column to "SomeChild/ModelName" and you will obtain XML with hierarchy, as shown in this result:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="122">`  
  
 `<SomeChild>`  
  
 `<ModelName>All-Purpose Bike Stand</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData id="119">`  
  
 `<SomeChild>`  
  
 `<ModelName>Bike Wash</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="146d1-124">除了产品型号 ID 和名称以外，以下查询还将检索产品型号的生产说明位置。</span><span class="sxs-lookup"><span data-stu-id="146d1-124">Besides the product model ID and name, the following query retrieves the manufacturing instruction locations for the product model.</span></span> <span data-ttu-id="146d1-125">由于 Instructions 列是 `xml` 类型，因此指定了 `query()` 数据类型的 `xml` 方法来检索该位置。</span><span class="sxs-lookup"><span data-stu-id="146d1-125">Because the Instructions column is of `xml` type, the `query()` method of `xml` data type is specified to retrieve the location.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') AS ManuInstr  
FROM Production.ProductModel  
WHERE ProductModelID = 7  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="146d1-126">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="146d1-126">This is the partial result.</span></span> <span data-ttu-id="146d1-127">因为该查询指定 ManuInstr 作为列名，所以该方法返回的 XML `query()` 包装在 <> 标记中，如下 `ManuInstr` 所示：</span><span class="sxs-lookup"><span data-stu-id="146d1-127">Because the query specifies ManuInstr as the column name, the XML returned by the `query()` method is wrapped in a <`ManuInstr`> tag as shown in the following:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="7">`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<ManuInstr>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `<MI:step>...</MI:step>...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ManuInstr>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="146d1-128">在上一个 FOR XML 查询中，您可能希望针对 <`Root`> 和 <`ProductModelData`> 元素包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="146d1-128">In the previous FOR XML query, you may want to include namespaces for the <`Root`> and <`ProductModelData`> elements.</span></span> <span data-ttu-id="146d1-129">首先使用 WITH XMLNAMESPACES 定义命名空间绑定的前缀，然后在 FOR XML 查询中使用前缀，即可达到此目的。</span><span class="sxs-lookup"><span data-stu-id="146d1-129">You can do this by first defining the prefix to namespace binding by using WITH XMLNAMESPACES and using prefixes in the FOR XML query.</span></span> <span data-ttu-id="146d1-130">有关详细信息，请参阅 [使用 WITH XMLNAMESPACES 将命名空间添加到查询](add-namespaces-to-queries-with-with-xmlnamespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="146d1-130">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES (  
   'uri1' AS ns1,    
   'uri2' AS ns2,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' as MI)  
SELECT ProductModelID AS "ns1:ProductModelID",  
       Name           AS "ns1:Name",  
       Instructions.query('  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ('ns2:ProductInfo'), root('ns1:root');  
GO  
```  
  
 <span data-ttu-id="146d1-131">请注意，在 `MI` 中也定义了 `WITH XMLNAMESPACES`前缀。</span><span class="sxs-lookup"><span data-stu-id="146d1-131">Note that the `MI` prefix is also defined in the `WITH XMLNAMESPACES`.</span></span> <span data-ttu-id="146d1-132">因此，所指定的 `query()` 类型的 `xml` 方法没有在查询 prolog 中定义此前缀。</span><span class="sxs-lookup"><span data-stu-id="146d1-132">As a result, the `query()` method of the `xml` type specified does not define the prefix in the query prolog.</span></span> <span data-ttu-id="146d1-133">结果如下：</span><span class="sxs-lookup"><span data-stu-id="146d1-133">This is the result:</span></span>  
  
 `<ns1:root xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">`  
  
 `<ns2:ProductInfo>`  
  
 `<ns1:ProductModelID>7</ns1:ProductModelID>`  
  
 `<ns1:Name>HL Touring Frame</ns1:Name>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `LaborHours="2.5" LotSize="100" MachineHours="3" SetupHours="0.5" LocationID="10" xmlns="">`  
  
 `<MI:step>`  
  
 `Insert <MI:material>aluminum sheet MS-2341</MI:material> into the <MI:tool>T-85A framing tool</MI:tool>.`  
  
 `</MI:step>`  
  
 `...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ns2:ProductInfo>`  
  
 `</ns1:root>`  
  
## <a name="generating-a-value-list-using-path-mode"></a><span data-ttu-id="146d1-134">使用 PATH 模式生成值列表</span><span class="sxs-lookup"><span data-stu-id="146d1-134">Generating a value list using PATH mode</span></span>  
 <span data-ttu-id="146d1-135">对于每个产品型号，此查询将构造一个由产品 ID 组成的值列表。</span><span class="sxs-lookup"><span data-stu-id="146d1-135">For each product model, this query constructs a value list of product IDs.</span></span> <span data-ttu-id="146d1-136">对于每个产品 ID，此查询还会构造 <`ProductName`> 嵌套元素，如下面的 XML 片段所示：</span><span class="sxs-lookup"><span data-stu-id="146d1-136">For each product ID, the query also constructs <`ProductName`> nested elements, as shown in this XML fragment:</span></span>  
  
 `<ProductModelData ProductModelID="7" ProductModelName="..."`  
  
 `ProductIDs="product id list in the product model" >`  
  
 `<ProductName>...</ProductName>`  
  
 `<ProductName>...</ProductName>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="146d1-137">以下是用于生成所需 XML 的查询：</span><span class="sxs-lookup"><span data-stu-id="146d1-137">This is the query that produces the XML you want:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID     AS "@ProductModelID",  
       Name               S "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')) S "@ProductIDs",  
       (SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
        FOR XML PATH ('')) as "ProductNames"  
FROM   Production.ProductModel  
WHERE  ProductModelID= 7 or ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="146d1-138">请注意上述查询的以下方面：</span><span class="sxs-lookup"><span data-stu-id="146d1-138">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="146d1-139">通过使用 `SELECT` 作为列名，第一个嵌套 `data()` 语句将返回 ProductID 的列表。</span><span class="sxs-lookup"><span data-stu-id="146d1-139">The first nested `SELECT` returns a list of ProductIDs by using `data()` as the column name.</span></span> <span data-ttu-id="146d1-140">由于此查询指定了一个空字符串作为 `FOR XML PATH`中的行元素名，因此不会生成元素。</span><span class="sxs-lookup"><span data-stu-id="146d1-140">Because the query specifies an empty string as the row element name in `FOR XML PATH`, no element is generated.</span></span> <span data-ttu-id="146d1-141">相反，值列表将被分配给 `ProductID` 属性。</span><span class="sxs-lookup"><span data-stu-id="146d1-141">Instead, the value list is assigned to the `ProductID` attribute.</span></span>  
  
-   <span data-ttu-id="146d1-142">第二个嵌套 `SELECT` 语句检索该产品型号中的产品的产品名。</span><span class="sxs-lookup"><span data-stu-id="146d1-142">The second nested `SELECT` retrieves product names for products in the product model.</span></span> <span data-ttu-id="146d1-143">它将生成 <`ProductName`> 元素，并将它们包装在 <`ProductNames`> 元素中返回，因为该查询指定 `ProductNames` 作为列名。</span><span class="sxs-lookup"><span data-stu-id="146d1-143">It generates <`ProductName`> elements that are returned wrapped in the <`ProductNames`> element, because the query specifies `ProductNames` as the column name.</span></span>  
  
 <span data-ttu-id="146d1-144">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="146d1-144">This is the partial result:</span></span>  
  
 `<ProductModelData PId="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>HL Touring Frame - Yellow, 60</ProductName>`  
  
 `<ProductName>HL Touring Frame - Yellow, 46</ProductName></ProductNames>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 `<ProductModelData PId="9"`  
  
 `ProductModelName="LL Road Frame"`  
  
 `ProductIDs="722 723 724 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>LL Road Frame - Black, 58</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 60</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 62</ProductName>`  
  
 `...`  
  
 `</ProductNames>`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="146d1-145">构造产品名的子查询将返回已实体化并随后添加到 XML 的字符串。</span><span class="sxs-lookup"><span data-stu-id="146d1-145">The subquery constructing the product names returns the result as a string that is entitized and then added to the XML.</span></span> <span data-ttu-id="146d1-146">如果添加 type 指令 `FOR XML PATH (''), type`，则该子查询将返回 `xml` 类型的结果，并且不会进行实体化。</span><span class="sxs-lookup"><span data-stu-id="146d1-146">If you add the type directive, `FOR XML PATH (''), type`, the subquery returns the result as `xml` type and no entitization occurs.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@ProductModelID",  
      Name AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ProductIDs",  
       (  
       SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH (''), type  
       ) AS "ProductNames"  
  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
## <a name="adding-namespaces-in-the-resulting-xml"></a><span data-ttu-id="146d1-147">在生成的 XML 中添加命名空间</span><span class="sxs-lookup"><span data-stu-id="146d1-147">Adding namespaces in the resulting XML</span></span>  
 <span data-ttu-id="146d1-148">如 [使用 WITH XMLNAMESPACES 添加命名空间](add-namespaces-to-queries-with-with-xmlnamespaces.md)中所述，您可以使用 WITH XMLNAMESPACES 在 PATH 模式查询中包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="146d1-148">As described in [Adding Namespaces Using WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md), you can use WITH XMLNAMESPACES to include namespaces in the PATH mode queries.</span></span> <span data-ttu-id="146d1-149">例如，SELECT 子句中所指定的名称包含命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="146d1-149">For example, names specified in the SELECT clause include namespace prefixes.</span></span> <span data-ttu-id="146d1-150">以下 `PATH` 模式查询将构造带命名空间的 XML。</span><span class="sxs-lookup"><span data-stu-id="146d1-150">The following `PATH` mode query constructs XML with namespaces.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
GO  
```  
  
 <span data-ttu-id="146d1-151">添加到 <`English`> 元素的 `@xml:lang` 属性在预定义的 xml 命名空间中定义。</span><span class="sxs-lookup"><span data-stu-id="146d1-151">The `@xml:lang` attribute added to the <`English`> element is defined in the predefined xml namespace.</span></span>  
  
 <span data-ttu-id="146d1-152">结果如下：</span><span class="sxs-lookup"><span data-stu-id="146d1-152">This is the result:</span></span>  
  
 `<Translation>`  
  
 `<English xml:lang="en">food</English>`  
  
 `<German xml:lang="ger">Essen</German>`  
  
 `</Translation>`  
  
 <span data-ttu-id="146d1-153">以下查询与示例 C 类似，只不过它使用 `WITH XMLNAMESPACES` 在 XML 结果中包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="146d1-153">The following query is similar to example C, except that it uses `WITH XMLNAMESPACES` to include namespaces in the XML result.</span></span> <span data-ttu-id="146d1-154">有关详细信息，请参阅 [使用 WITH XMLNAMESPACES 将命名空间添加到查询](add-namespaces-to-queries-with-with-xmlnamespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="146d1-154">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES ('uri1' AS ns1,  DEFAULT 'uri2')  
SELECT ProductModelID AS "@ns1:ProductModelID",  
      Name AS "@ns1:ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ns1:ProductIDs",  
       (  
       SELECT ProductID AS "@ns1:ProductID",   
              Name AS "@ns1:ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH , type   
       ) AS "ns1:ProductNames"  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData'), root('root');  
```  
  
 <span data-ttu-id="146d1-155">结果如下：</span><span class="sxs-lookup"><span data-stu-id="146d1-155">This is the result:</span></span>  
  
 `<root xmlns="uri2" xmlns:ns1="uri1">`  
  
 `<ProductModelData ns1:ProductModelID="7" ns1:ProductModelName="HL Touring Frame" ns1:ProductIDs="885 887 888 889 890 891 892 893">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="885" ns1:ProductName="HL Touring Frame - Yellow, 60" />`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="887" ns1:ProductName="HL Touring Frame - Yellow, 46" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData ns1:ProductModelID="9" ns1:ProductModelName="LL Road Frame" ns1:ProductIDs="722 723 724 725 726 727 728 729 730 736 737 738">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="722" ns1:ProductName="LL Road Frame - Black, 58" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `</root>`  
  
## <a name="see-also"></a><span data-ttu-id="146d1-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="146d1-156">See Also</span></span>  
 [<span data-ttu-id="146d1-157">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="146d1-157">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
