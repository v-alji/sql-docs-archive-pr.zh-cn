---
title: 分析 ODBC 驱动程序性能操作指南主题 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: rothja
ms.author: jroth
ms.openlocfilehash: d27547862138b511a4defaa3cae80f48f69fdc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577621"
---
# <a name="profiling-odbc-driver-performance-how-to-topics-odbc"></a><span data-ttu-id="d623f-102">对 ODBC 驱动程序性能进行事件探查的操作指南主题 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d623f-102">Profiling ODBC Driver Performance How-to Topics (ODBC)</span></span>
  <span data-ttu-id="d623f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驱动程序有两个特定于驱动程序的选项，用于对驱动程序的性能进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="d623f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver has two driver-specific options for profiling the performance of the driver.</span></span>  
  
 <span data-ttu-id="d623f-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC 驱动程序可以记录文件中的性能统计信息。</span><span class="sxs-lookup"><span data-stu-id="d623f-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver can log performance statistics in file.</span></span> <span data-ttu-id="d623f-105">日志文件是以制表符分隔的文件，它可以在支持以制表符分隔的文件（比如 Microsoft Excel）的任何电子表格中进行分析。</span><span class="sxs-lookup"><span data-stu-id="d623f-105">The log file is a tab-delimited file that can be analyzed in any spreadsheet supporting tab-delimited files, such as Microsoft Excel.</span></span>  
  
 <span data-ttu-id="d623f-106">驱动程序也可以记录长时间运行的查询（在指定长度的时间内未从服务器获得响应的查询）。</span><span class="sxs-lookup"><span data-stu-id="d623f-106">The driver can also log long-running queries (queries that do not get a response from the server in a specified length of time).</span></span> <span data-ttu-id="d623f-107">这些查询可以随后由程序员和数据库管理员进行分析。</span><span class="sxs-lookup"><span data-stu-id="d623f-107">These queries can later be analyzed by programmers and database administrators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d623f-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="d623f-108">In This Section</span></span>  
  
-   [<span data-ttu-id="d623f-109">&#40;ODBC&#41;的配置文件驱动程序性能数据</span><span class="sxs-lookup"><span data-stu-id="d623f-109">Profile Driver Performance Data &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data.md)  
  
-   [<span data-ttu-id="d623f-110">&#40;ODBC&#41;记录长时间运行的查询</span><span class="sxs-lookup"><span data-stu-id="d623f-110">Log Long-Running Queries &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a><span data-ttu-id="d623f-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d623f-111">See Also</span></span>  
 [<span data-ttu-id="d623f-112">ODBC 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="d623f-112">ODBC How-to Topics</span></span>](odbc-how-to-topics.md)  
  
  
