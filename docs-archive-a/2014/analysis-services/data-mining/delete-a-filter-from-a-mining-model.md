---
title: 从挖掘模型中删除筛选器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 404c23c0e55bffba2ce8410c9c30d6ad1fa1991b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578521"
---
# <a name="delete-a-filter-from-a-mining-model"></a><span data-ttu-id="6bb95-102">从挖掘模型中删除筛选器</span><span class="sxs-lookup"><span data-stu-id="6bb95-102">Delete a Filter from a Mining Model</span></span>
  <span data-ttu-id="6bb95-103">在挖掘模型上创建筛选器时，可以在数据源视图中的数据子集上创建模型。</span><span class="sxs-lookup"><span data-stu-id="6bb95-103">When you create a filter on a mining model, you can create models on a subset of the data in the data source view.</span></span> <span data-ttu-id="6bb95-104">对于在原始数据子集上测试模型的准确性，筛选器也很有用。</span><span class="sxs-lookup"><span data-stu-id="6bb95-104">Filters are also useful for testing the accuracy of the model on a subset of the original data.</span></span>  
  
 <span data-ttu-id="6bb95-105">不过，若要再次查看全部事例，则必须删除筛选器。</span><span class="sxs-lookup"><span data-stu-id="6bb95-105">However, you must delete the filter if you want to view the complete set of cases again.</span></span> <span data-ttu-id="6bb95-106">此过程介绍如何删除筛选器条件或完全删除筛选器。</span><span class="sxs-lookup"><span data-stu-id="6bb95-106">This procedure describes how to remove conditions on a filter, or delete the filter completely.</span></span>  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a><span data-ttu-id="6bb95-107">从挖掘模型筛选器中删除条件</span><span class="sxs-lookup"><span data-stu-id="6bb95-107">To delete a condition from a filter on a mining model</span></span>  
  
1.  <span data-ttu-id="6bb95-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中，单击包含要筛选的挖掘模型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="6bb95-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="6bb95-109">单击 **“挖掘模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6bb95-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="6bb95-110">选择模型，然后右键单击打开快捷菜单。</span><span class="sxs-lookup"><span data-stu-id="6bb95-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="6bb95-111">- 或 -</span><span class="sxs-lookup"><span data-stu-id="6bb95-111">-or-</span></span>  
  
     <span data-ttu-id="6bb95-112">选择该模型。</span><span class="sxs-lookup"><span data-stu-id="6bb95-112">Select the model.</span></span> <span data-ttu-id="6bb95-113">在 **“挖掘模型”** 菜单上，选择 **“设置模型筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="6bb95-113">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="6bb95-114">在“模型筛选器”\*\*\*\* 对话框中，右键单击网格中包含要删除的条件的行。</span><span class="sxs-lookup"><span data-stu-id="6bb95-114">In the **Model Filter** dialog box, right-click the row in the grid that contains the condition you want to delete.</span></span>  
  
5.  <span data-ttu-id="6bb95-115">选择“删除”。</span><span class="sxs-lookup"><span data-stu-id="6bb95-115">Select **Delete**.</span></span>  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a><span data-ttu-id="6bb95-116">在“筛选器编辑器”对话框中清除挖掘模型筛选器</span><span class="sxs-lookup"><span data-stu-id="6bb95-116">To clear the filter on a mining model in the Filter Editor dialog box</span></span>  
  
-   <span data-ttu-id="6bb95-117">在“筛选器编辑器”\*\*\*\* 对话框中，右键单击网格中的任意行，然后选择“全部删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6bb95-117">In the **Filter Editor** dialog box, right-click any row in the grid, and select **Delete All**.</span></span>  
  
## <a name="working-with-model-filters-using-the-properties-window"></a><span data-ttu-id="6bb95-118">通过“属性”窗口处理模型筛选器</span><span class="sxs-lookup"><span data-stu-id="6bb95-118">Working with Model Filters Using the Properties Window</span></span>  
 <span data-ttu-id="6bb95-119">若要删除整个筛选器，无需打开筛选器编辑器对话框。</span><span class="sxs-lookup"><span data-stu-id="6bb95-119">If you want to delete the whole filter, you do not need to open the filter editor dialog boxes.</span></span> <span data-ttu-id="6bb95-120">您所创建的筛选条件可在挖掘模型的 `Filter` 属性中找到。</span><span class="sxs-lookup"><span data-stu-id="6bb95-120">The filter conditions that you created are available in the `Filter` property of the mining model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bb95-121">可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中查看挖掘模型的属性，但不能在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看。</span><span class="sxs-lookup"><span data-stu-id="6bb95-121">You can view the properties of a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], but not in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a><span data-ttu-id="6bb95-122">在解决方案资源管理器中清除挖掘模型筛选器</span><span class="sxs-lookup"><span data-stu-id="6bb95-122">To clear the filter on a mining model in Solution Explorer</span></span>  
  
1.  <span data-ttu-id="6bb95-123">在解决方案资源管理器中，单击包含筛选器的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="6bb95-123">In Solution Explorer, click the mining model that contains the filter.</span></span>  
  
2.  <span data-ttu-id="6bb95-124">在 "**属性**" 窗口中，右键单击属性中的筛选器文本 `Filter` ，然后选择 "全**选**"。</span><span class="sxs-lookup"><span data-stu-id="6bb95-124">In the **Properties** window, right-click the filter text in the `Filter` property, and select **Select All**.</span></span>  
  
3.  <span data-ttu-id="6bb95-125">按 Backspace 或 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="6bb95-125">Press the Backspace or Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb95-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bb95-126">See Also</span></span>  
 <span data-ttu-id="6bb95-127">[从挖掘模型钻取到事例数据](drill-through-to-case-data-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="6bb95-127">[Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md) </span></span>  
 <span data-ttu-id="6bb95-128">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="6bb95-128">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="6bb95-129">挖掘模型的筛选器（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="6bb95-129">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
  
