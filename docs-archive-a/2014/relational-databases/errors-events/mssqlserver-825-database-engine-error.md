---
title: MSSQLSERVER_825 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b17dfac371ad3c805fdbb0b5d3269fc451dd9d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581247"
---
# <a name="mssqlserver_825"></a><span data-ttu-id="b7702-102">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="b7702-102">MSSQLSERVER_825</span></span>
    
## <a name="details"></a><span data-ttu-id="b7702-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b7702-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7702-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b7702-104">Product Name</span></span>|<span data-ttu-id="b7702-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b7702-105">SQL Server</span></span>|  
|<span data-ttu-id="b7702-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b7702-106">Event ID</span></span>|<span data-ttu-id="b7702-107">825</span><span class="sxs-lookup"><span data-stu-id="b7702-107">825</span></span>|  
|<span data-ttu-id="b7702-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b7702-108">Event Source</span></span>|<span data-ttu-id="b7702-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b7702-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b7702-110">组件</span><span class="sxs-lookup"><span data-stu-id="b7702-110">Component</span></span>|<span data-ttu-id="b7702-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b7702-111">SQLEngine</span></span>|  
|<span data-ttu-id="b7702-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b7702-112">Symbolic Name</span></span>|<span data-ttu-id="b7702-113">B_RETRYWORKED</span><span class="sxs-lookup"><span data-stu-id="b7702-113">B_RETRYWORKED</span></span>|  
|<span data-ttu-id="b7702-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b7702-114">Message Text</span></span>|<span data-ttu-id="b7702-115">在失败 %d 次(错误: %ls)之后，按偏移量 %#016I64x 对文件“%ls”读取成功。</span><span class="sxs-lookup"><span data-stu-id="b7702-115">A read of the file '%ls' at offset %#016I64x succeeded after failing %d time(s) with error: %ls.</span></span> <span data-ttu-id="b7702-116">SQL Server 错误日志和系统事件日志中的其他消息中可能有更详细的信息。</span><span class="sxs-lookup"><span data-stu-id="b7702-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="b7702-117">此错误情况威胁到数据库的完整性，因此必须予以更正。</span><span class="sxs-lookup"><span data-stu-id="b7702-117">This error condition threatens database integrity and must be corrected.</span></span> <span data-ttu-id="b7702-118">请运行一次完整的数据库一致性检查 (DBCC CHECKDB)。</span><span class="sxs-lookup"><span data-stu-id="b7702-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="b7702-119">此错误可能是由多种因素导致的；有关详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="b7702-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b7702-120">说明</span><span class="sxs-lookup"><span data-stu-id="b7702-120">Explanation</span></span>  
 <span data-ttu-id="b7702-121">此消息表明至少必须重新执行一次读取操作，且磁盘硬件存在严重问题。</span><span class="sxs-lookup"><span data-stu-id="b7702-121">This message indicates that the read operation had to be reissued at least one time, and indicates a major problem with the disk hardware.</span></span> <span data-ttu-id="b7702-122">此消息当前未指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 问题，但如果不解决磁盘问题，则可能会导致数据丢失或数据库损坏。</span><span class="sxs-lookup"><span data-stu-id="b7702-122">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem, but the disk problem could cause data loss or database corruption if it is not resolved.</span></span> <span data-ttu-id="b7702-123">系统事件日志可能包含有助于诊断此问题的相关事件。</span><span class="sxs-lookup"><span data-stu-id="b7702-123">The system event log may contain related events that help to diagnose the problem.</span></span> <span data-ttu-id="b7702-124">有关 I/O 错误的详细信息，请参阅 [Microsoft SQL Server I/O 基础知识，第 2 章](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))。</span><span class="sxs-lookup"><span data-stu-id="b7702-124">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b7702-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="b7702-125">User Action</span></span>  
 <span data-ttu-id="b7702-126">下列操作可帮助您识别和解决基本问题：</span><span class="sxs-lookup"><span data-stu-id="b7702-126">The following actions may help you identify and resolve the underlying problem:</span></span>  
  
-   <span data-ttu-id="b7702-127">查阅错误日志和此消息中的变量文本以获得说明问题的线索。</span><span class="sxs-lookup"><span data-stu-id="b7702-127">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="b7702-128">检查磁盘系统。</span><span class="sxs-lookup"><span data-stu-id="b7702-128">Check your disk system.</span></span> <span data-ttu-id="b7702-129">此问题可能与磁盘、磁盘控制器、阵列卡或磁盘驱动程序有关。</span><span class="sxs-lookup"><span data-stu-id="b7702-129">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="b7702-130">与磁盘制造商联系以获得用于检查磁盘系统状态的最新实用工具。</span><span class="sxs-lookup"><span data-stu-id="b7702-130">Contact the disk manufacturer for the latest utilities for checking the status of your disk system.</span></span>  
  
-   <span data-ttu-id="b7702-131">与磁盘制造商联系以获得最新的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="b7702-131">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
  
