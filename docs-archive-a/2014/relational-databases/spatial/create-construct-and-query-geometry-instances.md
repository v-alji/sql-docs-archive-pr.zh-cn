---
title: 创建、构造和查询几何图形实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- planar spatial data [SQL Server], getting started
- geometry data type [SQL Server], getting started
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 539f3f8bb1d9a1c277d6317cc571cf8bcb281833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578051"
---
# <a name="create-construct-and-query-geometry-instances"></a><span data-ttu-id="c6af8-102">创建、构造和查询几何图形实例</span><span class="sxs-lookup"><span data-stu-id="c6af8-102">Create, Construct, and Query geometry Instances</span></span>
  <span data-ttu-id="c6af8-103">平面空间数据类型 `geometry` 表示欧几里得（平面）坐标系中的数据。</span><span class="sxs-lookup"><span data-stu-id="c6af8-103">The planar spatial data type, `geometry`, represents data in a Euclidean (flat) coordinate system.</span></span> <span data-ttu-id="c6af8-104">此类型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中作为公共语言运行时 (CLR) 数据类型实现。</span><span class="sxs-lookup"><span data-stu-id="c6af8-104">This type is implemented as a common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c6af8-105">`geometry` 类型已进行预定义，可在每个数据库中使用。</span><span class="sxs-lookup"><span data-stu-id="c6af8-105">The `geometry` type is predefined and available in each database.</span></span> <span data-ttu-id="c6af8-106">您可以创建 `geometry` 类型的表列并对 `geometry` 数据进行操作，就像使用其他 CLR 类型一样。</span><span class="sxs-lookup"><span data-stu-id="c6af8-106">You can create table columns of type `geometry` and operate on `geometry` data in the same manner as you would use other CLR types.</span></span>  
  
 <span data-ttu-id="c6af8-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持的 `geometry` 数据类型（平面）符合开放地理空间联盟 (OGC) 的 SQL 简单特征规范 1.1.0 版。</span><span class="sxs-lookup"><span data-stu-id="c6af8-107">The `geometry` data type (planar) supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0.</span></span>  
  
 <span data-ttu-id="c6af8-108">有关 OGC 规范的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="c6af8-108">For more information on OGC specifications, see the following:</span></span>  
  
-   [<span data-ttu-id="c6af8-109">OGC Specifications, Simple Feature Access Part 1 - Common Architecture（OGC 规范：简单特征访问第 1 部分 - 公共体系结构）</span><span class="sxs-lookup"><span data-stu-id="c6af8-109">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   [<span data-ttu-id="c6af8-110">OGC Specifications, Simple Feature Access Part 2 - SQL Options（OGC 规范：简单特征访问第 2 部分 - SQL 选项）</span><span class="sxs-lookup"><span data-stu-id="c6af8-110">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span></span>](https://go.microsoft.com/fwlink/?LinkId=93629)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c6af8-111">支持现有 GML 3.1 标准的子集，该标准在下面的架构中定义：[https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959)。</span><span class="sxs-lookup"><span data-stu-id="c6af8-111">supports a subset of the existing GML 3.1 standard which is defined in the following schema: [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959).</span></span>  
  
##  <a name="creating-or-constructing-a-new-geometry-instance"></a><a name="creating"></a> <span data-ttu-id="c6af8-112">创建或构建新的几何图形实例</span><span class="sxs-lookup"><span data-stu-id="c6af8-112">Creating or constructing a new geometry instance</span></span>  
  
###  <a name="creating-a-new-geometry-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="c6af8-113">从现有实例创建新的几何图形实例</span><span class="sxs-lookup"><span data-stu-id="c6af8-113">Creating a New geometry Instance from an Existing Instance</span></span>  
 <span data-ttu-id="c6af8-114">`geometry` 数据类型提供了许多内置方法，您可以使用这些方法基于现有实例创建新的 `geometry` 实例。</span><span class="sxs-lookup"><span data-stu-id="c6af8-114">The `geometry` data type provides numerous built-in methods you can use to create new `geometry` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="c6af8-115">**在几何图形周围创建缓冲区**</span><span class="sxs-lookup"><span data-stu-id="c6af8-115">**To create a buffer around a geometry**</span></span>  
 [<span data-ttu-id="c6af8-116">STBuffer（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-116">STBuffer &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stbuffer-geometry-data-type)  
  
 [<span data-ttu-id="c6af8-117">BufferWithTolerance（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-117">BufferWithTolerance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type)  
  
 <span data-ttu-id="c6af8-118">**创建简化版的几何图形**</span><span class="sxs-lookup"><span data-stu-id="c6af8-118">**To create a simplified version of a geometry**</span></span>  
 [<span data-ttu-id="c6af8-119">Reduce（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-119">Reduce &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/reduce-geometry-data-type)  
  
 <span data-ttu-id="c6af8-120">**创建几何图形的凸包**</span><span class="sxs-lookup"><span data-stu-id="c6af8-120">**To create the convex hull of a geometry**</span></span>  
 [<span data-ttu-id="c6af8-121">STConvexHull（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-121">STConvexHull &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stconvexhull-geometry-data-type)  
  
 <span data-ttu-id="c6af8-122">**从两个几何图形的交集创建几何图形**</span><span class="sxs-lookup"><span data-stu-id="c6af8-122">**To create a geometry from the intersection of two geometries**</span></span>  
 [<span data-ttu-id="c6af8-123">STIntersection（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-123">STIntersection &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersection-geometry-data-type)  
  
 <span data-ttu-id="c6af8-124">**从两个几何图形的并集创建几何图形**</span><span class="sxs-lookup"><span data-stu-id="c6af8-124">**To create a geometry from the union of two geometries**</span></span>  
 [<span data-ttu-id="c6af8-125">STUnion（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-125">STUnion &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stunion-geometry-data-type)  
  
 <span data-ttu-id="c6af8-126">**从一个几何图形中与另一个几何图形不重叠的点创建几何图形**</span><span class="sxs-lookup"><span data-stu-id="c6af8-126">**To create a geometry from the points where one geometry does not overlap another**</span></span>  
 [<span data-ttu-id="c6af8-127">STDifference（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-127">STDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdifference-geometry-data-type)  
  
 <span data-ttu-id="c6af8-128">**从两个几何图形不重叠的点创建几何图形**</span><span class="sxs-lookup"><span data-stu-id="c6af8-128">**To create a geometry from the points where two geometries do not overlap**</span></span>  
 [<span data-ttu-id="c6af8-129">STSymDifference（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-129">STSymDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stsymdifference-geometry-data-type)  
  
 <span data-ttu-id="c6af8-130">**创建位于现有几何图形上的任意 Point 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-130">**To create an arbitrary Point instance that lies on an existing geometry**</span></span>  
 [<span data-ttu-id="c6af8-131">STPointOnSurface（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-131">STPointOnSurface &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="c6af8-132">从熟知文本输入构造几何图形实例</span><span class="sxs-lookup"><span data-stu-id="c6af8-132">Constructing a geometry Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="c6af8-133">`geometry` 数据类型提供了若干种用开放地理空间联盟 (OGC) WKT 表示形式生成几何图形的内置方法。</span><span class="sxs-lookup"><span data-stu-id="c6af8-133">The `geometry` data type provides several built-in methods that generate a geometry from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="c6af8-134">WKT 标准是一种允许几何图形数据以文本形式交换的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="c6af8-134">The WKT standard is a text string that allows geometry data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="c6af8-135">**用 WKT 输入构造任意类型的几何图形实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-135">**To construct any type of geometry instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-136">STGeomFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-136">STGeomFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)  
  
 [<span data-ttu-id="c6af8-137">Parse（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-137">Parse &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/parse-geometry-data-type)  
  
 <span data-ttu-id="c6af8-138">**用 WKT 输入构造几何图形 Point 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-138">**To construct a geometry Point instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-139">STPointFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-139">STPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="c6af8-140">**用 WKT 输入构造几何图形 MultiPoint 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-140">**To construct a geometry MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-141">STMPointFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-141">STMPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="c6af8-142">**用 WKT 输入构造几何图形 LineString 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-142">**To construct a geometry LineString instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-143">STLineFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-143">STLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="c6af8-144">**用 WKT 输入构造几何图形 MultiLineString 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-144">**To construct a geometry MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-145">STMLineFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-145">STMLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="c6af8-146">**用 WKT 输入构造几何图形 Polygon 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-146">**To construct a geometry Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-147">STPolyFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-147">STPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="c6af8-148">**用 WKT 输入构造几何图形 MultiPolygon 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-148">**To construct a geometry MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-149">STMPolyFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-149">STMPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="c6af8-150">**用 WKT 输入构造几何图形 GeometryCollection 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-150">**To construct a geometry GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="c6af8-151">STGeomCollFromText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-151">STGeomCollFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromtext-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="c6af8-152">从熟知二进制输入构造几何图形实例</span><span class="sxs-lookup"><span data-stu-id="c6af8-152">Constructing a geometry Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="c6af8-153">WKB 是开放地理空间联盟 (OGC) 规定的一种二进制格式，该格式允许 `geometry` 数据在客户端应用程序和 SQL 数据库之间进行交换。</span><span class="sxs-lookup"><span data-stu-id="c6af8-153">WKB is a binary format specified by the Open Geospatial Consortium (OGC) that permits `geometry` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="c6af8-154">以下函数接受用于构造几何图形的 WKB 输入：</span><span class="sxs-lookup"><span data-stu-id="c6af8-154">The following functions accept WKB input to construct geometries:</span></span>  
  
 <span data-ttu-id="c6af8-155">**用 WKB 输入构造任意类型的几何图形实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-155">**To construct any type of geometry instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-156">STGeomFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-156">STGeomFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-157">**用 WKB 输入构造几何图形 Point 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-157">**To construct a geometry Point instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-158">STPointFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-158">STPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-159">**用 WKB 输入构造几何图形 MultiPoint 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-159">**To construct a geometry MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-160">STMPointFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-160">STMPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-161">**用 WKB 输入构造几何图形 LineString 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-161">**To construct a geometry LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-162">STLineFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-162">STLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-163">**用 WKB 输入构造几何图形 MultiLineString 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-163">**To construct a geometry MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-164">STMLineFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-164">STMLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-165">**用 WKB 输入构造几何图形 Polygon 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-165">**To construct a geometry Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-166">STPolyFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-166">STPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-167">**用 WKB 输入构造几何图形 MultiPolygon 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-167">**To construct a geometry MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-168">STMPolyFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-168">STMPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="c6af8-169">**用 WKB 输入构造几何图形 GeometryCollection 实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-169">**To construct a geometry GeometryCollection instance from WKB input**</span></span>  
 [<span data-ttu-id="c6af8-170">STGeomCollFromWKB（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-170">STGeomCollFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromwkb-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="c6af8-171">用 GML 文本输入构造几何图形实例</span><span class="sxs-lookup"><span data-stu-id="c6af8-171">Constructing a geometry Instance from GML Text Input</span></span>  
 <span data-ttu-id="c6af8-172">`geometry`数据类型提供了一个方法，该方法 `geometry` 从 GML （几何对象的 XML 表示形式）生成实例。</span><span class="sxs-lookup"><span data-stu-id="c6af8-172">The `geometry` data type provides a method that generates a `geometry` instance from GML, an XML representation of geometric objects.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c6af8-173">支持部分 GML。</span><span class="sxs-lookup"><span data-stu-id="c6af8-173">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="c6af8-174">**用 GML 输入构造任意类型的几何图形实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-174">**To construct any type of geometry instance from GML input**</span></span>  
 [<span data-ttu-id="c6af8-175">GeomFromGml（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-175">GeomFromGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/geomfromgml-geometry-data-type)  
  
  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geometry-instance"></a><a name="returning"></a> <span data-ttu-id="c6af8-176">从几何图形实例返回熟知文本和熟知二进制</span><span class="sxs-lookup"><span data-stu-id="c6af8-176">Returning Well-Known Text and Well-Known Binary from a geometry Instance</span></span>  
 <span data-ttu-id="c6af8-177">可以使用以下方法返回 WKT 或 WKB 格式的 `geometry` 实例：</span><span class="sxs-lookup"><span data-stu-id="c6af8-177">You can use the following methods to return either the WKT or WKB format of a `geometry` instance:</span></span>  
  
 <span data-ttu-id="c6af8-178">**返回几何图形实例的 WKT 表示形式**</span><span class="sxs-lookup"><span data-stu-id="c6af8-178">**To return the WKT representation of a geometry instance**</span></span>  
 [<span data-ttu-id="c6af8-179">STAsText（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-179">STAsText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stastext-geometry-data-type)  
  
 [<span data-ttu-id="c6af8-180">ToString（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-180">ToString &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/tostring-geometry-data-type)  
  
 <span data-ttu-id="c6af8-181">**返回包括任何 Z 值和 M 值的几何图形的 WKT 表示形式**</span><span class="sxs-lookup"><span data-stu-id="c6af8-181">**To return the WKT representation of a geometry instance including any Z and M values**</span></span>  
 [<span data-ttu-id="c6af8-182">AsTextZM（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-182">AsTextZM &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/astextzm-geometry-data-type)  
  
 <span data-ttu-id="c6af8-183">**返回几何图形实例的 WKB 表示形式**</span><span class="sxs-lookup"><span data-stu-id="c6af8-183">**To return the WKB representation of a geometry instance**</span></span>  
 [<span data-ttu-id="c6af8-184">STAsBinary（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-184">STAsBinary &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stasbinary-geometry-data-type)  
  
 <span data-ttu-id="c6af8-185">**返回几何图形实例的 GML 表示形式**</span><span class="sxs-lookup"><span data-stu-id="c6af8-185">**To return a GML representation of a geometry instance**</span></span>  
 [<span data-ttu-id="c6af8-186">AsGml（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-186">AsGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/asgml-geometry-data-type)  
  
  
  
##  <a name="querying-the-properties-and-behaviors-of-geometry-instances"></a><a name="querying"></a> <span data-ttu-id="c6af8-187">查询几何图形实例的属性和行为</span><span class="sxs-lookup"><span data-stu-id="c6af8-187">Querying the Properties and Behaviors of geometry Instances</span></span>  
 <span data-ttu-id="c6af8-188">所有 `geometry` 实例都具有多个可通过提供的方法进行检索的属性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c6af8-188">All `geometry` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="c6af8-189">下列主题定义了几何图形类型的属性和行为，并为查询每种图形定义了方法。</span><span class="sxs-lookup"><span data-stu-id="c6af8-189">The following topics define the properties and behaviors of geometry types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="c6af8-190">有效性、实例类型和 GeometryCollection 信息</span><span class="sxs-lookup"><span data-stu-id="c6af8-190">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="c6af8-191">构造 `geometry` 实例后，就可以使用以下方法确定其格式是否正确、返回实例类型，或者，如果它是集合实例，则返回特定的 `geometry` 实例。</span><span class="sxs-lookup"><span data-stu-id="c6af8-191">Once a `geometry` instance is constructed, you can use the following methods to determine if it is well-formed, return the instance type, or, if it is a collection instance, return a specific `geometry` instance.</span></span>  
  
 <span data-ttu-id="c6af8-192">**返回几何图形的实例类型**</span><span class="sxs-lookup"><span data-stu-id="c6af8-192">**To return the instance type of a geometry**</span></span>  
 [<span data-ttu-id="c6af8-193">STGeometryType（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-193">STGeometryType &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeometrytype-geometry-data-type)  
  
 <span data-ttu-id="c6af8-194">**确定几何图形是否为给定的实例类型**</span><span class="sxs-lookup"><span data-stu-id="c6af8-194">**To determine if a geometry is a given instance type**</span></span>  
 [<span data-ttu-id="c6af8-195">InstanceOf（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-195">InstanceOf &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/instanceof-geometry-data-type)  
  
 <span data-ttu-id="c6af8-196">**确定几何图形实例对其实例类型而言格式是否正确**</span><span class="sxs-lookup"><span data-stu-id="c6af8-196">**To determine if a geometry instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="c6af8-197">STIsValid（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-197">STIsValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
 <span data-ttu-id="c6af8-198">**将几何图形实例转换成具有实例类型的格式正确的几何图形实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-198">**To convert a geometry instance to a well-formed geometry instance with an instance type**</span></span>  
 [<span data-ttu-id="c6af8-199">MakeValid（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-199">MakeValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)  
  
 <span data-ttu-id="c6af8-200">**返回几何图形集合实例中的几何图形数目**</span><span class="sxs-lookup"><span data-stu-id="c6af8-200">**To return the number of geometries in a geometry collection instance**</span></span>  
 [<span data-ttu-id="c6af8-201">STNumGeometries（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-201">STNumGeometries &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumgeometries-geometry-data-type)  
  
 <span data-ttu-id="c6af8-202">返回几何图形集合实例中的特定几何图形</span><span class="sxs-lookup"><span data-stu-id="c6af8-202">To return a specific geometry in a geometry collection instance</span></span>  
 <span data-ttu-id="c6af8-203">[STGeometryN（geometry 数据类型）](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-203">[STGeometryN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (geometry Data type)</span></span>  
  
  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="c6af8-204">点数</span><span class="sxs-lookup"><span data-stu-id="c6af8-204">Number of Points</span></span>  
 <span data-ttu-id="c6af8-205">所有非空 `geometry` 实例都由*点*组成。</span><span class="sxs-lookup"><span data-stu-id="c6af8-205">All nonempty `geometry` instances are comprised of *points*.</span></span> <span data-ttu-id="c6af8-206">这些点表示在其上绘制几何图形的面的 X 和 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="c6af8-206">These points represent the X- and Y-coordinates of the plane on which the geometries are drawn.</span></span> <span data-ttu-id="c6af8-207">`geometry` 提供许多用于查询实例的点的内置方法。</span><span class="sxs-lookup"><span data-stu-id="c6af8-207">`geometry` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="c6af8-208">**返回构成实例的点数。**</span><span class="sxs-lookup"><span data-stu-id="c6af8-208">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="c6af8-209">STNumPoints（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-209">STNumPoints &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)  
  
 <span data-ttu-id="c6af8-210">**返回实例中的特定点**</span><span class="sxs-lookup"><span data-stu-id="c6af8-210">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="c6af8-211">STPointN</span><span class="sxs-lookup"><span data-stu-id="c6af8-211">STPointN</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="c6af8-212">**返回位于实例上的某个任意点**</span><span class="sxs-lookup"><span data-stu-id="c6af8-212">**To return an arbitrary point that lies on an instance**</span></span>  
 [<span data-ttu-id="c6af8-213">STPointOnSurface</span><span class="sxs-lookup"><span data-stu-id="c6af8-213">STPointOnSurface</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
 <span data-ttu-id="c6af8-214">**返回实例的起始点**</span><span class="sxs-lookup"><span data-stu-id="c6af8-214">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="c6af8-215">STStartPoint</span><span class="sxs-lookup"><span data-stu-id="c6af8-215">STStartPoint</span></span>](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)  
  
 <span data-ttu-id="c6af8-216">**返回实例的终点**</span><span class="sxs-lookup"><span data-stu-id="c6af8-216">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="c6af8-217">STEndpoint</span><span class="sxs-lookup"><span data-stu-id="c6af8-217">STEndpoint</span></span>](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)  
  
 <span data-ttu-id="c6af8-218">**返回点实例的 X 坐标**</span><span class="sxs-lookup"><span data-stu-id="c6af8-218">**To return the X-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="c6af8-219">STX（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="c6af8-219">STX &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stx-geometry-data-type)  
  
 <span data-ttu-id="c6af8-220">**返回点实例的 Y 坐标**</span><span class="sxs-lookup"><span data-stu-id="c6af8-220">**To return the Y-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="c6af8-221">STY</span><span class="sxs-lookup"><span data-stu-id="c6af8-221">STY</span></span>](/sql/t-sql/spatial-geometry/sty-geometry-data-type)  
  
 <span data-ttu-id="c6af8-222">**返回 Polygon、CurvePolygon 或 MultiPolygon 实例的几何中心点**</span><span class="sxs-lookup"><span data-stu-id="c6af8-222">**To return the geometric center point of a Polygon, CurvePolygon, or MultiPolygon instance**</span></span>  
 [<span data-ttu-id="c6af8-223">STCentroid</span><span class="sxs-lookup"><span data-stu-id="c6af8-223">STCentroid</span></span>](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)  
  
  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="c6af8-224">维度</span><span class="sxs-lookup"><span data-stu-id="c6af8-224">Dimension</span></span>  
 <span data-ttu-id="c6af8-225">非空 `geometry` 实例可以为零维、一维或二维。</span><span class="sxs-lookup"><span data-stu-id="c6af8-225">A nonempty `geometry` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="c6af8-226">零维 `geometries`（例如 `Point` 和 `MultiPoint`）没有长度或面积。</span><span class="sxs-lookup"><span data-stu-id="c6af8-226">Zero-dimensional `geometries`, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="c6af8-227">一维对象（例如 `LineString, CircularString, CompoundCurve` 和 `MultiLineString`）具有长度。</span><span class="sxs-lookup"><span data-stu-id="c6af8-227">One-dimensional objects, such as `LineString, CircularString, CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="c6af8-228">二维实例（例如 `Polygon`、`CurvePolygon` 和 `MultiPolygon`）具有面积和长度。</span><span class="sxs-lookup"><span data-stu-id="c6af8-228">Two-dimensional instances, such as `Polygon`, `CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="c6af8-229">空实例将报告为 -1 维，并且`GeometryCollection` 将根据其内容类型报告一个面积。</span><span class="sxs-lookup"><span data-stu-id="c6af8-229">Empty instances will report a dimension of -1, and a `GeometryCollection` will report an area dependent on the types of its contents.</span></span>  
  
 <span data-ttu-id="c6af8-230">**返回实例的维度**</span><span class="sxs-lookup"><span data-stu-id="c6af8-230">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="c6af8-231">STDimension</span><span class="sxs-lookup"><span data-stu-id="c6af8-231">STDimension</span></span>](/sql/t-sql/spatial-geometry/stdimension-geometry-data-type)  
  
 <span data-ttu-id="c6af8-232">**返回实例的长度**</span><span class="sxs-lookup"><span data-stu-id="c6af8-232">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="c6af8-233">STLength</span><span class="sxs-lookup"><span data-stu-id="c6af8-233">STLength</span></span>](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)  
  
 <span data-ttu-id="c6af8-234">**返回实例的面积**</span><span class="sxs-lookup"><span data-stu-id="c6af8-234">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="c6af8-235">STArea</span><span class="sxs-lookup"><span data-stu-id="c6af8-235">STArea</span></span>](/sql/t-sql/spatial-geometry/starea-geometry-data-type)  
  
  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="c6af8-236">Empty</span><span class="sxs-lookup"><span data-stu-id="c6af8-236">Empty</span></span>  
 <span data-ttu-id="c6af8-237">*空* `geometry` 实例不包含任何点。</span><span class="sxs-lookup"><span data-stu-id="c6af8-237">An *empty*`geometry` instance does not have any points.</span></span> <span data-ttu-id="c6af8-238">空的 `LineString, CircularString`、`CompoundCurve` 和 `MultiLineString` 实例的长度为零。</span><span class="sxs-lookup"><span data-stu-id="c6af8-238">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is zero.</span></span> <span data-ttu-id="c6af8-239">空的 `Polygon`、`CurvePolygon` 和 `MultiPolygon` 实例的面积为 0。</span><span class="sxs-lookup"><span data-stu-id="c6af8-239">The area of empty `Polygon`, `CurvePolygon`, and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="c6af8-240">**确定实例是否为空**</span><span class="sxs-lookup"><span data-stu-id="c6af8-240">**To determine if an instance is empty**</span></span>  
 <span data-ttu-id="c6af8-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="c6af8-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type).</span></span>  
  
  
  
###  <a name="simple"></a><a name="simple"></a> <span data-ttu-id="c6af8-242">Simple</span><span class="sxs-lookup"><span data-stu-id="c6af8-242">Simple</span></span>  
 <span data-ttu-id="c6af8-243">为了使 `geometry` 实例的*简单*，它必须满足这两个要求：</span><span class="sxs-lookup"><span data-stu-id="c6af8-243">For a `geometry` of the instance to be *simple*, it must meet both of these requirements:</span></span>  
  
-   <span data-ttu-id="c6af8-244">实例的每个图形不能与自身相交，但其终点除外。</span><span class="sxs-lookup"><span data-stu-id="c6af8-244">Each figure of the instance must not intersect itself, except at its endpoints.</span></span>  
  
-   <span data-ttu-id="c6af8-245">实例的任何两个图形可在某个点上相交，但两个边界上的点除外。</span><span class="sxs-lookup"><span data-stu-id="c6af8-245">No two figures of the instance can intersect each other at a point that is not in both of their boundaries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6af8-246">空几何图形总是简单的。</span><span class="sxs-lookup"><span data-stu-id="c6af8-246">Empty geometries are always simple.</span></span>  
  
 <span data-ttu-id="c6af8-247">**确定实例是否是简单的**</span><span class="sxs-lookup"><span data-stu-id="c6af8-247">**To determine if an instance is simple**</span></span>  
 <span data-ttu-id="c6af8-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="c6af8-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type).</span></span>  
  
  
  
###  <a name="boundary-interior-and-exterior"></a><a name="boundary"></a> <span data-ttu-id="c6af8-249">边界、内部和外部</span><span class="sxs-lookup"><span data-stu-id="c6af8-249">Boundary, Interior, and Exterior</span></span>  
 <span data-ttu-id="c6af8-250">实例的*内部* `geometry` 是实例占用的空间，而*外部*是指未占用的空间。</span><span class="sxs-lookup"><span data-stu-id="c6af8-250">The *interior* of a `geometry` instance is the space occupied by the instance, and the *exterior* is the space not occupied it.</span></span>  
  
 <span data-ttu-id="c6af8-251">“边界”  由 OGC 定义，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6af8-251">*Boundary* is defined by the OGC as follows:</span></span>  
  
-   <span data-ttu-id="c6af8-252">`Point` 和 `MultiPoint` 实例没有边界。</span><span class="sxs-lookup"><span data-stu-id="c6af8-252">`Point` and `MultiPoint` instances do not have a boundary.</span></span>  
  
-   <span data-ttu-id="c6af8-253">`LineString` 和 `MultiLineString` 边界由起始点和终点形成，并删除那些出现次数为偶数的点。</span><span class="sxs-lookup"><span data-stu-id="c6af8-253">`LineString` and `MultiLineString` boundaries are formed by the start points and end points, removing those that occur an even number of times.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="c6af8-254">`Polygon` 或 `MultiPolygon` 实例的边界是其环的集合。</span><span class="sxs-lookup"><span data-stu-id="c6af8-254">The boundary of a `Polygon` or `MultiPolygon` instance is the set of its rings.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="c6af8-255">**返回实例的边界**</span><span class="sxs-lookup"><span data-stu-id="c6af8-255">**To return the boundary of an instance**</span></span>  
 [<span data-ttu-id="c6af8-256">STBoundary</span><span class="sxs-lookup"><span data-stu-id="c6af8-256">STBoundary</span></span>](/sql/t-sql/spatial-geometry/stboundary-geometry-data-type)  
  
  
  
###  <a name="envelope"></a><a name="envelope"></a> <span data-ttu-id="c6af8-257">包络线</span><span class="sxs-lookup"><span data-stu-id="c6af8-257">Envelope</span></span>  
 <span data-ttu-id="c6af8-258">实例的*信封* `geometry` 也称为 "*边界框*"，它是由实例的最小和最大 (X，Y) 坐标构成的轴对齐矩形。</span><span class="sxs-lookup"><span data-stu-id="c6af8-258">The *envelope* of a `geometry` instance, also known as the *bounding box*, is the axis-aligned rectangle formed by the minimum and maximum (X,Y) coordinates of the instance.</span></span>  
  
 <span data-ttu-id="c6af8-259">**返回实例的包络线**</span><span class="sxs-lookup"><span data-stu-id="c6af8-259">**To return the envelope of an instance**</span></span>  
 [<span data-ttu-id="c6af8-260">STEnvelope</span><span class="sxs-lookup"><span data-stu-id="c6af8-260">STEnvelope</span></span>](/sql/t-sql/spatial-geometry/stenvelope-geometry-data-type)  
  
  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="c6af8-261">闭合</span><span class="sxs-lookup"><span data-stu-id="c6af8-261">Closure</span></span>  
 <span data-ttu-id="c6af8-262">*闭合*的 `geometry` 实例是一个图形，其起点和终点是相同的。</span><span class="sxs-lookup"><span data-stu-id="c6af8-262">A *closed*`geometry` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="c6af8-263">`Polygon` 实例被视为闭合的。</span><span class="sxs-lookup"><span data-stu-id="c6af8-263">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="c6af8-264">`Point` 实例不是闭合的。</span><span class="sxs-lookup"><span data-stu-id="c6af8-264">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="c6af8-265">环是一个简单、闭合的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="c6af8-265">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="c6af8-266">**确定实例是否闭合**</span><span class="sxs-lookup"><span data-stu-id="c6af8-266">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="c6af8-267">STIsClosed</span><span class="sxs-lookup"><span data-stu-id="c6af8-267">STIsClosed</span></span>](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)  
  
 <span data-ttu-id="c6af8-268">**确定实例是否为环**</span><span class="sxs-lookup"><span data-stu-id="c6af8-268">**To determine if an instance is a ring**</span></span>  
 [<span data-ttu-id="c6af8-269">STIsRing</span><span class="sxs-lookup"><span data-stu-id="c6af8-269">STIsRing</span></span>](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)  
  
 <span data-ttu-id="c6af8-270">**返回多边形实例的外环**</span><span class="sxs-lookup"><span data-stu-id="c6af8-270">**To return the exterior ring of a Polygon instance**</span></span>  
 [<span data-ttu-id="c6af8-271">STExteriorRing</span><span class="sxs-lookup"><span data-stu-id="c6af8-271">STExteriorRing</span></span>](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)  
  
 <span data-ttu-id="c6af8-272">**返回多边形的内环数**</span><span class="sxs-lookup"><span data-stu-id="c6af8-272">**To return the number of interior rings in a Polygon**</span></span>  
 [<span data-ttu-id="c6af8-273">STNumInteriorRing</span><span class="sxs-lookup"><span data-stu-id="c6af8-273">STNumInteriorRing</span></span>](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)  
  
 <span data-ttu-id="c6af8-274">**返回多边形的指定内环**</span><span class="sxs-lookup"><span data-stu-id="c6af8-274">**To return a specified interior ring of a Polygon**</span></span>  
 [<span data-ttu-id="c6af8-275">STInteriorRingN</span><span class="sxs-lookup"><span data-stu-id="c6af8-275">STInteriorRingN</span></span>](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)  
  
  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="c6af8-276">空间引用标识符 (SRID)</span><span class="sxs-lookup"><span data-stu-id="c6af8-276">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="c6af8-277">空间引用标识符 (SRID) 是指定 `geometry` 实例所在的坐标系的标识符。</span><span class="sxs-lookup"><span data-stu-id="c6af8-277">The spatial reference ID (SRID) is an identifier specifying which coordinate system the `geometry` instance is represented in.</span></span> <span data-ttu-id="c6af8-278">两个拥有不同 SRID 的实例是不可比的。</span><span class="sxs-lookup"><span data-stu-id="c6af8-278">Two instances with different SRIDs are incomparable.</span></span>  
  
 <span data-ttu-id="c6af8-279">**设置或返回实例的 SRID**</span><span class="sxs-lookup"><span data-stu-id="c6af8-279">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="c6af8-280">STSrid</span><span class="sxs-lookup"><span data-stu-id="c6af8-280">STSrid</span></span>](/sql/t-sql/spatial-geometry/stsrid-geometry-data-type)  
  
 <span data-ttu-id="c6af8-281">此属性可以进行修改。</span><span class="sxs-lookup"><span data-stu-id="c6af8-281">This property can be modified.</span></span>  
  
  
  
##  <a name="determining-relationships-between-geometry-instances"></a><a name="rel"></a> <span data-ttu-id="c6af8-282">确定几何图形实例之间的关系</span><span class="sxs-lookup"><span data-stu-id="c6af8-282">Determining Relationships between geometry Instances</span></span>  
 <span data-ttu-id="c6af8-283">`geometry` 数据类型提供了许多内置方法，您可以使用这些方法确定两个 `geometry` 实例之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c6af8-283">The `geometry` data type provides many built-in methods you can use to determine relationships between two `geometry` instances.</span></span>  
  
 <span data-ttu-id="c6af8-284">**确定两个实例是否包含相同的点集**</span><span class="sxs-lookup"><span data-stu-id="c6af8-284">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="c6af8-285">STEquals</span><span class="sxs-lookup"><span data-stu-id="c6af8-285">STEquals</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="c6af8-286">**确定两个实例是否不相接**</span><span class="sxs-lookup"><span data-stu-id="c6af8-286">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="c6af8-287">STDisjoint</span><span class="sxs-lookup"><span data-stu-id="c6af8-287">STDisjoint</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="c6af8-288">**确定两个实例是否相交**</span><span class="sxs-lookup"><span data-stu-id="c6af8-288">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="c6af8-289">STIntersects</span><span class="sxs-lookup"><span data-stu-id="c6af8-289">STIntersects</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="c6af8-290">**确定两个实例是否接触**</span><span class="sxs-lookup"><span data-stu-id="c6af8-290">**To determine if two instances touch**</span></span>  
 [<span data-ttu-id="c6af8-291">STTouches</span><span class="sxs-lookup"><span data-stu-id="c6af8-291">STTouches</span></span>](/sql/t-sql/spatial-geometry/sttouches-geometry-data-type)  
  
 <span data-ttu-id="c6af8-292">**确定两个实例是否重叠**</span><span class="sxs-lookup"><span data-stu-id="c6af8-292">**To determine if two instances overlap**</span></span>  
 [<span data-ttu-id="c6af8-293">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="c6af8-293">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="c6af8-294">**确定两个实例是否交叉**</span><span class="sxs-lookup"><span data-stu-id="c6af8-294">**To determine if two instances cross**</span></span>  
 [<span data-ttu-id="c6af8-295">STCrosses</span><span class="sxs-lookup"><span data-stu-id="c6af8-295">STCrosses</span></span>](/sql/t-sql/spatial-geometry/stcrosses-geometry-data-type)  
  
 <span data-ttu-id="c6af8-296">**确定某个实例是否在另一个实例内部**</span><span class="sxs-lookup"><span data-stu-id="c6af8-296">**To determine if one instance is within another**</span></span>  
 [<span data-ttu-id="c6af8-297">STWithin</span><span class="sxs-lookup"><span data-stu-id="c6af8-297">STWithin</span></span>](/sql/t-sql/spatial-geometry/stwithin-geometry-data-type)  
  
 <span data-ttu-id="c6af8-298">**确定某个实例是否包含另一个实例**</span><span class="sxs-lookup"><span data-stu-id="c6af8-298">**To determine if one instance contains another**</span></span>  
 [<span data-ttu-id="c6af8-299">STContains</span><span class="sxs-lookup"><span data-stu-id="c6af8-299">STContains</span></span>](/sql/t-sql/spatial-geometry/stcontains-geometry-data-type)  
  
 <span data-ttu-id="c6af8-300">**确定某个实例是否与另一个实例重叠**</span><span class="sxs-lookup"><span data-stu-id="c6af8-300">**To determine if one instance overlaps another**</span></span>  
 [<span data-ttu-id="c6af8-301">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="c6af8-301">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="c6af8-302">**确定两个实例是否存在空间关系**</span><span class="sxs-lookup"><span data-stu-id="c6af8-302">**To determine if two instances are spatially related**</span></span>  
 [<span data-ttu-id="c6af8-303">STRelate</span><span class="sxs-lookup"><span data-stu-id="c6af8-303">STRelate</span></span>](/sql/t-sql/spatial-geometry/strelate-geometry-data-type)  
  
 <span data-ttu-id="c6af8-304">**确定两个几何图形中的点之间的最短距离**</span><span class="sxs-lookup"><span data-stu-id="c6af8-304">**To determine the shortest distance between points in two geometries**</span></span>  
 [<span data-ttu-id="c6af8-305">STDistance</span><span class="sxs-lookup"><span data-stu-id="c6af8-305">STDistance</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
  
  
##  <a name="geometry-instances-default-to-zero-srid"></a><a name="defaultsrid"></a> <span data-ttu-id="c6af8-306">几何图形实例默认 SRID 为零</span><span class="sxs-lookup"><span data-stu-id="c6af8-306">geometry Instances Default to Zero SRID</span></span>  
 <span data-ttu-id="c6af8-307">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 `geometry` 实例的默认 SRID 为 0。</span><span class="sxs-lookup"><span data-stu-id="c6af8-307">The default SRID for `geometry` instances in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 0.</span></span> <span data-ttu-id="c6af8-308">利用 `geometry` 空间数据，执行计算是不需要空间实例的指定 SRID 的；因此，实例可驻留在未定义的平面空间。</span><span class="sxs-lookup"><span data-stu-id="c6af8-308">With `geometry` spatial data, the specific SRID of the spatial instance is not required to perform calculations; thus, instances can reside in undefined planar space.</span></span> <span data-ttu-id="c6af8-309">若要在 `geometry` 数据类型方法的计算中指明未定义的平面空间，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 使用 SRID 0。</span><span class="sxs-lookup"><span data-stu-id="c6af8-309">To indicate undefined planar space in the calculations of `geometry` data type methods, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses SRID 0.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="c6af8-310">示例</span><span class="sxs-lookup"><span data-stu-id="c6af8-310">Examples</span></span>  
 <span data-ttu-id="c6af8-311">以下两个示例显示了如何添加和查询几何图形数据。</span><span class="sxs-lookup"><span data-stu-id="c6af8-311">The following two examples show how to add and query geometry data.</span></span>  
  
-   <span data-ttu-id="c6af8-312">第一个示例创建了带有标识列和 `geometry` 列 `GeomCol1`的表。</span><span class="sxs-lookup"><span data-stu-id="c6af8-312">The first example creates a table with an identity column and a `geometry` column `GeomCol1`.</span></span> <span data-ttu-id="c6af8-313">第三列将 `geometry` 列呈现为其开放地理空间信息联盟 (OGC) 熟知文本 (WKT) 表示形式，并使用 `STAsText()` 方法。</span><span class="sxs-lookup"><span data-stu-id="c6af8-313">A third column renders the `geometry` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="c6af8-314">接下来将插入两行：一行包含 `LineString` 类型的 `geometry`实例，一行包含 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="c6af8-314">Two rows are then inserted: one row contains a `LineString` instance of `geometry`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeomCol1 geometry,   
        GeomCol2 AS GeomCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
    GO  
    ```  
  
-   <span data-ttu-id="c6af8-315">第二个示例使用 `STIntersection()` 方法返回此前插入的两个 `geometry` 实例相交的点。</span><span class="sxs-lookup"><span data-stu-id="c6af8-315">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geometry` instances intersect.</span></span>  
  
    ```  
    DECLARE @geom1 geometry;  
    DECLARE @geom2 geometry;  
    DECLARE @result geometry;  
  
    SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geom1.STIntersection(@geom2);  
    SELECT @result.STAsText();  
    ```  
  
  
  
## <a name="see-also"></a><span data-ttu-id="c6af8-316">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6af8-316">See Also</span></span>  
 [<span data-ttu-id="c6af8-317">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c6af8-317">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
