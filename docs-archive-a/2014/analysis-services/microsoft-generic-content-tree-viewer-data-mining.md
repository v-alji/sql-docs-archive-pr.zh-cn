---
title: Microsoft 一般内容树查看器 (数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0dab06d6af8f2c5af029d9ce831f518faa4067e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693136"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a><span data-ttu-id="724dd-102">Microsoft 一般内容树查看器（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="724dd-102">Microsoft Generic Content Tree Viewer (Data Mining)</span></span>
  <span data-ttu-id="724dd-103">**“Microsoft 一般内容树查看器”** 以标准化 HTML 表格式显示有关数据挖掘模式的内容的详细信息。</span><span class="sxs-lookup"><span data-stu-id="724dd-103">The **Microsoft Generic Content Tree Viewer** displays detailed information about the contents of a data mining mode in a standardized HTML table format.</span></span> <span data-ttu-id="724dd-104">此视图很有用，因为它将公开模型的基础结构，以及有关系数、值的分布等项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="724dd-104">This view is useful because it exposes the underlying structure of the model, as well details about coefficients, the distribution of values, and much more.</span></span>  
  
 <span data-ttu-id="724dd-105">表中显示的实际内容因使用的算法而异，可能包括列、规则、属性、特性、节点和公式。</span><span class="sxs-lookup"><span data-stu-id="724dd-105">The actual content displayed in the table varies depending on the algorithm that was used and might include columns, rules, properties, attributes, nodes, and formulas.</span></span> <span data-ttu-id="724dd-106">有关模型内容以及如何解释每个模型类型信息的详细信息，请参阅[挖掘模型内容（Analysis Services - 数据挖掘）](data-mining/mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="724dd-106">For more information about model content, and how to interpret the information for each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="724dd-107">此查看器中显示的信息使用基于挖掘模型的内容架构行集的通用结构。</span><span class="sxs-lookup"><span data-stu-id="724dd-107">The information that is displayed in the viewer uses a common structure that is based on the content schema rowset for mining models.</span></span> <span data-ttu-id="724dd-108">内容架构行集是用于存储数据挖掘模型的模式、统计信息和其他内容的通用框架。</span><span class="sxs-lookup"><span data-stu-id="724dd-108">The content schema rowset is a generic framework for storing patterns, statistics, and other contents of a data mining model.</span></span> <span data-ttu-id="724dd-109">有关挖掘模型的数据挖掘架构行集中的列的列表，请参阅 [DMSCHEMA_MINING_MODEL_CONTENT 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)。</span><span class="sxs-lookup"><span data-stu-id="724dd-109">For a list of the columns in the data mining schema rowset for mining models, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
## <a name="options"></a><span data-ttu-id="724dd-110">选项</span><span class="sxs-lookup"><span data-stu-id="724dd-110">Options</span></span>  
 <span data-ttu-id="724dd-111">**节点标题(唯一 ID)**</span><span class="sxs-lookup"><span data-stu-id="724dd-111">**Node caption (Unique ID)**</span></span>  
 <span data-ttu-id="724dd-112">此窗格显示所选挖掘模型中所有节点的列表。</span><span class="sxs-lookup"><span data-stu-id="724dd-112">This pane displays a list of all the nodes in the selected mining model.</span></span> <span data-ttu-id="724dd-113">节点在树中的排列方式随要查看的模型类型的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="724dd-113">The way the nodes are arranged in the tree is different depending on the type of model you are viewing.</span></span>  
  
 <span data-ttu-id="724dd-114">可以单击每个节点，在 **“节点详细信息”** 窗格中显示有关该节点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="724dd-114">You can click each node to display details about the node in the **Node details** pane.</span></span>  
  
 <span data-ttu-id="724dd-115">**“节点详细信息”**</span><span class="sxs-lookup"><span data-stu-id="724dd-115">**Node details**</span></span>  
 <span data-ttu-id="724dd-116">显示选定节点的内容的详细信息。</span><span class="sxs-lookup"><span data-stu-id="724dd-116">Displays detailed information about the content of the selected node.</span></span> <span data-ttu-id="724dd-117">每个节点均以标准化格式存储其信息，但表中每个行的内容和基数取决于要查看的模型类型或节点类型。</span><span class="sxs-lookup"><span data-stu-id="724dd-117">Each node stores its information in a standardized format, but the contents and significance of each line of the table depends on the type of model or type of node that you are viewing.</span></span> <span data-ttu-id="724dd-118">例如，为表示关联模型中的规则的节点存储的信息不同于表示决策树模型中的树的节点中的信息。</span><span class="sxs-lookup"><span data-stu-id="724dd-118">For example, the information stored for a node that represents a rule in an association model contains different information than a node that represents a tree in a decision trees model.</span></span>  
  
 <span data-ttu-id="724dd-119">有关如何解释特定模型类型的节点信息的信息，请参阅[挖掘模型内容（Analysis Services - 数据挖掘）](data-mining/mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="724dd-119">For information about how to interpret the node information for a specific model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724dd-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="724dd-120">See Also</span></span>  
 <span data-ttu-id="724dd-121">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="724dd-121">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="724dd-122">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="724dd-122">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="724dd-123">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="724dd-123">Data Mining Queries</span></span>](data-mining/data-mining-queries.md)  
  
  
