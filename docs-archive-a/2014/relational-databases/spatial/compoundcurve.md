---
title: CompoundCurve | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6a899bbe9a17a64083592e1078e8cac93365f02b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578055"
---
# <a name="compoundcurve"></a><span data-ttu-id="90163-102">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="90163-102">CompoundCurve</span></span>
  <span data-ttu-id="90163-103">`CompoundCurve` 是几何图形或地域类型的零个或多个连续 `CircularString` 或 `LineString` 实例的集合。</span><span class="sxs-lookup"><span data-stu-id="90163-103">A `CompoundCurve` is a collection of zero or more continuous `CircularString` or `LineString` instances of either geometry or geography types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="90163-104">有关此版本中新的空间功能的详细说明和示例（包括 `CompoundCurve` 子类型），请下载白皮书[SQL Server 2012 中的新的空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="90163-104">For a detailed description and examples of the new spatial features in this release, including the `CompoundCurve` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

 <span data-ttu-id="90163-105">可以实例化空的 `CompoundCurve` 实例，但要使 `CompoundCurve` 有效，它必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="90163-105">An empty `CompoundCurve` instance can be instantiated, but for a `CompoundCurve` to be valid it must meet the following criteria:</span></span>

1.  <span data-ttu-id="90163-106">它必须至少包含一个 `CircularString` 或 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-106">It must contain at least one `CircularString` or `LineString` instance.</span></span>

2.  <span data-ttu-id="90163-107">`CircularString` 或 `LineString` 实例的序列必须是连续的。</span><span class="sxs-lookup"><span data-stu-id="90163-107">The sequence of `CircularString` or `LineString` instances must be continuous.</span></span>

 <span data-ttu-id="90163-108">如果 `CompoundCurve` 包含多个 `CircularString` 和实例的序列 `LineString` ，则每个实例（最后一个实例除外）的结束终结点都必须是序列中下一个实例的起始终结点。</span><span class="sxs-lookup"><span data-stu-id="90163-108">If a `CompoundCurve` contains a sequence of multiple `CircularString` and `LineString` instances, the ending endpoint for every instance except for the last instance must be the starting endpoint for the next instance in the sequence.</span></span> <span data-ttu-id="90163-109">这意味着，如果在序列中前一个实例的结束点是 (4 3 7 2)，则该序列中的下一个实例的起始点必须是 (4 3 7 2)。</span><span class="sxs-lookup"><span data-stu-id="90163-109">This means that if the ending point of a prior instance in the sequence is (4 3 7 2), the starting point for the next instance in the sequence must be (4 3 7 2).</span></span> <span data-ttu-id="90163-110">请注意，该点的 Z（标高）和 M（度量）值也必须相同。</span><span class="sxs-lookup"><span data-stu-id="90163-110">Note that Z(elevation) and M(measure) values for the point must also be the same.</span></span> <span data-ttu-id="90163-111">如果这两个点之间存在差异，则将引发 `System.FormatException` 。</span><span class="sxs-lookup"><span data-stu-id="90163-111">If there is a difference in the two points, a `System.FormatException` is thrown.</span></span> <span data-ttu-id="90163-112">`CircularString` 中的点不一定必须有 Z 值或 M 值。</span><span class="sxs-lookup"><span data-stu-id="90163-112">Points in a `CircularString` do not have to have a Z or M value.</span></span> <span data-ttu-id="90163-113">如果未向前一个实例的结束点提供 Z 值或 M 值，下一个实例的起始点就不能包含 Z 值或 M 值。</span><span class="sxs-lookup"><span data-stu-id="90163-113">If no Z or M values are given for the ending point of the prior instance, the starting point of the next instance cannot include Z or M values.</span></span> <span data-ttu-id="90163-114">如果前一个序列的结束点是 (4 3)，则后一个序列的起始点必须是 (4 3)；它不能是 (4 3 7 2）。</span><span class="sxs-lookup"><span data-stu-id="90163-114">If the ending point for the prior sequence is (4 3), the starting point for the next sequence must be (4 3); it cannot be (4 3 7 2).</span></span> <span data-ttu-id="90163-115">`CompoundCurve` 实例中的所有点要么不得有 Z 值，要么其 Z 值必须相同。</span><span class="sxs-lookup"><span data-stu-id="90163-115">All points in a `CompoundCurve` instance must have either no Z value or the same Z value.</span></span>

## <a name="compoundcurve-instances"></a><span data-ttu-id="90163-116">CompoundCurve 实例</span><span class="sxs-lookup"><span data-stu-id="90163-116">CompoundCurve instances</span></span>
 <span data-ttu-id="90163-117">下图显示了有效的 `CompoundCurve` 类型。</span><span class="sxs-lookup"><span data-stu-id="90163-117">The following illustration shows valid `CompoundCurve` types.</span></span>

 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")

### <a name="accepted-instances"></a><span data-ttu-id="90163-118">接受的实例</span><span class="sxs-lookup"><span data-stu-id="90163-118">Accepted instances</span></span>
 <span data-ttu-id="90163-119">如果 `CompoundCurve` 实例是空实例或者它满足以下条件，则接受该实例。</span><span class="sxs-lookup"><span data-stu-id="90163-119">`CompoundCurve` instance is accepted if it is an empty instance or meets the following criteria.</span></span>

1.  <span data-ttu-id="90163-120">`CompoundCurve` 实例包含的所有实例都是接受的圆弧线段实例。</span><span class="sxs-lookup"><span data-stu-id="90163-120">All the instances contained by `CompoundCurve` instance are accepted circular arc segment instances.</span></span> <span data-ttu-id="90163-121">有关接受的圆弧线段实例的详细信息，请参阅 [LineString](linestring.md) 和 [CircularString](circularstring.md)。</span><span class="sxs-lookup"><span data-stu-id="90163-121">For more information on accepted circular arc segment instances, see [LineString](linestring.md) and [CircularString](circularstring.md).</span></span>

2.  <span data-ttu-id="90163-122">`CompoundCurve` 实例中的所有圆弧线段都连接在一起。</span><span class="sxs-lookup"><span data-stu-id="90163-122">All of the circular arc segments in the `CompoundCurve` instance are connected.</span></span> <span data-ttu-id="90163-123">每个后续圆弧线段上的第一个点与前一个圆弧线段上的最后一个点相同。</span><span class="sxs-lookup"><span data-stu-id="90163-123">The first point for each succeeding circular arc segment is the same as the last point on the preceding circular arc segment.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="90163-124">Z 和 M 坐标也要相同。</span><span class="sxs-lookup"><span data-stu-id="90163-124">This includes the Z and M coordinates.</span></span> <span data-ttu-id="90163-125">因此，所有四个坐标 X、Y、Z 和 M 必须相同。</span><span class="sxs-lookup"><span data-stu-id="90163-125">So, all four coordinates X, Y, Z, and M must be the same.</span></span>

3.  <span data-ttu-id="90163-126">所有包含的实例都不是空实例。</span><span class="sxs-lookup"><span data-stu-id="90163-126">None of the contained instances are empty instances.</span></span>

 <span data-ttu-id="90163-127">下面的示例显示接受的 `CompoundCurve` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-127">The following example shows accepted `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
```

 <span data-ttu-id="90163-128">下面的示例显示未被接受的 `CompoundCurve` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-128">The following example shows `CompoundCurve` instances that are not accepted.</span></span> <span data-ttu-id="90163-129">这些实例引发 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="90163-129">These instances throw `System.FormatException`.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="90163-130">有效实例</span><span class="sxs-lookup"><span data-stu-id="90163-130">Valid instances</span></span>
 <span data-ttu-id="90163-131">如果满足以下条件，则 `CompoundCurve` 实例有效。</span><span class="sxs-lookup"><span data-stu-id="90163-131">A `CompoundCurve` instance is valid if it meets the following criteria.</span></span>

1.  <span data-ttu-id="90163-132">`CompoundCurve` 实例是接受的实例。</span><span class="sxs-lookup"><span data-stu-id="90163-132">The `CompoundCurve` instance is accepted.</span></span>

2.  <span data-ttu-id="90163-133">`CompoundCurve` 实例包含的所有圆弧线段实例都是有效实例。</span><span class="sxs-lookup"><span data-stu-id="90163-133">All circular arc segment instances contained by the `CompoundCurve` instance are valid instances.</span></span>

 <span data-ttu-id="90163-134">下面的示例显示有效的 `CompoundCurve` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-134">The following example shows valid `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();

```

 <span data-ttu-id="90163-135">`@g3` 有效，因为 `CircularString` 实例有效。</span><span class="sxs-lookup"><span data-stu-id="90163-135">`@g3` is valid because the `CircularString` instance is valid.</span></span> <span data-ttu-id="90163-136">有关实例的有效性的详细信息 `CircularString` ，请参阅[CircularString](circularstring.md)。</span><span class="sxs-lookup"><span data-stu-id="90163-136">For more information on the validity of the `CircularString` instance, see [CircularString](circularstring.md).</span></span>

 <span data-ttu-id="90163-137">下面的示例显示无效的 `CompoundCurve` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-137">The following example shows `CompoundCurve` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="90163-138">`@g1` 无效，因为第二个实例是无效的 LineString 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-138">`@g1` is not valid because the second instance is not a valid LineString instance.</span></span> <span data-ttu-id="90163-139">`@g2` 无效，因为 `LineString` 实例无效。</span><span class="sxs-lookup"><span data-stu-id="90163-139">`@g2` is not valid because the `LineString` instance is not valid.</span></span> <span data-ttu-id="90163-140">`@g3` 无效，因为 `CircularString` 实例无效。</span><span class="sxs-lookup"><span data-stu-id="90163-140">`@g3` is not valid because the `CircularString` instance is not valid.</span></span> <span data-ttu-id="90163-141">有关有效和实例的详细信息 `CircularString` `LineString` ，请参阅[CircularString](circularstring.md)和[LineString](linestring.md)。</span><span class="sxs-lookup"><span data-stu-id="90163-141">For more information on valid `CircularString` and `LineString` instances, see [CircularString](circularstring.md) and [LineString](linestring.md).</span></span>

## <a name="examples"></a><span data-ttu-id="90163-142">示例</span><span class="sxs-lookup"><span data-stu-id="90163-142">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a><span data-ttu-id="90163-143">A.</span><span class="sxs-lookup"><span data-stu-id="90163-143">A.</span></span> <span data-ttu-id="90163-144">使用空的 CompoundCurve 实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="90163-144">Instantiating a geometry instance with an empty CompooundCurve</span></span>
 <span data-ttu-id="90163-145">下面的示例演示如何创建空的 `CompoundCurve` 实例：</span><span class="sxs-lookup"><span data-stu-id="90163-145">The following example shows how to create an empty `CompoundCurve` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');
```

### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a><span data-ttu-id="90163-146">B.</span><span class="sxs-lookup"><span data-stu-id="90163-146">B.</span></span> <span data-ttu-id="90163-147">在同一语句中使用 CompoundCurve 声明和实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="90163-147">Declaring and instantiating a geometry instance using a CompoundCurve in the same statement</span></span>
 <span data-ttu-id="90163-148">下面的示例演示如何在同一语句中使用 `geometry` 声明和初始化 `CompoundCurve`实例：</span><span class="sxs-lookup"><span data-stu-id="90163-148">The following example shows how to declare and initialize a `geometry` instance with a `CompoundCurve`in the same statement:</span></span>

```sql
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';
```

### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a><span data-ttu-id="90163-149">C.</span><span class="sxs-lookup"><span data-stu-id="90163-149">C.</span></span> <span data-ttu-id="90163-150">使用 CompoundCurve 实例化一个地域实例</span><span class="sxs-lookup"><span data-stu-id="90163-150">Instantiating a geography instance with a CompoundCurve</span></span>
 <span data-ttu-id="90163-151">下面的示例演示如何使用 `CompoundCurve` 声明和初始化 `geography` 实例：</span><span class="sxs-lookup"><span data-stu-id="90163-151">The following example shows how to declare and initialize a `geography` instance with a `CompoundCurve`:</span></span>

```sql
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';
```

### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a><span data-ttu-id="90163-152">D.</span><span class="sxs-lookup"><span data-stu-id="90163-152">D.</span></span> <span data-ttu-id="90163-153">将一个正方形存储在 CompoundCurve 实例中</span><span class="sxs-lookup"><span data-stu-id="90163-153">Storing a square in a CompoundCurve instance</span></span>
 <span data-ttu-id="90163-154">下面的示例通过两种不同方式使用 `CompoundCurve` 实例存储一个正方形。</span><span class="sxs-lookup"><span data-stu-id="90163-154">The following example uses two different ways to use a `CompoundCurve` instance to store a square.</span></span>

```sql
DECLARE @g1 geometry, @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');
SELECT @g1.STLength(), @g2.STLength();
```

 <span data-ttu-id="90163-155">`@g1` 和 `@g2` 的长度相同。</span><span class="sxs-lookup"><span data-stu-id="90163-155">The lengths for both `@g1` and `@g2` are the same.</span></span> <span data-ttu-id="90163-156">请注意，在该示例中 `CompoundCurve` 实例可以存储一个或多个 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-156">Notice from the example that a `CompoundCurve` instance can store one or more instances of `LineString`.</span></span>

### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a><span data-ttu-id="90163-157">E.</span><span class="sxs-lookup"><span data-stu-id="90163-157">E.</span></span> <span data-ttu-id="90163-158">使用包含多个 CircularString 的 CompoundCurve 实例化一个几何图形实例</span><span class="sxs-lookup"><span data-stu-id="90163-158">Instantiating a geometry instance using a CompoundCurve with multiple CircularStrings</span></span>
 <span data-ttu-id="90163-159">下面的示例演示如何使用两个不同的 `CircularString` 实例初始化 `CompoundCurve`。</span><span class="sxs-lookup"><span data-stu-id="90163-159">The following example shows how to use two different `CircularString` instances to initialize a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT @g.STLength();
```

 <span data-ttu-id="90163-160">这将生成以下输出： 12.566370 .。。这等效于 4&#x03c0; (4 \* pi) 。</span><span class="sxs-lookup"><span data-stu-id="90163-160">This produces the following output: 12.566370... which is the equivalent of 4&#x03c0; (4 \* pi).</span></span> <span data-ttu-id="90163-161">该示例中的 `CompoundCurve` 实例存储一个半径为 2 的圆。</span><span class="sxs-lookup"><span data-stu-id="90163-161">The `CompoundCurve` instance in the example stores a circle with a radius of 2.</span></span> <span data-ttu-id="90163-162">前面的两个代码示例不一定非要使用 `CompoundCurve`。</span><span class="sxs-lookup"><span data-stu-id="90163-162">Both of the previous code examples did not have to use a `CompoundCurve`.</span></span> <span data-ttu-id="90163-163">对于第一个示例， `LineString` 实例将更为简单，对于第二个示例， `CircularString` 实例将更为简单。</span><span class="sxs-lookup"><span data-stu-id="90163-163">For the first example a `LineString` instance would have been simpler, and a `CircularString` instance would have been simpler for the second example.</span></span> <span data-ttu-id="90163-164">然而，下一个示例显示在何种情况下 `CompoundCurve` 提供更好的替代方法。</span><span class="sxs-lookup"><span data-stu-id="90163-164">However, the next example shows where a `CompoundCurve` provides a better alternative.</span></span>

### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a><span data-ttu-id="90163-165">F.</span><span class="sxs-lookup"><span data-stu-id="90163-165">F.</span></span> <span data-ttu-id="90163-166">使用 CompoundCurve 存储一个半圆</span><span class="sxs-lookup"><span data-stu-id="90163-166">Using a CompoundCurve to store a semicircle</span></span>
 <span data-ttu-id="90163-167">下面的示例使用 `CompoundCurve` 实例存储一个半圆。</span><span class="sxs-lookup"><span data-stu-id="90163-167">The following example uses a `CompoundCurve` instance to store a semicircle.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');
SELECT @g.STLength();
```

### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a><span data-ttu-id="90163-168">G.</span><span class="sxs-lookup"><span data-stu-id="90163-168">G.</span></span> <span data-ttu-id="90163-169">将多个 CircularString 和 LineString 实例存储在一个 CompoundCurve 中</span><span class="sxs-lookup"><span data-stu-id="90163-169">Storing multiple CircularString and LineString instances in a CompoundCurve</span></span>
 <span data-ttu-id="90163-170">下面的示例演示如何使用 `CircularString` 存储多个 `LineString` 和 `CompoundCurve`实例。</span><span class="sxs-lookup"><span data-stu-id="90163-170">The following example shows how multiple `CircularString` and `LineString` instances can be stored by using a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');
SELECT @g.STLength();
```

### <a name="h-storing-instances-with-z-and-m-values"></a><span data-ttu-id="90163-171">H.</span><span class="sxs-lookup"><span data-stu-id="90163-171">H.</span></span> <span data-ttu-id="90163-172">存储具有 Z 值和 M 值的实例</span><span class="sxs-lookup"><span data-stu-id="90163-172">Storing instances with Z and M values</span></span>
 <span data-ttu-id="90163-173">下面的示例演示如何使用 `CompoundCurve` 实例存储具有 Z 值和 M 值的 `CircularString` 和 `LineString` 实例的序列。</span><span class="sxs-lookup"><span data-stu-id="90163-173">The following example shows how to use a `CompoundCurve` instance to store a sequence of `CircularString` and `LineString` instances with both Z and M values.</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');
```

### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a><span data-ttu-id="90163-174">I.</span><span class="sxs-lookup"><span data-stu-id="90163-174">I.</span></span> <span data-ttu-id="90163-175">说明为什么必须显式声明 CircularString 实例</span><span class="sxs-lookup"><span data-stu-id="90163-175">Illustrating why CircularString instances must be explicitly declared</span></span>
 <span data-ttu-id="90163-176">下面的示例说明了为什么必须显式声明 `CircularString` 实例。</span><span class="sxs-lookup"><span data-stu-id="90163-176">The following example shows why `CircularString` instances must be explicitly declared.</span></span> <span data-ttu-id="90163-177">程序员试图将一个圆形存储在 `CompoundCurve` 实例中。</span><span class="sxs-lookup"><span data-stu-id="90163-177">The programmer is trying to store a circle in a `CompoundCurve` instance.</span></span>

```sql
DECLARE @g1 geometry;  
DECLARE @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount
```

 <span data-ttu-id="90163-178">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="90163-178">The output is as follows:</span></span>

```
Circle One11.940039...
Circle Two12.566370...
```

 <span data-ttu-id="90163-179">圆圈2的周长大约为 4&#x03c0; (4 \* pi) ，这是周长的实际值。</span><span class="sxs-lookup"><span data-stu-id="90163-179">The perimeter for Circle Two is approximately 4&#x03c0; (4 \* pi), which is the actual value for the perimeter.</span></span> <span data-ttu-id="90163-180">但是，圆形 1 的周长很不准确。</span><span class="sxs-lookup"><span data-stu-id="90163-180">However, the perimeter for Circle One is significantly inaccurate.</span></span> <span data-ttu-id="90163-181">圆形 1 的 `CompoundCurve` 实例存储一个圆弧线段 (ABC) 和两条直线段（CD、DA)。</span><span class="sxs-lookup"><span data-stu-id="90163-181">Circle One's `CompoundCurve` instance stores one circular arc segment (ABC) and two line segments (CD, DA).</span></span> <span data-ttu-id="90163-182">`CompoundCurve` 实例必须存储两个圆弧线段（ABC、CDA）才可以定义一个圆形。</span><span class="sxs-lookup"><span data-stu-id="90163-182">The `CompoundCurve` instance has to store two circular arc segments (ABC, CDA) to define a circle.</span></span> <span data-ttu-id="90163-183">`LineString` 实例定义圆形 1 的 `CompoundCurve` 实例中的第二组点（4 2、2 4、0 2）。</span><span class="sxs-lookup"><span data-stu-id="90163-183">A `LineString` instance defines the second set of points (4 2, 2 4, 0 2) in Circle One's `CompoundCurve` instance.</span></span> <span data-ttu-id="90163-184">必须在 `CircularString` 内部显式声明 `CompoundCurve`实例。</span><span class="sxs-lookup"><span data-stu-id="90163-184">You have to explicitly declare a `CircularString` instance inside a `CompoundCurve`.</span></span>

## <a name="see-also"></a><span data-ttu-id="90163-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90163-185">See Also</span></span>
 <span data-ttu-id="90163-186">[STIsValid &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STLength &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)数据类型&#41;[STEndpoint &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [LineString](linestring.md) [CircularString](circularstring.md) [空间数据类型概述](spatial-data-types-overview.md)[点](point.md)</span><span class="sxs-lookup"><span data-stu-id="90163-186">[STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [LineString](linestring.md) [CircularString](circularstring.md) [Spatial Data Types Overview](spatial-data-types-overview.md) [Point](point.md)</span></span>


