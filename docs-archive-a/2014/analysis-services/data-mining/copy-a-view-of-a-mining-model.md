---
title: 复制挖掘模型的视图 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clipboards [data mining]
- Mining Model Viewer [Analysis Services], clipboards
- copying mining models to clipboard
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36d4d372bd235cd1cc0c043ff98151091e242269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682453"
---
# <a name="copy-a-view-of-a-mining-model"></a><span data-ttu-id="08681-102">复制挖掘模型的视图</span><span class="sxs-lookup"><span data-stu-id="08681-102">Copy a View of a Mining Model</span></span>
  <span data-ttu-id="08681-103">对于每种类型的挖掘模型， **中数据挖掘设计器的** “挖掘模型查看器” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 选项卡使用单独的查看器。</span><span class="sxs-lookup"><span data-stu-id="08681-103">The **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] uses a separate viewer for each type of mining model.</span></span> <span data-ttu-id="08681-104">其中有数种查看器包含可以从中将内容复制到剪贴板的组件，并包含可以从中将内容粘贴到文档或图像处理软件的组件。</span><span class="sxs-lookup"><span data-stu-id="08681-104">Several of the viewers have components from which you can copy the contents to the Clipboard, and from there paste the contents into a document or into image manipulation software.</span></span> <span data-ttu-id="08681-105">下列组件提供了这项功能：</span><span class="sxs-lookup"><span data-stu-id="08681-105">The following components make this functionality available:</span></span>  
  
-   <span data-ttu-id="08681-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分类查看器和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器中的分类关系图</span><span class="sxs-lookup"><span data-stu-id="08681-106">Cluster Diagram in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="08681-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 树查看器和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 时序查看器中的决策树</span><span class="sxs-lookup"><span data-stu-id="08681-107">Decision Tree in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer</span></span>  
  
-   <span data-ttu-id="08681-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器中的状态转换</span><span class="sxs-lookup"><span data-stu-id="08681-108">State Transitions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="08681-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则查看器、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 查看器以及 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 树查看器中的相关性网络</span><span class="sxs-lookup"><span data-stu-id="08681-109">Dependency Network in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer</span></span>  
  
-   <span data-ttu-id="08681-110">从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器的“节点详细信息”窗格中挖掘模型内容</span><span class="sxs-lookup"><span data-stu-id="08681-110">Mining model content, from the Node Details pane of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer</span></span>  
  
 <span data-ttu-id="08681-111">可以复制整个挖掘模型或仅复制查看器中的可见部分。</span><span class="sxs-lookup"><span data-stu-id="08681-111">You can copy the complete representation of the mining model, or just the part that is visible in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="08681-112">使用查看器复制模型时，它不创建新的模型对象。</span><span class="sxs-lookup"><span data-stu-id="08681-112">When you copy a model using the viewer, it does not create a new model object.</span></span> <span data-ttu-id="08681-113">若要创建新模型，必须使用向导或数据挖掘设计器。</span><span class="sxs-lookup"><span data-stu-id="08681-113">To create a new model, you must use either the wizard, or the Data Mining Designer,.</span></span> <span data-ttu-id="08681-114">有关详细信息，请参阅 [生成挖掘模型的副本](make-a-copy-of-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="08681-114">For more information, see [Make a Copy of a Mining Model](make-a-copy-of-a-mining-model.md).</span></span>  
  
### <a name="to-copy-the-complete-model-to-the-clipboard"></a><span data-ttu-id="08681-115">将整个模型复制到剪贴板</span><span class="sxs-lookup"><span data-stu-id="08681-115">To copy the complete model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="08681-116">从 **“挖掘模型查看器”** 选项卡上的 **“挖掘模型”** 列表中，选择要查看的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="08681-116">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="08681-117">选择适当的选项卡（例如， **“相关性网络”** 选项卡），然后在该选项卡的工具栏上单击 **“复制整个图形”** 。</span><span class="sxs-lookup"><span data-stu-id="08681-117">Select the appropriate tab, such as the **Dependency Network** tab, and then click **Copy Entire Graph** on the toolbar of that tab.</span></span>  
  
### <a name="to-copy-the-visible-piece-of-the-model-to-the-clipboard"></a><span data-ttu-id="08681-118">将模型的可见部分复制到剪贴板</span><span class="sxs-lookup"><span data-stu-id="08681-118">To copy the visible piece of the model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="08681-119">从 **“挖掘模型查看器”** 选项卡上的 **“挖掘模型”** 列表中，选择要查看的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="08681-119">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="08681-120">选择适当的选项卡（例如， **“相关性网络”** 选项卡），然后执行放大或缩小操作以在您想要的级别上查看模型。</span><span class="sxs-lookup"><span data-stu-id="08681-120">Select the appropriate tab, such as the **Dependency Network** tab, and then zoom in or out to view the model at the level that you want.</span></span>  
  
3.  <span data-ttu-id="08681-121">在所选选项卡的工具栏上单击 **“复制图形视图”** 。</span><span class="sxs-lookup"><span data-stu-id="08681-121">Click **Copy Graph View** on the toolbar of the selected tab.</span></span>  
  
### <a name="to-copy-the-mining-model-content-to-the-clipboard"></a><span data-ttu-id="08681-122">将挖掘模型内容复制到剪贴板</span><span class="sxs-lookup"><span data-stu-id="08681-122">To copy the mining model content to the Clipboard</span></span>  
  
1.  <span data-ttu-id="08681-123">从 **“挖掘模型查看器”** 选项卡上的 **“挖掘模型”** 列表中，选择要查看的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="08681-123">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="08681-124">从“查看器”\*\*\*\* 下拉列表中，选择“Microsoft 一般内容树查看器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="08681-124">From the **Viewer** drop-down list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
3.  <span data-ttu-id="08681-125">在“节点标题(唯一 ID)”\*\*\*\* 窗格中，单击一个节点。</span><span class="sxs-lookup"><span data-stu-id="08681-125">In the **Node Caption (Unique ID)** pane, click a node.</span></span>  
  
4.  <span data-ttu-id="08681-126">右键单击“节点详细信息”\*\*\*\* 窗格，然后选择“全选”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="08681-126">Right-click the **Node Details** pane and then select **Select All**.</span></span>  
  
5.  <span data-ttu-id="08681-127">右键再次单击“节点详细信息”\*\*\*\* 窗格，然后选择“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="08681-127">Right-click the **Node Details** pane again and select **Copy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08681-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08681-128">See Also</span></span>  
 [<span data-ttu-id="08681-129">挖掘模型查看器任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="08681-129">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
