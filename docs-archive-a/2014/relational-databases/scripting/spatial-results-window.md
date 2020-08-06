---
title: “空间结果”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e018ec9f016dfc51ed1bb055ba94abf12bc878f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694430"
---
# <a name="spatial-results-window"></a><span data-ttu-id="54a6e-102">“空间结果”窗口</span><span class="sxs-lookup"><span data-stu-id="54a6e-102">Spatial Results Window</span></span>
  <span data-ttu-id="54a6e-103">**“空间结果”** 窗口提供了用于查看空间数据的可视化映射工具。</span><span class="sxs-lookup"><span data-stu-id="54a6e-103">The **Spatial results** window provides visual mapping tools for viewing spatial data.</span></span> <span data-ttu-id="54a6e-104">若要查看空间结果，查询结果中必须包括一个包含几何图形或地域数据的空间列。</span><span class="sxs-lookup"><span data-stu-id="54a6e-104">To view spatial results, your query results must include a spatial column with either geometry or geography data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54a6e-105">仅当结果返回到 **“结果”** 窗口中的某个网格时， **“空间结果”** 窗口才可用。</span><span class="sxs-lookup"><span data-stu-id="54a6e-105">The **Spatial results** window is only available if your results are returned to a grid in the **Results** window.</span></span> <span data-ttu-id="54a6e-106">如果指定将结果作为文本返回，则此窗口不可用。</span><span class="sxs-lookup"><span data-stu-id="54a6e-106">If you specify that your results are returned as text, this window is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="54a6e-107">选项</span><span class="sxs-lookup"><span data-stu-id="54a6e-107">Options</span></span>  
 <span data-ttu-id="54a6e-108">**选择空间列**</span><span class="sxs-lookup"><span data-stu-id="54a6e-108">**Select spatial column**</span></span>  
 <span data-ttu-id="54a6e-109">在查询结果中，从空间列指定要查看的空间列。</span><span class="sxs-lookup"><span data-stu-id="54a6e-109">Specify the spatial column you want to view from the spatial columns in the query results.</span></span> <span data-ttu-id="54a6e-110">一次只能选择一个列。</span><span class="sxs-lookup"><span data-stu-id="54a6e-110">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="54a6e-111">**选择标签列**</span><span class="sxs-lookup"><span data-stu-id="54a6e-111">**Select label column**</span></span>  
 <span data-ttu-id="54a6e-112">在查询结果中，从返回的列指定要标记空间数据的非空间列。</span><span class="sxs-lookup"><span data-stu-id="54a6e-112">Specify the non-spatial column from the columns returned in the query results to label the spatial data.</span></span> <span data-ttu-id="54a6e-113">一次只能选择一个列。</span><span class="sxs-lookup"><span data-stu-id="54a6e-113">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="54a6e-114">如果某个查询中仅返回了点实例，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="54a6e-114">This option is not available when only point instances are returned in a query.</span></span>  
  
 <span data-ttu-id="54a6e-115">**选择投影**</span><span class="sxs-lookup"><span data-stu-id="54a6e-115">**Select projection**</span></span>  
 <span data-ttu-id="54a6e-116">在下面的一个投影中显示地域数据：Equirectangular、Mercator、Robinson 或 Bonne。</span><span class="sxs-lookup"><span data-stu-id="54a6e-116">Display geography data in one of four projections: Equirectangular, Mercator, Robinson, or Bonne.</span></span>  
  
 <span data-ttu-id="54a6e-117">此选项不适用于几何图形数据。</span><span class="sxs-lookup"><span data-stu-id="54a6e-117">This option is not available for geometry data.</span></span>  
  
 <span data-ttu-id="54a6e-118">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="54a6e-118">**Zoom**</span></span>  
 <span data-ttu-id="54a6e-119">按指数比例调整映射显示。</span><span class="sxs-lookup"><span data-stu-id="54a6e-119">Adjust the map display on an exponential scale.</span></span>  
  
 <span data-ttu-id="54a6e-120">**显示网格线**</span><span class="sxs-lookup"><span data-stu-id="54a6e-120">**Show grid lines**</span></span>  
 <span data-ttu-id="54a6e-121">打开或关闭坐标网格线。</span><span class="sxs-lookup"><span data-stu-id="54a6e-121">Toggle coordinate gridlines on or off.</span></span>  
  
 <span data-ttu-id="54a6e-122">对于多边形形状，仅当形状大到能够容纳标签文本时，才显示标签。</span><span class="sxs-lookup"><span data-stu-id="54a6e-122">For polygon shapes, the label is displayed only when the shape is large enough to hold the label text.</span></span> <span data-ttu-id="54a6e-123">若要显示小形状的标签，请调整缩放比例。</span><span class="sxs-lookup"><span data-stu-id="54a6e-123">To display labels for small shapes, adjust the zoom.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54a6e-124">不能标记点实例。</span><span class="sxs-lookup"><span data-stu-id="54a6e-124">Point instances cannot be labeled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a6e-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54a6e-125">See Also</span></span>  
 <span data-ttu-id="54a6e-126">[在对象资源管理器中查看空间数据](view-spatial-data-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="54a6e-126">[View Spatial Data in Object Explorer](view-spatial-data-in-object-explorer.md) </span></span>  
 <span data-ttu-id="54a6e-127">[空间数据 (SQL Server)](../spatial/spatial-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="54a6e-127">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span></span>  
 <span data-ttu-id="54a6e-128">[数据库引擎查询编辑器 (SQL Server Management Studio)](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="54a6e-128">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="54a6e-129">查询和文本编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="54a6e-129">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
