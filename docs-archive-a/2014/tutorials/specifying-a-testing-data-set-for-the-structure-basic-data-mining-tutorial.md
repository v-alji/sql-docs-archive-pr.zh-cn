---
title: 为结构指定测试数据集 (数据挖掘基础教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c1430706a0ec2cd3ddc0eaee18d7001d05fefae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577148"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a><span data-ttu-id="b615e-102">为结构指定测试数据集（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b615e-102">Specifying a Testing Data Set for the Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b615e-103">在数据挖掘向导的最后几个屏幕上，将把数据拆分成测试集和定型集。</span><span class="sxs-lookup"><span data-stu-id="b615e-103">In the final few screens of the Data Mining Wizard you will split your data into a testing set and a training set.</span></span> <span data-ttu-id="b615e-104">随后您将命名您的结构并针对模型启用钻取。</span><span class="sxs-lookup"><span data-stu-id="b615e-104">You will then name your structure and enable drillthrough on the model.</span></span>  
  
## <a name="specifying-a-testing-set"></a><span data-ttu-id="b615e-105">指定测试集</span><span class="sxs-lookup"><span data-stu-id="b615e-105">Specifying a Testing Set</span></span>  
 <span data-ttu-id="b615e-106">在创建挖掘结构时将数据分成定型集和测试集，可以轻松地评估以后创建的挖掘模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="b615e-106">Separating data into training and testing sets when you create a mining structure makes it possible to easily assess the accuracy of the mining models that you create later.</span></span> <span data-ttu-id="b615e-107">有关测试集的详细信息，请参阅[定型和测试数据集](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="b615e-107">For more information on testing sets, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-specify-the-testing-set"></a><span data-ttu-id="b615e-108">指定测试集</span><span class="sxs-lookup"><span data-stu-id="b615e-108">To specify the testing set</span></span>  
  
1.  <span data-ttu-id="b615e-109">在 "**创建测试集**" 页上，对于要**测试的数据的百分比**，请保留的默认值 `30` 。</span><span class="sxs-lookup"><span data-stu-id="b615e-109">On the **Create Testing Set** page, for **Percentage of data for testing**, leave the default value of `30`.</span></span>  
  
2.  <span data-ttu-id="b615e-110">有关**测试数据集的最大事例数**，请键入 `1000` 。</span><span class="sxs-lookup"><span data-stu-id="b615e-110">For **Maximum number of cases in testing data set**, type `1000`.</span></span>  
  
3.  <span data-ttu-id="b615e-111">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b615e-111">Click **Next**.</span></span>  
  
## <a name="specifying-drillthrough"></a><span data-ttu-id="b615e-112">指定钻取</span><span class="sxs-lookup"><span data-stu-id="b615e-112">Specifying Drillthrough</span></span>  
 <span data-ttu-id="b615e-113">可以针对模型和结构启用钻取。</span><span class="sxs-lookup"><span data-stu-id="b615e-113">Drillthrough can be enabled on models and on structures.</span></span> <span data-ttu-id="b615e-114">此对话框中的复选框可对命名模型启用钻取功能。</span><span class="sxs-lookup"><span data-stu-id="b615e-114">The checkbox in this dialog box enables drillthrough on the named model.</span></span> <span data-ttu-id="b615e-115">在处理了该模型后，您将能够从定型数据中检索用于创建模型的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b615e-115">After the model has been processed,  you will be able to retrieve detailed information from the training data that were used to create the model.</span></span>  
  
 <span data-ttu-id="b615e-116">如果基础挖掘结构也已经配置为允许进行钻取，则可以从模型事例和挖掘结构返回详细信息（其中包括挖掘模型中所不包含的列）。</span><span class="sxs-lookup"><span data-stu-id="b615e-116">If the underlying mining structure has also been configured to allow drillthrough, you can retrieve detailed information from both the model cases and the mining structure, including columns that were not included in the mining model.</span></span> <span data-ttu-id="b615e-117">有关详细信息，请参阅 [钻取查询（数据挖掘）](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b615e-117">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a><span data-ttu-id="b615e-118">命名模型和结构并指定钻取</span><span class="sxs-lookup"><span data-stu-id="b615e-118">To name the model and structure and specify drillthrough</span></span>  
  
1.  <span data-ttu-id="b615e-119">在 "**完成向导**" 页上的 "**挖掘结构名称**" 中，键入 `Targeted Mailing` 。</span><span class="sxs-lookup"><span data-stu-id="b615e-119">On the **Completing the Wizard** page, in **Mining structure name**, type `Targeted Mailing`.</span></span>  
  
2.  <span data-ttu-id="b615e-120">在 "**挖掘模型名称**" 中，键入 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="b615e-120">In **Mining model name**, type `TM_Decision_Tree`.</span></span>  
  
3.  <span data-ttu-id="b615e-121">选中 "**允许钻取**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="b615e-121">Select the **Allow drill through** check box.</span></span>  
  
4.  <span data-ttu-id="b615e-122">查看**预览**窗格。</span><span class="sxs-lookup"><span data-stu-id="b615e-122">Review the **Preview** pane.</span></span> <span data-ttu-id="b615e-123">请注意，只会显示选定为**键**、**输入**或**可预测**列的列。</span><span class="sxs-lookup"><span data-stu-id="b615e-123">Notice that only those columns selected as **Key**, **Input** or **Predictable** are shown.</span></span> <span data-ttu-id="b615e-124">您选择的其他列（例如，AddressLine1）不能用于生成模型，但是将在基础结构中可用，您可以在处理和部署模型之后查询这些列。</span><span class="sxs-lookup"><span data-stu-id="b615e-124">The other columns you selected (e.g., AddressLine1) are not used for building the model but will be available in the underlying structure, and can be queried after the model is processed and deployed.</span></span>  
  
5.  <span data-ttu-id="b615e-125">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="b615e-125">Click **Finish**.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="b615e-126">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="b615e-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="b615e-127">指定数据类型和内容类型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b615e-127">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="b615e-128">下一课</span><span class="sxs-lookup"><span data-stu-id="b615e-128">Next Lesson</span></span>  
 [<span data-ttu-id="b615e-129">第 3 课：添加和处理模型</span><span class="sxs-lookup"><span data-stu-id="b615e-129">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="b615e-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b615e-130">See Also</span></span>  
 <span data-ttu-id="b615e-131">[为挖掘模型启用钻取](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="b615e-131">[Enable Drillthrough for a Mining Model](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span></span>  
 <span data-ttu-id="b615e-132">[数据挖掘 &#40;钻取查询&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b615e-132">[Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="b615e-133">在数据挖掘向导 &#40;指定定型数据&#41;</span><span class="sxs-lookup"><span data-stu-id="b615e-133">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
