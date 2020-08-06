---
title: 建立性能基线 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0cb85ae8ad370b816c6240b58aabd247c7593c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687783"
---
# <a name="establish-a-performance-baseline"></a><span data-ttu-id="8b4ff-102">建立性能基线</span><span class="sxs-lookup"><span data-stu-id="8b4ff-102">Establish a Performance Baseline</span></span>
  <span data-ttu-id="8b4ff-103">若要确定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统是否以最佳状态执行，可以定期进行性能度量（即使没有发生问题）以建立一条服务器性能基线。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-103">To determine whether your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system is performing optimally, take performance measurements at regular intervals over time, even when no problems occur, to establish a server performance baseline.</span></span> <span data-ttu-id="8b4ff-104">将每组新的度量值与以前取得的度量值进行比较。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-104">Compare each new set of measurements with those taken earlier.</span></span>  
  
 <span data-ttu-id="8b4ff-105">下列方面会影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的性能：</span><span class="sxs-lookup"><span data-stu-id="8b4ff-105">The following areas affect the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="8b4ff-106">系统资源（硬件）</span><span class="sxs-lookup"><span data-stu-id="8b4ff-106">System resources (hardware)</span></span>  
  
-   <span data-ttu-id="8b4ff-107">网络体系结构</span><span class="sxs-lookup"><span data-stu-id="8b4ff-107">Network architecture</span></span>  
  
-   <span data-ttu-id="8b4ff-108">操作系统</span><span class="sxs-lookup"><span data-stu-id="8b4ff-108">The operating system</span></span>  
  
-   <span data-ttu-id="8b4ff-109">数据库应用程序</span><span class="sxs-lookup"><span data-stu-id="8b4ff-109">Database applications</span></span>  
  
-   <span data-ttu-id="8b4ff-110">客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="8b4ff-110">Client applications</span></span>  
  
 <span data-ttu-id="8b4ff-111">至少，使用基线度量值确定：</span><span class="sxs-lookup"><span data-stu-id="8b4ff-111">At a minimum, use baseline measurements to determine:</span></span>  
  
-   <span data-ttu-id="8b4ff-112">操作的峰值时间和非峰值时间。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-112">Peak and off-peak hours of operation.</span></span>  
  
-   <span data-ttu-id="8b4ff-113">生产查询或批处理命令响应时间。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-113">Production-query or batch-command response times.</span></span>  
  
-   <span data-ttu-id="8b4ff-114">数据库备份和还原所需时间。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-114">Database backup and restore completion times.</span></span>  
  
 <span data-ttu-id="8b4ff-115">建立服务器性能基线后，将基线统计与当前服务器性能进行比较。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-115">After you establish a server performance baseline, compare the baseline statistics to current server performance.</span></span> <span data-ttu-id="8b4ff-116">对远高于或远低于基线的数字需要做进一步调查。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-116">Numbers far above or far below your baseline are candidates for further investigation.</span></span> <span data-ttu-id="8b4ff-117">它们可能表明有需要调整或重新配置的区域。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-117">They may indicate areas in need of tuning or reconfiguration.</span></span> <span data-ttu-id="8b4ff-118">例如，如果执行一组查询的时间增加，检查这些查询以确定能否重新编写它们，或者是否必须添加列统计信息或新索引。</span><span class="sxs-lookup"><span data-stu-id="8b4ff-118">For example, if the amount of time to execute a set of queries increases, examine the queries to determine if they can be rewritten, or if column statistics or new indexes must be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b4ff-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b4ff-119">See Also</span></span>  
 [<span data-ttu-id="8b4ff-120">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b4ff-120">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
