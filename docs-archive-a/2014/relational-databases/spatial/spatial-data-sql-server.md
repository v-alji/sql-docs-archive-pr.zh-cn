---
title: 空间数据 (SQL Server) | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4d491420a9eca7c35b89b254a03381c6467c834c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590652"
---
# <a name="spatial-data-sql-server"></a><span data-ttu-id="b1f75-102">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b1f75-102">Spatial Data (SQL Server)</span></span>
  <span data-ttu-id="b1f75-103">空间数据表示有关物理位置和几何对象形状的信息。</span><span class="sxs-lookup"><span data-stu-id="b1f75-103">Spatial data represents information about the physical location and shape of geometric objects.</span></span> <span data-ttu-id="b1f75-104">这些对象可能是点位置或更复杂的对象，例如国家/地区、道路或湖泊。</span><span class="sxs-lookup"><span data-stu-id="b1f75-104">These objects can be point locations or more complex objects such as countries, roads, or lakes.</span></span>  
  
 <span data-ttu-id="b1f75-105"> 支持两种空间数据类型： 数据类型和  数据类型。</span><span class="sxs-lookup"><span data-stu-id="b1f75-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports two spatial data types: the `geometry` data type and the `geography` data type.</span></span>  
  
-   <span data-ttu-id="b1f75-106"> 类型表示欧几里得（平面）坐标系中的数据。</span><span class="sxs-lookup"><span data-stu-id="b1f75-106">The `geometry` type represents data in a Euclidean (flat) coordinate system.</span></span>  
  
-   <span data-ttu-id="b1f75-107">`geography` 类型表示圆形地球坐标系中的数据。</span><span class="sxs-lookup"><span data-stu-id="b1f75-107">The `geography` type represents data in a round-earth coordinate system.</span></span>  
  
 <span data-ttu-id="b1f75-108">这两种数据类型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中都是作为 .NET 公共语言运行时 (CLR) 数据类型实现的。</span><span class="sxs-lookup"><span data-stu-id="b1f75-108">Both data types are implemented as .NET common language runtime (CLR) data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1f75-109">有关 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引入的空间功能的详细说明和示例，请下载白皮书 [SQL Server 2012 中的新空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="b1f75-109">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="b1f75-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="b1f75-110">Related Tasks</span></span>  
 [<span data-ttu-id="b1f75-111">创建、构造和查询几何图形实例</span><span class="sxs-lookup"><span data-stu-id="b1f75-111">Create, Construct, and Query geometry Instances</span></span>](create-construct-and-query-geometry-instances.md)  
 <span data-ttu-id="b1f75-112">介绍可用于 geometry 数据类型实例的方法。</span><span class="sxs-lookup"><span data-stu-id="b1f75-112">Describes the methods that you can use with instances of the geometry data type.</span></span>  
  
 [<span data-ttu-id="b1f75-113">创建、构造和查询地理实例</span><span class="sxs-lookup"><span data-stu-id="b1f75-113">Create, Construct, and Query geography Instances</span></span>](create-construct-and-query-geography-instances.md)  
 <span data-ttu-id="b1f75-114">介绍可用于 geography 数据类型实例的方法。</span><span class="sxs-lookup"><span data-stu-id="b1f75-114">Describes the methods that you can use with instances of the geography data type.</span></span>  
  
 [<span data-ttu-id="b1f75-115">为 Nearest Neighbor 查询空间数据</span><span class="sxs-lookup"><span data-stu-id="b1f75-115">Query Spatial Data for Nearest Neighbor</span></span>](query-spatial-data-for-nearest-neighbor.md)  
 <span data-ttu-id="b1f75-116">介绍用于查找与特定的空间对象最接近的空间对象的常见查询模式。</span><span class="sxs-lookup"><span data-stu-id="b1f75-116">Describes the common query pattern that is used to find the closest spatial objects to a specific spatial object.</span></span>  
  
 [<span data-ttu-id="b1f75-117">创建、修改和删除空间索引</span><span class="sxs-lookup"><span data-stu-id="b1f75-117">Create, Modify, and Drop Spatial Indexes</span></span>](create-modify-and-drop-spatial-indexes.md)  
 <span data-ttu-id="b1f75-118">提供有关创建、更改和删除空间索引的信息。</span><span class="sxs-lookup"><span data-stu-id="b1f75-118">Provides information about creating, altering, and dropping a spatial index.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b1f75-119">相关内容</span><span class="sxs-lookup"><span data-stu-id="b1f75-119">Related Content</span></span>  
 [<span data-ttu-id="b1f75-120">空间数据类型概述</span><span class="sxs-lookup"><span data-stu-id="b1f75-120">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
 <span data-ttu-id="b1f75-121">介绍空间数据类型。</span><span class="sxs-lookup"><span data-stu-id="b1f75-121">Introduces the spatial data types.</span></span>  
  
-   [<span data-ttu-id="b1f75-122">Point</span><span class="sxs-lookup"><span data-stu-id="b1f75-122">Point</span></span>](point.md)  
  
-   [<span data-ttu-id="b1f75-123">LineString</span><span class="sxs-lookup"><span data-stu-id="b1f75-123">LineString</span></span>](linestring.md)  
  
-   [<span data-ttu-id="b1f75-124">CircularString</span><span class="sxs-lookup"><span data-stu-id="b1f75-124">CircularString</span></span>](circularstring.md)  
  
-   [<span data-ttu-id="b1f75-125">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="b1f75-125">CompoundCurve</span></span>](compoundcurve.md)  
  
-   [<span data-ttu-id="b1f75-126">多边形</span><span class="sxs-lookup"><span data-stu-id="b1f75-126">Polygon</span></span>](polygon.md)  
  
-   [<span data-ttu-id="b1f75-127">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="b1f75-127">CurvePolygon</span></span>](curvepolygon.md)  
  
-   [<span data-ttu-id="b1f75-128">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="b1f75-128">MultiPoint</span></span>](multipoint.md)  
  
-   [<span data-ttu-id="b1f75-129">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="b1f75-129">MultiLineString</span></span>](multilinestring.md)  
  
-   [<span data-ttu-id="b1f75-130">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="b1f75-130">MultiPolygon</span></span>](multipolygon.md)  
  
-   [<span data-ttu-id="b1f75-131">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="b1f75-131">GeometryCollection</span></span>](geometrycollection.md)  
  
 [<span data-ttu-id="b1f75-132">空间索引概述</span><span class="sxs-lookup"><span data-stu-id="b1f75-132">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
 <span data-ttu-id="b1f75-133">介绍空间索引并描述分割和分割方案。</span><span class="sxs-lookup"><span data-stu-id="b1f75-133">Introduces spatial indexes and describes tessellation and tessellation schemes.</span></span>  
  
  
