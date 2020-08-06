---
title: 名称指定为通配符的列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b363baf8792628c2e17b1a695c19a6a338f4fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586535"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a><span data-ttu-id="d73d9-102">名称指定为通配符的列</span><span class="sxs-lookup"><span data-stu-id="d73d9-102">Columns with a Name Specified as a Wildcard Character</span></span>
  <span data-ttu-id="d73d9-103">如果指定的列名是一个通配符 (\*)，则插入此列的内容时就像没有指定列名那样插入。</span><span class="sxs-lookup"><span data-stu-id="d73d9-103">If the column name specified is a wildcard character (\*), the content of that column is inserted as if there is no column name specified.</span></span> <span data-ttu-id="d73d9-104">如果此列不是 `xml` 类型的列，则此列的内容将作为文本节点插入，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="d73d9-104">If this column is a non-`xml` type column, the column content is inserted as a text node, as shown in the following example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="d73d9-105">结果如下：</span><span class="sxs-lookup"><span data-stu-id="d73d9-105">This is the result:</span></span>  
  
 `<row EmpID="1">KenJS??nchez</row>`  
  
 <span data-ttu-id="d73d9-106">如果此列的类型为 `xml`，则将插入相应的 XML 树。</span><span class="sxs-lookup"><span data-stu-id="d73d9-106">If the column is of `xml` type, the corresponding XML tree is inserted.</span></span> <span data-ttu-id="d73d9-107">例如，下面的查询将“\*”指定为一个列的列名，该列包含由针对 Instructions 列的 XQuery 所返回的 XML。</span><span class="sxs-lookup"><span data-stu-id="d73d9-107">For example, the following query specifies "\*" for the column name that contains the XML returned by the XQuery against the Instructions column.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 <span data-ttu-id="d73d9-108">结果如下：</span><span class="sxs-lookup"><span data-stu-id="d73d9-108">This is the result.</span></span> <span data-ttu-id="d73d9-109">插入 XQuery 所返回的 XML 时不带包装元素。</span><span class="sxs-lookup"><span data-stu-id="d73d9-109">The XML returned by XQuery is inserted without a wrapping element.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="d73d9-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d73d9-110">See Also</span></span>  
 [<span data-ttu-id="d73d9-111">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="d73d9-111">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
