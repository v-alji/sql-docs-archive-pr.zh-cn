---
title: WMI 事件观察器任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be20624e5ccdf665e6274f647c342498e9c0f0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693415"
---
# <a name="wmi-event-watcher-task"></a><span data-ttu-id="d181f-102">WMI 事件观察器任务</span><span class="sxs-lookup"><span data-stu-id="d181f-102">WMI Event Watcher Task</span></span>
  <span data-ttu-id="d181f-103">WMI 事件观察器任务以使用 Management Instrumentation 查询语言 (WQL) 事件查询指定所关注事件的方式来监视 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="d181f-103">The WMI Event Watcher task watches for a Windows Management Instrumentation (WMI) event using a Management Instrumentation Query Language (WQL) event query to specify events of interest.</span></span> <span data-ttu-id="d181f-104">可以将 WMI 事件观察器任务用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="d181f-104">You can use the WMI Event Watcher task for the following purposes:</span></span>  
  
-   <span data-ttu-id="d181f-105">等待已将文件添加到文件夹的通知，然后开始处理文件。</span><span class="sxs-lookup"><span data-stu-id="d181f-105">Wait for notification that files have been added to a folder and then initiate the processing of the file.</span></span>  
  
-   <span data-ttu-id="d181f-106">当服务器上的可用内存低于指定百分比时，运行删除文件的包。</span><span class="sxs-lookup"><span data-stu-id="d181f-106">Run a package that deletes files when the available memory on a server drops lower than a specified percentage.</span></span>  
  
-   <span data-ttu-id="d181f-107">监视应用程序的安装，然后运行使用该应用程序的包。</span><span class="sxs-lookup"><span data-stu-id="d181f-107">Watch for installation of an application, and then run a package that uses the application.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="d181f-108">包含读取 WMI 信息的任务。</span><span class="sxs-lookup"><span data-stu-id="d181f-108">includes a task that reads WMI information.</span></span>  
  
 <span data-ttu-id="d181f-109">有关此任务的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="d181f-109">For more information about this task, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d181f-110">WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="d181f-110">WMI Data Reader Task</span></span>](wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a><span data-ttu-id="d181f-111">WQL 查询</span><span class="sxs-lookup"><span data-stu-id="d181f-111">WQL Queries</span></span>  
 <span data-ttu-id="d181f-112">WQL 是 SQL 的方言，其扩展插件支持 WMI 事件通知和其他 WMI 特定功能。</span><span class="sxs-lookup"><span data-stu-id="d181f-112">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="d181f-113">有关 WQL 的详细信息，请参阅 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553)中的 Windows Management Instrumentation 文档。</span><span class="sxs-lookup"><span data-stu-id="d181f-113">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d181f-114">WMI 类因 Windows 版本的不同而异。</span><span class="sxs-lookup"><span data-stu-id="d181f-114">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="d181f-115">以下查询监视 CPU 使用率超过 40% 的通知。</span><span class="sxs-lookup"><span data-stu-id="d181f-115">The following query watches for notification that the CPU use is more than 40 percent.</span></span>  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 <span data-ttu-id="d181f-116">以下查询监视已将文件添加到文件夹的通知。</span><span class="sxs-lookup"><span data-stu-id="d181f-116">The following query watches for notification that a file has been added to a folder.</span></span>  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a><span data-ttu-id="d181f-117">WMI 事件观察器任务可用的自定义日志记录消息</span><span class="sxs-lookup"><span data-stu-id="d181f-117">Custom Logging Messages Available on the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="d181f-118">下表列出了 WMI 事件观察器任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="d181f-118">The following table lists the custom log entries for the WMI Event Watcher task.</span></span> <span data-ttu-id="d181f-119">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="d181f-119">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="d181f-120">日志项</span><span class="sxs-lookup"><span data-stu-id="d181f-120">Log entry</span></span>|<span data-ttu-id="d181f-121">说明</span><span class="sxs-lookup"><span data-stu-id="d181f-121">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="d181f-122">指示发生了任务正在监视的事件。</span><span class="sxs-lookup"><span data-stu-id="d181f-122">Indicates that an event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="d181f-123">指示任务已超时。</span><span class="sxs-lookup"><span data-stu-id="d181f-123">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="d181f-124">指示任务已开始执行 WQL 查询。</span><span class="sxs-lookup"><span data-stu-id="d181f-124">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="d181f-125">日志项包括查询。</span><span class="sxs-lookup"><span data-stu-id="d181f-125">The entry includes the query.</span></span>|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="d181f-126">WMI 事件观察器任务的配置</span><span class="sxs-lookup"><span data-stu-id="d181f-126">Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="d181f-127">可以通过以下方式配置 WMI 数据读取器任务：</span><span class="sxs-lookup"><span data-stu-id="d181f-127">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="d181f-128">指定要使用的 WMI 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d181f-128">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="d181f-129">指定 WQL 查询的源。</span><span class="sxs-lookup"><span data-stu-id="d181f-129">Specify the source of the WQL query.</span></span> <span data-ttu-id="d181f-130">源可以在任务外部，比如变量或文件，否则可把查询存储在任务属性中。</span><span class="sxs-lookup"><span data-stu-id="d181f-130">The source can be external to the task, a variable or a file, or the query can be stored in a task property.</span></span>  
  
-   <span data-ttu-id="d181f-131">指定在 WMI 事件发生时任务所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d181f-131">Specify the action that the task takes when the WMI event occurs.</span></span> <span data-ttu-id="d181f-132">可以记录事件通知和事件后的状态，也可以引发自定义 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 事件来提供与 WMI 事件、通知和事件后的状态相关的信息。</span><span class="sxs-lookup"><span data-stu-id="d181f-132">You can log the event notification and the status after the event, or raise custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] events that provide information associated with the WMI event, the notification, and the status after the event.</span></span>  
  
-   <span data-ttu-id="d181f-133">定义任务对事件的响应方式。</span><span class="sxs-lookup"><span data-stu-id="d181f-133">Define how the task responds to the event.</span></span> <span data-ttu-id="d181f-134">可根据事件的不同将任务配置为成功或失败，或只是让任务重新监视事件。</span><span class="sxs-lookup"><span data-stu-id="d181f-134">The task can be configured to succeed or fail, depending on the event, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="d181f-135">指定当 WMI 查询超时的时候任务所执行的操作。可以记录超时和超时后的状态，也可以引发自定义的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 事件，以指示 WMI 事件已超时并记录超时和超时状态。</span><span class="sxs-lookup"><span data-stu-id="d181f-135">Specify the action the task takes when the WMI query times out. You can log the time-out and the status after time-out, or raise a custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] event, indicating that the WMI event timed out and logging the time-out and time-out status.</span></span>  
  
-   <span data-ttu-id="d181f-136">定义任务对超时的响应方式。可将任务配置为成功或失败，或只是让任务重新监视事件。</span><span class="sxs-lookup"><span data-stu-id="d181f-136">Define how the task responds to the time-out. The task can be configured to succeed or fail, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="d181f-137">指定任务监视事件的次数。</span><span class="sxs-lookup"><span data-stu-id="d181f-137">Specify the number of times the task watches for the event.</span></span>  
  
-   <span data-ttu-id="d181f-138">指定超时。</span><span class="sxs-lookup"><span data-stu-id="d181f-138">Specify the time-out.</span></span>  
  
 <span data-ttu-id="d181f-139">如果源是文件，则 WMI 事件观察器任务使用文件连接管理器连接到该文件。</span><span class="sxs-lookup"><span data-stu-id="d181f-139">If the source is a file, the WMI Event Watcher task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="d181f-140">有关详细信息，请参阅 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d181f-140">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d181f-141">WMI 事件观察器任务使用 WMI 连接管理器连接到它从中读取 WMI 信息的服务器。</span><span class="sxs-lookup"><span data-stu-id="d181f-141">The WMI Event Watcher task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="d181f-142">有关详细信息，请参阅 [WMI Connection Manager](../connection-manager/wmi-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d181f-142">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d181f-143">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="d181f-143">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d181f-144">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="d181f-144">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d181f-145">WMI 事件观察器任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="d181f-145">WMI Event Watcher Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="d181f-146">WMI 事件观察器任务编辑器（“WMI 选项”页）</span><span class="sxs-lookup"><span data-stu-id="d181f-146">WMI Event Watcher Task Editor &#40;WMI Options Page&#41;</span></span>](../wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [<span data-ttu-id="d181f-147">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="d181f-147">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="d181f-148">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="d181f-148">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d181f-149">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="d181f-149">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="d181f-150">WMI 事件观察器任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="d181f-150">Programmatic Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="d181f-151">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="d181f-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  
