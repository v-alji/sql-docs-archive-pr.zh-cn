---
title: MSSQLSERVER_7988 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7988 (Database Engine error)
ms.assetid: 29b967b8-de30-4618-99a8-8b1155e69026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 984cb03aeb5feaa230762e200304f16cd8c5df08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689383"
---
# <a name="mssqlserver_7988"></a><span data-ttu-id="ff068-102">MSSQLSERVER_7988</span><span class="sxs-lookup"><span data-stu-id="ff068-102">MSSQLSERVER_7988</span></span>
    
## <a name="details"></a><span data-ttu-id="ff068-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ff068-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff068-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ff068-104">Product Name</span></span>|<span data-ttu-id="ff068-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ff068-105">SQL Server</span></span>|  
|<span data-ttu-id="ff068-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ff068-106">Event ID</span></span>|<span data-ttu-id="ff068-107">7988</span><span class="sxs-lookup"><span data-stu-id="ff068-107">7988</span></span>|  
|<span data-ttu-id="ff068-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ff068-108">Event Source</span></span>|<span data-ttu-id="ff068-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ff068-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ff068-110">组件</span><span class="sxs-lookup"><span data-stu-id="ff068-110">Component</span></span>|<span data-ttu-id="ff068-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ff068-111">SQLEngine</span></span>|  
|<span data-ttu-id="ff068-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="ff068-112">Symbolic Name</span></span>|<span data-ttu-id="ff068-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span><span class="sxs-lookup"><span data-stu-id="ff068-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span></span>|  
|<span data-ttu-id="ff068-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="ff068-114">Message Text</span></span>|<span data-ttu-id="ff068-115">系统表预检查:对象 ID O_ID。</span><span class="sxs-lookup"><span data-stu-id="ff068-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="ff068-116">在 P_ID 处检测到数据链中存在循环。</span><span class="sxs-lookup"><span data-stu-id="ff068-116">Loop in data chain detected at P_ID.</span></span> <span data-ttu-id="ff068-117">由于不可修复的错误，Check 语句已终止。</span><span class="sxs-lookup"><span data-stu-id="ff068-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ff068-118">说明</span><span class="sxs-lookup"><span data-stu-id="ff068-118">Explanation</span></span>  
 <span data-ttu-id="ff068-119">DBCC CHECKDB 的第一个阶段用于对关键系统表的数据页进行简单检查。</span><span class="sxs-lookup"><span data-stu-id="ff068-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="ff068-120">如果找到任何错误，无法修复它们；因此，DBCC CHECKDB 立即终止。</span><span class="sxs-lookup"><span data-stu-id="ff068-120">If any errors are found, they cannot be repaired; therefore, DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="ff068-121">在页 *P_ID* 上检测到页链接循环。</span><span class="sxs-lookup"><span data-stu-id="ff068-121">A page linkage loop has been detected on page *P_ID*.</span></span> <span data-ttu-id="ff068-122">当页的下一页指针最终返回到该页时，将出现页链接循环。</span><span class="sxs-lookup"><span data-stu-id="ff068-122">A page linkage loop occurs when the next page pointers from a page eventually return to the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ff068-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="ff068-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="ff068-124">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="ff068-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="ff068-125">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="ff068-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="ff068-126">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="ff068-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="ff068-127">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="ff068-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="ff068-128">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="ff068-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="ff068-129">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="ff068-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="ff068-130">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="ff068-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="ff068-131">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="ff068-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="ff068-132">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="ff068-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ff068-133">从备份还原</span><span class="sxs-lookup"><span data-stu-id="ff068-133">Restore from Backup</span></span>  
 <span data-ttu-id="ff068-134">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="ff068-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="ff068-135">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="ff068-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="ff068-136">不适用。</span><span class="sxs-lookup"><span data-stu-id="ff068-136">Not applicable.</span></span> <span data-ttu-id="ff068-137">此错误无法自动修复。</span><span class="sxs-lookup"><span data-stu-id="ff068-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="ff068-138">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="ff068-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
