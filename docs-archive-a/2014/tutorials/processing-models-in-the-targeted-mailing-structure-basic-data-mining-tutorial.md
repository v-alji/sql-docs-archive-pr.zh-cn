---
title: 在目标邮件结构中处理模型 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8fb7b9f601f351520c3f611cc3c520614ed8ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689196"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="99b25-102">处理 Targeted Mailing 结构中的模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="99b25-102">Processing Models in the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="99b25-103">必须先部署 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目并处理挖掘结构和挖掘模型，然后才能浏览或使用创建的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="99b25-103">Before you can browse or work with the mining models that you have created, you must deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span>  
  
-   <span data-ttu-id="99b25-104">*部署*将项目发送到服务器，并在服务器上创建该项目中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="99b25-104">*Deploying* sends the project to a server and creates any objects in that project on the server.</span></span>  
  
-   <span data-ttu-id="99b25-105">*处理*将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用关系数据源中的数据填充对象。</span><span class="sxs-lookup"><span data-stu-id="99b25-105">*Processing* populates [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects with data from relational data sources.</span></span>  
  
 <span data-ttu-id="99b25-106">模型经过部署和处理后才能使用。</span><span class="sxs-lookup"><span data-stu-id="99b25-106">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="99b25-107">此外，当您对模型进行任何更改（如添加新数据）时，必须重新部署和重新处理模型。</span><span class="sxs-lookup"><span data-stu-id="99b25-107">Also, when you make any changes to the model, such as adding new data, you must redeploy and reprocess the models.</span></span>  
  
## <a name="ensuring-consistency-with-holdoutseed"></a><span data-ttu-id="99b25-108">确保与 HoldoutSeed 一致</span><span class="sxs-lookup"><span data-stu-id="99b25-108">Ensuring Consistency with HoldoutSeed</span></span>  
 <span data-ttu-id="99b25-109">部署项目并处理结构和模型后，将数据结构中的各行根据数值种子值分配给定型集或测试集。</span><span class="sxs-lookup"><span data-stu-id="99b25-109">When you deploy a project and process the structure and models, individual rows in your data structure are assigned to either the training set or testing set based on a numerical seed value.</span></span> <span data-ttu-id="99b25-110">默认情况下，数值种子值是根据数据结构的属性计算的。</span><span class="sxs-lookup"><span data-stu-id="99b25-110">By default, the numerical seed value is computed based on attributes of the data structure.</span></span> <span data-ttu-id="99b25-111">但是，如果您更改过模型的某些方面，该种子值将变化，导致结果略有不同。</span><span class="sxs-lookup"><span data-stu-id="99b25-111">However, if you ever change some aspects of your model, the seed value would change, leading to subtly different results.</span></span> <span data-ttu-id="99b25-112">因此，为了确保您的结果与此处所述的结果相同，我们将随机分配固定的*维持种子* `12` 。</span><span class="sxs-lookup"><span data-stu-id="99b25-112">Therefore, in order to ensure that your results are the same as described here, we will arbitrarily assign a fixed *holdout seed* of `12`.</span></span> <span data-ttu-id="99b25-113">维持种子用来初始化抽样算法的种子，并确保以大体相同的方式对所有挖掘结构及其模型中的数据进行分区。</span><span class="sxs-lookup"><span data-stu-id="99b25-113">The holdout seed is used to initialize the sampling algorithm, and ensures that the data is partitioned in roughly the same way for all mining structures and their models.</span></span>  
  
 <span data-ttu-id="99b25-114">此值不影响定型集内的事例数，它仅确保每次生成模型时将使用相同的分区方法。</span><span class="sxs-lookup"><span data-stu-id="99b25-114">This value does not affect the number of cases in the training set; it simply ensures that the same partitioning method will be used each time you build the model.</span></span>  
  
 <span data-ttu-id="99b25-115">有关维持种子的详细信息，请参阅[定型和测试数据集](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="99b25-115">For more information on holdout seed, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-set-the-holdout-seed"></a><span data-ttu-id="99b25-116">设置维持种子</span><span class="sxs-lookup"><span data-stu-id="99b25-116">To set the Holdout Seed</span></span>  
  
1.  <span data-ttu-id="99b25-117">在的数据挖掘设计器中单击 "**挖掘结构**" 选项卡或 "**挖掘模型**" 选项卡 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="99b25-117">Click on the **Mining Structure** tab or the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="99b25-118">**目标邮件 MiningStructure**显示在 "**属性**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="99b25-118">**Targeted Mailing MiningStructure** displays in the **Properties** pane.</span></span>  
  
2.  <span data-ttu-id="99b25-119">通过按**F4**确保 "**属性**" 窗格处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="99b25-119">Ensure that the **Properties** pane is open by pressing **F4**.</span></span>  
  
3.  <span data-ttu-id="99b25-120">确保将**CacheMode**设置为**KeepTrainingCases**。</span><span class="sxs-lookup"><span data-stu-id="99b25-120">Ensure that **CacheMode** is set to **KeepTrainingCases**.</span></span>  
  
4.  <span data-ttu-id="99b25-121">`12`为**HoldoutSeed**输入。</span><span class="sxs-lookup"><span data-stu-id="99b25-121">Enter `12` for **HoldoutSeed**.</span></span>  
  
## <a name="deploying-and-processing-the-models"></a><span data-ttu-id="99b25-122">部署并处理模型</span><span class="sxs-lookup"><span data-stu-id="99b25-122">Deploying and Processing the Models</span></span>  
 <span data-ttu-id="99b25-123">在数据挖掘设计器中，您可以决定要处理的对象，具体取决于您对模型或基础数据所做的更改的范围：</span><span class="sxs-lookup"><span data-stu-id="99b25-123">In Data Mining Designer, you can decide which objects to process, depending on the scope of changes you've made to your model or the underlying data:</span></span>  
  
 <span data-ttu-id="99b25-124">在本任务中，因为数据和模型是新的，我们将同时处理结构和所有模型。</span><span class="sxs-lookup"><span data-stu-id="99b25-124">For this task, because the data and the models are new, you will process the structure and all the models at the same time.</span></span>  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a><span data-ttu-id="99b25-125">部署项目并处理所有挖掘模型</span><span class="sxs-lookup"><span data-stu-id="99b25-125">To deploy the project and process all the mining models</span></span>  
  
1.  <span data-ttu-id="99b25-126">在 "**挖掘模型**" 菜单中，选择 "**处理挖掘结构和所有模型**"。</span><span class="sxs-lookup"><span data-stu-id="99b25-126">In the **Mining Model** menu, select **Process Mining Structure and All Models**.</span></span>  
  
     <span data-ttu-id="99b25-127">如果更改了结构，系统将提示您在处理模型之前生成和部署项目。</span><span class="sxs-lookup"><span data-stu-id="99b25-127">If you made changes to the structure, you will be prompted to build and deploy the project before processing the models.</span></span> <span data-ttu-id="99b25-128">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="99b25-128">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="99b25-129">在 "**处理挖掘结构-目标邮件**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="99b25-129">Click **Run** in the **Processing Mining Structure - Targeted Mailing** dialog box.</span></span>  
  
     <span data-ttu-id="99b25-130">**“处理进度”** 对话框将打开以显示有关模型处理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="99b25-130">The **Process Progress** dialog box opens to display the details of model processing.</span></span> <span data-ttu-id="99b25-131">模型处理可能需要一些时间，具体取决于您的计算机。</span><span class="sxs-lookup"><span data-stu-id="99b25-131">Model processing might take some time, depending on your computer.</span></span>  
  
3.  <span data-ttu-id="99b25-132">模型处理完成后，在 **“处理进度”** 对话框中单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="99b25-132">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="99b25-133">在 "**处理挖掘结构 \<structure> -** " 对话框中单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="99b25-133">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="99b25-134">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="99b25-134">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="99b25-135">将新模型添加到目标邮件结构 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="99b25-135">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="99b25-136">下一课</span><span class="sxs-lookup"><span data-stu-id="99b25-136">Next Lesson</span></span>  
 [<span data-ttu-id="99b25-137">第4课：浏览目标邮件模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="99b25-137">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="99b25-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99b25-138">See Also</span></span>  
 [<span data-ttu-id="99b25-139">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="99b25-139">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
