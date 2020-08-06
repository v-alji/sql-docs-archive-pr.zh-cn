---
title: "\"提升图\" 选项卡 (挖掘准确性图表视图) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.liftchart.f1
ms.assetid: f1674e2e-d38e-40c7-b8d1-5585ce9a0168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cdad01ff3549140bf4fed606b1e8f9eaed10dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694626"
---
# <a name="lift-chart-tab-mining-accuracy-chart-view"></a><span data-ttu-id="cf9b7-102">“提升图”选项卡（“挖掘准确性图表”视图）</span><span class="sxs-lookup"><span data-stu-id="cf9b7-102">Lift Chart Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="cf9b7-103">可以使用 **“提升图”** 窗格，查看比较所选挖掘结构中的所有选定挖掘模型的图表。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-103">Use the **Lift Chart** pane to view a chart that compares all the selected mining models in the selected mining structure.</span></span>  
  
 <span data-ttu-id="cf9b7-104">如果模型预测离散值，则该窗格可以显示提升图或利润图。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-104">If the model predicts a discrete attribute, the pane can display either a lift chart or a profit chart.</span></span> <span data-ttu-id="cf9b7-105">有关提升图的信息，请参阅[提升图（Analysis Services - 数据挖掘）](data-mining/lift-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-105">For information about lift charts, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="cf9b7-106">若要创建利润图，您必须提供有关挖掘模型的建议的实施成本的其他信息以及预期的回报。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-106">To create a profit chart, you must provide additional information about the cost of implementing the recommendations of the mining model, as well as the expected return.</span></span> <span data-ttu-id="cf9b7-107">有关详细信息，请参阅[利润图（Analysis Services - 数据挖掘）](data-mining/profit-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-107">For more information, see [Profit Chart &#40;Analysis Services - Data Mining&#41;](data-mining/profit-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="cf9b7-108">如果模型预测连续属性，该窗格将显示散点图。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-108">If the model predicts a continuous attribute, the pane will display a scatter plot graph.</span></span>  
  
 <span data-ttu-id="cf9b7-109">有关度量挖掘模型准确性的方法的常规信息，请参阅[提升图（Analysis Services - 数据挖掘）](data-mining/lift-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-109">For general information about methods of measuring the accuracy of a mining model, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf9b7-110">选项</span><span class="sxs-lookup"><span data-stu-id="cf9b7-110">Options</span></span>  
 <span data-ttu-id="cf9b7-111">**图表类型**</span><span class="sxs-lookup"><span data-stu-id="cf9b7-111">**Chart Type**</span></span>  
 <span data-ttu-id="cf9b7-112">设置要在查看器中显示的图表的类型。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-112">Sets the type of chart to display in the viewer.</span></span> <span data-ttu-id="cf9b7-113">您可以选择 **“提升图”** 或 **“利润图”**。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-113">You can select either **Lift Chart** or **Profit Chart**.</span></span>  
  
 <span data-ttu-id="cf9b7-114">**设置**</span><span class="sxs-lookup"><span data-stu-id="cf9b7-114">**Settings**</span></span>  
 <span data-ttu-id="cf9b7-115">打开“利润图设置”对话框，可以使用该对话框来配置利润图。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="cf9b7-115">Opens the **Profit Chart Settings** dialog box, which you can use to configure a profit chart.</span></span>  
  
 <span data-ttu-id="cf9b7-116">如果在 **“列映射”** 选项卡中选择了连续的可预测列，则利润图不可用。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-116">The profit chart is not available if a continuous predictable column was selected in the **Column Mapping** tab.</span></span>  
  
 <span data-ttu-id="cf9b7-117">**复制**</span><span class="sxs-lookup"><span data-stu-id="cf9b7-117">**Copy**</span></span>  
 <span data-ttu-id="cf9b7-118">将图表复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="cf9b7-118">Copies the chart to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9b7-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf9b7-119">See Also</span></span>  
 <span data-ttu-id="cf9b7-120">[挖掘准确性图表设计器 &#40;数据挖掘&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="cf9b7-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="cf9b7-121">[测试和验证任务以及操作方法 &#40;数据挖掘&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="cf9b7-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="cf9b7-122">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="cf9b7-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
