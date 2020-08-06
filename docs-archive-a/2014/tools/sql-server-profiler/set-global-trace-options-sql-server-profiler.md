---
title: 设置全局跟踪选项 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- global trace options [SQL Server]
ms.assetid: 2854608a-c3c7-4eb8-b567-034bfec4b1a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f0809ae11776e1bddf42c189b86f48689ff4859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577973"
---
# <a name="set-global-trace-options-sql-server-profiler"></a><span data-ttu-id="b2347-102">设置全局跟踪选项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="b2347-102">Set Global Trace Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="b2347-103">本主题介绍了如何设置应用于随特定的 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]实例创建的所有跟踪的选项。</span><span class="sxs-lookup"><span data-stu-id="b2347-103">This topic describes how to set options that apply to all traces that are created with a specific instance of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-global-trace-options"></a><span data-ttu-id="b2347-104">设置全局跟踪选项</span><span class="sxs-lookup"><span data-stu-id="b2347-104">To set global trace options</span></span>  
  
1.  <span data-ttu-id="b2347-105">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="b2347-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="b2347-106">在“常规选项”  对话框中，单击“选择字体”  修改显示选项，再单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b2347-106">In the **General Options**dialog box, click **Choose Font**to modify the display options, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b2347-107">根据需要选择 **“建立连接后立即开始跟踪”** 。</span><span class="sxs-lookup"><span data-stu-id="b2347-107">Optionally, select **Start tracing immediately after making connection**.</span></span>  
  
4.  <span data-ttu-id="b2347-108">根据需要选择 **“当提供程序版本发生更改时更新跟踪定义”** 。</span><span class="sxs-lookup"><span data-stu-id="b2347-108">Optionally, select **Update trace definition when provider version changes**.</span></span> <span data-ttu-id="b2347-109">建议选择该选项，且默认情况下选择该选项。</span><span class="sxs-lookup"><span data-stu-id="b2347-109">This option is recommended and is selected by default.</span></span> <span data-ttu-id="b2347-110">选择该选项后，跟踪定义会自动更新为执行跟踪的服务器的当前版本。</span><span class="sxs-lookup"><span data-stu-id="b2347-110">When this option is selected, the trace definition is automatically updated to the current version of the server where tracing is performed.</span></span>  
  
5.  <span data-ttu-id="b2347-111">根据需要指定服务器管理滚动更新文件的方式：</span><span class="sxs-lookup"><span data-stu-id="b2347-111">Optionally, specify how the server should manage rollover files:</span></span>  
  
    -   <span data-ttu-id="b2347-112">选择 **“不作提示，依次加载所有滚动更新文件”** 在重播期间自动加载滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="b2347-112">Select **Load all rollover files in sequence without prompting** to automatically load rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="b2347-113">选择 **“加载滚动更新文件之前进行提示”** 在重播期间控制滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="b2347-113">Select **Prompt before loading rollover files** to control rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="b2347-114">选择 **“从不加载后续滚动更新文件”** 每次只重播一个文件。</span><span class="sxs-lookup"><span data-stu-id="b2347-114">Select **Never load subsequent rollover files** to replay only one file at a time.</span></span>  
  
6.  <span data-ttu-id="b2347-115">根据需要设置重播选项：</span><span class="sxs-lookup"><span data-stu-id="b2347-115">Optionally, set replay options:</span></span>  
  
    -   <span data-ttu-id="b2347-116">**默认重播线程数** ：控制重播期间使用的处理器线程数。</span><span class="sxs-lookup"><span data-stu-id="b2347-116">**Default number of replay threads** controls the number of processor threads to use during replay.</span></span> <span data-ttu-id="b2347-117">线程数越多，重播越快，但这会导致重播期间服务器的性能降低。</span><span class="sxs-lookup"><span data-stu-id="b2347-117">A higher number of threads causes replay to complete faster, but causes server performance to degrade during replay.</span></span> <span data-ttu-id="b2347-118">建议将该项设置为 **4**。</span><span class="sxs-lookup"><span data-stu-id="b2347-118">The recommended setting is **4**.</span></span> <span data-ttu-id="b2347-119">下表列出了可用选项：</span><span class="sxs-lookup"><span data-stu-id="b2347-119">The following table lists the available options:</span></span>  
  
        |<span data-ttu-id="b2347-120">值</span><span class="sxs-lookup"><span data-stu-id="b2347-120">Value</span></span>|<span data-ttu-id="b2347-121">说明</span><span class="sxs-lookup"><span data-stu-id="b2347-121">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="b2347-122">**2**</span><span class="sxs-lookup"><span data-stu-id="b2347-122">**2**</span></span>|<span data-ttu-id="b2347-123">最小值。</span><span class="sxs-lookup"><span data-stu-id="b2347-123">Minimum value.</span></span> <span data-ttu-id="b2347-124">使用两个线程重播。</span><span class="sxs-lookup"><span data-stu-id="b2347-124">Use two threads to replay.</span></span>|  
        |<span data-ttu-id="b2347-125">**4**</span><span class="sxs-lookup"><span data-stu-id="b2347-125">**4**</span></span>|<span data-ttu-id="b2347-126">默认值。</span><span class="sxs-lookup"><span data-stu-id="b2347-126">Default value.</span></span>|  
        |<span data-ttu-id="b2347-127">**255**</span><span class="sxs-lookup"><span data-stu-id="b2347-127">**255**</span></span>|<span data-ttu-id="b2347-128">最大值。</span><span class="sxs-lookup"><span data-stu-id="b2347-128">Maximum value.</span></span> <span data-ttu-id="b2347-129">设置为最大值会影响其他进程的性能。</span><span class="sxs-lookup"><span data-stu-id="b2347-129">Setting a maximum value will impede performance for other processes.</span></span>|  
  
    -   <span data-ttu-id="b2347-130">“默认 Health Monitor 等待间隔(秒)”  设置重播线程可以阻塞其他进程的最长时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="b2347-130">**Default health monitor wait interval (sec)** sets the maximum amount of time that a replay thread can block another process in seconds.</span></span> <span data-ttu-id="b2347-131">下表说明了这些值。</span><span class="sxs-lookup"><span data-stu-id="b2347-131">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="b2347-132">值</span><span class="sxs-lookup"><span data-stu-id="b2347-132">Value</span></span>|<span data-ttu-id="b2347-133">说明</span><span class="sxs-lookup"><span data-stu-id="b2347-133">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="b2347-134">**0**</span><span class="sxs-lookup"><span data-stu-id="b2347-134">**0**</span></span>|<span data-ttu-id="b2347-135">最小值。</span><span class="sxs-lookup"><span data-stu-id="b2347-135">Minimum value.</span></span> <span data-ttu-id="b2347-136">设置为 **0** 表示 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 永远不会停止阻塞进程。</span><span class="sxs-lookup"><span data-stu-id="b2347-136">A setting of **0** means that [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will never stop a blocking process.</span></span>|  
        |<span data-ttu-id="b2347-137">**3600**</span><span class="sxs-lookup"><span data-stu-id="b2347-137">**3600**</span></span>|<span data-ttu-id="b2347-138">默认值。</span><span class="sxs-lookup"><span data-stu-id="b2347-138">Default value.</span></span> <span data-ttu-id="b2347-139">允许不超过 **3600** 秒（1 小时）的阻塞进程。</span><span class="sxs-lookup"><span data-stu-id="b2347-139">Allow blocking processes that do not exceed **3600** seconds, or one hour.</span></span>|  
        |<span data-ttu-id="b2347-140">**86400**</span><span class="sxs-lookup"><span data-stu-id="b2347-140">**86400**</span></span>|<span data-ttu-id="b2347-141">最大值。</span><span class="sxs-lookup"><span data-stu-id="b2347-141">Maximum value.</span></span> <span data-ttu-id="b2347-142">允许不超过 **86400** 秒（一天）的阻塞进程。</span><span class="sxs-lookup"><span data-stu-id="b2347-142">Allow blocking processes that do not exceed **86400** seconds, or one day.</span></span>|  
  
    -   <span data-ttu-id="b2347-143">“默认 Health Monitor 轮询间隔(秒)”  设置阻塞进程的轮询重播线程的频率。</span><span class="sxs-lookup"><span data-stu-id="b2347-143">**Default health monitor poll interval (sec)** sets the frequency to poll replay threads for blocking processes.</span></span> <span data-ttu-id="b2347-144">下表说明了这些值。</span><span class="sxs-lookup"><span data-stu-id="b2347-144">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="b2347-145">值</span><span class="sxs-lookup"><span data-stu-id="b2347-145">Value</span></span>|<span data-ttu-id="b2347-146">说明</span><span class="sxs-lookup"><span data-stu-id="b2347-146">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="b2347-147">**1**</span><span class="sxs-lookup"><span data-stu-id="b2347-147">**1**</span></span>|<span data-ttu-id="b2347-148">最小值。</span><span class="sxs-lookup"><span data-stu-id="b2347-148">Minimum value.</span></span> <span data-ttu-id="b2347-149">设置为 **1** 表示 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 每秒针对阻塞进程轮询一次。</span><span class="sxs-lookup"><span data-stu-id="b2347-149">A setting of **1** means [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will poll for blocking processes once per second.</span></span>|  
        |<span data-ttu-id="b2347-150">**60**</span><span class="sxs-lookup"><span data-stu-id="b2347-150">**60**</span></span>|<span data-ttu-id="b2347-151">默认值。</span><span class="sxs-lookup"><span data-stu-id="b2347-151">Default value.</span></span> <span data-ttu-id="b2347-152">每分钟针对阻塞进程轮询一次。</span><span class="sxs-lookup"><span data-stu-id="b2347-152">Poll for blocking processes once per minute.</span></span>|  
        |<span data-ttu-id="b2347-153">**86400**</span><span class="sxs-lookup"><span data-stu-id="b2347-153">**86400**</span></span>|<span data-ttu-id="b2347-154">最大值。</span><span class="sxs-lookup"><span data-stu-id="b2347-154">Maximum value.</span></span> <span data-ttu-id="b2347-155">每 **86400** 秒（一天）针对阻塞进程轮询一次。</span><span class="sxs-lookup"><span data-stu-id="b2347-155">Poll for blocking processes once per **86400** seconds, or one day.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2347-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2347-156">See Also</span></span>  
 <span data-ttu-id="b2347-157">[设置跟踪显示默认值 (SQL Server Profiler)](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b2347-157">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="b2347-158">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b2347-158">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
