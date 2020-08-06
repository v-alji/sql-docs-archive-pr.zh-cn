---
title: " (中级数据挖掘教程) 修改和处理市场篮模型 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 369de98e944c5ccf5d06ef61eaa16c06bb864e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577157"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="35c11-102">修改和处理市场篮模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="35c11-102">Modifying and Processing the Market Basket Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="35c11-103">在处理创建的关联挖掘模型之前，必须更改以下两个参数的默认值：*支持*和*概率*。</span><span class="sxs-lookup"><span data-stu-id="35c11-103">Before you process the association mining model that you created, you must change the default values of two of the parameters: *Support* and *Probability*.</span></span>  
  
-   <span data-ttu-id="35c11-104">*支持*定义规则在被视为有效前必须存在的事例的百分比。</span><span class="sxs-lookup"><span data-stu-id="35c11-104">*Support* defines the percentage of cases in which a rule must exist before it is considered valid.</span></span> <span data-ttu-id="35c11-105">您将指定规则必须至少是在百分之一的事例中发现的。</span><span class="sxs-lookup"><span data-stu-id="35c11-105">You will specify that a rule must be found in at least 1 percent of cases.</span></span>  
  
-   <span data-ttu-id="35c11-106">*概率*定义了关联在被视为有效之前必须具备的可能性。</span><span class="sxs-lookup"><span data-stu-id="35c11-106">*Probability* defines how likely an association must be before it is considered valid.</span></span> <span data-ttu-id="35c11-107">您将认为任何关联都必须具有至少百分之十的可能性。</span><span class="sxs-lookup"><span data-stu-id="35c11-107">You will consider any association with a probability of at least 10 percent.</span></span>  
  
 <span data-ttu-id="35c11-108">有关增加或降低支持和概率的影响的详细信息，请参阅[Microsoft 关联算法技术参考](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="35c11-108">For more information about the effects of increasing or decreasing support and probability, see [Microsoft Association Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="35c11-109">在定义了**关联**挖掘模型的结构和参数后，您将处理该模型。</span><span class="sxs-lookup"><span data-stu-id="35c11-109">After you have defined the structure and parameters for the **Association** mining model, you will process the model.</span></span>  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a><span data-ttu-id="35c11-110">调整 Association 模型的参数</span><span class="sxs-lookup"><span data-stu-id="35c11-110">To adjust the parameters of the Association model</span></span>  
  
1.  <span data-ttu-id="35c11-111">打开数据挖掘设计器的 "**挖掘模型**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="35c11-111">Open the **Mining Models** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="35c11-112">在设计器中右键单击网格中的 "**关联**" 列，然后选择 **"设置算法参数" 以打开 "算法参数"** 对话框。</span><span class="sxs-lookup"><span data-stu-id="35c11-112">Right-click the **Association** column in the grid in the designer and select **Set Algorithm Parameters to open the Algorithm Parameters** dialog box.</span></span>  
  
3.  <span data-ttu-id="35c11-113">在 "**算法参数**" 对话框的 "**值**" 列中，设置以下参数：</span><span class="sxs-lookup"><span data-stu-id="35c11-113">In the **Value** column of the **Algorithm Parameters** dialog box, set the following parameters:</span></span>  
  
     <span data-ttu-id="35c11-114">MINIMUM_PROBABILITY = 0.1</span><span class="sxs-lookup"><span data-stu-id="35c11-114">MINIMUM_PROBABILITY = 0.1</span></span>  
  
     <span data-ttu-id="35c11-115">MINIMUM_SUPPORT = 0.01</span><span class="sxs-lookup"><span data-stu-id="35c11-115">MINIMUM_SUPPORT = 0.01</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a><span data-ttu-id="35c11-116">处理挖掘模型</span><span class="sxs-lookup"><span data-stu-id="35c11-116">To process the mining model</span></span>  
  
1.  <span data-ttu-id="35c11-117">在的 "**挖掘模型**" 菜单上 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，选择 "**处理挖掘结构和所有模型"。**</span><span class="sxs-lookup"><span data-stu-id="35c11-117">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models.**</span></span>  
  
2.  <span data-ttu-id="35c11-118">如果出现警告，询问您是否要生成和部署项目，请单击 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="35c11-118">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
     <span data-ttu-id="35c11-119">"**处理挖掘结构-关联**" 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="35c11-119">The **Process Mining Structure - Association** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="35c11-120">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="35c11-120">Click **Run**.</span></span>  
  
     <span data-ttu-id="35c11-121">"**处理进度**" 对话框将打开以显示有关模型处理的信息。</span><span class="sxs-lookup"><span data-stu-id="35c11-121">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="35c11-122">处理新的结构和模型可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="35c11-122">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="35c11-123">处理完成后，单击 "**关闭**" 退出 "**处理进度**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="35c11-123">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="35c11-124">再次单击 "**关闭**" 以退出 "**处理挖掘结构-关联**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="35c11-124">Click **Close** again to exit the **Process Mining Structure - Association** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="35c11-125">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="35c11-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="35c11-126">&#40;中级数据挖掘教程了解市场篮模型&#41;</span><span class="sxs-lookup"><span data-stu-id="35c11-126">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="35c11-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35c11-127">See Also</span></span>  
 [<span data-ttu-id="35c11-128">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="35c11-128">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
