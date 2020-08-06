---
title: MSSQLSERVER_7984 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7984 (Database Engine error)
ms.assetid: e3192f56-e4e2-41da-b132-65f1e7540b1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7f92fe4f3751621e0cc636ffcd2d4de73b348d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589123"
---
# <a name="mssqlserver_7984"></a><span data-ttu-id="720c1-102">MSSQLSERVER_7984</span><span class="sxs-lookup"><span data-stu-id="720c1-102">MSSQLSERVER_7984</span></span>
    
## <a name="details"></a><span data-ttu-id="720c1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="720c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="720c1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="720c1-104">Product Name</span></span>|<span data-ttu-id="720c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="720c1-105">SQL Server</span></span>|  
|<span data-ttu-id="720c1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="720c1-106">Event ID</span></span>|<span data-ttu-id="720c1-107">7984</span><span class="sxs-lookup"><span data-stu-id="720c1-107">7984</span></span>|  
|<span data-ttu-id="720c1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="720c1-108">Event Source</span></span>|<span data-ttu-id="720c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="720c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="720c1-110">组件</span><span class="sxs-lookup"><span data-stu-id="720c1-110">Component</span></span>|<span data-ttu-id="720c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="720c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="720c1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="720c1-112">Symbolic Name</span></span>|<span data-ttu-id="720c1-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span><span class="sxs-lookup"><span data-stu-id="720c1-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span></span>|  
|<span data-ttu-id="720c1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="720c1-114">Message Text</span></span>|<span data-ttu-id="720c1-115">系统表预检查:对象 ID O_ID。</span><span class="sxs-lookup"><span data-stu-id="720c1-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="720c1-116">页 P_ID 具有意外的页类型 PAGETYPE。</span><span class="sxs-lookup"><span data-stu-id="720c1-116">Page P_ID has unexpected page type PAGETYPE.</span></span> <span data-ttu-id="720c1-117">由于不可修复的错误，Check 语句已终止。</span><span class="sxs-lookup"><span data-stu-id="720c1-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="720c1-118">说明</span><span class="sxs-lookup"><span data-stu-id="720c1-118">Explanation</span></span>  
 <span data-ttu-id="720c1-119">在指定对象的数据级别中找到了类型不是 DATA_PAGE 的页。</span><span class="sxs-lookup"><span data-stu-id="720c1-119">A page with a type other than DATA_PAGE was found in the data level of the specified object.</span></span> <span data-ttu-id="720c1-120">在 DBCC CHECKDB 命令检查的第一个阶段中引发了此错误。</span><span class="sxs-lookup"><span data-stu-id="720c1-120">This error is raised during the first phase of the DBCC CHECKDB command checks.</span></span> <span data-ttu-id="720c1-121">在此阶段中，DBCC CHECKDB 对关键系统基表的数据页执行简单检查。</span><span class="sxs-lookup"><span data-stu-id="720c1-121">During this phase, DBCC CHECKDB performs primitive checks on the data pages of critical system base tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="720c1-122">如果在系统表中找到任何错误，则无法修复这些错误；因此，DBCC CHECKDB 命令将立即结束。</span><span class="sxs-lookup"><span data-stu-id="720c1-122">If any errors are found in the system tables, the errors cannot be repaired; therefore, the DBCC CHECKDB command ends immediately.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="720c1-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="720c1-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="720c1-124">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="720c1-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="720c1-125">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="720c1-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="720c1-126">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="720c1-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="720c1-127">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="720c1-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="720c1-128">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="720c1-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="720c1-129">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="720c1-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="720c1-130">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="720c1-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="720c1-131">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="720c1-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="720c1-132">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="720c1-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="720c1-133">从备份还原</span><span class="sxs-lookup"><span data-stu-id="720c1-133">Restore from Backup</span></span>  
 <span data-ttu-id="720c1-134">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="720c1-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="720c1-135">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="720c1-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="720c1-136">不适用。</span><span class="sxs-lookup"><span data-stu-id="720c1-136">Not applicable.</span></span> <span data-ttu-id="720c1-137">此错误无法自动修复。</span><span class="sxs-lookup"><span data-stu-id="720c1-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="720c1-138">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="720c1-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
