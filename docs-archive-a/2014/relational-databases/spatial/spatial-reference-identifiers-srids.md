---
title: 空间引用标识符 (SRID) | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 15db59b43731b9a39ff4bef78e3a6cb6929e9b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587754"
---
# <a name="spatial-reference-identifiers-srids"></a><span data-ttu-id="dc366-102">空间引用标识符 (SRID)</span><span class="sxs-lookup"><span data-stu-id="dc366-102">Spatial Reference Identifiers (SRIDs)</span></span>
  <span data-ttu-id="dc366-103">每个空间实例都有一个空间引用标识符 (SRID)。</span><span class="sxs-lookup"><span data-stu-id="dc366-103">Each spatial instance has a spatial reference identifier (SRID).</span></span> <span data-ttu-id="dc366-104">SRID 对应于基于特定椭圆体的空间引用系统，可用于平面球体映射或圆球映射。</span><span class="sxs-lookup"><span data-stu-id="dc366-104">The SRID corresponds to a spatial reference system based on the specific ellipsoid used for either flat-earth mapping or round-earth mapping.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dc366-105"> 有关 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引入的空间功能的详细说明和示例（包括新 SRID），请下载白皮书 [SQL Server 2012 中的新空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。</span><span class="sxs-lookup"><span data-stu-id="dc366-105">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including a new SRID, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="dc366-106">空间列可包含具有不同 SRID 的对象。</span><span class="sxs-lookup"><span data-stu-id="dc366-106">A spatial column can contain objects with different SRIDs.</span></span> <span data-ttu-id="dc366-107">然而，在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空间数据方法对数据执行操作时，仅可使用具有相同 SRID 的空间实例。</span><span class="sxs-lookup"><span data-stu-id="dc366-107">However, only spatial instances with the same SRID can be used when performing operations with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data methods on your data.</span></span> <span data-ttu-id="dc366-108">从两个空间数据实例派生的任何空间方法的结果仅在这两个实例具有相同的 SRID（该 SRID 基于相同的用于确定实例坐标的度量单位、数据和投影）时才有效。</span><span class="sxs-lookup"><span data-stu-id="dc366-108">The result of any spatial method derived from two spatial data instances is valid only if those instances have the same SRID that is based on the same unit of measurement, datum, and projection used to determine the coordinates of the instances.</span></span> <span data-ttu-id="dc366-109">SRID 最常见的度量单位为米或平方米。</span><span class="sxs-lookup"><span data-stu-id="dc366-109">The most common units of measurement of a SRID are meters or square meters.</span></span>  
  
 <span data-ttu-id="dc366-110">如果两个空间实例的 SRID 不相同，则对这两个实例使用 `geometry` 或 `geography` 数据类型方法后的结果将返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="dc366-110">If two spatial instances do not have the same SRID, the results from a `geometry` or `geography` Data Type method used on the instances will return NULL.</span></span> <span data-ttu-id="dc366-111">例如，若要以下谓词返回非 NULL 结果，两个 `geometry` 实例（`geometry1` 和 `geometry2`）必须具有相同的 SRID：</span><span class="sxs-lookup"><span data-stu-id="dc366-111">For example, for the following predicate term to return a non-NULL result, the two `geometry` instances, `geometry1` and `geometry2`, must have the same SRID:</span></span>  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  <span data-ttu-id="dc366-112">空间引用标识系统是由 [欧洲石油测绘组 (European Petroleum Survey Group, EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) 的标准定义的，它是为绘图、测绘以及大地测量数据存储而开发的一组标准。</span><span class="sxs-lookup"><span data-stu-id="dc366-112">The spatial reference identification system is defined by the [European Petroleum Survey Group (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) standard, which is a set of standards developed for cartography, surveying, and geodetic data storage.</span></span> <span data-ttu-id="dc366-113">该标准归石油天然气生产商 (OGP) 测绘和定位委员会所有。</span><span class="sxs-lookup"><span data-stu-id="dc366-113">This standard is owned by the Oil and Gas Producers (OGP) Surveying and Positioning Committee.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc366-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc366-114">See Also</span></span>  
 [<span data-ttu-id="dc366-115">空间数据类型概述</span><span class="sxs-lookup"><span data-stu-id="dc366-115">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
