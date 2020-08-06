---
title: WMI 事件观察器任务编辑器 (WMI 选项 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7d95501f6442df3723261c970c7a90f48cbdc87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690698"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a><span data-ttu-id="137c6-102">WMI 事件观察器任务编辑器（“WMI 选项”页）</span><span class="sxs-lookup"><span data-stu-id="137c6-102">WMI Event Watcher Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="137c6-103">可以使用“WMI 事件观察器任务编辑器”  对话框的“WMI 选项”  页，指定 Windows Management Instrumentation 查询语言 (WQL) 查询的源以及 WMI 事件观察器任务响应 Microsoft Windows Instrumentation (WMI) 事件的方式。</span><span class="sxs-lookup"><span data-stu-id="137c6-103">Use the **WMI Options** page of the **WMI Event Watcher Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and how the WMI Event Watcher task responds to Microsoft Windows Instrumentation (WMI) events.</span></span>  
  
 <span data-ttu-id="137c6-104">若要了解此任务，请参阅 [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md)。</span><span class="sxs-lookup"><span data-stu-id="137c6-104">To learn about this task, see [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md).</span></span> <span data-ttu-id="137c6-105">有关 WMI 查询语言 (WQL) 的详细信息，请参阅 MSDN 库中的 Windows Management Instrumentation 主题 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)（利用 WQL 进行查询）。</span><span class="sxs-lookup"><span data-stu-id="137c6-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="137c6-106">静态选项</span><span class="sxs-lookup"><span data-stu-id="137c6-106">Static Options</span></span>  
 <span data-ttu-id="137c6-107">**WMIConnectionName**</span><span class="sxs-lookup"><span data-stu-id="137c6-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="137c6-108">从列表中选择 WMI 连接管理器，或单击 \<**New WMI Connection...**> 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="137c6-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="137c6-109">**相关主题：** [WMI 连接管理器](connection-manager/wmi-connection-manager.md)、[WMI 连接管理器编辑器](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="137c6-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="137c6-110">**WQLQuerySourceType**</span><span class="sxs-lookup"><span data-stu-id="137c6-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="137c6-111">选择任务运行的 WQL 查询的源类型。</span><span class="sxs-lookup"><span data-stu-id="137c6-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="137c6-112">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="137c6-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="137c6-113">值</span><span class="sxs-lookup"><span data-stu-id="137c6-113">Value</span></span>|<span data-ttu-id="137c6-114">说明</span><span class="sxs-lookup"><span data-stu-id="137c6-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="137c6-115">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="137c6-115">**Direct input**</span></span>|<span data-ttu-id="137c6-116">为 WQL 查询设置源。</span><span class="sxs-lookup"><span data-stu-id="137c6-116">Set the source to a WQL query.</span></span> <span data-ttu-id="137c6-117">选择此值将显示动态选项 **WQLQuerySource**。</span><span class="sxs-lookup"><span data-stu-id="137c6-117">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="137c6-118">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="137c6-118">**File connection**</span></span>|<span data-ttu-id="137c6-119">选择包含 WQL 查询的文件。</span><span class="sxs-lookup"><span data-stu-id="137c6-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="137c6-120">选择此值将显示动态选项 **WQLQuerySource**。</span><span class="sxs-lookup"><span data-stu-id="137c6-120">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="137c6-121">**变量**</span><span class="sxs-lookup"><span data-stu-id="137c6-121">**Variable**</span></span>|<span data-ttu-id="137c6-122">将源设置为定义 WQL 查询的变量。</span><span class="sxs-lookup"><span data-stu-id="137c6-122">Set the source to a variable that defines WQL query.</span></span> <span data-ttu-id="137c6-123">选择此值将显示动态选项 **WQLQuerySource**。</span><span class="sxs-lookup"><span data-stu-id="137c6-123">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
  
 <span data-ttu-id="137c6-124">**ActionAtEvent**</span><span class="sxs-lookup"><span data-stu-id="137c6-124">**ActionAtEvent**</span></span>  
 <span data-ttu-id="137c6-125">指定 WMI 事件是记录事件并启动 [!INCLUDE[ssIS](../includes/ssis-md.md)] 操作，还是只记录事件。</span><span class="sxs-lookup"><span data-stu-id="137c6-125">Specify whether the WMI event logs the event and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] action, or only logs the event.</span></span>  
  
 <span data-ttu-id="137c6-126">**AfterEvent**</span><span class="sxs-lookup"><span data-stu-id="137c6-126">**AfterEvent**</span></span>  
 <span data-ttu-id="137c6-127">指定任务在收到 WMI 事件之后是成功还是失败，或者任务是否继续监视事件的再次发生。</span><span class="sxs-lookup"><span data-stu-id="137c6-127">Specify whether the task succeeds or fails after it receives the WMI event, or if the task continues watching for the event to occur again.</span></span>  
  
 <span data-ttu-id="137c6-128">**ActionAtTimeout**</span><span class="sxs-lookup"><span data-stu-id="137c6-128">**ActionAtTimeout**</span></span>  
 <span data-ttu-id="137c6-129">指定任务是记录 WMI 查询超时并启动 [!INCLUDE[ssIS](../includes/ssis-md.md)] 事件作为响应，还是只记录超时。</span><span class="sxs-lookup"><span data-stu-id="137c6-129">Specify whether the task logs a WMI query time-out and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] event in response, or only logs the time-out.</span></span>  
  
 <span data-ttu-id="137c6-130">**AfterTimeout**</span><span class="sxs-lookup"><span data-stu-id="137c6-130">**AfterTimeout**</span></span>  
 <span data-ttu-id="137c6-131">指定任务对超时的响应是成功还是失败，或者任务是否继续监视超时的再次发生。</span><span class="sxs-lookup"><span data-stu-id="137c6-131">Specify whether the task succeeds or fails in response to a time-out, or if the task continues watching for another time-out to recur.</span></span>  
  
 <span data-ttu-id="137c6-132">**NumberOfEvents**</span><span class="sxs-lookup"><span data-stu-id="137c6-132">**NumberOfEvents**</span></span>  
 <span data-ttu-id="137c6-133">指定要监视的事件数。</span><span class="sxs-lookup"><span data-stu-id="137c6-133">Specify the number of events to watch for.</span></span>  
  
 <span data-ttu-id="137c6-134">**超时**</span><span class="sxs-lookup"><span data-stu-id="137c6-134">**Timeout**</span></span>  
 <span data-ttu-id="137c6-135">指定等待事件发生的秒数。</span><span class="sxs-lookup"><span data-stu-id="137c6-135">Specify the number of seconds to wait for the event to occur.</span></span> <span data-ttu-id="137c6-136">值为 0 表示实际上无超时。</span><span class="sxs-lookup"><span data-stu-id="137c6-136">A value of 0 means that no time-out is in effect.</span></span>  
  
## <a name="wqlquerysource-dynamic-options"></a><span data-ttu-id="137c6-137">WQLQuerySource 动态选项</span><span class="sxs-lookup"><span data-stu-id="137c6-137">WQLQuerySource Dynamic Options</span></span>  
  
### <a name="wqlquerysource--direct-input"></a><span data-ttu-id="137c6-138">WQLQuerySource = 直接输入</span><span class="sxs-lookup"><span data-stu-id="137c6-138">WQLQuerySource = Direct input</span></span>  
 <span data-ttu-id="137c6-139">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="137c6-139">**WQLQuerySource**</span></span>  
 <span data-ttu-id="137c6-140">提供查询，或单击省略号按钮 (...) 并使用“WQL 查询”对话框输入查询  。</span><span class="sxs-lookup"><span data-stu-id="137c6-140">Provide a query, or click the ellipsis button (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysource--file-connection"></a><span data-ttu-id="137c6-141">WQLQuerySource = 文件连接</span><span class="sxs-lookup"><span data-stu-id="137c6-141">WQLQuerySource = File connection</span></span>  
 <span data-ttu-id="137c6-142">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="137c6-142">**WQLQuerySource**</span></span>  
 <span data-ttu-id="137c6-143">从列表中选择文件连接管理器，或单击“\<**New connection...**>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="137c6-143">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="137c6-144">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="137c6-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysource--variable"></a><span data-ttu-id="137c6-145">WQLQuerySource = 变量</span><span class="sxs-lookup"><span data-stu-id="137c6-145">WQLQuerySource = Variable</span></span>  
 <span data-ttu-id="137c6-146">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="137c6-146">**WQLQuerySource**</span></span>  
 <span data-ttu-id="137c6-147">在列表中选择变量，或单击 \<**New variable...**> 创建新变量。</span><span class="sxs-lookup"><span data-stu-id="137c6-147">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="137c6-148">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="137c6-148">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137c6-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="137c6-149">See Also</span></span>  
 <span data-ttu-id="137c6-150">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="137c6-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="137c6-151">[WMI 事件观察器任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="137c6-151">[WMI Event Watcher Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="137c6-152">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="137c6-152">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="137c6-153">WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="137c6-153">WMI Data Reader Task</span></span>](control-flow/wmi-data-reader-task.md)  
  
  
