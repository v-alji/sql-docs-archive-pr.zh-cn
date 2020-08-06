---
title: GeometryCollection | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 71d2234a9b73b7647554e364fe3864f089a47a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590674"
---
# <a name="geometrycollection"></a><span data-ttu-id="19b1f-102">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="19b1f-102">GeometryCollection</span></span>
  <span data-ttu-id="19b1f-103">`GeometryCollection` 是零个或更多个 `geometry` 或 `geography` 实例的集合。</span><span class="sxs-lookup"><span data-stu-id="19b1f-103">A `GeometryCollection` is a collection of zero or more `geometry` or `geography` instances.</span></span> <span data-ttu-id="19b1f-104">`GeometryCollection` 可以为空。</span><span class="sxs-lookup"><span data-stu-id="19b1f-104">A `GeometryCollection` can be empty.</span></span>  
  
## <a name="geometrycollection-instances"></a><span data-ttu-id="19b1f-105">GeometryCollection 实例</span><span class="sxs-lookup"><span data-stu-id="19b1f-105">GeometryCollection Instances</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="19b1f-106">已接受的实例</span><span class="sxs-lookup"><span data-stu-id="19b1f-106">Accepted Instances</span></span>  
 <span data-ttu-id="19b1f-107">要接受某个 `GeometryCollection` 实例，该实例必须为空的 `GeometryCollection` 实例或组成 `GeometryCollection` 实例的所有实例必须为接受的实例。</span><span class="sxs-lookup"><span data-stu-id="19b1f-107">For a `GeometryCollection` instance to be accepted, it must either be an empty `GeometryCollection` instance or all the instances comprising the `GeometryCollection` instance must be accepted instances.</span></span> <span data-ttu-id="19b1f-108">下面的示例显示接受的实例。</span><span class="sxs-lookup"><span data-stu-id="19b1f-108">The following example shows accepted instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 <span data-ttu-id="19b1f-109">下面的示例引发一个 `System.FormatException`，因为 `LinesString` 实例中的 `GeometryCollection` 实例不是接受的实例。</span><span class="sxs-lookup"><span data-stu-id="19b1f-109">The following example throws a `System.FormatException` because the `LinesString` instance in the `GeometryCollection` instance is not accepted.</span></span>  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="19b1f-110">有效实例</span><span class="sxs-lookup"><span data-stu-id="19b1f-110">Valid Instances</span></span>  
 <span data-ttu-id="19b1f-111">当组成 `GeometryCollection` 实例的所有实例均有效时，`GeometryCollection` 实例有效。</span><span class="sxs-lookup"><span data-stu-id="19b1f-111">A `GeometryCollection` instance is valid when all instances that comprise the `GeometryCollection` instance are valid.</span></span> <span data-ttu-id="19b1f-112">以下示例显示三个有效的 `GeometryCollection` 实例和一个无效的实例。</span><span class="sxs-lookup"><span data-stu-id="19b1f-112">The following shows three valid `GeometryCollection` instances and one instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="19b1f-113">`@g4` 无效，因为 `Polygon` 实例中的 `GeometryCollection` 实例无效。</span><span class="sxs-lookup"><span data-stu-id="19b1f-113">`@g4` is not valid because the `Polygon` instance in the `GeometryCollection` instance is not valid.</span></span>  
  
 <span data-ttu-id="19b1f-114">有关接受的和有效的实例的详细信息，请参阅 [Point](point.md)、 [MultiPoint](multipoint.md)、 [LineString](linestring.md)、 [MultiLineString](multilinestring.md)、 [Polygon](polygon.md)和 [MultiPolygon](multipolygon.md)。</span><span class="sxs-lookup"><span data-stu-id="19b1f-114">For more information on accepted and valid instances, see [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md), and [MultiPolygon](multipolygon.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="19b1f-115">示例</span><span class="sxs-lookup"><span data-stu-id="19b1f-115">Examples</span></span>  
 <span data-ttu-id="19b1f-116">下面的示例实例化一个包含 `geometry``GeometryCollection` 实例和 `Point` 实例的 `Polygon` ，它具有 Z 值，且 SRID 为 1。</span><span class="sxs-lookup"><span data-stu-id="19b1f-116">The following example instantiates a `geometry``GeometryCollection` with Z values in SRID 1 containing a `Point` instance and a `Polygon` instance.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="19b1f-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19b1f-117">See Also</span></span>  
 [<span data-ttu-id="19b1f-118">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="19b1f-118">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
