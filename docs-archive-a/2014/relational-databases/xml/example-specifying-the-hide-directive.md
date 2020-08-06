---
title: 示例：指定 HIDE 指令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- HIDE directive
ms.assetid: 87504d87-1cbd-412a-9041-47884b6efcec
author: rothja
ms.author: jroth
ms.openlocfilehash: 423ee36f679467c07a604b9754172f6e261971b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590093"
---
# <a name="example-specifying-the-hide-directive"></a><span data-ttu-id="e8b8c-102">示例：指定 HIDE 指令</span><span class="sxs-lookup"><span data-stu-id="e8b8c-102">Example: Specifying the HIDE Directive</span></span>
  <span data-ttu-id="e8b8c-103">此示例说明如何使用 **HIDE** 指令。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-103">This example illustrates the use of the **HIDE** directive.</span></span> <span data-ttu-id="e8b8c-104">当希望查询返回一个属性以对该查询所返回的通用表中的行进行排序，但是不希望该属性出现在最终所得到的 XML 文档中时，该指令很有用。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-104">This directive is useful when you want the query to return an attribute for ordering the rows in the universal table that is returned by the query, but you do not want that attribute in the final resulting XML document.</span></span>  
  
 <span data-ttu-id="e8b8c-105">以下查询将构造此 XML：</span><span class="sxs-lookup"><span data-stu-id="e8b8c-105">This query constructs this XML:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
           <Summary> element from XML stored in CatalogDescription column  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="e8b8c-106">此查询将生成所需的 XML。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-106">This query generates the XML you want.</span></span> <span data-ttu-id="e8b8c-107">此查询标识列名中 Tag 值为 1 和 2 的两个列组。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-107">The query identifies two column groups having 1 and 2 as Tag values in the column names.</span></span>  
  
 <span data-ttu-id="e8b8c-108">此查询使用 [xml](/sql/t-sql/xml/query-method-xml-data-type) 数据类型的 **query() 方法（xml 数据类型）** 来查询 **xml** 类型的 CatalogDescription 列，以便检索摘要说明。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-108">This query uses the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) of the **xml** data type to query the CatalogDescription column of **xml** type in order to retrieve the summary description.</span></span> <span data-ttu-id="e8b8c-109">此查询还使用 [xml](/sql/t-sql/xml/value-method-xml-data-type) 数据类型的 **value() 方法（xml 数据类型）** 从 CatalogDescription 列中检索 ProductModelID 值。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-109">The query also uses the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) of the **xml** data type to retrieve the ProductModelID value from the CatalogDescription column.</span></span> <span data-ttu-id="e8b8c-110">所得到的 XML 中不需要此值，但对生成的行集进行排序时需要此值。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-110">This value is not required in the resulting XML, but is required to sort the resulting rowset.</span></span> <span data-ttu-id="e8b8c-111">因此，列名称 `[Summary!2!ProductModelID!HIDE]`包括 **HIDE** 指令。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-111">Therefore, the column name, `[Summary!2!ProductModelID!HIDE]`, includes the **HIDE** directive.</span></span> <span data-ttu-id="e8b8c-112">如果 SELECT 语句中不包括此列，您将不得不按 `[ProductModel!1!ProdModelID]` 和 `[Summary!2!SummaryDescription]` xml **类型的** 对行集进行排序，并且不能在 ORDER BY 中使用 **xml** 类型列。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-112">If this column is not included in the SELECT statement, you will have to sort the rowset by `[ProductModel!1!ProdModelID]` and `[Summary!2!SummaryDescription]` that is **xml** type and you cannot use the **xml** type column in ORDER BY.</span></span> <span data-ttu-id="e8b8c-113">因此，将另外添加一个 `[Summary!2!ProductModelID!HIDE]` 列，然后在 ORDER BY 子句中指定该列。</span><span class="sxs-lookup"><span data-stu-id="e8b8c-113">Therefore, the additional `[Summary!2!ProductModelID!HIDE]` column is added and is then specified in the ORDER BY clause.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID     as [ProductModel!1!ProdModelID],  
        Name               as [ProductModel!1!Name],  
        NULL               as [Summary!2!ProductModelID!hide],  
        NULL               as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
        CatalogDescription.value('  
         declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       (/PD:ProductDescription/@ProductModelID)[1]', 'int'),  
        CatalogDescription.query('  
         declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /pd:ProductDescription/pd:Summary')  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],[Summary!2!ProductModelID!hide]  
FOR XML EXPLICIT  
go  
```  
  
 <span data-ttu-id="e8b8c-114">结果如下：</span><span class="sxs-lookup"><span data-stu-id="e8b8c-114">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription" xmlns="">  
        <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike. Performance-enhancing options include the innovative HL Frame, super-smooth front suspension, and traction for all terrain. </p1:p>  
      </pd:Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8b8c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8b8c-115">See Also</span></span>  
 [<span data-ttu-id="e8b8c-116">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="e8b8c-116">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
