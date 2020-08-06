---
title: 示例：以 XML 形式检索产品型号信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: rothja
ms.author: jroth
ms.openlocfilehash: d580f53c4b5185a8b1b1467c75a08fc6929bdcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587273"
---
# <a name="example-retrieving-product-model-information-as-xml"></a><span data-ttu-id="14062-102">示例：以 XML 形式检索产品型号信息</span><span class="sxs-lookup"><span data-stu-id="14062-102">Example: Retrieving Product Model Information as XML</span></span>
  <span data-ttu-id="14062-103">下面的查询将返回产品型号信息。</span><span class="sxs-lookup"><span data-stu-id="14062-103">The following query returns product model information.</span></span> <span data-ttu-id="14062-104">`RAW` 子句中指定了 `FOR XML` 模式。</span><span class="sxs-lookup"><span data-stu-id="14062-104">`RAW` mode is specified in the `FOR XML` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14062-105">示例</span><span class="sxs-lookup"><span data-stu-id="14062-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 <span data-ttu-id="14062-106">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="14062-106">This is the partial result:</span></span>  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 <span data-ttu-id="14062-107">您可以通过指定 `ELEMENTS` 指令检索以元素为中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="14062-107">You can retrieve element-centric XML by specifying the `ELEMENTS` directive.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="14062-108">结果如下：</span><span class="sxs-lookup"><span data-stu-id="14062-108">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 <span data-ttu-id="14062-109">您可以选择性地指定 `TYPE` 指令将结果作为 `xml` 类型进行检索。</span><span class="sxs-lookup"><span data-stu-id="14062-109">You can optionally specify the `TYPE` directive to retrieve the results as `xml` type.</span></span> <span data-ttu-id="14062-110">`TYPE` 指令不会更改结果的内容。</span><span class="sxs-lookup"><span data-stu-id="14062-110">The `TYPE` directive does not change the content of the results.</span></span> <span data-ttu-id="14062-111">只影响结果的数据类型。</span><span class="sxs-lookup"><span data-stu-id="14062-111">Only the data type of the results is affected.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="14062-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14062-112">See Also</span></span>  
 [<span data-ttu-id="14062-113">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="14062-113">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
