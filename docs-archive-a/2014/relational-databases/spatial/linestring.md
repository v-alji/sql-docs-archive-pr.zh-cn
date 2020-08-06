---
title: LineString | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- LineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: e50d0b86-8b31-4285-be71-ad05c7712cbd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0f77959cfe4492eca6c38951ba2868452d41ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590672"
---
# <a name="linestring"></a><span data-ttu-id="8348f-102">LineString</span><span class="sxs-lookup"><span data-stu-id="8348f-102">LineString</span></span>
  <span data-ttu-id="8348f-103">`LineString` 是一个一维对象，表示一系列点和连接这些点的线段。</span><span class="sxs-lookup"><span data-stu-id="8348f-103">A `LineString` is a one-dimensional object representing a sequence of points and the line segments connecting them.</span></span>

## <a name="linestring-instances"></a><span data-ttu-id="8348f-104">LineString 实例</span><span class="sxs-lookup"><span data-stu-id="8348f-104">LineString Instances</span></span>
 <span data-ttu-id="8348f-105">下图显示了 `LineString` 实例的示例。</span><span class="sxs-lookup"><span data-stu-id="8348f-105">The illustration below shows examples of `LineString` instances.</span></span>

 <span data-ttu-id="8348f-106">![几何 LineString 实例的示例](../../database-engine/media/linestring.gif "几何 LineString 实例的示例")</span><span class="sxs-lookup"><span data-stu-id="8348f-106">![Examples of geometry LineString instances](../../database-engine/media/linestring.gif "Examples of geometry LineString instances")</span></span>

 <span data-ttu-id="8348f-107">如图中所示：</span><span class="sxs-lookup"><span data-stu-id="8348f-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="8348f-108">图 1 显示的是一个简单、非闭合的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-108">Figure 1 is a simple, nonclosed `LineString` instance.</span></span>

-   <span data-ttu-id="8348f-109">图 2 显示的是一个不简单、非闭合的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-109">Figure 2 is a nonsimple, nonclosed `LineString` instance.</span></span>

-   <span data-ttu-id="8348f-110">图 3 显示的是一个闭合、简单的 `LineString` 实例，因此是一个环。</span><span class="sxs-lookup"><span data-stu-id="8348f-110">Figure 3 is a closed, simple `LineString` instance, and therefore is a ring.</span></span>

-   <span data-ttu-id="8348f-111">图 4 显示的是一个闭合、不简单的 `LineString` 实例，因此不是一个环。</span><span class="sxs-lookup"><span data-stu-id="8348f-111">Figure 4 is a closed, nonsimple `LineString` instance, and therefore is not a ring.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="8348f-112">已接受的实例</span><span class="sxs-lookup"><span data-stu-id="8348f-112">Accepted Instances</span></span>
 <span data-ttu-id="8348f-113">可以将已接受的 `LineString` 实例输入到一个几何图形变量中，但它们可能不是有效的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-113">Accepted `LineString` instances can be input into a geometry variable, but they may not be valid `LineString` instances.</span></span> <span data-ttu-id="8348f-114">必须满足以下条件，`LineString` 实例才能被接受。</span><span class="sxs-lookup"><span data-stu-id="8348f-114">The following criteria must be met for a `LineString` instance to be accepted.</span></span> <span data-ttu-id="8348f-115">该实例必须由至少两个点组成，或者该实例必须为空。</span><span class="sxs-lookup"><span data-stu-id="8348f-115">The instance must be formed of at least two points or it must be empty.</span></span> <span data-ttu-id="8348f-116">下面是一些已接受的 LineString 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-116">The following LineString instances are accepted.</span></span>

```
DECLARE @g1 geometry = 'LINESTRING EMPTY';
DECLARE @g2 geometry = 'LINESTRING(1 1,2 3,4 8, -6 3)';
DECLARE @g3 geometry = 'LINESTRING(1 1, 1 1)';
```

 <span data-ttu-id="8348f-117">`@g3` 显示 `LineString` 实例可被接受，但无效。</span><span class="sxs-lookup"><span data-stu-id="8348f-117">`@g3` shows that a `LineString` instance can be accepted, but not valid.</span></span>

 <span data-ttu-id="8348f-118">下面的 `LineString` 实例不可接受。</span><span class="sxs-lookup"><span data-stu-id="8348f-118">The following `LineString` instance is not accepted.</span></span> <span data-ttu-id="8348f-119">它将引发 `System.FormatException`。</span><span class="sxs-lookup"><span data-stu-id="8348f-119">It will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'LINESTRING(1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="8348f-120">有效实例</span><span class="sxs-lookup"><span data-stu-id="8348f-120">Valid Instances</span></span>
 <span data-ttu-id="8348f-121">必须满足以下条件，`LineString` 实例才是有效的。</span><span class="sxs-lookup"><span data-stu-id="8348f-121">For a `LineString` instance to be valid it must meet the following criteria.</span></span>

1.  <span data-ttu-id="8348f-122">`LineString` 实例必须是已接受的实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-122">The `LineString` instance must be accepted.</span></span>

2.  <span data-ttu-id="8348f-123">如果 `LineString` 实例不为空，则它必须包含至少两个非重复点。</span><span class="sxs-lookup"><span data-stu-id="8348f-123">If a `LineString` instance is not empty then it must contain at least two distinct points.</span></span>

3.  <span data-ttu-id="8348f-124">在两个或更多连续点的间隔范围内，`LineString` 实例不能自身重叠。</span><span class="sxs-lookup"><span data-stu-id="8348f-124">The `LineString` instance cannot overlap itself over an interval of two or more consecutive points.</span></span>

 <span data-ttu-id="8348f-125">以下是有效的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-125">The following `LineString` instances are valid.</span></span>

```
DECLARE @g1 geometry= 'LINESTRING EMPTY';
DECLARE @g2 geometry= 'LINESTRING(1 1, 3 3)';
DECLARE @g3 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0)';
DECLARE @g4 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();

```

 <span data-ttu-id="8348f-126">以下是无效的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-126">The following `LineString` instances are not valid.</span></span>

```
DECLARE @g1 geometry = 'LINESTRING(1 4, 3 4, 2 4, 2 0)';
DECLARE @g2 geometry = 'LINESTRING(1 1, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

> [!WARNING]
>  <span data-ttu-id="8348f-127">`LineString` 重叠的检测基于不精确的浮点计算。</span><span class="sxs-lookup"><span data-stu-id="8348f-127">The detection of `LineString` overlaps is based on floating-point calculations, which are not exact.</span></span>

## <a name="examples"></a><span data-ttu-id="8348f-128">示例</span><span class="sxs-lookup"><span data-stu-id="8348f-128">Examples</span></span>
 <span data-ttu-id="8348f-129">下面的示例说明如何创建一个包含三个点且 SRID 为 0 的 `geometry``LineString` 实例：</span><span class="sxs-lookup"><span data-stu-id="8348f-129">The following example shows how to create a `geometry``LineString` instance with three points and an SRID of 0:</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1, 2 4, 3 9)', 0);
```

 <span data-ttu-id="8348f-130">此 `LineString` 实例中的每个点都可以包含 Z（仰角）和 M（度量）值。</span><span class="sxs-lookup"><span data-stu-id="8348f-130">Each point in the `LineString` instance may contain Z (elevation) and M (measure) values.</span></span> <span data-ttu-id="8348f-131">下面这个示例向上例中创建的 `LineString` 实例添加了 M 值。</span><span class="sxs-lookup"><span data-stu-id="8348f-131">This example adds M values to the `LineString` instance created in the example above.</span></span> <span data-ttu-id="8348f-132">M 和 Z 可以为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8348f-132">M and Z can be null values.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1 NULL 0, 2 4 NULL 12.3, 3 9 NULL 24.5)', 0);
```

 <span data-ttu-id="8348f-133">下面的示例说明如何创建一个包含两个相同点的 `geometry LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="8348f-133">The following example shows how to create a `geometry LineString` instance with two points that are the same.</span></span> <span data-ttu-id="8348f-134">对 `IsValid` 的调用指示 `LineString` 实例无效，并且对 `MakeValid` 的调用会将 `LineString` 实例转换为 `Point`。</span><span class="sxs-lookup"><span data-stu-id="8348f-134">A call to `IsValid` indicates that the `LineString` instance is not valid and a call to `MakeValid` will convert the `LineString` instance into a `Point`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::STGeomFromText('LINESTRING(1 3, 1 3)',0);
IF @g.STIsValid() = 1
  BEGIN
     SELECT @g.ToString() + ' is a valid LineString.';  
  END
ELSE
  BEGIN
     SELECT @g.ToString() + ' is not a valid LineString.';
     SET @g = @g.MakeValid();
     SELECT @g.ToString() + ' is a valid Point.';  
  END

```

 <span data-ttu-id="8348f-135">上面的代码段将返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="8348f-135">The above code snippet will return the following:</span></span>

```
LINESTRING(1 3, 1 3) is not a valid LineString
POINT(1 3) is a valid Point.
```

## <a name="see-also"></a><span data-ttu-id="8348f-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8348f-136">See Also</span></span>
 <span data-ttu-id="8348f-137">[STLength &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry 数据类型](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)&#41;[STIsClosed &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [空间数据 &#40;SQL Server](../spatial/spatial-data-sql-server.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="8348f-137">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


