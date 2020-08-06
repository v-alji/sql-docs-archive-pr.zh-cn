---
title: MultiLineString | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fdd093d99d055df8e15fc22e3e570e6805e35d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590664"
---
# <a name="multilinestring"></a><span data-ttu-id="af5e3-102">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="af5e3-102">MultiLineString</span></span>
  <span data-ttu-id="af5e3-103">`MultiLineString`是零个或多个 `geometry` 实例或**geographyLineString**实例的集合。</span><span class="sxs-lookup"><span data-stu-id="af5e3-103">A `MultiLineString` is a collection of zero or more `geometry` or **geographyLineString** instances.</span></span>  
  
## <a name="multilinestring-instances"></a><span data-ttu-id="af5e3-104">MultiLineString 实例</span><span class="sxs-lookup"><span data-stu-id="af5e3-104">MultiLineString instances</span></span>  
 <span data-ttu-id="af5e3-105">下图显示了 `MultiLineString` 实例的示例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-105">The illustration below shows examples of `MultiLineString` instances.</span></span>  
  
 <span data-ttu-id="af5e3-106">![几何 MultiLineString 实例的示例](../../database-engine/media/multilinestring.gif "几何 MultiLineString 实例的示例")</span><span class="sxs-lookup"><span data-stu-id="af5e3-106">![Examples of geometry MultiLineString instances](../../database-engine/media/multilinestring.gif "Examples of geometry MultiLineString instances")</span></span>  
  
 <span data-ttu-id="af5e3-107">如图中所示：</span><span class="sxs-lookup"><span data-stu-id="af5e3-107">As shown in the illustration:</span></span>  
  
-   <span data-ttu-id="af5e3-108">图1是一个简单的 `MultiLineString` 实例，其边界是其两个元素的四个终结点 `LineString` 。</span><span class="sxs-lookup"><span data-stu-id="af5e3-108">Figure 1 is a simple `MultiLineString` instance whose boundary is the four endpoints of its two `LineString` elements.</span></span>  
  
-   <span data-ttu-id="af5e3-109">图 2 显示的是一个简单的 `MultiLineString` 实例，因为只有 `LineString` 元素的端点相交。</span><span class="sxs-lookup"><span data-stu-id="af5e3-109">Figure 2 is a simple `MultiLineString` instance because only the endpoints of the `LineString` elements intersect.</span></span> <span data-ttu-id="af5e3-110">边界是两个不重叠的端点。</span><span class="sxs-lookup"><span data-stu-id="af5e3-110">The boundary is the two non-overlapping endpoints.</span></span>  
  
-   <span data-ttu-id="af5e3-111">图 3 显示的是一个不简单的 `MultiLineString` 实例，因为它的其中一个 `LineString` 元素的内部出现了相交。</span><span class="sxs-lookup"><span data-stu-id="af5e3-111">Figure 3 is a nonsimple `MultiLineString` instance because the interior of one of its `LineString` elements is intersected.</span></span> <span data-ttu-id="af5e3-112">此 `MultiLineString` 实例的边界是四个端点。</span><span class="sxs-lookup"><span data-stu-id="af5e3-112">The boundary of this `MultiLineString` instance is the four endpoints.</span></span>  
  
-   <span data-ttu-id="af5e3-113">图 4 显示的是一个不简单、非闭合的 `MultiLineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-113">Figure 4 is a nonsimple, nonclosed `MultiLineString` instance.</span></span>  
  
-   <span data-ttu-id="af5e3-114">图 5 显示的是一个简单、非闭合的 `MultiLineString`。</span><span class="sxs-lookup"><span data-stu-id="af5e3-114">Figure 5 is a simple, nonclosed `MultiLineString`.</span></span> <span data-ttu-id="af5e3-115">它不会关闭，因为它的 `LineStrings` 元素未关闭。</span><span class="sxs-lookup"><span data-stu-id="af5e3-115">It is not closed because its `LineStrings` elements are not closed.</span></span> <span data-ttu-id="af5e3-116">而其简单的原因在于，其任何 `LineStrings` 实例的内部都没有出现相交。</span><span class="sxs-lookup"><span data-stu-id="af5e3-116">It is simple because none of the interiors of any of the `LineStrings` instances intersect.</span></span>  
  
-   <span data-ttu-id="af5e3-117">图 6 显示的是一个简单、闭合的 `MultiLineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-117">Figure 6 is a simple, closed `MultiLineString` instance.</span></span> <span data-ttu-id="af5e3-118">它为闭合的是因为它的所有元素都是闭合的。</span><span class="sxs-lookup"><span data-stu-id="af5e3-118">It is closed because all its elements are closed.</span></span> <span data-ttu-id="af5e3-119">而其简单的原因在于，其所有元素都没有出现内部相交现象。</span><span class="sxs-lookup"><span data-stu-id="af5e3-119">It is simple because none of its elements intersect at the interiors.</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="af5e3-120">接受的实例</span><span class="sxs-lookup"><span data-stu-id="af5e3-120">Accepted instances</span></span>  
 <span data-ttu-id="af5e3-121">为使 `MultiLineString` 实例可接受，它必须或者为空，或者仅由接受的 `LineString` 实例组成。</span><span class="sxs-lookup"><span data-stu-id="af5e3-121">For a `MultiLineString` instance to be accepted it must either be empty or comprised of only `LineString` intances that are accepted.</span></span> <span data-ttu-id="af5e3-122">有关接受的实例的详细信息 `LineString` ，请参阅[LineString](../spatial/linestring.md)。</span><span class="sxs-lookup"><span data-stu-id="af5e3-122">For more information on accepted `LineString` instances, see [LineString](../spatial/linestring.md).</span></span> <span data-ttu-id="af5e3-123">下面的示例显示接受的 `MultiLineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-123">The following are examples of accepted `MultiLineString` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 <span data-ttu-id="af5e3-124">下面的示例引发 `System.FormatException`，因为第二个 `LineString` 实例无效。</span><span class="sxs-lookup"><span data-stu-id="af5e3-124">The following example throws a `System.FormatException` because the second `LineString` instance is not valid.</span></span>  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="af5e3-125">有效实例</span><span class="sxs-lookup"><span data-stu-id="af5e3-125">Valid instances</span></span>  
 <span data-ttu-id="af5e3-126">必须满足以下条件，`MultiLineString` 实例才是有效的：</span><span class="sxs-lookup"><span data-stu-id="af5e3-126">For a `MultiLineString` instance to be valid it must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="af5e3-127">组成 `MultiLineString` 实例的所有实例必须是有效的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-127">All instances comprising the `MultiLineString` instance must be valid `LineString` instances.</span></span>  
  
2.  <span data-ttu-id="af5e3-128">组成 `LineString` 实例的任何两个 `MultiLineString` 实例在某个间隔内都不会重叠。</span><span class="sxs-lookup"><span data-stu-id="af5e3-128">No two `LineString` instances comprising the `MultiLineString` instance may overlap over an interval.</span></span> <span data-ttu-id="af5e3-129">`LineString` 实例只能与其自身或其他 `LineString` 实例在有限数量的点相交或接触。</span><span class="sxs-lookup"><span data-stu-id="af5e3-129">The `LineString` instances can only intersect or touch themselves or other `LineString` instances at a finite number of points.</span></span>  
  
 <span data-ttu-id="af5e3-130">以下示例显示三个有效的 `MultiLineString` 实例和一个无效的 `MultiLineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-130">The following example shows three valid `MultiLineString` instances and one `MultiLineString` instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="af5e3-131">`@g4` 无效，因为第二个 `LineString` 实例与第一个 `LineString` 实例在某个间隔重叠。</span><span class="sxs-lookup"><span data-stu-id="af5e3-131">`@g4` is not valid because the second `LineString` instance overlaps the first `LineString` instance at an interval.</span></span> <span data-ttu-id="af5e3-132">它们在无限数量的点处接触。</span><span class="sxs-lookup"><span data-stu-id="af5e3-132">They touch at an infinite number of points.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="af5e3-133">示例</span><span class="sxs-lookup"><span data-stu-id="af5e3-133">Examples</span></span>  
 <span data-ttu-id="af5e3-134">下面的示例创建了一个包含两个 `geometry``MultiLineString` 元素且 SRID 为 0 的简单 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="af5e3-134">The following example creates a simple `geometry``MultiLineString` instance containing two `LineString` elements with the SRID 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 <span data-ttu-id="af5e3-135">若要使用不同的 SRID 实例化此实例，请使用 `STGeomFromText()` 或 `STMLineStringFromText()`。</span><span class="sxs-lookup"><span data-stu-id="af5e3-135">To instantiate this instance with a different SRID, use `STGeomFromText()` or `STMLineStringFromText()`.</span></span> <span data-ttu-id="af5e3-136">也可以使用 `Parse()` ，然后修改 SRID，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="af5e3-136">You can also use `Parse()` and then modify the SRID, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a><span data-ttu-id="af5e3-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af5e3-137">See Also</span></span>  
 <span data-ttu-id="af5e3-138">[STLength（geometry 数据类型）](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="af5e3-138">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span></span>  
 <span data-ttu-id="af5e3-139">[STIsClosed（geometry 数据类型）](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="af5e3-139">[STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span></span>  
 <span data-ttu-id="af5e3-140">[LineString](../spatial/linestring.md) </span><span class="sxs-lookup"><span data-stu-id="af5e3-140">[LineString](../spatial/linestring.md) </span></span>  
 [<span data-ttu-id="af5e3-141">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="af5e3-141">Spatial Data &#40;SQL Server&#41;</span></span>](../spatial/spatial-data-sql-server.md)  
  
  
