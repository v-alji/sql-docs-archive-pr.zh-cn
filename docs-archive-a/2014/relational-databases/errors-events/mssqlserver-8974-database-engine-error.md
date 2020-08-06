---
title: MSSQLSERVER_8974 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8974 (Database Engine error)
ms.assetid: 52098678-0858-4a14-ad07-37ebbafca5fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3107f5b62caf04e232532c2d2b93d5da19fb53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591897"
---
# <a name="mssqlserver_8974"></a><span data-ttu-id="a95d3-102">MSSQLSERVER_8974</span><span class="sxs-lookup"><span data-stu-id="a95d3-102">MSSQLSERVER_8974</span></span>
    
## <a name="details"></a><span data-ttu-id="a95d3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a95d3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a95d3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a95d3-104">Product Name</span></span>|<span data-ttu-id="a95d3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a95d3-105">SQL Server</span></span>|  
|<span data-ttu-id="a95d3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a95d3-106">Event ID</span></span>|<span data-ttu-id="a95d3-107">8974</span><span class="sxs-lookup"><span data-stu-id="a95d3-107">8974</span></span>|  
|<span data-ttu-id="a95d3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a95d3-108">Event Source</span></span>|<span data-ttu-id="a95d3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a95d3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a95d3-110">组件</span><span class="sxs-lookup"><span data-stu-id="a95d3-110">Component</span></span>|<span data-ttu-id="a95d3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a95d3-111">SQLEngine</span></span>|  
|<span data-ttu-id="a95d3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a95d3-112">Symbolic Name</span></span>|<span data-ttu-id="a95d3-113">DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS</span><span class="sxs-lookup"><span data-stu-id="a95d3-113">DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS</span></span>|  
|<span data-ttu-id="a95d3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a95d3-114">Message Text</span></span>|<span data-ttu-id="a95d3-115">表错误:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID (类型为 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="a95d3-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="a95d3-116">页 P_ID2，槽 S_ID2 和页 P_ID3，槽 P_ID3 都指向了位于页 P_ID1，槽 S_ID1，文本 ID TEXT_ID 的行外数据节点。</span><span class="sxs-lookup"><span data-stu-id="a95d3-116">The off-row data node at page P_ID1, slot S_ID1, text ID TEXT_ID is pointed to by page P_ID2, slot S_ID2 and by page P_ID3, slot P_ID3.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a95d3-117">说明</span><span class="sxs-lookup"><span data-stu-id="a95d3-117">Explanation</span></span>  
 <span data-ttu-id="a95d3-118">行外数据节点有两条数据或索引记录将其列为子节点。</span><span class="sxs-lookup"><span data-stu-id="a95d3-118">An off-row data node has two data or index records that list it as a child node.</span></span> <span data-ttu-id="a95d3-119">一个节点只能有一个父节点。</span><span class="sxs-lookup"><span data-stu-id="a95d3-119">A node can have only one parent node.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a95d3-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="a95d3-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="a95d3-121">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="a95d3-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="a95d3-122">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="a95d3-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="a95d3-123">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="a95d3-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="a95d3-124">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="a95d3-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="a95d3-125">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="a95d3-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="a95d3-126">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="a95d3-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="a95d3-127">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="a95d3-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="a95d3-128">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="a95d3-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="a95d3-129">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="a95d3-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="a95d3-130">从备份还原</span><span class="sxs-lookup"><span data-stu-id="a95d3-130">Restore from Backup</span></span>  
 <span data-ttu-id="a95d3-131">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="a95d3-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="a95d3-132">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="a95d3-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="a95d3-133">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="a95d3-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="a95d3-134">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="a95d3-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="a95d3-135">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="a95d3-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a95d3-136">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="a95d3-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="a95d3-137">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="a95d3-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="a95d3-138">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="a95d3-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="a95d3-139">将删除页 *P_ID1* 上的行外数据节点，并删除对页 *P_ID2* 和 *P_ID3* 的引用。</span><span class="sxs-lookup"><span data-stu-id="a95d3-139">The off-row data node on page *P_ID1* will be deleted and both references on pages *P_ID2* and *P_ID3* will be deleted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a95d3-140">此修复可能会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="a95d3-140">This repair might cause data loss.</span></span>  
  
  
