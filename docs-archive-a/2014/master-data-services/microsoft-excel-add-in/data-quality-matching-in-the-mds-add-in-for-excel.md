---
title: MDS Add-in for Excel 中的数据质量匹配 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 037e535452e7f19644837e0cbcfd02efec5422b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589735"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a><span data-ttu-id="547a4-102">用于 Excel 的 MDS 外接程序中的数据质量匹配</span><span class="sxs-lookup"><span data-stu-id="547a4-102">Data Quality Matching in the MDS Add-in for Excel</span></span>
  <span data-ttu-id="547a4-103">随着时间的推移，您将会想要向 MDS 存储库中添加更多的数据。</span><span class="sxs-lookup"><span data-stu-id="547a4-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="547a4-104">在添加数据前，将新数据与已在 MDS 中进行管理的数据进行比较可能会很有用，因为这样可以确保不会添加重复数据或不正确的数据。</span><span class="sxs-lookup"><span data-stu-id="547a4-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure you are not adding duplicate or inaccurate data.</span></span>  
  
 <span data-ttu-id="547a4-105">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Data Quality Services (DQS) 功能来匹配相似的数据。</span><span class="sxs-lookup"><span data-stu-id="547a4-105">The MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] uses the Data Quality Services (DQS) feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to match data that's similar.</span></span> <span data-ttu-id="547a4-106">当您在该外接程序中使用此匹配功能时，相似的记录将组合在一起，并且显示表示结果精确性的得分。</span><span class="sxs-lookup"><span data-stu-id="547a4-106">When you use the matching functionality in the Add-in, similar records are grouped together and a score that represents the accuracy of the result is displayed.</span></span> <span data-ttu-id="547a4-107">有关 DQS 提供的匹配功能的详细信息，请参阅 [Data Matching](../../data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="547a4-107">For more information about the matching functionality provided by DQS, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
## <a name="workflow-for-data-quality-matching"></a><span data-ttu-id="547a4-108">用于数据质量匹配的工作流</span><span class="sxs-lookup"><span data-stu-id="547a4-108">Workflow for Data Quality Matching</span></span>  
 <span data-ttu-id="547a4-109">在将 DQS 用于 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]时，使用以下工作流：</span><span class="sxs-lookup"><span data-stu-id="547a4-109">When using DQS with the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use the following workflow:</span></span>  
  
1.  <span data-ttu-id="547a4-110">检索 MDS 管理的数据的列表并将其与未在 MDS 中管理的列表合并。</span><span class="sxs-lookup"><span data-stu-id="547a4-110">Retrieve a list of MDS-managed data and combine it with a list that is not managed in MDS.</span></span> <span data-ttu-id="547a4-111">有关详细信息，请参阅 [合并数据（用于 Excel 的 MDS 外接程序）](combine-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="547a4-111">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="547a4-112">使用 DQS 知识可以比较合并的列表中的数据。</span><span class="sxs-lookup"><span data-stu-id="547a4-112">Use DQS knowledge to compare the data in the combined list.</span></span> <span data-ttu-id="547a4-113">有关详细信息，请参阅 [匹配相似数据（用于 Excel 的 MDS 外接程序）](match-similar-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="547a4-113">For more information, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
3.  <span data-ttu-id="547a4-114">若要查看与 DQS 发现的相似性有关的详细信息，请显示详细信息列。</span><span class="sxs-lookup"><span data-stu-id="547a4-114">To view more details about the similarities found by DQS, show the detail columns.</span></span>  
  
4.  <span data-ttu-id="547a4-115">浏览结果并且确定哪些数据应该添加到 MDS 存储库中以及哪些数据是重复的。</span><span class="sxs-lookup"><span data-stu-id="547a4-115">Go through the results and determine which data should be added to the MDS repository and which data is duplicated.</span></span>  
  
5.  <span data-ttu-id="547a4-116">将新的和/或已更新的数据发布到 MDS 存储库中。</span><span class="sxs-lookup"><span data-stu-id="547a4-116">Publish the new and/or updated data to the MDS repository.</span></span>  
  
## <a name="knowledge-bases"></a><span data-ttu-id="547a4-117">知识库</span><span class="sxs-lookup"><span data-stu-id="547a4-117">Knowledge Bases</span></span>  
 <span data-ttu-id="547a4-118">在外接程序中提供的匹配结果基于 DQS 知识库。</span><span class="sxs-lookup"><span data-stu-id="547a4-118">The matching results provided in the Add-in are based on a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="547a4-119">默认知识库（DQS 数据）是在安装 DQS 时创建的。</span><span class="sxs-lookup"><span data-stu-id="547a4-119">The default knowledge base (DQS Data) is created when DQS is installed.</span></span> <span data-ttu-id="547a4-120">如果您选择使用默认知识库（没有将匹配策略添加到数据质量客户端的默认知识库中），则必须将工作表中的列映射到知识库中的域，然后将权重值分配给您选择的域。</span><span class="sxs-lookup"><span data-stu-id="547a4-120">If you choose to use the default knowledge base (without adding a matching policy to the default knowledge base in the Data Quality Client), you must map columns in the worksheet to domains in the knowledge base, and then assign a weight value to the domains you choose.</span></span>  
  
-   <span data-ttu-id="547a4-121">您可以使用数据质量客户端创建具有匹配策略的新的知识库，或者将一个匹配策略添加到默认知识库。</span><span class="sxs-lookup"><span data-stu-id="547a4-121">You can use the Data Quality Client to create a new knowledge base with a matching policy, or to add a matching policy to the default knowledge base.</span></span> <span data-ttu-id="547a4-122">在此情况下，权重值由您已创建的匹配策略确定，并且您仅需将列映射到域。</span><span class="sxs-lookup"><span data-stu-id="547a4-122">In this case, the weight values are determined by the matching policy you already created and you need only to map the columns to the domains.</span></span> <span data-ttu-id="547a4-123">有关详细信息，请参阅 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="547a4-123">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
 <span data-ttu-id="547a4-124">有关知识库的详细信息，请参阅 [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="547a4-124">For more information about knowledge bases, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="547a4-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="547a4-125">Related Tasks</span></span>  
  
|<span data-ttu-id="547a4-126">任务说明</span><span class="sxs-lookup"><span data-stu-id="547a4-126">Task Description</span></span>|<span data-ttu-id="547a4-127">主题</span><span class="sxs-lookup"><span data-stu-id="547a4-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="547a4-128">将外部数据与 MDS 管理的数据进行合并以便准备进行比较。</span><span class="sxs-lookup"><span data-stu-id="547a4-128">Combine external data with MDS-managed data in preparation to compare it.</span></span>|[<span data-ttu-id="547a4-129">合并数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="547a4-129">Combine Data &#40;MDS Add-in for Excel&#41;</span></span>](combine-data-mds-add-in-for-excel.md)|  
|<span data-ttu-id="547a4-130">使用 DQS 知识来查找您的数据中的相似之处。</span><span class="sxs-lookup"><span data-stu-id="547a4-130">Use DQS knowledge to find similarities in your data.</span></span>|[<span data-ttu-id="547a4-131">匹配相似数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="547a4-131">Match Similar Data &#40;MDS Add-in for Excel&#41;</span></span>](match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="547a4-132">相关内容</span><span class="sxs-lookup"><span data-stu-id="547a4-132">Related Content</span></span>  
  
-   [<span data-ttu-id="547a4-133">MDS Add-in for Excel&#41;发布数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="547a4-133">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="547a4-134">数据匹配</span><span class="sxs-lookup"><span data-stu-id="547a4-134">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
