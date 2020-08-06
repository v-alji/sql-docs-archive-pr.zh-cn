---
title: 挖掘模型任务和操作指南 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- mining models [Analysis Services], how-to topics
ms.assetid: 7c2073e5-b40f-4bf8-aa51-021adb08e072
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3648e8e47cc1954eaf8bca1e3608e9abbdf82b02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589351"
---
# <a name="mining-model-tasks-and-how-tos"></a><span data-ttu-id="7367e-102">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="7367e-102">Mining Model Tasks and How-tos</span></span>
  <span data-ttu-id="7367e-103">可以使用 **中的数据挖掘设计器的** “挖掘模型” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 选项卡，管理和处理挖掘结构中的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7367e-103">Use the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to manage and process mining models in a mining structure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7367e-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="7367e-104">In This Section</span></span>  
  
-   [<span data-ttu-id="7367e-105">在现有挖掘结构中添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7367e-105">Add a Mining Model to an Existing Mining Structure</span></span>](add-a-mining-model-to-an-existing-mining-structure.md)  
  
-   [<span data-ttu-id="7367e-106">从挖掘结构中删除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7367e-106">Delete a Mining Model from a Mining Structure</span></span>](delete-a-mining-model-from-a-mining-structure.md)  
  
-   [<span data-ttu-id="7367e-107">从挖掘模型中排除列</span><span class="sxs-lookup"><span data-stu-id="7367e-107">Exclude a Column from a Mining Model</span></span>](exclude-a-column-from-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-108">为模型列创建别名</span><span class="sxs-lookup"><span data-stu-id="7367e-108">Create an Alias for a Model Column</span></span>](create-an-alias-for-a-model-column.md)  
  
-   [<span data-ttu-id="7367e-109">更改挖掘模型中列的离散化</span><span class="sxs-lookup"><span data-stu-id="7367e-109">Change the Discretization of a Column in a Mining Model</span></span>](change-the-discretization-of-a-column-in-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-110">查看或更改建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="7367e-110">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
-   [<span data-ttu-id="7367e-111">在模型中指定用作回归量的列</span><span class="sxs-lookup"><span data-stu-id="7367e-111">Specify a Column to Use as Regressor in a Model</span></span>](specify-a-column-to-use-as-regressor-in-a-model.md)  
  
-   [<span data-ttu-id="7367e-112">更改挖掘模型的属性</span><span class="sxs-lookup"><span data-stu-id="7367e-112">Change the Properties of a Mining Model</span></span>](change-the-properties-of-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-113">对挖掘模型应用筛选器</span><span class="sxs-lookup"><span data-stu-id="7367e-113">Apply a Filter to a Mining Model</span></span>](apply-a-filter-to-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-114">从挖掘模型中删除筛选器</span><span class="sxs-lookup"><span data-stu-id="7367e-114">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-115">对挖掘模型启用钻取</span><span class="sxs-lookup"><span data-stu-id="7367e-115">Enable Drillthrough for a Mining Model</span></span>](enable-drillthrough-for-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-116">查看或更改算法参数</span><span class="sxs-lookup"><span data-stu-id="7367e-116">View or Change Algorithm Parameters</span></span>](view-or-change-algorithm-parameters.md)  
  
-   [<span data-ttu-id="7367e-117">生成挖掘模型的副本</span><span class="sxs-lookup"><span data-stu-id="7367e-117">Make a Copy of a Mining Model</span></span>](make-a-copy-of-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-118">处理挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7367e-118">Process a Mining Model</span></span>](process-a-mining-model.md)  
  
-   [<span data-ttu-id="7367e-119">创建数据挖掘维度</span><span class="sxs-lookup"><span data-stu-id="7367e-119">Create a Data Mining Dimension</span></span>](create-a-data-mining-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="7367e-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7367e-120">See Also</span></span>  
 <span data-ttu-id="7367e-121">[挖掘结构任务和操作指南](mining-structure-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7367e-121">[Mining Structure Tasks and How-tos](mining-structure-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="7367e-122">[挖掘模型 &#40;Analysis Services 数据挖掘&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7367e-122">[Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="7367e-123">数据挖掘概念</span><span class="sxs-lookup"><span data-stu-id="7367e-123">Data Mining Concepts</span></span>](data-mining-concepts.md)  
  
  
