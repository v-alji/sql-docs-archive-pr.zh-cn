---
title: 在关联规则模型中筛选项集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f841280a6dd39a5f824f2e6a10975b0f80ed0761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577913"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a><span data-ttu-id="68ccd-102">在关联规则模型中筛选项集</span><span class="sxs-lookup"><span data-stu-id="68ccd-102">Filter an Itemset in an Association Rules Model</span></span>
  <span data-ttu-id="68ccd-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，可以筛选 **关联规则查看器的** “项集” [!INCLUDE[msCoName](../../includes/msconame-md.md)] 选项卡中显示的项集。</span><span class="sxs-lookup"><span data-stu-id="68ccd-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can filter the itemsets that are displayed in the **Itemsets** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer.</span></span>  
  
### <a name="to-filter-an-itemset"></a><span data-ttu-id="68ccd-104">筛选项集</span><span class="sxs-lookup"><span data-stu-id="68ccd-104">To filter an itemset</span></span>  
  
1.  <span data-ttu-id="68ccd-105">在 **中的数据挖掘设计器的** “挖掘模型查看器” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡上，单击 **“关联规则查看器”** 的 **“项集”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="68ccd-105">On the **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Itemsets** tab of the **Association Rules Viewer**.</span></span>  
  
2.  <span data-ttu-id="68ccd-106">在 **“筛选项集”** 框中输入规则条件。</span><span class="sxs-lookup"><span data-stu-id="68ccd-106">Enter a rule condition in the **Filter itemset** box.</span></span> <span data-ttu-id="68ccd-107">例如，规则条件可以为“Touring-1000 = existing”</span><span class="sxs-lookup"><span data-stu-id="68ccd-107">For example, a rule condition might be "Touring-1000 = existing"</span></span>  
  
3.  <span data-ttu-id="68ccd-108">单击 **“输入”**。</span><span class="sxs-lookup"><span data-stu-id="68ccd-108">Click **Enter**.</span></span>  
  
 <span data-ttu-id="68ccd-109">现在便对项集进行了筛选以仅显示包含所选项的那些项集。</span><span class="sxs-lookup"><span data-stu-id="68ccd-109">The itemsets are now filtered to display only those itemsets that contain the selected items.</span></span> <span data-ttu-id="68ccd-110">该框不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="68ccd-110">The box is not case-sensitive.</span></span> <span data-ttu-id="68ccd-111">筛选器存储在内存中，因此您可以从列表中选择过去使用的筛选器。</span><span class="sxs-lookup"><span data-stu-id="68ccd-111">Filters are stored in memory so that you can select an old filter from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ccd-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68ccd-112">See Also</span></span>  
 [<span data-ttu-id="68ccd-113">挖掘模型查看器任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="68ccd-113">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
