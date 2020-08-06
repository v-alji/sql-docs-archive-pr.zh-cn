---
title: 空间数据类型概述 | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c0548d974e83bfe2b1e103d4458b17078fba8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691148"
---
# <a name="spatial-data-types-overview"></a><span data-ttu-id="6448a-102">空间数据类型概述</span><span class="sxs-lookup"><span data-stu-id="6448a-102">Spatial Data Types Overview</span></span>
  <span data-ttu-id="6448a-103">有两种类型的空间数据。</span><span class="sxs-lookup"><span data-stu-id="6448a-103">There are two types of spatial data.</span></span> <span data-ttu-id="6448a-104"> 数据类型支持平面或欧几里得（平面球）数据。</span><span class="sxs-lookup"><span data-stu-id="6448a-104">The `geometry` data type supports planar, or Euclidean (flat-earth), data.</span></span> <span data-ttu-id="6448a-105">`geometry` 数据类型符合开放地理空间联盟 (OGC) 的 SQL 简单特征规范 1.1.0 版 并符合 SQL MM（ISO 标准）。</span><span class="sxs-lookup"><span data-stu-id="6448a-105">The `geometry` data type both conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 and is compliant with SQL MM (ISO standard).</span></span>

 <span data-ttu-id="6448a-106">另外，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持 `geography` 数据类型，该数据类型可存储诸如 GPS 纬度和经度坐标之类的椭圆体（圆球）数据。</span><span class="sxs-lookup"><span data-stu-id="6448a-106">In addition, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supports the `geography` data type, which stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6448a-107">有关 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引入的空间功能的详细说明和示例（包括对空间数据类型的改进），请下载白皮书 [SQL Server Code-Named "Denali" 中的新空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="6448a-107">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including enhancements to the spatial data types, download the white paper, [New Spatial Features in SQL Server Code-Named "Denali"](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

##  <a name="spatial-data-objects"></a><a name="objects"></a> <span data-ttu-id="6448a-108">空间数据对象</span><span class="sxs-lookup"><span data-stu-id="6448a-108">Spatial Data Objects</span></span>
 <span data-ttu-id="6448a-109">`geometry` 和 `geography` 数据类型支持十六种空间数据对象或实例类型。</span><span class="sxs-lookup"><span data-stu-id="6448a-109">The `geometry` and `geography` data types support sixteen spatial data objects, or instance types.</span></span> <span data-ttu-id="6448a-110">但是，这些实例类型中只有十一种  “可实例化”；可以在数据库中创建并使用这些实例（或可对其进行实例化）。</span><span class="sxs-lookup"><span data-stu-id="6448a-110">However, only eleven of these instance types are *instantiable*; you can create and work with these instances (or instantiate them) in a database.</span></span> <span data-ttu-id="6448a-111">这些实例从其父数据类型派生某些属性，这些属性将它们作为 `Points` 、 **linestring、circularstring**、 `CompoundCurves` 、 `Polygons` `CurvePolygons` 或作为中的多个 `geometry` 或 `geography` 实例 `GeometryCollection` 加以区分。</span><span class="sxs-lookup"><span data-stu-id="6448a-111">These instances derive certain properties from their parent data types that distinguish them as `Points`, **LineStrings, CircularStrings**, `CompoundCurves`, `Polygons`, `CurvePolygons` or as multiple `geometry` or `geography` instances in a `GeometryCollection`.</span></span> <span data-ttu-id="6448a-112"> 类型具有附加实例类型 。</span><span class="sxs-lookup"><span data-stu-id="6448a-112">`Geography` type has an additional instance type, `FullGlobe`.</span></span>

 <span data-ttu-id="6448a-113">下图描述了 `geometry` 和 `geometry` 数据类型所基于的 `geography` 层次结构。</span><span class="sxs-lookup"><span data-stu-id="6448a-113">The figure below depicts the `geometry` hierarchy upon which the `geometry` and `geography` data types are based.</span></span> <span data-ttu-id="6448a-114">和的可实例化类型 `geometry` `geography` 以蓝色表示。</span><span class="sxs-lookup"><span data-stu-id="6448a-114">The instantiable types of `geometry` and `geography` are indicated in blue.</span></span>

 <span data-ttu-id="6448a-115">![几何类型的层次结构](../../database-engine/media/geom-hierarchy.gif "几何类型的层次结构")</span><span class="sxs-lookup"><span data-stu-id="6448a-115">![Hierarchy of the geometry type](../../database-engine/media/geom-hierarchy.gif "Hierarchy of the geometry type")</span></span>

 <span data-ttu-id="6448a-116">如图所示， `geometry` 和数据类型的十种可实例化类型 `geography` 为 `Point` 、、、、、、、、 `MultiPoint` `LineString` `CircularString` `MultiLineString` `CompoundCurve` `Polygon` `CurvePolygon` `MultiPolygon` 和 `GeometryCollection` 。</span><span class="sxs-lookup"><span data-stu-id="6448a-116">As the figure indicates, the ten instantiable types of the `geometry` and `geography` data types are `Point`, `MultiPoint`, `LineString`, `CircularString`, `MultiLineString`, `CompoundCurve`, `Polygon`, `CurvePolygon`, `MultiPolygon`, and `GeometryCollection`.</span></span> <span data-ttu-id="6448a-117">geography 数据类型有一个附加可实例化类型：`FullGlobe`。</span><span class="sxs-lookup"><span data-stu-id="6448a-117">There is one additional instantiable type for the geography data type: `FullGlobe`.</span></span> <span data-ttu-id="6448a-118">`geometry`和 `geography` 类型可以识别特定的实例，只要它是格式正确的实例，即使未显式定义该实例也是如此。</span><span class="sxs-lookup"><span data-stu-id="6448a-118">The `geometry` and `geography` types can recognize a specific instance as long as it is a well-formed instance, even if the instance is not defined explicitly.</span></span> <span data-ttu-id="6448a-119">例如，如果 `Point` 使用 ( STPointFromText 显式定义了一个实例，则 `geometry` `geography` `Point` 只要方法输入的格式正确，就会将该实例识别为。</span><span class="sxs-lookup"><span data-stu-id="6448a-119">For example, if you define a `Point` instance explicitly using the STPointFromText() method, `geometry` and `geography` recognize the instance as a `Point`, as long as the method input is well-formed.</span></span> <span data-ttu-id="6448a-120">如果您使用 `STGeomFromText()` 方法定义了相同的实例，则 `geometry` 和 `geography` 数据类型都将该实例识别为 `Point`。</span><span class="sxs-lookup"><span data-stu-id="6448a-120">If you define the same instance using the `STGeomFromText()` method, both the `geometry` and `geography` data types recognize the instance as a `Point`.</span></span>

 <span data-ttu-id="6448a-121">geometry 和 geography 类型的子类型分为简单类型和集合类型。</span><span class="sxs-lookup"><span data-stu-id="6448a-121">The subtypes for geometry and geography types are divided into simple and collection types.</span></span>  <span data-ttu-id="6448a-122">类似 `STNumCurves()` 的一些方法仅适用于简单类型。</span><span class="sxs-lookup"><span data-stu-id="6448a-122">Some methods like `STNumCurves()` work only with simple types.</span></span>

 <span data-ttu-id="6448a-123">简单类型包括：</span><span class="sxs-lookup"><span data-stu-id="6448a-123">Simple types include:</span></span>

-   [<span data-ttu-id="6448a-124">Point</span><span class="sxs-lookup"><span data-stu-id="6448a-124">Point</span></span>](../spatial/point.md)

-   [<span data-ttu-id="6448a-125">LineString</span><span class="sxs-lookup"><span data-stu-id="6448a-125">LineString</span></span>](../spatial/linestring.md)

-   [<span data-ttu-id="6448a-126">CircularString</span><span class="sxs-lookup"><span data-stu-id="6448a-126">CircularString</span></span>](../spatial/circularstring.md)

-   [<span data-ttu-id="6448a-127">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="6448a-127">CompoundCurve</span></span>](../spatial/compoundcurve.md)

-   [<span data-ttu-id="6448a-128">多边形</span><span class="sxs-lookup"><span data-stu-id="6448a-128">Polygon</span></span>](../spatial/polygon.md)

-   [<span data-ttu-id="6448a-129">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="6448a-129">CurvePolygon</span></span>](../spatial/curvepolygon.md)

 <span data-ttu-id="6448a-130">集合类型包括：</span><span class="sxs-lookup"><span data-stu-id="6448a-130">Collection types include:</span></span>

-   [<span data-ttu-id="6448a-131">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="6448a-131">MultiPoint</span></span>](../spatial/multipoint.md)

-   [<span data-ttu-id="6448a-132">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="6448a-132">MultiLineString</span></span>](../spatial/multilinestring.md)

-   [<span data-ttu-id="6448a-133">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="6448a-133">MultiPolygon</span></span>](../spatial/multipolygon.md)

-   [<span data-ttu-id="6448a-134">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="6448a-134">GeometryCollection</span></span>](../spatial/geometrycollection.md)


##  <a name="differences-between-the-geometry-and-geography-data-types"></a><a name="differences"></a> <span data-ttu-id="6448a-135">GEOMETRY 和 GEOGRAPHY 数据类型之间的差异</span><span class="sxs-lookup"><span data-stu-id="6448a-135">Differences Between the geometry and geography Data Types</span></span>
 <span data-ttu-id="6448a-136">两种空间数据类型的行为经常非常相似，但在数据存储方式和操作方式上存在某些重要的差别。</span><span class="sxs-lookup"><span data-stu-id="6448a-136">The two types of spatial data often behave quite similarly, but there are some key differences in how the data is stored and manipulated.</span></span>

### <a name="how-connecting-edges-are-defined"></a><span data-ttu-id="6448a-137">如何定义连接边</span><span class="sxs-lookup"><span data-stu-id="6448a-137">How connecting edges are defined</span></span>
 <span data-ttu-id="6448a-138">用于 `LineString` 和 `Polygon` 类型的定义数据仅限顶点。</span><span class="sxs-lookup"><span data-stu-id="6448a-138">The defining data for `LineString` and `Polygon` types are vertices only.</span></span>  <span data-ttu-id="6448a-139">geometry 类型中两个顶点之间的连接边是直线。</span><span class="sxs-lookup"><span data-stu-id="6448a-139">The connecting edge between two vertices in a geometry type is a straight line.</span></span>  <span data-ttu-id="6448a-140">但是，geography 类型中两个顶点之间的连接边是两个顶点之间的短的大椭圆弧。</span><span class="sxs-lookup"><span data-stu-id="6448a-140">However, the connecting edge between two vertices in a geography type is a short great elliptic arc between the two vertices.</span></span>  <span data-ttu-id="6448a-141">大椭圆是具有穿过其中心的投影的椭圆体的相交部分，大椭圆弧是大椭圆上的弧形线段。</span><span class="sxs-lookup"><span data-stu-id="6448a-141">A great ellipse is the intersection of the ellipsoid with a plane through its center and a great elliptic arc is an arc segment on the great ellipse.</span></span>

### <a name="how-circular-arc-segments-are-defined"></a><span data-ttu-id="6448a-142">如何定义圆弧线段</span><span class="sxs-lookup"><span data-stu-id="6448a-142">How circular arc segments are defined</span></span>
 <span data-ttu-id="6448a-143">在 XY 笛卡尔坐标平面上定义 geometry 类型的圆弧线段（Z 值被忽略）。</span><span class="sxs-lookup"><span data-stu-id="6448a-143">Circular arc segments for geometry types are defined on the XY Cartesian coordinate plane (Z values are ignored).</span></span> <span data-ttu-id="6448a-144">geography 类型的圆弧线段由参考球上的曲线段定义。</span><span class="sxs-lookup"><span data-stu-id="6448a-144">Circular arc segments for geography types are defined by curve segments on a reference sphere.</span></span> <span data-ttu-id="6448a-145">参考球上的任何平行面可以由两个互补圆弧（两个弧的点有一个恒定的纬度角）定义。</span><span class="sxs-lookup"><span data-stu-id="6448a-145">Any parallel on the reference sphere can be defined by two complementary circular arcs where the points for both arcs have a constant latitude angle.</span></span>

### <a name="measurements-in-spatial-data-types"></a><span data-ttu-id="6448a-146">空间数据类型中的度量</span><span class="sxs-lookup"><span data-stu-id="6448a-146">Measurements in spatial data types</span></span>
 <span data-ttu-id="6448a-147">在平面（或平面球）系统中，均以相同的度量单位为坐标测量距离和面积。</span><span class="sxs-lookup"><span data-stu-id="6448a-147">In the planar, or flat-earth, system, measurements of distances and areas are given in the same unit of measurement as coordinates.</span></span> <span data-ttu-id="6448a-148">如果使用 `geometry` 数据类型，(2, 2) 和 (5, 6) 之间的距离为 5 个单位，与所用的单位无关。</span><span class="sxs-lookup"><span data-stu-id="6448a-148">Using the `geometry` data type, the distance between (2, 2) and (5, 6) is 5 units, regardless of the units used.</span></span>

 <span data-ttu-id="6448a-149">在椭圆体（或圆球）系统中，坐标以经度和纬度的度数给定。</span><span class="sxs-lookup"><span data-stu-id="6448a-149">In the ellipsoidal, or round-earth system, coordinates are given in degrees of latitude and longitude.</span></span> <span data-ttu-id="6448a-150">但是，即使测量可能依据的是 `geography` 实例的空间引用标识符 (SRID)，长度和面积的测量单位也通常为米或平方米。</span><span class="sxs-lookup"><span data-stu-id="6448a-150">However, lengths and areas are usually measured in meters and square meters, though the measurement may depend on the spatial reference identifier (SRID) of the `geography` instance.</span></span> <span data-ttu-id="6448a-151"> 数据类型最常见的度量单位为米。</span><span class="sxs-lookup"><span data-stu-id="6448a-151">The most common unit of measurement for the `geography` data type is meters.</span></span>

### <a name="orientation-of-spatial-data"></a><span data-ttu-id="6448a-152">空间数据的方向</span><span class="sxs-lookup"><span data-stu-id="6448a-152">Orientation of spatial data</span></span>
 <span data-ttu-id="6448a-153">在平面系统中，多边形的环方向并非重要因素。</span><span class="sxs-lookup"><span data-stu-id="6448a-153">In the planar system, the ring orientation of a polygon is not an important factor.</span></span> <span data-ttu-id="6448a-154">例如，((0, 0), (10, 0), (0, 20), (0, 0)) 描述的多边形与 ((0, 0), (0, 20), (10, 0), (0, 0)) 描述的多边形相同。</span><span class="sxs-lookup"><span data-stu-id="6448a-154">For example, a polygon described by ((0, 0), (10, 0), (0, 20), (0, 0)) is the same as a polygon described by ((0, 0), (0, 20), (10, 0), (0, 0)).</span></span> <span data-ttu-id="6448a-155">SQL 规范的 OGC 简单特征未规定环顺序，并且 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不会强制环的顺序。</span><span class="sxs-lookup"><span data-stu-id="6448a-155">The OGC Simple Features for SQL Specification does not dictate a ring ordering, and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not enforce ring ordering.</span></span>

 <span data-ttu-id="6448a-156">在椭圆体系统中，多边形无意义，或者模糊不清，没有方向。</span><span class="sxs-lookup"><span data-stu-id="6448a-156">In an ellipsoidal system, a polygon has no meaning, or is ambiguous, without an orientation.</span></span> <span data-ttu-id="6448a-157">例如，赤道周围的环是否描述了北半球或南半球？</span><span class="sxs-lookup"><span data-stu-id="6448a-157">For example, does a ring around the equator describe the northern or southern hemisphere?</span></span> <span data-ttu-id="6448a-158">如果我们使用 `geography` 数据类型存储空间实例，必须指定环的方向并准确地描述实例的位置。</span><span class="sxs-lookup"><span data-stu-id="6448a-158">If we use the `geography` data type to store the spatial instance, we must specify the orientation of the ring and accurately describe the location of the instance.</span></span> <span data-ttu-id="6448a-159">椭圆体系统中多边形的内部由左侧规则定义。</span><span class="sxs-lookup"><span data-stu-id="6448a-159">The interior of the polygon in an ellipsoidal system is defined by the left-hand rule.</span></span>

 <span data-ttu-id="6448a-160">如果兼容级别为100或更低， [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 则 `geography` 数据类型具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="6448a-160">When the compatibility level is 100 or below in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] then the `geography` data type has the following restrictions:</span></span>

-   <span data-ttu-id="6448a-161">每个 `geography` 实例必须能够容纳在单个半球的内部。</span><span class="sxs-lookup"><span data-stu-id="6448a-161">Each `geography` instance must fit inside a single hemisphere.</span></span> <span data-ttu-id="6448a-162">任何大于半球的对象都无法存储。</span><span class="sxs-lookup"><span data-stu-id="6448a-162">No spatial objects larger than a hemisphere can be stored.</span></span>

-   <span data-ttu-id="6448a-163">使用开放地理空间联盟 (OGC) 熟知文本 (Well-Known Text, WKT) 或熟知二进制 (Well-Known Binary, WKB) 表示形式并且会产生大于一个半球的对象的任何 `geography` 实例都会引发一个 `ArgumentException` 异常。</span><span class="sxs-lookup"><span data-stu-id="6448a-163">Any `geography` instance from an Open Geospatial Consortium (OGC) Well-Known Text (WKT) or Well-Known Binary (WKB) representation that produces an object larger than a hemisphere throws an `ArgumentException`.</span></span>

-   <span data-ttu-id="6448a-164">`geography`需要输入两个实例的数据类型方法（ `geography` 如 STIntersection ( # A1、STUnion ( # A3、STDifference ( # A5 和 STSymDifference ( # A7）将返回 null （如果这些方法的结果不能容纳在单个半球内）。</span><span class="sxs-lookup"><span data-stu-id="6448a-164">The `geography` data type methods that require the input of two `geography` instances, such as STIntersection(), STUnion(), STDifference(), and STSymDifference(), will return null if the results from the methods do not fit inside a single hemisphere.</span></span> <span data-ttu-id="6448a-165">如果输出超过单个半球，STBuffer() 也将返回 Null。</span><span class="sxs-lookup"><span data-stu-id="6448a-165">STBuffer() will also return null if the output exceeds a single hemisphere.</span></span>

 <span data-ttu-id="6448a-166">在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中，`FullGlobe` 是一种特殊类型的多边形，涵盖了整个球体。</span><span class="sxs-lookup"><span data-stu-id="6448a-166">In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], `FullGlobe` is a special type of Polygon that covers the entire globe.</span></span> <span data-ttu-id="6448a-167">`FullGlobe` 有面积，但是没有边框或顶点。</span><span class="sxs-lookup"><span data-stu-id="6448a-167">`FullGlobe` has an area, but no borders or vertices.</span></span>

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a><span data-ttu-id="6448a-168">在 geography 数据类型中外环和内环并不重要</span><span class="sxs-lookup"><span data-stu-id="6448a-168">Outer and inner rings not important in geography data type</span></span>
 <span data-ttu-id="6448a-169">SQL 规范的 OGC 简单功能讨论了外环和内环，但此差别对数据类型来说几乎毫无意义 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` ; 多边形的任何环都可以作为外环。</span><span class="sxs-lookup"><span data-stu-id="6448a-169">The OGC Simple Features for SQL Specification discusses outer rings and inner rings, but this distinction makes little sense for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` data type; any ring of a polygon can be taken to be the outer ring.</span></span>

 <span data-ttu-id="6448a-170">有关 OGC 规范的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="6448a-170">For more information on OGC specifications, see the following:</span></span>

-   [<span data-ttu-id="6448a-171">OGC Specifications, Simple Feature Access Part 1 - Common Architecture（OGC 规范：简单特征访问第 1 部分 - 公共体系结构）</span><span class="sxs-lookup"><span data-stu-id="6448a-171">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93627)

-   [<span data-ttu-id="6448a-172">OGC Specifications, Simple Feature Access Part 2 - SQL Options（OGC 规范：简单特征访问第 2 部分 - SQL 选项）</span><span class="sxs-lookup"><span data-stu-id="6448a-172">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)


##  <a name="circular-arc-segments"></a><a name="circular"></a> <span data-ttu-id="6448a-173">圆弧线段</span><span class="sxs-lookup"><span data-stu-id="6448a-173">Circular Arc Segments</span></span>
 <span data-ttu-id="6448a-174">三种可实例化类型可以采用圆弧线段：`CircularString`、`CompoundCurve` 和 `CurvePolygon`。</span><span class="sxs-lookup"><span data-stu-id="6448a-174">Three instantiable types can take circular arc segments: `CircularString`, `CompoundCurve`, and `CurvePolygon`.</span></span>  <span data-ttu-id="6448a-175">圆弧线段在二维平面中由三个点定义；第三个点不能与第一个点相同。</span><span class="sxs-lookup"><span data-stu-id="6448a-175">A circular arc segment is defined by three points in a two dimensional plane and the third point cannot be the same as the first point.</span></span>

 <span data-ttu-id="6448a-176">图 A 和 B 显示典型的圆弧线段。</span><span class="sxs-lookup"><span data-stu-id="6448a-176">Figures A and B show typical circular arc segments.</span></span> <span data-ttu-id="6448a-177">请注意这三个点如何落在圆周上。</span><span class="sxs-lookup"><span data-stu-id="6448a-177">Note how each of the three points lie on the perimeter of a circle.</span></span>

 <span data-ttu-id="6448a-178">图 C 和 D 显示直线线段如何定义为圆弧线段。</span><span class="sxs-lookup"><span data-stu-id="6448a-178">Figures C and D show how a line segment can be defined as a circular arc segment.</span></span>  <span data-ttu-id="6448a-179">请注意仍需要三个点定义圆弧线段，不像普通直线线段只需要两个点来定义。</span><span class="sxs-lookup"><span data-stu-id="6448a-179">Note that three points are still needed to define the circular arc segment unlike a regular line segment which can be defined by just two points.</span></span>

 <span data-ttu-id="6448a-180">针对圆弧线段类型的方法使用直线线段来近似圆弧。用于近似圆弧的直线线段数量将取决于弧的长度和曲率。可以为每个圆弧线段类型存储 Z 值；但是，方法将不在计算中使用 Z 值。</span><span class="sxs-lookup"><span data-stu-id="6448a-180">Methods operating on circular arc segment types use straight line segments to approximate the circular arc. The number of line segments used to approximate the arc will depend on the length and curvature of the arc. Z values can be stored for each of the circular arc segment types; however, methods will not use the Z values in their calculations.</span></span>

> [!NOTE]
>  <span data-ttu-id="6448a-181">如果为圆弧线段指定 Z 值，则这些值对于圆弧线段中的所有点必须相同，才接受输入。</span><span class="sxs-lookup"><span data-stu-id="6448a-181">If Z values are given for circular arc segments then they must be the same for all points in the circular arc segment for it to be accepted for input.</span></span> <span data-ttu-id="6448a-182">例如，接受 `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` ，但是不接受 `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` 。</span><span class="sxs-lookup"><span data-stu-id="6448a-182">For example: `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` is accepted, but `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` is not accepted.</span></span>

### <a name="linestring-and-circularstring-comparison"></a><span data-ttu-id="6448a-183">LineString 和 CircularString 的比较</span><span class="sxs-lookup"><span data-stu-id="6448a-183">LineString and CircularString comparison</span></span>
 <span data-ttu-id="6448a-184">下图显示相同的等腰三角形（三角形 A 使用直线线段定义，三角形 B 使用圆弧线段定义）：</span><span class="sxs-lookup"><span data-stu-id="6448a-184">The following diagram shows identical isosceles triangles (triangle A uses line segments to define the triangle and triangle B uses circular arc segments to defined the triangle):</span></span>

 ![](../../database-engine/media/7e382f76-59da-4b62-80dc-caf93e637c14.png "7e382f76-59da-4b62-80dc-caf93e637c14")

 <span data-ttu-id="6448a-185">此示例显示如何使用 `LineString` 实例和 `CircularString` 实例存储上述等腰三角形：</span><span class="sxs-lookup"><span data-stu-id="6448a-185">This example shows how to store the above isosceles triangles using both a `LineString` instance and `CircularString` instance:</span></span>

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```

 <span data-ttu-id="6448a-186">请注意，`CircularString` 实例需要七个点来定义三角形，但是 `LineString` 实例只需要四个点定义三角形。</span><span class="sxs-lookup"><span data-stu-id="6448a-186">Notice that a `CircularString` instance requires seven points to define the triangle, but a `LineString` instance requires only four points to define the triangle.</span></span> <span data-ttu-id="6448a-187">原因是 `CircularString` 实例存储的是圆弧线段而非直线线段。</span><span class="sxs-lookup"><span data-stu-id="6448a-187">The reason for this is that a `CircularString` instance stores circular arc segments and not line segments.</span></span> <span data-ttu-id="6448a-188">因此，存储在 `CircularString` 实例中的三角形边是 ABC、CDE 和 EFA，而存储在 `LineString` 实例中的三角形边是 AC、CE 和 EA。</span><span class="sxs-lookup"><span data-stu-id="6448a-188">So the sides of the triangle stored in the `CircularString` instance are ABC, CDE, and EFA whereas the sides of the triangle stored in the `LineString` instance are AC, CE, and EA.</span></span>

 <span data-ttu-id="6448a-189">请思考以下代码片段：</span><span class="sxs-lookup"><span data-stu-id="6448a-189">Consider the following code snippet:</span></span>

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

 <span data-ttu-id="6448a-190">此代码段将生成以下结果：</span><span class="sxs-lookup"><span data-stu-id="6448a-190">This snippet will produce the following results:</span></span>

```
LS LengthCS Length
5.65685...6.28318...
```

 <span data-ttu-id="6448a-191">下图显示了如何将每种类型存储 (红线显示 `LineString``@g1` ，蓝线显示 `CircularString``@g2`) ：</span><span class="sxs-lookup"><span data-stu-id="6448a-191">The following illustration shows how each type is stored (red line shows `LineString``@g1`, blue line shows `CircularString``@g2`):</span></span>

 ![](../../database-engine/media/e52157b5-5160-4a4b-8560-50cdcf905b76.png "e52157b5-5160-4a4b-8560-50cdcf905b76")

 <span data-ttu-id="6448a-192">如上图所示，`CircularString` 实例与 `LineString` 实例相比，使用更少的点来存储曲线边界，而且更精确。</span><span class="sxs-lookup"><span data-stu-id="6448a-192">As the illustration above shows, `CircularString` instances use fewer points to store curve boundaries with greater precision than `LineString` instances.</span></span> <span data-ttu-id="6448a-193">`CircularString` 实例对于存储圆边界（如针对特定点的二十英里搜索半径）很有用。</span><span class="sxs-lookup"><span data-stu-id="6448a-193">`CircularString` instances are useful for storing circular boundaries like a twenty-mile search radius from a specific point.</span></span> <span data-ttu-id="6448a-194">`LineString` 实例则适合存储线性边界（如方形城市街区）。</span><span class="sxs-lookup"><span data-stu-id="6448a-194">`LineString` instances are good for storing boundaries that are linear like a square city block.</span></span>

### <a name="linestring-and-compoundcurve-comparison"></a><span data-ttu-id="6448a-195">LineString 和 CompoundCurve 的比较</span><span class="sxs-lookup"><span data-stu-id="6448a-195">LineString and CompoundCurve comparison</span></span>
 <span data-ttu-id="6448a-196">以下代码示例显示如何使用 `LineString` 和 `CompoundCurve` 实例存储相同的图形：</span><span class="sxs-lookup"><span data-stu-id="6448a-196">The following code examples show how to store the same figure using `LineString` and `CompoundCurve` instances:</span></span>

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

 <span data-ttu-id="6448a-197">或</span><span class="sxs-lookup"><span data-stu-id="6448a-197">or</span></span>

 <span data-ttu-id="6448a-198">在上述示例中，`LineString` 实例或 `CompoundCurve` 实例都可以存储该图形。</span><span class="sxs-lookup"><span data-stu-id="6448a-198">In the examples above, either a `LineString` instance or a `CompoundCurve` instance could store the figure.</span></span>  <span data-ttu-id="6448a-199">下一个示例使用 `CompoundCurve` 存储饼图切片：</span><span class="sxs-lookup"><span data-stu-id="6448a-199">This next example uses a `CompoundCurve` to store a pie slice:</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');
```

 <span data-ttu-id="6448a-200"> 实例可以直接存储圆弧线段 (2 2, 1 3, 0 2)，而  实例则必须将曲线转换为几个更小的直线线段。</span><span class="sxs-lookup"><span data-stu-id="6448a-200">A `CompoundCurve` instance can store the circular arc segment (2 2, 1 3, 0 2) directly whereas a `LineString` instance would have to convert the curve into several smaller line segments.</span></span>

### <a name="circularstring-and-compoundcurve-comparison"></a><span data-ttu-id="6448a-201">CircularString 和 CompoundCurve 的比较</span><span class="sxs-lookup"><span data-stu-id="6448a-201">CircularString and CompoundCurve comparison</span></span>
 <span data-ttu-id="6448a-202">以下代码示例显示如何将饼图切片存储在 `CircularString` 实例中：</span><span class="sxs-lookup"><span data-stu-id="6448a-202">The following code example shows how the pie slice can be stored in a `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

 <span data-ttu-id="6448a-203">要使用 `CircularString` 实例存储饼图切片，要求每个直线线段使用三个点。</span><span class="sxs-lookup"><span data-stu-id="6448a-203">To store the pie slice using a `CircularString` instance requires that three points be used for each line segment.</span></span>  <span data-ttu-id="6448a-204">如果一个中间点未知，必须计算它或必须将直线线段的端点加倍，如以下代码段所示：</span><span class="sxs-lookup"><span data-stu-id="6448a-204">If an intermediate point is not known, it either has to be calculated or the endpoint of the line segment has to be doubled as the following snippet shows:</span></span>

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

 <span data-ttu-id="6448a-205">`CompoundCurve` 实例允许 `LineString` 和  `CircularString` 组件，因此只需要知道饼图切片的直线线段的两个点。</span><span class="sxs-lookup"><span data-stu-id="6448a-205">`CompoundCurve` instances allow both `LineString` and `CircularString` components so that only two points to the line segments of the pie slice need to be known.</span></span>  <span data-ttu-id="6448a-206">此代码示例显示如何使用 `CompoundCurve` 存储相同的图形：</span><span class="sxs-lookup"><span data-stu-id="6448a-206">This code example shows how to use a `CompoundCurve` to store the same figure:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a><span data-ttu-id="6448a-207">Polygon 和 CurvePolygon 的比较</span><span class="sxs-lookup"><span data-stu-id="6448a-207">Polygon and CurvePolygon comparison</span></span>
 <span data-ttu-id="6448a-208">在定义外部环和内部环时，`CurvePolygon` 实例可以使用 `CircularString` 和 `CompoundCurve` 实例。</span><span class="sxs-lookup"><span data-stu-id="6448a-208">`CurvePolygon` instances can use `CircularString` and `CompoundCurve` instances when defining their exterior and interior rings.</span></span>  <span data-ttu-id="6448a-209">`Polygon` 实例不能使用圆弧线段类型：`CircularString` 和 `CompoundCurve`。</span><span class="sxs-lookup"><span data-stu-id="6448a-209">`Polygon` instances cannot use the circular arc segment types: `CircularString` and `CompoundCurve`.</span></span>


## <a name="see-also"></a><span data-ttu-id="6448a-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6448a-210">See Also</span></span>
 <span data-ttu-id="6448a-211">[空间数据 &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [Geometry 数据类型方法引用](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography 数据类型方法引用](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;Geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;geography 数据](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type)类型&#41;[STGeomFromText &#40;geometry](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)数据类型&#41;[STGeomFromText &#40;geography 数据类型&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span><span class="sxs-lookup"><span data-stu-id="6448a-211">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) [STGeomFromText &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span></span>


