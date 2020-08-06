---
title: MSSQLSERVER_2577 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2577 (Database Engine error)
ms.assetid: f53256a2-2fb0-47fd-9ed9-c45389104145
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9e4b7b85f59ba721eae6b4a0ac8db1b2d288422d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589607"
---
# <a name="mssqlserver_2577"></a><span data-ttu-id="f3d88-102">MSSQLSERVER_2577</span><span class="sxs-lookup"><span data-stu-id="f3d88-102">MSSQLSERVER_2577</span></span>
    
## <a name="details"></a><span data-ttu-id="f3d88-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f3d88-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3d88-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f3d88-104">Product Name</span></span>|<span data-ttu-id="f3d88-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f3d88-105">SQL Server</span></span>|  
|<span data-ttu-id="f3d88-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f3d88-106">Event ID</span></span>|<span data-ttu-id="f3d88-107">2577</span><span class="sxs-lookup"><span data-stu-id="f3d88-107">2577</span></span>|  
|<span data-ttu-id="f3d88-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f3d88-108">Event Source</span></span>|<span data-ttu-id="f3d88-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f3d88-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f3d88-110">组件</span><span class="sxs-lookup"><span data-stu-id="f3d88-110">Component</span></span>|<span data-ttu-id="f3d88-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f3d88-111">SQLEngine</span></span>|  
|<span data-ttu-id="f3d88-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f3d88-112">Symbolic Name</span></span>|<span data-ttu-id="f3d88-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="f3d88-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="f3d88-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f3d88-114">Message Text</span></span>|<span data-ttu-id="f3d88-115">在对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）的索引分配映射 (IAM) 链中，链序列号顺序不对。</span><span class="sxs-lookup"><span data-stu-id="f3d88-115">Chain sequence numbers out of order in the Index Allocation Map (IAM) chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="f3d88-116">序列号为 SEQUENCE1 的页 P_ID1 指向了序列号为 SEQUENCE2 的页 P_ID2。</span><span class="sxs-lookup"><span data-stu-id="f3d88-116">Page P_ID1 with sequence number SEQUENCE1 points to page P_ID2 with sequence number SEQUENCE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f3d88-117">说明</span><span class="sxs-lookup"><span data-stu-id="f3d88-117">Explanation</span></span>  
 <span data-ttu-id="f3d88-118">每个索引分配映射 (IAM) 页都有一个序列号。</span><span class="sxs-lookup"><span data-stu-id="f3d88-118">Every Index Allocation Map (IAM) page has a sequence number.</span></span> <span data-ttu-id="f3d88-119">该序列号指示 IAM 页在 IAM 链内的位置。</span><span class="sxs-lookup"><span data-stu-id="f3d88-119">The sequence number is the position of the IAM page within the IAM chain.</span></span> <span data-ttu-id="f3d88-120">规则是用该序列号加一来表示每个 IAM 页。</span><span class="sxs-lookup"><span data-stu-id="f3d88-120">The rule is that sequence numbers increase by one for each IAM page.</span></span> <span data-ttu-id="f3d88-121">IAM 页 *P_ID2* 具有的序列号未遵循此规则。</span><span class="sxs-lookup"><span data-stu-id="f3d88-121">IAM page, *P_ID2*, has a sequence number that does not follow this rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f3d88-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="f3d88-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="f3d88-123">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="f3d88-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="f3d88-124">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="f3d88-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="f3d88-125">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="f3d88-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="f3d88-126">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="f3d88-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="f3d88-127">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="f3d88-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="f3d88-128">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="f3d88-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="f3d88-129">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="f3d88-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="f3d88-130">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="f3d88-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="f3d88-131">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="f3d88-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="f3d88-132">从备份还原</span><span class="sxs-lookup"><span data-stu-id="f3d88-132">Restore from Backup</span></span>  
 <span data-ttu-id="f3d88-133">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="f3d88-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="f3d88-134">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="f3d88-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="f3d88-135">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="f3d88-135">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="f3d88-136">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="f3d88-136">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="f3d88-137">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="f3d88-137">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f3d88-138">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="f3d88-138">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="f3d88-139">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="f3d88-139">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="f3d88-140">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="f3d88-140">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="f3d88-141">运行 REPAIR 将重新生成 IAM 链。</span><span class="sxs-lookup"><span data-stu-id="f3d88-141">Running REPAIR will rebuild the IAM chain.</span></span> <span data-ttu-id="f3d88-142">REPAIR 首先将现有的 IAM 链拆分为两半。</span><span class="sxs-lookup"><span data-stu-id="f3d88-142">REPAIR first splits the existing IAM chain in two halves.</span></span> <span data-ttu-id="f3d88-143">链的第一半将以 IAM 页 *P_ID1* 结束。</span><span class="sxs-lookup"><span data-stu-id="f3d88-143">The first half of the chain will end with IAM page, *P_ID1*.</span></span> <span data-ttu-id="f3d88-144">*P_ID1* 页的下一页指针将设置为 (0:0)。</span><span class="sxs-lookup"><span data-stu-id="f3d88-144">The next page pointer of the *P_ID1* page will be set to (0:0).</span></span> <span data-ttu-id="f3d88-145">链的第二半将从 IAM 页 *P_ID2* 开始。</span><span class="sxs-lookup"><span data-stu-id="f3d88-145">The second half of the chain will start with IAM page, *P_ID2*.</span></span> <span data-ttu-id="f3d88-146">*P_ID2* 页的上一页指针将设置为 (0:0)。</span><span class="sxs-lookup"><span data-stu-id="f3d88-146">The previous page pointer of the *P_ID2* page will be set to (0:0).</span></span>  
  
 <span data-ttu-id="f3d88-147">然后，REPAIR 将链的两半连接在一起，并重新生成 IAM 链的序列号。</span><span class="sxs-lookup"><span data-stu-id="f3d88-147">REPAIR will then connect the two haves of the chain together and regenerate the sequence numbers for the IAM chain.</span></span> <span data-ttu-id="f3d88-148">将释放无法修复的任何 IAM 页。</span><span class="sxs-lookup"><span data-stu-id="f3d88-148">Any IAM pages that cannot be repaired will be deallocated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f3d88-149">此修复可能会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="f3d88-149">This repair may cause data loss.</span></span>  
  
  
