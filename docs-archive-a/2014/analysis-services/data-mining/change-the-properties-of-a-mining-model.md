---
title: 更改挖掘模型的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 395e6a4cb9c0f0dac0f0c717dfe0695033cad050
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577923"
---
# <a name="change-the-properties-of-a-mining-model"></a><span data-ttu-id="c70dc-102">更改挖掘模型的属性</span><span class="sxs-lookup"><span data-stu-id="c70dc-102">Change the Properties of a Mining Model</span></span>
  <span data-ttu-id="c70dc-103">某些挖掘模型属性应用于整个模型，而其他一些模型属性应用于单独的列。</span><span class="sxs-lookup"><span data-stu-id="c70dc-103">Some mining model properties apply to the model as a whole, and other model properties apply to individual columns.</span></span> <span data-ttu-id="c70dc-104">例如，`Drillthrough` 属性就应用于整个模型，它指定事例数据是否应该可用于查询；`Description` 属性也是此类属性。</span><span class="sxs-lookup"><span data-stu-id="c70dc-104">Examples of properties that apply to the entire model would be the `Drillthrough` property, which specifies whether the case data should be available for querying, and the `Description` property.</span></span> <span data-ttu-id="c70dc-105">应用于列的属性包括 `Usage` 和 `ModelingFlags`；它们控制列中的数据在模型内的使用方式。</span><span class="sxs-lookup"><span data-stu-id="c70dc-105">Properties that apply to the column include `Usage` and `ModelingFlags`, which control how data in the column is used within the model.</span></span>  
  
 <span data-ttu-id="c70dc-106">下面的模型属性具有可用于创建表达式或配置复杂模型属性的高级编辑器。</span><span class="sxs-lookup"><span data-stu-id="c70dc-106">The following model properties have advanced editors that you can use to create expressions or configure complex model properties.</span></span> <span data-ttu-id="c70dc-107">以下属性提供：</span><span class="sxs-lookup"><span data-stu-id="c70dc-107">The following properties provide:</span></span>  
  
-   <span data-ttu-id="c70dc-108">`Filter`属性：打开 "[数据集筛选器" 或 "模型筛选器" 对话框](../data-set-filter-or-model-filter-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="c70dc-108">`Filter` property: Opens the [Data Set Filter or Model Filter Dialog Box](../data-set-filter-or-model-filter-dialog-box.md).</span></span>  
  
-   <span data-ttu-id="c70dc-109">`AlgorithmParameters`属性：打开 "[算法参数" 对话框 &#40;挖掘模型 "视图&#41;](../algorithm-parameters-dialog-box-mining-models-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c70dc-109">`AlgorithmParameters` property: Opens the [Algorithm Parameters Dialog Box &#40;Mining Models View&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).</span></span>  
  
 <span data-ttu-id="c70dc-110">有关如何在挖掘模型中设置属性的信息，请参阅 [挖掘模型列](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="c70dc-110">For information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model"></a><span data-ttu-id="c70dc-111">更改挖掘模型的属性</span><span class="sxs-lookup"><span data-stu-id="c70dc-111">To change the properties of a mining model</span></span>  
  
1.  <span data-ttu-id="c70dc-112">在数据挖掘设计器的“挖掘模型”选项卡中，右键单击包含挖掘模型名称的列标题，或者网格中包含挖掘算法名称的行，然后选择“属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c70dc-112">In the **Mining Models** tab in Data Mining Designer, right-click either the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c70dc-113">在屏幕右侧的 **“属性”** 窗口中，突出显示与要更改的属性对应的值，然后输入新的值。</span><span class="sxs-lookup"><span data-stu-id="c70dc-113">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
     <span data-ttu-id="c70dc-114">在设计器中选择一个不同的元素后，新值即生效。</span><span class="sxs-lookup"><span data-stu-id="c70dc-114">The new value will take effect when you select a different element in the designer.</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a><span data-ttu-id="c70dc-115">更改挖掘模型列的属性</span><span class="sxs-lookup"><span data-stu-id="c70dc-115">To change the properties of a mining model column</span></span>  
  
1.  <span data-ttu-id="c70dc-116">在数据挖掘设计器的“挖掘模型”选项卡中，右键单击网格中位于挖掘结构列与挖掘模型的交叉点处的单元格，然后选择“属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c70dc-116">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the grid at the intersection of the mining structure column and the mining model, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c70dc-117">在屏幕右侧的 **“属性”** 窗口中，突出显示与要更改的属性对应的值，然后输入新的值。</span><span class="sxs-lookup"><span data-stu-id="c70dc-117">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c70dc-118">如果列用法设置为，则 `Ignore` 列的 "**属性**" 窗口为空。</span><span class="sxs-lookup"><span data-stu-id="c70dc-118">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="c70dc-119">在设计器中选择一个不同的元素后，新值即生效。</span><span class="sxs-lookup"><span data-stu-id="c70dc-119">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70dc-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c70dc-120">See Also</span></span>  
 [<span data-ttu-id="c70dc-121">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="c70dc-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
