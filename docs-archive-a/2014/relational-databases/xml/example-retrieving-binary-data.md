---
title: 示例：检索二进制数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: rothja
ms.author: jroth
ms.openlocfilehash: 516c7d91d0a6ebac7366b4bb3cbafe5d05aaa232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591153"
---
# <a name="example-retrieving-binary-data"></a><span data-ttu-id="d1843-102">示例：检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="d1843-102">Example: Retrieving Binary Data</span></span>
  <span data-ttu-id="d1843-103">下面的查询返回在 `varbinary(max)` 类型列中存储的产品照片。</span><span class="sxs-lookup"><span data-stu-id="d1843-103">The following query returns the product photo stored in a `varbinary(max)` type column.</span></span> <span data-ttu-id="d1843-104">在此查询中指定了 `BINARY BASE64` 选项，以便以 base64 编码格式返回二进制数据。</span><span class="sxs-lookup"><span data-stu-id="d1843-104">The `BINARY BASE64` option is specified in the query to return the binary data in base64-encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1843-105">示例</span><span class="sxs-lookup"><span data-stu-id="d1843-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 <span data-ttu-id="d1843-106">结果如下：</span><span class="sxs-lookup"><span data-stu-id="d1843-106">This is the result:</span></span>  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1843-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1843-107">See Also</span></span>  
 [<span data-ttu-id="d1843-108">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="d1843-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
