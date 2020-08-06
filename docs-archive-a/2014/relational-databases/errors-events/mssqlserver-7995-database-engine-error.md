---
title: MSSQLSERVER_7995 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7995 (Database Engine error)
ms.assetid: af6d6322-3cba-43d8-be97-e6ef15f8c933
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c65cf2b16c4d7a0dcf40272f8280205a111d08e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587391"
---
# <a name="mssqlserver_7995"></a><span data-ttu-id="52376-102">MSSQLSERVER_7995</span><span class="sxs-lookup"><span data-stu-id="52376-102">MSSQLSERVER_7995</span></span>
    
## <a name="details"></a><span data-ttu-id="52376-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="52376-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52376-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="52376-104">Product Name</span></span>|<span data-ttu-id="52376-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="52376-105">SQL Server</span></span>|  
|<span data-ttu-id="52376-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="52376-106">Event ID</span></span>|<span data-ttu-id="52376-107">7995</span><span class="sxs-lookup"><span data-stu-id="52376-107">7995</span></span>|  
|<span data-ttu-id="52376-108">事件源</span><span class="sxs-lookup"><span data-stu-id="52376-108">Event Source</span></span>|<span data-ttu-id="52376-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="52376-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="52376-110">组件</span><span class="sxs-lookup"><span data-stu-id="52376-110">Component</span></span>|<span data-ttu-id="52376-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="52376-111">SQLEngine</span></span>|  
|<span data-ttu-id="52376-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="52376-112">Symbolic Name</span></span>|<span data-ttu-id="52376-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="52376-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span></span>|  
|<span data-ttu-id="52376-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="52376-114">Message Text</span></span>|<span data-ttu-id="52376-115">数据库 'DBNAME'：系统目录中存在一致性错误，无法进一步处理 DBCC CHECKNAME。</span><span class="sxs-lookup"><span data-stu-id="52376-115">Database 'DBNAME': consistency errors in system catalogs prevent further DBCC CHECKNAME processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="52376-116">说明</span><span class="sxs-lookup"><span data-stu-id="52376-116">Explanation</span></span>  
 <span data-ttu-id="52376-117">DBCC CHECKDB 进程包含以下三个阶段：</span><span class="sxs-lookup"><span data-stu-id="52376-117">The DBCC CHECKDB process consists of the following three stages:</span></span>  
  
1.  <span data-ttu-id="52376-118">分配检查。</span><span class="sxs-lookup"><span data-stu-id="52376-118">Allocation checks.</span></span> <span data-ttu-id="52376-119">这等效于运行 DBCC CHECKALLOC。</span><span class="sxs-lookup"><span data-stu-id="52376-119">This is equivalent to running DBCC CHECKALLOC.</span></span>  
  
2.  <span data-ttu-id="52376-120">系统表一致性检查。</span><span class="sxs-lookup"><span data-stu-id="52376-120">System tables consistency checks.</span></span> <span data-ttu-id="52376-121">这等效于对所需系统基表的小列表运行 DBCC CHECKTABLE。</span><span class="sxs-lookup"><span data-stu-id="52376-121">This is equivalent to running DBCC CHECKTABLE on a small list of necessary system base tables.</span></span>  
  
3.  <span data-ttu-id="52376-122">完成数据库一致性检查。</span><span class="sxs-lookup"><span data-stu-id="52376-122">Complete database consistency checks.</span></span>  
  
 <span data-ttu-id="52376-123">MSSQLEngine_7995 在第 2 阶段中引发，指示 DBCC CHECKDB 找到该命令无法修复的错误或者尚未指定 REPAIR。</span><span class="sxs-lookup"><span data-stu-id="52376-123">MSSQLEngine_7995 is raised in stage 2 to indicate that DBCC CHECKDB has found errors that the command cannot repair or that REPAIR has not been specified.</span></span> <span data-ttu-id="52376-124">DBCC CHECKDB 无法继续执行第 3 阶段，因为相关的系统基表存储数据库中所有对象的元数据，或者系统基表已损坏。</span><span class="sxs-lookup"><span data-stu-id="52376-124">DBCC CHECKDB cannot continue with stage 3 because either the system base tables in question store the metadata for all objects in the database or the system base tables are corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52376-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="52376-125">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="52376-126">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="52376-126">Look for Hardware Failure</span></span>  
 <span data-ttu-id="52376-127">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="52376-127">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="52376-128">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="52376-128">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="52376-129">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="52376-129">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="52376-130">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="52376-130">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="52376-131">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="52376-131">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="52376-132">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="52376-132">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="52376-133">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="52376-133">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="52376-134">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="52376-134">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="52376-135">从备份还原</span><span class="sxs-lookup"><span data-stu-id="52376-135">Restore from Backup</span></span>  
 <span data-ttu-id="52376-136">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="52376-136">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="52376-137">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="52376-137">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="52376-138">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="52376-138">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="52376-139">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="52376-139">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="52376-140">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="52376-140">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="52376-141">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="52376-141">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="52376-142">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="52376-142">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="52376-143">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="52376-143">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="52376-144">检查错误列表以查看 REPAIR 将对每个错误执行的操作。</span><span class="sxs-lookup"><span data-stu-id="52376-144">Examine the list of errors to see what REPAIR will do for each.</span></span>  
  
  
