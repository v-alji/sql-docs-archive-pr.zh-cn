---
title: "\"属性配置文件\" 选项卡 (挖掘模型查看器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61c81b95f030bf1a69aed165bd64e58ff9af8339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579360"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a><span data-ttu-id="e3fcd-102">“属性配置文件”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="e3fcd-102">Attribute Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="e3fcd-103">可以使用 **“属性配置文件”** 选项卡，来查看 Naive Bayes 模型状态中输入值的分布如何生成结果属性的每个状态。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-103">Use the **Attribute Profiles** tab to see how the distribution of input values in a Naive Bayes model state contribute to each state of the outcome attribute.</span></span> <span data-ttu-id="e3fcd-104">值的分布会显示为一个彩色直方图且所有分布都以表格格式显示，以便能更轻松地比较值。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-104">The distribution of values is shown as a colored histogram, all distributions presented in a tabular format, to make it easier to compare values.</span></span>  
  
 <span data-ttu-id="e3fcd-105">\*\*有关详细信息，请参阅 \*\* [Microsoft Naive Bayes 算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft Naive Bayes 查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="e3fcd-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="e3fcd-106">选项</span><span class="sxs-lookup"><span data-stu-id="e3fcd-106">Options</span></span>  
 <span data-ttu-id="e3fcd-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="e3fcd-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="e3fcd-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-109">**Mining Model**</span></span>  
 <span data-ttu-id="e3fcd-110">从当前挖掘结构的挖掘模型中选择一个挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-110">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="e3fcd-111">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="e3fcd-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-112">**Viewer**</span></span>  
 <span data-ttu-id="e3fcd-113">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="e3fcd-114">可以选择为每个挖掘模型提供的自定义查看器或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-114">You can choose the custom viewer provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="e3fcd-115">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-115">You can also use plug-in viewers if they are available.</span></span>  
  
 <span data-ttu-id="e3fcd-116">**显示图例**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-116">**Show Legend**</span></span>  
 <span data-ttu-id="e3fcd-117">选择此选项可显示一个键，该键将“状态”\*\*\*\* 中的每个值与分布图表中使用的一种颜色匹配。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-117">Select this option to display a key that matches each value in **States** to one of the colors used in the distribution chart.</span></span>  
  
 <span data-ttu-id="e3fcd-118">**直方图图条**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-118">**Histogram bars**</span></span>  
 <span data-ttu-id="e3fcd-119">选择要在直方图中包含多少个图条。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-119">Select how many bars to include in the histogram.</span></span> <span data-ttu-id="e3fcd-120">如果存在的图条数多于您选择显示的图条数，则会保留重要性最高的那些图条，其余图条则组合到 **“其他”** 中。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-120">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="e3fcd-121">**可预测**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-121">**Predictable**</span></span>  
 <span data-ttu-id="e3fcd-122">从挖掘模型中选择可预测列。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-122">Select a predictable column from the mining model.</span></span>  
  
 <span data-ttu-id="e3fcd-123">**属性配置文件**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-123">**Attribute Profiles**</span></span>  
 <span data-ttu-id="e3fcd-124">该表包含以下列：</span><span class="sxs-lookup"><span data-stu-id="e3fcd-124">The table contains the following columns:</span></span>  
  
|<span data-ttu-id="e3fcd-125">值</span><span class="sxs-lookup"><span data-stu-id="e3fcd-125">Value</span></span>|<span data-ttu-id="e3fcd-126">说明</span><span class="sxs-lookup"><span data-stu-id="e3fcd-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3fcd-127">**属性**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-127">**Attributes**</span></span>|<span data-ttu-id="e3fcd-128">列出挖掘模型中包含的挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-128">Lists the mining model columns contained within the mining model.</span></span>|  
|<span data-ttu-id="e3fcd-129">**状态**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-129">**States**</span></span>|<span data-ttu-id="e3fcd-130">一个说明相应属性行中的颜色所表示的状态的可选列。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-130">An optional column that describes what state the color in the corresponding row of attributes represents.</span></span> <span data-ttu-id="e3fcd-131">通过使用 **“显示图例”** 复选框进行添加或删除。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-131">Add or remove by using the **Show Legend** check box.</span></span>|  
|<span data-ttu-id="e3fcd-132">**总数**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-132">**Population**</span></span>|<span data-ttu-id="e3fcd-133">显示属性在整个数据集中的分布情况。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-133">Displays the distribution of the attribute across the whole dataset.</span></span>|  
|<span data-ttu-id="e3fcd-134">**可预测属性的状态列**</span><span class="sxs-lookup"><span data-stu-id="e3fcd-134">**Column for states of predictable attribute**</span></span>|<span data-ttu-id="e3fcd-135">为可预测列的每个状态显示一列，其中每一行对应于模型中的一个输入属性。</span><span class="sxs-lookup"><span data-stu-id="e3fcd-135">Displays a column for each state of the predictable column, with each row corresponding to an input attribute in the model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3fcd-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3fcd-136">See Also</span></span>  
 <span data-ttu-id="e3fcd-137">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e3fcd-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e3fcd-138">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e3fcd-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="e3fcd-139">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="e3fcd-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
