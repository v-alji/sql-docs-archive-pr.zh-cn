---
title: 创建挖掘模型的副本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: a05eb75210ce9f601aeca515cd299f4204908705
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577096"
---
# <a name="make-a-copy-of-a-mining-model"></a><span data-ttu-id="7848d-102">生成挖掘模型的副本</span><span class="sxs-lookup"><span data-stu-id="7848d-102">Make a Copy of a Mining Model</span></span>
  <span data-ttu-id="7848d-103">在要快速创建基于相同数据的多个挖掘模型时，创建挖掘模型的副本将很有用。</span><span class="sxs-lookup"><span data-stu-id="7848d-103">Creating a copy of a mining model is useful when you want to quickly create several mining models that are based on the same data.</span></span> <span data-ttu-id="7848d-104">在您复制模型后，可以通过更改参数或添加筛选器，编辑新副本。</span><span class="sxs-lookup"><span data-stu-id="7848d-104">After you copy the model, you can then edit the new copy by changing parameters or adding a filter.</span></span>  
  
 <span data-ttu-id="7848d-105">例如，如果你有一个链接到购买表的 Customers 表，则可以创建副本以便针对各个客户人口统计学指标生成单独的挖掘模型，并且对年龄或区域之类的属性进行筛选。</span><span class="sxs-lookup"><span data-stu-id="7848d-105">For example, if you have a Customers table that is linked to a table of purchases, you could create copies to generate separate mining models for each customer demographic, filtering on attributes such as age or region.</span></span>  
  
 <span data-ttu-id="7848d-106">有关如何将模型内容（如图形表示形式或模型模式）复制到剪贴板以供其他程序使用的信息，请参阅 [复制挖掘模型的视图](copy-a-view-of-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7848d-106">For information about how to copy the content of the model (such as the graphical representation or the model patterns) to the Clipboard for use in other programs, see [Copy a View of a Mining Model](copy-a-view-of-a-mining-model.md).</span></span>  
  
### <a name="to-create-a-related-mining-model"></a><span data-ttu-id="7848d-107">创建相关的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7848d-107">To create a related mining model</span></span>  
  
1.  <span data-ttu-id="7848d-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中，单击包含挖掘模型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="7848d-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model.</span></span>  
  
2.  <span data-ttu-id="7848d-109">单击 **“挖掘模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7848d-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="7848d-110">选择模型，然后右键单击打开快捷菜单。</span><span class="sxs-lookup"><span data-stu-id="7848d-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="7848d-111">- 或 -</span><span class="sxs-lookup"><span data-stu-id="7848d-111">-or-</span></span>  
  
     <span data-ttu-id="7848d-112">选择该模型。</span><span class="sxs-lookup"><span data-stu-id="7848d-112">Select the model.</span></span> <span data-ttu-id="7848d-113">在 **“挖掘模型”** 菜单中，选择 **“新建挖掘模型”**。</span><span class="sxs-lookup"><span data-stu-id="7848d-113">On the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="7848d-114">为新的挖掘模型键入名称，并选择一种算法。</span><span class="sxs-lookup"><span data-stu-id="7848d-114">Type a name for the new mining model, and select an algorithm.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a><span data-ttu-id="7848d-115">编辑已复制的挖掘模型的筛选器</span><span class="sxs-lookup"><span data-stu-id="7848d-115">To edit the filter on the copied mining model</span></span>  
  
1.  <span data-ttu-id="7848d-116">选择挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7848d-116">Select the mining model.</span></span>  
  
2.  <span data-ttu-id="7848d-117">在 "**属性**" 窗口中，单击 "**筛选器**" 属性文本框，然后单击 "生成\*\* ( ..." ) \*\*按钮。</span><span class="sxs-lookup"><span data-stu-id="7848d-117">In the **Properties** window, click the text box for the **Filter** property, and the click the build **(...)** button.</span></span>  
  
3.  <span data-ttu-id="7848d-118">更改筛选条件。</span><span class="sxs-lookup"><span data-stu-id="7848d-118">Change the filter conditions.</span></span>  
  
     <span data-ttu-id="7848d-119">有关如何使用筛选器编辑器对话框的详细信息，请参阅 [对挖掘模型应用筛选器](apply-a-filter-to-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7848d-119">For more information about how to use the filter editor dialog boxes, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
4.  <span data-ttu-id="7848d-120">在 "**属性**" 窗口的文本框中， `AlgorithmParameters` 单击 "**需要参数**"，然后根据需要更改算法参数。</span><span class="sxs-lookup"><span data-stu-id="7848d-120">In the **Properties** window, in the `AlgorithmParameters` text box, click **Setalgorithm parameters**, and change algorithm parameters, if desired.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7848d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7848d-121">See Also</span></span>  
 <span data-ttu-id="7848d-122">[挖掘模型的筛选器 &#40;Analysis Services 数据挖掘&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7848d-122">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7848d-123">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7848d-123">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="7848d-124">从挖掘模型中删除筛选器</span><span class="sxs-lookup"><span data-stu-id="7848d-124">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
