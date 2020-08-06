---
title: 示例：指定 ELEMENT 指令和实体编码 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ba4e419d31aa7c02cc2dc8f19a3350c233f042b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682766"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a><span data-ttu-id="3d331-102">示例：指定 ELEMENT 指令和实体编码</span><span class="sxs-lookup"><span data-stu-id="3d331-102">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>
  <span data-ttu-id="3d331-103">下面的这个示例说明了 **ELEMENT** 和 **XML** 指令之间的差异。</span><span class="sxs-lookup"><span data-stu-id="3d331-103">This example illustrates the difference between the **ELEMENT** and **XML** directives.</span></span> <span data-ttu-id="3d331-104">**ELEMENT** 指令会实体化数据，但 **XML** 指令则不会。</span><span class="sxs-lookup"><span data-stu-id="3d331-104">The **ELEMENT** directive entitizes the data, but the **XML** directive does not.</span></span> <span data-ttu-id="3d331-105">在查询中向 \<Summary> 元素分配了 XML，`<Summary>This is summary description</Summary>`。</span><span class="sxs-lookup"><span data-stu-id="3d331-105">The \<Summary> element is assigned XML, `<Summary>This is summary description</Summary>`, in the query.</span></span>  
  
 <span data-ttu-id="3d331-106">请看下面的查询：</span><span class="sxs-lookup"><span data-stu-id="3d331-106">Consider this query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="3d331-107">结果如下：</span><span class="sxs-lookup"><span data-stu-id="3d331-107">This is the result.</span></span> <span data-ttu-id="3d331-108">在结果中，对摘要说明进行了实体化。</span><span class="sxs-lookup"><span data-stu-id="3d331-108">The summary description is entitized in the result.</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="3d331-109">现在，如果在列名 **中指定** XML `Summary!2!SummaryDescription!XML`指令而不是 **ELEMENT** 指令，则您将收到未经实例化的摘要说明。</span><span class="sxs-lookup"><span data-stu-id="3d331-109">Now, if you specify the **XML** directive in the column name, `Summary!2!SummaryDescription!XML`, instead of the **ELEMENT** directive, you will receive the summary description without entitization.</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="3d331-110">以下查询使用 **xml** 类型的 **query()** 方法（而不是分配一个静态 XML 值）从 **xml** 类型的 CatalogDescription 列中检索产品型号摘要说明。</span><span class="sxs-lookup"><span data-stu-id="3d331-110">Instead of assigning a static XML value, the following query uses the **query()** method of the **xml** type to retrieve the product model summary description from the CatalogDescription column of **xml** type.</span></span> <span data-ttu-id="3d331-111">因为已经知道结果为 **xml** 类型，所以未进行实体化。</span><span class="sxs-lookup"><span data-stu-id="3d331-111">Because the result is known to be of **xml** type, no entitization is applied.</span></span>  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d331-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d331-112">See Also</span></span>  
 [<span data-ttu-id="3d331-113">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="3d331-113">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
