---
title: 示例：指定 XMLTEXT 指令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XMLTEXT directive
ms.assetid: e78008ec-51e8-4fd1-b86f-1058a781de17
author: rothja
ms.author: jroth
ms.openlocfilehash: d14299ad3e989c6600434b857a650fbbddd7a590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590085"
---
# <a name="example-specifying-the-xmltext-directive"></a><span data-ttu-id="36365-102">示例：指定 XMLTEXT 指令</span><span class="sxs-lookup"><span data-stu-id="36365-102">Example: Specifying the XMLTEXT Directive</span></span>
  <span data-ttu-id="36365-103">此示例说明如何在使用 EXPLICIT 模式的 `SELECT` 语句中使用 `XMLTEXT` 指令处理溢出列中的数据。</span><span class="sxs-lookup"><span data-stu-id="36365-103">This example illustrates how data in the overflow column is addressed by using the `XMLTEXT` directive in a `SELECT` statement using EXPLICIT mode.</span></span>  
  
 <span data-ttu-id="36365-104">请考虑一下 `Person` 表。</span><span class="sxs-lookup"><span data-stu-id="36365-104">Consider the `Person` table.</span></span> <span data-ttu-id="36365-105">此表含有存储 XML 文档的未使用部分的 `Overflow` 列。</span><span class="sxs-lookup"><span data-stu-id="36365-105">This table has an `Overflow` column that stores the unconsumed part of the XML document.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE TABLE Person(PersonID varchar(5), PersonName varchar(20), Overflow nvarchar(200));  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
   ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P">content</SomeTag>');  
```  
  
 <span data-ttu-id="36365-106">此查询从 `Person` 表中检索列。</span><span class="sxs-lookup"><span data-stu-id="36365-106">This query retrieves columns from the `Person` table.</span></span> <span data-ttu-id="36365-107">对于 `Overflow` 列，没有指定 *AttributeName* ，但是在提供通用表列名的过程中，已将 *directive* 设置为 `XMLTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="36365-107">For the `Overflow` column, *AttributeName* is not specified, but *directive* is set to `XMLTEXT` as part of providing a universal table column name.</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEST] -- No AttributeName; XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="36365-108">在所得到的 XML 文档中：</span><span class="sxs-lookup"><span data-stu-id="36365-108">In the resulting XML document:</span></span>  
  
-   <span data-ttu-id="36365-109">因为 `Overflow` 列没有指定 *AttributeName*，但却指定了 `xmltext` 指令，所以 <`overflow`> 元素中的属性被追加到封闭的 <`Parent`> 元素的属性列表中。</span><span class="sxs-lookup"><span data-stu-id="36365-109">Because *AttributeName* is not specified for the `Overflow` column and the `xmltext` directive is specified, the attributes in the <`overflow`> element are appended to the attribute list of the enclosing <`Parent`> element.</span></span>  
  
-   <span data-ttu-id="36365-110">因为 <`xmltext`> 元素中的 `PersonID` 属性与相同元素级上检索到的 `PersonID` 属性冲突，所以忽略 <`xmltext`> 元素中的此属性，即使 `PersonID` 为 NULL 也是如此。</span><span class="sxs-lookup"><span data-stu-id="36365-110">Because the `PersonID`attribute in the <`xmltext`> element conflicts with the `PersonID` attribute retrieved on the same element level, the attribute in the <`xmltext`> element is ignored, even if `PersonID` is NULL.</span></span> <span data-ttu-id="36365-111">通常情况下，属性将覆盖溢出中具有相同名称的属性。</span><span class="sxs-lookup"><span data-stu-id="36365-111">Generally, an attribute overrides an attribute of the same name in the overflow.</span></span>  
  
 <span data-ttu-id="36365-112">结果如下：</span><span class="sxs-lookup"><span data-stu-id="36365-112">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">content</Parent>`  
  
 <span data-ttu-id="36365-113">如果溢出数据包含子元素且指定了相同的查询，则 `Overflow` 列中的子元素将作为包含它的 <`Parent`> 元素的子元素添加。</span><span class="sxs-lookup"><span data-stu-id="36365-113">If the overflow data has subelements and the same query is specified, the subelements in the `Overflow` column are added as the subelements of the enclosing <`Parent`> element.</span></span>  
  
 <span data-ttu-id="36365-114">例如，更改 `Person` 表中的数据以使 `Overflow` 列此时包含子元素。</span><span class="sxs-lookup"><span data-stu-id="36365-114">For example, change the data in the `Person` table so that the `Overflow` column now has subelements.</span></span>  
  
```  
USE tempdb;  
GO  
TRUNCATE TABLE Person;  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
    ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P"><name>PersonName</name></SomeTag>');  
```  
  
 <span data-ttu-id="36365-115">如果执行相同的查询，则 <`xmltext`> 元素中的子元素将作为包含它的 <`Parent`> 元素的子元素添加。</span><span class="sxs-lookup"><span data-stu-id="36365-115">If the same query is executed, the subelements in the <`xmltext`> element are added as subelements of the enclosing <`Parent`> element:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEXT] -- no AttributeName, XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="36365-116">结果如下：</span><span class="sxs-lookup"><span data-stu-id="36365-116">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `</Parent>`  
  
 <span data-ttu-id="36365-117">如果使用 `xmltext` 指令指定了 *AttributeName*，则 <`overflow`> 元素的属性将作为封闭的 <`Parent`> 元素的子元素属性添加。</span><span class="sxs-lookup"><span data-stu-id="36365-117">If *AttributeName* is specified with the `xmltext` directive, the attributes of the <`overflow`> element are added as attributes of the subelements of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="36365-118">为*AttributeName*指定的名称将成为子元素的名称。</span><span class="sxs-lookup"><span data-stu-id="36365-118">The name specified for *AttributeName* becomes the name of the subelement.</span></span>  
  
 <span data-ttu-id="36365-119">在此查询中， *AttributeName*<`overflow`> 与指令一起指定 `xmltext` ：</span><span class="sxs-lookup"><span data-stu-id="36365-119">In this query, *AttributeName*, <`overflow`>, is specified together with the `xmltext` directive:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!overflow!XMLTEXT] -- Overflow is AttributeName  
                      -- XMLTEXT is a directive  
FROM Person  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="36365-120">结果如下：</span><span class="sxs-lookup"><span data-stu-id="36365-120">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe">`  
  
 `<overflow attr1="data">content</overflow>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe">`  
  
 `<overflow attr2="data" />`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe">`  
  
 `<overflow attr3="data" PersonID="P">`  
  
 `<name>PersonName</name>`  
  
 `</overflow>`  
  
 `</Parent>`  
  
 <span data-ttu-id="36365-121">在此查询元素中，为 *指令一起指定* 属性指定了 `PersonName` 。</span><span class="sxs-lookup"><span data-stu-id="36365-121">In this query element, *directive* is specified for `PersonName` attribute.</span></span> <span data-ttu-id="36365-122">这将导致 `PersonName` 作为包含它的 <`Parent`> 元素的子元素添加。</span><span class="sxs-lookup"><span data-stu-id="36365-122">This results in `PersonName` being added as a subelement of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="36365-123"><`xmltext`> 的属性仍将追加到包含它的 <`Parent`> 元素中。</span><span class="sxs-lookup"><span data-stu-id="36365-123">The attributes of the <`xmltext`> are still appended to the enclosing <`Parent`> element.</span></span> <span data-ttu-id="36365-124"><`overflow`> 元素、子元素的内容将放置到包含它们的 <`Parent`> 元素的其他子元素之前。</span><span class="sxs-lookup"><span data-stu-id="36365-124">The contents of the <`overflow`> element, subelements, are prepended to the other subelements of the enclosing <`Parent`> elements.</span></span>  
  
```  
SELECT 1      AS Tag, NULL as parent,  
       PersonID   AS [Parent!1!PersonID],  
       PersonName AS [Parent!1!PersonName!element], -- element directive  
       Overflow   AS [Parent!1!!XMLTEXT]  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="36365-125">结果如下：</span><span class="sxs-lookup"><span data-stu-id="36365-125">This is the result:</span></span>  
  
 `<Parent PersonID="P1" attr1="data">content<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" attr2="data">`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 <span data-ttu-id="36365-126">如果 `XMLTEXT` 列数据包含根元素的属性，这些属性将不显示在 XML 数据架构中，并且 MSXML 分析器不会验证所得到的 XML 文档片段。</span><span class="sxs-lookup"><span data-stu-id="36365-126">If the `XMLTEXT` column data contains attributes on the root element, these attributes are not shown in the XML data schema and the MSXML parser does not validate the resulting XML document fragment.</span></span> <span data-ttu-id="36365-127">例如：</span><span class="sxs-lookup"><span data-stu-id="36365-127">For example:</span></span>  
  
```  
SELECT 1 AS Tag,  
       0 ASParent,  
       N'<overflow a="1"/>' AS 'overflow!1!!xmltext'  
FOR XML EXPLICIT, xmldata;  
```  
  
 <span data-ttu-id="36365-128">结果如下：</span><span class="sxs-lookup"><span data-stu-id="36365-128">This is the result.</span></span> <span data-ttu-id="36365-129">请注意，在返回的架构中缺少溢出属性 `a` ：</span><span class="sxs-lookup"><span data-stu-id="36365-129">Note that in the returned schema, the overflow attribute `a` is missing from the schema:</span></span>  
  
 `<Schema name="Schema2"`  
  
 `xmlns="urn:schemas-microsoft-com:xml-data"`  
  
 `xmlns:dt="urn:schemas-microsoft-com:datatypes">`  
  
 `<ElementType name="overflow" content="mixed" model="open">`  
  
 `</ElementType>`  
  
 `</Schema>`  
  
 `<overflow xmlns="x-schema:#Schema2" a="1">`  
  
 `</overflow>`  
  
## <a name="see-also"></a><span data-ttu-id="36365-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36365-130">See Also</span></span>  
 [<span data-ttu-id="36365-131">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="36365-131">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
