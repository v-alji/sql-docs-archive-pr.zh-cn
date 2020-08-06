---
title: MultiPoint | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b741071b7986aceea4e49d4fde8293ef2c96fc2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590661"
---
# <a name="multipoint"></a><span data-ttu-id="7f46a-102">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="7f46a-102">MultiPoint</span></span>
  <span data-ttu-id="7f46a-103">`MultiPoint` 是零个点或更多个点的集合。</span><span class="sxs-lookup"><span data-stu-id="7f46a-103">A `MultiPoint` is a collection of zero or more points.</span></span> <span data-ttu-id="7f46a-104">`MultiPoint` 实例的边界为空。</span><span class="sxs-lookup"><span data-stu-id="7f46a-104">The boundary of a `MultiPoint` instance is empty.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7f46a-105">示例</span><span class="sxs-lookup"><span data-stu-id="7f46a-105">Examples</span></span>  
 <span data-ttu-id="7f46a-106">下面的示例创建一个 `geometry MultiPoint` 实例，该实例的 SRID 为 23 且包含两个点：一个点的坐标为 (2, 3)，另一个点的坐标为 (7, 8)，Z 值为 9.5。</span><span class="sxs-lookup"><span data-stu-id="7f46a-106">The following example creates a `geometry MultiPoint` instance with SRID 23 and two points: one point with the coordinates (2, 3), one point with the coordinates (7, 8), and a Z value of 9.5.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="7f46a-107">该 `MultiPoint` 实例也可使用 `STMPointFromText()` 表示，如下所示。</span><span class="sxs-lookup"><span data-stu-id="7f46a-107">This `MultiPoint` instance can also be expressed using `STMPointFromText()` as shown below.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="7f46a-108">下面的示例使用方法 `STGeometryN()` 来检索有关集合中第一个点的说明。</span><span class="sxs-lookup"><span data-stu-id="7f46a-108">The following example uses the method `STGeometryN()` to retrieve a description of the first point in the collection.</span></span>  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f46a-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f46a-109">See Also</span></span>  
 <span data-ttu-id="7f46a-110">[情况](point.md) </span><span class="sxs-lookup"><span data-stu-id="7f46a-110">[Point](point.md) </span></span>  
 [<span data-ttu-id="7f46a-111">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7f46a-111">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
