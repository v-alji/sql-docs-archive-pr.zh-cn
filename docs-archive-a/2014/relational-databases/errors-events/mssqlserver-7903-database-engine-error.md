---
title: MSSQLSERVER_7903 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7903 (Database Engine error)
ms.assetid: 991a86df-42cd-435e-85b3-f42e4cb13039
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e30247c5c858cf8ce6dcd75e41f1fb567e974201
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586706"
---
# <a name="mssqlserver_7903"></a><span data-ttu-id="b2a25-102">MSSQLSERVER_7903</span><span class="sxs-lookup"><span data-stu-id="b2a25-102">MSSQLSERVER_7903</span></span>
    
## <a name="details"></a><span data-ttu-id="b2a25-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b2a25-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2a25-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b2a25-104">Product Name</span></span>|<span data-ttu-id="b2a25-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b2a25-105">SQL Server</span></span>|  
|<span data-ttu-id="b2a25-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b2a25-106">Event ID</span></span>|<span data-ttu-id="b2a25-107">7903</span><span class="sxs-lookup"><span data-stu-id="b2a25-107">7903</span></span>|  
|<span data-ttu-id="b2a25-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b2a25-108">Event Source</span></span>|<span data-ttu-id="b2a25-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b2a25-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b2a25-110">组件</span><span class="sxs-lookup"><span data-stu-id="b2a25-110">Component</span></span>|<span data-ttu-id="b2a25-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b2a25-111">SQLEngine</span></span>|  
|<span data-ttu-id="b2a25-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b2a25-112">Symbolic Name</span></span>|<span data-ttu-id="b2a25-113">DBCC2_FS_ORPHANED_FILE</span><span class="sxs-lookup"><span data-stu-id="b2a25-113">DBCC2_FS_ORPHANED_FILE</span></span>|  
|<span data-ttu-id="b2a25-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b2a25-114">Message Text</span></span>|<span data-ttu-id="b2a25-115">表错误:在对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，列 ID C_ID 的 FileStream 目录中发现孤立文件“FILE”。</span><span class="sxs-lookup"><span data-stu-id="b2a25-115">Table error: The orphaned file 'FILE' was found in the Filestream directory for object ID O_ID, index ID I_ID, partition ID PN_ID, column ID C_ID.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2a25-116">说明</span><span class="sxs-lookup"><span data-stu-id="b2a25-116">Explanation</span></span>  
 <span data-ttu-id="b2a25-117">在 FILESTREAM 列目录中发现了 FILESTREAM 文件，但是在分区中缺少对应的列值。</span><span class="sxs-lookup"><span data-stu-id="b2a25-117">A FILESTREAM file was found in a FILESTREAM column directory; however, the corresponding column value in the partition is missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2a25-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="b2a25-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="b2a25-119">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="b2a25-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="b2a25-120">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="b2a25-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="b2a25-121">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="b2a25-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="b2a25-122">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="b2a25-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="b2a25-123">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="b2a25-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="b2a25-124">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="b2a25-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="b2a25-125">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b2a25-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="b2a25-126">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="b2a25-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="b2a25-127">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="b2a25-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="b2a25-128">从备份还原</span><span class="sxs-lookup"><span data-stu-id="b2a25-128">Restore from Backup</span></span>  
 <span data-ttu-id="b2a25-129">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="b2a25-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="b2a25-130">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="b2a25-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="b2a25-131">不适用。</span><span class="sxs-lookup"><span data-stu-id="b2a25-131">Not applicable.</span></span> <span data-ttu-id="b2a25-132">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="b2a25-132">This error cannot be repaired.</span></span> <span data-ttu-id="b2a25-133">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="b2a25-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
