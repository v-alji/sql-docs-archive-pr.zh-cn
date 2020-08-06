---
title: 隔离性能问题 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b42d780a8174ab57d00de72e8b00ef7af0abc17e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689878"
---
# <a name="isolate-performance-problems"></a><span data-ttu-id="9a2e9-102">隔离性能问题</span><span class="sxs-lookup"><span data-stu-id="9a2e9-102">Isolate Performance Problems</span></span>
  <span data-ttu-id="9a2e9-103">在一般情况下，同时使用多个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Microsoft Windows 工具比一次只用一个工具隔离数据库性能问题更有效。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-103">It is often more effective to use several [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Microsoft Windows tools together to isolate database performance problems than to use one tool at a time.</span></span> <span data-ttu-id="9a2e9-104">例如，图形执行计划功能（也称为“显示计划”）可以迅速识别单个查询中的死锁。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-104">For example, the graphical Execution Plan feature, also called Showplan, helps you quickly recognize deadlocks in a single query.</span></span> <span data-ttu-id="9a2e9-105">然而，如果同时使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 的监视功能，将更容易识别某些其他性能问题。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-105">However, you can recognize some other performance problems more easily if you use the monitoring features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows together.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="9a2e9-106">可用来监视和解决 Transact-SQL 问题以及与应用程序有关的问题。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-106">can be used to monitor and troubleshoot Transact-SQL and application-related problems.</span></span> <span data-ttu-id="9a2e9-107">可以使用系统监视器监视硬件问题和其他与系统有关的问题。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-107">System Monitor can be used to monitor hardware and other system-related problems.</span></span>  
  
 <span data-ttu-id="9a2e9-108">可以监视下列方面以解决问题：</span><span class="sxs-lookup"><span data-stu-id="9a2e9-108">You can monitor the following areas to troubleshoot problems:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9a2e9-109">存储过程或用户应用程序提交的批处理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-109">stored procedures or batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted by user applications.</span></span>  
  
-   <span data-ttu-id="9a2e9-110">用户活动（如阻塞锁或死锁）。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-110">User activity, such as blocking locks or deadlocks.</span></span>  
  
-   <span data-ttu-id="9a2e9-111">硬件活动（如磁盘使用）。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-111">Hardware activity, such as disk usage.</span></span>  
  
 <span data-ttu-id="9a2e9-112">问题可以包括：</span><span class="sxs-lookup"><span data-stu-id="9a2e9-112">Problems can include:</span></span>  
  
-   <span data-ttu-id="9a2e9-113">应用程序开发错误（包括错误编写 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句）。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-113">Application development errors involving incorrectly written [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="9a2e9-114">硬件错误（如磁盘错误或与网络有关的错误）。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-114">Hardware errors, such as disk- or network-related errors.</span></span>  
  
-   <span data-ttu-id="9a2e9-115">由于数据库设计不正确导致的过多阻塞。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-115">Excessive blocking due to an incorrectly designed database.</span></span>  
  
## <a name="tools-for-common-performance-problems"></a><span data-ttu-id="9a2e9-116">用于解决常见性能问题的工具</span><span class="sxs-lookup"><span data-stu-id="9a2e9-116">Tools for Common Performance Problems</span></span>  
 <span data-ttu-id="9a2e9-117">仔细选择您希望每个工具监视或优化的性能问题同样重要。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-117">Equally important is careful selection of the performance problem that you want each tool to monitor or tune.</span></span> <span data-ttu-id="9a2e9-118">所选的工具和实用工具取决于您要解决的性能问题的类型。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-118">The tool and the utility depend on the type of performance problem you want to resolve.</span></span>  
  
 <span data-ttu-id="9a2e9-119">以下主题将介绍各种监视和优化工具及它们可以解决的问题。</span><span class="sxs-lookup"><span data-stu-id="9a2e9-119">The following topics describe a variety of monitoring and tuning tools and the problems they uncover.</span></span>  
  
 [<span data-ttu-id="9a2e9-120">识别瓶颈</span><span class="sxs-lookup"><span data-stu-id="9a2e9-120">Identify Bottlenecks</span></span>](identify-bottlenecks.md)  
  
 [<span data-ttu-id="9a2e9-121">监视内存用量</span><span class="sxs-lookup"><span data-stu-id="9a2e9-121">Monitor Memory Usage</span></span>](../performance-monitor/monitor-memory-usage.md)  
  
  
