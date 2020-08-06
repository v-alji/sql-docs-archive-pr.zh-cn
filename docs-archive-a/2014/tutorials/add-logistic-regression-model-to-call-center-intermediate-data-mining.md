---
title: 向呼叫中心结构中添加逻辑回归模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7d0100313d1ea5a1af5f729249bc2d743a730222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691415"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="57bba-102">向呼叫中心结构中添加逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="57bba-102">Adding a Logistic Regression Model to the Call Center Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="57bba-103">除了分析可能影响呼叫中心运营的因素之外，您还需要就员工如何提升其服务质量提供一些具体的建议。</span><span class="sxs-lookup"><span data-stu-id="57bba-103">In addition to analyzing the factors that might affect call center operations, you were also asked to provide some specific recommendations on how the staff can improve service quality.</span></span> <span data-ttu-id="57bba-104">在此任务中，您将使用生成探索模型时所使用的挖掘结构，并添加一个用来创建预测的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="57bba-104">In this task, you will use the same mining structure that you used to build the exploratory model and add a mining model that will be used for creating predictions.</span></span>  
  
 <span data-ttu-id="57bba-105">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中，逻辑回归模型基于神经网络算法，因此可以提供与神经网络模型相同的灵活性和功能，</span><span class="sxs-lookup"><span data-stu-id="57bba-105">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], a logistic regression model is based on the neural networks algorithm, and therefore provides the same flexibility and power as a neural network model.</span></span> <span data-ttu-id="57bba-106">但更适合于预测二进制结果。</span><span class="sxs-lookup"><span data-stu-id="57bba-106">However, logistic regression is particularly well-suited for predicting binary outcomes.</span></span>  
  
 <span data-ttu-id="57bba-107">在此方案中，您将使用用于神经网络模型中的同一挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="57bba-107">For this scenario, you will use the same mining structure that you used for the neural network model.</span></span> <span data-ttu-id="57bba-108">但是，您将根据自己的业务问题自定义新模型。</span><span class="sxs-lookup"><span data-stu-id="57bba-108">However, you will customize the new model to target your business questions.</span></span> <span data-ttu-id="57bba-109">您关注提高服务质量并确定需要多少有经验的操作员，因此将设置自己的模型来预测这些值。</span><span class="sxs-lookup"><span data-stu-id="57bba-109">You are interested in improving service quality and determining how many experienced operators you need, so you will set up your model to predict those values.</span></span>  
  
 <span data-ttu-id="57bba-110">为了确保基于呼叫中心数据的所有模型尽可能类似，将使用与以前相同的种子值。</span><span class="sxs-lookup"><span data-stu-id="57bba-110">To ensure that all the models based on the call center data are as similar as possible, you will use the same seed value as before.</span></span> <span data-ttu-id="57bba-111">设置种子参数确保模型从同一起点处理数据并将数据中项目导致的变差最小化。</span><span class="sxs-lookup"><span data-stu-id="57bba-111">Setting the seed parameter ensures that the model processes the data from the same starting point, and minimizes variations caused by artifacts in the data.</span></span>  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a><span data-ttu-id="57bba-112">向呼叫中心挖掘结构中添加新的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="57bba-112">To add a new mining model to the call center mining structure</span></span>  
  
1.  <span data-ttu-id="57bba-113">在的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 解决方案资源管理器中，右键单击挖掘结构**呼叫中心装箱**，然后选择 "**打开设计器**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, right-click the mining structure, **Call Center Binned**, and select **Open Designer**.</span></span>  
  
2.  <span data-ttu-id="57bba-114">在数据挖掘设计器中，单击 "**挖掘模型**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="57bba-114">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="57bba-115">单击 "**创建相关挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-115">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="57bba-116">在 "**新建挖掘模型**" 对话框的 "**模型名称**" 中，键入 `Call Center - LR` 。</span><span class="sxs-lookup"><span data-stu-id="57bba-116">In the **New Mining Model** dialog box, for **Model name**, type `Call Center - LR`.</span></span>  <span data-ttu-id="57bba-117">对于 "**算法名称**"，选择 " **Microsoft 逻辑回归**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-117">For **Algorithm name**, select **Microsoft Logistic Regression**.</span></span>  
  
5.  <span data-ttu-id="57bba-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="57bba-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="57bba-119">新的挖掘模型将显示在 "**挖掘模型**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="57bba-119">The new mining model is displayed in the **Mining Models** tab.</span></span>  
  
### <a name="to-customize-the-logistic-regression-model"></a><span data-ttu-id="57bba-120">自定义逻辑回归模型</span><span class="sxs-lookup"><span data-stu-id="57bba-120">To customize the logistic regression model</span></span>  
  
1.  <span data-ttu-id="57bba-121">在新挖掘模型的列中， `Call Center - LR` 将事实 CALLCENTER ID 保留为键。</span><span class="sxs-lookup"><span data-stu-id="57bba-121">In the column for the new mining model, `Call Center - LR`, leave Fact CallCenter ID as the key.</span></span>  
  
2.  <span data-ttu-id="57bba-122">将 ServiceGrade 和 Level 2 运算符的值更改为 "**预测**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-122">Change the value of ServiceGrade and Level Two Operators to **Predict**.</span></span>  
  
     <span data-ttu-id="57bba-123">这些列既可以用作输入，也可以用于预测。</span><span class="sxs-lookup"><span data-stu-id="57bba-123">These columns will be used both as input and for prediction.</span></span> <span data-ttu-id="57bba-124">本质上，您对同一数据创建了两个独立的模型：一个预测操作员数，一个预测服务等级。</span><span class="sxs-lookup"><span data-stu-id="57bba-124">In essence, you are creating two separate models on the same data: one that predicts the number of operators, and one that predicts the service grade.</span></span>  
  
3.  <span data-ttu-id="57bba-125">将所有其他列更改为**输入**。</span><span class="sxs-lookup"><span data-stu-id="57bba-125">Change all other columns to **Input**.</span></span>  
  
### <a name="to-specify-the-seed-and-process-the-models"></a><span data-ttu-id="57bba-126">指定种子并处理模型</span><span class="sxs-lookup"><span data-stu-id="57bba-126">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="57bba-127">在 "**挖掘模型**" 选项卡中，右键单击名为呼叫中心-LR 的模型的列，然后选择 "**设置算法参数**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-127">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="57bba-128">在 HOLDOUT_SEED 参数所在的行中，单击 "**值**" 下的空单元，然后键入 `1` 。</span><span class="sxs-lookup"><span data-stu-id="57bba-128">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="57bba-129">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="57bba-129">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57bba-130">选择哪个值作为种子无关紧要，关键是您需要对所有相关模型使用同一个种子。</span><span class="sxs-lookup"><span data-stu-id="57bba-130">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="57bba-131">在 "**挖掘模型**" 菜单中，选择 "**处理挖掘结构和所有模型**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-131">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="57bba-132">单击 **"是"** 将更新后的数据挖掘项目部署到服务器。</span><span class="sxs-lookup"><span data-stu-id="57bba-132">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="57bba-133">在 "**处理挖掘模型**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-133">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="57bba-134">单击 "**关闭**" 关闭 "**处理进度**" 对话框，然后再次单击 "**处理挖掘模型**" 对话框中的 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="57bba-134">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="57bba-135">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="57bba-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="57bba-136">&#40;中级数据挖掘教程为呼叫中心模型创建预测&#41;</span><span class="sxs-lookup"><span data-stu-id="57bba-136">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="57bba-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57bba-137">See Also</span></span>  
 [<span data-ttu-id="57bba-138">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="57bba-138">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
