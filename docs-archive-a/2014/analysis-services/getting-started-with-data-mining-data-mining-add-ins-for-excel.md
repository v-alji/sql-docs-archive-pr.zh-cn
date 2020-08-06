---
title: 入门 Excel) 的数据挖掘 (数据挖掘外接程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
ms.openlocfilehash: 066fc72fa0570d56376cc73478a68e42d20ffbc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579161"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a><span data-ttu-id="0a73b-102">数据挖掘入门（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="0a73b-102">Getting Started with Data Mining (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="0a73b-103">数据挖掘是在数据中发现有意义的模式的过程。</span><span class="sxs-lookup"><span data-stu-id="0a73b-103">Data mining is the process of discovering meaningful patterns in data.</span></span> <span data-ttu-id="0a73b-104">数据挖掘是通过传统的商业智能来浏览和理解数据的过程的自然而然的补充。</span><span class="sxs-lookup"><span data-stu-id="0a73b-104">Data mining is a natural complement to the process of exploring and understanding your data through traditional BI.</span></span> <span data-ttu-id="0a73b-105">计算机算法可以处理大量数据，并发现以其他方式可能发现不了的模式和趋势。</span><span class="sxs-lookup"><span data-stu-id="0a73b-105">Machine algorithms can process very large amounts of data and discover patterns and trends that would otherwise be hidden.</span></span>  
  
 <span data-ttu-id="0a73b-106">若要进行数据挖掘，需要收集与特定问题相关的数据，例如 "谁是我的客户？"</span><span class="sxs-lookup"><span data-stu-id="0a73b-106">To do data mining, you collect data that is relevant to a specific question, such as "Who are my customers?"</span></span> <span data-ttu-id="0a73b-107">或者 "购买了哪些产品？"</span><span class="sxs-lookup"><span data-stu-id="0a73b-107">or "what products were purchased?"</span></span> <span data-ttu-id="0a73b-108">然后应用一种算法来查找数据中的统计相关性。</span><span class="sxs-lookup"><span data-stu-id="0a73b-108">and then apply an algorithm to find statistical correlations in the data.</span></span> <span data-ttu-id="0a73b-109">通过分析找到的模式和趋势存储为挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="0a73b-109">The patterns and trends found through analysis are stored as a mining model.</span></span> <span data-ttu-id="0a73b-110">然后可以将挖掘模型应用于业务方案（如以下方案）中的新数据：</span><span class="sxs-lookup"><span data-stu-id="0a73b-110">You can then apply the mining model to new data, in business scenarios such as these:</span></span>  
  
-   <span data-ttu-id="0a73b-111">使用过去的趋势预测下个季度的销售额、库存要求或客户满意度。</span><span class="sxs-lookup"><span data-stu-id="0a73b-111">Use past trends to forecast sales for the next quarter, inventory requirements, or customer satisfaction.</span></span>  
  
-   <span data-ttu-id="0a73b-112">应用当前客户知识以便勾画新客户的情形以及建议新产品或机遇。</span><span class="sxs-lookup"><span data-stu-id="0a73b-112">Apply knowledge of current customers to profile new customers and recommend new products or opportunities.</span></span>  
  
-   <span data-ttu-id="0a73b-113">查找过去事件中的相关性以便预测服务器故障或停机时间。</span><span class="sxs-lookup"><span data-stu-id="0a73b-113">Find correlations among past events to predict server failures or downtime.</span></span>  
  
-   <span data-ttu-id="0a73b-114">分析客户将会一起购买哪些产品并且使用这些信息来建议捆绑产品或计划产品摆放。</span><span class="sxs-lookup"><span data-stu-id="0a73b-114">Analyze which products customers purchase together and use the information to recommend bundles or plan product placement.</span></span>  
  
 <span data-ttu-id="0a73b-115">您选择的分析方法取决于您的目标。</span><span class="sxs-lookup"><span data-stu-id="0a73b-115">The method of analysis you choose depends on your goals.</span></span> <span data-ttu-id="0a73b-116">数据挖掘外接程序支持以下类型的分析：</span><span class="sxs-lookup"><span data-stu-id="0a73b-116">The Data Mining Add-ins support these types of analysis:</span></span>  
  
-   <span data-ttu-id="0a73b-117">监督的学习和无人监督的学习</span><span class="sxs-lookup"><span data-stu-id="0a73b-117">Supervised and unsupervised learning</span></span>  
  
-   <span data-ttu-id="0a73b-118">聚类分析（分段）</span><span class="sxs-lookup"><span data-stu-id="0a73b-118">Clustering (segmentation)</span></span>  
  
-   <span data-ttu-id="0a73b-119">因素分析，使用 Bayesian 和神经网络</span><span class="sxs-lookup"><span data-stu-id="0a73b-119">Factor analysis, using Bayesian and neural networks</span></span>  
  
-   <span data-ttu-id="0a73b-120">时序分析</span><span class="sxs-lookup"><span data-stu-id="0a73b-120">Time series analysis</span></span>  
  
-   <span data-ttu-id="0a73b-121">关联分析、建议和购物篮分析</span><span class="sxs-lookup"><span data-stu-id="0a73b-121">Association analysis, recommendations, and shopping basket analysis</span></span>  
  
-   <span data-ttu-id="0a73b-122">计分二进制结果</span><span class="sxs-lookup"><span data-stu-id="0a73b-122">Scoring binary outcomes</span></span>  
  
-   <span data-ttu-id="0a73b-123">线性回归</span><span class="sxs-lookup"><span data-stu-id="0a73b-123">Linear regression</span></span>  
  
 <span data-ttu-id="0a73b-124">此外，外接程序可为数据准备阶段提供帮助：数据选择、浏览和数据清理。</span><span class="sxs-lookup"><span data-stu-id="0a73b-124">In addition, the add-ins provide help the data preparation phase: data selection, exploration, and data cleansing.</span></span>  
  
## <a name="define-your-goal"></a><span data-ttu-id="0a73b-125">定义您的目标</span><span class="sxs-lookup"><span data-stu-id="0a73b-125">Define Your Goal</span></span>  
 <span data-ttu-id="0a73b-126">在开始之前，请用一点时间来考虑实际需要回答的问题。</span><span class="sxs-lookup"><span data-stu-id="0a73b-126">Before you get started, take a minute to consider the question you really want to answer.</span></span> <span data-ttu-id="0a73b-127">探索本身固然很好，但如果您要将找到的内容应用于新数据，则应该能够明确指出您预期模型要达到什么效果，以及如何衡量模型是否实现您的目标。</span><span class="sxs-lookup"><span data-stu-id="0a73b-127">Exploration for its own sake is illuminating, but if you want to apply your findings to new data, you should be able to state clearly what you expect the model to produce, and how you will measure whether the model accomplishes your goals.</span></span>  
  
 <span data-ttu-id="0a73b-128">例如，不是 "查找新客户" 的目标，而是将目标阐明为更具体的内容，如 "确定可能购买产品的客户的人口统计信息，概率至少为 65%"。</span><span class="sxs-lookup"><span data-stu-id="0a73b-128">For example, rather than a goal of "finding new customers", clarify your objective to something more concrete, such as "identify the demographics of customers that are likely to buy our product, with a probability of at least 65%".</span></span>  
  
-   <span data-ttu-id="0a73b-129">您的数据集应包含至少一个可用于定型和预测的 "result" 属性。</span><span class="sxs-lookup"><span data-stu-id="0a73b-129">Your dataset should contain at least one "result" attribute that you can use for training and prediction.</span></span> <span data-ttu-id="0a73b-130">如果没有此类属性，可以手动标记一些定型数据，也可以使用其他列创建针对该结果的替代数据。</span><span class="sxs-lookup"><span data-stu-id="0a73b-130">If there is no such attribute, you can manually label some training data, or use other columns to create a proxy for the outcome.</span></span>  
  
     <span data-ttu-id="0a73b-131">例如，如果要预测 "最佳潜在客户"，应事先应用某种业务规则来标记现有客户，以便数据挖掘可以从您提供的示例中学习。</span><span class="sxs-lookup"><span data-stu-id="0a73b-131">For example, if you want to predict "the best prospects", you should apply some business rule beforehand to label existing customers, so that data mining can learn from the examples you provide.</span></span>  
  
-   <span data-ttu-id="0a73b-132">如果要处理随时间变化的值，并预测将来的趋势，应考虑所需结果的粒度。</span><span class="sxs-lookup"><span data-stu-id="0a73b-132">If you are working with a value that changes over time, and want to predict future trends, think about the granularity of the results you need.</span></span> <span data-ttu-id="0a73b-133">您是否想要按月、天或年进行预测？</span><span class="sxs-lookup"><span data-stu-id="0a73b-133">Do you want predictions for a month, day, or yearly basis?</span></span> <span data-ttu-id="0a73b-134">必须使用相同单位对您要预测的数据进行分析。</span><span class="sxs-lookup"><span data-stu-id="0a73b-134">Your data has to be analyzed using the same units that you want to predict.</span></span>  
  
     <span data-ttu-id="0a73b-135">使用循环模式时，如果不能使用每日数据获得良好的结果，请尝试使用不同的时间段，或尝试使用工作日、月甚至假期。</span><span class="sxs-lookup"><span data-stu-id="0a73b-135">With cyclical patterns, if you don't get good results with daily data, try different time slices, or try using week days, months, or even holidays.</span></span>  
  
-   <span data-ttu-id="0a73b-136">在启动向导以便在您的数据中找到新关联之前，再看一下您的数据并且考虑在数据集中可能存在何种现有关系。</span><span class="sxs-lookup"><span data-stu-id="0a73b-136">Before you launch a wizard to find new correlations in your data, take one more look at your data and consider what sort of existing relationships might be present in the dataset.</span></span> <span data-ttu-id="0a73b-137">是否有令人混淆的变量？</span><span class="sxs-lookup"><span data-stu-id="0a73b-137">Are there confounding variables?</span></span> <span data-ttu-id="0a73b-138">是否有重复项或代理？</span><span class="sxs-lookup"><span data-stu-id="0a73b-138">Are there duplicates or proxies?</span></span>  
  
-   <span data-ttu-id="0a73b-139">将通过哪些指标计算模型的成功？</span><span class="sxs-lookup"><span data-stu-id="0a73b-139">What are the metrics by which the model's success will be evaluated?</span></span> <span data-ttu-id="0a73b-140">您如何知道该模型 "足够好" 呢？</span><span class="sxs-lookup"><span data-stu-id="0a73b-140">How will you know that the model is "good enough"?</span></span>  
  
-   <span data-ttu-id="0a73b-141">您要通过数据挖掘模型进行预测，还是仅仅查找关注的模式和关联？</span><span class="sxs-lookup"><span data-stu-id="0a73b-141">Do you want to make predictions from the data mining model or just look for interesting patterns and associations?</span></span>  
  
## <a name="explore-your-data-and-explore-the-model"></a><span data-ttu-id="0a73b-142">浏览数据并且浏览模型</span><span class="sxs-lookup"><span data-stu-id="0a73b-142">Explore Your Data and Explore the Model</span></span>  
 <span data-ttu-id="0a73b-143">可能您已充分了解了数据和域。</span><span class="sxs-lookup"><span data-stu-id="0a73b-143">Perhaps you already thoroughly understand the data and the domain.</span></span> <span data-ttu-id="0a73b-144">即便如此，也应该花费一些时间来通过建模剖析您的数据。</span><span class="sxs-lookup"><span data-stu-id="0a73b-144">Even if you do, you should take some time to profile your data with modeling in mind.</span></span>  
  
 <span data-ttu-id="0a73b-145">花点时间查看值的分布，并且确定缺少值或占位符之类的潜在问题。</span><span class="sxs-lookup"><span data-stu-id="0a73b-145">Take a minute to view the distribution of values, and identify potential problems such as missing values or placeholders.</span></span>  
  
 <span data-ttu-id="0a73b-146">如果您计划针对某个数据集执行数据挖掘，而该数据集很大或很复杂，并且您无法使用其他方法对其进行分析，请考虑采样或数据缩减。</span><span class="sxs-lookup"><span data-stu-id="0a73b-146">If you are planning to perform data mining against a data set that was so large or complex that you couldn't analyze it with other methods, consider sampling or data reduction.</span></span>  
  
-   <span data-ttu-id="0a73b-147">数据是如何分布的？</span><span class="sxs-lookup"><span data-stu-id="0a73b-147">How is the data distributed?</span></span>  
  
-   <span data-ttu-id="0a73b-148">列如何关联，或者如果有多个表，则表如何关联？</span><span class="sxs-lookup"><span data-stu-id="0a73b-148">How are the columns related, or if there are multiple tables, how are the tables related?</span></span>  
  
-   <span data-ttu-id="0a73b-149">是否缺少任何值？</span><span class="sxs-lookup"><span data-stu-id="0a73b-149">Are any values missing?</span></span> <span data-ttu-id="0a73b-150">是否有需要转换或预处理的值？</span><span class="sxs-lookup"><span data-stu-id="0a73b-150">Are there values that need conversion or preprocessing?</span></span>  
  
-   <span data-ttu-id="0a73b-151">数据主要是文本、数字还是两者的混合？</span><span class="sxs-lookup"><span data-stu-id="0a73b-151">Is the data mostly text, mostly numbers, or a mix?</span></span>  
  
-   <span data-ttu-id="0a73b-152">是否有足够的数据来支持目标结果的分析？</span><span class="sxs-lookup"><span data-stu-id="0a73b-152">Do you have enough data to support analysis of the targeted outcomes?</span></span> <span data-ttu-id="0a73b-153">如果要分析产品之间的关联，可能需要更多大量数据。</span><span class="sxs-lookup"><span data-stu-id="0a73b-153">If you are analyzing associations among products, you might need lots more data.</span></span> <span data-ttu-id="0a73b-154">如果您要预测二进制结果，可以使用更少数据得到结果，假定数据集是均衡的。</span><span class="sxs-lookup"><span data-stu-id="0a73b-154">If you are predicting a binary outcome, you can get by with much less, assuming the dataset is balanced.</span></span>  
  
 <span data-ttu-id="0a73b-155">在完成您的模型之后，应花一些时间来查看结果并且确定修改数据或者获得更好结果的方法。</span><span class="sxs-lookup"><span data-stu-id="0a73b-155">After your model is complete, take some time to review the results and identify ways to amend the data or get better results.</span></span> <span data-ttu-id="0a73b-156">您的第一个模型就能够解决所有问题的情形十分罕见。</span><span class="sxs-lookup"><span data-stu-id="0a73b-156">It is exceedingly rare that your first model provides all the answers.</span></span> <span data-ttu-id="0a73b-157">数据挖掘通常是一个迭代的过程。</span><span class="sxs-lookup"><span data-stu-id="0a73b-157">Data mining is typically an iterative process.</span></span>  
  
 <span data-ttu-id="0a73b-158">尝试以不同方式装箱数据或添加新列时，请记住使用**文档模型**向导捕获每个模型的元数据和结果的快照。</span><span class="sxs-lookup"><span data-stu-id="0a73b-158">As you try binning your data different ways, or adding new columns, remember to use the **Document Model** wizard to capture a snapshot of each model's metadata and results.</span></span> <span data-ttu-id="0a73b-159">具有记录将会更便于跟踪探索进度。</span><span class="sxs-lookup"><span data-stu-id="0a73b-159">Having a record will make it easier to track progress in your exploration.</span></span>  
  
 [<span data-ttu-id="0a73b-160">浏览和清除数据</span><span class="sxs-lookup"><span data-stu-id="0a73b-160">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a><span data-ttu-id="0a73b-161">验证您的模型</span><span class="sxs-lookup"><span data-stu-id="0a73b-161">Validate Your Model</span></span>  
 <span data-ttu-id="0a73b-162">在您运行每个向导或工具时，算法会分析数据内容并且确定在统计上有效的模式是否存在。</span><span class="sxs-lookup"><span data-stu-id="0a73b-162">As you run each wizard or tool, the algorithm analyzes the contents of the data and determines whether a statistically valid pattern exists.</span></span> <span data-ttu-id="0a73b-163">如果算法找不到有效模式，你将收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="0a73b-163">If the algorithm cannot find valid patterns, you'll get an error message.</span></span> <span data-ttu-id="0a73b-164">但是，即使已成功创建模型，你也需要测试模型，以确定它是否验证了假设。</span><span class="sxs-lookup"><span data-stu-id="0a73b-164">However, even if a model was successfully created, you'll want to test the model to see if it validates your assumptions.</span></span> <span data-ttu-id="0a73b-165">您可以使用 "[准确性图表" &#40;SQL Server 数据挖掘外接程序&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)或[交叉验证 &#40;SQL Server 数据挖掘外](cross-validation-sql-server-data-mining-add-ins.md)接程序&#41;生成模型质量的统计度量值。</span><span class="sxs-lookup"><span data-stu-id="0a73b-165">You can use tools such as the [Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) or [Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md) to produce statistical measures of model quality.</span></span>  
  
 <span data-ttu-id="0a73b-166">在评估您的首个模型的效果时，向自己提出如下问题：</span><span class="sxs-lookup"><span data-stu-id="0a73b-166">As you assess the results of your first model, ask yourself questions such as these:</span></span>  
  
-   <span data-ttu-id="0a73b-167">发现了何种类型的模式？</span><span class="sxs-lookup"><span data-stu-id="0a73b-167">What kinds of patterns were found?</span></span> <span data-ttu-id="0a73b-168">概率和支持值是什么？</span><span class="sxs-lookup"><span data-stu-id="0a73b-168">What are the probabilities and support values?</span></span>  
  
-   <span data-ttu-id="0a73b-169">我们的趋势预测是否正确，或者是否有出人意料的关联？</span><span class="sxs-lookup"><span data-stu-id="0a73b-169">Were our guesses about trends correct, or were there surprising correlations?</span></span>  
  
-   <span data-ttu-id="0a73b-170">我们是否收集了足够的数据？</span><span class="sxs-lookup"><span data-stu-id="0a73b-170">Did we collect enough data?</span></span> <span data-ttu-id="0a73b-171">将数据装箱是否会产生更清晰的模式？</span><span class="sxs-lookup"><span data-stu-id="0a73b-171">Would binning the data produce clearer patterns?</span></span>  
  
-   <span data-ttu-id="0a73b-172">数据集是否平衡？</span><span class="sxs-lookup"><span data-stu-id="0a73b-172">Is the data set balanced?</span></span> <span data-ttu-id="0a73b-173">交叉验证可测试数据的代表性。</span><span class="sxs-lookup"><span data-stu-id="0a73b-173">Cross-validation can test the representativeness of your data.</span></span>  
  
 [<span data-ttu-id="0a73b-174">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="0a73b-174">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
 [<span data-ttu-id="0a73b-175">Excel 数据挖掘客户端 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="0a73b-175">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="0a73b-176">选择模型</span><span class="sxs-lookup"><span data-stu-id="0a73b-176">Choosing a Model</span></span>](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a><span data-ttu-id="0a73b-177">探索和优化</span><span class="sxs-lookup"><span data-stu-id="0a73b-177">Explore and Refine</span></span>  
 <span data-ttu-id="0a73b-178">如果模型看似有效，则您可以使用它进行预测、提出建议、推导深层次关系或计划业务策略。</span><span class="sxs-lookup"><span data-stu-id="0a73b-178">If the model appears to be valid, you can use the model for prediction, recommendation, deriving insights, or planning business strategies..</span></span>  
  
-   <span data-ttu-id="0a73b-179">使用 Data Mining Client for Excel 中的数据挖掘浏览器可以探索模型以及与模型交互。</span><span class="sxs-lookup"><span data-stu-id="0a73b-179">Use the data mining browser in the Data Mining Client for Excel to explore and interact with the model.</span></span>  
  
-   <span data-ttu-id="0a73b-180">使用 Excel 可对结果进行重新排列和筛选。</span><span class="sxs-lookup"><span data-stu-id="0a73b-180">Use Excel to rearrange and filter the results.</span></span>  
  
-   <span data-ttu-id="0a73b-181">使用 Visio 可创建演示文稿并且突出显示在数据中找到的关系。</span><span class="sxs-lookup"><span data-stu-id="0a73b-181">Use Visio to create presentations and highlight the relationships found in the data.</span></span>  
  
 <span data-ttu-id="0a73b-182">通常，分析的第一个结果是您知道了改进分析的方法，或意识到需要获取新的更好的数据。</span><span class="sxs-lookup"><span data-stu-id="0a73b-182">Often, the first result of analysis is that you see ways to improve the analysis, or realize that you need to get new and better data.</span></span> <span data-ttu-id="0a73b-183">因为使用 Excel 数据挖掘外接程序创建的模型可以保存到 Analysis Service 实例，使用新数据更新模型相对容易，并继续优化和重用成功的模型。</span><span class="sxs-lookup"><span data-stu-id="0a73b-183">Because the models that you create using the Data Mining Add-ins for Excel can be saved to an instance of Analysis Service, it is relatively easy to update the model with new data, and continue to refine and re-use successful models.</span></span>  
  
 <span data-ttu-id="0a73b-184">数据挖掘模型的一个重要用途是创建预测和建议。</span><span class="sxs-lookup"><span data-stu-id="0a73b-184">An important use of data mining models is to create predictions and recommendations.</span></span> <span data-ttu-id="0a73b-185">Excel 数据挖掘外接程序包括一些工具，这些工具使得用户可以轻松生成很复杂的预测查询，以将发现的模式转换为可操作的结果。</span><span class="sxs-lookup"><span data-stu-id="0a73b-185">The Data Mining Add-ins for Excel includes tools that make it easy to generate even complex prediction queries, for converting insights into actionable results.</span></span> <span data-ttu-id="0a73b-186">所有这些工具都可以与 Excel 完全集成。</span><span class="sxs-lookup"><span data-stu-id="0a73b-186">All of these tools are fully integrated with Excel.</span></span>  
  
 [<span data-ttu-id="0a73b-187">查看模型 &#40;Office 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="0a73b-187">Viewing Models &#40;Data Mining Add-ins for Office&#41;</span></span>](viewing-models-data-mining-add-ins-for-office.md)  
  
 [<span data-ttu-id="0a73b-188">验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="0a73b-188">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="0a73b-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a73b-189">See Also</span></span>  
 <span data-ttu-id="0a73b-190">[Office 数据挖掘外接程序中包含的内容](what-s-included-in-the-data-mining-add-ins-for-office.md) </span><span class="sxs-lookup"><span data-stu-id="0a73b-190">[What's Included in the Data Mining Add-Ins for Office](what-s-included-in-the-data-mining-add-ins-for-office.md) </span></span>  
 [<span data-ttu-id="0a73b-191">用于 Excel 的数据挖掘外接程序的技术参考 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="0a73b-191">Technical Reference &#40;Data Mining Add-ins for Excel&#41;</span></span>](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
