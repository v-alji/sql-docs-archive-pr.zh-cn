---
title: MSSQLSERVER_823 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa5858bbdc9452a33a3d43fdd783e59556a11e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586695"
---
# <a name="mssqlserver_823"></a><span data-ttu-id="3bf8c-102">MSSQLSERVER_823</span><span class="sxs-lookup"><span data-stu-id="3bf8c-102">MSSQLSERVER_823</span></span>
    
## <a name="details"></a><span data-ttu-id="3bf8c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="3bf8c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bf8c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="3bf8c-104">Product Name</span></span>|<span data-ttu-id="3bf8c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3bf8c-105">SQL Server</span></span>|  
|<span data-ttu-id="3bf8c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3bf8c-106">Event ID</span></span>|<span data-ttu-id="3bf8c-107">823</span><span class="sxs-lookup"><span data-stu-id="3bf8c-107">823</span></span>|  
|<span data-ttu-id="3bf8c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="3bf8c-108">Event Source</span></span>|<span data-ttu-id="3bf8c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3bf8c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3bf8c-110">组件</span><span class="sxs-lookup"><span data-stu-id="3bf8c-110">Component</span></span>|<span data-ttu-id="3bf8c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3bf8c-111">SQLEngine</span></span>|  
|<span data-ttu-id="3bf8c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="3bf8c-112">Symbolic Name</span></span>|<span data-ttu-id="3bf8c-113">B_HARDERR</span><span class="sxs-lookup"><span data-stu-id="3bf8c-113">B_HARDERR</span></span>|  
|<span data-ttu-id="3bf8c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="3bf8c-114">Message Text</span></span>|<span data-ttu-id="3bf8c-115">在文件 '%ls' 中、偏移量为 %#016I64x 的位置执行 %S_MSG 期间，操作系统已经向 SQL Server 返回了错误 %ls。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-115">The operating system returned error %ls to SQL Server during a %S_MSG at offset %#016I64x in file '%ls'.</span></span> <span data-ttu-id="3bf8c-116">SQL Server 错误日志和系统事件日志中的其他消息中可能有更详细的信息。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="3bf8c-117">这是一个威胁数据库完整性的严重系统级错误条件，必须立即纠正。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-117">This is a severe system-level error condition that threatens database integrity and must be corrected immediately.</span></span> <span data-ttu-id="3bf8c-118">请运行一次完整的数据库一致性检查 (DBCC CHECKDB)。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="3bf8c-119">此错误可能是由多种因素导致的；有关详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3bf8c-120">说明</span><span class="sxs-lookup"><span data-stu-id="3bf8c-120">Explanation</span></span>  
 <span data-ttu-id="3bf8c-121">Windows 读取或写入请求失败。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-121">A Windows read or write request has failed.</span></span> <span data-ttu-id="3bf8c-122">将 Windows 返回的错误代码和相应的文本插入到消息中。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-122">The error code that is returned by Windows and the corresponding text are inserted into the message.</span></span> <span data-ttu-id="3bf8c-123">对于读取操作，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已经重试读取请求四次。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-123">In the read case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will have already retried the read request four times.</span></span> <span data-ttu-id="3bf8c-124">通常是硬件错误导致此错误，但也可能是设备驱动程序导致的。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-124">This error is often the result of a hardware error, but may be caused by the device driver.</span></span> <span data-ttu-id="3bf8c-125">有关错误823的详细信息，请参阅 [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339) 。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-125">For more information about error 823, see [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339).</span></span> <span data-ttu-id="3bf8c-126">有关 I/O 错误的详细信息，请参阅 [Microsoft SQL Server I/O 基础知识，第 2 章](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-126">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3bf8c-127">用户操作</span><span class="sxs-lookup"><span data-stu-id="3bf8c-127">User Action</span></span>  
 <span data-ttu-id="3bf8c-128">查看系统事件日志中的其他信息。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-128">Check for additional information in the system event log.</span></span> <span data-ttu-id="3bf8c-129">与硬件制造商或 Microsoft 客户服务与支持部门联系，以确定原因和纠正操作。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-129">Contact the hardware manufacturer or Microsoft Customer Services and Support to determine the cause and corrective action.</span></span> <span data-ttu-id="3bf8c-130">在修复硬件错误后，还原所有数据库并运行 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="3bf8c-130">After the hardware error is fixed, restore all databases and run DBCC CHECKDB.</span></span>  
  
  
