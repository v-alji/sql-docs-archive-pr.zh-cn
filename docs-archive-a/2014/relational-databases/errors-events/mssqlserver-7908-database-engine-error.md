---
title: MSSQLSERVER_7908 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7908 (Database Engine error)
ms.assetid: 470045b0-ebe9-44a7-b456-480e7a516a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b80812e0e36e5bed542f7193b7422f2de37720f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586698"
---
# <a name="mssqlserver_7908"></a><span data-ttu-id="b6594-102">MSSQLSERVER_7908</span><span class="sxs-lookup"><span data-stu-id="b6594-102">MSSQLSERVER_7908</span></span>
    
## <a name="details"></a><span data-ttu-id="b6594-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b6594-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6594-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b6594-104">Product Name</span></span>|<span data-ttu-id="b6594-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6594-105">SQL Server</span></span>|  
|<span data-ttu-id="b6594-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b6594-106">Event ID</span></span>|<span data-ttu-id="b6594-107">7908</span><span class="sxs-lookup"><span data-stu-id="b6594-107">7908</span></span>|  
|<span data-ttu-id="b6594-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b6594-108">Event Source</span></span>|<span data-ttu-id="b6594-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b6594-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b6594-110">组件</span><span class="sxs-lookup"><span data-stu-id="b6594-110">Component</span></span>|<span data-ttu-id="b6594-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b6594-111">SQLEngine</span></span>|  
|<span data-ttu-id="b6594-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b6594-112">Symbolic Name</span></span>|<span data-ttu-id="b6594-113">DBCC2_FS_INVALID_COLUMN_LEVEL_FILE</span><span class="sxs-lookup"><span data-stu-id="b6594-113">DBCC2_FS_INVALID_COLUMN_LEVEL_FILE</span></span>|  
|<span data-ttu-id="b6594-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b6594-114">Message Text</span></span>|<span data-ttu-id="b6594-115">表错误:分区 ID PN_ID 中的文件 FILE 不是有效的 Filestream 文件。</span><span class="sxs-lookup"><span data-stu-id="b6594-115">Table error: The file 'FILE' in partition ID PN_ID is not a valid Filestream file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b6594-116">说明</span><span class="sxs-lookup"><span data-stu-id="b6594-116">Explanation</span></span>  
 <span data-ttu-id="b6594-117">列目录中 FILESTREAM 文件的名称为 ROWGUID。</span><span class="sxs-lookup"><span data-stu-id="b6594-117">The name of a FILESTREAM file in a column directory is a ROWGUID.</span></span> <span data-ttu-id="b6594-118">如果无法将列目录中的文件名转换为 ROWGUID，则该文件不是有效文件。</span><span class="sxs-lookup"><span data-stu-id="b6594-118">If a file name in a column directory cannot be converted to a ROWGUID, the file is not a valid file.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b6594-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="b6594-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="b6594-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="b6594-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="b6594-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="b6594-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="b6594-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="b6594-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="b6594-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="b6594-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="b6594-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="b6594-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="b6594-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="b6594-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="b6594-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b6594-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="b6594-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="b6594-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="b6594-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="b6594-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="b6594-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="b6594-129">Restore from Backup</span></span>  
 <span data-ttu-id="b6594-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="b6594-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="b6594-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="b6594-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="b6594-132">不适用。</span><span class="sxs-lookup"><span data-stu-id="b6594-132">Not applicable.</span></span> <span data-ttu-id="b6594-133">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="b6594-133">This error cannot be repaired.</span></span> <span data-ttu-id="b6594-134">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="b6594-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
