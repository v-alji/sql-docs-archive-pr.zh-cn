---
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e20018c0fe1cd0748f4930e0022622adcbfad10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586685"
---
# <a name="mssqlserver_833"></a><span data-ttu-id="f088c-102">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="f088c-102">MSSQLSERVER_833</span></span>
    
## <a name="details"></a><span data-ttu-id="f088c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f088c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f088c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f088c-104">Product Name</span></span>|<span data-ttu-id="f088c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f088c-105">SQL Server</span></span>|  
|<span data-ttu-id="f088c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f088c-106">Event ID</span></span>|<span data-ttu-id="f088c-107">833</span><span class="sxs-lookup"><span data-stu-id="f088c-107">833</span></span>|  
|<span data-ttu-id="f088c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f088c-108">Event Source</span></span>|<span data-ttu-id="f088c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f088c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f088c-110">组件</span><span class="sxs-lookup"><span data-stu-id="f088c-110">Component</span></span>|<span data-ttu-id="f088c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f088c-111">SQLEngine</span></span>|  
|<span data-ttu-id="f088c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f088c-112">Symbolic Name</span></span>|<span data-ttu-id="f088c-113">BUF_LONG_IO</span><span class="sxs-lookup"><span data-stu-id="f088c-113">BUF_LONG_IO</span></span>|  
|<span data-ttu-id="f088c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f088c-114">Message Text</span></span>|<span data-ttu-id="f088c-115">SQL Server 在数据库中的文件 [% ls] 上遇到超过% d 秒的 i/o 请求) 出现% d 次 (。 `[%ls] (%d)`</span><span class="sxs-lookup"><span data-stu-id="f088c-115">SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database`[%ls] (%d)`.</span></span>  <span data-ttu-id="f088c-116">OS 文件句柄是 0x%p。</span><span class="sxs-lookup"><span data-stu-id="f088c-116">The OS file handle is 0x%p.</span></span>  <span data-ttu-id="f088c-117">最新的长时间 I/O 操作的偏移量是: %#016I64x。</span><span class="sxs-lookup"><span data-stu-id="f088c-117">The offset of the latest long I/O is: %#016I64x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f088c-118">说明</span><span class="sxs-lookup"><span data-stu-id="f088c-118">Explanation</span></span>  
 <span data-ttu-id="f088c-119">该消息指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已从磁盘发出读取或写入请求，并且表明该请求返回所用的时间已超过 15 秒。</span><span class="sxs-lookup"><span data-stu-id="f088c-119">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="f088c-120">该错误由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 报告，表明 IO 子系统有问题。</span><span class="sxs-lookup"><span data-stu-id="f088c-120">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the IO subsystem.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="f088c-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="f088c-121">Possible Causes</span></span>  
 <span data-ttu-id="f088c-122">这种问题可能是由于系统性能问题、硬件错误、固件错误、设备驱动程序问题或 IO 进程中的筛选器驱动程序干预引起的。</span><span class="sxs-lookup"><span data-stu-id="f088c-122">This problem can be caused system performance issues, hardware errors, firmware errors, device driver problems, or filter driver intervention in the IO process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f088c-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="f088c-123">User Action</span></span>  
 <span data-ttu-id="f088c-124">通过检查系统事件日志获得硬件相关错误消息来纠正引错误。</span><span class="sxs-lookup"><span data-stu-id="f088c-124">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="f088c-125">并且，如果有特定于硬件的日志，也要进行检查。</span><span class="sxs-lookup"><span data-stu-id="f088c-125">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="f088c-126">使用性能监视器检查以下计数器：</span><span class="sxs-lookup"><span data-stu-id="f088c-126">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="f088c-127">**Average Disk Sec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="f088c-127">**Average Disk Sec/Transfer**</span></span>  
  
-   <span data-ttu-id="f088c-128">**Average Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="f088c-128">**Average Disk Queue Length**</span></span>  
  
-   <span data-ttu-id="f088c-129">**Current Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="f088c-129">**Current Disk Queue Length**</span></span>  
  
 <span data-ttu-id="f088c-130">例如，运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机上的 **Average Disk Sec/Transfer** 时间通常少于 15 毫秒。</span><span class="sxs-lookup"><span data-stu-id="f088c-130">For example, the **Average Disk Sec/Transfer** time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="f088c-131">如果 **Average Disk Sec/Transfer** 值增加，这表明 I/O 子系统未能完全满足 I/O 需求。</span><span class="sxs-lookup"><span data-stu-id="f088c-131">If the **Average Disk Sec/Transfer** value increases, this indicates that the I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f088c-132">防病毒程序可能会减慢磁盘访问速度。</span><span class="sxs-lookup"><span data-stu-id="f088c-132">Disk access can be slowed by an antivirus program.</span></span> <span data-ttu-id="f088c-133">若要提高访问速度，请将错误消息中指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据文件从实时病毒扫描中排除。</span><span class="sxs-lookup"><span data-stu-id="f088c-133">To increase access speed, exclude the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that are specified in the error message from active virus scans.</span></span>  
  
 <span data-ttu-id="f088c-134">有关 I/O 错误的详细信息，请参阅 [Microsoft SQL Server I/O 基础知识，第 2 章](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))以及 [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284) 上的知识库文章。</span><span class="sxs-lookup"><span data-stu-id="f088c-134">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) and the Knowledge Base article at [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).</span></span>  
  
  
