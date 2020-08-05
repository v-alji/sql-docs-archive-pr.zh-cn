---
title: 数据挖掘准备工作清单 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: e37b1adb6aebe5d5f8fd23f5289f52425f752a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579899"
---
# <a name="checklist-of-preparation-for-data-mining"></a><span data-ttu-id="1e295-102">数据挖掘准备清单</span><span class="sxs-lookup"><span data-stu-id="1e295-102">Checklist of Preparation for Data Mining</span></span>
  <span data-ttu-id="1e295-103">虽然数据挖掘外接程序让创建和试验模型变得简单有趣，但在需要可重复、可操作的结果时，必须有足够的时间制定基本业务需求以及获取和准备数据。</span><span class="sxs-lookup"><span data-stu-id="1e295-103">Although the Data Mining Add-ins make it fairly easy and fun to create and experiment with models, when you need to get repeatable, actionable results, you must allow adequate time for formulating basic business requirements, and for obtaining and preparing data.</span></span> <span data-ttu-id="1e295-104">本节提供了一个清单，可帮助对您的调查进行计划，并且描述常见问题。</span><span class="sxs-lookup"><span data-stu-id="1e295-104">This section provides a checklist to help you plan your investigation, and describes common problems.</span></span>  
  
## <a name="checklist-of-data-preparation"></a><span data-ttu-id="1e295-105">数据准备清单</span><span class="sxs-lookup"><span data-stu-id="1e295-105">Checklist of Data Preparation</span></span>  
 <span data-ttu-id="1e295-106">**我已确定了明确定义的输出。**</span><span class="sxs-lookup"><span data-stu-id="1e295-106">**I have identified a clearly defined output.**</span></span>  
 <span data-ttu-id="1e295-107">具有针对结果使用方式的计划。</span><span class="sxs-lookup"><span data-stu-id="1e295-107">Have a plan for how you will use the results.</span></span> <span data-ttu-id="1e295-108">不同类型的模型具有不同的输出。</span><span class="sxs-lookup"><span data-stu-id="1e295-108">Different types of models have different outputs.</span></span> <span data-ttu-id="1e295-109">时序模型生成将来的序列值，这些值易于理解和操作。</span><span class="sxs-lookup"><span data-stu-id="1e295-109">A time series model generates values for a series in the future, which are easily understood and acted on.</span></span> <span data-ttu-id="1e295-110">其他模型生成复杂集合，行业专家必须对这些复杂集合进行分析才能产生最大价值。</span><span class="sxs-lookup"><span data-stu-id="1e295-110">Other models generate complex sets that must be analyzed by subject matter experts to yield the most value.</span></span>  
  
-   <span data-ttu-id="1e295-111">您想要何种类型的输出？</span><span class="sxs-lookup"><span data-stu-id="1e295-111">What output do you want?</span></span>  
  
-   <span data-ttu-id="1e295-112">您是否可以将输出定义为单个列或单个值，或者定义为其他可操作结果？</span><span class="sxs-lookup"><span data-stu-id="1e295-112">Can you define the output as a single column or value, or other actionable result?</span></span>  
  
-   <span data-ttu-id="1e295-113">根据哪些标准您会知道该模型是有用的？</span><span class="sxs-lookup"><span data-stu-id="1e295-113">What are your criteria for knowing that the model was useful?</span></span>  
  
-   <span data-ttu-id="1e295-114">您将如何使用和解释这些结果？</span><span class="sxs-lookup"><span data-stu-id="1e295-114">How will you use and interpret those results?</span></span>  
  
-   <span data-ttu-id="1e295-115">是否可以将新的输入数据映射到期望结果？</span><span class="sxs-lookup"><span data-stu-id="1e295-115">Can you map new input data to the expected results?</span></span>  
  
 <span data-ttu-id="1e295-116">**我知道输入数据的含义、数据类型和分布。**</span><span class="sxs-lookup"><span data-stu-id="1e295-116">**I know the meaning, data types, and distribution of the input data.**</span></span>  
 <span data-ttu-id="1e295-117">花一些时间浏览并了解您的源数据。</span><span class="sxs-lookup"><span data-stu-id="1e295-117">Take some time to explore and understand your source data.</span></span> <span data-ttu-id="1e295-118">查看模型的人应了解所使用的输入数据类型，知道如何解释这些数据类型和变化形式以及平衡和质量，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="1e295-118">It is important that people who review the model understand what kind of input data was used and know how to interpret the data types and the variability, as well as the balance and the quality.</span></span>  
  
-   <span data-ttu-id="1e295-119">您具有多少数据？</span><span class="sxs-lookup"><span data-stu-id="1e295-119">How much data do you have?</span></span> <span data-ttu-id="1e295-120">是否有足够的数据进行建模？</span><span class="sxs-lookup"><span data-stu-id="1e295-120">Is there sufficient data for modeling?</span></span>  
  
     <span data-ttu-id="1e295-121">它不需要太大的容量，更小，平衡起来就更好了。</span><span class="sxs-lookup"><span data-stu-id="1e295-121">It need not be a huge amount - smaller and balanced can be better.</span></span>  
  
-   <span data-ttu-id="1e295-122">数据是来自多个数据源还是单个数据源？</span><span class="sxs-lookup"><span data-stu-id="1e295-122">Is the data from multiple sources, or a single source?</span></span>  
  
-   <span data-ttu-id="1e295-123">数据是否已处理和清理？</span><span class="sxs-lookup"><span data-stu-id="1e295-123">Is the data already processed and clean?</span></span> <span data-ttu-id="1e295-124">是否有更多输入数据可用？</span><span class="sxs-lookup"><span data-stu-id="1e295-124">Is more input data available?</span></span>  
  
-   <span data-ttu-id="1e295-125">你是否知道在收到它之前操作的方式-数据可能已被截断、汇总或转换？</span><span class="sxs-lookup"><span data-stu-id="1e295-125">Do you know how it was manipulated before you received it - how data might have been truncated, summarized, or converted?</span></span>  
  
-   <span data-ttu-id="1e295-126">输入数据是否具有可用于定型的一些示例结果？</span><span class="sxs-lookup"><span data-stu-id="1e295-126">Does the input data have some example results that can be used for training?</span></span>  
  
 <span data-ttu-id="1e295-127">**我了解我们所具有的数据完整性级别及所需级别。**</span><span class="sxs-lookup"><span data-stu-id="1e295-127">**I understand the level of data integrity we have and the level we need.**</span></span>  
 <span data-ttu-id="1e295-128">不良数据可能会影响模型的质量，甚至导致模型完全不能生成。</span><span class="sxs-lookup"><span data-stu-id="1e295-128">Bad data can affect the quality of the model, or prevent the model from being built at all.</span></span> <span data-ttu-id="1e295-129">您应充分了解数据的含义和分布以及它成为此状态的方式。</span><span class="sxs-lookup"><span data-stu-id="1e295-129">You should have a good understanding of both the distribution and meaning of the data, and how it came to this state.</span></span> <span data-ttu-id="1e295-130">您需要了解是否可以通过标记、截断数值数据类型或通过汇总简化数据。</span><span class="sxs-lookup"><span data-stu-id="1e295-130">You'll need to understand if it is possible or appropriate to simplify the data by labeling, truncating numeric data types, or by summarizing.</span></span>  
  
-   <span data-ttu-id="1e295-131">数据标签：是否清晰正确？</span><span class="sxs-lookup"><span data-stu-id="1e295-131">Data labels: are they clear and correct?</span></span>  
  
-   <span data-ttu-id="1e295-132">数据类型：是否合适，是否更改过？</span><span class="sxs-lookup"><span data-stu-id="1e295-132">Data types: are they appropriate, and have they been changed?</span></span>  
  
-   <span data-ttu-id="1e295-133">是否已对数据进行了排序或清理，或者放弃了错误的数据？</span><span class="sxs-lookup"><span data-stu-id="1e295-133">Have you sorted, cleaned up, or discarded wrong data?</span></span>  
  
     <span data-ttu-id="1e295-134">是否已验证了没有重复项？</span><span class="sxs-lookup"><span data-stu-id="1e295-134">Have you verified there are no duplicates?</span></span>  
  
-   <span data-ttu-id="1e295-135">将如何处理缺失值？</span><span class="sxs-lookup"><span data-stu-id="1e295-135">How will you handle missing values?</span></span> <span data-ttu-id="1e295-136">缺失值是否有意义？</span><span class="sxs-lookup"><span data-stu-id="1e295-136">Do missing values have a meaning?</span></span>  
  
-   <span data-ttu-id="1e295-137">是否对数据源进行了验证，查看在导入过程中是否引入了任何错误？</span><span class="sxs-lookup"><span data-stu-id="1e295-137">Have you verified the sources to see if any errors might have been introduced in the import process?</span></span>  
  
     <span data-ttu-id="1e295-138">输入存储于何处？</span><span class="sxs-lookup"><span data-stu-id="1e295-138">Where is the input stored?</span></span> <span data-ttu-id="1e295-139">它的可用时间有多长？</span><span class="sxs-lookup"><span data-stu-id="1e295-139">How long does it stay available?</span></span>  
  
     <span data-ttu-id="1e295-140">是否有数据字典？</span><span class="sxs-lookup"><span data-stu-id="1e295-140">Is there a data dictionary?</span></span> <span data-ttu-id="1e295-141">是否可以创建一个数据字典？</span><span class="sxs-lookup"><span data-stu-id="1e295-141">Can you create one?</span></span>  
  
-   <span data-ttu-id="1e295-142">如果合并了多个数据集，是否检查了是否存在表示相同数据的多个列？</span><span class="sxs-lookup"><span data-stu-id="1e295-142">If you combined data sets, did you check for multiple columns representing the same data?</span></span>  
  
 <span data-ttu-id="1e295-143">**我知道源数据的存储位置、源数据的来源以及处理方式。如果需要，可以轻松地重复此过程。**</span><span class="sxs-lookup"><span data-stu-id="1e295-143">**I know where source data is stored, where it came from, and how it is processed. The process can be easily repeated if needed.**</span></span>  
 <span data-ttu-id="1e295-144">一次性数据集适用于试验，但如果想要将模型移动到生产环境中，则需要提前考虑如何将清理过程应用于操作数据。</span><span class="sxs-lookup"><span data-stu-id="1e295-144">One-off data sets are fine for experiments, but if you ever want to move the model into production, you'll want to think in advance about how the cleaning process can be applied to operational data.</span></span> <span data-ttu-id="1e295-145">此外，如果您有操作数据，您需要知道在您准备之前如何更改它-您需要知道如何对其进行舍入或汇总。</span><span class="sxs-lookup"><span data-stu-id="1e295-145">Also, if you have operational data, you need to know how it might have been altered before you got it-you'll need to know how it was rounded, or summarized, certainly.</span></span>  
  
-   <span data-ttu-id="1e295-146">是否想要能够重复进行试验？</span><span class="sxs-lookup"><span data-stu-id="1e295-146">Do you want to be able to repeat the experiment?</span></span>  
  
-   <span data-ttu-id="1e295-147">将使用哪些工具以支持数据分析的格式准备数据？</span><span class="sxs-lookup"><span data-stu-id="1e295-147">What tools will you use to prepare data in a format that supports data analysis?</span></span> <span data-ttu-id="1e295-148">这一过程是否可自动执行，还是需要有人在 Excel 中查看和清理数据？</span><span class="sxs-lookup"><span data-stu-id="1e295-148">Can it be automated or do you need someone to review and clean up in Excel?</span></span>  
  
-   <span data-ttu-id="1e295-149">如果您的数据来自于其他系统，您是否能够捕获和跟踪已应用的筛选器？</span><span class="sxs-lookup"><span data-stu-id="1e295-149">If you are sourcing data from another system, will you be able to capture and track filters that were applied?</span></span>  
  
-   <span data-ttu-id="1e295-150">数据处理框架是否还应用计算机学习算法、执行测试以及直观地展示结果？</span><span class="sxs-lookup"><span data-stu-id="1e295-150">Can your data processing framework also apply machine learning algorithms, perform tests, and visualize results?</span></span>  
  
 <span data-ttu-id="1e295-151">**我们已经商定所需预测粒度并已将数据改为输出这些单位。**</span><span class="sxs-lookup"><span data-stu-id="1e295-151">**We have agreed on the desired granularity of predictions and our data has been modified to output those units.**</span></span>  
 <span data-ttu-id="1e295-152">请在准备数据前决定所需结果粒度，例如，是要每天的销量预测还是每季度的销量预测。</span><span class="sxs-lookup"><span data-stu-id="1e295-152">Decide on the granularity of the results you want before preparing data, For example, do you want sales predictions by the day, or for each quarter?</span></span> <span data-ttu-id="1e295-153">应考虑对相同数据设置不同的数据结构，以便处理不同的汇总级别。</span><span class="sxs-lookup"><span data-stu-id="1e295-153">You might consider setting up different data structures for the same data, to handle different levels of summary.</span></span>  
  
-   <span data-ttu-id="1e295-154">当前度量单位或时间单位是什么？</span><span class="sxs-lookup"><span data-stu-id="1e295-154">What is the current unit of measure or unit of time?</span></span>  
  
     <span data-ttu-id="1e295-155">您要在结果中使用的单位是什么？</span><span class="sxs-lookup"><span data-stu-id="1e295-155">What unit do you want to use in the results?</span></span>  
  
-   <span data-ttu-id="1e295-156">是否可以为所有输入数据定义基本单位 (例如，每小时/每小时/最小/指令调用) ？</span><span class="sxs-lookup"><span data-stu-id="1e295-156">Is it possible to define a basic unit (e.g. day/ hour / min / instruction call) for all input data?</span></span>  
  
     <span data-ttu-id="1e295-157">是否想要汇总到更高单位？</span><span class="sxs-lookup"><span data-stu-id="1e295-157">Do you want to rollup to higher units?</span></span>  
  
-   <span data-ttu-id="1e295-158">是否以一致的方式对类别进行了标记？</span><span class="sxs-lookup"><span data-stu-id="1e295-158">Are categories labeled consistently?</span></span> <span data-ttu-id="1e295-159">是否可以轻松地添加或删除类别？</span><span class="sxs-lookup"><span data-stu-id="1e295-159">Is it easy to add or remove categories?</span></span>  
  
 <span data-ttu-id="1e295-160">**我们的实验设计是可重复且可再现的。**</span><span class="sxs-lookup"><span data-stu-id="1e295-160">**Our experimental design is repeatable and reproducible.**</span></span>  
 <span data-ttu-id="1e295-161">考虑用于对您的结果进行分析和验证的策略，并且计划捕获数据快照，以便确保您可以追溯数据结果。</span><span class="sxs-lookup"><span data-stu-id="1e295-161">Consider strategies for analyzing and validating your results and plan to capture a data snapshot, to make sure you can trace back effects to data.</span></span> <span data-ttu-id="1e295-162">如果使用随机种子，结果可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="1e295-162">If a random seed is used, the results can differ subtly.</span></span> <span data-ttu-id="1e295-163">这会使比较和验证模型比较困难。</span><span class="sxs-lookup"><span data-stu-id="1e295-163">This can make it difficult to compare and validate models.</span></span>  
  
-   <span data-ttu-id="1e295-164">如果您对数据进行了许多自定义更改，下次您要生成模型时将会发生什么？</span><span class="sxs-lookup"><span data-stu-id="1e295-164">If you make a lot of custom changes to the data, what happens the next time you want to build the model?</span></span>  
  
-   <span data-ttu-id="1e295-165">是否已定义了应该用来处理输入和获取预期输出的手动过程或许可流程？</span><span class="sxs-lookup"><span data-stu-id="1e295-165">Has a manual procedure or approved process already been defined that you should use to process input and get the desired outputs?</span></span>  
  
-   <span data-ttu-id="1e295-166">您是否已决定将种子用于模型？</span><span class="sxs-lookup"><span data-stu-id="1e295-166">Have you decided to use a seed for the model?</span></span>  
  
 <span data-ttu-id="1e295-167">**我们拥有验证结果所需的领域知识，或者可以联系行业专家寻求建议。**</span><span class="sxs-lookup"><span data-stu-id="1e295-167">**We have the domain knowledge to validate the results, or have access to subject matter experts who can advise.**</span></span>  
 <span data-ttu-id="1e295-168">花费一些时间来验证变量、模型和结果。</span><span class="sxs-lookup"><span data-stu-id="1e295-168">Take time to validate the variables, the model, and the results.</span></span> <span data-ttu-id="1e295-169">获取专家帮助以便评估交互和结果。</span><span class="sxs-lookup"><span data-stu-id="1e295-169">Get the help of experts to assess interactions and results.</span></span> <span data-ttu-id="1e295-170">但是，不要假设反驳的证据。</span><span class="sxs-lookup"><span data-stu-id="1e295-170">However, don't let assumptions overrule evidence.</span></span> <span data-ttu-id="1e295-171">要对新发现和意外发现持开放的态度。</span><span class="sxs-lookup"><span data-stu-id="1e295-171">Be open to new and unexpected findings.</span></span>  
  
-   <span data-ttu-id="1e295-172">域知识是否可有助于筛选数据和减少输入干扰？</span><span class="sxs-lookup"><span data-stu-id="1e295-172">Is domain knowledge available to help in filtering data and reducing input noise?</span></span>  
  
-   <span data-ttu-id="1e295-173">域专家是否可以帮助理解和解释结果以及建议改进？</span><span class="sxs-lookup"><span data-stu-id="1e295-173">Can domain experts help understand interpret the results and suggest improvements?</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e295-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e295-174">See Also</span></span>  
 [<span data-ttu-id="1e295-175">为数据挖掘选择数据</span><span class="sxs-lookup"><span data-stu-id="1e295-175">Choosing Data for Data Mining</span></span>](choosing-data-for-data-mining.md)  
  
  
