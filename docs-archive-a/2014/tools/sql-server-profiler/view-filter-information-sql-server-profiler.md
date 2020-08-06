---
title: 查看 (SQL Server Profiler) 的筛选器信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 931b83f8087d446cfc7b08d9582cbad5b02cf671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579930"
---
# <a name="view-filter-information-sql-server-profiler"></a><span data-ttu-id="8ec12-102">查看筛选器信息 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="8ec12-102">View Filter Information (SQL Server Profiler)</span></span>
  <span data-ttu-id="8ec12-103">本主题介绍了如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]查看数据列的事件类筛选器。</span><span class="sxs-lookup"><span data-stu-id="8ec12-103">This topic describes how to view filters on data columns for event classes by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-view-filter-information"></a><span data-ttu-id="8ec12-104">查看筛选器信息</span><span class="sxs-lookup"><span data-stu-id="8ec12-104">To view filter information</span></span>  
  
1.  <span data-ttu-id="8ec12-105">打开跟踪文件、跟踪表或 SQL 脚本，在 **“文件”** 菜单上，单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="8ec12-105">Open a trace file, trace table, or SQL script, and on the **File** menu, click **Properties**.</span></span> <span data-ttu-id="8ec12-106">如果要编辑跟踪模板或创建新跟踪，请跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="8ec12-106">If you are editing a trace template or creating a new trace, skip this step.</span></span>  
  
2.  <span data-ttu-id="8ec12-107">在“事件选择”选项卡上，右键单击要查看的筛选器的数据列名称，然后单击“编辑列筛选器”。</span><span class="sxs-lookup"><span data-stu-id="8ec12-107">On the **Events Selection** tab, right-click the data column name for the filter you want to view, and click **Edit Column Filter**.</span></span>  
  
3.  <span data-ttu-id="8ec12-108">在 **“编辑筛选器”** 对话框中，展开筛选器比较运算符以查看为指定的标准分配的值。</span><span class="sxs-lookup"><span data-stu-id="8ec12-108">In the **Edit Filter** dialog box, expand the filter comparison operators to see the assigned value for the specified criterion.</span></span> <span data-ttu-id="8ec12-109">对要查看筛选器信息的所有列，重复步骤 2 和步骤 3。</span><span class="sxs-lookup"><span data-stu-id="8ec12-109">Repeat Steps 2 and 3 for all columns for which you want to view filter information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ec12-110">具有分配值的比较运算符显示为粗体格式。</span><span class="sxs-lookup"><span data-stu-id="8ec12-110">Comparison operators with assigned values are formatted bold.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec12-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ec12-111">See Also</span></span>  
 [<span data-ttu-id="8ec12-112">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8ec12-112">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
