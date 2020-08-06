---
title: 向现有挖掘结构中添加挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], adding
- mining structures [Analysis Services], mining models
- adding mining models
ms.assetid: fcf72300-0674-4e73-a826-9b8eeffefbb5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0afdf5f795303eaa8bb672aa80e68e0f1f891607
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588765"
---
# <a name="add-a-mining-model-to-an-existing-mining-structure"></a><span data-ttu-id="0ddac-102">在现有挖掘结构中添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="0ddac-102">Add a Mining Model to an Existing Mining Structure</span></span>
  <span data-ttu-id="0ddac-103">在添加初始模型后，可以将更多挖掘模型添加到挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="0ddac-103">You can add more mining models to a mining structure, after you add the initial model.</span></span> <span data-ttu-id="0ddac-104">每个模型必须包含在结构中存在的列，但您可以为每个挖掘模型定义不同的列用法。</span><span class="sxs-lookup"><span data-stu-id="0ddac-104">Each model must contain columns that exist in the structure, but you can define the usage of the columns differently for each mining model.</span></span> <span data-ttu-id="0ddac-105">有关如何定义挖掘模型列的详细信息，请参阅 [挖掘模型列](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="0ddac-105">For more information about how to define mining models columns, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-a-mining-model-to-the-structure"></a><span data-ttu-id="0ddac-106">在结构中添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="0ddac-106">To add a mining model to the structure</span></span>  
  
1.  <span data-ttu-id="0ddac-107">在 **中的** “挖掘模型” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]菜单项中，选择 **“新建挖掘模型”**。</span><span class="sxs-lookup"><span data-stu-id="0ddac-107">From the **Mining Model** menu item in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select **New Mining Model**.</span></span>  
  
     <span data-ttu-id="0ddac-108">此时将打开 **“新建挖掘模型”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0ddac-108">The **New Mining Model** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="0ddac-109">在 **“模型名称”** 下面，输入新挖掘模型的名称。</span><span class="sxs-lookup"><span data-stu-id="0ddac-109">Under **Model name**, enter a name for the new mining model.</span></span>  
  
3.  <span data-ttu-id="0ddac-110">在 **“算法名称”** 下面，选择将用来生成挖掘模型的算法。</span><span class="sxs-lookup"><span data-stu-id="0ddac-110">Under **Algorithm name**, select the algorithm that the mining model will be built from.</span></span>  
  
4.  <span data-ttu-id="0ddac-111">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="0ddac-111">Click **OK**.</span></span>  
  
 <span data-ttu-id="0ddac-112">新的挖掘模型将显示在 "**挖掘模型**" 选项卡中。模型使用结构中存在的默认列。</span><span class="sxs-lookup"><span data-stu-id="0ddac-112">A new mining model appears in the **Mining Models** tab. The model uses the default columns that exist in the structure.</span></span> <span data-ttu-id="0ddac-113">有关如何修改列的信息，请参阅 [更改挖掘模型的属性](change-the-properties-of-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="0ddac-113">For information about how to modify the columns, see [Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddac-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ddac-114">See Also</span></span>  
 [<span data-ttu-id="0ddac-115">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="0ddac-115">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
