---
title: 数据挖掘查询任务编辑器 (查询选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.query.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 72b1755d-d226-46c5-b862-0c9333196a10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6005c92d0d48850461c01353ddf94c61140d0f2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692452"
---
# <a name="data-mining-query-task-editor-query-tab"></a><span data-ttu-id="0525b-102">数据挖掘查询任务编辑器（“查询”选项卡）</span><span class="sxs-lookup"><span data-stu-id="0525b-102">Data Mining Query Task Editor (Query Tab)</span></span>
  <span data-ttu-id="0525b-103">可以使用 **“数据挖掘查询任务”** 对话框的 **“查询”** 选项卡，基于挖掘模式创建预测查询。</span><span class="sxs-lookup"><span data-stu-id="0525b-103">Use the **Query** tab of the **Data Mining Query Task** dialog box to create prediction queries based on a mining model.</span></span> <span data-ttu-id="0525b-104">在此对话框中还可以将参数和结果集绑定到变量。</span><span class="sxs-lookup"><span data-stu-id="0525b-104">In this dialog box you can also bind parameters and result sets to variables.</span></span>  
  
 <span data-ttu-id="0525b-105">若要了解有关在包中实现数据挖掘的详细信息，请参阅 [数据挖掘查询任务](control-flow/data-mining-query-task.md) 和 [数据挖掘解决方案](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)。</span><span class="sxs-lookup"><span data-stu-id="0525b-105">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="0525b-106">常规选项</span><span class="sxs-lookup"><span data-stu-id="0525b-106">General Options</span></span>  
 <span data-ttu-id="0525b-107">**名称**</span><span class="sxs-lookup"><span data-stu-id="0525b-107">**Name**</span></span>  
 <span data-ttu-id="0525b-108">为数据挖掘查询任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="0525b-108">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="0525b-109">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="0525b-109">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0525b-110">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0525b-110">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="0525b-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="0525b-111">**Description**</span></span>  
 <span data-ttu-id="0525b-112">键入数据挖掘查询任务的说明。</span><span class="sxs-lookup"><span data-stu-id="0525b-112">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="build-query-tab-options"></a><span data-ttu-id="0525b-113">“生成查询”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="0525b-113">Build Query Tab Options</span></span>  
 <span data-ttu-id="0525b-114">**数据挖掘查询**</span><span class="sxs-lookup"><span data-stu-id="0525b-114">**Data mining query**</span></span>  
 <span data-ttu-id="0525b-115">键入数据挖掘查询。</span><span class="sxs-lookup"><span data-stu-id="0525b-115">Type a data mining query.</span></span>  
  
 <span data-ttu-id="0525b-116">**相关主题：**  [数据挖掘扩展插件 (DMX) 参考](/sql/dmx/data-mining-extensions-dmx-reference)</span><span class="sxs-lookup"><span data-stu-id="0525b-116">**Related Topics:**  [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference)</span></span>  
  
 <span data-ttu-id="0525b-117">**生成新查询**</span><span class="sxs-lookup"><span data-stu-id="0525b-117">**Build New Query**</span></span>  
 <span data-ttu-id="0525b-118">使用图形工具创建数据挖掘查询。</span><span class="sxs-lookup"><span data-stu-id="0525b-118">Create the data mining query using a graphical tool.</span></span>  
  
 <span data-ttu-id="0525b-119">**相关主题：** [Data Mining Query](control-flow/data-mining-query.md)</span><span class="sxs-lookup"><span data-stu-id="0525b-119">**Related Topics:** [Data Mining Query](control-flow/data-mining-query.md)</span></span>  
  
## <a name="parameter-mapping-tab-options"></a><span data-ttu-id="0525b-120">“参数映射”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="0525b-120">Parameter Mapping Tab Options</span></span>  
 <span data-ttu-id="0525b-121">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="0525b-121">**Parameter Name**</span></span>  
 <span data-ttu-id="0525b-122">根据需要更新参数名称。</span><span class="sxs-lookup"><span data-stu-id="0525b-122">Optionally, update the parameter name.</span></span> <span data-ttu-id="0525b-123">通过在 **“变量名称”** 列表中选择变量，将参数映射到变量。</span><span class="sxs-lookup"><span data-stu-id="0525b-123">Map the parameter to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="0525b-124">**“变量名称”**</span><span class="sxs-lookup"><span data-stu-id="0525b-124">**Variable Name**</span></span>  
 <span data-ttu-id="0525b-125">在列表中选择变量以将其映射到参数。</span><span class="sxs-lookup"><span data-stu-id="0525b-125">Select a variable in the list to map it to the parameter.</span></span>  
  
 <span data-ttu-id="0525b-126">**添加**</span><span class="sxs-lookup"><span data-stu-id="0525b-126">**Add**</span></span>  
 <span data-ttu-id="0525b-127">将参数添加到列表。</span><span class="sxs-lookup"><span data-stu-id="0525b-127">Add to a parameter to the list.</span></span>  
  
 <span data-ttu-id="0525b-128">**移除**</span><span class="sxs-lookup"><span data-stu-id="0525b-128">**Remove**</span></span>  
 <span data-ttu-id="0525b-129">选择一个参数，再单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0525b-129">Select a parameter, and then click **Remove**.</span></span>  
  
## <a name="result-set-tab-options"></a><span data-ttu-id="0525b-130">“结果集”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="0525b-130">Result Set Tab Options</span></span>  
 <span data-ttu-id="0525b-131">**结果名称**</span><span class="sxs-lookup"><span data-stu-id="0525b-131">**Result Name**</span></span>  
 <span data-ttu-id="0525b-132">根据需要更新结果集的名称。</span><span class="sxs-lookup"><span data-stu-id="0525b-132">Optionally, update the result set name.</span></span> <span data-ttu-id="0525b-133">通过在 **“变量名称”** 列表中选择变量，将结果映射到变量。</span><span class="sxs-lookup"><span data-stu-id="0525b-133">Map the result to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="0525b-134">通过单击 **“添加”** 添加结果之后，为该结果提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="0525b-134">After you have added a result by clicking **Add**, provide a unique name for the result.</span></span>  
  
 <span data-ttu-id="0525b-135">**“变量名称”**</span><span class="sxs-lookup"><span data-stu-id="0525b-135">**Variable Name**</span></span>  
 <span data-ttu-id="0525b-136">在列表中选择变量以将其映射到结果集。</span><span class="sxs-lookup"><span data-stu-id="0525b-136">Select a variable in the list to map it to the result set.</span></span>  
  
 <span data-ttu-id="0525b-137">**结果类型**</span><span class="sxs-lookup"><span data-stu-id="0525b-137">**Result Type**</span></span>  
 <span data-ttu-id="0525b-138">指示是返回单行还是返回完整结果集。</span><span class="sxs-lookup"><span data-stu-id="0525b-138">Indicate whether to return a single row or a full result set.</span></span>  
  
 <span data-ttu-id="0525b-139">**添加**</span><span class="sxs-lookup"><span data-stu-id="0525b-139">**Add**</span></span>  
 <span data-ttu-id="0525b-140">向列表中添加结果集。</span><span class="sxs-lookup"><span data-stu-id="0525b-140">Add a result set to the list.</span></span>  
  
 <span data-ttu-id="0525b-141">**移除**</span><span class="sxs-lookup"><span data-stu-id="0525b-141">**Remove**</span></span>  
 <span data-ttu-id="0525b-142">选择一个结果，再单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0525b-142">Select a result, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0525b-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0525b-143">See Also</span></span>  
 <span data-ttu-id="0525b-144">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0525b-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0525b-145">[数据挖掘查询任务编辑器 &#40;挖掘模型 "选项卡&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="0525b-145">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="0525b-146">[数据挖掘查询任务编辑器 &#40;输出 "选项卡&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="0525b-146">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="0525b-147">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="0525b-147">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
