---
title: 使用嵌套的 FOR XML 查询形成 XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
author: rothja
ms.author: jroth
ms.openlocfilehash: 738b5b3ec67dada90c851d284ccc8b3009a51aa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588375"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a><span data-ttu-id="79026-102">使用嵌套的 FOR XML 查询形成 XML</span><span class="sxs-lookup"><span data-stu-id="79026-102">Shape XML with Nested FOR XML Queries</span></span>
  <span data-ttu-id="79026-103">下面的示例查询 `Production.Product` 表以检索特定产品的 `ListPrice` 值和 `StandardCost` 值。</span><span class="sxs-lookup"><span data-stu-id="79026-103">The following example queries the `Production.Product` table to retrieve the `ListPrice` and `StandardCost` values of a specific product.</span></span> <span data-ttu-id="79026-104">为使查询具有趣味性，这两个价格都在 <`Price`> 元素中返回，每个 <`Price`> 元素都有 `PriceType` 属性。</span><span class="sxs-lookup"><span data-stu-id="79026-104">To make the query interesting, both prices are returned in a <`Price`> element, and each <`Price`> element has a `PriceType` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79026-105">示例</span><span class="sxs-lookup"><span data-stu-id="79026-105">Example</span></span>  
 <span data-ttu-id="79026-106">以下是期望的 XML 形状：</span><span class="sxs-lookup"><span data-stu-id="79026-106">This is the expected shape of the XML:</span></span>  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 <span data-ttu-id="79026-107">以下是嵌套的 FOR XML 查询：</span><span class="sxs-lookup"><span data-stu-id="79026-107">This is the nested FOR XML query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 <span data-ttu-id="79026-108">请注意上述查询的以下方面：</span><span class="sxs-lookup"><span data-stu-id="79026-108">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="79026-109">外部 SELECT 语句构造具有 **ProductID** 属性和两个 <`Price`> 子元素的 <`Product`> 元素。</span><span class="sxs-lookup"><span data-stu-id="79026-109">The outer SELECT statement constructs the <`Product`> element that has a **ProductID** attribute and two <`Price`> child elements.</span></span>  
  
-   <span data-ttu-id="79026-110">两个内部 SELECT 语句构造两个 <`Price`> 元素，每一个都具有一个 **PriceType** 属性和可以返回产品价格的 XML。</span><span class="sxs-lookup"><span data-stu-id="79026-110">The two inner SELECT statements construct two <`Price`> elements, each with a **PriceType** attribute and XML that returns the product price.</span></span>  
  
-   <span data-ttu-id="79026-111">外部 SELECT 语句中的 XMLSCHEMA 指令生成用于描述结果 XML 外形的内联 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="79026-111">The XMLSCHEMA directive in the outer SELECT statement generates the inline XSD schema that describes the shape of the resulting XML.</span></span>  
  
 <span data-ttu-id="79026-112">为使查询能够更加有趣，可以编写 FOR XML 查询，然后针对结果编写 XQuery 以重新定形 XML，如以下查询所示：</span><span class="sxs-lookup"><span data-stu-id="79026-112">To make the query interesting, you can write the FOR XML query and then write an XQuery against the result to reshape the XML, as shown in the following query:</span></span>  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="79026-113">先前的示例使用 `query()` 数据类型的 `xml` 方法查询由内部 FOR XML 查询返回的 XML，并构造预期的结果。</span><span class="sxs-lookup"><span data-stu-id="79026-113">The previous example uses the `query()` method of the `xml` data type to query the XML returned by the inner FOR XML query and construct the expected result.</span></span>  
  
 <span data-ttu-id="79026-114">结果如下：</span><span class="sxs-lookup"><span data-stu-id="79026-114">This is the result:</span></span>  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79026-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79026-115">See Also</span></span>  
 [<span data-ttu-id="79026-116">使用嵌套 FOR XML 查询</span><span class="sxs-lookup"><span data-stu-id="79026-116">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
