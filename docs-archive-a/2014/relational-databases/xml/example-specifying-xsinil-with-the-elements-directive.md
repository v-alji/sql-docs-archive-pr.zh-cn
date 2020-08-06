---
title: 示例：使用 ELEMENTS 指令指定 XSINIL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
author: rothja
ms.author: jroth
ms.openlocfilehash: 7817d2c72909ca66fb9fac10f8fcb32a759faf56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682760"
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a><span data-ttu-id="52a40-102">示例：指定带有 ELEMENTS 指令的 XSINIL</span><span class="sxs-lookup"><span data-stu-id="52a40-102">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>
  <span data-ttu-id="52a40-103">以下查询将指定 `ELEMENTS` 指令以根据查询结果生成以元素为中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="52a40-103">The following query specifies the `ELEMENTS` directive to generate element-centric XML from the query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52a40-104">示例</span><span class="sxs-lookup"><span data-stu-id="52a40-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="52a40-105">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="52a40-105">This is the partial result.</span></span>  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 <span data-ttu-id="52a40-106">由于 `Color` 列针对某些产品包含 Null 值，因此生成的 XML 将不会生成对应的 <`Color`> 元素。</span><span class="sxs-lookup"><span data-stu-id="52a40-106">Because the `Color` column has null values for some products, the resulting XML will not generate the corresponding <`Color`> element.</span></span> <span data-ttu-id="52a40-107">通过添加 `XSINIL` 和 `ELEMENTS` 指令，甚至可以针对结果集中的 NULL 颜色值生成 <`Color`> 元素。</span><span class="sxs-lookup"><span data-stu-id="52a40-107">By adding the `XSINIL` directive with `ELEMENTS`, you can generate the <`Color`> element even for NULL color values in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 <span data-ttu-id="52a40-108">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="52a40-108">This is the partial result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52a40-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52a40-109">See Also</span></span>  
 [<span data-ttu-id="52a40-110">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="52a40-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
