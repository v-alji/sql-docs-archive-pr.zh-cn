---
title: MSSQLSERVER_5233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5233 (Database Engine error)
ms.assetid: 7a855afa-2d3b-49b7-adef-197b99fc98b1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a5e2c603652534a6d3093a01da0a926a7195954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589587"
---
# <a name="mssqlserver_5233"></a><span data-ttu-id="05de0-102">MSSQLSERVER_5233</span><span class="sxs-lookup"><span data-stu-id="05de0-102">MSSQLSERVER_5233</span></span>
    
## <a name="details"></a><span data-ttu-id="05de0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="05de0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05de0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="05de0-104">Product Name</span></span>|<span data-ttu-id="05de0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="05de0-105">SQL Server</span></span>|  
|<span data-ttu-id="05de0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="05de0-106">Event ID</span></span>|<span data-ttu-id="05de0-107">5233</span><span class="sxs-lookup"><span data-stu-id="05de0-107">5233</span></span>|  
|<span data-ttu-id="05de0-108">事件源</span><span class="sxs-lookup"><span data-stu-id="05de0-108">Event Source</span></span>|<span data-ttu-id="05de0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="05de0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="05de0-110">组件</span><span class="sxs-lookup"><span data-stu-id="05de0-110">Component</span></span>|<span data-ttu-id="05de0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="05de0-111">SQLEngine</span></span>|  
|<span data-ttu-id="05de0-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="05de0-112">Symbolic Name</span></span>|<span data-ttu-id="05de0-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span><span class="sxs-lookup"><span data-stu-id="05de0-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span></span>|  
|<span data-ttu-id="05de0-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="05de0-114">Message Text</span></span>|<span data-ttu-id="05de0-115">表错误: 分配单元 ID A_ID，页 P_ID。</span><span class="sxs-lookup"><span data-stu-id="05de0-115">Table error: alloc unit ID A_ID, page P_ID.</span></span> <span data-ttu-id="05de0-116">测试 (TEST) 失败。</span><span class="sxs-lookup"><span data-stu-id="05de0-116">The test (TEST) failed.</span></span> <span data-ttu-id="05de0-117">值是 VAL1 和 VAL2。</span><span class="sxs-lookup"><span data-stu-id="05de0-117">The values are VAL1 and VAL2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05de0-118">说明</span><span class="sxs-lookup"><span data-stu-id="05de0-118">Explanation</span></span>  
 <span data-ttu-id="05de0-119">由于页 *P_ID* 的页眉中有损坏，因此该页未通过审核。</span><span class="sxs-lookup"><span data-stu-id="05de0-119">Page *P_ID* has failed auditing due to a corruption in its page header.</span></span> <span data-ttu-id="05de0-120">TEST 中的字符串提供了发生失败的实际测试。</span><span class="sxs-lookup"><span data-stu-id="05de0-120">The string in TEST gives the actual test that failed.</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="05de0-121">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="05de0-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="05de0-122">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="05de0-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="05de0-123">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="05de0-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="05de0-124">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="05de0-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="05de0-125">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="05de0-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="05de0-126">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="05de0-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="05de0-127">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="05de0-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="05de0-128">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="05de0-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="05de0-129">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="05de0-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="05de0-130">从备份还原</span><span class="sxs-lookup"><span data-stu-id="05de0-130">Restore from Backup</span></span>  
 <span data-ttu-id="05de0-131">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="05de0-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="05de0-132">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="05de0-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="05de0-133">不适用。</span><span class="sxs-lookup"><span data-stu-id="05de0-133">Not applicable.</span></span> <span data-ttu-id="05de0-134">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="05de0-134">This error cannot be repaired.</span></span> <span data-ttu-id="05de0-135">如果无法从备份还原数据库，请与 Microsoft 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="05de0-135">If you cannot restore the database from a backup, contact Microsoft Customer Service and Support (CSS).</span></span>  
  
  
