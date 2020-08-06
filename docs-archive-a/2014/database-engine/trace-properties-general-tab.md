---
title: ) 的 "常规" 选项卡 (跟踪属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30de30c88db35a41f8f118b6545d56a78b2dec79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693446"
---
# <a name="trace-properties-general-tab"></a><span data-ttu-id="8ce23-102">跟踪属性（“常规”选项卡）</span><span class="sxs-lookup"><span data-stu-id="8ce23-102">Trace Properties (General Tab)</span></span>
  <span data-ttu-id="8ce23-103">使用 **“跟踪属性”** 对话框中的 **“常规”** 选项卡可以查看或指定跟踪属性。</span><span class="sxs-lookup"><span data-stu-id="8ce23-103">Use the **General** tab of the **Trace Properties** dialog box to view or specify properties of a trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ce23-104">选项</span><span class="sxs-lookup"><span data-stu-id="8ce23-104">Options</span></span>  
 <span data-ttu-id="8ce23-105">**跟踪名称**</span><span class="sxs-lookup"><span data-stu-id="8ce23-105">**Trace name**</span></span>  
 <span data-ttu-id="8ce23-106">指定跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="8ce23-106">Specify the name of the trace.</span></span>  
  
 <span data-ttu-id="8ce23-107">**跟踪提供程序名称**</span><span class="sxs-lookup"><span data-stu-id="8ce23-107">**Trace provider name**</span></span>  
 <span data-ttu-id="8ce23-108">显示要跟踪的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8ce23-108">Shows the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that will be traced.</span></span> <span data-ttu-id="8ce23-109">将使用连接时指定的服务器的名称自动填充此字段。</span><span class="sxs-lookup"><span data-stu-id="8ce23-109">This field is populated automatically with the name of the server that you specified when you connected.</span></span> <span data-ttu-id="8ce23-110">若要更改跟踪提供程序的名称，请单击 **“取消”** 关闭该对话框，然后启动新的跟踪。</span><span class="sxs-lookup"><span data-stu-id="8ce23-110">To change the name of the trace provider, click **Cancel** to close the dialog box, and start a new trace.</span></span>  
  
 <span data-ttu-id="8ce23-111">**跟踪提供程序类型**</span><span class="sxs-lookup"><span data-stu-id="8ce23-111">**Trace provider type**</span></span>  
 <span data-ttu-id="8ce23-112">显示提供跟踪的服务器类型。</span><span class="sxs-lookup"><span data-stu-id="8ce23-112">Shows the server type that is providing the trace.</span></span> <span data-ttu-id="8ce23-113">跟踪定义文件将自动填充 **“跟踪提供程序类型”** 字段。</span><span class="sxs-lookup"><span data-stu-id="8ce23-113">The trace definition file populates the **Trace provider type** field automatically.</span></span> <span data-ttu-id="8ce23-114">您无法修改此字段。</span><span class="sxs-lookup"><span data-stu-id="8ce23-114">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="8ce23-115">**version**</span><span class="sxs-lookup"><span data-stu-id="8ce23-115">**version**</span></span>  
 <span data-ttu-id="8ce23-116">显示提供跟踪的服务器的版本。</span><span class="sxs-lookup"><span data-stu-id="8ce23-116">Shows the version of the server that is providing the trace.</span></span> <span data-ttu-id="8ce23-117">跟踪定义文件将自动填充 **“版本”** 字段。</span><span class="sxs-lookup"><span data-stu-id="8ce23-117">The trace definition file populates the **Version** field automatically.</span></span> <span data-ttu-id="8ce23-118">您无法修改此字段。</span><span class="sxs-lookup"><span data-stu-id="8ce23-118">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="8ce23-119">**使用模板**</span><span class="sxs-lookup"><span data-stu-id="8ce23-119">**Use the template**</span></span>  
 <span data-ttu-id="8ce23-120">从模板目录中选择一个模板。</span><span class="sxs-lookup"><span data-stu-id="8ce23-120">Select a template from the template directory.</span></span> <span data-ttu-id="8ce23-121">将使用默认模板和为当前跟踪提供程序类型创建的任何用户定义模板来填充该目录。</span><span class="sxs-lookup"><span data-stu-id="8ce23-121">The directory is populated with the default templates and any user-defined templates created for the current trace provider type.</span></span>  
  
 <span data-ttu-id="8ce23-122">**保存到文件**</span><span class="sxs-lookup"><span data-stu-id="8ce23-122">**Save to file**</span></span>  
 <span data-ttu-id="8ce23-123">将跟踪数据捕获到 .trc 文件。</span><span class="sxs-lookup"><span data-stu-id="8ce23-123">Capture the trace data to a .trc file.</span></span> <span data-ttu-id="8ce23-124">保存跟踪数据有助于以后进行查看和分析。</span><span class="sxs-lookup"><span data-stu-id="8ce23-124">Saving trace data is useful for later review and analysis.</span></span>  
  
 <span data-ttu-id="8ce23-125">**设置最大文件大小(MB)**</span><span class="sxs-lookup"><span data-stu-id="8ce23-125">**Set maximum file size (MB)**</span></span>  
 <span data-ttu-id="8ce23-126">如果选择将跟踪数据保存到文件，则必须指定跟踪文件的最大大小。</span><span class="sxs-lookup"><span data-stu-id="8ce23-126">If you choose to save the trace data to a file, you must specify the maximum size of the trace file.</span></span> <span data-ttu-id="8ce23-127">默认值为 5 MB。</span><span class="sxs-lookup"><span data-stu-id="8ce23-127">The default is 5 megabytes (MB).</span></span> <span data-ttu-id="8ce23-128">最大大小仅受保存该文件的文件系统（NTFS、FAT）的限制。</span><span class="sxs-lookup"><span data-stu-id="8ce23-128">The maximum size is limited only by the file system (NTFS, FAT) where the file is saved.</span></span>  
  
 <span data-ttu-id="8ce23-129">\<Graphic>**另存为**</span><span class="sxs-lookup"><span data-stu-id="8ce23-129">\<Graphic> **Save As**</span></span>  
 <span data-ttu-id="8ce23-130">在选择进行保存后，可以选择此图标来更改文件名。</span><span class="sxs-lookup"><span data-stu-id="8ce23-130">After you have selected to save, you can select this icon to change the file name.</span></span>  
  
 <span data-ttu-id="8ce23-131">**启用文件滚动更新**</span><span class="sxs-lookup"><span data-stu-id="8ce23-131">**Enable file rollover**</span></span>  
 <span data-ttu-id="8ce23-132">选择此选项允许在达到最大文件大小时创建其他文件来接受跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="8ce23-132">Select to enable the creation of additional files to accept the trace data when the maximum file size is reached.</span></span> <span data-ttu-id="8ce23-133">每个新文件名都由原始 .trc 文件名按顺序编号而成。</span><span class="sxs-lookup"><span data-stu-id="8ce23-133">Each new file name consists of the original .trc file name, numbered sequentially.</span></span> <span data-ttu-id="8ce23-134">例如，当 **NewTrace.trc** 达到最大文件大小时，将关闭该文件，并打开一个新文件 **NewTrace_1.trc**，在新文件达到最大文件大小时将打开 **NewTrace_2.trc**，依此类推。</span><span class="sxs-lookup"><span data-stu-id="8ce23-134">For example, once it reaches maximum file size, **NewTrace.trc** closes, and a new file, **NewTrace_1.trc**, opens, followed by **NewTrace_2.trc**, and so on.</span></span> <span data-ttu-id="8ce23-135">默认情况下，在将跟踪保存到文件时将启用文件滚动更新。</span><span class="sxs-lookup"><span data-stu-id="8ce23-135">File rollover is enabled by default when you save a trace to a file.</span></span>  
  
 <span data-ttu-id="8ce23-136">**服务器处理跟踪数据**</span><span class="sxs-lookup"><span data-stu-id="8ce23-136">**Server processes trace data**</span></span>  
 <span data-ttu-id="8ce23-137">指定由运行跟踪的服务器来处理跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="8ce23-137">Specify that the server running the trace should process the trace data.</span></span> <span data-ttu-id="8ce23-138">使用此选项可降低跟踪所需的性能开销。</span><span class="sxs-lookup"><span data-stu-id="8ce23-138">Using this option reduces the performance overhead incurred by tracing.</span></span> <span data-ttu-id="8ce23-139">如果选中此复选框，即使在高负荷环境下也不会跳过任何事件。</span><span class="sxs-lookup"><span data-stu-id="8ce23-139">If selected, no events are skipped even under stress conditions.</span></span> <span data-ttu-id="8ce23-140">如果清除此复选框，则由 SQL Server Profiler 执行处理任务，在高负荷环境下可能不会跟踪某些事件。</span><span class="sxs-lookup"><span data-stu-id="8ce23-140">If this check box is cleared, processing is performed by SQL Server Profiler, and there is a possibility that some events are not traced under stress conditions.</span></span>  
  
 <span data-ttu-id="8ce23-141">**保存到表**</span><span class="sxs-lookup"><span data-stu-id="8ce23-141">**Save to table**</span></span>  
 <span data-ttu-id="8ce23-142">将跟踪数据捕获到数据库表。</span><span class="sxs-lookup"><span data-stu-id="8ce23-142">Capture the trace data to a database table.</span></span> <span data-ttu-id="8ce23-143">保存跟踪数据有助于以后进行查看和分析。</span><span class="sxs-lookup"><span data-stu-id="8ce23-143">Saving trace data is useful for later review and analysis.</span></span> <span data-ttu-id="8ce23-144">但是，将跟踪数据保存到表会导致在保存跟踪的服务器上产生很大的开销。</span><span class="sxs-lookup"><span data-stu-id="8ce23-144">However, saving trace data to a table can incur significant overhead on the server where the trace is being saved.</span></span> <span data-ttu-id="8ce23-145">如果可能，请不要将跟踪表保存到正在跟踪的同一服务器上。</span><span class="sxs-lookup"><span data-stu-id="8ce23-145">If possible, do not save the trace table on the same server that is being traced.</span></span>  
  
 <span data-ttu-id="8ce23-146">\<Graphic>**目标表**</span><span class="sxs-lookup"><span data-stu-id="8ce23-146">\<Graphic> **Destination Table**</span></span>  
 <span data-ttu-id="8ce23-147">在选择将跟踪数据保存到数据库表后，可以选择此图标来更改表名称。</span><span class="sxs-lookup"><span data-stu-id="8ce23-147">After you have selected to save the trace data to a database table, you can select this icon to change the table name.</span></span>  
  
 <span data-ttu-id="8ce23-148">**设置最大行数(千行)**</span><span class="sxs-lookup"><span data-stu-id="8ce23-148">**Set maximum rows (in thousands)**</span></span>  
 <span data-ttu-id="8ce23-149">指定保存数据的最大行数。</span><span class="sxs-lookup"><span data-stu-id="8ce23-149">Specify the largest number of rows in which to save data.</span></span> <span data-ttu-id="8ce23-150">默认值为 1000 行。</span><span class="sxs-lookup"><span data-stu-id="8ce23-150">The default is 1000 rows.</span></span>  
  
 <span data-ttu-id="8ce23-151">**启用跟踪停止时间**</span><span class="sxs-lookup"><span data-stu-id="8ce23-151">**Enable trace stop time**</span></span>  
 <span data-ttu-id="8ce23-152">为跟踪设置日期和时间，以便到时候终止并关闭此跟踪。</span><span class="sxs-lookup"><span data-stu-id="8ce23-152">Set the date and time for the trace to end and close itself.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce23-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ce23-153">See Also</span></span>  
 [<span data-ttu-id="8ce23-154">创建跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="8ce23-154">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
