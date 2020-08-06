---
title: "\"分类矩阵\" 选项卡 (挖掘准确性图表视图) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
author: minewiskan
ms.author: owend
ms.openlocfilehash: d202d552b25095d0d0845ff64f9c0e289f7bba0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579267"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a><span data-ttu-id="3f116-102">“分类矩阵”选项卡（“挖掘准确性图表”视图）</span><span class="sxs-lookup"><span data-stu-id="3f116-102">Classification Matrix Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="3f116-103">"**分类矩阵**" 选项卡为在 "**列映射**" 选项卡上的 "模型" 网格中选择的每个模型显示分类矩阵。仅当在 "**列映射**" 选项卡中选择的可预测列不连续时，分类矩阵才可用。</span><span class="sxs-lookup"><span data-stu-id="3f116-103">The **Classification Matrix** tab displays a classification matrix for each model selected in the models grid on the **Column Mapping** tab. The classification matrix is only available if the predictable column that is selected in the **Column Mapping** tab is not continuous.</span></span> <span data-ttu-id="3f116-104">有关 "**分类矩阵**" 选项卡的详细说明，请参阅[测试和验证 &#40;数据挖掘&#41;](data-mining/testing-and-validation-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="3f116-104">For a more detailed description of the **Classification Matrix** tab, see [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f116-105">选项</span><span class="sxs-lookup"><span data-stu-id="3f116-105">Options</span></span>  
 <span data-ttu-id="3f116-106">**复制**</span><span class="sxs-lookup"><span data-stu-id="3f116-106">**Copy**</span></span>  
 <span data-ttu-id="3f116-107">将每个分类矩阵的内容复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="3f116-107">Copies the content of each classification matrix to the clipboard.</span></span>  
  
 <span data-ttu-id="3f116-108">**\<model>的计数\< predictable column>**</span><span class="sxs-lookup"><span data-stu-id="3f116-108">**Counts for \<model> on \< predictable column>**</span></span>  
 <span data-ttu-id="3f116-109">显示挖掘结构中每个挖掘模型的分类矩阵。</span><span class="sxs-lookup"><span data-stu-id="3f116-109">Displays a classification matrix for each mining model in the mining structure.</span></span> <span data-ttu-id="3f116-110">该矩阵包含以下列：</span><span class="sxs-lookup"><span data-stu-id="3f116-110">The matrix contains the following columns:</span></span>  
  
|<span data-ttu-id="3f116-111">值</span><span class="sxs-lookup"><span data-stu-id="3f116-111">Value</span></span>|<span data-ttu-id="3f116-112">说明</span><span class="sxs-lookup"><span data-stu-id="3f116-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f116-113">**预测**</span><span class="sxs-lookup"><span data-stu-id="3f116-113">**Predicted**</span></span>|<span data-ttu-id="3f116-114">对于可预测列的每一个状态包含一行。</span><span class="sxs-lookup"><span data-stu-id="3f116-114">Contains a row for each state of the predictable column.</span></span>|  
|<span data-ttu-id="3f116-115">\*\*\<states> (实际) \*\*</span><span class="sxs-lookup"><span data-stu-id="3f116-115">**\<states> (actual)**</span></span>|<span data-ttu-id="3f116-116">可预测列中与每个状态对应的列。</span><span class="sxs-lookup"><span data-stu-id="3f116-116">A column for each state in the predictable column.</span></span> <span data-ttu-id="3f116-117">如果行的状态与列的状态相对应，则单元显示数据库中该状态发生的实际次数。</span><span class="sxs-lookup"><span data-stu-id="3f116-117">If the state of the row and the column correspond, the cell represents the actual number of times the state exists in the database.</span></span> <span data-ttu-id="3f116-118">如果行的状态与列的状态不对应，则单元显示预测错误。</span><span class="sxs-lookup"><span data-stu-id="3f116-118">If they do not correspond, the cell represents the error of the prediction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f116-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f116-119">See Also</span></span>  
 <span data-ttu-id="3f116-120">[挖掘准确性图表设计器 &#40;数据挖掘&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3f116-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="3f116-121">[测试和验证任务以及操作方法 &#40;数据挖掘&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3f116-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="3f116-122">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="3f116-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
