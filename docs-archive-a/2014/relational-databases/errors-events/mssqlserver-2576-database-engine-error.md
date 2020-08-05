---
title: MSSQLSERVER_2576 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2576 (Database Engine error)
ms.assetid: b727cc2f-c76c-46f8-bbbe-5e7a05a6eabf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f378051c7844bf08d617db56666d69b22ecf732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580277"
---
# <a name="mssqlserver_2576"></a><span data-ttu-id="e40b7-102">MSSQLSERVER_2576</span><span class="sxs-lookup"><span data-stu-id="e40b7-102">MSSQLSERVER_2576</span></span>
    
## <a name="details"></a><span data-ttu-id="e40b7-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="e40b7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e40b7-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e40b7-104">Product Name</span></span>|<span data-ttu-id="e40b7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e40b7-105">SQL Server</span></span>|  
|<span data-ttu-id="e40b7-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e40b7-106">Event ID</span></span>|<span data-ttu-id="e40b7-107">2576</span><span class="sxs-lookup"><span data-stu-id="e40b7-107">2576</span></span>|  
|<span data-ttu-id="e40b7-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e40b7-108">Event Source</span></span>|<span data-ttu-id="e40b7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e40b7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e40b7-110">组件</span><span class="sxs-lookup"><span data-stu-id="e40b7-110">Component</span></span>|<span data-ttu-id="e40b7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e40b7-111">SQLEngine</span></span>|  
|<span data-ttu-id="e40b7-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="e40b7-112">Symbolic Name</span></span>|<span data-ttu-id="e40b7-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="e40b7-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="e40b7-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="e40b7-114">Message Text</span></span>|<span data-ttu-id="e40b7-115">位于对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）中的上一个指针 IAM 页 P_ID2 指向了索引分配映射 (IAM) 页 P_ID1 ，但在扫描过程中检测不到该页。</span><span class="sxs-lookup"><span data-stu-id="e40b7-115">The Index Allocation Map (IAM) page P_ID1 is pointed to by the previous pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e40b7-116">说明</span><span class="sxs-lookup"><span data-stu-id="e40b7-116">Explanation</span></span>  
 <span data-ttu-id="e40b7-117">找不到索引分配映射 (IAM) 页或元数据条目，尽管对该页的引用作为上一页链接存在于 IAM 链中另一 IAM 页上。</span><span class="sxs-lookup"><span data-stu-id="e40b7-117">An Index Allocation Map (IAM) page or metadata entry was not located, even though a reference to the page exists as the previous page link on another IAM page in an IAM chain.</span></span> <span data-ttu-id="e40b7-118">如果 *P_ID1* 页是 (0:0)，则 IAM 页 *P_ID2* 是 IAM 链的开头，而且缺少 IAM 链的元数据条目。</span><span class="sxs-lookup"><span data-stu-id="e40b7-118">If the *P_ID1* page is (0:0), the IAM page, *P_ID2*, is the start of an IAM chain, and the metadata entry for the IAM chain is missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e40b7-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="e40b7-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="e40b7-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="e40b7-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="e40b7-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="e40b7-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="e40b7-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="e40b7-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="e40b7-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="e40b7-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="e40b7-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="e40b7-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="e40b7-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="e40b7-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="e40b7-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="e40b7-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="e40b7-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="e40b7-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="e40b7-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="e40b7-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="e40b7-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="e40b7-129">Restore from Backup</span></span>  
 <span data-ttu-id="e40b7-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="e40b7-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="e40b7-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="e40b7-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="e40b7-132">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="e40b7-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="e40b7-133">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="e40b7-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="e40b7-134">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="e40b7-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e40b7-135">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="e40b7-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="e40b7-136">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="e40b7-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="e40b7-137">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="e40b7-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="e40b7-138">REPAIR 将尝试重新生成涉及 *P_ID2* 页的 IAM 链。</span><span class="sxs-lookup"><span data-stu-id="e40b7-138">REPAIR will try to rebuild the IAM chain involving the *P_ID2* page.</span></span> <span data-ttu-id="e40b7-139">重新生成链可能涉及从链中删除页，或者删除整个链（如果元数据已损坏）。</span><span class="sxs-lookup"><span data-stu-id="e40b7-139">Rebuilding the chain may involve removing pages from the chain, or removing the whole chain if the metadata is corrupted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e40b7-140">此修复可能会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="e40b7-140">This repair may cause data loss.</span></span>  
  
  
