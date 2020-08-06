---
title: MSSQLSERVER_2512 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2512 (Database Engine error)
ms.assetid: 989b527f-5b02-403c-9b7f-51580f4e7688
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da121c8b49ab8290c494d33f0f2a0ba6fded9e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688930"
---
# <a name="mssqlserver_2512"></a><span data-ttu-id="da361-102">MSSQLSERVER_2512</span><span class="sxs-lookup"><span data-stu-id="da361-102">MSSQLSERVER_2512</span></span>
    
## <a name="details"></a><span data-ttu-id="da361-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="da361-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da361-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="da361-104">Product Name</span></span>|<span data-ttu-id="da361-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="da361-105">SQL Server</span></span>|  
|<span data-ttu-id="da361-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="da361-106">Event ID</span></span>|<span data-ttu-id="da361-107">2512</span><span class="sxs-lookup"><span data-stu-id="da361-107">2512</span></span>|  
|<span data-ttu-id="da361-108">事件源</span><span class="sxs-lookup"><span data-stu-id="da361-108">Event Source</span></span>|<span data-ttu-id="da361-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="da361-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="da361-110">组件</span><span class="sxs-lookup"><span data-stu-id="da361-110">Component</span></span>|<span data-ttu-id="da361-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="da361-111">SQLEngine</span></span>|  
|<span data-ttu-id="da361-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="da361-112">Symbolic Name</span></span>|<span data-ttu-id="da361-113">DBCC_DUPLICATE_KEYS</span><span class="sxs-lookup"><span data-stu-id="da361-113">DBCC_DUPLICATE_KEYS</span></span>|  
|<span data-ttu-id="da361-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="da361-114">Message Text</span></span>|<span data-ttu-id="da361-115">表错误:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID (类型为 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="da361-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="da361-116">页 P_ID1 槽 SLOT1 和页 P_ID2 槽 SLOT2 中的重复键。</span><span class="sxs-lookup"><span data-stu-id="da361-116">Duplicate keys on page P_ID1 slot SLOT1 and page P_ID2 slot SLOT2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da361-117">说明</span><span class="sxs-lookup"><span data-stu-id="da361-117">Explanation</span></span>  
 <span data-ttu-id="da361-118">两个指定的槽具有相同的键，其中包含任何 `uniqueifiers`。</span><span class="sxs-lookup"><span data-stu-id="da361-118">The two specified slots have identical keys, including any `uniqueifiers`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da361-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="da361-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="da361-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="da361-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="da361-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="da361-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="da361-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="da361-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="da361-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="da361-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="da361-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="da361-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="da361-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="da361-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="da361-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="da361-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="da361-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="da361-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="da361-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="da361-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="da361-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="da361-129">Restore from Backup</span></span>  
 <span data-ttu-id="da361-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="da361-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="da361-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="da361-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="da361-132">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="da361-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="da361-133">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="da361-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="da361-134">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="da361-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="da361-135">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="da361-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="da361-136">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="da361-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="da361-137">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="da361-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="da361-138">如果记录为虚影或者索引不唯一，则 DBCC 可以通过重新生成索引来修复此问题。</span><span class="sxs-lookup"><span data-stu-id="da361-138">If either record is a ghost or the index is nonunique, DBCC can repair this problem by rebuilding the index.</span></span> <span data-ttu-id="da361-139">否则，REPAIR 在必要时将删除页 *P_ID2* 上的槽 *SLOT2*，或者将该槽标记为虚影。</span><span class="sxs-lookup"><span data-stu-id="da361-139">Otherwise, if necessary, REPAIR will delete slot *SLOT2* on page *P_ID2* or mark the slot as a ghost.</span></span>  
  
  
