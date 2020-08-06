---
title: 为模型列创建别名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 908c0a8d8caa810badf4b82dc3dd3f411d09f323
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578522"
---
# <a name="create-an-alias-for-a-model-column"></a><span data-ttu-id="5ef1c-102">为模型列创建别名</span><span class="sxs-lookup"><span data-stu-id="5ef1c-102">Create an Alias for a Model Column</span></span>
  <span data-ttu-id="5ef1c-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，可以为模型列创建别名。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create an alias for a model column.</span></span> <span data-ttu-id="5ef1c-104">当挖掘结构名称太长而不便使用，或者当您需要重命名列以便更清楚地说明其内容或在模型中的用法时，这可能很有用。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-104">This might be useful when the mining structure name is too long to easily work with, or when you want to rename the column to be more descriptive of its contents or usage in the model.</span></span> <span data-ttu-id="5ef1c-105">例如，如果复制一个结构列，然后以不同的方式为特定模型离散化该列，可以重命名该列，以便更准确地反映其内容。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-105">For example, if you make a copy of a structure column and then discretize the column differently for a particular model, you can rename the column to reflect the content more accurately.</span></span>  
  
 <span data-ttu-id="5ef1c-106">若要为模型列创建别名，请使用 **“属性”** 窗格并设置该列的 [“名称”](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) 属性。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-106">To create an alias for a model column, you use the **Properties** pane and set the [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) property of the column.</span></span>  
  
 <span data-ttu-id="5ef1c-107">在数据挖掘设计器的 **“挖掘模型”** 选项卡上，别名显示在列用法标签旁的括号中。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-107">On the **Mining Models** tab of Data Mining Designer, the alias appears enclosed in parentheses next to the column usage label.</span></span>  
  
 <span data-ttu-id="5ef1c-108">有关如何在挖掘模型中设置属性的信息，请参阅 [挖掘模型列](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-108">For information about how to set the properties of a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a><span data-ttu-id="5ef1c-109">为挖掘模型列添加别名</span><span class="sxs-lookup"><span data-stu-id="5ef1c-109">To add an alias to a mining model column</span></span>  
  
1.  <span data-ttu-id="5ef1c-110">在数据挖掘设计器的“挖掘模型”\*\*\*\* 选项卡中，右键单击挖掘模型中与要更改的挖掘列对应的单元，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-110">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the mining model for the mining column that you want to change, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="5ef1c-111">在屏幕右侧的 **“属性”** 窗口中，单击“名称”属性旁的单元格并删除当前值。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-111">In the **Properties** window on the right side of the screen, click the cell next to the Name property and delete the current value.</span></span> <span data-ttu-id="5ef1c-112">为该列键入一个新名称。</span><span class="sxs-lookup"><span data-stu-id="5ef1c-112">Type a new name for the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef1c-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ef1c-113">See Also</span></span>  
 <span data-ttu-id="5ef1c-114">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="5ef1c-114">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="5ef1c-115">挖掘模型属性</span><span class="sxs-lookup"><span data-stu-id="5ef1c-115">Mining Model Properties</span></span>](mining-model-properties.md)  
  
  
