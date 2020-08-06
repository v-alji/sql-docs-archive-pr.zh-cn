---
title: 浏览和清理数据 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: 154c711f735bcbb472e49654139fd16a036a0dd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577057"
---
# <a name="exploring-and-cleaning-data"></a><span data-ttu-id="9d51b-102">浏览和清除数据</span><span class="sxs-lookup"><span data-stu-id="9d51b-102">Exploring and Cleaning Data</span></span>
  <span data-ttu-id="9d51b-103">数据准备不仅在于清理数据。</span><span class="sxs-lookup"><span data-stu-id="9d51b-103">Data preparation is much more than data cleansing.</span></span> <span data-ttu-id="9d51b-104">请牢记，准备数据的方式还会影响最终解释结果的方式。</span><span class="sxs-lookup"><span data-stu-id="9d51b-104">Remember that how data is prepared also affects how results are interpreted in the end.</span></span> <span data-ttu-id="9d51b-105">数据准备涉及以下任务：</span><span class="sxs-lookup"><span data-stu-id="9d51b-105">Data preparation involves these tasks:</span></span>  
  
-   <span data-ttu-id="9d51b-106">探索和检查数据的分布。</span><span class="sxs-lookup"><span data-stu-id="9d51b-106">Exploring and checking the distribution of data.</span></span>  
  
-   <span data-ttu-id="9d51b-107">清除有错的记录并选择用于数据挖掘的列。</span><span class="sxs-lookup"><span data-stu-id="9d51b-107">Cleaning bad records, and choosing columns for data mining.</span></span>  
  
-   <span data-ttu-id="9d51b-108">适当地处理 null。</span><span class="sxs-lookup"><span data-stu-id="9d51b-108">Handling nulls appropriately.</span></span>  
  
-   <span data-ttu-id="9d51b-109">按不同的大块时间将值归入统计或聚合值。</span><span class="sxs-lookup"><span data-stu-id="9d51b-109">Binning values, or aggregating values by different chunks of time.</span></span>  
  
-   <span data-ttu-id="9d51b-110">添加标签以提高结果的可用性。</span><span class="sxs-lookup"><span data-stu-id="9d51b-110">Adding labels to improve the usability of the results.</span></span>  
  
-   <span data-ttu-id="9d51b-111">在必要时转换数据类型或将值分类以供分析。</span><span class="sxs-lookup"><span data-stu-id="9d51b-111">Converting data types or categorizing values where necessary for analysis.</span></span>  
  
 <span data-ttu-id="9d51b-112">如果您不熟悉数据建模，则建议您阅读相关主题 "[数据挖掘准备工作清单](checklist-of-preparation-for-data-mining.md)"。</span><span class="sxs-lookup"><span data-stu-id="9d51b-112">If you are new to data modeling, we recommend that you read the related topic, [Checklist of Preparation for Data Mining](checklist-of-preparation-for-data-mining.md).</span></span>  
  
## <a name="data-preparation-tools"></a><span data-ttu-id="9d51b-113">数据准备工具</span><span class="sxs-lookup"><span data-stu-id="9d51b-113">Data Preparation Tools</span></span>  
 <span data-ttu-id="9d51b-114">Office 数据挖掘外接程序包括以下用于数据清理和准备的工具：</span><span class="sxs-lookup"><span data-stu-id="9d51b-114">The Data Mining Add-ins for Office includes the following tools for data cleansing and preparation:</span></span>  
  
### <a name="explore-data"></a><span data-ttu-id="9d51b-115">浏览数据</span><span class="sxs-lookup"><span data-stu-id="9d51b-115">Explore Data</span></span>  
 <span data-ttu-id="9d51b-116">使用 "**浏览数据**" 向导执行以下数据准备任务：</span><span class="sxs-lookup"><span data-stu-id="9d51b-116">Use the **Explore Data** wizard for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="9d51b-117">预览数据并且标识在分析前必须修复的错误。</span><span class="sxs-lookup"><span data-stu-id="9d51b-117">Preview your data and identify errors that must be fixed prior to analysis.</span></span>  
  
-   <span data-ttu-id="9d51b-118">收集用于了解数据的平衡性和所需的清理任务的统计信息。</span><span class="sxs-lookup"><span data-stu-id="9d51b-118">Gather statistical information that is useful for understanding the balance of data and the required clean-up tasks.</span></span>  
  
-   <span data-ttu-id="9d51b-119">标识用于分析的列，并且对数据建模阶段进行计划。</span><span class="sxs-lookup"><span data-stu-id="9d51b-119">Identify columns that are useful for analysis, and plan the data modeling phase.</span></span>  
  
 <span data-ttu-id="9d51b-120">[浏览数据 &#40;SQL Server 数据挖掘外接程序&#41;](explore-data-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="9d51b-120">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="detect-and-handle-outliers"></a><span data-ttu-id="9d51b-121">检测和处理离群值</span><span class="sxs-lookup"><span data-stu-id="9d51b-121">Detect and Handle Outliers</span></span>  
 <span data-ttu-id="9d51b-122">**离群**值向导将图形中的值分布图形，有助于删除极值。</span><span class="sxs-lookup"><span data-stu-id="9d51b-122">The **Outliers** wizard graphs the distribution of values in your data and helps you remove extreme values.</span></span> <span data-ttu-id="9d51b-123">使用**离群**值工具执行以下数据准备任务：</span><span class="sxs-lookup"><span data-stu-id="9d51b-123">Use the **Outliers** tool for the following data preparation tasks:</span></span>  
  
-   <span data-ttu-id="9d51b-124">基于在数据中发现的模式确定单独值是否可靠。</span><span class="sxs-lookup"><span data-stu-id="9d51b-124">Determine whether individual values are reliable, based on patterns found in the data.</span></span>  
  
-   <span data-ttu-id="9d51b-125">检查异常值并且采取删除或替换它们等操作措施。</span><span class="sxs-lookup"><span data-stu-id="9d51b-125">Review unusual values and take action by deleting or replacing them.</span></span>  
  
-   <span data-ttu-id="9d51b-126">将某一模型的范围划定到特定的值范围。</span><span class="sxs-lookup"><span data-stu-id="9d51b-126">Scope a model to a specific range of values.</span></span> <span data-ttu-id="9d51b-127">例如，如果您知道在某一特定商店中具有离群值，则可以删除该值并且获取更好地预测其他商店的模型。</span><span class="sxs-lookup"><span data-stu-id="9d51b-127">For example, if you know that you have outliers at a particular store, you can eliminate that value and get a model that better predicts other stores.</span></span>  
  
 <span data-ttu-id="9d51b-128">"[离群值" &#40;SQL Server 数据挖掘外接&#41;](outliers-sql-server-data-mining-add-ins.md)"。</span><span class="sxs-lookup"><span data-stu-id="9d51b-128">[Outliers &#40;SQL Server Data Mining Add-ins&#41;](outliers-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="relabel-and-bin-data"></a><span data-ttu-id="9d51b-129">对数据进行重新标记和装箱</span><span class="sxs-lookup"><span data-stu-id="9d51b-129">Relabel and Bin Data</span></span>  
 <span data-ttu-id="9d51b-130">重新**标记**向导按值对数据进行分组，以便您可以更改数据的标签。</span><span class="sxs-lookup"><span data-stu-id="9d51b-130">The **Relabel** wizard groups data by values so that you can change the labels on the data.</span></span> <span data-ttu-id="9d51b-131">使用重新标记工具可执行以下数据准备任务：</span><span class="sxs-lookup"><span data-stu-id="9d51b-131">Use the Relabel tool for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="9d51b-132">将调查结果中使用的数值代码更改为该数值代码所表示的文本说明。</span><span class="sxs-lookup"><span data-stu-id="9d51b-132">Change numeric codes used in survey results to a text description of what the numeric code means.</span></span>  
  
     <span data-ttu-id="9d51b-133">例如，您可能替换数据条目（如将“性别 = 1”更换为“性别 = 女”）。</span><span class="sxs-lookup"><span data-stu-id="9d51b-133">For example, you might replace data entries such as Gender = 1 with Gender = Female.</span></span>  
  
-   <span data-ttu-id="9d51b-134">箱数据，通过创建组来表示数字范围。</span><span class="sxs-lookup"><span data-stu-id="9d51b-134">Bin data, by creating groups to represents number ranges.</span></span>  
  
     <span data-ttu-id="9d51b-135">例如，您可能想要将数字的收入列替换为**收入-中等**和**收入高**的标签。</span><span class="sxs-lookup"><span data-stu-id="9d51b-135">For example, you might want to replace an Income column of numbers with labels such as **Income - Moderate** and **Income - High**.</span></span>  
  
-   <span data-ttu-id="9d51b-136">将离散值折叠为类别。</span><span class="sxs-lookup"><span data-stu-id="9d51b-136">Collapse discrete values into categories.</span></span>  
  
     <span data-ttu-id="9d51b-137">例如，如果您有很多单个产品要检测购买模式，可能尝试将产品划分为更宽泛的类别。</span><span class="sxs-lookup"><span data-stu-id="9d51b-137">For example, if you have too many individual products to detect a pattern among purchases, you could try assigning products into broader categories.</span></span>  
  
 [<span data-ttu-id="9d51b-138">重新标记 SQL Server 数据挖掘外接 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="9d51b-138">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a><span data-ttu-id="9d51b-139">清理数据</span><span class="sxs-lookup"><span data-stu-id="9d51b-139">Cleanse Data</span></span>  
 <span data-ttu-id="9d51b-140">数据清理包括多种活动，其中大多数活动是由外接程序支持的</span><span class="sxs-lookup"><span data-stu-id="9d51b-140">Data cleansing encompasses a wide range of activities, most of which are supported by the add-ins</span></span>  
  
-   <span data-ttu-id="9d51b-141">标识 null 并确定它们是应更改为真实值还是作为 `Missing` 值处理。</span><span class="sxs-lookup"><span data-stu-id="9d51b-141">Identify nulls and determine whether they should be changed to a real value or handled as `Missing` values.</span></span>  
  
-   <span data-ttu-id="9d51b-142">检测缺失值，然后删除它们或归结相应值，例如均值、null 或其他值。</span><span class="sxs-lookup"><span data-stu-id="9d51b-142">Detect missing values, and then remove them, or impute an appropriate value, such as a mean, null, or other value.</span></span>  
  
 [<span data-ttu-id="9d51b-143">浏览数据挖掘外接 &#40;SQL Server 数据&#41;</span><span class="sxs-lookup"><span data-stu-id="9d51b-143">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="9d51b-144">重新标记 SQL Server 数据挖掘外接 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="9d51b-144">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="9d51b-145">从示例填充</span><span class="sxs-lookup"><span data-stu-id="9d51b-145">Fill From Example</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a><span data-ttu-id="9d51b-146">示例数据</span><span class="sxs-lookup"><span data-stu-id="9d51b-146">Sample Data</span></span>  
 <span data-ttu-id="9d51b-147">示例数据向导为定型模型和测试模型提供了两种创建平衡数据集的方法。</span><span class="sxs-lookup"><span data-stu-id="9d51b-147">The Sample Data wizard provides two methods for creating balanced data sets for training and testing models.</span></span>  
  
-   <span data-ttu-id="9d51b-148">**随机抽样。**</span><span class="sxs-lookup"><span data-stu-id="9d51b-148">**Random sampling.**</span></span> <span data-ttu-id="9d51b-149">使用此选项从较大的数据集提取有代表性的一组数据，以便用于定型或测试。</span><span class="sxs-lookup"><span data-stu-id="9d51b-149">Use this option to extract a representative set of data from a larger data set, for use in either training or testing.</span></span> <span data-ttu-id="9d51b-150">数据挖掘外接程序使用*分层采样*，以确保为每个被采样的变量获取均衡的值集。</span><span class="sxs-lookup"><span data-stu-id="9d51b-150">The Data Mining Add-ins use *stratified sampling* to ensure that a balanced set of values is obtained for each variable sampled.</span></span>  
  
-   <span data-ttu-id="9d51b-151">**过度抽样.**</span><span class="sxs-lookup"><span data-stu-id="9d51b-151">**Oversampling.**</span></span> <span data-ttu-id="9d51b-152">当您具有的数据比目标结果所需的数据少且需要加大该数据权重时，使用此选项。</span><span class="sxs-lookup"><span data-stu-id="9d51b-152">Use this option when you have less data than you would like for a target outcome, and need to weight that data more heavily.</span></span> <span data-ttu-id="9d51b-153">例如，欺诈可能相对较少，但是您可以对涉及欺诈的事例过度抽样以便获得建模所需的足够数据。</span><span class="sxs-lookup"><span data-stu-id="9d51b-153">For example, fraud might be relatively rare, but you can oversample cases involving fraud to get adequate data for modeling.</span></span>  
  
 <span data-ttu-id="9d51b-154">[SQL Server 数据挖掘外接 &#40;的示例数据&#41;](sample-data-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="9d51b-154">[Sample Data &#40;SQL Server Data Mining Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d51b-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d51b-155">See Also</span></span>  
 <span data-ttu-id="9d51b-156">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="9d51b-156">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="9d51b-157">[验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="9d51b-157">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="9d51b-158">&#40;Excel 数据挖掘外接程序部署和缩放挖掘模型&#41;</span><span class="sxs-lookup"><span data-stu-id="9d51b-158">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
