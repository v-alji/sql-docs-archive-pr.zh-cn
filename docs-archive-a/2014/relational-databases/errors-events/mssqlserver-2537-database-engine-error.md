---
title: MSSQLSERVER_2537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2537 (Database Engine error)
ms.assetid: 0af6ff69-d75a-4c39-8da2-9bd0695277c6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c227867bac5a0ea5789ba653414444d011e5910d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589615"
---
# <a name="mssqlserver_2537"></a><span data-ttu-id="d0006-102">MSSQLSERVER_2537</span><span class="sxs-lookup"><span data-stu-id="d0006-102">MSSQLSERVER_2537</span></span>
    
## <a name="details"></a><span data-ttu-id="d0006-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d0006-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0006-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d0006-104">Product Name</span></span>|<span data-ttu-id="d0006-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0006-105">SQL Server</span></span>|  
|<span data-ttu-id="d0006-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d0006-106">Event ID</span></span>|<span data-ttu-id="d0006-107">2537</span><span class="sxs-lookup"><span data-stu-id="d0006-107">2537</span></span>|  
|<span data-ttu-id="d0006-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d0006-108">Event Source</span></span>|<span data-ttu-id="d0006-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d0006-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d0006-110">组件</span><span class="sxs-lookup"><span data-stu-id="d0006-110">Component</span></span>|<span data-ttu-id="d0006-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d0006-111">SQLEngine</span></span>|  
|<span data-ttu-id="d0006-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d0006-112">Symbolic Name</span></span>|<span data-ttu-id="d0006-113">DBCC_RECORD_CHECK_FAILED</span><span class="sxs-lookup"><span data-stu-id="d0006-113">DBCC_RECORD_CHECK_FAILED</span></span>|  
|<span data-ttu-id="d0006-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d0006-114">Message Text</span></span>|<span data-ttu-id="d0006-115">表错误:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE），页 P_ID，行 ROW_ID。</span><span class="sxs-lookup"><span data-stu-id="d0006-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page P_ID, row ROW_ID.</span></span> <span data-ttu-id="d0006-116">记录检查(CHECK_TEXT)失败。</span><span class="sxs-lookup"><span data-stu-id="d0006-116">Record check (CHECK_TEXT) failed.</span></span> <span data-ttu-id="d0006-117">值为 VALUE1 和 VALUE2。</span><span class="sxs-lookup"><span data-stu-id="d0006-117">Values are VALUE1 and VALUE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d0006-118">说明</span><span class="sxs-lookup"><span data-stu-id="d0006-118">Explanation</span></span>  
 <span data-ttu-id="d0006-119">行 ROW_ID（或该行中的某列）未通过 CHECK_TEXT 所描述的测试或条件。</span><span class="sxs-lookup"><span data-stu-id="d0006-119">The row ROW_ID (or a column in the row) failed the test or condition described by CHECK_TEXT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d0006-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="d0006-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d0006-121">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="d0006-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d0006-122">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="d0006-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d0006-123">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="d0006-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d0006-124">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="d0006-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d0006-125">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="d0006-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d0006-126">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="d0006-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d0006-127">如果您怀疑是写缓存出现问题，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="d0006-127">If you suspect that write-caching is the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d0006-128">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="d0006-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d0006-129">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="d0006-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d0006-130">从备份还原</span><span class="sxs-lookup"><span data-stu-id="d0006-130">Restore from Backup</span></span>  
 <span data-ttu-id="d0006-131">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="d0006-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d0006-132">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="d0006-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d0006-133">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="d0006-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="d0006-134">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="d0006-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="d0006-135">然后运行带有所推荐 REPAIR 子句的 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="d0006-135">Then, run DBCC CHECKDB with the recommended REPAIR clause.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d0006-136">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="d0006-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="d0006-137">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="d0006-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="d0006-138">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="d0006-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="d0006-139">如果索引存在，则 REPAIR 将重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="d0006-139">REPAIR will rebuild the index if an index exists.</span></span>  
  
 <span data-ttu-id="d0006-140">**警告** 此修复可能会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="d0006-140">**Caution** This repair may cause data loss.</span></span>  
  
  
