---
title: MSSQLSERVER_8994 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8994 (Database Engine error)
ms.assetid: 8f4b0e2f-04c0-46e4-9208-20a7085d7a1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0bcc0b1db100b70390c09e9c825dbfd068d968af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577709"
---
# <a name="mssqlserver_8994"></a><span data-ttu-id="ae390-102">MSSQLSERVER_8994</span><span class="sxs-lookup"><span data-stu-id="ae390-102">MSSQLSERVER_8994</span></span>
    
## <a name="details"></a><span data-ttu-id="ae390-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ae390-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae390-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ae390-104">Product Name</span></span>|<span data-ttu-id="ae390-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ae390-105">SQL Server</span></span>|  
|<span data-ttu-id="ae390-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ae390-106">Event ID</span></span>|<span data-ttu-id="ae390-107">8994</span><span class="sxs-lookup"><span data-stu-id="ae390-107">8994</span></span>|  
|<span data-ttu-id="ae390-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ae390-108">Event Source</span></span>|<span data-ttu-id="ae390-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ae390-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ae390-110">组件</span><span class="sxs-lookup"><span data-stu-id="ae390-110">Component</span></span>|<span data-ttu-id="ae390-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ae390-111">SQLEngine</span></span>|  
|<span data-ttu-id="ae390-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="ae390-112">Symbolic Name</span></span>|<span data-ttu-id="ae390-113">DBCC3_MISSING_FORWARDING_ROW</span><span class="sxs-lookup"><span data-stu-id="ae390-113">DBCC3_MISSING_FORWARDING_ROW</span></span>|  
|<span data-ttu-id="ae390-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="ae390-114">Message Text</span></span>|<span data-ttu-id="ae390-115">前推行页 P_ID2，槽 S_ID2 应指向对象 ID O_ID，被前推行页 P_ID1，槽 S_ID1。</span><span class="sxs-lookup"><span data-stu-id="ae390-115">Object ID O_ID, forwarded row page P_ID1, slot S_ID1 should be pointed to by forwarding row page P_ID2, slot S_ID2.</span></span> <span data-ttu-id="ae390-116">但未遇到前推行。</span><span class="sxs-lookup"><span data-stu-id="ae390-116">Did not encounter forwarding row.</span></span> <span data-ttu-id="ae390-117">可能是因为分配错误。</span><span class="sxs-lookup"><span data-stu-id="ae390-117">Possible allocation error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae390-118">说明</span><span class="sxs-lookup"><span data-stu-id="ae390-118">Explanation</span></span>  
 <span data-ttu-id="ae390-119">堆集中的被前推行缺少应该指向它的前推行。</span><span class="sxs-lookup"><span data-stu-id="ae390-119">A forwarded row in a heap is missing the forwarding row that should point to it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae390-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="ae390-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="ae390-121">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="ae390-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="ae390-122">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="ae390-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="ae390-123">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="ae390-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="ae390-124">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="ae390-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="ae390-125">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="ae390-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="ae390-126">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="ae390-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="ae390-127">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="ae390-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="ae390-128">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="ae390-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="ae390-129">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="ae390-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ae390-130">从备份还原</span><span class="sxs-lookup"><span data-stu-id="ae390-130">Restore from Backup</span></span>  
 <span data-ttu-id="ae390-131">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="ae390-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="ae390-132">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="ae390-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="ae390-133">如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。</span><span class="sxs-lookup"><span data-stu-id="ae390-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="ae390-134">建议使用 DBCC CHECKDB 的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="ae390-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="ae390-135">接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。</span><span class="sxs-lookup"><span data-stu-id="ae390-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ae390-136">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="ae390-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="ae390-137">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="ae390-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="ae390-138">运行 REPAIR 选项的结果</span><span class="sxs-lookup"><span data-stu-id="ae390-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="ae390-139">被前推行将转换为常规数据行。</span><span class="sxs-lookup"><span data-stu-id="ae390-139">The forwarded row will be converted to a regular data row.</span></span>  
  
  
