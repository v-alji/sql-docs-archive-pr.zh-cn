---
title: MSSQLSERVER_7932 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7932 (Database Engine error)
ms.assetid: e2ad218a-3249-4f18-8b32-09f0030765a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 237d9be3e0f22664adb061d3bba526c9878d3bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587404"
---
# <a name="mssqlserver_7932"></a><span data-ttu-id="d36e3-102">MSSQLSERVER_7932</span><span class="sxs-lookup"><span data-stu-id="d36e3-102">MSSQLSERVER_7932</span></span>
    
## <a name="details"></a><span data-ttu-id="d36e3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d36e3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d36e3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d36e3-104">Product Name</span></span>|<span data-ttu-id="d36e3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d36e3-105">SQL Server</span></span>|  
|<span data-ttu-id="d36e3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d36e3-106">Event ID</span></span>|<span data-ttu-id="d36e3-107">7932</span><span class="sxs-lookup"><span data-stu-id="d36e3-107">7932</span></span>|  
|<span data-ttu-id="d36e3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d36e3-108">Event Source</span></span>|<span data-ttu-id="d36e3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d36e3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d36e3-110">组件</span><span class="sxs-lookup"><span data-stu-id="d36e3-110">Component</span></span>|<span data-ttu-id="d36e3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d36e3-111">SQLEngine</span></span>|  
|<span data-ttu-id="d36e3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d36e3-112">Symbolic Name</span></span>|<span data-ttu-id="d36e3-113">DBCC2_FS_ROWSET_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="d36e3-113">DBCC2_FS_ROWSET_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="d36e3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d36e3-114">Message Text</span></span>|<span data-ttu-id="d36e3-115">表错误:对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID 的 FileStream 目录 ID F_ID 位于文件组 FG_ID1 中，但该目录应位于文件组 FG_ID2 中。</span><span class="sxs-lookup"><span data-stu-id="d36e3-115">Table error: The FileStream directory ID F_ID for object ID O_ID, index ID I_ID, partition ID PN_ID is in filegroup FG_ID1, but should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d36e3-116">说明</span><span class="sxs-lookup"><span data-stu-id="d36e3-116">Explanation</span></span>  
 <span data-ttu-id="d36e3-117">在运行 DBCC CHECKDB 期间，在错误的文件组中检测到指定对象的 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="d36e3-117">During DBCC CHECKDB, the FILESTREAM storage for the specified object was detected in the wrong filegroup.</span></span> <span data-ttu-id="d36e3-118">这可能是由于对象元数据损坏。</span><span class="sxs-lookup"><span data-stu-id="d36e3-118">This could be a corruption in the metadata of the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d36e3-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="d36e3-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d36e3-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="d36e3-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d36e3-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="d36e3-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d36e3-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="d36e3-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d36e3-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="d36e3-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d36e3-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="d36e3-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d36e3-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="d36e3-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d36e3-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="d36e3-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d36e3-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="d36e3-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d36e3-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="d36e3-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d36e3-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="d36e3-129">Restore from Backup</span></span>  
 <span data-ttu-id="d36e3-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="d36e3-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d36e3-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="d36e3-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d36e3-132">不适用。</span><span class="sxs-lookup"><span data-stu-id="d36e3-132">Not applicable.</span></span> <span data-ttu-id="d36e3-133">此错误无法自动修复。</span><span class="sxs-lookup"><span data-stu-id="d36e3-133">This error cannot be repaired automatically.</span></span> <span data-ttu-id="d36e3-134">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="d36e3-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
