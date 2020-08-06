---
title: 创建相关的顺序分析和聚类分析模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d015ed8a9887cb6164020806bf4136f58629ad11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690941"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="bb694-102">创建相关的顺序分析和聚类分析模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="bb694-102">Creating a Related Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="bb694-103">通过浏览顺序分析和聚类分析模型，您了解到如 Region 或 Income 等其他属性对模型有巨大影响；因此为了更好地了解序列，您将创建一个相关的顺序分析和聚类分析模型，并删除与客户人口统计信息有关的属性。</span><span class="sxs-lookup"><span data-stu-id="bb694-103">Through your exploration of the sequence clustering model, you learned that other attributes such as Region or Income have a strong effect on the models; therefore, to understand the sequences better, you will create a related sequence clustering model and remove the attributes related to customer demographics.</span></span>  
  
 <span data-ttu-id="bb694-104">在本任务中，您将创建区域顺序分析和聚类分析模型的副本，然后从该模型中删除与序列没有直接关系的任何列。</span><span class="sxs-lookup"><span data-stu-id="bb694-104">In this task, you will create a copy of the regional sequence clustering model, and then remove from the model any columns that are not directly related to the sequences.</span></span>  
  
 <span data-ttu-id="bb694-105">新模型包含的所有列与它所基于的挖掘模型的列相同。</span><span class="sxs-lookup"><span data-stu-id="bb694-105">The new model will contain all the same columns as the mining model on which it is based.</span></span> <span data-ttu-id="bb694-106">但是，您不需要删除挖掘结构中的列，只需指定新挖掘模型忽略这些列即可。</span><span class="sxs-lookup"><span data-stu-id="bb694-106">However, you do not need to remove the columns from the mining structure, only specify that the new mining model ignore the columns.</span></span>  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a><span data-ttu-id="bb694-107">创建顺序分析和聚类分析模型的副本</span><span class="sxs-lookup"><span data-stu-id="bb694-107">To make a copy of the sequence clustering model</span></span>  
  
1.  <span data-ttu-id="bb694-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的数据挖掘设计器中，单击 "**挖掘模型**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bb694-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in the Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="bb694-109">右键单击要复制的模型，然后选择 "**新建挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="bb694-109">Right-click the model you want to copy, and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="bb694-110">在 "**新建挖掘模型**" 对话框中，键入模型名称，然后选择 "Microsoft" `Sequence Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="bb694-110">In the **New Mining Model** dialog box, type a model name, and select Microsoft `Sequence Clustering`.</span></span>  
  
     <span data-ttu-id="bb694-111">对于本教程，请键入名称 `Sequence Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="bb694-111">For this tutorial, type the name `Sequence Clustering`.</span></span>  
  
4.  <span data-ttu-id="bb694-112">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="bb694-112">Click **OK**.</span></span>  
  
### <a name="to-remove-columns-from-the-mining-model"></a><span data-ttu-id="bb694-113">从挖掘模型中删除列</span><span class="sxs-lookup"><span data-stu-id="bb694-113">To remove columns from the mining model</span></span>  
  
1.  <span data-ttu-id="bb694-114">在 "**挖掘模型**" 选项卡中，在名为 "序列聚类分析" 的新模型的列中，单击 "**收入组**" 属性所在的行，然后选择 "**忽略**"。</span><span class="sxs-lookup"><span data-stu-id="bb694-114">In the **Mining Model** tab, in the column for the new model named Sequence Clustering, click the row for the **Income Group** attribute, and select **Ignore**.</span></span>  
  
2.  <span data-ttu-id="bb694-115">为属性**区域**重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="bb694-115">Repeat this step for the attribute **Region**.</span></span>  
  
3.  <span data-ttu-id="bb694-116">单击表名称旁边的加号 " **v Assoc Seq 行项**"，展开表并查看嵌套表中的列。</span><span class="sxs-lookup"><span data-stu-id="bb694-116">Click the plus sign next to the table name, **v Assoc Seq Line Items**, to expand the table and view the columns from the nested table.</span></span>  
  
     <span data-ttu-id="bb694-117">新模型应该仅有以下列：</span><span class="sxs-lookup"><span data-stu-id="bb694-117">The new model should have only the following columns:</span></span>  
  
     <span data-ttu-id="bb694-118">**订单 NumberKey**</span><span class="sxs-lookup"><span data-stu-id="bb694-118">**Order NumberKey**</span></span>  
  
     <span data-ttu-id="bb694-119">**行号键**</span><span class="sxs-lookup"><span data-stu-id="bb694-119">**Line Number Key**</span></span>  
  
     <span data-ttu-id="bb694-120">**模型预测**</span><span class="sxs-lookup"><span data-stu-id="bb694-120">**Model Predict**</span></span>  
  
### <a name="to-process-the-new-sequence-clustering-model"></a><span data-ttu-id="bb694-121">处理新的顺序分析和聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="bb694-121">To process the new sequence clustering model</span></span>  
  
1.  <span data-ttu-id="bb694-122">在 "**挖掘模型**" 选项卡中，右键单击名为的新模型 `Sequence Clustering` ，然后选择 "**处理模型**"。</span><span class="sxs-lookup"><span data-stu-id="bb694-122">In the **Mining Model** tab, right-click the new model named `Sequence Clustering`, and select **Process Model**.</span></span>  
  
     <span data-ttu-id="bb694-123">由于该新的简化挖掘模型基于已经处理过的结构，因此您不需要再重新处理该结构。</span><span class="sxs-lookup"><span data-stu-id="bb694-123">Because the new simplified mining model is based on a structure that has already been processed, you do not need to reprocess the structure.</span></span> <span data-ttu-id="bb694-124">您只需处理该新的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="bb694-124">You can process just the new mining model.</span></span>  
  
2.  <span data-ttu-id="bb694-125">单击 **"是"** 将更新后的数据挖掘项目部署到服务器。</span><span class="sxs-lookup"><span data-stu-id="bb694-125">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
3.  <span data-ttu-id="bb694-126">在 "**处理挖掘模型**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="bb694-126">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="bb694-127">单击 "**关闭**" 关闭 "**处理进度**" 对话框，然后再次单击 "**处理挖掘模型**" 对话框中的 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="bb694-127">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bb694-128">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="bb694-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bb694-129">对顺序分析和聚类分析模型创建预测 &#40;中间数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="bb694-129">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb694-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb694-130">See Also</span></span>  
 [<span data-ttu-id="bb694-131">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bb694-131">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
