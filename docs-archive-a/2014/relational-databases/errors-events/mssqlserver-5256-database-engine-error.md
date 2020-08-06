---
title: MSSQLSERVER_5256 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5256 (Database Engine error)
ms.assetid: 6fe254b4-2926-446f-8b20-0f1d921a4615
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9146b7744e78550463cbec4c05df5fd75a049898
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690616"
---
# <a name="mssqlserver_5256"></a><span data-ttu-id="186d5-102">MSSQLSERVER_5256</span><span class="sxs-lookup"><span data-stu-id="186d5-102">MSSQLSERVER_5256</span></span>
    
## <a name="details"></a><span data-ttu-id="186d5-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="186d5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="186d5-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="186d5-104">Product Name</span></span>|<span data-ttu-id="186d5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="186d5-105">SQL Server</span></span>|  
|<span data-ttu-id="186d5-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="186d5-106">Event ID</span></span>|<span data-ttu-id="186d5-107">5256</span><span class="sxs-lookup"><span data-stu-id="186d5-107">5256</span></span>|  
|<span data-ttu-id="186d5-108">事件源</span><span class="sxs-lookup"><span data-stu-id="186d5-108">Event Source</span></span>|<span data-ttu-id="186d5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="186d5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="186d5-110">组件</span><span class="sxs-lookup"><span data-stu-id="186d5-110">Component</span></span>|<span data-ttu-id="186d5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="186d5-111">SQLEngine</span></span>|  
|<span data-ttu-id="186d5-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="186d5-112">Symbolic Name</span></span>|<span data-ttu-id="186d5-113">DBCC4_INCORRECT_PAGE_ID_IN_HEADER_NO_METADATA</span><span class="sxs-lookup"><span data-stu-id="186d5-113">DBCC4_INCORRECT_PAGE_ID_IN_HEADER_NO_METADATA</span></span>|  
|<span data-ttu-id="186d5-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="186d5-114">Message Text</span></span>|<span data-ttu-id="186d5-115">表错误：分配单元 ID A_ID，页 P_ID1 在页头中包含错误的页 ID。</span><span class="sxs-lookup"><span data-stu-id="186d5-115">Table error: alloc unit ID A_ID, page P_ID1 contains an incorrect page ID in its page header.</span></span> <span data-ttu-id="186d5-116">该页头中的 PageId 为 P_ID2。</span><span class="sxs-lookup"><span data-stu-id="186d5-116">The PageId in the page header = P_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="186d5-117">说明</span><span class="sxs-lookup"><span data-stu-id="186d5-117">Explanation</span></span>  
 <span data-ttu-id="186d5-118">页 *P_ID1* 的页眉包含错误的页 ID *P_ID2*。</span><span class="sxs-lookup"><span data-stu-id="186d5-118">The page header of page *P_ID1* contains an incorrect page ID, *P_ID2*.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="186d5-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="186d5-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="186d5-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="186d5-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="186d5-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="186d5-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="186d5-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="186d5-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="186d5-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="186d5-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="186d5-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="186d5-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="186d5-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="186d5-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="186d5-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="186d5-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="186d5-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="186d5-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="186d5-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="186d5-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="186d5-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="186d5-129">Restore from Backup</span></span>  
 <span data-ttu-id="186d5-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="186d5-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="186d5-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="186d5-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="186d5-132">不适用。</span><span class="sxs-lookup"><span data-stu-id="186d5-132">Not applicable.</span></span> <span data-ttu-id="186d5-133">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="186d5-133">This error cannot be repaired.</span></span> <span data-ttu-id="186d5-134">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="186d5-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  