---
title: MSSQLSERVER_7986 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7986 (Database Engine error)
ms.assetid: ae64276c-4e1e-4ef3-9ee9-ebeb2f61e565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f7d312987a2692c95f2cf6dbe0c86a4b2acbe6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690612"
---
# <a name="mssqlserver_7986"></a><span data-ttu-id="6a8e7-102">MSSQLSERVER_7986</span><span class="sxs-lookup"><span data-stu-id="6a8e7-102">MSSQLSERVER_7986</span></span>
    
## <a name="details"></a><span data-ttu-id="6a8e7-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6a8e7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a8e7-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6a8e7-104">Product Name</span></span>|<span data-ttu-id="6a8e7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a8e7-105">SQL Server</span></span>|  
|<span data-ttu-id="6a8e7-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6a8e7-106">Event ID</span></span>|<span data-ttu-id="6a8e7-107">7986</span><span class="sxs-lookup"><span data-stu-id="6a8e7-107">7986</span></span>|  
|<span data-ttu-id="6a8e7-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6a8e7-108">Event Source</span></span>|<span data-ttu-id="6a8e7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a8e7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a8e7-110">组件</span><span class="sxs-lookup"><span data-stu-id="6a8e7-110">Component</span></span>|<span data-ttu-id="6a8e7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a8e7-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a8e7-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6a8e7-112">Symbolic Name</span></span>|<span data-ttu-id="6a8e7-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span><span class="sxs-lookup"><span data-stu-id="6a8e7-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span></span>|  
|<span data-ttu-id="6a8e7-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6a8e7-114">Message Text</span></span>|<span data-ttu-id="6a8e7-115">系统表预检查:对象 ID O_ID 具有跨对象的链链接。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-115">System table pre-checks: Object ID O_ID has cross-object chain linkage.</span></span> <span data-ttu-id="6a8e7-116">页 P_ID1 指向分配单元 ID A_ID1 中的 P_ID2（应为 A_ID2）。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-116">Page P_ID1 points to P_ID2 in alloc unit ID A_ID1 (should be A_ID2).</span></span> <span data-ttu-id="6a8e7-117">由于不可修复的错误，CHECK 语句已终止。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-117">Check statement terminated due to unrepairable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a8e7-118">说明</span><span class="sxs-lookup"><span data-stu-id="6a8e7-118">Explanation</span></span>  
 <span data-ttu-id="6a8e7-119">DBCC CHECKDB 的第一个阶段用于对关键系统表的数据页进行简单检查。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="6a8e7-120">如果找到任何错误，则无法修复它们；因此，DBCC CHECKDB 立即终止。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-120">If any errors are found, they cannot be repaired; therefore, the DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="6a8e7-121">指定对象的数据级别中页 *P_ID1* 的下一页指针指向其他对象中的页 *P_ID2*。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-121">The next page pointer of page *P_ID1* in the data level of the specified object points to a page, *P_ID2*, in a different object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a8e7-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="6a8e7-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="6a8e7-123">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="6a8e7-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="6a8e7-124">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="6a8e7-125">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="6a8e7-126">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="6a8e7-127">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="6a8e7-128">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="6a8e7-129">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="6a8e7-130">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="6a8e7-131">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="6a8e7-132">从备份还原</span><span class="sxs-lookup"><span data-stu-id="6a8e7-132">Restore from Backup</span></span>  
 <span data-ttu-id="6a8e7-133">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="6a8e7-134">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="6a8e7-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="6a8e7-135">不适用。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-135">Not applicable.</span></span> <span data-ttu-id="6a8e7-136">此错误无法自动修复。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-136">This error cannot be repaired automatically.</span></span> <span data-ttu-id="6a8e7-137">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="6a8e7-137">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
