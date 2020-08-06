---
title: 示例：指定 CDATA 指令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9b4f949ae1e9f309a13906efe44b329db2e47ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682769"
---
# <a name="example-specifying-the-cdata-directive"></a><span data-ttu-id="6b709-102">示例：指定 CDATA 指令</span><span class="sxs-lookup"><span data-stu-id="6b709-102">Example: Specifying the CDATA Directive</span></span>
  <span data-ttu-id="6b709-103">如果指令设置为 **CDATA**，则不对包含的数据进行实体编码，而是将其放入 CDATA 部分。</span><span class="sxs-lookup"><span data-stu-id="6b709-103">If the directive is set to **CDATA**, the contained data is not entity encoded, but is put in the CDATA section.</span></span> <span data-ttu-id="6b709-104">**CDATA** 属性必须没有名称。</span><span class="sxs-lookup"><span data-stu-id="6b709-104">The **CDATA** attributes must be nameless.</span></span>  
  
 <span data-ttu-id="6b709-105">以下查询将产品型号摘要说明包装在 CDATA 部分中。</span><span class="sxs-lookup"><span data-stu-id="6b709-105">The following query wraps the product model summary description in a CDATA section.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="6b709-106">结果如下：</span><span class="sxs-lookup"><span data-stu-id="6b709-106">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b709-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b709-107">See Also</span></span>  
 [<span data-ttu-id="6b709-108">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="6b709-108">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
