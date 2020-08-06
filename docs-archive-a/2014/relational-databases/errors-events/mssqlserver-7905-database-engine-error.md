---
title: MSSQLSERVER_7905 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7905 (Database Engine error)
ms.assetid: cf19fbbb-7158-45f2-8778-8f3cad7f574a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 253bf03c1bfacccfd809cd417163eb9d54644f28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586704"
---
# <a name="mssqlserver_7905"></a><span data-ttu-id="1a5ce-102">MSSQLSERVER_7905</span><span class="sxs-lookup"><span data-stu-id="1a5ce-102">MSSQLSERVER_7905</span></span>
    
## <a name="details"></a><span data-ttu-id="1a5ce-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="1a5ce-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a5ce-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="1a5ce-104">Product Name</span></span>|<span data-ttu-id="1a5ce-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1a5ce-105">SQL Server</span></span>|  
|<span data-ttu-id="1a5ce-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="1a5ce-106">Event ID</span></span>|<span data-ttu-id="1a5ce-107">7905</span><span class="sxs-lookup"><span data-stu-id="1a5ce-107">7905</span></span>|  
|<span data-ttu-id="1a5ce-108">事件源</span><span class="sxs-lookup"><span data-stu-id="1a5ce-108">Event Source</span></span>|<span data-ttu-id="1a5ce-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1a5ce-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1a5ce-110">组件</span><span class="sxs-lookup"><span data-stu-id="1a5ce-110">Component</span></span>|<span data-ttu-id="1a5ce-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1a5ce-111">SQLEngine</span></span>|  
|<span data-ttu-id="1a5ce-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="1a5ce-112">Symbolic Name</span></span>|<span data-ttu-id="1a5ce-113">DBCC2_FS_INVALID_ROWSET_DIRECTORY</span><span class="sxs-lookup"><span data-stu-id="1a5ce-113">DBCC2_FS_INVALID_ROWSET_DIRECTORY</span></span>|  
|<span data-ttu-id="1a5ce-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="1a5ce-114">Message Text</span></span>|<span data-ttu-id="1a5ce-115">数据库错误:目录 DIRECTORY 不是有效的 FileStream 目录。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-115">Database error: The directory 'DIRECTORY' is not a valid Filestream directory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a5ce-116">说明</span><span class="sxs-lookup"><span data-stu-id="1a5ce-116">Explanation</span></span>  
 <span data-ttu-id="1a5ce-117">行集目录的名称是分区的分区 ID，但特殊的行集目录名称（如“ghost”）除外。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-117">The name of a rowset directory is the partition ID of the partition, except for the special rowset directory names such as 'ghost'.</span></span> <span data-ttu-id="1a5ce-118">如果无法将行集目录名称转换为分区 ID，则该目录不是有效的行集目录。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-118">If a rowset directory name cannot be converted to a partition ID, the directory is not a valid rowset directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a5ce-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="1a5ce-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="1a5ce-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="1a5ce-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="1a5ce-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="1a5ce-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="1a5ce-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="1a5ce-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="1a5ce-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="1a5ce-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="1a5ce-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="1a5ce-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="1a5ce-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="1a5ce-129">Restore from Backup</span></span>  
 <span data-ttu-id="1a5ce-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="1a5ce-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="1a5ce-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="1a5ce-132">不适用。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-132">Not applicable.</span></span> <span data-ttu-id="1a5ce-133">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-133">This error cannot be repaired.</span></span> <span data-ttu-id="1a5ce-134">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="1a5ce-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
