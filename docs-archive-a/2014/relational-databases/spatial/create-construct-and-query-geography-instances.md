---
title: 创建、构造和查询地理实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d744457cc517a6172cca96b27eae1f456deca24e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578053"
---
# <a name="create-construct-and-query-geography-instances"></a><span data-ttu-id="763c4-102">创建、构造和查询地理实例</span><span class="sxs-lookup"><span data-stu-id="763c4-102">Create, Construct, and Query geography Instances</span></span>
  <span data-ttu-id="763c4-103">地理空间数据类型 `geography` 表示圆形地球坐标系中的数据。</span><span class="sxs-lookup"><span data-stu-id="763c4-103">The geography spatial data type, `geography`, represents data in a round-earth coordinate system.</span></span> <span data-ttu-id="763c4-104">此类型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中作为 .NET 公共语言运行时 (CLR) 数据类型实现。</span><span class="sxs-lookup"><span data-stu-id="763c4-104">This type is implemented as a .NET common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="763c4-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` 数据类型存储诸如 GPS 纬度和经度坐标之类的椭球体（圆形地球）数据。</span><span class="sxs-lookup"><span data-stu-id="763c4-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` data type stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>  
  
 <span data-ttu-id="763c4-106">`geography` 类型已进行预定义，可在每个数据库中使用。</span><span class="sxs-lookup"><span data-stu-id="763c4-106">The `geography` type is predefined and available in each database.</span></span> <span data-ttu-id="763c4-107">您可以创建 `geography` 类型的表列并对 `geography` 数据进行操作，就像使用其他系统提供的数据类型一样。</span><span class="sxs-lookup"><span data-stu-id="763c4-107">You can create table columns of type `geography` and operate on `geography` data in the same manner as you would use other system-supplied types.</span></span>  
  
##  <a name="creating-or-constructing-a-new-geography-instance"></a><a name="creating"></a> <span data-ttu-id="763c4-108">创建或构建新的地域实例</span><span class="sxs-lookup"><span data-stu-id="763c4-108">Creating or constructing a new geography instance</span></span>  
  
###  <a name="creating-a-new-geography-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="763c4-109">从现有实例创建新的地域实例</span><span class="sxs-lookup"><span data-stu-id="763c4-109">Creating a New geography Instance from an Existing Instance</span></span>  
 <span data-ttu-id="763c4-110">`geography` 数据类型提供了许多内置方法，您可以使用这些方法基于现有实例创建新的 `geography` 实例。</span><span class="sxs-lookup"><span data-stu-id="763c4-110">The `geography` data type provides numerous built-in methods you can use to create new `geography` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="763c4-111">**在地域周围创建缓冲区**</span><span class="sxs-lookup"><span data-stu-id="763c4-111">**To create a buffer around a geography**</span></span>  
 [<span data-ttu-id="763c4-112">STBuffer（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-112">STBuffer &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 <span data-ttu-id="763c4-113">**在地域周围创建缓冲区，允许公差**</span><span class="sxs-lookup"><span data-stu-id="763c4-113">**To create a buffer around a geography, allowing for a tolerance**</span></span>  
 [<span data-ttu-id="763c4-114">BufferWithTolerance（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-114">BufferWithTolerance &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 <span data-ttu-id="763c4-115">**通过两个地域实例的交集创建地域**</span><span class="sxs-lookup"><span data-stu-id="763c4-115">**To create a geography from the intersection of two geography instances**</span></span>  
 [<span data-ttu-id="763c4-116">STIntersection（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-116">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="763c4-117">**通过两个地域的实例并集创建地域**</span><span class="sxs-lookup"><span data-stu-id="763c4-117">**To create a geography from the union of two geography instances**</span></span>  
 [<span data-ttu-id="763c4-118">STUnion（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-118">STUnion &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 <span data-ttu-id="763c4-119">**通过一个地域中没有与另一个地域发生重叠的点创建地域**</span><span class="sxs-lookup"><span data-stu-id="763c4-119">**To create a geography from the points where one geography does not overlap another**</span></span>  
 [<span data-ttu-id="763c4-120">STDifference（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-120">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="763c4-121">从熟知文本输入构造地域实例</span><span class="sxs-lookup"><span data-stu-id="763c4-121">Constructing a geography Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="763c4-122">`geography` 数据类型提供了若干种用开放地理空间联盟 (OGC) WKT 表示形式生成地域的内置方法。</span><span class="sxs-lookup"><span data-stu-id="763c4-122">The `geography` data type provides several built-in methods that generate a geography from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="763c4-123">WKT 标准是一种允许地域数据以文本形式交换的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="763c4-123">The WKT standard is a text string that allows geography data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="763c4-124">**用 WKT 输入构造任意类型的地域实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-124">**To construct any type of geography instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-125">STGeomFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-125">STGeomFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [<span data-ttu-id="763c4-126">Parse（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-126">Parse &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 <span data-ttu-id="763c4-127">**用 WKT 输入构造地域 Point 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-127">**To construct a geography Point instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-128">STPointFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-128">STPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 <span data-ttu-id="763c4-129">**用 WKT 输入构造地域 MultiPoint 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-129">**To construct a geography MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-130">STMPointFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-130">STMPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 <span data-ttu-id="763c4-131">**用 WKT 输入构造地域 LineString 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-131">**To construct a geography LineString instance from WKT input**</span></span>  
 <span data-ttu-id="763c4-132">STLineFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-132">STLineFromText (geography Data Type)</span></span>  
  
 <span data-ttu-id="763c4-133">**用 WKT 输入构造地域 MultiLineString 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-133">**To construct a geography MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-134">STMLineFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-134">STMLineFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 <span data-ttu-id="763c4-135">**用 WKT 输入构造地域 Polygon 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-135">**To construct a geography Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-136">STPolyFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-136">STPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="763c4-137">**用 WKT 输入构造地域 MultiPolygon 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-137">**To construct a geography MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-138">STMPolyFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-138">STMPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="763c4-139">**用 WKT 输入构造地域 GeometryCollection 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-139">**To construct a geography GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="763c4-140">STGeomCollFromText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-140">STGeomCollFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="763c4-141">从熟知二进制输入构造地域实例</span><span class="sxs-lookup"><span data-stu-id="763c4-141">Constructing a geography Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="763c4-142">WKB 是 OGC 规定的一种二进制格式，该格式允许 `Geography` 数据在客户端应用程序和 SQL 数据库之间进行交换。</span><span class="sxs-lookup"><span data-stu-id="763c4-142">WKB is a binary format specified by the OGC that permits `Geography` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="763c4-143">以下函数接受使用 WKB 输入构造地域实例：</span><span class="sxs-lookup"><span data-stu-id="763c4-143">The following functions accept WKB input to construct geography instances:</span></span>  
  
 <span data-ttu-id="763c4-144">**用 WKB 输入构造任意类型的地域实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-144">**To construct any type of geography instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-145">STGeomFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-145">STGeomFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-146">**用 WKB 输入构造地域 Point 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-146">**To construct a geography Point instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-147">STPointFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-147">STPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-148">**用 WKB 输入构造地域 MultiPoint 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-148">**To construct a geography MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-149">STMPointFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-149">STMPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-150">**用 WKB 输入构造地域 LineString 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-150">**To construct a geography LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-151">STLineFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-151">STLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-152">**用 WKB 输入构造地域 MultiLineString 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-152">**To construct a geography MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-153">STMLineFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-153">STMLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-154">**用 WKB 输入构造地域 Polygon 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-154">**To construct a geography Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-155">STPolyFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-155">STPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-156">**用 WKB 输入构造地域 MultiPolygon 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-156">**To construct a geography MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="763c4-157">STMPolyFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-157">STMPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="763c4-158">**用 WKB 输入构造地域 GeometryCollection 实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-158">**To construct a geography GeometryCollection instance from WKB input**</span></span>  
 <span data-ttu-id="763c4-159">[STGeomCollFromWKB（geography 数据类型）](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type) STGeomCollFromWKB（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-159">[STGeomCollFromWKB &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography Data Type)</span></span>  
  
###  <a name="constructing-a-geography-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="763c4-160">用 GML 文本输入构造地域实例</span><span class="sxs-lookup"><span data-stu-id="763c4-160">Constructing a geography Instance from GML Text Input</span></span>  
 <span data-ttu-id="763c4-161">`geography`数据类型提供了一个方法，该方法可 `geography` 从 GML （实例的 XML 表示形式）生成实例 `geography` 。</span><span class="sxs-lookup"><span data-stu-id="763c4-161">The `geography` data type provides a method that generates a `geography` instance from GML, an XML representation of a `geography` instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="763c4-162">支持部分 GML。</span><span class="sxs-lookup"><span data-stu-id="763c4-162">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="763c4-163">有关地域标记语言的详细信息，请参阅 OGC 规范： [OGC Specifications, Geography Markup Language](https://go.microsoft.com/fwlink/?LinkId=93629)（OGC 规范，地域标记语言）。</span><span class="sxs-lookup"><span data-stu-id="763c4-163">For more information on Geography Markup Language, see the OGC Specification: [OGC Specifications, Geography Markup Language.](https://go.microsoft.com/fwlink/?LinkId=93629)</span></span>  
  
 <span data-ttu-id="763c4-164">**用 GML 输入构造任意类型的地域实例**</span><span class="sxs-lookup"><span data-stu-id="763c4-164">**To construct any type of geography instance from GML input**</span></span>  
 [<span data-ttu-id="763c4-165">GeomFromGML（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-165">GeomFromGML &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geography-instance"></a><a name="returning"></a> <span data-ttu-id="763c4-166">从地域实例返回熟知文本和熟知二进制</span><span class="sxs-lookup"><span data-stu-id="763c4-166">Returning Well-Known Text and Well-Known Binary from a geography Instance</span></span>  
 <span data-ttu-id="763c4-167">可以使用以下方法返回 WKT 或 WKB 格式的 `geography` 实例：</span><span class="sxs-lookup"><span data-stu-id="763c4-167">You can use the following methods to return either the WKT or WKB format of a `geography` instance:</span></span>  
  
 <span data-ttu-id="763c4-168">**返回地域实例的 WKT 表示形式**</span><span class="sxs-lookup"><span data-stu-id="763c4-168">**To return the WKT representation of a geography instance**</span></span>  
 [<span data-ttu-id="763c4-169">STAsText（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-169">STAsText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [<span data-ttu-id="763c4-170">ToString（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-170">ToString &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 <span data-ttu-id="763c4-171">**返回包括任何 Z 值和 M 值的地域实例的 WKT 表示形式**</span><span class="sxs-lookup"><span data-stu-id="763c4-171">**To return the WKT representation of a geography instance including any Z and M values**</span></span>  
 [<span data-ttu-id="763c4-172">AsTextZM（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-172">AsTextZM &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 <span data-ttu-id="763c4-173">**返回地域实例的 WKB 表示形式**</span><span class="sxs-lookup"><span data-stu-id="763c4-173">**To return the WKB representation of a geography instance**</span></span>  
 [<span data-ttu-id="763c4-174">STAsBinary（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-174">STAsBinary &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 <span data-ttu-id="763c4-175">**返回地域实例的 GML 表示形式**</span><span class="sxs-lookup"><span data-stu-id="763c4-175">**To return a GML representation of a geography instance**</span></span>  
 [<span data-ttu-id="763c4-176">AsGml（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-176">AsGml &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="querying-the-properties-and-behaviors-of-geography-instances"></a><a name="query"></a> <span data-ttu-id="763c4-177">查询地域实例的属性和行为</span><span class="sxs-lookup"><span data-stu-id="763c4-177">Querying the Properties and Behaviors of geography Instances</span></span>  
 <span data-ttu-id="763c4-178">所有 `geography` 实例都具有多个可通过提供的方法进行检索的属性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="763c4-178">All `geography` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="763c4-179">下列主题定义了地域类型的属性和行为，并为查询每种图形定义了方法。</span><span class="sxs-lookup"><span data-stu-id="763c4-179">The following topics define the properties and behaviors of geography types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="763c4-180">有效性、实例类型和 GeometryCollection 信息</span><span class="sxs-lookup"><span data-stu-id="763c4-180">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="763c4-181">`geography`构造实例后，可以使用以下方法返回实例类型，或者，如果它是 `GeometryCollection` 实例，则返回特定的 `geography` 实例。</span><span class="sxs-lookup"><span data-stu-id="763c4-181">After a `geography` instance is constructed, you can use the following methods to return the instance type, or if it is a `GeometryCollection` instance, return a specific `geography` instance.</span></span>  
  
 <span data-ttu-id="763c4-182">**返回地域的实例类型**</span><span class="sxs-lookup"><span data-stu-id="763c4-182">**To return the instance type of a geography**</span></span>  
 [<span data-ttu-id="763c4-183">STGeometryType（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-183">STGeometryType &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 <span data-ttu-id="763c4-184">**确定地域是否为给定的实例类型**</span><span class="sxs-lookup"><span data-stu-id="763c4-184">**To determine if a geography is a given instance type**</span></span>  
 [<span data-ttu-id="763c4-185">InstanceOf（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-185">InstanceOf &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 <span data-ttu-id="763c4-186">**确定地域实例对其实例类型而言格式是否正确**</span><span class="sxs-lookup"><span data-stu-id="763c4-186">**To determine if a geography instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="763c4-187">STNumGeometries（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-187">STNumGeometries &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 <span data-ttu-id="763c4-188">**返回 GeometryCollection 实例中的特定地域**</span><span class="sxs-lookup"><span data-stu-id="763c4-188">**To return a specific geography in a GeometryCollection instance**</span></span>  
 <span data-ttu-id="763c4-189">[STGeometryN（geography 数据类型）](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-189">[STGeometryN &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography Data Type)</span></span>  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="763c4-190">点数</span><span class="sxs-lookup"><span data-stu-id="763c4-190">Number of Points</span></span>  
 <span data-ttu-id="763c4-191">所有非空 `geography` 实例都由*点*组成。</span><span class="sxs-lookup"><span data-stu-id="763c4-191">All nonempty `geography` instances are comprised of *points*.</span></span> <span data-ttu-id="763c4-192">这些点表示球体的纬度和经度坐标，在其上可绘制 `geography` 实例。</span><span class="sxs-lookup"><span data-stu-id="763c4-192">These points represent the latitude and longitude coordinates of the earth on which the `geography` instances are drawn.</span></span> <span data-ttu-id="763c4-193">数据类型 `geography` 提供了许多用于查询实例点的内置方法。</span><span class="sxs-lookup"><span data-stu-id="763c4-193">The data type `geography` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="763c4-194">**返回构成实例的点数。**</span><span class="sxs-lookup"><span data-stu-id="763c4-194">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="763c4-195">STNumPoints（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-195">STNumPoints &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 <span data-ttu-id="763c4-196">**返回实例中的特定点**</span><span class="sxs-lookup"><span data-stu-id="763c4-196">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="763c4-197">STPointN（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-197">STPointN &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="763c4-198">**返回实例的起始点**</span><span class="sxs-lookup"><span data-stu-id="763c4-198">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="763c4-199">STStartPoint（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-199">STStartPoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 <span data-ttu-id="763c4-200">**返回实例的终点**</span><span class="sxs-lookup"><span data-stu-id="763c4-200">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="763c4-201">STEndpoint（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-201">STEndpoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="763c4-202">维度</span><span class="sxs-lookup"><span data-stu-id="763c4-202">Dimension</span></span>  
 <span data-ttu-id="763c4-203">非空 `geography` 实例可以为零维、一维或二维。</span><span class="sxs-lookup"><span data-stu-id="763c4-203">A nonempty `geography` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="763c4-204">零维 `geography` 实例（例如 `Point` 和）没有 `MultiPoint` 长度或面积。</span><span class="sxs-lookup"><span data-stu-id="763c4-204">Zero-dimensional `geography` instances, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="763c4-205">一维对象（例如 `LineString, CircularString`、`CompoundCurve` 和 `MultiLineString`）具有长度。</span><span class="sxs-lookup"><span data-stu-id="763c4-205">One-dimensional objects, such as `LineString, CircularString`, `CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="763c4-206">二维实例（如 `Polygon, CurvePolygon` 、和 `MultiPolygon` ）具有面积和长度。</span><span class="sxs-lookup"><span data-stu-id="763c4-206">Two-dimensional instances, such as `Polygon, CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="763c4-207">空实例将报告 -1 维，并且 `GeometryCollection` 报告其内容的最大维度。</span><span class="sxs-lookup"><span data-stu-id="763c4-207">Empty instances report a dimension of -1, and a `GeometryCollection` reports the maximum dimension of its contents.</span></span>  
  
 <span data-ttu-id="763c4-208">**返回实例的维度**</span><span class="sxs-lookup"><span data-stu-id="763c4-208">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="763c4-209">STDimension（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-209">STDimension &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 <span data-ttu-id="763c4-210">**返回实例的长度**</span><span class="sxs-lookup"><span data-stu-id="763c4-210">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="763c4-211">STLength（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-211">STLength &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 <span data-ttu-id="763c4-212">**返回实例的面积**</span><span class="sxs-lookup"><span data-stu-id="763c4-212">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="763c4-213">STArea（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-213">STArea &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="763c4-214">Empty</span><span class="sxs-lookup"><span data-stu-id="763c4-214">Empty</span></span>  
 <span data-ttu-id="763c4-215">*空* `geography` 实例不包含任何点。</span><span class="sxs-lookup"><span data-stu-id="763c4-215">An *empty*`geography` instance does not have any points.</span></span> <span data-ttu-id="763c4-216">空的 `LineString, CircularString`、`CompoundCurve` 和 `MultiLineString` 实例的长度为 0。</span><span class="sxs-lookup"><span data-stu-id="763c4-216">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is 0.</span></span> <span data-ttu-id="763c4-217">空的 `Polygon, CurvePolygon` 和 `MultiPolygon` 实例的面积为 0。</span><span class="sxs-lookup"><span data-stu-id="763c4-217">The area of empty `Polygon, CurvePolygon` and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="763c4-218">**确定实例是否为空**</span><span class="sxs-lookup"><span data-stu-id="763c4-218">**To determine if an instance is empty**</span></span>  
 [<span data-ttu-id="763c4-219">STIsEmpty（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-219">STIsEmpty &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="763c4-220">闭合</span><span class="sxs-lookup"><span data-stu-id="763c4-220">Closure</span></span>  
 <span data-ttu-id="763c4-221">*闭合*的 `geography` 实例是一个图形，其起点和终点是相同的。</span><span class="sxs-lookup"><span data-stu-id="763c4-221">A *closed*`geography` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="763c4-222">`Polygon` 实例被视为闭合的。</span><span class="sxs-lookup"><span data-stu-id="763c4-222">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="763c4-223">`Point` 实例不是闭合的。</span><span class="sxs-lookup"><span data-stu-id="763c4-223">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="763c4-224">环是一个简单、闭合的 `LineString` 实例。</span><span class="sxs-lookup"><span data-stu-id="763c4-224">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="763c4-225">**确定实例是否闭合**</span><span class="sxs-lookup"><span data-stu-id="763c4-225">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="763c4-226">STIsClosed（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-226">STIsClosed &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 <span data-ttu-id="763c4-227">**返回多边形实例的环数**</span><span class="sxs-lookup"><span data-stu-id="763c4-227">**To return the number of rings in a Polygon instance**</span></span>  
 [<span data-ttu-id="763c4-228">NumRings（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-228">NumRings &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 <span data-ttu-id="763c4-229">**返回地域实例的指定环**</span><span class="sxs-lookup"><span data-stu-id="763c4-229">**To return a specified ring of a geography instance**</span></span>  
 [<span data-ttu-id="763c4-230">RingN（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-230">RingN &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="763c4-231">空间引用标识符 (SRID)</span><span class="sxs-lookup"><span data-stu-id="763c4-231">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="763c4-232">空间引用标识符 (SRID) 是指定 `geography` 实例所在的椭球坐标系的标识符。</span><span class="sxs-lookup"><span data-stu-id="763c4-232">The spatial reference ID (SRID) is an identifier specifying which ellipsoidal coordinate system the `geography` instance is represented in.</span></span> <span data-ttu-id="763c4-233">两个拥有不同 SRID 的 `geography` 实例是不可比的。</span><span class="sxs-lookup"><span data-stu-id="763c4-233">Two `geography` instances with different SRIDs cannot be compared.</span></span>  
  
 <span data-ttu-id="763c4-234">**设置或返回实例的 SRID**</span><span class="sxs-lookup"><span data-stu-id="763c4-234">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="763c4-235">STSrid（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-235">STSrid &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 <span data-ttu-id="763c4-236">此属性可以进行修改。</span><span class="sxs-lookup"><span data-stu-id="763c4-236">This property can be modified.</span></span>  
  
##  <a name="determining-relationships-between-geography-instances"></a><a name="rel"></a> <span data-ttu-id="763c4-237">确定地域实例之间的关系</span><span class="sxs-lookup"><span data-stu-id="763c4-237">Determining Relationships between geography Instances</span></span>  
 <span data-ttu-id="763c4-238">`geography` 数据类型提供了许多内置方法，您可以使用这些方法确定两个 `geography` 实例之间的关系。</span><span class="sxs-lookup"><span data-stu-id="763c4-238">The `geography` data type provides many built-in methods you can use to determine relationships between two `geography` instances.</span></span>  
  
 <span data-ttu-id="763c4-239">**确定两个实例是否包含相同的点集**</span><span class="sxs-lookup"><span data-stu-id="763c4-239">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="763c4-240">STEquals（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-240">STEquals &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="763c4-241">**确定两个实例是否不相接**</span><span class="sxs-lookup"><span data-stu-id="763c4-241">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="763c4-242">STDisjoint（geometry 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-242">STDisjoint &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="763c4-243">**确定两个实例是否相交**</span><span class="sxs-lookup"><span data-stu-id="763c4-243">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="763c4-244">STIntersects（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-244">STIntersects &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="763c4-245">**确定两个实例的交点**</span><span class="sxs-lookup"><span data-stu-id="763c4-245">**To determine the point or points where two instances intersect**</span></span>  
 [<span data-ttu-id="763c4-246">STIntersection（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-246">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="763c4-247">**确定两个地域实例中点之间的最短距离**</span><span class="sxs-lookup"><span data-stu-id="763c4-247">**To determine the shortest distance between points in two geography instances**</span></span>  
 [<span data-ttu-id="763c4-248">STDistance（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-248">STDistance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 <span data-ttu-id="763c4-249">**确定两个地域实例之间点的不同**</span><span class="sxs-lookup"><span data-stu-id="763c4-249">**To determine the difference in points between two geography instances**</span></span>  
 [<span data-ttu-id="763c4-250">STDifference（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-250">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 <span data-ttu-id="763c4-251">**派生一个地域实例相比于另一个地域实例的余集或唯一点**</span><span class="sxs-lookup"><span data-stu-id="763c4-251">**To derive the symmetric difference, or unique points, of one geography instance compared with another instance**</span></span>  
 [<span data-ttu-id="763c4-252">STSymDifference（geography 数据类型）</span><span class="sxs-lookup"><span data-stu-id="763c4-252">STSymDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="geography-instances-must-use-supported-srid"></a><a name="supportedsrid"></a> <span data-ttu-id="763c4-253">地域实例必须使用支持的 SRID</span><span class="sxs-lookup"><span data-stu-id="763c4-253">geography Instances Must Use Supported SRID</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="763c4-254">支持基于 EPSG 标准的 SRID。</span><span class="sxs-lookup"><span data-stu-id="763c4-254">supports SRIDs based on the EPSG standards.</span></span> <span data-ttu-id="763c4-255">必须使用 `geography` 实例的支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 SRID 执行计算或将方法用于地域空间数据。</span><span class="sxs-lookup"><span data-stu-id="763c4-255">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-supported SRID for `geography` instances must be used when performing calculations or using methods with geography spatial data.</span></span> <span data-ttu-id="763c4-256">SRID 必须与 **sys.spatial_reference_systems** 目录视图中显示的 SRID 中的一个匹配。</span><span class="sxs-lookup"><span data-stu-id="763c4-256">The SRID must match one of the SRIDs displayed in the **sys.spatial_reference_systems** catalog view.</span></span> <span data-ttu-id="763c4-257">如前所述，在使用 `geography` 数据类型对空间数据执行计算时，结果将取决于在创建数据时使用的是哪个椭圆体，因为为每个椭圆体都分配了一个特定空间引用标识符 (SRID)。</span><span class="sxs-lookup"><span data-stu-id="763c4-257">As mentioned previously, when you perform calculations on your spatial data using the `geography` data type, your results will depend on which ellipsoid was used in the creation of your data, as each ellipsoid is assigned a specific spatial reference identifier (SRID).</span></span>  
  
 <span data-ttu-id="763c4-258">对 `geography` 实例使用方法时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用等于 4326 的默认 SRID，它将映射到 WGS 84 空间引用系统。</span><span class="sxs-lookup"><span data-stu-id="763c4-258">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the default SRID of 4326, which maps to the WGS 84 spatial reference system, when using methods on `geography` instances.</span></span> <span data-ttu-id="763c4-259">如果要使用 WGS 84（或 SRID 4326）之外的某个空间引用系统中的数据，您需要确定地域空间数据的特定 SRID。</span><span class="sxs-lookup"><span data-stu-id="763c4-259">If you use data from a spatial reference system other than WGS 84 (or SRID 4326), you will need to determine the specific SRID for your geography spatial data.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="763c4-260">示例</span><span class="sxs-lookup"><span data-stu-id="763c4-260">Examples</span></span>  
 <span data-ttu-id="763c4-261">以下示例说明如何添加和查询地理数据。</span><span class="sxs-lookup"><span data-stu-id="763c4-261">The following examples show how to add and query geography data.</span></span>  
  
-   <span data-ttu-id="763c4-262">第一个示例创建了带有标识列和 `geography` 列 `GeogCol1`的表。</span><span class="sxs-lookup"><span data-stu-id="763c4-262">The first example creates a table with an identity column and a `geography` column `GeogCol1`.</span></span> <span data-ttu-id="763c4-263">第三列将 `geography` 列呈现为其开放地理空间信息联盟 (OGC) 熟知文本 (WKT) 表示形式，并使用 `STAsText()` 方法。</span><span class="sxs-lookup"><span data-stu-id="763c4-263">A third column renders the `geography` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="763c4-264">接下来将插入两行：一行包含 `LineString` 类型的 `geography`实例，一行包含 `Polygon` 实例。</span><span class="sxs-lookup"><span data-stu-id="763c4-264">Two rows are then inserted: one row contains a `LineString` instance of `geography`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   <span data-ttu-id="763c4-265">第二个示例使用 `STIntersection()` 方法返回此前插入的两个 `geography` 实例相交的点。</span><span class="sxs-lookup"><span data-stu-id="763c4-265">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geography` instances intersect.</span></span>  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="763c4-266">另请参阅</span><span class="sxs-lookup"><span data-stu-id="763c4-266">See Also</span></span>  
 [<span data-ttu-id="763c4-267">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="763c4-267">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
