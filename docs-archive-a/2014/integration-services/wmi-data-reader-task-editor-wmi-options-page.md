---
title: WMI 数据读取器任务编辑器 (WMI 选项 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb28e7f8f352f708085bf664757391a05869752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590250"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a><span data-ttu-id="273d0-102">WMI 数据读取器任务编辑器（“WMI 选项”页）</span><span class="sxs-lookup"><span data-stu-id="273d0-102">WMI Data Reader Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="273d0-103">可以使用“WMI 数据读取器任务编辑器”  对话框的“WMI 选项”  页，指定 Windows Management Instrumentation 查询语言 (WQL) 查询的源和查询结果的目标。</span><span class="sxs-lookup"><span data-stu-id="273d0-103">Use the **WMI Options** page of the **WMI Data Reader Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and the destination of the query result.</span></span>  
  
 <span data-ttu-id="273d0-104">若要了解此任务，请参阅 [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)。</span><span class="sxs-lookup"><span data-stu-id="273d0-104">To learn about this task, see [WMI Data Reader Task](control-flow/wmi-data-reader-task.md).</span></span> <span data-ttu-id="273d0-105">有关 WMI 查询语言 (WQL) 的详细信息，请参阅 MSDN 库中的 Windows Management Instrumentation 主题 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)（利用 WQL 进行查询）。</span><span class="sxs-lookup"><span data-stu-id="273d0-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="273d0-106">静态选项</span><span class="sxs-lookup"><span data-stu-id="273d0-106">Static Options</span></span>  
 <span data-ttu-id="273d0-107">**WMIConnectionName**</span><span class="sxs-lookup"><span data-stu-id="273d0-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="273d0-108">从列表中选择 WMI 连接管理器，或单击 \<**New WMI Connection...**> 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="273d0-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="273d0-109">**相关主题：** [WMI 连接管理器](connection-manager/wmi-connection-manager.md)、[WMI 连接管理器编辑器](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="273d0-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="273d0-110">**WQLQuerySourceType**</span><span class="sxs-lookup"><span data-stu-id="273d0-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="273d0-111">选择任务运行的 WQL 查询的源类型。</span><span class="sxs-lookup"><span data-stu-id="273d0-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="273d0-112">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="273d0-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="273d0-113">值</span><span class="sxs-lookup"><span data-stu-id="273d0-113">Value</span></span>|<span data-ttu-id="273d0-114">说明</span><span class="sxs-lookup"><span data-stu-id="273d0-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="273d0-115">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="273d0-115">**Direct input**</span></span>|<span data-ttu-id="273d0-116">为 WQL 查询设置源。</span><span class="sxs-lookup"><span data-stu-id="273d0-116">Set the source to a WQL query.</span></span> <span data-ttu-id="273d0-117">选择此值将显示动态选项 **WQLQuerySourceType**。</span><span class="sxs-lookup"><span data-stu-id="273d0-117">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="273d0-118">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="273d0-118">**File connection**</span></span>|<span data-ttu-id="273d0-119">选择包含 WQL 查询的文件。</span><span class="sxs-lookup"><span data-stu-id="273d0-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="273d0-120">选择此值将显示动态选项 **WQLQuerySourceType**。</span><span class="sxs-lookup"><span data-stu-id="273d0-120">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="273d0-121">**变量**</span><span class="sxs-lookup"><span data-stu-id="273d0-121">**Variable**</span></span>|<span data-ttu-id="273d0-122">将源设置为定义 WQL 查询的变量。</span><span class="sxs-lookup"><span data-stu-id="273d0-122">Set the source to a variable that defines the WQL query.</span></span> <span data-ttu-id="273d0-123">选择此值将显示动态选项 **WQLQuerySourceType**。</span><span class="sxs-lookup"><span data-stu-id="273d0-123">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
  
 <span data-ttu-id="273d0-124">**OutputType**</span><span class="sxs-lookup"><span data-stu-id="273d0-124">**OutputType**</span></span>  
 <span data-ttu-id="273d0-125">指定输出是数据表、属性值还是属性名称和值。</span><span class="sxs-lookup"><span data-stu-id="273d0-125">Specify whether the output should be a data table, property value, or property name and value.</span></span>  
  
 <span data-ttu-id="273d0-126">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="273d0-126">**OverwriteDestination**</span></span>  
 <span data-ttu-id="273d0-127">指定是保留、覆盖还是追加到目标文件或变量中的原始数据。</span><span class="sxs-lookup"><span data-stu-id="273d0-127">Specifies whether to keep, overwrite, or append to the original data in the destination file or variable.</span></span>  
  
 <span data-ttu-id="273d0-128">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="273d0-128">**DestinationType**</span></span>  
 <span data-ttu-id="273d0-129">选择任务运行的 WQL 查询的目标类型。</span><span class="sxs-lookup"><span data-stu-id="273d0-129">Select the destination type of the WQL query that the task runs.</span></span> <span data-ttu-id="273d0-130">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="273d0-130">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="273d0-131">值</span><span class="sxs-lookup"><span data-stu-id="273d0-131">Value</span></span>|<span data-ttu-id="273d0-132">说明</span><span class="sxs-lookup"><span data-stu-id="273d0-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="273d0-133">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="273d0-133">**File connection**</span></span>|<span data-ttu-id="273d0-134">选择用于保存 WQL 查询结果的文件。</span><span class="sxs-lookup"><span data-stu-id="273d0-134">Select a file to save the results of the WQL query in.</span></span> <span data-ttu-id="273d0-135">选择此值将显示动态选项 **DestinationType**。</span><span class="sxs-lookup"><span data-stu-id="273d0-135">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
|<span data-ttu-id="273d0-136">**变量**</span><span class="sxs-lookup"><span data-stu-id="273d0-136">**Variable**</span></span>|<span data-ttu-id="273d0-137">设置用于存储 WQL 查询结果的变量。</span><span class="sxs-lookup"><span data-stu-id="273d0-137">Set the variable to store the results of the WQL query in.</span></span> <span data-ttu-id="273d0-138">选择此值将显示动态选项 **DestinationType**。</span><span class="sxs-lookup"><span data-stu-id="273d0-138">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a><span data-ttu-id="273d0-139">WQLQuerySourceType 动态选项</span><span class="sxs-lookup"><span data-stu-id="273d0-139">WQLQuerySourceType Dynamic Options</span></span>  
  
### <a name="wqlquerysourcetype--direct-input"></a><span data-ttu-id="273d0-140">WQLQuerySourceType = 直接输入</span><span class="sxs-lookup"><span data-stu-id="273d0-140">WQLQuerySourceType = Direct input</span></span>  
 <span data-ttu-id="273d0-141">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="273d0-141">**WQLQuerySource**</span></span>  
 <span data-ttu-id="273d0-142">提供查询，或单击省略号 (…)，然后使用“WQL 查询”对话框输入查询  。</span><span class="sxs-lookup"><span data-stu-id="273d0-142">Provide a query, or click the ellipsis (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysourcetype--file-connection"></a><span data-ttu-id="273d0-143">WQLQuerySourceType = 文件连接</span><span class="sxs-lookup"><span data-stu-id="273d0-143">WQLQuerySourceType = File connection</span></span>  
 <span data-ttu-id="273d0-144">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="273d0-144">**WQLQuerySource**</span></span>  
 <span data-ttu-id="273d0-145">从列表中选择文件连接管理器，或单击“\<**New connection...**>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="273d0-145">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="273d0-146">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="273d0-146">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysourcetype--variable"></a><span data-ttu-id="273d0-147">WQLQuerySourceType = 变量</span><span class="sxs-lookup"><span data-stu-id="273d0-147">WQLQuerySourceType = Variable</span></span>  
 <span data-ttu-id="273d0-148">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="273d0-148">**WQLQuerySource**</span></span>  
 <span data-ttu-id="273d0-149">在列表中选择变量，或单击 \<**New variable...**> 创建新变量。</span><span class="sxs-lookup"><span data-stu-id="273d0-149">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="273d0-150">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="273d0-150">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="destinationtype-dynamic-options"></a><span data-ttu-id="273d0-151">DestinationType 动态选项</span><span class="sxs-lookup"><span data-stu-id="273d0-151">DestinationType Dynamic Options</span></span>  
  
### <a name="destinationtype--file-connection"></a><span data-ttu-id="273d0-152">DestinationType = 文件连接</span><span class="sxs-lookup"><span data-stu-id="273d0-152">DestinationType = File connection</span></span>  
 <span data-ttu-id="273d0-153">**目标**</span><span class="sxs-lookup"><span data-stu-id="273d0-153">**Destination**</span></span>  
 <span data-ttu-id="273d0-154">从列表中选择文件连接管理器，或单击 \<**New connection...**> 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="273d0-154">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="273d0-155">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="273d0-155">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="destinationtype--variable"></a><span data-ttu-id="273d0-156">DestinationType = 变量</span><span class="sxs-lookup"><span data-stu-id="273d0-156">DestinationType = Variable</span></span>  
 <span data-ttu-id="273d0-157">**目标**</span><span class="sxs-lookup"><span data-stu-id="273d0-157">**Destination**</span></span>  
 <span data-ttu-id="273d0-158">在列表中选择变量，或单击 \<**New variable...**> 创建新变量。</span><span class="sxs-lookup"><span data-stu-id="273d0-158">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="273d0-159">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="273d0-159">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273d0-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="273d0-160">See Also</span></span>  
 <span data-ttu-id="273d0-161">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="273d0-161">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="273d0-162">[WMI 数据读取器任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="273d0-162">[WMI Data Reader Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="273d0-163">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="273d0-163">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="273d0-164">WMI 事件观察器任务</span><span class="sxs-lookup"><span data-stu-id="273d0-164">WMI Event Watcher Task</span></span>](control-flow/wmi-event-watcher-task.md)  
  
  
