---
title: 查看或更改算法参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- mining models [Analysis Services], algorithms
ms.assetid: 151b899b-c27a-4a09-bcf5-5c9f0ec24168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30719cd50e0c473cf2aab5d9689d27dff4f26343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581013"
---
# <a name="view-or-change-algorithm-parameters"></a><span data-ttu-id="efd61-102">查看或更改算法参数</span><span class="sxs-lookup"><span data-stu-id="efd61-102">View or Change Algorithm Parameters</span></span>
  <span data-ttu-id="efd61-103">可以更改随用于生成数据挖掘模型的算法一起提供的参数，以自定义模型的结果。</span><span class="sxs-lookup"><span data-stu-id="efd61-103">You can change the parameters provided with the algorithms that you use to build data mining models to customize the results of the model.</span></span>  
  
 <span data-ttu-id="efd61-104">更改中提供的算法参数不仅仅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 是模型的属性，它们可用于从根本上更改处理、分组和显示数据的方式。</span><span class="sxs-lookup"><span data-stu-id="efd61-104">The algorithm parameters provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] change much more than just properties on the model: they can be used to fundamentally alter the way that data is processed, grouped, and displayed.</span></span> <span data-ttu-id="efd61-105">例如，您可以使用算法参数执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="efd61-105">For example, you can use algorithm parameters to do the following:</span></span>  
  
-   <span data-ttu-id="efd61-106">更改分析方法，如聚类分析方法。</span><span class="sxs-lookup"><span data-stu-id="efd61-106">Change the method of analysis, such as the clustering method.</span></span>  
  
-   <span data-ttu-id="efd61-107">控制功能选择行为。</span><span class="sxs-lookup"><span data-stu-id="efd61-107">Control feature selection behavior.</span></span>  
  
-   <span data-ttu-id="efd61-108">指定项集的大小或规则的概率。</span><span class="sxs-lookup"><span data-stu-id="efd61-108">Specify the size of itemsets or the probability of rules.</span></span>  
  
-   <span data-ttu-id="efd61-109">控制决策树的分支和深度。</span><span class="sxs-lookup"><span data-stu-id="efd61-109">Control branching and depth of decision trees.</span></span>  
  
-   <span data-ttu-id="efd61-110">指定种子值或用于模型创建的内部维持集的大小。</span><span class="sxs-lookup"><span data-stu-id="efd61-110">Specify a seed value or the size of the internal holdout set used for model creation.</span></span>  
  
 <span data-ttu-id="efd61-111">为每个算法提供的参数变动很大；有关可以为每个算法设置的参数列表，请参阅本节中的技术参考主题：[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="efd61-111">The parameters provided for each algorithm vary greatly; for a list of the parameters that you can set for each algorithm, see the technical reference topics in this section: [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="change-an-algorithm-parameter"></a><span data-ttu-id="efd61-112">更改算法参数</span><span class="sxs-lookup"><span data-stu-id="efd61-112">Change an algorithm parameter</span></span>  
  
1.  <span data-ttu-id="efd61-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的数据挖掘设计器的“挖掘模型”\*\*\*\* 选项卡中，右键单击要为其优化算法的挖掘模型的算法类型，选择“设置算法参数”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="efd61-113">On the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the algorithm type of the mining model for which you want to tune the algorithm, and select **Set Algorithm Parameters**.</span></span>  
  
     <span data-ttu-id="efd61-114">此时将打开 **“算法参数”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="efd61-114">The **Algorithm Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="efd61-115">在 **“值”** 列中，为要更改的算法设置新值。</span><span class="sxs-lookup"><span data-stu-id="efd61-115">In the **Value** column, set a new value for the algorithm that you want to change.</span></span>  
  
     <span data-ttu-id="efd61-116">如果未在 **“值”** 列中输入值， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将使用默认参数值。</span><span class="sxs-lookup"><span data-stu-id="efd61-116">If you do not enter a value in the **Value** column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the default parameter value.</span></span> <span data-ttu-id="efd61-117">**“范围”** 列说明了您可以输入的可能值。</span><span class="sxs-lookup"><span data-stu-id="efd61-117">The **Range** column describes the possible values that you can enter.</span></span>  
  
3.  <span data-ttu-id="efd61-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="efd61-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="efd61-119">此时，算法参数被设置为新值。</span><span class="sxs-lookup"><span data-stu-id="efd61-119">The algorithm parameter is set with the new value.</span></span> <span data-ttu-id="efd61-120">重新处理挖掘模型后，参数更改才反映在该模型中。</span><span class="sxs-lookup"><span data-stu-id="efd61-120">The parameter change will not be reflected in the mining model until you reprocess the model.</span></span>  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a><span data-ttu-id="efd61-121">查看现有模型中使用的参数</span><span class="sxs-lookup"><span data-stu-id="efd61-121">View the parameters used in an existing model</span></span>  
  
1.  <span data-ttu-id="efd61-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开一个 DMX 查询窗口。</span><span class="sxs-lookup"><span data-stu-id="efd61-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window.</span></span>  
  
2.  <span data-ttu-id="efd61-123">按如下所示键入查询：</span><span class="sxs-lookup"><span data-stu-id="efd61-123">Type a query like this one:</span></span>  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="efd61-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efd61-124">See Also</span></span>  
 [<span data-ttu-id="efd61-125">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="efd61-125">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
