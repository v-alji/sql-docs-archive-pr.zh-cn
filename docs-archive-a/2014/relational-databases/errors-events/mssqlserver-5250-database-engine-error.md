---
title: MSSQLSERVER_5250 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5250 (Database Engine error)
ms.assetid: f4a1d0e8-f27f-4cb8-a25d-040b40555dcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace26b88aca5b00c23aff3fe48f7c1d04ef35245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690618"
---
# <a name="mssqlserver_5250"></a><span data-ttu-id="2ec04-102">MSSQLSERVER_5250</span><span class="sxs-lookup"><span data-stu-id="2ec04-102">MSSQLSERVER_5250</span></span>
    
## <a name="details"></a><span data-ttu-id="2ec04-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2ec04-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ec04-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2ec04-104">Product Name</span></span>|<span data-ttu-id="2ec04-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2ec04-105">SQL Server</span></span>|  
|<span data-ttu-id="2ec04-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2ec04-106">Event ID</span></span>|<span data-ttu-id="2ec04-107">5250</span><span class="sxs-lookup"><span data-stu-id="2ec04-107">5250</span></span>|  
|<span data-ttu-id="2ec04-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2ec04-108">Event Source</span></span>|<span data-ttu-id="2ec04-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2ec04-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2ec04-110">组件</span><span class="sxs-lookup"><span data-stu-id="2ec04-110">Component</span></span>|<span data-ttu-id="2ec04-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2ec04-111">SQLEngine</span></span>|  
|<span data-ttu-id="2ec04-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2ec04-112">Symbolic Name</span></span>|<span data-ttu-id="2ec04-113">DBCC4_CRITICAL_DATABASE_PAGE_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="2ec04-113">DBCC4_CRITICAL_DATABASE_PAGE_CORRUPT</span></span>|  
|<span data-ttu-id="2ec04-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="2ec04-114">Message Text</span></span>|<span data-ttu-id="2ec04-115">数据库错误:数据库 NAME（数据库 ID DB_ID）的 PAGE_TYPE 页 P_ID 无效。</span><span class="sxs-lookup"><span data-stu-id="2ec04-115">Database error: PAGE_TYPE page P_ID for database 'NAME' (database ID DB_ID) is invalid.</span></span> <span data-ttu-id="2ec04-116">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="2ec04-116">This error cannot be repaired.</span></span> <span data-ttu-id="2ec04-117">您必须通过备份还原。</span><span class="sxs-lookup"><span data-stu-id="2ec04-117">You must restore from backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2ec04-118">说明</span><span class="sxs-lookup"><span data-stu-id="2ec04-118">Explanation</span></span>  
 <span data-ttu-id="2ec04-119">指定数据库中的文件头页或引导页已损坏。</span><span class="sxs-lookup"><span data-stu-id="2ec04-119">A file header page or boot page in the specified database is corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2ec04-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="2ec04-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2ec04-121">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="2ec04-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2ec04-122">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="2ec04-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2ec04-123">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="2ec04-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="2ec04-124">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="2ec04-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2ec04-125">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="2ec04-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2ec04-126">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="2ec04-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2ec04-127">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="2ec04-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2ec04-128">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="2ec04-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2ec04-129">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="2ec04-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2ec04-130">从备份还原</span><span class="sxs-lookup"><span data-stu-id="2ec04-130">Restore from Backup</span></span>  
 <span data-ttu-id="2ec04-131">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="2ec04-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="2ec04-132">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="2ec04-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="2ec04-133">不适用。</span><span class="sxs-lookup"><span data-stu-id="2ec04-133">Not applicable.</span></span> <span data-ttu-id="2ec04-134">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="2ec04-134">This error cannot be repaired.</span></span> <span data-ttu-id="2ec04-135">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="2ec04-135">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
