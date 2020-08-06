---
title: CurvePolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e000a1d8-a049-4542-bfeb-943fd6ab3969
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b90fdbd9a0bc80dfc6a82416d0193b2951fe13ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578050"
---
# <a name="curvepolygon"></a><span data-ttu-id="f9c57-102">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="f9c57-102">CurvePolygon</span></span>
  <span data-ttu-id="f9c57-103"> 是由一个外部边界环以及零个或多个内环界定的在拓扑结构上闭合的图面。</span><span class="sxs-lookup"><span data-stu-id="f9c57-103">A `CurvePolygon` is a topologically closed surface defined by an exterior bounding ring and zero or more interior rings</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f9c57-104">有关中引入的空间功能的详细说明和示例 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] （包括 `CurvePolygon` 子类型），请下载白皮书[SQL Server 2012 中的新的空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="f9c57-104">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CurvePolygon` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="f9c57-105">以下条件定义实例的属性 `CurvePolygon` ：</span><span class="sxs-lookup"><span data-stu-id="f9c57-105">The following criteria define attributes of a `CurvePolygon` instance:</span></span>  
  
-   <span data-ttu-id="f9c57-106">该 `CurvePolygon` 实例的边界由外环和所有内环界定。</span><span class="sxs-lookup"><span data-stu-id="f9c57-106">The boundary of the `CurvePolygon` instance is defined by the exterior ring and all interior rings.</span></span>  
  
-   <span data-ttu-id="f9c57-107">该 `CurvePolygon` 实例的内部是外环和所有内环之间的空间。</span><span class="sxs-lookup"><span data-stu-id="f9c57-107">The interior of the `CurvePolygon` instance is the space between the exterior ring and all of the interior rings.</span></span>  
  
 <span data-ttu-id="f9c57-108">`CurvePolygon` 实例不同于 `Polygon` 实例，因为 `CurvePolygon` 实例可以包含以下圆弧线段：`CircularString` 和 `CompoundCurve`。</span><span class="sxs-lookup"><span data-stu-id="f9c57-108">A `CurvePolygon` instance differs from a `Polygon` instance in that a `CurvePolygon` instance may contain the following circular arc segments: `CircularString` and `CompoundCurve`.</span></span>  
  
## <a name="compoundcurve-instances"></a><span data-ttu-id="f9c57-109">CompoundCurve 实例</span><span class="sxs-lookup"><span data-stu-id="f9c57-109">CompoundCurve instances</span></span>  
 <span data-ttu-id="f9c57-110">下图显示有效的 `CurvePolygon` 图形：</span><span class="sxs-lookup"><span data-stu-id="f9c57-110">Illustration below shows valid `CurvePolygon` figures:</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="f9c57-111">接受的实例</span><span class="sxs-lookup"><span data-stu-id="f9c57-111">Accepted instances</span></span>  
 <span data-ttu-id="f9c57-112">为使 `CurvePolygon` 实例可接受，它需要或者为空，或者仅包含接受的圆弧环。</span><span class="sxs-lookup"><span data-stu-id="f9c57-112">For a `CurvePolygon` instance to be accepted, it needs to be either empty or contain only circular arc rings that are accepted.</span></span> <span data-ttu-id="f9c57-113">接受的圆弧环满足以下要求。</span><span class="sxs-lookup"><span data-stu-id="f9c57-113">An accepted circular arc ring meets the following requirements.</span></span>  
  
1.  <span data-ttu-id="f9c57-114">是接受的 `LineString`、 `CircularString` 或 `CompoundCurve` 实例。</span><span class="sxs-lookup"><span data-stu-id="f9c57-114">Is an accepted `LineString`, `CircularString`, or `CompoundCurve` instance.</span></span> <span data-ttu-id="f9c57-115">有关接受的实例的详细信息，请参阅 [LineString](linestring.md)、 [CircularString](circularstring.md)和 [CompoundCurve](compoundcurve.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c57-115">For more information on accepted instances, see [LineString](linestring.md), [CircularString](circularstring.md), and [CompoundCurve](compoundcurve.md).</span></span>  
  
2.  <span data-ttu-id="f9c57-116">具有至少四个点。</span><span class="sxs-lookup"><span data-stu-id="f9c57-116">Has at least four points.</span></span>  
  
3.  <span data-ttu-id="f9c57-117">起点和终点具有相同的 X 和 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="f9c57-117">The start and end point have the same X and Y coordinates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9c57-118">Z 和 M 值被忽略。</span><span class="sxs-lookup"><span data-stu-id="f9c57-118">Z and M values are ignored.</span></span>  
  
 <span data-ttu-id="f9c57-119">下面的示例显示接受的 `CurvePolygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="f9c57-119">The following example shows accepted `CurvePolygon` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0, 0 0))';  
DECLARE @g3 geometry = 'CURVEPOLYGON((0 0 1, 0 0 2, 0 0 3, 0 0 3))'  
DECLARE @g4 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
DECLARE @g5 geography = 'CURVEPOLYGON((-122.3 47, 122.3 -47, 125.7 -49, 121 -38, -122.3 47))';  
```  
  
 <span data-ttu-id="f9c57-120">`@g3` 已被接受，即使在起点和终点具有不同的 Z 值时也是如此，因为 Z 值被忽略。</span><span class="sxs-lookup"><span data-stu-id="f9c57-120">`@g3` is accepted even though the start and end points have different Z values because Z values are ignored.</span></span> <span data-ttu-id="f9c57-121"> 已被接受，即使  类型实例无效时也是如此。</span><span class="sxs-lookup"><span data-stu-id="f9c57-121">`@g5` is accepted even though the `geography` type instance is not valid.</span></span>  
  
 <span data-ttu-id="f9c57-122">下面的示例引发 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="f9c57-122">The following examples throw `System.FormatException`.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON((0 5, 0 0, 0 0, 0 0))';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0))';  
```  
  
 <span data-ttu-id="f9c57-123">`@g1` 不被接受，因为起点和终点不具有相同的 Y 值。</span><span class="sxs-lookup"><span data-stu-id="f9c57-123">`@g1` is not accepted because the start and end points do not have the same Y value.</span></span> <span data-ttu-id="f9c57-124">`@g2` 不被接受，因为环没有足够的点。</span><span class="sxs-lookup"><span data-stu-id="f9c57-124">`@g2` is not accepted because the ring does not have enough points.</span></span>  
  
### <a name="valid-instances"></a><span data-ttu-id="f9c57-125">有效实例</span><span class="sxs-lookup"><span data-stu-id="f9c57-125">Valid instances</span></span>  
 <span data-ttu-id="f9c57-126">为使 `CurvePolygon` 实例有效，外环和内环都必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="f9c57-126">For a `CurvePolygon` instance to be valid both exterior and interior rings must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="f9c57-127">它们只能在单个切点处接触。</span><span class="sxs-lookup"><span data-stu-id="f9c57-127">They may only touch at single tangent points.</span></span>  
  
2.  <span data-ttu-id="f9c57-128">它们不能彼此交叉。</span><span class="sxs-lookup"><span data-stu-id="f9c57-128">They cannot cross each other.</span></span>  
  
3.  <span data-ttu-id="f9c57-129">每个环都必须至少包含四个点。</span><span class="sxs-lookup"><span data-stu-id="f9c57-129">Each ring must contain at least four points.</span></span>  
  
4.  <span data-ttu-id="f9c57-130">每个环都必须是可接受的曲线类型。</span><span class="sxs-lookup"><span data-stu-id="f9c57-130">Each ring must be an acceptable curve type.</span></span>  
  
 <span data-ttu-id="f9c57-131"> 实例根据其是  还是  数据类型，也需要满足特定的条件。</span><span class="sxs-lookup"><span data-stu-id="f9c57-131">`CurvePolygon` instances also need to meet specific criteria depending on whether they are `geometry` or `geography` data types.</span></span>  
  
#### <a name="geometry-data-type"></a><span data-ttu-id="f9c57-132">geometry 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9c57-132">Geometry data type</span></span>  
 <span data-ttu-id="f9c57-133">一个有效的 **geometryCurvePolygon** 实例必须具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="f9c57-133">A valid **geometryCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="f9c57-134">所有内环都必须包含在外环内。</span><span class="sxs-lookup"><span data-stu-id="f9c57-134">All the interior rings must be contained within the exterior ring.</span></span>  
  
2.  <span data-ttu-id="f9c57-135">可具有多个内环，但一个外环不能包含另一个内环。</span><span class="sxs-lookup"><span data-stu-id="f9c57-135">May have multiple interior rings, but an interior ring cannot contain another interior ring.</span></span>  
  
3.  <span data-ttu-id="f9c57-136">环不能与自身或其他环交叉。</span><span class="sxs-lookup"><span data-stu-id="f9c57-136">No ring can cross itself or another ring.</span></span>  
  
4.  <span data-ttu-id="f9c57-137">环只能在单个切点处接触（环接触的点数必须有限）。</span><span class="sxs-lookup"><span data-stu-id="f9c57-137">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
5.  <span data-ttu-id="f9c57-138">多边形的内部必须连接。</span><span class="sxs-lookup"><span data-stu-id="f9c57-138">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="f9c57-139">下面的示例显示有效的 **geometryCurvePolygon** 实例。</span><span class="sxs-lookup"><span data-stu-id="f9c57-139">The following example shows valid **geometryCurvePolygon** instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
 <span data-ttu-id="f9c57-140">CurvePolygon 实例具有与 Polygon 实例大体上相同的有效性规则，只有一个例外，就是 CurvePolygon 实例可接受新的圆弧线段类型。</span><span class="sxs-lookup"><span data-stu-id="f9c57-140">CurvePolygon instances have the same validity rules as Polygon instances with the exception that CurvePolygon instances may accept the new circular arc segment types.</span></span> <span data-ttu-id="f9c57-141">有关有效实例或无效实例的更多示例，请参阅 [Polygon](polygon.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c57-141">For more examples of instances that are valid or not valid, see [Polygon](polygon.md).</span></span>  
  
#### <a name="geography-data-type"></a><span data-ttu-id="f9c57-142">geography 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9c57-142">Geography data type</span></span>  
 <span data-ttu-id="f9c57-143">一个有效的 **geographyCurvePolygon** 实例必须具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="f9c57-143">A valid **geographyCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="f9c57-144">多边形的内部使用左手定律进行连接。</span><span class="sxs-lookup"><span data-stu-id="f9c57-144">The interior of the polygon is connected using the left-hand rule.</span></span>  
  
2.  <span data-ttu-id="f9c57-145">环不能与自身或其他环交叉。</span><span class="sxs-lookup"><span data-stu-id="f9c57-145">No ring can cross itself or another ring.</span></span>  
  
3.  <span data-ttu-id="f9c57-146">环只能在单个切点处接触（环接触的点数必须有限）。</span><span class="sxs-lookup"><span data-stu-id="f9c57-146">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
4.  <span data-ttu-id="f9c57-147">多边形的内部必须连接。</span><span class="sxs-lookup"><span data-stu-id="f9c57-147">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="f9c57-148">下面的示例显示一个有效的地理 CurvePolygon 实例。</span><span class="sxs-lookup"><span data-stu-id="f9c57-148">The following example shows a valid geography CurvePolygon instance.</span></span>  
  
```  
DECLARE @g geography = 'CURVEPOLYGON((-122.3 47, 122.3 47, 125.7 49, 121 38, -122.3 47))';  
SELECT @g.STIsValid();  
```  
  
## <a name="examples"></a><span data-ttu-id="f9c57-149">示例</span><span class="sxs-lookup"><span data-stu-id="f9c57-149">Examples</span></span>  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-curvepolygon"></a><span data-ttu-id="f9c57-150">A.</span><span class="sxs-lookup"><span data-stu-id="f9c57-150">A.</span></span> <span data-ttu-id="f9c57-151">实例化具有空 CurvePolygon 的几何图形实例</span><span class="sxs-lookup"><span data-stu-id="f9c57-151">Instantiating a Geometry Instance with an Empty CurvePolygon</span></span>  
 <span data-ttu-id="f9c57-152">该示例说明如何创建一个空的 `CurvePolygon` 实例：</span><span class="sxs-lookup"><span data-stu-id="f9c57-152">This example shows how to create an empty `CurvePolygon` instance:</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-with-a-curvepolygon-in-the-same-statement"></a><span data-ttu-id="f9c57-153">B.</span><span class="sxs-lookup"><span data-stu-id="f9c57-153">B.</span></span> <span data-ttu-id="f9c57-154">在同一语句中声明和实例化一个具有 CurvePolygon 的几何图形实例</span><span class="sxs-lookup"><span data-stu-id="f9c57-154">Declaring and Instantiating a Geometry Instance with a CurvePolygon in the Same Statement</span></span>  
 <span data-ttu-id="f9c57-155">此代码段说明如何在同一语句中声明和实例化一个具有 `CurvePolygon` 的几何图形实例：</span><span class="sxs-lookup"><span data-stu-id="f9c57-155">This code snippet shows how to declare and initialize a geometry instance with a `CurvePolygon` in the same statement:</span></span>  
  
```sql  
DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))'  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-curvepolygon"></a><span data-ttu-id="f9c57-156">C.</span><span class="sxs-lookup"><span data-stu-id="f9c57-156">C.</span></span> <span data-ttu-id="f9c57-157">实例化一个具有 CurvePolygon 的几何图形实例</span><span class="sxs-lookup"><span data-stu-id="f9c57-157">Instantiating a Geography Instance with a CurvePolygon</span></span>  
 <span data-ttu-id="f9c57-158">此代码段说明如何声明和实例化一个具有 `geography` 的 `CurvePolygon` 实例：</span><span class="sxs-lookup"><span data-stu-id="f9c57-158">This code snippet shows how to declare and initialize a `geography` instance with a `CurvePolygon`:</span></span>  
  
```sql  
DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-curvepolygon-with-only-an-exterior-bounding-ring"></a><span data-ttu-id="f9c57-159">D.</span><span class="sxs-lookup"><span data-stu-id="f9c57-159">D.</span></span> <span data-ttu-id="f9c57-160">存储仅具有一个外部边界环的 CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="f9c57-160">Storing a CurvePolygon with Only an Exterior Bounding Ring</span></span>  
 <span data-ttu-id="f9c57-161">此示例说明如何在一个 `CurvePolygon` 实例中存储一个简单的圆形（仅有一个外部边界环用于界定该圆形）：</span><span class="sxs-lookup"><span data-stu-id="f9c57-161">This example shows how to store a simple circle in a `CurvePolygon` instance (only an exterior bounding ring is used to define the circle):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
### <a name="e-storing-a-curvepolygon-containing-interior-rings"></a><span data-ttu-id="f9c57-162">E.</span><span class="sxs-lookup"><span data-stu-id="f9c57-162">E.</span></span> <span data-ttu-id="f9c57-163">存储包含内环的 CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="f9c57-163">Storing a CurvePolygon Containing Interior Rings</span></span>  
 <span data-ttu-id="f9c57-164">此示例在 `CurvePolygon` 实例中创建一个圆环图（使用一个外部边界环和一个内环来界定该圆环图）：</span><span class="sxs-lookup"><span data-stu-id="f9c57-164">This example creates a donut in a `CurvePolygon` instance (both an exterior bounding ring and an interior ring is used to define the donut):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
 <span data-ttu-id="f9c57-165">此示例说明在使用内环时的一个有效的 `CurvePolygon` 实例和一个无效的实例：</span><span class="sxs-lookup"><span data-stu-id="f9c57-165">This example shows both a valid `CurvePolygon` instance and an invalid instance when using interior rings:</span></span>  
  
```sql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (-2 2, 2 2, 2 -2, -2 -2, -2 2))');  
IF @g1.STIsValid() = 1  
  BEGIN  
     SELECT @g1.STArea();  
  END  
SET @g2 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (0 5, 5 0, 0 -5, -5 0, 0 5))');  
IF @g2.STIsValid() = 1  
  BEGIN  
     SELECT @g2.STArea();  
  END  
SELECT @g1.STIsValid() AS G1, @g2.STIsValid() AS G2;  
```  
  
 <span data-ttu-id="f9c57-166">@g1 和 @g2 都使用相同的外部边界环：一个半径为 5 的圆形，并且它们都使用一个正方形作为内环。</span><span class="sxs-lookup"><span data-stu-id="f9c57-166">Both @g1 and @g2 use the same exterior bounding ring: a circle with a radius of 5 and they both use a square for an interior ring.</span></span>  <span data-ttu-id="f9c57-167">不过，实例 @g1 有效，而实例 @g2 却无效。</span><span class="sxs-lookup"><span data-stu-id="f9c57-167">However, the instance @g1 is valid, but the instance @g2 is invalid.</span></span>  <span data-ttu-id="f9c57-168">@g2 无效的原因在于内环将外环界定的内部空间拆分为四个单独的区域。</span><span class="sxs-lookup"><span data-stu-id="f9c57-168">The reason that @g2 is invalid is that the interior ring splits the interior space bounded by the exterior ring into four separate regions.</span></span>  <span data-ttu-id="f9c57-169">下图显示所发生的情况：</span><span class="sxs-lookup"><span data-stu-id="f9c57-169">The following drawing shows what occurred:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c57-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9c57-170">See Also</span></span>  
 <span data-ttu-id="f9c57-171">[Polygon](polygon.md) </span><span class="sxs-lookup"><span data-stu-id="f9c57-171">[Polygon](polygon.md) </span></span>  
 <span data-ttu-id="f9c57-172">[CircularString](circularstring.md) </span><span class="sxs-lookup"><span data-stu-id="f9c57-172">[CircularString](circularstring.md) </span></span>  
 <span data-ttu-id="f9c57-173">[CompoundCurve](compoundcurve.md) </span><span class="sxs-lookup"><span data-stu-id="f9c57-173">[CompoundCurve](compoundcurve.md) </span></span>  
 <span data-ttu-id="f9c57-174">[geometry 数据类型方法引用](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f9c57-174">[geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span></span>  
 <span data-ttu-id="f9c57-175">[geography 数据类型方法引用](/sql/t-sql/spatial-geography/spatial-types-geography) </span><span class="sxs-lookup"><span data-stu-id="f9c57-175">[geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) </span></span>  
 [<span data-ttu-id="f9c57-176">空间数据类型概述</span><span class="sxs-lookup"><span data-stu-id="f9c57-176">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
