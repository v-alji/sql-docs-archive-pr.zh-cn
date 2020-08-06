---
title: MSSQLSERVER_7936 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7936 (Database Engine error)
ms.assetid: d78fc8a9-d173-4801-bb32-ed6a29257f08
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c478e998b6185b0a8e22cd99caf2be4fc2fdee33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589128"
---
# <a name="mssqlserver_7936"></a><span data-ttu-id="2c25c-102">MSSQLSERVER_7936</span><span class="sxs-lookup"><span data-stu-id="2c25c-102">MSSQLSERVER_7936</span></span>
    
## <a name="details"></a><span data-ttu-id="2c25c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2c25c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c25c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2c25c-104">Product Name</span></span>|<span data-ttu-id="2c25c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2c25c-105">SQL Server</span></span>|  
|<span data-ttu-id="2c25c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2c25c-106">Event ID</span></span>|<span data-ttu-id="2c25c-107">7936</span><span class="sxs-lookup"><span data-stu-id="2c25c-107">7936</span></span>|  
|<span data-ttu-id="2c25c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2c25c-108">Event Source</span></span>|<span data-ttu-id="2c25c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2c25c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2c25c-110">组件</span><span class="sxs-lookup"><span data-stu-id="2c25c-110">Component</span></span>|<span data-ttu-id="2c25c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2c25c-111">SQLEngine</span></span>|  
|<span data-ttu-id="2c25c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2c25c-112">Symbolic Name</span></span>|<span data-ttu-id="2c25c-113">DBCC2_FS_ORPHANED_COLUMN_DIRECTORY</span><span class="sxs-lookup"><span data-stu-id="2c25c-113">DBCC2_FS_ORPHANED_COLUMN_DIRECTORY</span></span>|  
|<span data-ttu-id="2c25c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="2c25c-114">Message Text</span></span>|<span data-ttu-id="2c25c-115">表错误:存在对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID 的列 ID C_ID 的 Filestream 目录，但该列不是 Filestream 列。</span><span class="sxs-lookup"><span data-stu-id="2c25c-115">Table error: Filestream directory exists for column ID C_ID of object ID O_ID, index ID I_ID, partition ID PN_ID, but that column is not a Filestream column.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2c25c-116">说明</span><span class="sxs-lookup"><span data-stu-id="2c25c-116">Explanation</span></span>  
 <span data-ttu-id="2c25c-117">在运行 DBCC CHECKDB 期间，发现指定列的 FILESTREAM 目录；但该列不是 `FILESTREAM` 列。</span><span class="sxs-lookup"><span data-stu-id="2c25c-117">During DBCC CHECKDB, a FILESTREAM directory was found for the specified column; however, the column is not a `FILESTREAM` column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2c25c-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="2c25c-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2c25c-119">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="2c25c-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2c25c-120">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="2c25c-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2c25c-121">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="2c25c-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="2c25c-122">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="2c25c-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2c25c-123">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="2c25c-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2c25c-124">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="2c25c-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2c25c-125">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="2c25c-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2c25c-126">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="2c25c-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2c25c-127">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="2c25c-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2c25c-128">从备份还原</span><span class="sxs-lookup"><span data-stu-id="2c25c-128">Restore from Backup</span></span>  
 <span data-ttu-id="2c25c-129">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="2c25c-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="2c25c-130">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="2c25c-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="2c25c-131">不适用。</span><span class="sxs-lookup"><span data-stu-id="2c25c-131">Not applicable.</span></span> <span data-ttu-id="2c25c-132">此错误无法自动修复。</span><span class="sxs-lookup"><span data-stu-id="2c25c-132">This error cannot be repaired automatically.</span></span> <span data-ttu-id="2c25c-133">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="2c25c-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
