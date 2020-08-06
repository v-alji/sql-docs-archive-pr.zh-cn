---
title: 从模型查看器使用钻取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97bf20023009ec0e245126644d9fd38537182b2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691358"
---
# <a name="use-drillthrough-from-the-model-viewers"></a><span data-ttu-id="7e8bf-102">从模型查看器使用钻取</span><span class="sxs-lookup"><span data-stu-id="7e8bf-102">Use Drillthrough from the Model Viewers</span></span>
  <span data-ttu-id="7e8bf-103">根据模型类型，您可以从数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上的浏览查看器中使用钻取功能，以便浏览在挖掘模型中使用的事例或查看挖掘结构中的其他列。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-103">Depending on the model type, you can use drillthrough from the browse viewers on the **Mining Model Viewer** tab of Data Mining Designer to explore the cases used in the mining model or to see additional columns in the mining structure.</span></span> <span data-ttu-id="7e8bf-104">尽管因为模型中的模式无法直接链接到特定事例，导致许多模型类型不支持钻取功能，但以下模型类型是支持钻取功能的。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-104">Although many model types do not support drillthrough because the patterns in the model cannot be directly linked to specific cases, the following model types do support drillthrough.</span></span>  
  
 <span data-ttu-id="7e8bf-105">请注意，必须对模型启用钻取，并且您必须拥有适当的权限。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-105">Note that drillthrough must have been enabled on the model, and you must have the appropriate permissions.</span></span> <span data-ttu-id="7e8bf-106">如果模型处于未处理状态，钻取选项也可能会被禁用；而与模型是否以前已处理和具有内容无关。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-106">The drillthrough option might also be disabled if the model is in an unprocessed state, regardless of whether the model was previously processed and has content.</span></span> <span data-ttu-id="7e8bf-107">若要通过使用钻取功能检索模型事例数据，结构和模型的缓存必须是当前的。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-107">To retrieve model case data by using drillthrough, the cache of the structure and model must be current.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a><span data-ttu-id="7e8bf-108">在 Microsoft 树查看器中使用钻取</span><span class="sxs-lookup"><span data-stu-id="7e8bf-108">Use drillthrough in the Microsoft Tree Viewer</span></span>  
  
1.  <span data-ttu-id="7e8bf-109">在数据挖掘设计器中，选择某一决策树模型，并且选择 **“浏览模型”** 以便在 **“Microsoft 树查看器”** 中打开该模型。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-109">In Data Mining Designer, select a decision trees model, and select **Browse Model** to open the model in the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="7e8bf-110">在 SQL Server Management Studio 中，右键单击该模型，然后选择“浏览”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7e8bf-110">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="7e8bf-111">右键单击树图形中的任何节点，然后选择“钻取”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-111">Right-click any node in the tree graph, and select **Drill through**.</span></span>  
  
3.  <span data-ttu-id="7e8bf-112">选择以下选项之一： **“仅限模型列”** 或 **“模型和结构列”**。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-112">Select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="7e8bf-113">如果您没有权限，则某个选项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-113">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="7e8bf-114">“钻取”\*\*\*\* 对话框将打开，并且显示事例数据和/或结构数据。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-114">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="7e8bf-115">该对话框的标题栏还包含说明，标识已从其执行钻取查询的节点。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-115">The title bar of the dialog box also contains a description that identifies the node from which the drillthrough query was executed.</span></span>  
  
5.  <span data-ttu-id="7e8bf-116">右键单击结果中的任何地方，然后选择“全部复制”\*\*\*\* 以便将结果保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-116">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a><span data-ttu-id="7e8bf-117">在 Microsoft 分类查看器中使用钻取</span><span class="sxs-lookup"><span data-stu-id="7e8bf-117">Use drillthrough in the Microsoft Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="7e8bf-118">在数据挖掘设计器中，选择某一聚类分析模型，并且选择 **“浏览模型”** 以便在 **“Microsoft 分类查看器”** 中打开该模型。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-118">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="7e8bf-119">在 SQL Server Management Studio 中，右键单击该模型，然后选择 "**浏览**"。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-119">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="7e8bf-120">对“分类”\*\*\*\* 选项卡上，右键单击任何节点。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-120">On the **Cluster** tab, right-click any node.</span></span>  
  
3.  <span data-ttu-id="7e8bf-121">选择 **“钻取”**，然后选择以下选项之一： **“仅限模型列”** 或 **“模型和结构列”**。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-121">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="7e8bf-122">如果您没有权限，则某个选项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-122">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="7e8bf-123">“钻取”\*\*\*\* 对话框将打开，并且显示事例数据和/或结构数据。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-123">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="7e8bf-124">该对话框的标题栏还包含标识事例分类的说明。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-124">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="7e8bf-125">右键单击结果中的任何地方，然后选择“全部复制”\*\*\*\* 以便将结果保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-125">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a><span data-ttu-id="7e8bf-126">在 Microsoft 关联规则查看器中使用钻取</span><span class="sxs-lookup"><span data-stu-id="7e8bf-126">Use drillthrough in the Microsoft Association Rules Viewer</span></span>  
  
1.  <span data-ttu-id="7e8bf-127">在数据挖掘设计器中，选择某一关联模型，并且选择 **“浏览模型”** 以便在 **“Microsoft 关联规则查看器”** 中打开该模型。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-127">In Data Mining Designer, select an association model, and select **Browse Model** to open the model in the **Microsoft Association Rules Viewer**.</span></span> <span data-ttu-id="7e8bf-128">在 SQL Server Management Studio 中，右键单击该模型，然后选择“浏览”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7e8bf-128">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="7e8bf-129">在“规则”\*\*\*\* 选项卡上，右键单击表示某一规则的任何行。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-129">On the **Rules** tab, right-click any row that represents a rule.</span></span> <span data-ttu-id="7e8bf-130">在 **“项集”** 选项卡上，单击包含某一项集的任何行。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-130">On the **Itemsets** tab, click on any row that contains an itemset.</span></span>  
  
3.  <span data-ttu-id="7e8bf-131">选择 **“钻取”**，然后选择以下选项之一： **“仅限模型列”** 或 **“模型和结构列”**。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-131">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="7e8bf-132">如果您没有权限，则某个选项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-132">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="7e8bf-133">“钻取”\*\*\*\* 对话框将打开，并且显示事例数据和/或结构数据。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-133">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="7e8bf-134">该对话框的标题栏还包含标识规则名称的说明。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-134">The title bar of the dialog box also contains a description that identifies the rule name.</span></span>  
  
5.  <span data-ttu-id="7e8bf-135">右键单击结果中的任何地方，然后选择“全部复制”\*\*\*\* 以便将完整事例结果保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-135">Right-click anywhere in the results and select **Copy All** to save the complete case results to the Clipboard.</span></span> <span data-ttu-id="7e8bf-136">您还可以选择 **“复制”** 以便只复制所选事例。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-136">You can also select **Copy** to copy just the selected case.</span></span> <span data-ttu-id="7e8bf-137">如果模型包含嵌套表列，则只粘贴嵌套表列的名称；若要检索每个事例的嵌套表列内的数据值，您必须对模型内容创建查询。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-137">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a><span data-ttu-id="7e8bf-138">在 Microsoft 序列分类查看器中使用钻取</span><span class="sxs-lookup"><span data-stu-id="7e8bf-138">Use drillthrough in the Microsoft Sequence Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="7e8bf-139">在数据挖掘设计器中，选择某一聚类分析模型，并且选择 **“浏览模型”** 以便在 **“Microsoft 分类查看器”** 中打开该模型。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-139">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="7e8bf-140">在 SQL Server Management Studio 中，右键单击该模型，然后选择 "**浏览**"。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-140">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="7e8bf-141">对“分类关系图”\*\*\*\* 选项卡上，右键单击表示某一分类的任何节点。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-141">On the **Cluster Diagram tab**, right-click any node that represents a cluster.</span></span> <span data-ttu-id="7e8bf-142">从 **“分类剖面图”** 选项卡，在分类剖面图中或者表示模型总量的分类中单击任何地方。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-142">From the **Cluster Profiles** tab, click anywhere in a cluster profile or in the cluster representing the total model population.</span></span>  
  
3.  <span data-ttu-id="7e8bf-143">选择 **“钻取”**，然后选择以下选项之一： **“仅限模型列”** 或 **“模型和结构列”**。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-143">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="7e8bf-144">如果您没有权限，则某个选项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-144">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="7e8bf-145">“钻取”\*\*\*\* 对话框将打开，并且显示事例数据和/或结构数据。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-145">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="7e8bf-146">该对话框的标题栏还包含标识事例分类的说明。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-146">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="7e8bf-147">右键单击结果中的任何地方，然后选择“全部复制”\*\*\*\* 以便将结果保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-147">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span> <span data-ttu-id="7e8bf-148">如果模型包含嵌套表列，则只粘贴嵌套表列的名称；若要检索每个事例的嵌套表列内的数据值，您必须对模型内容创建查询。</span><span class="sxs-lookup"><span data-stu-id="7e8bf-148">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8bf-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e8bf-149">See Also</span></span>  
 <span data-ttu-id="7e8bf-150">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7e8bf-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="7e8bf-151">[挖掘模型钻取](drillthrough-on-mining-models.md) </span><span class="sxs-lookup"><span data-stu-id="7e8bf-151">[Drillthrough on Mining Models](drillthrough-on-mining-models.md) </span></span>  
 [<span data-ttu-id="7e8bf-152">对挖掘结构的钻取功能</span><span class="sxs-lookup"><span data-stu-id="7e8bf-152">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
