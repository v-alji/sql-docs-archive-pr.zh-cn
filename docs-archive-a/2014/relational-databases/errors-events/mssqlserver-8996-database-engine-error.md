---
title: MSSQLSERVER_8996 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8996 (Database Engine error)
ms.assetid: 4e655cdc-945a-4a18-95dd-75f050563d26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d0cb5f0294ea471a6e300adbabc0f7b55632994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589576"
---
# <a name="mssqlserver_8996"></a><span data-ttu-id="cfeb0-102">MSSQLSERVER_8996</span><span class="sxs-lookup"><span data-stu-id="cfeb0-102">MSSQLSERVER_8996</span></span>
    
## <a name="details"></a><span data-ttu-id="cfeb0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cfeb0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cfeb0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cfeb0-104">Product Name</span></span>|<span data-ttu-id="cfeb0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cfeb0-105">SQL Server</span></span>|  
|<span data-ttu-id="cfeb0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cfeb0-106">Event ID</span></span>|<span data-ttu-id="cfeb0-107">8996</span><span class="sxs-lookup"><span data-stu-id="cfeb0-107">8996</span></span>|  
|<span data-ttu-id="cfeb0-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cfeb0-108">Event Source</span></span>|<span data-ttu-id="cfeb0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cfeb0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cfeb0-110">组件</span><span class="sxs-lookup"><span data-stu-id="cfeb0-110">Component</span></span>|<span data-ttu-id="cfeb0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cfeb0-111">SQLEngine</span></span>|  
|<span data-ttu-id="cfeb0-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cfeb0-112">Symbolic Name</span></span>|<span data-ttu-id="cfeb0-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="cfeb0-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="cfeb0-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cfeb0-114">Message Text</span></span>|<span data-ttu-id="cfeb0-115">对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）的 IAM 页 P_ID 控制着文件组 FG_ID1 中的页，这些页应该在文件组 FG_ID2 中。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-115">IAM page P_ID for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) controls pages in filegroup FG_ID1, that should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cfeb0-116">说明</span><span class="sxs-lookup"><span data-stu-id="cfeb0-116">Explanation</span></span>  
 <span data-ttu-id="cfeb0-117">文件组 *FG_ID1* 中的索引分配映射 (IAM) 页 *P_ID* 错误地包括了文件组 *FG_ID2* 的区数。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-117">The index allocation map (IAM) page *P_ID* in filegroup *FG_ID1* incorrectly includes extents from filegroup *FG_ID2*.</span></span> <span data-ttu-id="cfeb0-118">IAM 页的所有区都应该在与 IAM 页本身相同的文件组中。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-118">All extents for an IAM page should be in the same filegroup as the IAM page itself.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cfeb0-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="cfeb0-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="cfeb0-120">查找硬件故障</span><span class="sxs-lookup"><span data-stu-id="cfeb0-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="cfeb0-121">运行硬件诊断并更正任何问题。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="cfeb0-122">也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="cfeb0-123">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="cfeb0-124">如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="cfeb0-125">进行检查以确保系统未启用磁盘控制器上的写缓存。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="cfeb0-126">如果怀疑写入缓存是问题起因，请与硬件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="cfeb0-127">最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="cfeb0-128">此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="cfeb0-129">从备份还原</span><span class="sxs-lookup"><span data-stu-id="cfeb0-129">Restore from Backup</span></span>  
 <span data-ttu-id="cfeb0-130">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="cfeb0-131">运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="cfeb0-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="cfeb0-132">不适用。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-132">Not applicable.</span></span> <span data-ttu-id="cfeb0-133">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-133">This error cannot be repaired.</span></span> <span data-ttu-id="cfeb0-134">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="cfeb0-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
