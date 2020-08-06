---
title: 将新模型添加到目标邮件结构 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b83dfc6c9e218eecf3f2abe636b8c24d69d1b507
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691409"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="63581-102">向 Targeted Mailing 结构中添加新模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="63581-102">Adding New Models to the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="63581-103">在此任务中，您将使用数据挖掘设计器的 "**挖掘模型**" 选项卡定义另外两个模型。</span><span class="sxs-lookup"><span data-stu-id="63581-103">In this task, you will define two additional models by using the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="63581-104">您将使用 Microsoft 聚类分析算法和 Microsoft Naive Bayes 算法创建模型。</span><span class="sxs-lookup"><span data-stu-id="63581-104">You will use the Microsoft Clustering and Microsoft Naive Bayes algorithms to create the models.</span></span> <span data-ttu-id="63581-105">之所以选择这两种算法，是因为它们能够预测离散值（例如，自行车购买行为）。</span><span class="sxs-lookup"><span data-stu-id="63581-105">These two algorithms are selected because of their ability to predict a discrete value (i.e., bike purchase).</span></span> <span data-ttu-id="63581-106">有关这些算法的详细信息，请参阅[Microsoft 聚类分析算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)和[Microsoft Naive Bayes 算法](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="63581-106">For more information about these algorithms, see [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)</span></span>  
  
### <a name="to-create-a-clustering-mining-model"></a><span data-ttu-id="63581-107">创建聚类分析挖掘模型</span><span class="sxs-lookup"><span data-stu-id="63581-107">To create a clustering mining model</span></span>  
  
1.  <span data-ttu-id="63581-108">切换到中数据挖掘设计器中的 "**挖掘模型**" 选项卡 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="63581-108">Switch to the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="63581-109">请注意，设计器将显示两个列，一个用于挖掘结构，另一个用于 `TM_Decision_Tree` 在上一课中创建的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="63581-109">Notice that the designer displays two columns, one for the mining structure and one for the `TM_Decision_Tree` mining model, which you created in the previous lesson.</span></span>  
  
2.  <span data-ttu-id="63581-110">右键单击 "**结构**" 列，然后选择 "**新建挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="63581-110">Right-click the **Structure** column and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="63581-111">在 "**新建挖掘模型**" 对话框中的 "**模型名称**" 中，键入 `TM_Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="63581-111">In the **New Mining Model** dialog box, in **Model name**, type `TM_Clustering`.</span></span>  
  
4.  <span data-ttu-id="63581-112">在 "**算法名称**" 中选择 " **Microsoft 群集**"。</span><span class="sxs-lookup"><span data-stu-id="63581-112">In **Algorithm name**, select **Microsoft Clustering**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="63581-113">新模型现在会显示在数据挖掘设计器的 "**挖掘模型**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="63581-113">The new model now appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="63581-114">此模型是通过 [!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法生成的，它将具有类似特征的客户分组到群集中，并为每个分类预测自行车购买量。</span><span class="sxs-lookup"><span data-stu-id="63581-114">This model, built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, groups customers with similar characteristics into clusters and predicts bike buying for each cluster.</span></span> <span data-ttu-id="63581-115">虽然您可以修改新模型的列用法和属性，但本教程不需要对模型进行任何更改 `TM_Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="63581-115">Although you can modify the column usage and properties for the new model, no changes to the `TM_Clustering` model are necessary for this tutorial.</span></span>  
  
### <a name="to-create-a-naive-bayes-mining-model"></a><span data-ttu-id="63581-116">创建 Naive Bayes 挖掘模型</span><span class="sxs-lookup"><span data-stu-id="63581-116">To create a Naive Bayes mining model</span></span>  
  
1.  <span data-ttu-id="63581-117">在数据挖掘设计器的 "**挖掘模型**" 选项卡中，右键单击 productsportal**结构**列，然后选择 "**新建挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="63581-117">In the **Mining Models** tab of Data Mining Designer, right-clickthe **Structure** column, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="63581-118">在 "**新建挖掘模型**" 对话框中的 "**模型名称**" 下，键入 `TM_NaiveBayes` 。</span><span class="sxs-lookup"><span data-stu-id="63581-118">In the **New Mining Model** dialog box, under **Model name**, type `TM_NaiveBayes`.</span></span>  
  
3.  <span data-ttu-id="63581-119">在 "**算法名称**" 中，选择 " **Microsoft Naive Bayes**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="63581-119">In **Algorithm name**, select **Microsoft Naive Bayes**, then click **OK**.</span></span>  
  
     <span data-ttu-id="63581-120">此时会出现一条消息，指出 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 算法不支持**年龄**列和**每年收入**列，这是连续的。</span><span class="sxs-lookup"><span data-stu-id="63581-120">A message appears stating that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm does not support the **Age** and **Yearly Income** columns, which are continuous.</span></span>  
  
4.  <span data-ttu-id="63581-121">单击 **"是"** 以确认消息并继续。</span><span class="sxs-lookup"><span data-stu-id="63581-121">Click **Yes** to acknowledge the message and continue.</span></span>  
  
 <span data-ttu-id="63581-122">新模型将显示在数据挖掘设计器的 "**挖掘模型**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="63581-122">A new model appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="63581-123">虽然您可以修改此选项卡中所有模型的列用法和属性，但本教程不需要对模型进行任何更改 `TM_NaiveBayes` 。</span><span class="sxs-lookup"><span data-stu-id="63581-123">Although you can modify the column usage and properties for all the models in this tab, no changes to the `TM_NaiveBayes` model are necessary for this tutorial.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="63581-124">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="63581-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="63581-125">在目标邮件结构中处理模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="63581-125">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="63581-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63581-126">See Also</span></span>  
 <span data-ttu-id="63581-127">[向结构中添加挖掘模型 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="63581-127">[Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="63581-128">[数据挖掘设计器](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="63581-128">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="63581-129">移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="63581-129">Moving Data Mining Objects</span></span>](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
