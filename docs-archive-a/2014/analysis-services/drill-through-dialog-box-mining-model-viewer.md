---
title: "\"钻取\" 对话框 (挖掘模型查看器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b00c62017de5a26c4507a04aeaf59aba7522146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589946"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a><span data-ttu-id="4dd1b-102">“钻取”对话框（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="4dd1b-102">Drill Through Dialog Box (Mining Model Viewer)</span></span>
  <span data-ttu-id="4dd1b-103">在使用数据挖掘设计器的 **“挖掘模型查看器”** 选项卡查看挖掘模型时，可以钻取到有关事例数据的详细信息（假定模型已启用钻取功能）。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-103">When you view a mining model by using the **Mining Model Viewer** tab of Data Mining Designer, you can drill through into details about the case data, provided the model has drillthrough enabled.</span></span> <span data-ttu-id="4dd1b-104">而且，如果基础挖掘结构已启用钻取功能，则还可以查看挖掘结构中的列，即使挖掘模型中没有包含这些列也是如此。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-104">Moreover, if the underlying mining structure has drillthrough enabled, you can also see columns in the mining structure, even if those columns were not included in the mining model.</span></span> <span data-ttu-id="4dd1b-105">在列列表中，结构列的前缀为标签</span><span class="sxs-lookup"><span data-stu-id="4dd1b-105">In the column list, the structure columns are prefixed by the "Structure."</span></span> <span data-ttu-id="4dd1b-106">“Structure”。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-106">label.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4dd1b-107">您不能对现有的挖掘结构启用钻取功能，</span><span class="sxs-lookup"><span data-stu-id="4dd1b-107">You cannot enable drillthrough on an existing mining structure.</span></span> <span data-ttu-id="4dd1b-108">而必须重新创建挖掘结构并在创建过程中启用钻取功能。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-108">Instead, you must re-create the mining structure and enable drillthrough during the creation process.</span></span>  
  
 <span data-ttu-id="4dd1b-109">有关如何从每个支持钻取的挖掘模型查看器访问事例数据的信息，**请参阅**[从挖掘模型钻取到事例数据](data-mining/drill-through-to-case-data-from-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-109">For information about how to access case data from each of the mining model viewers that support drillthrough, **see** [Drill Through to Case Data from a Mining Model](data-mining/drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4dd1b-110">选项</span><span class="sxs-lookup"><span data-stu-id="4dd1b-110">Options</span></span>  
 <span data-ttu-id="4dd1b-111">**事例分类为**</span><span class="sxs-lookup"><span data-stu-id="4dd1b-111">**Cases Classified To**</span></span>  
 <span data-ttu-id="4dd1b-112">显示在选定的节点中包含的规则、项集和分类的定义。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-112">Displays the definition of the rule, itemset, and cluster that are contained in the selected node.</span></span>  
  
 <span data-ttu-id="4dd1b-113">**列列表**</span><span class="sxs-lookup"><span data-stu-id="4dd1b-113">**Column list**</span></span>  
 <span data-ttu-id="4dd1b-114">显示模型中的列，后面跟随结构列。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-114">Displays the columns in the model, followed by the structure columns.</span></span>  
  
 <span data-ttu-id="4dd1b-115">**注意** 仅当对挖掘结构启用了钻取功能并且选中选项 **“模型和结构列”** 时才会显示结构列。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-115">**Note** Structure columns are displayed only if drillthrough is enabled on the mining structure, and if you selected the option, **Model and Structure Columns**.</span></span> <span data-ttu-id="4dd1b-116">此外，您还必须具有对要查看列的挖掘模型和挖掘结构的钻取权限。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-116">Moreover, you must have drillthrough permissions on both the mining model and the mining structure to view the columns.</span></span>  
  
 <span data-ttu-id="4dd1b-117">未包含在模型中的结构列显示为 "**结构" \<column name> 。**</span><span class="sxs-lookup"><span data-stu-id="4dd1b-117">Structure columns that are not included in the model appear as **Structure.\<column name>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4dd1b-118">可在列网格中右键单击任意位置，并选择“全部复制”\*\*\*\*，以将钻取数据以制表符分隔的格式复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-118">You can right-click anywhere in the column grid and select **Copy All** to copy the drillthrough data, in tab-delimited format, to the Clipboard.</span></span> <span data-ttu-id="4dd1b-119">复制的数据只包含事例数据，而不包含节点定义。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-119">The copied data includes only the case data, not the node definition.</span></span>  
  
 <span data-ttu-id="4dd1b-120">**显示**</span><span class="sxs-lookup"><span data-stu-id="4dd1b-120">**Play**</span></span>  
 <span data-ttu-id="4dd1b-121">单击绿色箭头按钮刷新数据。</span><span class="sxs-lookup"><span data-stu-id="4dd1b-121">Click the green arrow button to refresh the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd1b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4dd1b-122">See Also</span></span>  
 <span data-ttu-id="4dd1b-123">[数据挖掘 &#40;钻取查询&#41;](data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4dd1b-123">[Drillthrough Queries &#40;Data Mining&#41;](data-mining/drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="4dd1b-124">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="4dd1b-124">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="4dd1b-125">挖掘模型查看器任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="4dd1b-125">Mining Model Viewer Tasks and How-tos</span></span>](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
