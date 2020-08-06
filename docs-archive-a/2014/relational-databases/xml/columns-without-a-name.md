---
title: 没有名称的列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: rothja
ms.author: jroth
ms.openlocfilehash: 43d1cbce816e4666e6dab52fdffe5850e65740e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688660"
---
# <a name="columns-without-a-name"></a><span data-ttu-id="7d7d4-102">没有名称的列</span><span class="sxs-lookup"><span data-stu-id="7d7d4-102">Columns without a Name</span></span>
  <span data-ttu-id="7d7d4-103">任何没有名称的列都将成为内联列。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-103">Any column without a name will be inlined.</span></span> <span data-ttu-id="7d7d4-104">例如，未指定列别名的计算列或嵌套标量查询将生成没有名称的列。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-104">For example, computed columns or nested scalar queries that do not specify column alias will generate columns without any name.</span></span> <span data-ttu-id="7d7d4-105">如果该列属于 `xml` 类型，则将插入该数据类型实例的内容。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-105">If the column is of `xml` type, the content of that data type instance is inserted.</span></span> <span data-ttu-id="7d7d4-106">否则，列内容将作为文本节点插入。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-106">Otherwise, the column content is inserted as a text node.</span></span>  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 <span data-ttu-id="7d7d4-107">生成此 XML。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-107">Produce this XML.</span></span> <span data-ttu-id="7d7d4-108">默认情况下，针对行集中的每一行，生成的 XML 中将生成一个相应的 <`row`> 元素。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-108">By default, for each row in the rowset, a <`row`> element is generated in the resulting XML.</span></span> <span data-ttu-id="7d7d4-109">这与 RAW 模式相同。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-109">This is the same as RAW mode.</span></span>  
  
 `<row>4</row>`  
  
 <span data-ttu-id="7d7d4-110">以下查询将返回一个包含三列的行集。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-110">The following query returns a three-column rowset.</span></span> <span data-ttu-id="7d7d4-111">第三列没有名称，且包含 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-111">The third column without a name has XML data.</span></span> <span data-ttu-id="7d7d4-112">PATH 模式将插入一个 xml 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="7d7d4-112">The PATH mode inserts an instance of the xml type.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 <span data-ttu-id="7d7d4-113">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="7d7d4-113">This is the partial result:</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="7d7d4-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d7d4-114">See Also</span></span>  
 [<span data-ttu-id="7d7d4-115">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="7d7d4-115">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
