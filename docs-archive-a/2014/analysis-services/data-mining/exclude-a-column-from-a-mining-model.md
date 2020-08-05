---
title: 从挖掘模型中排除列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30affebc143184c6287858f60b5d4f5d089c322a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580467"
---
# <a name="exclude-a-column-from-a-mining-model"></a><span data-ttu-id="4c2be-102">从挖掘模型中排除列</span><span class="sxs-lookup"><span data-stu-id="4c2be-102">Exclude a Column from a Mining Model</span></span>
  <span data-ttu-id="4c2be-103">在创建新的挖掘模型时，您可能不希望使用模型基于的挖掘结构中存在的所有列。</span><span class="sxs-lookup"><span data-stu-id="4c2be-103">When you create a new mining model, you may not want to use all the columns that exist in the mining structure on which the model is based.</span></span> <span data-ttu-id="4c2be-104">例如，您可能已为钻取添加了一个客户名称列，但不希望将其用于建模。</span><span class="sxs-lookup"><span data-stu-id="4c2be-104">For example, you might have added a customer name column for drillthrough, but don't want to use it for modeling.</span></span> <span data-ttu-id="4c2be-105">或者，您可能决定为一个列创建具有不同离散化的多个副本，并且在每个模型中仅使用这些副本中的一个，而忽略其余副本。</span><span class="sxs-lookup"><span data-stu-id="4c2be-105">Or, you might decide to create multiple copies of a column with different discretizations, and use only one of the copies in each model, and ignore the rest.</span></span> <span data-ttu-id="4c2be-106">您还可以有选择地在若干不同模型中添加输入列，看看所添加的变量是如何影响输出列的。</span><span class="sxs-lookup"><span data-stu-id="4c2be-106">You could also selectively add input columns in several different models to see how the added variable affects the output column.</span></span>  
  
 <span data-ttu-id="4c2be-107">您不需要为每个列组合都创建新的挖掘结构；相反，您只需将某个列标记为不在特定的模型中使用。</span><span class="sxs-lookup"><span data-stu-id="4c2be-107">You do not need to create a new mining structure for each combination of columns; instead, you can simply flag a column as not being used in a particular model.</span></span>  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a><span data-ttu-id="4c2be-108">从挖掘模型中排除列</span><span class="sxs-lookup"><span data-stu-id="4c2be-108">To exclude a column from a mining model</span></span>  
  
1.  <span data-ttu-id="4c2be-109">在 **中的数据挖掘设计器的** “挖掘模型” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡中，在有关的挖掘模型下，选择与要排除的列相对应的单元。</span><span class="sxs-lookup"><span data-stu-id="4c2be-109">In the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the cell that corresponds to the column you want to exclude, under the appropriate mining model.</span></span>  
  
2.  <span data-ttu-id="4c2be-110">从下拉列表框中选择“忽略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c2be-110">Select **Ignore** from the drop-down list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2be-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c2be-111">See Also</span></span>  
 [<span data-ttu-id="4c2be-112">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="4c2be-112">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
