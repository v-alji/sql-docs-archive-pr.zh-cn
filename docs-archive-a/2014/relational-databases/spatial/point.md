---
title: Point | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4b12069d84e00738e3ddac8c414f33903f4f0999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590657"
---
# <a name="point"></a><span data-ttu-id="f543b-102">Point</span><span class="sxs-lookup"><span data-stu-id="f543b-102">Point</span></span>
  <span data-ttu-id="f543b-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空间数据中，`Point` 是表示单个位置的零维对象，可能包含 Z（仰角）和 M（度量）值。</span><span class="sxs-lookup"><span data-stu-id="f543b-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data, a `Point` is a 0-dimensional object representing a single location and may contain Z (elevation) and M (measure) values.</span></span>  
  
## <a name="geography-data-type"></a><span data-ttu-id="f543b-104">Geography 数据类型</span><span class="sxs-lookup"><span data-stu-id="f543b-104">Geography Data Type</span></span>  
 <span data-ttu-id="f543b-105">Geography 数据类型的 Point 类型表示单个位置，其中 *Lat* 表示纬度， *Long* 表示经度。</span><span class="sxs-lookup"><span data-stu-id="f543b-105">The Point type for the geography data type represents a single location where *Lat* represents latitude and *Long* represents longitude.</span></span> <span data-ttu-id="f543b-106">维度和经度值以度数进行衡量。</span><span class="sxs-lookup"><span data-stu-id="f543b-106">The values for latitude and longitude are measured in degrees.</span></span> <span data-ttu-id="f543b-107">纬度值始终处于间隔 [-90, 90] 内，如果输入的值超出此范围，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="f543b-107">Values for latitude always lie in the interval [-90, 90], and values that are inputted outside this range will throw an exception.</span></span> <span data-ttu-id="f543b-108">经度值始终处于间隔 (-180, 180] 内，如果输入的值超出此范围，将对值进行回绕以便适合此范围。</span><span class="sxs-lookup"><span data-stu-id="f543b-108">Values for longitude always lie in the interval (-180, 180], and values inputted outside this range are wrapped around to fit in this range.</span></span> <span data-ttu-id="f543b-109">例如，如果为经度值输入 190，则该值将被回绕到值 -170。</span><span class="sxs-lookup"><span data-stu-id="f543b-109">For example, if 190 is inputted for longitude, then it will be wrapped to the value -170.</span></span> <span data-ttu-id="f543b-110">*SRID* 表示您希望返回的 **geography** 实例的空间引用 ID。</span><span class="sxs-lookup"><span data-stu-id="f543b-110">*SRID* represents the spatial reference ID of the **geography** instance that you wish to return.</span></span>  
  
## <a name="geometry-data-type"></a><span data-ttu-id="f543b-111">Geometry 数据类型</span><span class="sxs-lookup"><span data-stu-id="f543b-111">Geometry Data Type</span></span>  
 <span data-ttu-id="f543b-112">Geometry 数据类型的 Point 类型表示单个位置，其中 *X* 表示要生成的点的 X 坐标， *Y* 表示要生成的点的 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="f543b-112">The Point type for the geometry data type represents a single location where *X* represents the X-coordinate of the Point being generated and *Y* represents the Y-coordinate of the Point being generated.</span></span> <span data-ttu-id="f543b-113">*SRID* 表示您希望返回的 **geometry** 实例的空间引用 ID。</span><span class="sxs-lookup"><span data-stu-id="f543b-113">*SRID* represents the spatial reference ID of the **geometry** instance that you wish to return.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f543b-114">示例</span><span class="sxs-lookup"><span data-stu-id="f543b-114">Examples</span></span>  
 <span data-ttu-id="f543b-115">下面的示例创建一个表示点 (3, 4) 的 `geometry Point`实例，该实例的 SRID 为 0。</span><span class="sxs-lookup"><span data-stu-id="f543b-115">The following example creates a `geometry Point`instance representing the point (3, 4) with an SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 <span data-ttu-id="f543b-116">下一个示例创建一个表示点 (3, 4) 的 `geometry``Point` 实例，该实例的 Z（仰角）值为 7，M（度量）值为 2.5，默认 SRID 为 0。</span><span class="sxs-lookup"><span data-stu-id="f543b-116">The next example creates a `geometry``Point` instance representing the point (3, 4) with a Z (elevation) value of 7, an M (measure) value of 2.5, and the default SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 <span data-ttu-id="f543b-117">最后一个示例返回 `geometry``Point` 实例的 X、Y、Z 和 M 值。</span><span class="sxs-lookup"><span data-stu-id="f543b-117">The final example returns the X, Y, Z, and M values for the `geometry``Point` instance.</span></span>  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 <span data-ttu-id="f543b-118">Z 和 M 值可以显式指定为 NULL，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="f543b-118">Z and M values may be explicitly specified as NULL, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a><span data-ttu-id="f543b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f543b-119">See Also</span></span>  
 <span data-ttu-id="f543b-120">[单](multipoint.md) </span><span class="sxs-lookup"><span data-stu-id="f543b-120">[MultiPoint](multipoint.md) </span></span>  
 <span data-ttu-id="f543b-121">[STX &#40;geometry 数据类型&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="f543b-121">[STX &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span></span>  
 <span data-ttu-id="f543b-122">[STY（geometry 数据类型）](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="f543b-122">[STY &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span></span>  
 [<span data-ttu-id="f543b-123">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f543b-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
