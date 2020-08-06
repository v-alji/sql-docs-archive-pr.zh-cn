---
title: 使用 Microsoft 一般内容树查看器浏览模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
ms.assetid: 4a5f7c51-c704-4214-b05d-21cf735e6d96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90d47262a09060a11020e50b3724753799d2d188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591023"
---
# <a name="browse-a-model-using-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="49321-102">使用 Microsoft 一般内容树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="49321-102">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>
  <span data-ttu-id="49321-103">通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般挖掘模型内容查看器，可以查看有关挖掘算法找到的模式的详细信息，以及访问在分析过程中生成的各种统计信息。</span><span class="sxs-lookup"><span data-stu-id="49321-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Mining Model Content Viewer provides detailed information about the patterns found by the mining algorithm, and also provides access to various statistics generated during the analysis process.</span></span> <span data-ttu-id="49321-104">信息的数量和类型取决于使用的算法，但可包括以下几类：</span><span class="sxs-lookup"><span data-stu-id="49321-104">The amount and type of information depends on the algorithm that was used, but can include the following categories:</span></span>  
  
-   <span data-ttu-id="49321-105">数据段及其特征。</span><span class="sxs-lookup"><span data-stu-id="49321-105">Segments of data, and their characteristics.</span></span>  
  
-   <span data-ttu-id="49321-106">有关每个组或整个数据集的说明性统计信息。</span><span class="sxs-lookup"><span data-stu-id="49321-106">Descriptive statistics about each group or about the whole set of data.</span></span>  
  
-   <span data-ttu-id="49321-107">树中的分支或子节点的数目。</span><span class="sxs-lookup"><span data-stu-id="49321-107">The number of branches or child nodes in a tree.</span></span>  
  
-   <span data-ttu-id="49321-108">对群集或整个数据集的计算，例如方差和平均值。</span><span class="sxs-lookup"><span data-stu-id="49321-108">Calculations, such as variance and mean, for a cluster or a whole set of data.</span></span>  
  
 <span data-ttu-id="49321-109">查看这些信息可帮助您更好地理解分析结果。</span><span class="sxs-lookup"><span data-stu-id="49321-109">Viewing this information can help you better understand the results of your analysis.</span></span> <span data-ttu-id="49321-110">此外，您还可确定微调模型继而为模型重新定型的方法，</span><span class="sxs-lookup"><span data-stu-id="49321-110">You can also identify ways to fine-tune, and then retrain, your model.</span></span> <span data-ttu-id="49321-111">或者，您可决定使用其他算法重新定型。</span><span class="sxs-lookup"><span data-stu-id="49321-111">Or, you might decide to retrain by using a different algorithm.</span></span>  
  
## <a name="viewing-mining-model-content"></a><span data-ttu-id="49321-112">查看挖掘模型内容</span><span class="sxs-lookup"><span data-stu-id="49321-112">Viewing Mining Model Content</span></span>  
 <span data-ttu-id="49321-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容查看器显示挖掘模型的“内容架构行集” \*\* 中的列、规则、属性、特性、节点和其他内容。</span><span class="sxs-lookup"><span data-stu-id="49321-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Viewer displays the columns, rules, properties, attributes, nodes, and other content from the *content schema rowset* of the mining model.</span></span> <span data-ttu-id="49321-114">内容架构行集是用于呈现数据挖掘模型内容详细信息的通用框架。</span><span class="sxs-lookup"><span data-stu-id="49321-114">The content schema rowset is a generic framework for presenting detailed information about the content of a data mining model.</span></span>  
  
 <span data-ttu-id="49321-115">此详细信息包含在一个 HTML 表中，该表将模型中的模式、群集或树表示为节点。</span><span class="sxs-lookup"><span data-stu-id="49321-115">This detailed information is contained in an HTML table that represents the patterns, clusters, or trees in the model as nodes.</span></span> <span data-ttu-id="49321-116">您可以单击各节点，然后将其展开以便查看详细信息，例如针对数值属性的不同值的公式或计数。</span><span class="sxs-lookup"><span data-stu-id="49321-116">You can click on each node and expand it to see more detail, such as the formulas or the count of distinct values for a numeric attribute.</span></span> <span data-ttu-id="49321-117">您也可以浏览节点中的父子关系。</span><span class="sxs-lookup"><span data-stu-id="49321-117">You can also explore the child-parent relationships among the nodes.</span></span>  
  
 <span data-ttu-id="49321-118">有关挖掘模型内容中所用术语的常规含义的详细信息，请参阅[挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="49321-118">For more information about the general meaning of the terms used in the mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span> <span data-ttu-id="49321-119">本主题还包括指向特定类型模型的挖掘模型内容信息的链接。</span><span class="sxs-lookup"><span data-stu-id="49321-119">The topic also contains links to information about mining model content for specific types of models.</span></span> <span data-ttu-id="49321-120">每种挖掘模型包含的信息都是高度特定于数据中的算法和模式的，因此，我们建议您查阅每个模型类型的技术参考主题以全面了解各模型类型。</span><span class="sxs-lookup"><span data-stu-id="49321-120">Each type of mining model contains information that is highly specific to the algorithm and the patterns found in the data, so we recommend that you consult the technical reference topic for each model type in order to fully understand each model type.</span></span>  
  
## <a name="querying-mining-model-content"></a><span data-ttu-id="49321-121">查询挖掘模型内容</span><span class="sxs-lookup"><span data-stu-id="49321-121">Querying Mining Model Content</span></span>  
 <span data-ttu-id="49321-122">通过查询挖掘模型，同样可以获取 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器提供的信息。</span><span class="sxs-lookup"><span data-stu-id="49321-122">The same information that is provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer is also available by querying the mining model.</span></span> <span data-ttu-id="49321-123">可以使用数据挖掘扩展插件 (DMX) 语句来创建针对挖掘模型内容的查询。</span><span class="sxs-lookup"><span data-stu-id="49321-123">You can create queries against mining model content by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="49321-124">例如，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，可通过执行以下 DMX 语句来运行内容查询。</span><span class="sxs-lookup"><span data-stu-id="49321-124">For example, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can run a content query by executing the following DMX statement:</span></span>  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 <span data-ttu-id="49321-125">有关详细信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="49321-125">For more information, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49321-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49321-126">See Also</span></span>  
 <span data-ttu-id="49321-127">[Microsoft 一般内容树查看器 &#40;数据挖掘&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="49321-127">[Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span></span>  
 [<span data-ttu-id="49321-128">数据挖掘算法（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="49321-128">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
  
