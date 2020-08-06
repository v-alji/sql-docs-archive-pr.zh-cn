---
title: PATH 模式中的命名空间支持 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: rothja
ms.author: jroth
ms.openlocfilehash: abd6cd1f5590bffcd841b07897c9685faed4726f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687555"
---
# <a name="namespace-support-in-path-mode"></a><span data-ttu-id="02243-102">PATH 模式中的命名空间支持</span><span class="sxs-lookup"><span data-stu-id="02243-102">Namespace Support in PATH Mode</span></span>
  <span data-ttu-id="02243-103">PATH 模式中的命名空间支持是通过使用 WITH NAMESPACES 提供的。</span><span class="sxs-lookup"><span data-stu-id="02243-103">Namespace support in the PATH mode is provided by using WITH NAMESPACES.</span></span> <span data-ttu-id="02243-104">例如，下面的查询演示了如何使用 WITH NAMESPACES 语法声明一个命名空间 (a:)，随后即可在后续的 SELECT 语句中使用此命名空间：</span><span class="sxs-lookup"><span data-stu-id="02243-104">For example, the following query demonstrates the WITH NAMESPACES syntax to declare a namespace ("a:") that can then be used in the subsequent SELECT statement:</span></span>  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a><span data-ttu-id="02243-105">示例</span><span class="sxs-lookup"><span data-stu-id="02243-105">Examples</span></span>  
 <span data-ttu-id="02243-106">以下这些示例演示了使用 PATH 模式从 SELECT 查询生成 XML 的过程。</span><span class="sxs-lookup"><span data-stu-id="02243-106">These samples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="02243-107">这些查询中有许多都是针对 ProductModel 表的 Instructions 列中存储的自行车生产说明 XML 文档指定的。</span><span class="sxs-lookup"><span data-stu-id="02243-107">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02243-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02243-108">See Also</span></span>  
 [<span data-ttu-id="02243-109">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="02243-109">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
