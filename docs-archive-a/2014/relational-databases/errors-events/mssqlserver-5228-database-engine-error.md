---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5228 (Database Engine error)
ms.assetid: 5e83c617-4aa2-4755-bcc5-a798c46b97e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eef59e62f00a44aad7bfefb1719a6d8d2b3d0290
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577714"
---
# <a name="mssqlserver_5228"></a><span data-ttu-id="6bf51-102">MSSQLSERVER_5228</span><span class="sxs-lookup"><span data-stu-id="6bf51-102">MSSQLSERVER_5228</span></span>
    
## <a name="details"></a><span data-ttu-id="6bf51-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6bf51-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6bf51-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6bf51-104">Product Name</span></span>|<span data-ttu-id="6bf51-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6bf51-105">SQL Server</span></span>|  
|<span data-ttu-id="6bf51-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6bf51-106">Event ID</span></span>|<span data-ttu-id="6bf51-107">5228</span><span class="sxs-lookup"><span data-stu-id="6bf51-107">5228</span></span>|  
|<span data-ttu-id="6bf51-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6bf51-108">Event Source</span></span>|<span data-ttu-id="6bf51-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6bf51-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6bf51-110">组件</span><span class="sxs-lookup"><span data-stu-id="6bf51-110">Component</span></span>|<span data-ttu-id="6bf51-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6bf51-111">SQLEngine</span></span>|  
|<span data-ttu-id="6bf51-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6bf51-112">Symbolic Name</span></span>|<span data-ttu-id="6bf51-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span><span class="sxs-lookup"><span data-stu-id="6bf51-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span></span>|  
|<span data-ttu-id="6bf51-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6bf51-114">Message Text</span></span>|<span data-ttu-id="6bf51-115">表错误:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE），页 PG_ID，行 R_ID。</span><span class="sxs-lookup"><span data-stu-id="6bf51-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page PG_ID, row R_ID.</span></span> <span data-ttu-id="6bf51-116">DBCC 检测到来自联机索引生成操作的不完全清除。</span><span class="sxs-lookup"><span data-stu-id="6bf51-116">DBCC detected incomplete cleanup from an online index build operation.</span></span> <span data-ttu-id="6bf51-117">(Antimatter 列值为 VALUE。)</span><span class="sxs-lookup"><span data-stu-id="6bf51-117">(Antimatter column value is VALUE.)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6bf51-118">说明</span><span class="sxs-lookup"><span data-stu-id="6bf51-118">Explanation</span></span>  
 <span data-ttu-id="6bf51-119">检测到对象 *O_ID*、索引 *I_ID* 和分区 *PN_ID* 存在未完成的联机索引生成。</span><span class="sxs-lookup"><span data-stu-id="6bf51-119">An unfinished online index build was detected for object *O_ID*, index *I_ID*, and partition *PN_ID*.</span></span> <span data-ttu-id="6bf51-120">这将由行 *R_ID* 上存在的 antimatter 列进行显示。</span><span class="sxs-lookup"><span data-stu-id="6bf51-120">This is manifested by the presence of an antimatter column on the row *R_ID*.</span></span> <span data-ttu-id="6bf51-121">在联机索引生成过程中协调来自多个源的记录时，将使用 antimatter 列。</span><span class="sxs-lookup"><span data-stu-id="6bf51-121">An antimatter column is used when reconciling records from multiple sources during an online index build.</span></span> <span data-ttu-id="6bf51-122">此错误消息还指出 antimatter 列的值。</span><span class="sxs-lookup"><span data-stu-id="6bf51-122">The error message also indicates the value of the antimatter column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6bf51-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="6bf51-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="6bf51-124">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="6bf51-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="6bf51-125">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="6bf51-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="6bf51-126">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="6bf51-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="6bf51-127">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="6bf51-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="6bf51-128">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="6bf51-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="6bf51-129">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="6bf51-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="6bf51-130">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="6bf51-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="6bf51-131">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="6bf51-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="6bf51-132">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="6bf51-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="6bf51-133">从备份还原</span><span class="sxs-lookup"><span data-stu-id="6bf51-133">Restore from Backup</span></span>  
 <span data-ttu-id="6bf51-134">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="6bf51-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="6bf51-135">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="6bf51-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="6bf51-136">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="6bf51-136">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="6bf51-137">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="6bf51-137">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="6bf51-138">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="6bf51-138">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6bf51-139">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="6bf51-139">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="6bf51-140">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="6bf51-140">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="6bf51-141">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="6bf51-141">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="6bf51-142">运行 REPAIR 将会重新生成指定的索引及其所有相关索引。</span><span class="sxs-lookup"><span data-stu-id="6bf51-142">Running REPAIR will cause the specified index and all its dependent indexes to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf51-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bf51-143">See Also</span></span>  
 [<span data-ttu-id="6bf51-144">DBCC CHECKDB (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6bf51-144">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
