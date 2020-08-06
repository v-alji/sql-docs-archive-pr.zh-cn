---
title: 带有指定为 data() 的路径的列名 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: rothja
ms.author: jroth
ms.openlocfilehash: 61aa7f85c7ee2358ddcf99f81c87c1295fac8fb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577430"
---
# <a name="column-names-with-the-path-specified-as-data"></a><span data-ttu-id="e7278-102">带有指定为 data() 的路径的列名</span><span class="sxs-lookup"><span data-stu-id="e7278-102">Column Names with the Path Specified as data()</span></span>
  <span data-ttu-id="e7278-103">如果被指定为列名的路径为 data()，则在生成的 XML 中，该值将被作为一个原子值来处理。</span><span class="sxs-lookup"><span data-stu-id="e7278-103">If the path specified as column name is "data()", the value is treated as an atomic value in the generated XML.</span></span> <span data-ttu-id="e7278-104">如果序列化中的下一项也是一个原子值，则将向 XML 中添加一个空格字符。</span><span class="sxs-lookup"><span data-stu-id="e7278-104">A space character is added to the XML if the next item in the serialization is also an atomic value.</span></span> <span data-ttu-id="e7278-105">这在创建列表类型化元素值和属性值时很有用。</span><span class="sxs-lookup"><span data-stu-id="e7278-105">This is useful when you are creating list typed element and attribute values.</span></span> <span data-ttu-id="e7278-106">以下查询将检索产品型号 ID、名称和该产品型号中的产品列表。</span><span class="sxs-lookup"><span data-stu-id="e7278-106">The following query retrieves the product model ID, name, and list of products in that product model.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="e7278-107">嵌套 SELECT 语句将检索产品 ID 列表。</span><span class="sxs-lookup"><span data-stu-id="e7278-107">The nested SELECT retrieves a list of product IDs.</span></span> <span data-ttu-id="e7278-108">它指定 data() 作为产品 ID 列名。</span><span class="sxs-lookup"><span data-stu-id="e7278-108">It specifies "data()" as the column name for product IDs.</span></span> <span data-ttu-id="e7278-109">由于 PATH 模式为行元素名指定了空字符串，因此不会生成行元素。</span><span class="sxs-lookup"><span data-stu-id="e7278-109">Because PATH mode specifies an empty string for the row element name, there is no row element generated.</span></span> <span data-ttu-id="e7278-110">相反，将返回值以分配给父级 SELECT 的 <`ProductModelData`> 行元素的 ProductIDs 属性。</span><span class="sxs-lookup"><span data-stu-id="e7278-110">Instead, the values are returned as assigned to a ProductIDs attribute of the <`ProductModelData`> row element of the parent SELECT.</span></span> <span data-ttu-id="e7278-111">结果如下：</span><span class="sxs-lookup"><span data-stu-id="e7278-111">This is the result:</span></span>  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## <a name="see-also"></a><span data-ttu-id="e7278-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7278-112">See Also</span></span>  
 [<span data-ttu-id="e7278-113">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="e7278-113">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
