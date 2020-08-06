---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c701cdc2e8538a5b91093e17714fd9f6508d1c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578057"
---
# <a name="circularstring"></a><span data-ttu-id="ab8f2-102">CircularString</span><span class="sxs-lookup"><span data-stu-id="ab8f2-102">CircularString</span></span>
  <span data-ttu-id="ab8f2-103">`CircularString` 是零个或多个连续圆弧线段的集合。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-103">A `CircularString` is a collection of zero or more continuous circular arc segments.</span></span> <span data-ttu-id="ab8f2-104">圆弧线段是二维平面中由三个点定义的曲线段；第一个点不能与第三个点相同。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-104">A circular arc segment is a curved segment defined by three points in a two-dimensional plane; the first point cannot be the same as the third point.</span></span> <span data-ttu-id="ab8f2-105">如果圆弧线段的所有三个点共线，则将该圆弧线段视为一条直线段。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-105">If all three points of a circular arc segment are collinear, the arc segment is treated as a line segment.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ab8f2-106">有关中引入的新空间功能的详细说明和示例 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] （包括 `CircularString` 子类型），请下载白皮书[SQL Server 2012 中的新的空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-106">For a detailed description and examples of the new spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CircularString` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

## <a name="circularstring-instances"></a><span data-ttu-id="ab8f2-107">CircularString 实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-107">CircularString instances</span></span>
 <span data-ttu-id="ab8f2-108">下面的图形显示了有效的 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-108">The drawing below shows valid `CircularString` instances:</span></span>

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a><span data-ttu-id="ab8f2-109">接受的实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-109">Accepted instances</span></span>
 <span data-ttu-id="ab8f2-110">`CircularString`如果实例为空或包含奇数个点 n，其中 n > 1，则接受该实例。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-110">A `CircularString` instance is accepted if it is either empty or contains an odd number of points, n, where n > 1.</span></span> <span data-ttu-id="ab8f2-111">下面的 `CircularString` 实例均为已接受实例。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-111">The following `CircularString` instances are accepted.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 <span data-ttu-id="ab8f2-112">`@g3` 显示 `CircularString` 实例可能被接受，但无效。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-112">`@g3` shows that `CircularString` instance may be accepted, but not valid.</span></span> <span data-ttu-id="ab8f2-113">下面的 CircularString 实例声明未被接受。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-113">The following CircularString instance declaration is not accepted.</span></span> <span data-ttu-id="ab8f2-114">此声明引发 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-114">This declaration throws a `System.FormatException`.</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="ab8f2-115">有效实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-115">Valid instances</span></span>
 <span data-ttu-id="ab8f2-116">有效 `CircularString` 实例必须为空或具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-116">A valid `CircularString` instance must be empty or have the following attributes:</span></span>

-   <span data-ttu-id="ab8f2-117">必须至少包含一条圆弧线段（也就是至少有三个点）。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-117">It must contain at least one circular arc segment (that is, have a minimum of three points).</span></span>

-   <span data-ttu-id="ab8f2-118">序列中的每条圆弧线段（最后一条线段除外）的最后一个端点必须是序列中后一条线段的第一个端点。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-118">The last endpoint for each circular arc segment in the sequence, except for the last segment, must be the first endpoint for the next segment in the sequence.</span></span>

-   <span data-ttu-id="ab8f2-119">必须有奇数个点。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-119">It must have an odd number of points.</span></span>

-   <span data-ttu-id="ab8f2-120">不能有一段与自身重合。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-120">It cannot overlap itself over an interval.</span></span>

-   <span data-ttu-id="ab8f2-121">虽然 `CircularString` 实例可能包含直线段，但这些直线段必须由三个共线点定义。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-121">Although `CircularString` instances may contain line segments, these line segments must be defined by three collinear points.</span></span>

 <span data-ttu-id="ab8f2-122">下面的示例显示有效的 `CircularString` 实例。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-122">The following example shows valid `CircularString` instances.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 <span data-ttu-id="ab8f2-123">`CircularString` 实例必须至少包含两条圆弧线段以定义完整的圆。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-123">A `CircularString` instance must contain at least two circular arc segments to define a complete circle.</span></span> <span data-ttu-id="ab8f2-124">`CircularString` 实例不能使用一条圆弧线段（例如（1 1、3 1、1 1））定义一个完整的圆。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-124">A `CircularString` instance cannot use a single circular arc segment (such as (1 1, 3 1, 1 1)) to define a complete circle.</span></span> <span data-ttu-id="ab8f2-125">使用（1 1、2 2、3 1、2 0、1 1）定义圆。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-125">Use (1 1, 2 2, 3 1, 2 0, 1 1) to define the circle.</span></span>

 <span data-ttu-id="ab8f2-126">下面的示例显示无效的 CircularString 实例。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-126">The following example shows CircularString instances that are not valid.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a><span data-ttu-id="ab8f2-127">具有共线点的实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-127">Instances with collinear points</span></span>
 <span data-ttu-id="ab8f2-128">在下列情况下，圆弧线段将被视为直线段：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-128">In the following cases a circular arc segment will be treated as a line segment:</span></span>

-   <span data-ttu-id="ab8f2-129">当所有三个点共线时，例如（1 3、4 4、7 5）。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-129">When all three points are collinear (for example, (1 3, 4 4, 7 5)).</span></span>

-   <span data-ttu-id="ab8f2-130">当第一个点和中间的点相同但第三个点不同时，例如（1 3、1 3、7 5）。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-130">When the first and middle point are the same, but the third point is different (for example, (1 3, 1 3, 7 5)).</span></span>

-   <span data-ttu-id="ab8f2-131">当中间的点和最后一个点相同但第一个点不同时，例如（1 3、4 4、4 4）。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-131">When the middle and last point are the same, but the first point is different (for example, (1 3, 4 4, 4 4)).</span></span>

## <a name="examples"></a><span data-ttu-id="ab8f2-132">示例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-132">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a><span data-ttu-id="ab8f2-133">A.</span><span class="sxs-lookup"><span data-stu-id="ab8f2-133">A.</span></span> <span data-ttu-id="ab8f2-134">使用空的 CircularString 实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-134">Instantiating a Geometry Instance with an Empty CircularString</span></span>
 <span data-ttu-id="ab8f2-135">该示例说明如何创建一个空的 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-135">This example shows how to create an empty `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a><span data-ttu-id="ab8f2-136">B.</span><span class="sxs-lookup"><span data-stu-id="ab8f2-136">B.</span></span> <span data-ttu-id="ab8f2-137">使用具有一条圆弧线段的 CircularString 实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-137">Instantiating a Geometry Instance Using a CircularString with One Circular Arc Segment</span></span>
 <span data-ttu-id="ab8f2-138">下面的示例演示如何创建一个具有一条圆弧线段（半圆）的 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-138">The following example shows how to create a `CircularString` instance with a single circular arc segment (half-circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a><span data-ttu-id="ab8f2-139">C.</span><span class="sxs-lookup"><span data-stu-id="ab8f2-139">C.</span></span> <span data-ttu-id="ab8f2-140">使用具有多条圆弧线段的 CircularString 实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-140">Instantiating a Geometry Instance Using a CircularString with Multiple Circular Arc Segments</span></span>
 <span data-ttu-id="ab8f2-141">下面的示例演示如何创建一个具有多条圆弧线段（整圆）的 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-141">The following example shows how to create a `CircularString` instance with more than one circular arc segment (full circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 <span data-ttu-id="ab8f2-142">此代码产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-142">This produces the following output:</span></span>

```
Circumference = 6.28319
```

 <span data-ttu-id="ab8f2-143">在使用 `LineString` 而不使用 `CircularString` 时，比较输出结果：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-143">Compare the output when `LineString` is used instead of `CircularString`:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 <span data-ttu-id="ab8f2-144">此代码产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-144">This produces the following output:</span></span>

```
Perimeter = 5.65685
```

 <span data-ttu-id="ab8f2-145">请注意，该示例的值 `CircularString` 接近 2&#x03c0; (2 \* pi) ，这是圆的实际周长。</span><span class="sxs-lookup"><span data-stu-id="ab8f2-145">Notice that the value for the `CircularString` example is close to 2&#x03c0; (2 \* pi), which is the actual circumference of the circle.</span></span>

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a><span data-ttu-id="ab8f2-146">D.</span><span class="sxs-lookup"><span data-stu-id="ab8f2-146">D.</span></span> <span data-ttu-id="ab8f2-147">在同一语句中使用 CircularString 声明和实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-147">Declaring and Instantiating a Geometry Instance with a CircularString in the Same Statement</span></span>
 <span data-ttu-id="ab8f2-148">此代码段说明了如何在同一语句中使用 `geometry` 声明和实例化 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-148">This snippet shows how to declare and instantiate a `geometry` instance with a `CircularString` in the same statement:</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a><span data-ttu-id="ab8f2-149">E.</span><span class="sxs-lookup"><span data-stu-id="ab8f2-149">E.</span></span> <span data-ttu-id="ab8f2-150">使用 CircularString 实例化一个地域实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-150">Instantiating a Geography Instance with a CircularString</span></span>
 <span data-ttu-id="ab8f2-151">下面的示例演示如何使用 `geography` 声明和实例化 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-151">The following example shows how to declare and instantiate a `geography` instance with a `CircularString`:</span></span>

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a><span data-ttu-id="ab8f2-152">F.</span><span class="sxs-lookup"><span data-stu-id="ab8f2-152">F.</span></span> <span data-ttu-id="ab8f2-153">使用直线 CircularString 实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="ab8f2-153">Instantiating a Geometry Instance with a CircularString that is a Straight Line</span></span>
 <span data-ttu-id="ab8f2-154">下面的示例演示如何创建一个直线 `CircularString` 实例：</span><span class="sxs-lookup"><span data-stu-id="ab8f2-154">The following example shows how to create a `CircularString` instance that is a straight line:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a><span data-ttu-id="ab8f2-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab8f2-155">See Also</span></span>
 <span data-ttu-id="ab8f2-156">[空间数据类型概述](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;geography 数据类型&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STIsValid &#40;geography 数据类型&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)数据类型&#41;STEndpoint &#40;geometry 数据[类型&#41;STPointN](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [&#40;geometry 数据](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)[类型&#41;STNumPoints](linestring.md) &#40;geometry[数据](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)[类型&#41;STIsRing](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) &#40;geometry[数据类型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [STIsClosed &#40;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)</span><span class="sxs-lookup"><span data-stu-id="ab8f2-156">[Spatial Data Types Overview](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [LineString](linestring.md)</span></span>


