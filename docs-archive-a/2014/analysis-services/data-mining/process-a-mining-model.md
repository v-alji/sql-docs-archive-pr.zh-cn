---
title: 处理挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
author: minewiskan
ms.author: owend
ms.openlocfilehash: c2fed5d72c677dc175f4c9681096d1859b30d829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690878"
---
# <a name="process-a-mining-model"></a><span data-ttu-id="aa84e-102">处理挖掘模型</span><span class="sxs-lookup"><span data-stu-id="aa84e-102">Process a Mining Model</span></span>
  <span data-ttu-id="aa84e-103">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的数据挖掘设计器的“挖掘模型”选项卡中，您可以处理与挖掘结构关联的特定挖掘模型，也可以处理与结构关联的所有模型。</span><span class="sxs-lookup"><span data-stu-id="aa84e-103">In the Mining Models tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can either process a specific mining model that is associated with a mining structure or you can process all the models that are associated with the structure.</span></span>  
  
 <span data-ttu-id="aa84e-104">可以使用以下工具处理挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="aa84e-104">You can process a mining model by using the following tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 <span data-ttu-id="aa84e-105">还可以使用 XMLA 处理命令。</span><span class="sxs-lookup"><span data-stu-id="aa84e-105">You can also use an XMLA Process command.</span></span> <span data-ttu-id="aa84e-106">有关详细信息，请参阅[用于处理的工具和方法 (Analysis Services)](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aa84e-106">For more information, see  [Tools and Approaches for Processing &#40;Analysis Services&#41;](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).</span></span>  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="aa84e-107">使用 SQL Server Data Tools 处理单个挖掘模型</span><span class="sxs-lookup"><span data-stu-id="aa84e-107">Process a single mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="aa84e-108">在数据挖掘设计器的 **“挖掘模型”** 选项卡上，从网格中的一列或多列模型中选择一个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="aa84e-108">On the **Mining Models** tab of Data Mining Designer, select a mining model from the one or more columns of models in the grid.</span></span>  
  
2.  <span data-ttu-id="aa84e-109">在 **“挖掘模型”** 菜单中，选择 **“处理模型”**。</span><span class="sxs-lookup"><span data-stu-id="aa84e-109">On the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="aa84e-110">如果更改了挖掘结构，系统将提示您在处理模型之前重新部署结构。</span><span class="sxs-lookup"><span data-stu-id="aa84e-110">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the model.</span></span> <span data-ttu-id="aa84e-111">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="aa84e-111">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="aa84e-112">在 "**处理挖掘模型 \<model> \*\* " 对话框中，单击 "**运行\*\*"。</span><span class="sxs-lookup"><span data-stu-id="aa84e-112">In the **Processing Mining Model - \<model>** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="aa84e-113">此时，将打开 **“处理进度”** 对话框，以显示模型处理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="aa84e-113">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
4.  <span data-ttu-id="aa84e-114">成功处理完模型之后，在 **“处理进度”** 对话框中，单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="aa84e-114">After the model has successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="aa84e-115">在 "**处理挖掘模型 \<model> -** " 对话框中单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="aa84e-115">Click **Close** in the **Processing Mining Model - \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="aa84e-116">只有挖掘结构和所选挖掘模型被处理。</span><span class="sxs-lookup"><span data-stu-id="aa84e-116">Only the mining structure and the selected mining model have been processed.</span></span>  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a><span data-ttu-id="aa84e-117">处理与挖掘结构关联的所有挖掘模型</span><span class="sxs-lookup"><span data-stu-id="aa84e-117">Process all mining models that are associated with a mining structure</span></span>  
  
1.  <span data-ttu-id="aa84e-118">在数据挖掘设计器的 **“挖掘模型”** 选项卡中，从 **“挖掘模型”** 菜单中选择 **“处理挖掘结构和所有模型”** 。</span><span class="sxs-lookup"><span data-stu-id="aa84e-118">On the **Mining Models** tab of Data Mining Designer, select **Process Mining Structure and All Models** from the **Mining Model** menu.</span></span>  
  
2.  <span data-ttu-id="aa84e-119">如果更改了挖掘结构，系统将提示您在处理模型之前重新部署结构。</span><span class="sxs-lookup"><span data-stu-id="aa84e-119">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="aa84e-120">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="aa84e-120">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="aa84e-121">在 "**处理挖掘结构 \<structure> \*\* " 对话框中，单击 "**运行\*\*"。</span><span class="sxs-lookup"><span data-stu-id="aa84e-121">In the **Processing Mining Structure - \<structure>** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="aa84e-122">此时，将打开 **“处理进度”** 对话框，以显示模型处理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="aa84e-122">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
5.  <span data-ttu-id="aa84e-123">成功处理完模型之后，在 **“处理进度”** 对话框中，单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="aa84e-123">After the models have successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
6.  <span data-ttu-id="aa84e-124">在 "**处理 \<model> \*\* " 对话框中单击 "**关闭\*\*"。</span><span class="sxs-lookup"><span data-stu-id="aa84e-124">Click **Close** in the **Processing \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="aa84e-125">挖掘结构和所有关联的挖掘模型被处理。</span><span class="sxs-lookup"><span data-stu-id="aa84e-125">The mining structure and all the associated mining models have been processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa84e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa84e-126">See Also</span></span>  
 [<span data-ttu-id="aa84e-127">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="aa84e-127">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
