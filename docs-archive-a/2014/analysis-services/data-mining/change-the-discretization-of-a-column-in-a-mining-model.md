---
title: 更改挖掘模型中列的离散化 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b20d6428afac5c1492fdc74aafd4d0c010159d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589974"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a><span data-ttu-id="20d1e-102">更改挖掘模型中列的离散化</span><span class="sxs-lookup"><span data-stu-id="20d1e-102">Change the Discretization of a Column in a Mining Model</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="20d1e-103">自动离散化值-也就是说，在某些情况下，它会将数据置于数值列中。</span><span class="sxs-lookup"><span data-stu-id="20d1e-103">automatically discretizes values-that is to say, it bins data in numeric column-in certain scenarios.</span></span> <span data-ttu-id="20d1e-104">例如，如果数据包含连续数值数据，并且创建了决策树模型，则将依据数据的分布，自动将连续数据的所有列都存入 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="20d1e-104">For example, if your data contains continuous numeric data and you create a decision tree model, each column of continuous data will be automatically binned, depending on the distribution of the data.</span></span> <span data-ttu-id="20d1e-105">如果要控制数据的离散化方式，则必须更改挖掘结构列的属性，这些属性可控制数据在模型中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="20d1e-105">If you want to control how the data is discretized, you must change the properties on the mining structure column that control how the data is used in the model.</span></span>  
  
 <span data-ttu-id="20d1e-106">有关如何在挖掘模型中设置属性的常规信息，请参阅 [挖掘模型列](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="20d1e-106">For general information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a><span data-ttu-id="20d1e-107">显示挖掘模型列的属性</span><span class="sxs-lookup"><span data-stu-id="20d1e-107">To display the properties for a mining model column</span></span>  
  
1.  <span data-ttu-id="20d1e-108">在数据挖掘设计器的“挖掘模型”选项卡中，右键单击包含挖掘模型名称的列标题，或者网格中包含挖掘算法名称的行，然后选择“属性”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="20d1e-108">In the **Mining Models** tab in Data Mining Designer, right-click the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="20d1e-109">**“属性”** 窗口将显示与挖掘模型相关联的所有属性。</span><span class="sxs-lookup"><span data-stu-id="20d1e-109">The **Properties** window displays the properties that are associated with the mining model as a whole.</span></span>  
  
2.  <span data-ttu-id="20d1e-110">在靠近屏幕左侧的 **“结构”** 列中，单击包含要离散化的连续数值数据的列。</span><span class="sxs-lookup"><span data-stu-id="20d1e-110">In the **Structure** column near the left side of the screen, click the column that contains the continuous numeric data you want to discretize.</span></span>  
  
     <span data-ttu-id="20d1e-111">**“属性”** 窗口更改为只显示与该列相关联的属性。</span><span class="sxs-lookup"><span data-stu-id="20d1e-111">The **Properties** window changes to display just the properties associated with that column.</span></span>  
  
### <a name="to-change-the-discretization-method"></a><span data-ttu-id="20d1e-112">更改离散化方法</span><span class="sxs-lookup"><span data-stu-id="20d1e-112">To change the discretization method</span></span>  
  
1.  <span data-ttu-id="20d1e-113">在 "**挖掘属性**" 窗口中，单击 "**内容**" 旁的文本框，然后 `Discretized` 从下拉列表中选择。</span><span class="sxs-lookup"><span data-stu-id="20d1e-113">In the **Mining Properties** window, click the text box next to **Content**, and select `Discretized` from the dropdown list.</span></span>  
  
     <span data-ttu-id="20d1e-114"><xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 和 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 属性均处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="20d1e-114">The <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> properties are now enabled.</span></span>  
  
2.  <span data-ttu-id="20d1e-115">在 "**属性**" 窗口中，单击旁边的文本框， <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 然后选择下列值之一： `Automatic` 、 `EqualAreas` 或 `Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="20d1e-115">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> and select one of the following values: `Automatic`, `EqualAreas`, or `Cluster`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="20d1e-116">如果列用法设置为，则 `Ignore` 列的 "**属性**" 窗口为空。</span><span class="sxs-lookup"><span data-stu-id="20d1e-116">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="20d1e-117">在设计器中选择一个不同的元素后，新值即生效。</span><span class="sxs-lookup"><span data-stu-id="20d1e-117">The new value will take effect when you select a different element in the designer.</span></span>  
  
3.  <span data-ttu-id="20d1e-118">在 "**属性**" 窗口中，单击旁边的文本框， <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 然后键入一个数值。</span><span class="sxs-lookup"><span data-stu-id="20d1e-118">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and type a numeric value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="20d1e-119">如果更改这些属性，则必须重新处理该结构以及要对其使用新设置的所有模型。</span><span class="sxs-lookup"><span data-stu-id="20d1e-119">If you change these properties, the structure must be reprocessed, along with any models that you want to use the new setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d1e-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20d1e-120">See Also</span></span>  
 [<span data-ttu-id="20d1e-121">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="20d1e-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
