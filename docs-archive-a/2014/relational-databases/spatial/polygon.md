---
title: Polygon | Microsoft Docs
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 040bb8a2558cc57b1b99a3ce984bec3c8925bc0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590656"
---
# <a name="polygon"></a><span data-ttu-id="9fd11-102">Polygon</span><span class="sxs-lookup"><span data-stu-id="9fd11-102">Polygon</span></span>
  <span data-ttu-id="9fd11-103">`Polygon`是存储为一系列点的二维表面，这些点定义一个外部边界环和零个或多个内部环。</span><span class="sxs-lookup"><span data-stu-id="9fd11-103">A `Polygon` is a two-dimensional surface stored as a sequence of points defining an exterior bounding ring and zero or more interior rings.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="9fd11-104">Polygon 实例</span><span class="sxs-lookup"><span data-stu-id="9fd11-104">Polygon instances</span></span>
 <span data-ttu-id="9fd11-105">可以从至少具有三个不同点的环中构建一个 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-105">A `Polygon` instance can be formed from a ring that has at least three distinct points.</span></span> <span data-ttu-id="9fd11-106">`Polygon` 实例也可以为空。</span><span class="sxs-lookup"><span data-stu-id="9fd11-106">A `Polygon` instance can also be empty.</span></span>

 <span data-ttu-id="9fd11-107">`Polygon` 的外部环和任意内部环定义了其边界。</span><span class="sxs-lookup"><span data-stu-id="9fd11-107">The exterior and any interior rings of a `Polygon` define its boundary.</span></span> <span data-ttu-id="9fd11-108">环内部的空间定义了 `Polygon` 的内部。</span><span class="sxs-lookup"><span data-stu-id="9fd11-108">The space within the rings defines the interior of the `Polygon`.</span></span>

 <span data-ttu-id="9fd11-109">下图显示了 `Polygon` 实例的示例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-109">The illustration below shows examples of `Polygon` instances.</span></span>

 <span data-ttu-id="9fd11-110">![几何 Polygon 实例的示例](../../database-engine/media/polygon.gif "几何 Polygon 实例的示例")</span><span class="sxs-lookup"><span data-stu-id="9fd11-110">![Examples of geometry Polygon instances](../../database-engine/media/polygon.gif "Examples of geometry Polygon instances")</span></span>

 <span data-ttu-id="9fd11-111">如图中所示：</span><span class="sxs-lookup"><span data-stu-id="9fd11-111">As shown in the illustration:</span></span>

1.  <span data-ttu-id="9fd11-112">图 1 是由外部环定义其边界的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-112">Figure 1 is a `Polygon` instance whose boundary is defined by an exterior ring.</span></span>

2.  <span data-ttu-id="9fd11-113">图 2 是由外部环和两个内部环定义其边界的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-113">Figure 2 is a `Polygon` instance whose boundary is defined by an exterior ring and two interior rings.</span></span> <span data-ttu-id="9fd11-114">内部环内的面积是 `Polygon` 实例的外部环的一部分。</span><span class="sxs-lookup"><span data-stu-id="9fd11-114">The area inside the interior rings is part of the exterior of the `Polygon` instance.</span></span>

3.  <span data-ttu-id="9fd11-115">图 3 是一个有效的 `Polygon` 实例，因为其内部环在单个切点处相交。</span><span class="sxs-lookup"><span data-stu-id="9fd11-115">Figure 3 is a valid `Polygon` instance because its interior rings intersect at a single tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="9fd11-116">接受的实例</span><span class="sxs-lookup"><span data-stu-id="9fd11-116">Accepted instances</span></span>
 <span data-ttu-id="9fd11-117">已接受的 `Polygon` 实例是可以在不引发异常的情况下存储到 `geometry` 或 `geography` 变量中的实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-117">Accepted `Polygon` instances are instances that can be stored in a `geometry` or `geography` variable without throwing an exception.</span></span> <span data-ttu-id="9fd11-118">下面是一些已接受的 `Polygon` 实例：</span><span class="sxs-lookup"><span data-stu-id="9fd11-118">The following are accepted `Polygon` instances:</span></span>

-   <span data-ttu-id="9fd11-119">空的 `Polygon` 实例</span><span class="sxs-lookup"><span data-stu-id="9fd11-119">An Empty `Polygon` instance</span></span>

-   <span data-ttu-id="9fd11-120">具有一个可接受的外部环和零个或多个可接受的内部环的 `Polygon` 实例</span><span class="sxs-lookup"><span data-stu-id="9fd11-120">A `Polygon` instance that has an acceptable exterior ring and zero or more acceptable interior rings</span></span>

 <span data-ttu-id="9fd11-121">要使环可接受，需要满足以下条件。</span><span class="sxs-lookup"><span data-stu-id="9fd11-121">The following criteria are needed for a ring to be acceptable.</span></span>

-   <span data-ttu-id="9fd11-122">`LineString` 实例必须是已接受的实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-122">The `LineString` instance must be accepted.</span></span>

-   <span data-ttu-id="9fd11-123">`LineString` 实例至少必须有四个点。</span><span class="sxs-lookup"><span data-stu-id="9fd11-123">The `LineString` instance must have at least four points.</span></span>

-   <span data-ttu-id="9fd11-124">`LineString` 实例的起始点和结束点必须相同。</span><span class="sxs-lookup"><span data-stu-id="9fd11-124">The starting and ending points of the `LineString` instance must be the same.</span></span>

 <span data-ttu-id="9fd11-125">下面的示例显示接受的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-125">The following example shows accepted `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON EMPTY';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
```

 <span data-ttu-id="9fd11-126">`@g4` 和 `@g5` 显示接受的 `Polygon` 实例可能不是有效的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-126">As `@g4` and `@g5` show an accepted `Polygon` instance may not be a valid `Polygon` instance.</span></span> <span data-ttu-id="9fd11-127">`@g5` 还显示 Polygon 实例只需包含一个具有任意四个点的环便可以被接受。</span><span class="sxs-lookup"><span data-stu-id="9fd11-127">`@g5` also shows that a Polygon instance needs to only contain a ring with any four points to be accepted.</span></span>

 <span data-ttu-id="9fd11-128">下面的示例引发 `System.FormatException`，因为 `Polygon` 实例未被接受。</span><span class="sxs-lookup"><span data-stu-id="9fd11-128">The following examples throw a `System.FormatException` because the `Polygon` instances are not accepted.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';
```

 <span data-ttu-id="9fd11-129">`@g1` 未被接受，因为外部环的 `LineString` 实例不包含足够的点。</span><span class="sxs-lookup"><span data-stu-id="9fd11-129">`@g1` is not accepted because the `LineString` instance for the exterior ring does not contain enough points.</span></span> <span data-ttu-id="9fd11-130">`@g2` 未被接受，因为外部环 `LineString` 实例的起始点与结束点不同。</span><span class="sxs-lookup"><span data-stu-id="9fd11-130">`@g2` is not accepted because the starting point of the exterior ring `LineString` instance is not the same as the ending point.</span></span> <span data-ttu-id="9fd11-131">下面的示例有一个可接受的外部环，但内部环不可接受。</span><span class="sxs-lookup"><span data-stu-id="9fd11-131">The following example has an acceptable exterior ring, but the interior ring is not acceptable.</span></span> <span data-ttu-id="9fd11-132">这也会引发 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="9fd11-132">This also throws a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="9fd11-133">有效实例</span><span class="sxs-lookup"><span data-stu-id="9fd11-133">Valid instances</span></span>
 <span data-ttu-id="9fd11-134">`Polygon` 的内部环在单个切点处既可与自身接触也可彼此接触，但如果 `Polygon` 的内部环交叉，则该实例无效。</span><span class="sxs-lookup"><span data-stu-id="9fd11-134">The interior rings of a `Polygon` can touch both themselves and each other at single tangent points, but if the interior rings of a `Polygon` cross, the instance is not valid.</span></span>

 <span data-ttu-id="9fd11-135">下面的示例显示有效的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-135">The following example shows valid `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="9fd11-136">`@g3` 有效，因为两个内部环在一个点相切并且没有相互交叉。</span><span class="sxs-lookup"><span data-stu-id="9fd11-136">`@g3` is valid because the two interior rings touch at a single point and do not cross each other.</span></span> <span data-ttu-id="9fd11-137">下面的示例显示无效的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-137">The following example shows `Polygon` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();
```

 <span data-ttu-id="9fd11-138">`@g1` 无效，因为内部环在两个位置接触外部环。</span><span class="sxs-lookup"><span data-stu-id="9fd11-138">`@g1` is not valid because the inner ring touches the exterior ring in two places.</span></span> <span data-ttu-id="9fd11-139">`@g2` 无效，因为第二个内部环位于第一个内部环的内部。</span><span class="sxs-lookup"><span data-stu-id="9fd11-139">`@g2` is not valid because the second inner ring in within the interior of the first inner ring.</span></span> <span data-ttu-id="9fd11-140">`@g3` 无效，因为两个内部环在多个连续点接触。</span><span class="sxs-lookup"><span data-stu-id="9fd11-140">`@g3` is not valid because the two inner rings touch at multiple consecutive points.</span></span> <span data-ttu-id="9fd11-141">`@g4` 无效，因为两个内部环的内部重叠。</span><span class="sxs-lookup"><span data-stu-id="9fd11-141">`@g4` is not valid because the interiors of the two inner rings overlap.</span></span> <span data-ttu-id="9fd11-142">`@g5` 无效，因为外部环不是第一个环形。</span><span class="sxs-lookup"><span data-stu-id="9fd11-142">`@g5` is not valid because the exterior ring is not the first ring.</span></span> <span data-ttu-id="9fd11-143">`@g6` 无效，因为环未至少具有三个不同的点。</span><span class="sxs-lookup"><span data-stu-id="9fd11-143">`@g6` is not valid because the ring does not have at least three distinct points.</span></span>

## <a name="examples"></a><span data-ttu-id="9fd11-144">示例</span><span class="sxs-lookup"><span data-stu-id="9fd11-144">Examples</span></span>
 <span data-ttu-id="9fd11-145">下面的示例创建了一个带有孔和 SRID 为 10 的简单 `geometry``Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-145">The following example creates a simple `geometry``Polygon` instance with a hole and SRID 10.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);
```

 <span data-ttu-id="9fd11-146">可能输入无效的实例并转换为有效的 `geometry` 实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-146">Aninstance that is not valid may be entered and converted to a valid `geometry` instance.</span></span> <span data-ttu-id="9fd11-147">在下列 `Polygon`示例中，内部环和外部环重叠且该实例无效。</span><span class="sxs-lookup"><span data-stu-id="9fd11-147">In the following example of a `Polygon`, the interior and exterior rings overlap and the instance is not valid.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');
```

 <span data-ttu-id="9fd11-148">在下面的示例中，无效实例通过 `MakeValid()`成为有效实例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-148">In the following example, the invalid instance is made valid with `MakeValid()`.</span></span>

```
SET @g = @g.MakeValid();
SELECT @g.ToString();
```

 <span data-ttu-id="9fd11-149">以上示例中返回的 `geometry` 实例为 `MultiPolygon`。</span><span class="sxs-lookup"><span data-stu-id="9fd11-149">The `geometry` instance returned from the above example is a `MultiPolygon`.</span></span>

```
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))
```

 <span data-ttu-id="9fd11-150">下面是另一个演示将无效实例转换为有效的几何图形实例的示例。</span><span class="sxs-lookup"><span data-stu-id="9fd11-150">Here is another example of converting an invalid instance to a valid geometry instance.</span></span> <span data-ttu-id="9fd11-151">在下面的示例中，已经使用完全相同的三个点创建了 `Polygon` 实例：</span><span class="sxs-lookup"><span data-stu-id="9fd11-151">In the following example the `Polygon` instance has been created using three points that are exactly the same:</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');
SET @g = @g.MakeValid();
SELECT @g.ToString()
```

 <span data-ttu-id="9fd11-152">上面返回的几何图形实例是 `Point(1 3)`。</span><span class="sxs-lookup"><span data-stu-id="9fd11-152">The geometry instance returned above is a `Point(1 3)`.</span></span>  <span data-ttu-id="9fd11-153">如果给出的 `Polygon` 是 `POLYGON((1 3, 1 5, 1 3, 1 3))` ，则 `MakeValid()` 将返回 `LINESTRING(1 3, 1 5)`。</span><span class="sxs-lookup"><span data-stu-id="9fd11-153">If the `Polygon` given is `POLYGON((1 3, 1 5, 1 3, 1 3))` then `MakeValid()` would return `LINESTRING(1 3, 1 5)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fd11-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fd11-154">See Also</span></span>
 <span data-ttu-id="9fd11-155">[STArea &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [MultiPolygon](../spatial/polygon.md) [空间数据 &#40;SQL Server](../spatial/spatial-data-sql-server.md)&#41;[STIsValid &#40;geography 数据类型&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STIsValid &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)</span><span class="sxs-lookup"><span data-stu-id="9fd11-155">[STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [MultiPolygon](../spatial/polygon.md) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)</span></span>


