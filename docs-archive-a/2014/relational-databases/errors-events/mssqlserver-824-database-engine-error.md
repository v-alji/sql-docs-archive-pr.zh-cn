---
title: MSSQLSERVER_824 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d57b19bc8c837b92b65728fbb0046039b862d31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586690"
---
# <a name="mssqlserver_824"></a><span data-ttu-id="78690-102">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="78690-102">MSSQLSERVER_824</span></span>
    
## <a name="details"></a><span data-ttu-id="78690-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="78690-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78690-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="78690-104">Product Name</span></span>|<span data-ttu-id="78690-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="78690-105">SQL Server</span></span>|  
|<span data-ttu-id="78690-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="78690-106">Event ID</span></span>|<span data-ttu-id="78690-107">824</span><span class="sxs-lookup"><span data-stu-id="78690-107">824</span></span>|  
|<span data-ttu-id="78690-108">事件源</span><span class="sxs-lookup"><span data-stu-id="78690-108">Event Source</span></span>|<span data-ttu-id="78690-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="78690-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="78690-110">组件</span><span class="sxs-lookup"><span data-stu-id="78690-110">Component</span></span>|<span data-ttu-id="78690-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="78690-111">SQLEngine</span></span>|  
|<span data-ttu-id="78690-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="78690-112">Symbolic Name</span></span>|<span data-ttu-id="78690-113">B_HARDSSERR</span><span class="sxs-lookup"><span data-stu-id="78690-113">B_HARDSSERR</span></span>|  
|<span data-ttu-id="78690-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="78690-114">Message Text</span></span>|<span data-ttu-id="78690-115">SQL Server 检测到基于一致性的逻辑 I/O 错误: %ls。</span><span class="sxs-lookup"><span data-stu-id="78690-115">SQL Server detected a logical consistency-based I/O error: %ls.</span></span> <span data-ttu-id="78690-116">在文件 '%ls' 中、偏移量为 %#016I64x 的位置对数据库 ID %d 中的页 %S_PGID 执行 %S_MSG 期间，发生了该错误。</span><span class="sxs-lookup"><span data-stu-id="78690-116">It occurred during a %S_MSG of page %S_PGID in database ID %d at offset %#016I64x in file '%ls'.</span></span>  <span data-ttu-id="78690-117">SQL Server 错误日志或系统事件日志中的其他消息可能提供了更详细信息。</span><span class="sxs-lookup"><span data-stu-id="78690-117">Additional messages in the SQL Server error log or system event log may provide more detail.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="78690-118">说明</span><span class="sxs-lookup"><span data-stu-id="78690-118">Explanation</span></span>  
 <span data-ttu-id="78690-119">此错误表明 Windows 报告已从磁盘成功读取页，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 检测到页中存在错误。</span><span class="sxs-lookup"><span data-stu-id="78690-119">This error indicates that Windows reports that the page is successfully read from disk, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has discovered something wrong with the page.</span></span> <span data-ttu-id="78690-120">此错误与错误 823 类似，只是 Windows 不检测这一错误。</span><span class="sxs-lookup"><span data-stu-id="78690-120">This error is similar to error 823 except that Windows did not detect the error.</span></span> <span data-ttu-id="78690-121">这通常表明 I/O 子系统中存在问题，例如磁盘驱动器存在故障、磁盘固件存在问题、设备驱动程序不正确等等。</span><span class="sxs-lookup"><span data-stu-id="78690-121">This usually indicates a problem in the I/O subsystem, such as a failing disk drive, disk firmware problems, faulty device driver, and so on.</span></span> <span data-ttu-id="78690-122">有关 I/O 错误的详细信息，请参阅 [Microsoft SQL Server I/O 基础知识，第 2 章](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))。</span><span class="sxs-lookup"><span data-stu-id="78690-122">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78690-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="78690-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="78690-124">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="78690-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="78690-125">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="78690-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="78690-126">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以查看是否存在由硬件故障引起的错误。</span><span class="sxs-lookup"><span data-stu-id="78690-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred because of hardware failure.</span></span> <span data-ttu-id="78690-127">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="78690-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="78690-128">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="78690-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="78690-129">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="78690-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="78690-130">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="78690-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="78690-131">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="78690-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="78690-132">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="78690-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="78690-133">从备份还原</span><span class="sxs-lookup"><span data-stu-id="78690-133">Restore from Backup</span></span>  
 <span data-ttu-id="78690-134">如果出现的问题与硬件无关，并且已知的干净备份可用，则请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="78690-134">If the problem is not hardware-related and a known clean backup is available, restore the database from the backup.</span></span>  
  
 <span data-ttu-id="78690-135">考虑将数据库改为使用 PAGE_VERIFY CHECKSUM 选项。</span><span class="sxs-lookup"><span data-stu-id="78690-135">Consider changing the databases to use the PAGE_VERIFY CHECKSUM option.</span></span> <span data-ttu-id="78690-136">有关 PAGE_VERIFY 的信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78690-136">For information about PAGE_VERIFY, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78690-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78690-137">See Also</span></span>  
 [<span data-ttu-id="78690-138">管理 suspect_pages 表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="78690-138">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
