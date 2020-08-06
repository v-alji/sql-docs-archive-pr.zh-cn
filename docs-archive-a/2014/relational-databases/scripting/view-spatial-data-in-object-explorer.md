---
title: 在对象资源管理器中查看空间数据
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 881adf69ee83ee4b7536afae0b190fbec90f132c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587320"
---
# <a name="view-spatial-data-in-object-explorer"></a><span data-ttu-id="75edb-102">在对象资源管理器中查看空间数据</span><span class="sxs-lookup"><span data-stu-id="75edb-102">View Spatial Data in Object Explorer</span></span>
  <span data-ttu-id="75edb-103">查询编辑器中的 **“空间结果”** 窗口中提供了一些可视化工具，可用来查看空间数据结果以及在 **“结果”** 窗口中以网格格式显示的数据。</span><span class="sxs-lookup"><span data-stu-id="75edb-103">The **Spatial results** window in Query Editor provides visual mapping tools for viewing spatial data results in addition to the data displayed in grid format in the **Results** window.</span></span> <span data-ttu-id="75edb-104">若要在 **“空间结果”** 窗口中显示空间数据，则查询结果中必须至少包括一个包含几何图形或地域数据的空间数据列。</span><span class="sxs-lookup"><span data-stu-id="75edb-104">To display spatial data in the **Spatial Results** window, your query results must contain at least one spatial data column with either geometry or geography data.</span></span>  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a><span data-ttu-id="75edb-105">在“空间结果”窗口中查看空间数据</span><span class="sxs-lookup"><span data-stu-id="75edb-105">To view spatial data in the Spatial results window</span></span>  
  
1.  <span data-ttu-id="75edb-106">在查询编辑器中单击 **“空间结果”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="75edb-106">In Query Editor, click the **Spatial results** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="75edb-107">如果查询结果中不包含空间数据或者指定将结果作为文本返回，则此窗口不可用。</span><span class="sxs-lookup"><span data-stu-id="75edb-107">This window is not available if your query results do not contain spatial data or if you specify that your results are returned as text.</span></span>  
  
2.  <span data-ttu-id="75edb-108">从 **“选择空间列”** 列表中选择要查看的列。</span><span class="sxs-lookup"><span data-stu-id="75edb-108">Select the column you want to view from the **Select spatial column** list.</span></span> <span data-ttu-id="75edb-109">如果表中只有一个空间列，则此列是列表中的默认选项。</span><span class="sxs-lookup"><span data-stu-id="75edb-109">If there is only one spatial column in your table, this column is the default option in the list.</span></span>  
  
3.  <span data-ttu-id="75edb-110">从“选择标签列”  列表中选择要用作数据标签的非空间列。</span><span class="sxs-lookup"><span data-stu-id="75edb-110">Select the non-spatial column you want to use as data labels from the **Select label columns** list.</span></span>  
  
4.  <span data-ttu-id="75edb-111">从 **“选择投影”** 列表中选择地域数据所需的投影。</span><span class="sxs-lookup"><span data-stu-id="75edb-111">Select the projection you want for geography data from the **Select projection** list.</span></span> <span data-ttu-id="75edb-112">默认投影为 Equirectangular；其他可用投影为 Mercator、Robinson 或 Bonne。</span><span class="sxs-lookup"><span data-stu-id="75edb-112">The default projection is Equirectangular; other projections available are Mercator, Robinson, or Bonne.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="75edb-113">如果空间列中包含几何图形数据，则“选择投影”  不可用。</span><span class="sxs-lookup"><span data-stu-id="75edb-113">**Select projection** is not available if your spatial column contains geometry data.</span></span>  
  
5.  <span data-ttu-id="75edb-114">调整 **“缩放”** 滑块可增加映射元素的可视大小。</span><span class="sxs-lookup"><span data-stu-id="75edb-114">Adjust the **Zoom** slider to increase the visual size of mapped elements.</span></span> <span data-ttu-id="75edb-115">对于多边形形状，仅当形状大到能够容纳标签文本时，标签才可见。</span><span class="sxs-lookup"><span data-stu-id="75edb-115">For polygon shapes, the label is visible only when the shape is large enough to hold the label text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75edb-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75edb-116">See Also</span></span>  
 <span data-ttu-id="75edb-117">[“空间结果”窗口](spatial-results-window.md) </span><span class="sxs-lookup"><span data-stu-id="75edb-117">[Spatial Results Window](spatial-results-window.md) </span></span>  
 <span data-ttu-id="75edb-118">[数据库引擎查询编辑器 (SQL Server Management Studio)](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="75edb-118">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="75edb-119">查询和文本编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="75edb-119">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
