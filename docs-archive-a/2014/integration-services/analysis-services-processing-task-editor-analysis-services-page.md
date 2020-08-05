---
title: Analysis Services 处理任务编辑器 (Analysis Services "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aabcfe286b40f58b429227654107d58e8a4ee837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579717"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a><span data-ttu-id="abc49-102">Analysis Services 处理任务编辑器（Analysis Services 页）</span><span class="sxs-lookup"><span data-stu-id="abc49-102">Analysis Services Processing Task Editor (Analysis Services Page)</span></span>
  <span data-ttu-id="abc49-103">可以使用 **“Analysis Services 处理任务编辑器”** 对话框的 **Analysis Services** 页指定 Analysis Services 连接管理器，选择要处理的分析对象，以及设置处理选项和错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="abc49-103">Use the **Analysis Services** page of the **Analysis Services Processing Task Editor** dialog box to specify an Analysis Services connection manager, select the analytic objects to process, and set processing and error handling options.</span></span>  
  
 <span data-ttu-id="abc49-104">处理表格模型时，请记住以下事项：</span><span class="sxs-lookup"><span data-stu-id="abc49-104">When processing tabular models, keep the following in mind:</span></span>  
  
1.  <span data-ttu-id="abc49-105">不能对表格模型执行影响分析。</span><span class="sxs-lookup"><span data-stu-id="abc49-105">You cannot perform impact analysis on tabular models.</span></span>  
  
2.  <span data-ttu-id="abc49-106">不公开表格模型的一些处理选项，如“处理碎片整理”和“处理重新计算”。</span><span class="sxs-lookup"><span data-stu-id="abc49-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="abc49-107">您可以使用执行 DDL 任务来执行这些功能。</span><span class="sxs-lookup"><span data-stu-id="abc49-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
3.  <span data-ttu-id="abc49-108">提供的一些处理选项（如处理索引）不适用于表格模型，不应使用它们。</span><span class="sxs-lookup"><span data-stu-id="abc49-108">Some processing options provided, such as process indexes, are not appropriate for tabular models and should not be used.</span></span>  
  
4.  <span data-ttu-id="abc49-109">对表格模型忽略批处理设置。</span><span class="sxs-lookup"><span data-stu-id="abc49-109">Batch settings are ignored for tabular models.</span></span>  
  
 <span data-ttu-id="abc49-110">若要了解此任务，请参阅 [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md)。</span><span class="sxs-lookup"><span data-stu-id="abc49-110">To learn about this task, see [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="abc49-111">选项</span><span class="sxs-lookup"><span data-stu-id="abc49-111">Options</span></span>  
 <span data-ttu-id="abc49-112">**Analysis Services 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="abc49-112">**Analysis Services connection manager**</span></span>  
 <span data-ttu-id="abc49-113">从列表中选择现有的 Analysis Services 连接管理器，或单击\*\*\*\*“新建”以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="abc49-113">Select an existing Analysis Services connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="abc49-114">**新建**</span><span class="sxs-lookup"><span data-stu-id="abc49-114">**New**</span></span>  
 <span data-ttu-id="abc49-115">创建新的 Analysis Services 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="abc49-115">Create a new Analysis Services connection manager.</span></span>  
  
 <span data-ttu-id="abc49-116">**相关主题：** [Analysis Services 连接管理器](connection-manager/analysis-services-connection-manager.md)、[“添加 Analysis Services 连接管理器”对话框 UI 参考](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="abc49-116">**Related Topics:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="abc49-117">**对象列表**</span><span class="sxs-lookup"><span data-stu-id="abc49-117">**Object list**</span></span>  
 |<span data-ttu-id="abc49-118">属性</span><span class="sxs-lookup"><span data-stu-id="abc49-118">Property</span></span>|<span data-ttu-id="abc49-119">说明</span><span class="sxs-lookup"><span data-stu-id="abc49-119">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="abc49-120">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="abc49-120">**Object Name**</span></span>|<span data-ttu-id="abc49-121">列出指定对象的名称。</span><span class="sxs-lookup"><span data-stu-id="abc49-121">Lists the specified object names.</span></span>|  
|<span data-ttu-id="abc49-122">**Type**</span><span class="sxs-lookup"><span data-stu-id="abc49-122">**Type**</span></span>|<span data-ttu-id="abc49-123">列出指定对象的类型。</span><span class="sxs-lookup"><span data-stu-id="abc49-123">Lists the types of the specified objects.</span></span>|  
|<span data-ttu-id="abc49-124">**处理选项**</span><span class="sxs-lookup"><span data-stu-id="abc49-124">**Process Options**</span></span>|<span data-ttu-id="abc49-125">从列表中选择处理选项。</span><span class="sxs-lookup"><span data-stu-id="abc49-125">Select a processing option in the list.</span></span><br /><br /> <span data-ttu-id="abc49-126">**相关主题**：[多维模型对象处理](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span><span class="sxs-lookup"><span data-stu-id="abc49-126">**Related Topics**: [Multidimensional Model Object Processing](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span></span>|  
|<span data-ttu-id="abc49-127">**设置**</span><span class="sxs-lookup"><span data-stu-id="abc49-127">**Settings**</span></span>|<span data-ttu-id="abc49-128">列出指定对象的处理设置。</span><span class="sxs-lookup"><span data-stu-id="abc49-128">Lists processing settings for the specified objects.</span></span>|  
  
 <span data-ttu-id="abc49-129">**添加**</span><span class="sxs-lookup"><span data-stu-id="abc49-129">**Add**</span></span>  
 <span data-ttu-id="abc49-130">将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="abc49-130">Add an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object to the list.</span></span>  
  
 <span data-ttu-id="abc49-131">**移除**</span><span class="sxs-lookup"><span data-stu-id="abc49-131">**Remove**</span></span>  
 <span data-ttu-id="abc49-132">选择对象，再单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="abc49-132">Select an object, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="abc49-133">**影响分析**</span><span class="sxs-lookup"><span data-stu-id="abc49-133">**Impact Analysis**</span></span>  
 <span data-ttu-id="abc49-134">对所选对象进行影响分析。</span><span class="sxs-lookup"><span data-stu-id="abc49-134">Perform impact analysis on the selected object.</span></span>  
  
 <span data-ttu-id="abc49-135">**相关主题：** [“影响分析”对话框（Analysis Services - 多维数据）](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="abc49-135">**Related Topics:** [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
 <span data-ttu-id="abc49-136">**批设置摘要**</span><span class="sxs-lookup"><span data-stu-id="abc49-136">**Batch Settings Summary**</span></span>  
 |<span data-ttu-id="abc49-137">属性</span><span class="sxs-lookup"><span data-stu-id="abc49-137">Property</span></span>|<span data-ttu-id="abc49-138">说明</span><span class="sxs-lookup"><span data-stu-id="abc49-138">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="abc49-139">**处理顺序**</span><span class="sxs-lookup"><span data-stu-id="abc49-139">**Processing order**</span></span>|<span data-ttu-id="abc49-140">指定是按顺序处理对象还是按批处理对象；如果使用并行处理，则指定要并发处理的对象数。</span><span class="sxs-lookup"><span data-stu-id="abc49-140">Specifies whether objects are processed sequentially or in a batch; if parallel processing is used, specifies the number of objects to process concurrently.</span></span>|  
|<span data-ttu-id="abc49-141">**事务模式**</span><span class="sxs-lookup"><span data-stu-id="abc49-141">**Transaction mode**</span></span>|<span data-ttu-id="abc49-142">指定按顺序处理时的事务模式。</span><span class="sxs-lookup"><span data-stu-id="abc49-142">Specifies the transaction mode for sequential processing.</span></span>|  
|<span data-ttu-id="abc49-143">**维度错误**</span><span class="sxs-lookup"><span data-stu-id="abc49-143">**Dimension errors**</span></span>|<span data-ttu-id="abc49-144">指定在发生错误时的任务行为。</span><span class="sxs-lookup"><span data-stu-id="abc49-144">Specifies the task behavior when errors occur.</span></span>|  
|<span data-ttu-id="abc49-145">**维度键错误日志路径**</span><span class="sxs-lookup"><span data-stu-id="abc49-145">**Dimension key error log path**</span></span>|<span data-ttu-id="abc49-146">指定记录错误的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="abc49-146">Specifies the path of the file to which errors are logged.</span></span>|  
|<span data-ttu-id="abc49-147">**处理受影响的对象**</span><span class="sxs-lookup"><span data-stu-id="abc49-147">**Process affected objects**</span></span>|<span data-ttu-id="abc49-148">指示是否还处理依赖对象或受影响的对象。</span><span class="sxs-lookup"><span data-stu-id="abc49-148">Indicates whether dependent or affected objects are also processed.</span></span>|  
  
 <span data-ttu-id="abc49-149">**更改设置**</span><span class="sxs-lookup"><span data-stu-id="abc49-149">**Change Settings**</span></span>  
 <span data-ttu-id="abc49-150">更改处理选项以及对维度键中错误的处理方式。</span><span class="sxs-lookup"><span data-stu-id="abc49-150">Change the processing options and the handling of errors in dimension keys.</span></span>  
  
 <span data-ttu-id="abc49-151">**相关主题：** [“更改设置”对话框（Analysis Services - 多维数据）](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="abc49-151">**Related Topics:** [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc49-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abc49-152">See Also</span></span>  
 <span data-ttu-id="abc49-153">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="abc49-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="abc49-154">[Analysis Services 处理任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="abc49-154">[Analysis Services Processing Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="abc49-155">Analysis Services 执行 DDL 任务</span><span class="sxs-lookup"><span data-stu-id="abc49-155">Analysis Services Execute DDL Task</span></span>](control-flow/analysis-services-execute-ddl-task.md)  
  
  
