---
title: MSSQLSERVER_2575 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2575 (Database Engine error)
ms.assetid: 92dfe449-a122-4730-942b-e1d319862d20
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 461d2b57b5ace98ca624f8dc3717c98f3e9e4d67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577718"
---
# <a name="mssqlserver_2575"></a><span data-ttu-id="9ea55-102">MSSQLSERVER_2575</span><span class="sxs-lookup"><span data-stu-id="9ea55-102">MSSQLSERVER_2575</span></span>
    
## <a name="details"></a><span data-ttu-id="9ea55-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="9ea55-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ea55-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9ea55-104">Product Name</span></span>|<span data-ttu-id="9ea55-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ea55-105">SQL Server</span></span>|  
|<span data-ttu-id="9ea55-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9ea55-106">Event ID</span></span>|<span data-ttu-id="9ea55-107">2575</span><span class="sxs-lookup"><span data-stu-id="9ea55-107">2575</span></span>|  
|<span data-ttu-id="9ea55-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9ea55-108">Event Source</span></span>|<span data-ttu-id="9ea55-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9ea55-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9ea55-110">组件</span><span class="sxs-lookup"><span data-stu-id="9ea55-110">Component</span></span>|<span data-ttu-id="9ea55-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9ea55-111">SQLEngine</span></span>|  
|<span data-ttu-id="9ea55-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="9ea55-112">Symbolic Name</span></span>|<span data-ttu-id="9ea55-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="9ea55-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="9ea55-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="9ea55-114">Message Text</span></span>|<span data-ttu-id="9ea55-115">对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID (类型为 TYPE) 中 IAM 页 P_ID2 的下一个指针指向了 IAM 页 P_ID1，但在扫描过程中检测不到页 P_ID1。</span><span class="sxs-lookup"><span data-stu-id="9ea55-115">IAM page P_ID1 is pointed to by the next pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ea55-116">说明</span><span class="sxs-lookup"><span data-stu-id="9ea55-116">Explanation</span></span>  
 <span data-ttu-id="9ea55-117">找到了指定索引的索引分配映射 (IAM) 页；但是，找不到该索引下一页指针的 IAM 页。</span><span class="sxs-lookup"><span data-stu-id="9ea55-117">An Index Allocation Map (IAM) page was found for the specified index; however, the IAM page for its next-page pointer was not found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ea55-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="9ea55-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="9ea55-119">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="9ea55-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="9ea55-120">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="9ea55-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="9ea55-121">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="9ea55-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="9ea55-122">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="9ea55-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="9ea55-123">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="9ea55-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="9ea55-124">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="9ea55-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="9ea55-125">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="9ea55-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="9ea55-126">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="9ea55-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="9ea55-127">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="9ea55-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="9ea55-128">从备份还原</span><span class="sxs-lookup"><span data-stu-id="9ea55-128">Restore from Backup</span></span>  
 <span data-ttu-id="9ea55-129">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="9ea55-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="9ea55-130">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="9ea55-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="9ea55-131">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="9ea55-131">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="9ea55-132">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="9ea55-132">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="9ea55-133">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="9ea55-133">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9ea55-134">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="9ea55-134">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="9ea55-135">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="9ea55-135">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="9ea55-136">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="9ea55-136">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="9ea55-137">DBCC 将重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="9ea55-137">DBCC will rebuild the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea55-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ea55-138">See Also</span></span>  
 [<span data-ttu-id="9ea55-139">DBCC CHECKDB (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ea55-139">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
