---
title: MSSQLSERVER_2534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 409c429f961cd8357bfa2e40663c33f3c1f2e36d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589620"
---
# <a name="mssqlserver_2534"></a><span data-ttu-id="847cd-102">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="847cd-102">MSSQLSERVER_2534</span></span>
    
## <a name="details"></a><span data-ttu-id="847cd-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="847cd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="847cd-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="847cd-104">Product Name</span></span>|<span data-ttu-id="847cd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="847cd-105">SQL Server</span></span>|  
|<span data-ttu-id="847cd-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="847cd-106">Event ID</span></span>|<span data-ttu-id="847cd-107">2534</span><span class="sxs-lookup"><span data-stu-id="847cd-107">2534</span></span>|  
|<span data-ttu-id="847cd-108">事件源</span><span class="sxs-lookup"><span data-stu-id="847cd-108">Event Source</span></span>|<span data-ttu-id="847cd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="847cd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="847cd-110">组件</span><span class="sxs-lookup"><span data-stu-id="847cd-110">Component</span></span>|<span data-ttu-id="847cd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="847cd-111">SQLEngine</span></span>|  
|<span data-ttu-id="847cd-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="847cd-112">Symbolic Name</span></span>|<span data-ttu-id="847cd-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="847cd-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span></span>|  
|<span data-ttu-id="847cd-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="847cd-114">Message Text</span></span>|<span data-ttu-id="847cd-115">表错误:页 P_ID 的页头表明它已分配给对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE），但是实际上分配给了另一对象。</span><span class="sxs-lookup"><span data-stu-id="847cd-115">Table error: Page P_ID, whose header indicates it as being allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), is allocated by another object.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="847cd-116">说明</span><span class="sxs-lookup"><span data-stu-id="847cd-116">Explanation</span></span>  
 <span data-ttu-id="847cd-117">页头包含分配单元 ID *A_ID*，但该分配单元的索引分配映射 (IAM) 页都未分配该页。</span><span class="sxs-lookup"><span data-stu-id="847cd-117">The header of the page contains the allocation unit ID, *A_ID*, but none of the Index Allocation Map (IAM) pages of that allocation unit allocates the page.</span></span> <span data-ttu-id="847cd-118">因此，页头包含错误的分配单元 ID，而且该页还将具有一个匹配的 MSSQLServer_2533 错误，对应于实际分配该页的分配单元 ID。</span><span class="sxs-lookup"><span data-stu-id="847cd-118">Therefore, the header of the page contains the wrong allocation unit ID, and the page will have a matching MSSQLServer_2533 error that corresponds to the allocation unit ID to which the page is actually allocated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="847cd-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="847cd-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="847cd-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="847cd-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="847cd-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="847cd-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="847cd-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="847cd-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="847cd-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="847cd-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="847cd-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="847cd-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="847cd-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="847cd-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="847cd-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="847cd-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="847cd-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="847cd-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="847cd-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="847cd-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="847cd-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="847cd-129">Restore from Backup</span></span>  
 <span data-ttu-id="847cd-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="847cd-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="847cd-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="847cd-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="847cd-132">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="847cd-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="847cd-133">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="847cd-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="847cd-134">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="847cd-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="847cd-135">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="847cd-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="847cd-136">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="847cd-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="847cd-137">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="847cd-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="847cd-138">如果索引存在，则 REPAIR 将重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="847cd-138">REPAIR will rebuild the index if an index exists.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="847cd-139">对匹配的 [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) 错误运行 REPAIR 将在重新生成之前释放页。</span><span class="sxs-lookup"><span data-stu-id="847cd-139">Running REPAIR for the matching [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) error deallocates the page before the rebuild.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="847cd-140">此修复可能会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="847cd-140">This repair may cause data loss.</span></span>  
  
  
