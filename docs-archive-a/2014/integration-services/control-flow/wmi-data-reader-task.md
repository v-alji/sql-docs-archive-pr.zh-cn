---
title: WMI 数据读取器任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d2f16a28e8b6c94c7275468dedb6d2dfec76d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578989"
---
# <a name="wmi-data-reader-task"></a><span data-ttu-id="fb025-102">WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="fb025-102">WMI Data Reader Task</span></span>
  <span data-ttu-id="fb025-103">WMI 数据读取器任务使用 Windows Management Instrumentation (WMI) 查询语言来运行查询，此查询语言从 WMI 返回有关计算机系统的信息。</span><span class="sxs-lookup"><span data-stu-id="fb025-103">The WMI Data Reader task runs queries using the Windows Management Instrumentation (WMI) Query Language that returns information from WMI about a computer system.</span></span> <span data-ttu-id="fb025-104">可以将 WMI 数据读取器任务用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="fb025-104">You can use the WMI Data Reader task for the following purposes:</span></span>  
  
-   <span data-ttu-id="fb025-105">查询本地或远程计算机上的 Windows 事件日志并将此信息写入文件或变量。</span><span class="sxs-lookup"><span data-stu-id="fb025-105">Query the Windows event logs on a local or remote computer and write the information to a file or variable.</span></span>  
  
-   <span data-ttu-id="fb025-106">获取有关硬件组件的存在、状态或属性的信息，然后使用此信息决定控制流中的其他任务是否应该运行。</span><span class="sxs-lookup"><span data-stu-id="fb025-106">Obtain information about the presence, state, or properties of hardware components, and then use this information to determine whether other tasks in the control flow should run.</span></span>  
  
-   <span data-ttu-id="fb025-107">获取应用程序的列表，并确定每个应用程序安装的是何种版本。</span><span class="sxs-lookup"><span data-stu-id="fb025-107">Get a list of applications and determine what version of each application is installed.</span></span>  
  
 <span data-ttu-id="fb025-108">可以通过以下方式配置 WMI 数据读取器任务：</span><span class="sxs-lookup"><span data-stu-id="fb025-108">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="fb025-109">指定要使用的 WMI 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="fb025-109">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="fb025-110">指定 WQL 查询的源。</span><span class="sxs-lookup"><span data-stu-id="fb025-110">Specify the source of the WQL query.</span></span> <span data-ttu-id="fb025-111">查询可以存储在任务属性中，也可以存储在任务之外的变量或文件中。</span><span class="sxs-lookup"><span data-stu-id="fb025-111">The query can be stored in a task property, or the query can be stored outside the task, in a variable or a file.</span></span>  
  
-   <span data-ttu-id="fb025-112">定义 WQL 查询结果的格式。</span><span class="sxs-lookup"><span data-stu-id="fb025-112">Define the format of the WQL query results.</span></span> <span data-ttu-id="fb025-113">该任务支持表、属性名称/值对或属性值三种格式。</span><span class="sxs-lookup"><span data-stu-id="fb025-113">The task supports a table, property name/value pair, or property value format.</span></span>  
  
-   <span data-ttu-id="fb025-114">指定查询目标。</span><span class="sxs-lookup"><span data-stu-id="fb025-114">Specify the destination of the query.</span></span> <span data-ttu-id="fb025-115">目标可以是变量或文件。</span><span class="sxs-lookup"><span data-stu-id="fb025-115">The destination can be a variable or a file.</span></span>  
  
-   <span data-ttu-id="fb025-116">指示覆盖、保留还是追加查询目标。</span><span class="sxs-lookup"><span data-stu-id="fb025-116">Indicate whether the query destination is overwritten, kept, or appended.</span></span>  
  
 <span data-ttu-id="fb025-117">如果源或目标是文件，则 WMI 数据读取器任务使用文件连接管理器连接到该文件。</span><span class="sxs-lookup"><span data-stu-id="fb025-117">If the source or destination is a file, the WMI Data Reader task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="fb025-118">有关详细信息，请参阅 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fb025-118">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="fb025-119">WMI 数据读取器任务使用 WMI 连接管理器连接到该任务从中读取 WMI 信息的服务器。</span><span class="sxs-lookup"><span data-stu-id="fb025-119">The WMI Data Reader task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="fb025-120">有关详细信息，请参阅 [WMI Connection Manager](../connection-manager/wmi-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fb025-120">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="wql-query"></a><span data-ttu-id="fb025-121">WQL 查询</span><span class="sxs-lookup"><span data-stu-id="fb025-121">WQL Query</span></span>  
 <span data-ttu-id="fb025-122">WQL 是 SQL 的方言，其扩展插件支持 WMI 事件通知和其他 WMI 特定功能。</span><span class="sxs-lookup"><span data-stu-id="fb025-122">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="fb025-123">有关 WQL 的详细信息，请参阅 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022)中的 Windows Management Instrumentation 文档。</span><span class="sxs-lookup"><span data-stu-id="fb025-123">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb025-124">WMI 类因 Windows 版本的不同而异。</span><span class="sxs-lookup"><span data-stu-id="fb025-124">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="fb025-125">下列 WQL 查询返回应用程序日志事件中的项。</span><span class="sxs-lookup"><span data-stu-id="fb025-125">The following WQL query returns entries in the Application log event.</span></span>  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 <span data-ttu-id="fb025-126">下列 WQL 查询返回逻辑磁盘信息。</span><span class="sxs-lookup"><span data-stu-id="fb025-126">The following WQL query returns logical disk information.</span></span>  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 <span data-ttu-id="fb025-127">下列 WQL 查询返回操作系统的快速修补工程 (QFE) 更新列表。</span><span class="sxs-lookup"><span data-stu-id="fb025-127">The following WQL query returns a list of the quick fix engineering (QFE) updates to the operating system.</span></span>  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a><span data-ttu-id="fb025-128">WMI 数据读取器任务可用的自定义日志记录消息</span><span class="sxs-lookup"><span data-stu-id="fb025-128">Custom Logging Messages Available on the WMI Data Reader Task</span></span>  
 <span data-ttu-id="fb025-129">下表列出了 WMI 数据读取器任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="fb025-129">The following table lists the custom log entries for the WMI Data Reader task.</span></span> <span data-ttu-id="fb025-130">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="fb025-130">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="fb025-131">日志项</span><span class="sxs-lookup"><span data-stu-id="fb025-131">Log entry</span></span>|<span data-ttu-id="fb025-132">说明</span><span class="sxs-lookup"><span data-stu-id="fb025-132">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="fb025-133">指示任务已开始读取 WMI 数据。</span><span class="sxs-lookup"><span data-stu-id="fb025-133">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="fb025-134">报告任务所运行的 WQL 查询。</span><span class="sxs-lookup"><span data-stu-id="fb025-134">Reports the WQL query that the task ran.</span></span>|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a><span data-ttu-id="fb025-135">配置 WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="fb025-135">Configuration of the WMI Data Reader Task</span></span>  
 <span data-ttu-id="fb025-136">可以采用编程方式或通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="fb025-136">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="fb025-137">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="fb025-137">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="fb025-138">WMI 数据读取器任务编辑器（“WMI 选项”页）</span><span class="sxs-lookup"><span data-stu-id="fb025-138">WMI Data Reader Task Editor &#40;WMI Options Page&#41;</span></span>](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [<span data-ttu-id="fb025-139">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="fb025-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="fb025-140">有关以编程方式设置这些属性的信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="fb025-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="fb025-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fb025-141">Related Tasks</span></span>  
 <span data-ttu-id="fb025-142">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="fb025-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="fb025-143">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="fb025-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb025-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb025-144">See Also</span></span>  
 <span data-ttu-id="fb025-145">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="fb025-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="fb025-146">控制流</span><span class="sxs-lookup"><span data-stu-id="fb025-146">Control Flow</span></span>](control-flow.md)  
  
  
