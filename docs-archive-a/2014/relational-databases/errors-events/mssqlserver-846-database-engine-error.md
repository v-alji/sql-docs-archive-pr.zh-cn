---
title: MSSQLSERVER_846 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 846 (Database Engine error)
ms.assetid: ccf367eb-06b0-42b8-b4d6-2b88f4a502d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b7cb6461d467090b03c246db5074ad203ce0ac3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588567"
---
# <a name="mssqlserver_846"></a><span data-ttu-id="d27c9-102">MSSQLSERVER_846</span><span class="sxs-lookup"><span data-stu-id="d27c9-102">MSSQLSERVER_846</span></span>
    
## <a name="details"></a><span data-ttu-id="d27c9-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d27c9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d27c9-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d27c9-104">Product Name</span></span>|<span data-ttu-id="d27c9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d27c9-105">SQL Server</span></span>|  
|<span data-ttu-id="d27c9-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d27c9-106">Event ID</span></span>|<span data-ttu-id="d27c9-107">846</span><span class="sxs-lookup"><span data-stu-id="d27c9-107">846</span></span>|  
|<span data-ttu-id="d27c9-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d27c9-108">Event Source</span></span>|<span data-ttu-id="d27c9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d27c9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d27c9-110">组件</span><span class="sxs-lookup"><span data-stu-id="d27c9-110">Component</span></span>|<span data-ttu-id="d27c9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d27c9-111">SQLEngine</span></span>|  
|<span data-ttu-id="d27c9-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d27c9-112">Symbolic Name</span></span>|<span data-ttu-id="d27c9-113">空值</span><span class="sxs-lookup"><span data-stu-id="d27c9-113">N/A</span></span>|  
|<span data-ttu-id="d27c9-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d27c9-114">Message Text</span></span>|<span data-ttu-id="d27c9-115">等待缓冲区闩锁时出现超时 - 类型 %d，bp %p，页 %d:%d，stat %#x，数据库 ID: %d，分配单元 ID: %I64d%ls，任务 0x%p : %d，等待时间 %d，标志 0x%I64x，所属任务 0x%p。</span><span class="sxs-lookup"><span data-stu-id="d27c9-115">A time-out occurred while waiting for buffer latch -- type %d, bp %p, page %d:%d, stat %#x, database id: %d, allocation unit Id: %I64d%ls, task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span> <span data-ttu-id="d27c9-116">将不继续等待。</span><span class="sxs-lookup"><span data-stu-id="d27c9-116">Not continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d27c9-117">说明</span><span class="sxs-lookup"><span data-stu-id="d27c9-117">Explanation</span></span>  
 <span data-ttu-id="d27c9-118">计算机可能停止响应，或在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将缓冲区闩锁错误写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志的同时可能出现超时或某些其他常规操作中断。</span><span class="sxs-lookup"><span data-stu-id="d27c9-118">A computer might stop responding, or a time-out or some other disruption of regular operations might occur at the same time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] writes buffer latch errors to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="d27c9-119">如果消息中的状态字段的值为 0x04 on，则表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在等待 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="d27c9-119">If the stat field in the message has the value of 0x04 on, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for an I/O operation.</span></span> <span data-ttu-id="d27c9-120">也可能在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中收到消息 [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md)。</span><span class="sxs-lookup"><span data-stu-id="d27c9-120">You may also receive message [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="d27c9-121">如果消息中的状态字段的值为 0x04 off，则表示存在对某个页的大量争用。</span><span class="sxs-lookup"><span data-stu-id="d27c9-121">If the stat field in the message has the value 0x04 off, there is heavy contention for a page.</span></span> <span data-ttu-id="d27c9-122">如果对象是数据页，则错误可能是由低效的代码设计引起的。</span><span class="sxs-lookup"><span data-stu-id="d27c9-122">If the object is a data page, this can be caused by inefficient code design.</span></span> <span data-ttu-id="d27c9-123">如果是非数据页，则错误可能由服务器瓶颈引起，如硬件资源不足。</span><span class="sxs-lookup"><span data-stu-id="d27c9-123">If the page is nondata, the error might be caused by server bottlenecks, such as insufficient hardware resources.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d27c9-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="d27c9-124">User Action</span></span>  
 <span data-ttu-id="d27c9-125">若要解决此问题，根据环境的不同，采取以下一个或多个步骤可能会减少或消除错误消息：</span><span class="sxs-lookup"><span data-stu-id="d27c9-125">To work around this problem, depending on your environment, one or more of the following steps might reduce or eliminate the error messages:</span></span>  
  
-   <span data-ttu-id="d27c9-126">确定是否存在硬件瓶颈。</span><span class="sxs-lookup"><span data-stu-id="d27c9-126">Determine whether you have any hardware bottlenecks.</span></span> <span data-ttu-id="d27c9-127">如有必要，请升级您的硬件以便能够支持环境的配置、查询和负载要求。</span><span class="sxs-lookup"><span data-stu-id="d27c9-127">If it is necessary, upgrade your hardware so that it can support the configuration, query, and load requirements of your environment.</span></span> <span data-ttu-id="d27c9-128">有关瓶颈的详细信息，请参阅[识别瓶颈](../performance/identify-bottlenecks.md)。</span><span class="sxs-lookup"><span data-stu-id="d27c9-128">For more information about bottlenecks, see [Identify Bottlenecks](../performance/identify-bottlenecks.md).</span></span>  
  
-   <span data-ttu-id="d27c9-129">检查任何已记录的错误并运行硬件供应商提供的任何诊断程序。</span><span class="sxs-lookup"><span data-stu-id="d27c9-129">Check for any logged errors and run any diagnostics provided by your hardware vendor.</span></span>  
  
-   <span data-ttu-id="d27c9-130">确保未压缩磁盘驱动器。</span><span class="sxs-lookup"><span data-stu-id="d27c9-130">Make sure that your disk drives are not compressed.</span></span> <span data-ttu-id="d27c9-131">不支持将数据或日志文件存储在压缩驱动器上。</span><span class="sxs-lookup"><span data-stu-id="d27c9-131">Storing data or log files on compressed drives is not supported.</span></span> <span data-ttu-id="d27c9-132">有关物理文件的详细信息，请参阅[数据库文件和文件组](../databases/database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="d27c9-132">For more information about physical files, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
-   <span data-ttu-id="d27c9-133">查看在您将以下选项设置为关闭时错误消息是否消失：</span><span class="sxs-lookup"><span data-stu-id="d27c9-133">See whether the error messages disappear when you set the following options to off:</span></span>  
  
    -   <span data-ttu-id="d27c9-134">SQL Server priority boost 配置选项</span><span class="sxs-lookup"><span data-stu-id="d27c9-134">SQL Server priority boost configuration option</span></span>  
  
    -   <span data-ttu-id="d27c9-135">Lightweight pooling（纤程模式）选项</span><span class="sxs-lookup"><span data-stu-id="d27c9-135">Lightweight pooling (fiber mode) option</span></span>  
  
    -   <span data-ttu-id="d27c9-136">set working set size 选项</span><span class="sxs-lookup"><span data-stu-id="d27c9-136">Set working set size option</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d27c9-137">如果对以上设置的默认设置 OFF 进行更改，则这些设置可能会经常使系统效率降低。</span><span class="sxs-lookup"><span data-stu-id="d27c9-137">The previous settings can frequently be counter-productive if you change them from their default setting of OFF.</span></span> <span data-ttu-id="d27c9-138">有关设置的详细信息，请参阅[服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d27c9-138">For more information about the settings, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
-   <span data-ttu-id="d27c9-139">优化查询，以减少占用的系统资源。</span><span class="sxs-lookup"><span data-stu-id="d27c9-139">Tune queries to reduce resources used on the system.</span></span> <span data-ttu-id="d27c9-140">性能优化将有助于降低系统面临的压力，并缩短单个查询的响应时间。</span><span class="sxs-lookup"><span data-stu-id="d27c9-140">Performance tuning will help reduce the stress on a system and improve response time for individual queries.</span></span>  
  
-   <span data-ttu-id="d27c9-141">将 AUTO_SHRINK 选项设置为 OFF，以降低更改数据库大小的开销。</span><span class="sxs-lookup"><span data-stu-id="d27c9-141">Set the AUTO_SHRINK option to OFF to reduce the overhead of changes to the database size.</span></span>  
  
-   <span data-ttu-id="d27c9-142">确保将 FILEGROWTH 选项设置为足够大的增量，以便减少文件增长的频率。</span><span class="sxs-lookup"><span data-stu-id="d27c9-142">Make sure that you set the FILEGROWTH option to increments that are large enough to be infrequent.</span></span> <span data-ttu-id="d27c9-143">制定一个检查数据库中可用空间的作业计划，然后在非高峰时间内增加数据库大小。</span><span class="sxs-lookup"><span data-stu-id="d27c9-143">Schedule a job to check the available space in the databases, and then increase the database size during nonpeak hours.</span></span>  
  
  
