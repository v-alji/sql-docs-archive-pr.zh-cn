---
title: " (Excel) 数据挖掘外接程序的分类向导 |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
ms.openlocfilehash: b82fc98df10ae2e6754a378dacea108f9f3379ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579264"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="dcce0-102">分类向导（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="dcce0-102">Classify Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="dcce0-103">![“数据挖掘”功能区中的分类向导](media/dmc-classify.gif "“数据挖掘”功能区中的分类向导")</span><span class="sxs-lookup"><span data-stu-id="dcce0-103">![Classify wizard in Data Mining ribbon](media/dmc-classify.gif "Classify wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="dcce0-104">**分类**向导可帮助您基于 excel 表、excel 区域或外部数据源中的现有数据生成分类模型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-104">The **Classify** wizard helps you build a classification model based on existing data in an Excel table, an Excel range, or an external data source.</span></span>  
  
 <span data-ttu-id="dcce0-105">分类模型提取数据中表示相似性的模式，并帮助您基于值的分组进行预测。</span><span class="sxs-lookup"><span data-stu-id="dcce0-105">A classification model extracts patterns in your data that indicate similarities and helps you make predictions based on groupings of values.</span></span> <span data-ttu-id="dcce0-106">例如，分类模型可用于根据收入或消费模式来预测风险。</span><span class="sxs-lookup"><span data-stu-id="dcce0-106">For example, a classification model might be used to predict risk based on income or spending patterns.</span></span>  
  
## <a name="using-the-classify-wizard"></a><span data-ttu-id="dcce0-107">使用分类向导</span><span class="sxs-lookup"><span data-stu-id="dcce0-107">Using the Classify Wizard</span></span>  
  
1.  <span data-ttu-id="dcce0-108">在 "**数据挖掘**" 功能区中，单击 "**分类**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="dcce0-108">In the **Data Mining** ribbon, click **Classify**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="dcce0-109">在 "**选择源数据**" 页中，选择要分析的数据。</span><span class="sxs-lookup"><span data-stu-id="dcce0-109">In the **Select Source Data** page, choose the data to analyze.</span></span>  
  
     <span data-ttu-id="dcce0-110">此向导支持多种数据：Excel 表、Excel 区域和外部数据源。</span><span class="sxs-lookup"><span data-stu-id="dcce0-110">This wizard supports multiple kinds of data: Excel tables, Excel ranges, and external data sources.</span></span> <span data-ttu-id="dcce0-111">对于外部数据，可以将其添加到 Excel 中，也可以在 Analysis Services 数据源中选择一组表或视图。</span><span class="sxs-lookup"><span data-stu-id="dcce0-111">With external data, you can either add it into Excel, or choose a set of tables or views in an Analysis Services data source.</span></span> <span data-ttu-id="dcce0-112">还可以添加表并更改列以创建临时数据源。</span><span class="sxs-lookup"><span data-stu-id="dcce0-112">You can also add tables and change columns to create ad hoc data sources.</span></span>  
  
3.  <span data-ttu-id="dcce0-113">在 "**分类**" 页上，选择要分类的列。</span><span class="sxs-lookup"><span data-stu-id="dcce0-113">On the **Classification** page, choose the column that you want to classify.</span></span>  
  
     <span data-ttu-id="dcce0-114">查看列表中的列、**输入列**，然后取消选择具有唯一值的任何列，因此不能用于创建模式，如 ID 号、客户名称等。</span><span class="sxs-lookup"><span data-stu-id="dcce0-114">Review the columns in the list, **Input columns**, and deselect any columns that have unique values and thus aren't useful for creating patterns, such as ID numbers, customer names, and so on.</span></span> <span data-ttu-id="dcce0-115">您还应删除与可分类列基本重复的列。</span><span class="sxs-lookup"><span data-stu-id="dcce0-115">You should also remove columns that essentially duplicate the classifiable column.</span></span>  
  
     <span data-ttu-id="dcce0-116">举例来说，如果您要分类产品类别的预测，则在有已知业务规则时应排除子类别字段，否则此规则的强度可能会阻止您发现其他关联。</span><span class="sxs-lookup"><span data-stu-id="dcce0-116">For example, if you are classifying predicting the category of a product, you should exclude the subcategory field if there is a known business rule, or else the strength of that rule might prevent you from discovering other correlations.</span></span>  
  
4.  <span data-ttu-id="dcce0-117">（可选）单击 "**参数**" 更改算法参数，并自定义聚类分析模型的行为。</span><span class="sxs-lookup"><span data-stu-id="dcce0-117">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="dcce0-118">在 "将**数据拆分为定型集和测试集**" 页中，指定要保留多少数据用于测试。</span><span class="sxs-lookup"><span data-stu-id="dcce0-118">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="dcce0-119">剩余的数据始终用于定型模型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-119">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="dcce0-120">默认设置为 30% 的测试数据和 70% 的定型数据。</span><span class="sxs-lookup"><span data-stu-id="dcce0-120">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="dcce0-121">在 "**完成**" 页上，为数据集和模型提供描述性名称，并设置以下选项来控制使用已完成模型的方式：</span><span class="sxs-lookup"><span data-stu-id="dcce0-121">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="dcce0-122">**浏览模型**。</span><span class="sxs-lookup"><span data-stu-id="dcce0-122">**Browse model**.</span></span> <span data-ttu-id="dcce0-123">如果选择此选项，向导处理完模型后就会立即打开 "**浏览**" 窗口，以帮助您浏览结果。</span><span class="sxs-lookup"><span data-stu-id="dcce0-123">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="dcce0-124">查看器的内容取决于您建立的模型的类型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-124">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="dcce0-125">有关详细信息，请参阅[浏览决策树模型](browsing-a-decision-trees-model.md)和[浏览神经网络模型](browsing-a-neural-network-model.md)。</span><span class="sxs-lookup"><span data-stu-id="dcce0-125">For more information, see [Browsing a Decision Trees Model](browsing-a-decision-trees-model.md) and [Browsing a Neural Network Model](browsing-a-neural-network-model.md).</span></span>  
  
    -   <span data-ttu-id="dcce0-126">**启用钻取**。</span><span class="sxs-lookup"><span data-stu-id="dcce0-126">**Enable drillthrough**.</span></span> <span data-ttu-id="dcce0-127">选择此选项可以查看已完成模型中的基础数据。</span><span class="sxs-lookup"><span data-stu-id="dcce0-127">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="dcce0-128">此选项仅在建立决策树模型时可用。</span><span class="sxs-lookup"><span data-stu-id="dcce0-128">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="dcce0-129">**使用临时模型**。</span><span class="sxs-lookup"><span data-stu-id="dcce0-129">**Use temporary model**.</span></span> <span data-ttu-id="dcce0-130">如果您选择此选项，模型将不会被保存到服务器。</span><span class="sxs-lookup"><span data-stu-id="dcce0-130">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="dcce0-131">在您关闭 Excel 时，临时模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="dcce0-131">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-classification-models"></a><span data-ttu-id="dcce0-132">有关分类模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="dcce0-132">More About Classification Models</span></span>  
 <span data-ttu-id="dcce0-133">在 "**算法参数**" 对话框中，你还可以从 Analysis Services 中提供的以下算法中选择分类方法：</span><span class="sxs-lookup"><span data-stu-id="dcce0-133">In the **Algorithm Parameters** dialog box, you can also choose the classification method from among these algorithms provided in Analysis Services:</span></span>  
  
-   <span data-ttu-id="dcce0-134">Microsoft 决策树</span><span class="sxs-lookup"><span data-stu-id="dcce0-134">Microsoft Decision Tree</span></span>  
  
-   <span data-ttu-id="dcce0-135">Microsoft 逻辑回归</span><span class="sxs-lookup"><span data-stu-id="dcce0-135">Microsoft Logistic Regression</span></span>  
  
-   <span data-ttu-id="dcce0-136">Microsoft Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="dcce0-136">Microsoft Naïve Bayes</span></span>  
  
-   <span data-ttu-id="dcce0-137">Microsoft 神经网络</span><span class="sxs-lookup"><span data-stu-id="dcce0-137">Microsoft Neural Network</span></span>  
  
 <span data-ttu-id="dcce0-138">虽然多种算法可能会产生类似的结果，但是它们分析数据的方式不同，因此，我们建议尝试几种算法并比较结果。</span><span class="sxs-lookup"><span data-stu-id="dcce0-138">Although the algorithms might yield similar results, they analyze the data differently, so we recommend trying several algorithms and comparing the results.</span></span> <span data-ttu-id="dcce0-139">默认方法是 Microsoft 决策树。</span><span class="sxs-lookup"><span data-stu-id="dcce0-139">The default method is Microsoft Decision Trees.</span></span>  
  
 <span data-ttu-id="dcce0-140">在 "**参数**" 列表中，您可以更改高级选项，这些选项取决于您选择的算法类型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-140">In the **Parameters** list, you can change advanced options, which depend on the type of algorithm you choose.</span></span> <span data-ttu-id="dcce0-141">每种算法的参数在 SQL Server 联机丛书中有更详细的说明。</span><span class="sxs-lookup"><span data-stu-id="dcce0-141">The parameters for each algorithm are described in more detail in SQL Server Books Online.</span></span>  
  
 [<span data-ttu-id="dcce0-142">Microsoft 决策树算法技术参考</span><span class="sxs-lookup"><span data-stu-id="dcce0-142">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="dcce0-143">Microsoft 逻辑回归算法技术参考</span><span class="sxs-lookup"><span data-stu-id="dcce0-143">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="dcce0-144">Microsoft Naive Bayes 算法技术参考</span><span class="sxs-lookup"><span data-stu-id="dcce0-144">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="dcce0-145">Microsoft 神经网络算法技术参考</span><span class="sxs-lookup"><span data-stu-id="dcce0-145">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="dcce0-146">要求</span><span class="sxs-lookup"><span data-stu-id="dcce0-146">Requirements</span></span>  
 <span data-ttu-id="dcce0-147">若要使用**分类**向导，必须连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="dcce0-147">To use the **Classify** wizard, you must be connected to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="dcce0-148">有关如何创建连接的信息，请参阅[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="dcce0-148">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcce0-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcce0-149">See Also</span></span>  
 [<span data-ttu-id="dcce0-150">创建数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="dcce0-150">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
