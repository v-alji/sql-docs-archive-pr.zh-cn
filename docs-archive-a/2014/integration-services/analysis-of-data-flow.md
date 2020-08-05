---
title: 数据流分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 184b53d3e982cd80d7c9c0909538a751585ae21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579722"
---
# <a name="analysis-of-data-flow"></a><span data-ttu-id="a4d54-102">数据流分析</span><span class="sxs-lookup"><span data-stu-id="a4d54-102">Analysis of Data Flow</span></span>
  <span data-ttu-id="a4d54-103">您可以使用[catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` 数据库视图来分析包的数据流。</span><span class="sxs-lookup"><span data-stu-id="a4d54-103">You can use the [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md)`SSISDB` database view to analyze the data flow of packages.</span></span> <span data-ttu-id="a4d54-104">此视图在每当数据流组件将数据发送到下游组件时显示一行。</span><span class="sxs-lookup"><span data-stu-id="a4d54-104">This view displays a row each time a data flow component sends data to a downstream component.</span></span> <span data-ttu-id="a4d54-105">这些信息可用来进一步了解发送到每个组件的行。</span><span class="sxs-lookup"><span data-stu-id="a4d54-105">The information can be used to gain a deeper understanding of the rows that are sent to each component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4d54-106">日志记录级别必须设置为“详细”  ，才能通过 catalog.execution_data_statistics 视图捕获信息。</span><span class="sxs-lookup"><span data-stu-id="a4d54-106">The logging level must be set to **Verbose** in order to capture information with the catalog.execution_data_statistics view.</span></span>  
  
 <span data-ttu-id="a4d54-107">以下示例显示在包的组件之间发送的行数。</span><span class="sxs-lookup"><span data-stu-id="a4d54-107">The following example displays the number of rows sent between components of a package.</span></span>  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 <span data-ttu-id="a4d54-108">以下示例计算每个组件针对特定的执行每毫秒所发送的行数。</span><span class="sxs-lookup"><span data-stu-id="a4d54-108">The following example calculates the number of rows per millisecond sent by each component for a specific execution.</span></span> <span data-ttu-id="a4d54-109">计算的值为：</span><span class="sxs-lookup"><span data-stu-id="a4d54-109">The calculated values are:</span></span>  
  
-   <span data-ttu-id="a4d54-110">**total_rows** - 组件发送的所有行的总和</span><span class="sxs-lookup"><span data-stu-id="a4d54-110">**total_rows** - the sum of all the rows sent by the component</span></span>  
  
-   <span data-ttu-id="a4d54-111">**wall_clock_time_ms** - 每个组件已使用的执行总时间（以毫秒为单位）</span><span class="sxs-lookup"><span data-stu-id="a4d54-111">**wall_clock_time_ms** - the total elapsed execution time, in milliseconds, for each component</span></span>  
  
-   <span data-ttu-id="a4d54-112">**num_rows_per_millisecond** - 每个组件每毫秒发送的行数</span><span class="sxs-lookup"><span data-stu-id="a4d54-112">**num_rows_per_millisecond** - the number of rows per millisecond sent by each component</span></span>  
  
 <span data-ttu-id="a4d54-113">`HAVING`子句用于防止在计算中出现被零除错误。</span><span class="sxs-lookup"><span data-stu-id="a4d54-113">The `HAVING` clause is used to prevent a divide-by-zero error in the calculations.</span></span>  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="a4d54-114">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a4d54-114">Related Tasks</span></span>  
 [<span data-ttu-id="a4d54-115">调试数据流</span><span class="sxs-lookup"><span data-stu-id="a4d54-115">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="a4d54-116">包执行的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="a4d54-116">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4d54-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4d54-117">See Also</span></span>  
 [<span data-ttu-id="a4d54-118">数据流中的数据</span><span class="sxs-lookup"><span data-stu-id="a4d54-118">Data in Data Flows</span></span>](data-flow/data-in-data-flows.md)  
  
  
