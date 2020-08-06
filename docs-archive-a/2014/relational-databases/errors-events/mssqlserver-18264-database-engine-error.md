---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3edfeb82601e254c02df87cc4a978b9ab5e653e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587843"
---
# <a name="mssqlserver_18264"></a><span data-ttu-id="107d2-102">MSSQLSERVER_18264</span><span class="sxs-lookup"><span data-stu-id="107d2-102">MSSQLSERVER_18264</span></span>
    
## <a name="details"></a><span data-ttu-id="107d2-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="107d2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="107d2-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="107d2-104">Product Name</span></span>|<span data-ttu-id="107d2-105">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="107d2-105">Microsoft SQL Server</span></span>|  
|<span data-ttu-id="107d2-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="107d2-106">Event ID</span></span>|<span data-ttu-id="107d2-107">18264</span><span class="sxs-lookup"><span data-stu-id="107d2-107">18264</span></span>|  
|<span data-ttu-id="107d2-108">事件源</span><span class="sxs-lookup"><span data-stu-id="107d2-108">Event Source</span></span>|<span data-ttu-id="107d2-109">MSSQLENGINE</span><span class="sxs-lookup"><span data-stu-id="107d2-109">MSSQLENGINE</span></span>|  
|<span data-ttu-id="107d2-110">组件</span><span class="sxs-lookup"><span data-stu-id="107d2-110">Component</span></span>|<span data-ttu-id="107d2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="107d2-111">SQLEngine</span></span>|  
|<span data-ttu-id="107d2-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="107d2-112">Symbolic Name</span></span>|<span data-ttu-id="107d2-113">STRMIO_DBDUMP</span><span class="sxs-lookup"><span data-stu-id="107d2-113">STRMIO_DBDUMP</span></span>|  
|<span data-ttu-id="107d2-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="107d2-114">Message Text</span></span>|<span data-ttu-id="107d2-115">数据库已备份。</span><span class="sxs-lookup"><span data-stu-id="107d2-115">Database backed up.</span></span> <span data-ttu-id="107d2-116">数据库: %s，创建日期(时间): %s(%s)，转储的页数: %d，第一个 LSN: %s，最后一个 LSN: %s，转储设备数: %d，设备信息: (%s)。</span><span class="sxs-lookup"><span data-stu-id="107d2-116">Database: %s, creation date(time): %s(%s), pages dumped: %d, first LSN: %s, last LSN: %s, number of dump devices: %d, device information: (%s).</span></span> <span data-ttu-id="107d2-117">这只是一条信息性消息。</span><span class="sxs-lookup"><span data-stu-id="107d2-117">This is an informational message only.</span></span> <span data-ttu-id="107d2-118">不需要任何用户操作。</span><span class="sxs-lookup"><span data-stu-id="107d2-118">No user action is required.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="107d2-119">说明</span><span class="sxs-lookup"><span data-stu-id="107d2-119">Explanation</span></span>  
 <span data-ttu-id="107d2-120">默认情况下，每个成功的备份操作都会将该信息性消息添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和系统事件日志中。</span><span class="sxs-lookup"><span data-stu-id="107d2-120">By default, every successful backup adds this informational message to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the system event log.</span></span> <span data-ttu-id="107d2-121">如果非常频繁地备份事务日志，这些消息会迅速累积，从而产生一个巨大的错误日志，这样会使查找其他消息变得非常困难。</span><span class="sxs-lookup"><span data-stu-id="107d2-121">If you very frequently back up the transaction log, these messages can accumulate quickly, creating very large error logs that can make finding other messages difficult.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="107d2-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="107d2-122">User Action</span></span>  
 <span data-ttu-id="107d2-123">可以通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 跟踪标志 **3226** 来禁止显示这些日志条目。</span><span class="sxs-lookup"><span data-stu-id="107d2-123">You can suppress these log entries by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace flag **3226**.</span></span> <span data-ttu-id="107d2-124">如果您频繁地运行日志备份，而且没有任何脚本依赖于这些条目，则启用该跟踪标志非常有用。</span><span class="sxs-lookup"><span data-stu-id="107d2-124">Enabling this trace flag is useful if you are running frequent log backups and if none of your scripts depend on those entries.</span></span>  
  
 <span data-ttu-id="107d2-125">有关使用跟踪标志的信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="107d2-125">For information about using trace flags, see SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107d2-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="107d2-126">See Also</span></span>  
 [<span data-ttu-id="107d2-127">跟踪标志 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="107d2-127">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
