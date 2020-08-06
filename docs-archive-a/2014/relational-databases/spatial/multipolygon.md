---
title: MultiPolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f18fd2485c9b2e62586d9f3e81f76f6cf680dbfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590660"
---
# <a name="multipolygon"></a><span data-ttu-id="fa021-102">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="fa021-102">MultiPolygon</span></span>
  <span data-ttu-id="fa021-103">`MultiPolygon` 实例是零个或更多个 `Polygon` 实例的集合。</span><span class="sxs-lookup"><span data-stu-id="fa021-103">A `MultiPolygon` instance is a collection of zero or more `Polygon` instances.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="fa021-104">Polygon 实例</span><span class="sxs-lookup"><span data-stu-id="fa021-104">Polygon Instances</span></span>
 <span data-ttu-id="fa021-105">下图显示了 `MultiPolygon` 实例的示例。</span><span class="sxs-lookup"><span data-stu-id="fa021-105">The illustration below shows examples of `MultiPolygon` instances.</span></span>

 <span data-ttu-id="fa021-106">![几何 MultiPolygon 实例的示例](../../database-engine/media/multipolygon.gif "几何 MultiPolygon 实例的示例")</span><span class="sxs-lookup"><span data-stu-id="fa021-106">![Examples of geometry MultiPolygon instances](../../database-engine/media/multipolygon.gif "Examples of geometry MultiPolygon instances")</span></span>

 <span data-ttu-id="fa021-107">如图中所示：</span><span class="sxs-lookup"><span data-stu-id="fa021-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="fa021-108">图 1 是一个包含两个 `Polygon` 元素的 `MultiPolygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-108">Figure 1 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="fa021-109">边界由两个外环和三个内环界定。</span><span class="sxs-lookup"><span data-stu-id="fa021-109">The boundary is defined by the two exterior rings and the three interior rings.</span></span>

-   <span data-ttu-id="fa021-110">图 2 是一个包含两个 `MultiPolygon` 元素的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-110">Figure 2 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="fa021-111">边界由两个外环和三个内环界定。</span><span class="sxs-lookup"><span data-stu-id="fa021-111">The boundary is defined by the two exterior rings and the three interior rings.</span></span> <span data-ttu-id="fa021-112">这两个 `Polygon` 元素在切点处相交。</span><span class="sxs-lookup"><span data-stu-id="fa021-112">The two `Polygon` elements intersect at a tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="fa021-113">已接受的实例</span><span class="sxs-lookup"><span data-stu-id="fa021-113">Accepted Instances</span></span>
 <span data-ttu-id="fa021-114">当满足以下条件之一时，接受 `MultiPolygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-114">A `MultiPolygon` instance is accepted one of the following conditions is met.</span></span>

-   <span data-ttu-id="fa021-115">它是空的 `MultiPolygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-115">It is an empty `MultiPolygon` instance.</span></span>

-   <span data-ttu-id="fa021-116">组成 `MultiPolygon` 实例的所有实例是接受的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-116">All instances comprising the `MultiPolygon` instance are accepted `Polygon` instances.</span></span> <span data-ttu-id="fa021-117">有关接受的实例的详细信息 `Polygon` ，请参阅[多边形](../spatial/polygon.md)。</span><span class="sxs-lookup"><span data-stu-id="fa021-117">For more information on accepted `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

 <span data-ttu-id="fa021-118">下面的示例显示接受 `MultiPolygon` 的实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-118">The following examples show accepted `MultiPolygon` instances.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
```

 <span data-ttu-id="fa021-119">下面的示例显示一个将引发 `System.FormatException`的 MultiPolygon 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-119">The following example shows a MultiPolygon instance that will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';
```

 <span data-ttu-id="fa021-120">MultiPolygon 中的第二个实例是 LineString 实例，而不是接受的 Polygon 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-120">The second instance in the MultiPolygon is a LineString instance and not an accepted Polygon instance.</span></span>

### <a name="valid-instances"></a><span data-ttu-id="fa021-121">有效实例</span><span class="sxs-lookup"><span data-stu-id="fa021-121">Valid Instances</span></span>
 <span data-ttu-id="fa021-122">如果 `MultiPolygon` 实例是空的 `MultiPolygon` 实例或者它满足以下条件，则前者有效。</span><span class="sxs-lookup"><span data-stu-id="fa021-122">A `MultiPolygon` instance is valid if it is an empty `MultiPolygon` instance or if it meets the following criteria.</span></span>

1.  <span data-ttu-id="fa021-123">组成 `MultiPolygon` 实例的所有实例是有效的 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-123">All of the instances comprising the `MultiPolygon` instance are valid `Polygon` instances.</span></span> <span data-ttu-id="fa021-124">有关有效的 `Polygon` 实例，请参阅[多边形](../spatial/polygon.md)。</span><span class="sxs-lookup"><span data-stu-id="fa021-124">For valid `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

2.  <span data-ttu-id="fa021-125">组成 `Polygon` 实例的所有 `MultiPolygon` 实例都不会重叠。</span><span class="sxs-lookup"><span data-stu-id="fa021-125">None of the `Polygon` instances comprising the `MultiPolygon` instance overlap.</span></span>

 <span data-ttu-id="fa021-126">以下示例显示两个有效的 `MultiPolygon` 实例和一个无效的 `MultiPolygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-126">The following example shows two valid `MultiPolygon` instances and one invalid `MultiPolygon` instance.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="fa021-127">`@g2` 之所以有效，原因在于两个 `Polygon` 实例仅在切点接触。</span><span class="sxs-lookup"><span data-stu-id="fa021-127">`@g2` is valid because the two `Polygon` instances touch only at a tangent point.</span></span> <span data-ttu-id="fa021-128">`@g3` 之所以无效，原因在于这两个  `Polygon` 实例的内部相互重叠。</span><span class="sxs-lookup"><span data-stu-id="fa021-128">`@g3` is not valid because the interiors of the two `Polygon` instances overlap each other.</span></span>

## <a name="examples"></a><span data-ttu-id="fa021-129">示例</span><span class="sxs-lookup"><span data-stu-id="fa021-129">Examples</span></span>
 <span data-ttu-id="fa021-130">下面的示例演示如何创建 `geometry``MultiPolygon` 实例，并返回第二个组件的熟知文本 (WKT)。</span><span class="sxs-lookup"><span data-stu-id="fa021-130">The following example shows the creation of a `geometry``MultiPolygon` instance and returns the Well-Known Text (WKT) of the second component.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');
SELECT @g.STGeometryN(2).STAsText();
```

 <span data-ttu-id="fa021-131">该示例实例化一个空的 `MultiPolygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="fa021-131">This example instantiates an empty `MultiPolygon` instance.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');
```

## <a name="see-also"></a><span data-ttu-id="fa021-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa021-132">See Also</span></span>
 <span data-ttu-id="fa021-133">[多边形](../spatial/polygon.md) [STArea &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [空间数据 &#40;SQL Server](../spatial/spatial-data-sql-server.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="fa021-133">[Polygon](../spatial/polygon.md) [STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


