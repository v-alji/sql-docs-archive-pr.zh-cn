---
title: MSSQLSERVER_2533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2533 (Database Engine error)
ms.assetid: 0418352c-0ab2-4dc7-b8b9-5c3bad94560c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1eb3e2780693a3a0ffed21ce7b9d7887615536c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689389"
---
# <a name="mssqlserver_2533"></a><span data-ttu-id="93790-102">MSSQLSERVER_2533</span><span class="sxs-lookup"><span data-stu-id="93790-102">MSSQLSERVER_2533</span></span>
    
## <a name="details"></a><span data-ttu-id="93790-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="93790-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93790-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="93790-104">Product Name</span></span>|<span data-ttu-id="93790-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="93790-105">SQL Server</span></span>|  
|<span data-ttu-id="93790-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="93790-106">Event ID</span></span>|<span data-ttu-id="93790-107">2533</span><span class="sxs-lookup"><span data-stu-id="93790-107">2533</span></span>|  
|<span data-ttu-id="93790-108">事件源</span><span class="sxs-lookup"><span data-stu-id="93790-108">Event Source</span></span>|<span data-ttu-id="93790-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="93790-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="93790-110">组件</span><span class="sxs-lookup"><span data-stu-id="93790-110">Component</span></span>|<span data-ttu-id="93790-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="93790-111">SQLEngine</span></span>|  
|<span data-ttu-id="93790-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="93790-112">Symbolic Name</span></span>|<span data-ttu-id="93790-113">DBCC_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="93790-113">DBCC_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="93790-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="93790-114">Message Text</span></span>|<span data-ttu-id="93790-115">表错误:看不到分配给对象 ID O_ID、索引 ID I_ID、分区 ID PN_ID、分配单元 ID A_ID（类型为 TYPE）的页 P_ID。</span><span class="sxs-lookup"><span data-stu-id="93790-115">Table error: Page P_ID allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) was not seen.</span></span> <span data-ttu-id="93790-116">该页可能无效，或者页头中可能包含错误的分配单元 ID。</span><span class="sxs-lookup"><span data-stu-id="93790-116">Page may be invalid or have incorrect alloc unit ID in its header.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="93790-117">说明</span><span class="sxs-lookup"><span data-stu-id="93790-117">Explanation</span></span>  
 <span data-ttu-id="93790-118">页已分配给分配单元 ID *A_ID*，但此分配单元 ID 不在页头中。</span><span class="sxs-lookup"><span data-stu-id="93790-118">A page is allocated to the allocation unit ID, *A_ID*, but this allocation unit ID is not in the header of the page.</span></span> <span data-ttu-id="93790-119">页头具有其他的分配单元 ID。</span><span class="sxs-lookup"><span data-stu-id="93790-119">The header has a different allocation unit ID.</span></span> <span data-ttu-id="93790-120">如果页头中的分配单元 ID 用于有效的对象，则该页可能具有匹配的 MSSQLEngine_2534 错误。</span><span class="sxs-lookup"><span data-stu-id="93790-120">If the allocation unit ID in the header of the page is for a valid object, the page may have a matching MSSQLEngine_2534 error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="93790-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="93790-121">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="93790-122">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="93790-122">Look for Hardware Failure</span></span>  
 <span data-ttu-id="93790-123">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="93790-123">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="93790-124">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="93790-124">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="93790-125">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="93790-125">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="93790-126">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="93790-126">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="93790-127">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="93790-127">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="93790-128">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="93790-128">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="93790-129">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="93790-129">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="93790-130">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="93790-130">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="93790-131">从备份还原</span><span class="sxs-lookup"><span data-stu-id="93790-131">Restore from Backup</span></span>  
 <span data-ttu-id="93790-132">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="93790-132">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="93790-133">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="93790-133">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="93790-134">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="93790-134">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="93790-135">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="93790-135">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="93790-136">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="93790-136">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="93790-137">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="93790-137">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="93790-138">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="93790-138">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="93790-139">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="93790-139">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="93790-140">REPAIR 将释放页。</span><span class="sxs-lookup"><span data-stu-id="93790-140">REPAIR will deallocate the page.</span></span> <span data-ttu-id="93790-141">如果页来自行内数据分配单元，则将重新生成索引（如果存在索引）。</span><span class="sxs-lookup"><span data-stu-id="93790-141">If the page was from an in-row data allocation unit, the index, if one exists, will be rebuilt.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="93790-142">此修复可能会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="93790-142">This repair may cause data loss.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93790-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93790-143">See Also</span></span>  
 [<span data-ttu-id="93790-144">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="93790-144">MSSQLSERVER_2534</span></span>](mssqlserver-2534-database-engine-error.md)  
  
  
