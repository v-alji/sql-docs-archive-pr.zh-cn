---
title: SQL Server Profiler 源表-数据库引擎优化顾问-选择工作负荷表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d10899c01df8e7fbc7ee45d108841a18d3248500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580860"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a><span data-ttu-id="fbc8a-102">SQL Server Profiler 源表-数据库引擎优化顾问-选择工作负荷表</span><span class="sxs-lookup"><span data-stu-id="fbc8a-102">SQL Server Profiler - Source Table-Database Engine Tuning Advisor - Select Workload Table</span></span>
  <span data-ttu-id="fbc8a-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]和 [!INCLUDE[ssDE](../includes/ssde-md.md)]优化顾问使用此对话框来选择表。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] and [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor use this dialog box to select tables.</span></span>  
  
 <span data-ttu-id="fbc8a-104">在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 中，使用\*\*\*\*“源表”对话框为跟踪表指定源表。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-104">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use the **Source Table** dialog box to specify a source table for a trace table.</span></span> <span data-ttu-id="fbc8a-105">源表是一个加载跟踪的表，重播跟踪时需要查看或使用其内容。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-105">This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.</span></span>  
  
 <span data-ttu-id="fbc8a-106">在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 优化顾问中，使用\*\*\*\*“选择工作负荷表”对话框选择包含 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 跟踪信息的数据库表，以用作优化工作负荷或在开始优化分析前预览表的内容。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-106">In [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor, use the **Select Workload Table** dialog box to select a database table that contains [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information to use as a tuning workload, or to preview the table contents before starting tuning analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fbc8a-107">选项</span><span class="sxs-lookup"><span data-stu-id="fbc8a-107">Options</span></span>  
 <span data-ttu-id="fbc8a-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fbc8a-108">**SQL Server**</span></span>  
 <span data-ttu-id="fbc8a-109">指定当前连接的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-109">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] currently connected.</span></span> <span data-ttu-id="fbc8a-110">此字段将自动填充，并且无法更新。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-110">This field is populated automatically and cannot be updated.</span></span>  
  
 <span data-ttu-id="fbc8a-111">**Database**</span><span class="sxs-lookup"><span data-stu-id="fbc8a-111">**Database**</span></span>  
 <span data-ttu-id="fbc8a-112">指定跟踪表所在的数据库。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-112">Specify the database where the trace table is located.</span></span>  
  
 <span data-ttu-id="fbc8a-113">**所有者**</span><span class="sxs-lookup"><span data-stu-id="fbc8a-113">**Owner**</span></span>  
 <span data-ttu-id="fbc8a-114">Specifies the owner of the trace table.</span><span class="sxs-lookup"><span data-stu-id="fbc8a-114">Specifies the owner of the trace table.</span></span> <span data-ttu-id="fbc8a-115">此字段将自动填充为 **dbo**。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-115">This field is populated automatically as **dbo**.</span></span>  
  
 <span data-ttu-id="fbc8a-116">**表**</span><span class="sxs-lookup"><span data-stu-id="fbc8a-116">**Table**</span></span>  
 <span data-ttu-id="fbc8a-117">指定将从中读取跟踪的跟踪表的名称。</span><span class="sxs-lookup"><span data-stu-id="fbc8a-117">Specify the name of the trace table from which the trace should be read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc8a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbc8a-118">See Also</span></span>  
 <span data-ttu-id="fbc8a-119">[将跟踪结果保存到表 (SQL Server Profiler)](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="fbc8a-119">[Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="fbc8a-120">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="fbc8a-120">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="fbc8a-121">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="fbc8a-121">Database Engine Tuning Advisor</span></span>](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
