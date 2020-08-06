---
title: 创建神经网络结构和模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 91c0210213083868eaab36cf34a05d0b7824a654
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577970"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="dd1b6-102">创建神经网络结构和模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="dd1b6-102">Creating a Neural Network Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="dd1b6-103">若要创建数据挖掘模型，必须先使用数据挖掘向导基于新数据源视图创建一个新的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-103">To create a data mining model, you must first use the Data Mining Wizard to create a new mining structure based on the new data source view.</span></span> <span data-ttu-id="dd1b6-104">在本任务中，您将使用该向导创建一个挖掘结构，同时创建一个基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 神经网络算法的关联挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-104">In this task you will use the wizard to create a mining structure, and at the same time create an associated mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="dd1b6-105">由于神经网络非常灵活且可以分析输入和输出的多个组合，因此应试用多种处理数据的方式以获得最佳结果。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-105">Because neural networks are extremely flexible and can analyze many combinations of inputs and outputs, you should experiment with several ways of processing the data to get the best results.</span></span> <span data-ttu-id="dd1b6-106">例如，你可能想要自定义服务质量的数字目标*装箱*或分组的方式，以满足特定的业务要求。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-106">For example, you might want to customize the way that the numerical target for service quality is *binned*, or grouped, to target specific business requirements.</span></span> <span data-ttu-id="dd1b6-107">为此，您将向该挖掘结构中添加一个以不同的方式对数值数据进行分组的新列，然后创建一个使用这个新列的模型。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-107">To do this, you will add a new column to the mining structure that groups numerical data in a different way, and then create a model that uses the new column.</span></span> <span data-ttu-id="dd1b6-108">您将使用这些挖掘模型来进行一些浏览。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-108">You will use these mining models to do some exploration.</span></span>  
  
 <span data-ttu-id="dd1b6-109">最后，在您从神经网络模型中了解到哪些因素对您的业务问题影响最大之后，您需要生成一个单独的预测和记分模型。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-109">Finally, when you have learned from the neural network model which factors have the greatest impact for your business question, you will build a separate model for prediction and scoring.</span></span> <span data-ttu-id="dd1b6-110">需要使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 逻辑回归算法，该算法基于神经网络模型，但经过优化可用于基于特定输入查找解决方案。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-110">You will use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm, which is based on the neural networks model but is optimized for finding a solution based on specific inputs.</span></span>  
  
 <span data-ttu-id="dd1b6-111">**步骤**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-111">**Steps**</span></span>  
  
 [<span data-ttu-id="dd1b6-112">创建默认挖掘结构和模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-112">Create the default mining structure and model</span></span>](#bkmk_defaul)  
  
 [<span data-ttu-id="dd1b6-113">使用离散化将可预测列装箱</span><span class="sxs-lookup"><span data-stu-id="dd1b6-113">Use discretization to bin the predictable column</span></span>](#bkmk_ColumnCopy)  
  
 [<span data-ttu-id="dd1b6-114">复制列并为不同模型更改离散化方法</span><span class="sxs-lookup"><span data-stu-id="dd1b6-114">Copy the column and change the discretization method for a different model</span></span>](#bkmk_Alias)  
  
 [<span data-ttu-id="dd1b6-115">为可预测列创建别名以便比较模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-115">Create an alias for the predictable column so that you can compare models</span></span>](#bkmk_Alias2)  
  
 [<span data-ttu-id="dd1b6-116">处理所有模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-116">Process all models</span></span>](#bkmk_SeedProcess)  
  
## <a name="create-the-default-call-center-structure"></a><span data-ttu-id="dd1b6-117">创建默认呼叫中心结构<a name="bkmk_defaul"></a></span><span class="sxs-lookup"><span data-stu-id="dd1b6-117">Create the Default Call Center Structure  <a name="bkmk_defaul"></a></span></span>  
  
1.  <span data-ttu-id="dd1b6-118">在的解决方案资源管理器中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，右键单击 "**挖掘结构**"，然后选择 "**新建挖掘结构**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-118">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="dd1b6-119">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-119">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="dd1b6-120">在 "**选择定义方法**" 页上，验证是否选择了 "**从现有关系数据库或数据仓库**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-120">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="dd1b6-121">在 "**创建数据挖掘结构**" 页上，验证是否选择了 "**创建具有挖掘模型的挖掘结构**" 选项。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-121">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span>  
  
5.  <span data-ttu-id="dd1b6-122">单击 "**要使用何种数据挖掘技术？**" 选项的下拉列表，然后选择 " **Microsoft 神经网络**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-122">Click the dropdown list for the option **Which data mining technique do you want to use?**, then select **Microsoft Neural Networks**.</span></span>  
  
     <span data-ttu-id="dd1b6-123">由于逻辑回归模型基于神经网络，因此，您可以重用同一结构，添加新的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-123">Because the logistic regression models are based on the neural networks, you can reuse the same structure and add a new mining model.</span></span>  
  
6.  <span data-ttu-id="dd1b6-124">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-124">Click **Next**.</span></span>  
  
     <span data-ttu-id="dd1b6-125">此时将显示 "**选择数据源视图**" 页。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-125">The **Select Data Source View** page appears.</span></span>  
  
7.  <span data-ttu-id="dd1b6-126">在 "**可用数据源视图**" 下，选择 `Call Center` ，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-126">Under **Available data source views**, select `Call Center`, and click **Next**.</span></span>  
  
8.  <span data-ttu-id="dd1b6-127">在 "**指定表类型**" 页上，选中**FactCallCenter**表旁边的 "**事例**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-127">On the **Specify Table Types** page, select the **Case** check box next to the **FactCallCenter** table.</span></span> <span data-ttu-id="dd1b6-128">不要为**DimDate**选择任何内容。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-128">Do not select anything for **DimDate**.</span></span> <span data-ttu-id="dd1b6-129">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="dd1b6-130">在 "**指定定型数据**" 页上，选择列 "FactCallCenterID" 旁边的 "**键**" **。**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-130">On the **Specify the Training Data** page, select **Key** next to the column **FactCallCenterID.**</span></span>  
  
10. <span data-ttu-id="dd1b6-131">选中 `Predict` 和**输入**复选框。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-131">Select the `Predict` and **Input** check boxes.</span></span>  
  
11. <span data-ttu-id="dd1b6-132">选中 "**键**"、"**输入**" 和 `Predict` 复选框，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-132">Select the **Key**, **Input**, and `Predict` check boxes as shown in the following table:</span></span>  
  
    |<span data-ttu-id="dd1b6-133">表/列</span><span class="sxs-lookup"><span data-stu-id="dd1b6-133">Tables/Columns</span></span>|<span data-ttu-id="dd1b6-134">键/输入/预测</span><span class="sxs-lookup"><span data-stu-id="dd1b6-134">Key/Input/Predict</span></span>|  
    |---------------------|-------------------------|  
    |<span data-ttu-id="dd1b6-135">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="dd1b6-135">AutomaticResponses</span></span>|<span data-ttu-id="dd1b6-136">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-136">Input</span></span>|  
    |<span data-ttu-id="dd1b6-137">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="dd1b6-137">AverageTimePerIssue</span></span>|<span data-ttu-id="dd1b6-138">输入/预测</span><span class="sxs-lookup"><span data-stu-id="dd1b6-138">Input/Predict</span></span>|  
    |<span data-ttu-id="dd1b6-139">调用</span><span class="sxs-lookup"><span data-stu-id="dd1b6-139">Calls</span></span>|<span data-ttu-id="dd1b6-140">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-140">Input</span></span>|  
    |<span data-ttu-id="dd1b6-141">DateKey</span><span class="sxs-lookup"><span data-stu-id="dd1b6-141">DateKey</span></span>|<span data-ttu-id="dd1b6-142">请勿使用</span><span class="sxs-lookup"><span data-stu-id="dd1b6-142">Do not use</span></span>|  
    |<span data-ttu-id="dd1b6-143">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="dd1b6-143">DayOfWeek</span></span>|<span data-ttu-id="dd1b6-144">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-144">Input</span></span>|  
    |<span data-ttu-id="dd1b6-145">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="dd1b6-145">FactCallCenterID</span></span>|<span data-ttu-id="dd1b6-146">密钥</span><span class="sxs-lookup"><span data-stu-id="dd1b6-146">Key</span></span>|  
    |<span data-ttu-id="dd1b6-147">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="dd1b6-147">IssuesRaised</span></span>|<span data-ttu-id="dd1b6-148">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-148">Input</span></span>|  
    |<span data-ttu-id="dd1b6-149">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-149">LevelOneOperators</span></span>|<span data-ttu-id="dd1b6-150">输入/预测</span><span class="sxs-lookup"><span data-stu-id="dd1b6-150">Input/Predict</span></span>|  
    |<span data-ttu-id="dd1b6-151">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-151">LevelTwoOperators</span></span>|<span data-ttu-id="dd1b6-152">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-152">Input</span></span>|  
    |<span data-ttu-id="dd1b6-153">Orders</span><span class="sxs-lookup"><span data-stu-id="dd1b6-153">Orders</span></span>|<span data-ttu-id="dd1b6-154">输入/预测</span><span class="sxs-lookup"><span data-stu-id="dd1b6-154">Input/Predict</span></span>|  
    |<span data-ttu-id="dd1b6-155">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="dd1b6-155">ServiceGrade</span></span>|<span data-ttu-id="dd1b6-156">输入/预测</span><span class="sxs-lookup"><span data-stu-id="dd1b6-156">Input/Predict</span></span>|  
    |<span data-ttu-id="dd1b6-157">移位</span><span class="sxs-lookup"><span data-stu-id="dd1b6-157">Shift</span></span>|<span data-ttu-id="dd1b6-158">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-158">Input</span></span>|  
    |<span data-ttu-id="dd1b6-159">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-159">TotalOperators</span></span>|<span data-ttu-id="dd1b6-160">请勿使用</span><span class="sxs-lookup"><span data-stu-id="dd1b6-160">Do not use</span></span>|  
    |<span data-ttu-id="dd1b6-161">WageType</span><span class="sxs-lookup"><span data-stu-id="dd1b6-161">WageType</span></span>|<span data-ttu-id="dd1b6-162">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-162">Input</span></span>|  
  
     <span data-ttu-id="dd1b6-163">请注意已选定多个可预测列。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-163">Note that multiple predictable columns have been selected.</span></span> <span data-ttu-id="dd1b6-164">神经网络算法的优点之一是：它可以分析输入和输出属性的所有可能组合。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-164">One of the strengths of the neural network algorithm is that it can analyze all possible combinations of input and output attributes.</span></span> <span data-ttu-id="dd1b6-165">对于大型数据集，不需要执行此操作，因为这可能会使处理时间呈指数级增长。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-165">You wouldn't want to do this for a large data set, as it could exponentially increase processing time..</span></span>  
  
12. <span data-ttu-id="dd1b6-166">在 "**指定列的内容和数据类型"** 页上，验证网格中是否包含下表中所示的列、内容类型和数据类型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-166">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="dd1b6-167">列</span><span class="sxs-lookup"><span data-stu-id="dd1b6-167">Columns</span></span>|<span data-ttu-id="dd1b6-168">内容类型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-168">Content Type</span></span>|<span data-ttu-id="dd1b6-169">数据类型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-169">Data Types</span></span>|  
    |-------------|------------------|----------------|  
    |<span data-ttu-id="dd1b6-170">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="dd1b6-170">AutomaticResponses</span></span>|<span data-ttu-id="dd1b6-171">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-171">Continuous</span></span>|<span data-ttu-id="dd1b6-172">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-172">Long</span></span>|  
    |<span data-ttu-id="dd1b6-173">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="dd1b6-173">AverageTimePerIssue</span></span>|<span data-ttu-id="dd1b6-174">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-174">Continuous</span></span>|<span data-ttu-id="dd1b6-175">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-175">Long</span></span>|  
    |<span data-ttu-id="dd1b6-176">调用</span><span class="sxs-lookup"><span data-stu-id="dd1b6-176">Calls</span></span>|<span data-ttu-id="dd1b6-177">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-177">Continuous</span></span>|<span data-ttu-id="dd1b6-178">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-178">Long</span></span>|  
    |<span data-ttu-id="dd1b6-179">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="dd1b6-179">DayOfWeek</span></span>|<span data-ttu-id="dd1b6-180">离散</span><span class="sxs-lookup"><span data-stu-id="dd1b6-180">Discrete</span></span>|<span data-ttu-id="dd1b6-181">文本</span><span class="sxs-lookup"><span data-stu-id="dd1b6-181">Text</span></span>|  
    |<span data-ttu-id="dd1b6-182">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="dd1b6-182">FactCallCenterID</span></span>|<span data-ttu-id="dd1b6-183">密钥</span><span class="sxs-lookup"><span data-stu-id="dd1b6-183">Key</span></span>|<span data-ttu-id="dd1b6-184">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-184">Long</span></span>|  
    |<span data-ttu-id="dd1b6-185">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="dd1b6-185">IssuesRaised</span></span>|<span data-ttu-id="dd1b6-186">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-186">Continuous</span></span>|<span data-ttu-id="dd1b6-187">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-187">Long</span></span>|  
    |<span data-ttu-id="dd1b6-188">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-188">LevelOneOperators</span></span>|<span data-ttu-id="dd1b6-189">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-189">Continuous</span></span>|<span data-ttu-id="dd1b6-190">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-190">Long</span></span>|  
    |<span data-ttu-id="dd1b6-191">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-191">LevelTwoOperators</span></span>|<span data-ttu-id="dd1b6-192">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-192">Continuous</span></span>|<span data-ttu-id="dd1b6-193">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-193">Long</span></span>|  
    |<span data-ttu-id="dd1b6-194">Orders</span><span class="sxs-lookup"><span data-stu-id="dd1b6-194">Orders</span></span>|<span data-ttu-id="dd1b6-195">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-195">Continuous</span></span>|<span data-ttu-id="dd1b6-196">Long</span><span class="sxs-lookup"><span data-stu-id="dd1b6-196">Long</span></span>|  
    |<span data-ttu-id="dd1b6-197">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="dd1b6-197">ServiceGrade</span></span>|<span data-ttu-id="dd1b6-198">连续</span><span class="sxs-lookup"><span data-stu-id="dd1b6-198">Continuous</span></span>|<span data-ttu-id="dd1b6-199">Double</span><span class="sxs-lookup"><span data-stu-id="dd1b6-199">Double</span></span>|  
    |<span data-ttu-id="dd1b6-200">移位</span><span class="sxs-lookup"><span data-stu-id="dd1b6-200">Shift</span></span>|<span data-ttu-id="dd1b6-201">离散</span><span class="sxs-lookup"><span data-stu-id="dd1b6-201">Discrete</span></span>|<span data-ttu-id="dd1b6-202">文本</span><span class="sxs-lookup"><span data-stu-id="dd1b6-202">Text</span></span>|  
    |<span data-ttu-id="dd1b6-203">WageType</span><span class="sxs-lookup"><span data-stu-id="dd1b6-203">WageType</span></span>|<span data-ttu-id="dd1b6-204">离散</span><span class="sxs-lookup"><span data-stu-id="dd1b6-204">Discrete</span></span>|<span data-ttu-id="dd1b6-205">文本</span><span class="sxs-lookup"><span data-stu-id="dd1b6-205">Text</span></span>|  
  
13. <span data-ttu-id="dd1b6-206">在 "**创建测试集**" 页上，清除选项的 "文本" 框中要**测试的数据的百分比**。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-206">On the **Create testing set** page, clear the text box for the option, **Percentage of data for testing**.</span></span> <span data-ttu-id="dd1b6-207">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-207">Click **Next**.</span></span>  
  
14. <span data-ttu-id="dd1b6-208">在 "**完成向导**" 页的 "**挖掘结构名称**" 中，键入 `Call Center` 。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-208">On the **Completing the Wizard** page, for the **Mining structure name**, type `Call Center`.</span></span>  
  
15. <span data-ttu-id="dd1b6-209">对于 "**挖掘模型名称**"，请键入 `Call Center Default NN` ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-209">For the **Mining model name**, type `Call Center Default NN`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="dd1b6-210">"**允许钻取**" 框被禁用，因为您不能使用神经网络模型钻取到数据。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-210">The **Allow drill through** box is disabled because you cannot drill through to data with neural network models.</span></span>  
  
16. <span data-ttu-id="dd1b6-211">在解决方案资源管理器中，右键单击刚创建的数据挖掘结构的名称，然后选择 "**处理**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-211">In Solution Explorer, right-click the name of the data mining structure that you just created, and select **Process**.</span></span>  
  
## <a name="use-discretization-to-bin-the-target-column"></a><span data-ttu-id="dd1b6-212">使用离散化将目标列装箱</span><span class="sxs-lookup"><span data-stu-id="dd1b6-212">Use Discretization to Bin the Target Column</span></span>  
 <span data-ttu-id="dd1b6-213">默认情况下，创建具有数值型可预测属性的神经网络模型时，Microsoft 神经网络算法将该属性视为连续数值。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-213">By default, when you create a neural network model that has a numeric predictable attribute, the Microsoft Neural Network algorithm treats the attribute as a continuous number.</span></span> <span data-ttu-id="dd1b6-214">例如，ServiceGrade 属性在理论上是介于 0.00（应答所有呼叫）和 1.00（挂断所有呼叫）之间的数值。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-214">For example, the ServiceGrade attribute is a number that theoretically ranges from 0.00 (all calls are answered) to 1.00 (all callers hang up).</span></span> <span data-ttu-id="dd1b6-215">在此数据集中的值具有以下分布：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-215">In this data set, the values have the following distribution:</span></span>  
  
 <span data-ttu-id="dd1b6-216">![服务级别值的分发](../../2014/tutorials/media/skt-service-grade-valuesc.gif "服务级别值的分发")</span><span class="sxs-lookup"><span data-stu-id="dd1b6-216">![distribution of service grade values](../../2014/tutorials/media/skt-service-grade-valuesc.gif "distribution of service grade values")</span></span>  
  
 <span data-ttu-id="dd1b6-217">因此，处理模型时，输出的分组方式可能会与预期的不同。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-217">As a result, when you process the model the outputs might be grouped differently than you expect.</span></span> <span data-ttu-id="dd1b6-218">例如，如果使用聚类分析来识别最佳值组，则算法会将 ServiceGrade 中的值划分为多个范围，例如： 0.0748051948-0.09716216215。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-218">For example, if you use clustering to identify the best groups of values, the algorithm divides the values in ServiceGrade into ranges such as this one: 0.0748051948 - 0.09716216215.</span></span> <span data-ttu-id="dd1b6-219">尽管此分组在数学上很准确，但此类范围可能对业务用户并没有太大意义。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-219">Although this grouping is mathematically accurate, such ranges might not be as meaningful to business users.</span></span>  
  
 <span data-ttu-id="dd1b6-220">在此步骤中，若要使结果更加直观，你需要以不同的方式对数值进行分组，从而创建数值数据列的副本。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-220">In this step, to make the result more intuitive, you'll group the numerical values differently, creating copies of the numerical data column.</span></span>  
  
### <a name="how-discretization-works"></a><span data-ttu-id="dd1b6-221">如何使用离散化</span><span class="sxs-lookup"><span data-stu-id="dd1b6-221">How Discretization Works</span></span>  
 <span data-ttu-id="dd1b6-222">Analysis Services 提供了各种装箱或处理数值数据的方法。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-222">Analysis Services provides a variety of methods for binning or processing numerical data.</span></span> <span data-ttu-id="dd1b6-223">下表说明了以三种不同方式处理输出属性 ServiceGrade 所得到的结果的差异：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-223">The following table illustrates the differences between the results when the output attribute ServiceGrade has been processed three different ways:</span></span>  
  
-   <span data-ttu-id="dd1b6-224">将其视为连续数值。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-224">Treating it as a continuous number.</span></span>  
  
-   <span data-ttu-id="dd1b6-225">让算法使用聚类分析来确定最佳值划分方式。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-225">Having the algorithm use clustering to identify the best arrangement of values.</span></span>  
  
-   <span data-ttu-id="dd1b6-226">指定数值按等面积方法装箱。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-226">Specifying that the numbers be binned by the Equal Areas method.</span></span>  
  
 <span data-ttu-id="dd1b6-227">默认模型（连续）</span><span class="sxs-lookup"><span data-stu-id="dd1b6-227">Default model (continuous)</span></span>  
  
|<span data-ttu-id="dd1b6-228">值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-228">VALUE</span></span>|<span data-ttu-id="dd1b6-229">Support</span><span class="sxs-lookup"><span data-stu-id="dd1b6-229">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="dd1b6-230">Missing</span><span class="sxs-lookup"><span data-stu-id="dd1b6-230">Missing</span></span>|<span data-ttu-id="dd1b6-231">0</span><span class="sxs-lookup"><span data-stu-id="dd1b6-231">0</span></span>|  
|<span data-ttu-id="dd1b6-232">0.09875</span><span class="sxs-lookup"><span data-stu-id="dd1b6-232">0.09875</span></span>|<span data-ttu-id="dd1b6-233">120</span><span class="sxs-lookup"><span data-stu-id="dd1b6-233">120</span></span>|  
  
 <span data-ttu-id="dd1b6-234">以聚类分析方式装箱</span><span class="sxs-lookup"><span data-stu-id="dd1b6-234">Binned by clustering</span></span>  
  
|<span data-ttu-id="dd1b6-235">值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-235">VALUE</span></span>|<span data-ttu-id="dd1b6-236">Support</span><span class="sxs-lookup"><span data-stu-id="dd1b6-236">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="dd1b6-237">\<0.0748051948</span><span class="sxs-lookup"><span data-stu-id="dd1b6-237">\< 0.0748051948</span></span>|<span data-ttu-id="dd1b6-238">34</span><span class="sxs-lookup"><span data-stu-id="dd1b6-238">34</span></span>|  
|<span data-ttu-id="dd1b6-239">0.0748051948-0.09716216215</span><span class="sxs-lookup"><span data-stu-id="dd1b6-239">0.0748051948 - 0.09716216215</span></span>|<span data-ttu-id="dd1b6-240">27</span><span class="sxs-lookup"><span data-stu-id="dd1b6-240">27</span></span>|  
|<span data-ttu-id="dd1b6-241">0.09716216215-0.13297297295</span><span class="sxs-lookup"><span data-stu-id="dd1b6-241">0.09716216215 - 0.13297297295</span></span>|<span data-ttu-id="dd1b6-242">39</span><span class="sxs-lookup"><span data-stu-id="dd1b6-242">39</span></span>|  
|<span data-ttu-id="dd1b6-243">0.13297297295 - 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="dd1b6-243">0.13297297295 - 0.167499999975</span></span>|<span data-ttu-id="dd1b6-244">10</span><span class="sxs-lookup"><span data-stu-id="dd1b6-244">10</span></span>|  
|<span data-ttu-id="dd1b6-245">>= 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="dd1b6-245">>= 0.167499999975</span></span>|<span data-ttu-id="dd1b6-246">10</span><span class="sxs-lookup"><span data-stu-id="dd1b6-246">10</span></span>|  
  
 <span data-ttu-id="dd1b6-247">按等面积装箱</span><span class="sxs-lookup"><span data-stu-id="dd1b6-247">Binned by equal areas</span></span>  
  
|<span data-ttu-id="dd1b6-248">值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-248">VALUE</span></span>|<span data-ttu-id="dd1b6-249">Support</span><span class="sxs-lookup"><span data-stu-id="dd1b6-249">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="dd1b6-250">\<0.07</span><span class="sxs-lookup"><span data-stu-id="dd1b6-250">\< 0.07</span></span>|<span data-ttu-id="dd1b6-251">26</span><span class="sxs-lookup"><span data-stu-id="dd1b6-251">26</span></span>|  
|<span data-ttu-id="dd1b6-252">0.07-0.00</span><span class="sxs-lookup"><span data-stu-id="dd1b6-252">0.07 - 0.00</span></span>|<span data-ttu-id="dd1b6-253">22</span><span class="sxs-lookup"><span data-stu-id="dd1b6-253">22</span></span>|  
|<span data-ttu-id="dd1b6-254">0.09-0.11</span><span class="sxs-lookup"><span data-stu-id="dd1b6-254">0.09 - 0.11</span></span>|<span data-ttu-id="dd1b6-255">36</span><span class="sxs-lookup"><span data-stu-id="dd1b6-255">36</span></span>|  
|<span data-ttu-id="dd1b6-256">>= 0.12</span><span class="sxs-lookup"><span data-stu-id="dd1b6-256">>= 0.12</span></span>|<span data-ttu-id="dd1b6-257">36</span><span class="sxs-lookup"><span data-stu-id="dd1b6-257">36</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="dd1b6-258">可以在处理完所有数据后，从模型的边际统计信息节点获取这些统计信息。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-258">You can obtain these statistics from the marginal statistics node of the model, after all the data has been processed.</span></span> <span data-ttu-id="dd1b6-259">有关边际统计信息节点的详细信息，请参阅[神经网络模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-259">For more information about the marginal statistics node, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="dd1b6-260">此表中，VALUE 列为您显示了 ServiceGrade 的数值的处理方式。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-260">In this table, the VALUE column shows you how the number for ServiceGrade has been handled.</span></span> <span data-ttu-id="dd1b6-261">SUPPORT 列为您显示有多少事例具有此值或属于该范围。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-261">The SUPPORT column shows you how many cases had that value, or that fell in that range.</span></span>  
  
-   <span data-ttu-id="dd1b6-262">**使用连续数值（默认值）**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-262">**Use continuous numbers (default)**</span></span>  
  
     <span data-ttu-id="dd1b6-263">如果使用了默认方法，算法将计算 120 个非重复值的结果，这些值的均值为 0.09875。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-263">If you used the default method, the algorithm would compute outcomes for 120 distinct values, the mean value of which is 0.09875.</span></span> <span data-ttu-id="dd1b6-264">您还可以查看缺失值的数目。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-264">You can also see the number of missing values.</span></span>  
  
-   <span data-ttu-id="dd1b6-265">**分类**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-265">**Bin by clustering**</span></span>  
  
     <span data-ttu-id="dd1b6-266">如果让 Microsoft 聚类分析算法来确定值的可选分组时，该算法会将 ServiceGrade 的值划分为五个 (5) 范围。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-266">When you let the Microsoft Clustering algorithm determine the optional grouping of values, the algorithm would group the values for ServiceGrade into five (5) ranges.</span></span> <span data-ttu-id="dd1b6-267">每个范围内的事例数目不是均匀分布的，正如您从 support 列看到的那样。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-267">The number of cases in each range is not evenly distributed, as you can see from the support column.</span></span>  
  
-   <span data-ttu-id="dd1b6-268">**按等区域分类**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-268">**Bin by equal areas**</span></span>  
  
     <span data-ttu-id="dd1b6-269">如果选择此方法，该算法会强制将值划分到大小相等的 Bucket 中，而这又会更改每个范围的上下限。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-269">When you choose this method, the algorithm forces the values into buckets of equal size, which in turn changes the upper and lower bounds of each range.</span></span> <span data-ttu-id="dd1b6-270">您可以指定 Bucket 的数目，但要避免任何 Bucket 中的值少于两个。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-270">You can specify the number of buckets, but you want to avoid having two few values in any bucket.</span></span>  
  
 <span data-ttu-id="dd1b6-271">有关装箱选项的详细信息，请参阅[数据挖掘&#41;&#40;离散化方法](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-271">For more information about binning options, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span>  
  
 <span data-ttu-id="dd1b6-272">或者，您可以添加一个单独的派生列，将服务等级归类为预定义的目标范围，例如**最佳** (ServiceGrade \<= 0.05), **Acceptable** (0.10 > ServiceGrade > 0.05) ，不**太** (ServiceGrade >= 0.10) ，而不是使用数值。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-272">Alternatively, rather than using the numeric values, you could add a separate derived column that classifies the service grades into predefined target ranges, such as **Best** (ServiceGrade \<= 0.05), **Acceptable** (0.10 > ServiceGrade > 0.05), and **Poor** (ServiceGrade >= 0.10).</span></span>  
  
###  <a name="create-a-copy-of-a-column-and-change-the-discretization-method"></a><a name="bkmk_newColumn"></a><span data-ttu-id="dd1b6-273">创建列的副本并更改离散化方法</span><span class="sxs-lookup"><span data-stu-id="dd1b6-273">Create a Copy of a Column and Change the Discretization Method</span></span>  
 <span data-ttu-id="dd1b6-274">您将创建包含目标属性的挖掘列的副本 ServiceGrade，并更改数字的分组方式。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-274">You'll make a copy of the mining column that contains the target attribute, ServiceGrade and change the way the numbers are grouped.</span></span> <span data-ttu-id="dd1b6-275">可以创建挖掘结构中任何列（包括可预测属性）的多个副本。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-275">You can create multiple copies of any column in a mining structure, including the predictable attribute.</span></span>  
  
 <span data-ttu-id="dd1b6-276">在本教程中，您将使用离散化的等面积方法并指定四个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-276">For this tutorial, you will use the Equal Areas method of discretization, and specify four buckets.</span></span> <span data-ttu-id="dd1b6-277">此方法所产生的分组与您的业务用户所希望的目标值十分接近。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-277">The groupings that result from this method are fairly close to the target values of interest to your business users.</span></span>  
  
####  <a name="to-create-a-customized-copy-of-a-column-in-the-mining-structure"></a><a name="bkmk_ColumnCopy"></a><span data-ttu-id="dd1b6-278">在挖掘结构中创建列的自定义副本</span><span class="sxs-lookup"><span data-stu-id="dd1b6-278">To create a customized copy of a column in the mining structure</span></span>  
  
1.  <span data-ttu-id="dd1b6-279">在解决方案资源管理器中，双击刚刚创建的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-279">In Solution Explorer, double-click the mining structure that you just created.</span></span>  
  
2.  <span data-ttu-id="dd1b6-280">在 "挖掘结构" 选项卡中，单击 "**添加挖掘结构列**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-280">In the Mining Structure tab, click **Add a mining structure column**.</span></span>  
  
3.  <span data-ttu-id="dd1b6-281">在 "**选择列**" 对话框中，从 "**源列**" 列表中选择 "ServiceGrade"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-281">In the **Select column** dialog box, select ServiceGrade from the list in **Source column**, then click **OK**.</span></span>  
  
     <span data-ttu-id="dd1b6-282">一个新的列添加到挖掘结构列的列表中。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-282">A new column is added to the list of mining structure columns.</span></span> <span data-ttu-id="dd1b6-283">默认情况下，这个新的挖掘列具有与现有列相同的名称，并有一个数值后缀，如 ServiceGrade 1。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-283">By default, the new mining column has the same name as the existing column, with a numerical postfix: for example, ServiceGrade 1.</span></span> <span data-ttu-id="dd1b6-284">您可以更改该列的名称，使其更具描述性。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-284">You can change the name of this column to be more descriptive.</span></span>  
  
     <span data-ttu-id="dd1b6-285">您还将指定离散化方法。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-285">You will also specify the discretization method.</span></span>  
  
4.  <span data-ttu-id="dd1b6-286">右键单击 "ServiceGrade 1"，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-286">Right-click ServiceGrade 1 and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="dd1b6-287">在 "**属性**" 窗口中，找到 "**名称**" 属性，然后将 "名称" 更改为 "**装箱**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-287">In the **Properties** window, locate the **Name** property, and change the name to **Service Grade Binned** .</span></span>  
  
6.  <span data-ttu-id="dd1b6-288">出现一个对话框，询问您是否要对所有相关的挖掘模型列的名称进行同样的更改。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-288">A dialog box appears asking whether you want to make the same change to the name of all related mining model columns.</span></span> <span data-ttu-id="dd1b6-289">单击 **“否”**。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-289">Click **No**.</span></span>  
  
7.  <span data-ttu-id="dd1b6-290">在 "**属性**" 窗口中，找到 "**数据类型**" 部分，并根据需要将其展开。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-290">In the **Properties** window, locate the section **Data Type** and expand it if necessary.</span></span>  
  
8.  <span data-ttu-id="dd1b6-291">将属性 `Content` 的值从 `Continuous` 更改为 `Discretized`。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-291">Change the value of the property `Content` from `Continuous` to `Discretized`.</span></span>  
  
     <span data-ttu-id="dd1b6-292">以下属性现在可用。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-292">The following properties are now available.</span></span> <span data-ttu-id="dd1b6-293">按下表所示更改属性值：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-293">Change the values of the properties as shown in the following table:</span></span>  
  
    |<span data-ttu-id="dd1b6-294">properties</span><span class="sxs-lookup"><span data-stu-id="dd1b6-294">Property</span></span>|<span data-ttu-id="dd1b6-295">默认值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-295">Default value</span></span>|<span data-ttu-id="dd1b6-296">新值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-296">New value</span></span>|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|<span data-ttu-id="dd1b6-297">无值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-297">No value</span></span>|<span data-ttu-id="dd1b6-298">4</span><span class="sxs-lookup"><span data-stu-id="dd1b6-298">4</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd1b6-299"><xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 的默认值实际为 0，这意味着算法将自动确定 Bucket 的最佳数量。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-299">The default value of <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> is actually 0, which means that the algorithm automatically determines the optimum number of buckets.</span></span> <span data-ttu-id="dd1b6-300">因此，如果希望将该属性的值重置为其默认值，请键入 0。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-300">Therefore, if you want to reset the value of this property to its default, type 0.</span></span>  
  
9. <span data-ttu-id="dd1b6-301">在数据挖掘设计器中，单击 "**挖掘模型**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-301">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
     <span data-ttu-id="dd1b6-302">请注意，在您添加挖掘结构列的副本时，该副本的用法标志将自动设置为 `Ignore`。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-302">Notice that when you add a copy of a mining structure column, the usage flag for the copy is automatically set to `Ignore`.</span></span> <span data-ttu-id="dd1b6-303">通常，当您向挖掘结构中添加列的副本时，您不会将该副本与原始列一起用于分析，否则算法会发现两列之间存在可能掩盖其他关系的密切关联。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-303">Usually, when you add a copy of a column to a mining structure, you would not use the copy for analysis together with the original column, or the algorithm will find a strong correlation between the two columns that might obscure other relationships.</span></span>  
  
##  <a name="add-a-new-mining-model-to-the-mining-structure"></a><a name="bkmk_NewModel"></a><span data-ttu-id="dd1b6-304">向挖掘结构添加新的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-304">Add a New Mining Model to the Mining Structure</span></span>  
 <span data-ttu-id="dd1b6-305">至此您已针对目标属性创建了一个新的分组，现在需要添加一个使用该离散化列的新挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-305">Now that you have created a new grouping for the target attribute, you need to add a new mining model that uses the discretized column.</span></span> <span data-ttu-id="dd1b6-306">完成后，CallCenter 挖掘结构将有两个挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-306">When you are done, the CallCenter mining structure will have two mining models:</span></span>  
  
-   <span data-ttu-id="dd1b6-307">挖掘模型 Call Center Default NN 将 ServiceGrade 值作为连续范围来处理。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-307">The mining model, Call Center Default NN, handles the ServiceGrade values as a continuous range.</span></span>  
  
-   <span data-ttu-id="dd1b6-308">您将创建一个新的挖掘模型装箱 NN，它使用作为其目标结果的 ServiceGrade 列的值，分布到大小相等的四个存储桶中。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-308">You will create a new mining model, Call Center Binned NN, that uses as its target outcomes the values of the ServiceGrade column, distributed into four buckets of equal size.</span></span>  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a><span data-ttu-id="dd1b6-309">添加基于新的离散化列的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-309">To add a mining model based on the new discretized column</span></span>  
  
1.  <span data-ttu-id="dd1b6-310">在解决方案资源管理器中，右键单击刚创建的挖掘结构，然后选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-310">In Solution Explorer, right-click the mining structure that you just created, and select **Open**.</span></span>  
  
2.  <span data-ttu-id="dd1b6-311">单击 **“挖掘模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-311">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="dd1b6-312">单击 "**创建相关挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-312">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="dd1b6-313">在 "**新建挖掘模型**" 对话框的 "**模型名称**" 中，键入 `Call Center Binned NN` 。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-313">In the **New Mining Model** dialog box, for **Model name**, type `Call Center Binned NN`.</span></span> <span data-ttu-id="dd1b6-314">在 "**算法名称**" 下拉列表中，选择 " **Microsoft 神经网络**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-314">In the **Algorithm name** dropdown list, select **Microsoft Neural Network**.</span></span>  
  
5.  <span data-ttu-id="dd1b6-315">在新挖掘模型中包含的列列表中，找到 ServiceGrade，将用法从 `Predict` 改为 `Ignore`。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-315">In the list of columns contained in the new mining model, locate ServiceGrade, and change the usage from `Predict` to `Ignore`.</span></span>  
  
6.  <span data-ttu-id="dd1b6-316">同样，找到 ServiceGrade Binned，将用法从 `Ignore` 改为 `Predict`。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-316">Similarly, locate ServiceGrade Binned, and change the usage from `Ignore` to `Predict`.</span></span>  
  
##  <a name="create-an-alias-for-the-target-column"></a><a name="bkmk_Alias2"></a><span data-ttu-id="dd1b6-317">为目标列创建别名</span><span class="sxs-lookup"><span data-stu-id="dd1b6-317">Create an Alias for the Target Column</span></span>  
 <span data-ttu-id="dd1b6-318">通常，您不能比较使用不同可预测属性的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-318">Ordinarily you cannot compare mining models that use different predictable attributes.</span></span> <span data-ttu-id="dd1b6-319">但是，您可以为挖掘模型列创建别名。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-319">However, you can create an alias for a mining model column.</span></span> <span data-ttu-id="dd1b6-320">也就是说，您可以在挖掘模型中重命名列 ServiceGrade 装箱，使其具有与原始列相同的名称。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-320">That is, you can rename the column, ServiceGrade Binned, within the mining model so that it has the same name as the original column.</span></span> <span data-ttu-id="dd1b6-321">然后可以在一个准确性图表中直接比较这两个模型，即使数据是以不同的方式离散化的也是如此。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-321">You can then directly compare these two models in an accuracy chart, even though the data is discretized differently.</span></span>  
  
###  <a name="to-add-an-alias-for-a-mining-structure-column-in-a-mining-model"></a><a name="bkmk_Alias"></a><span data-ttu-id="dd1b6-322">为挖掘模型中的挖掘结构列添加别名</span><span class="sxs-lookup"><span data-stu-id="dd1b6-322">To add an alias for a mining structure column in a mining model</span></span>  
  
1.  <span data-ttu-id="dd1b6-323">在 "**挖掘模型**" 选项卡的 "**结构**" 下，选择 ServiceGrade 装箱。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-323">In the **Mining Models** tab, under **Structure**, select ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="dd1b6-324">请注意，"**属性**" 窗口显示对象的属性 ScalarMiningStructure 列。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-324">Note that the **Properties** window displays the properties of the object, ScalarMiningStructure column.</span></span>  
  
2.  <span data-ttu-id="dd1b6-325">在挖掘模型列 ServiceGrade Binned NN 下方单击与 ServiceGrade Binned 列对应的单元格。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-325">Under the column for the mining model, ServiceGrade Binned NN, click the cell corresponding to the column ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="dd1b6-326">请注意，现在 "**属性**" 窗口显示对象 MiningModelColumn 的属性。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-326">Note that now the **Properties** window displays the properties for the object, MiningModelColumn.</span></span>  
  
3.  <span data-ttu-id="dd1b6-327">找到 "**名称**" 属性，并将值更改为 `ServiceGrade` 。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-327">Locate the **Name** property, and change the value to `ServiceGrade`.</span></span>  
  
4.  <span data-ttu-id="dd1b6-328">找到 "**说明**" 属性并键入**临时列别名**。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-328">Locate the **Description** property and type **Temporary column alias**.</span></span>  
  
     <span data-ttu-id="dd1b6-329">"**属性**" 窗口应包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-329">The **Properties** window should contain the following information:</span></span>  
  
    |<span data-ttu-id="dd1b6-330">属性</span><span class="sxs-lookup"><span data-stu-id="dd1b6-330">Property</span></span>|<span data-ttu-id="dd1b6-331">值</span><span class="sxs-lookup"><span data-stu-id="dd1b6-331">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="dd1b6-332">**说明**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-332">**Description**</span></span>|<span data-ttu-id="dd1b6-333">Temporary column alias</span><span class="sxs-lookup"><span data-stu-id="dd1b6-333">Temporary column alias</span></span>|  
    |<span data-ttu-id="dd1b6-334">**ID**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-334">**ID**</span></span>|<span data-ttu-id="dd1b6-335">ServiceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="dd1b6-335">ServiceGrade Binned</span></span>|  
    |<span data-ttu-id="dd1b6-336">**建模标志**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-336">**Modeling Flags**</span></span>||  
    |<span data-ttu-id="dd1b6-337">**名称**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-337">**Name**</span></span>|<span data-ttu-id="dd1b6-338">Service Grade</span><span class="sxs-lookup"><span data-stu-id="dd1b6-338">Service Grade</span></span>|  
    |<span data-ttu-id="dd1b6-339">**SourceColumn ID**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-339">**SourceColumn ID**</span></span>|<span data-ttu-id="dd1b6-340">Service Grade 1</span><span class="sxs-lookup"><span data-stu-id="dd1b6-340">Service Grade 1</span></span>|  
    |<span data-ttu-id="dd1b6-341">**使用情况**</span><span class="sxs-lookup"><span data-stu-id="dd1b6-341">**Usage**</span></span>|<span data-ttu-id="dd1b6-342">Predict</span><span class="sxs-lookup"><span data-stu-id="dd1b6-342">Predict</span></span>|  
  
5.  <span data-ttu-id="dd1b6-343">单击 "**挖掘模型**" 选项卡中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-343">Click anywhere in the **Mining Model** tab.</span></span>  
  
     <span data-ttu-id="dd1b6-344">网格将更新以显示新的临时列别名，并显示在 `ServiceGrade` 列用法旁边。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-344">The grid is updated to show the new temporary column alias, `ServiceGrade`, beside the column usage.</span></span> <span data-ttu-id="dd1b6-345">包含挖掘结构及两个挖掘模型的网格应如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd1b6-345">The grid containing the mining structure and two mining models should look like the following:</span></span>  
  
    |<span data-ttu-id="dd1b6-346">结构</span><span class="sxs-lookup"><span data-stu-id="dd1b6-346">Structure</span></span>|<span data-ttu-id="dd1b6-347">Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="dd1b6-347">Call Center Default NN</span></span>|<span data-ttu-id="dd1b6-348">Call Center Binned NN</span><span class="sxs-lookup"><span data-stu-id="dd1b6-348">Call Center Binned NN</span></span>|  
    |---------------|----------------------------|---------------------------|  
    ||<span data-ttu-id="dd1b6-349">Microsoft 神经网络</span><span class="sxs-lookup"><span data-stu-id="dd1b6-349">Microsoft Neural Network</span></span>|<span data-ttu-id="dd1b6-350">Microsoft 神经网络</span><span class="sxs-lookup"><span data-stu-id="dd1b6-350">Microsoft Neural Network</span></span>|  
    |<span data-ttu-id="dd1b6-351">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="dd1b6-351">AutomaticResponses</span></span>|<span data-ttu-id="dd1b6-352">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-352">Input</span></span>|<span data-ttu-id="dd1b6-353">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-353">Input</span></span>|  
    |<span data-ttu-id="dd1b6-354">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="dd1b6-354">AverageTimePerIssue</span></span>|<span data-ttu-id="dd1b6-355">Predict</span><span class="sxs-lookup"><span data-stu-id="dd1b6-355">Predict</span></span>|<span data-ttu-id="dd1b6-356">Predict</span><span class="sxs-lookup"><span data-stu-id="dd1b6-356">Predict</span></span>|  
    |<span data-ttu-id="dd1b6-357">调用</span><span class="sxs-lookup"><span data-stu-id="dd1b6-357">Calls</span></span>|<span data-ttu-id="dd1b6-358">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-358">Input</span></span>|<span data-ttu-id="dd1b6-359">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-359">Input</span></span>|  
    |<span data-ttu-id="dd1b6-360">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="dd1b6-360">DayOfWeek</span></span>|<span data-ttu-id="dd1b6-361">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-361">Input</span></span>|<span data-ttu-id="dd1b6-362">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-362">Input</span></span>|  
    |<span data-ttu-id="dd1b6-363">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="dd1b6-363">FactCallCenterID</span></span>|<span data-ttu-id="dd1b6-364">密钥</span><span class="sxs-lookup"><span data-stu-id="dd1b6-364">Key</span></span>|<span data-ttu-id="dd1b6-365">密钥</span><span class="sxs-lookup"><span data-stu-id="dd1b6-365">Key</span></span>|  
    |<span data-ttu-id="dd1b6-366">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="dd1b6-366">IssuesRaised</span></span>|<span data-ttu-id="dd1b6-367">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-367">Input</span></span>|<span data-ttu-id="dd1b6-368">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-368">Input</span></span>|  
    |<span data-ttu-id="dd1b6-369">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-369">LevelOneOperators</span></span>|<span data-ttu-id="dd1b6-370">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-370">Input</span></span>|<span data-ttu-id="dd1b6-371">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-371">Input</span></span>|  
    |<span data-ttu-id="dd1b6-372">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-372">LevelTwoOperators</span></span>|<span data-ttu-id="dd1b6-373">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-373">Input</span></span>|<span data-ttu-id="dd1b6-374">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-374">Input</span></span>|  
    |<span data-ttu-id="dd1b6-375">Orders</span><span class="sxs-lookup"><span data-stu-id="dd1b6-375">Orders</span></span>|<span data-ttu-id="dd1b6-376">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-376">Input</span></span>|<span data-ttu-id="dd1b6-377">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-377">Input</span></span>|  
    |<span data-ttu-id="dd1b6-378">ServceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="dd1b6-378">ServceGrade Binned</span></span>|<span data-ttu-id="dd1b6-379">忽略</span><span class="sxs-lookup"><span data-stu-id="dd1b6-379">Ignore</span></span>|<span data-ttu-id="dd1b6-380">预测 (ServiceGrade)</span><span class="sxs-lookup"><span data-stu-id="dd1b6-380">Predict (ServiceGrade)</span></span>|  
    |<span data-ttu-id="dd1b6-381">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="dd1b6-381">ServiceGrade</span></span>|<span data-ttu-id="dd1b6-382">Predict</span><span class="sxs-lookup"><span data-stu-id="dd1b6-382">Predict</span></span>|<span data-ttu-id="dd1b6-383">忽略</span><span class="sxs-lookup"><span data-stu-id="dd1b6-383">Ignore</span></span>|  
    |<span data-ttu-id="dd1b6-384">移位</span><span class="sxs-lookup"><span data-stu-id="dd1b6-384">Shift</span></span>|<span data-ttu-id="dd1b6-385">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-385">Input</span></span>|<span data-ttu-id="dd1b6-386">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-386">Input</span></span>|  
    |<span data-ttu-id="dd1b6-387">Total Operators</span><span class="sxs-lookup"><span data-stu-id="dd1b6-387">Total Operators</span></span>|<span data-ttu-id="dd1b6-388">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-388">Input</span></span>|<span data-ttu-id="dd1b6-389">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-389">Input</span></span>|  
    |<span data-ttu-id="dd1b6-390">WageType</span><span class="sxs-lookup"><span data-stu-id="dd1b6-390">WageType</span></span>|<span data-ttu-id="dd1b6-391">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-391">Input</span></span>|<span data-ttu-id="dd1b6-392">输入</span><span class="sxs-lookup"><span data-stu-id="dd1b6-392">Input</span></span>|  
  
## <a name="process-all-models"></a><span data-ttu-id="dd1b6-393">处理所有模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-393">Process All Models</span></span>  
 <span data-ttu-id="dd1b6-394">最后，为了确保您创建的模型易于比较，将为默认模型和装箱模型均设置种子参数。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-394">Finally, to ensure that the models you have created can be easily compared, you will set the seed parameter for both the default and binned models.</span></span> <span data-ttu-id="dd1b6-395">设置种子值可保证每个模型都从同一点开始处理数据。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-395">Setting a seed value guarantees that each model starts processing the data from the same point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd1b6-396">如果不为种子参数指定一个数值，SQL Server Analysis Services 将基于模型的名称来生成一个种子。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-396">If you do not specify a numeric value for the seed parameter, SQL Server Analysis Services will generate a seed based on the name of the model.</span></span> <span data-ttu-id="dd1b6-397">由于这些模型始终具有不同的名称，因此您必须设置一个种子值，以确保这两个模型按相同的顺序来处理数据。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-397">Because the models always have different names, you must set a seed value to ensure that they process data in the same order.</span></span>  
  
###  <a name="to-specify-the-seed-and-process-the-models"></a><a name="bkmk_SeedProcess"></a><span data-ttu-id="dd1b6-398">指定种子并处理模型</span><span class="sxs-lookup"><span data-stu-id="dd1b6-398">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="dd1b6-399">在 "**挖掘模型**" 选项卡中，右键单击名为呼叫中心-LR 的模型的列，然后选择 "**设置算法参数**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-399">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="dd1b6-400">在 HOLDOUT_SEED 参数所在的行中，单击 "**值**" 下的空单元，然后键入 `1` 。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-400">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="dd1b6-401">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-401">Click **OK**.</span></span> <span data-ttu-id="dd1b6-402">对与此结构关联的每个模型重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-402">Repeat this step for each model associated with the structure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd1b6-403">选择哪个值作为种子无关紧要，关键是您需要对所有相关模型使用同一个种子。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-403">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="dd1b6-404">在 "**挖掘模型**" 菜单中，选择 "**处理挖掘结构和所有模型**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-404">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="dd1b6-405">单击 **"是"** 将更新后的数据挖掘项目部署到服务器。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-405">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="dd1b6-406">在 "**处理挖掘模型**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-406">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="dd1b6-407">单击 "**关闭**" 关闭 "**处理进度**" 对话框，然后再次单击 "**处理挖掘模型**" 对话框中的 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-407">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="dd1b6-408">至此您已创建两个相关的挖掘模型，接下来将浏览数据以发现数据中的关系。</span><span class="sxs-lookup"><span data-stu-id="dd1b6-408">Now that you have created the two related mining models, you will explore the data to discover relationships in the data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="dd1b6-409">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="dd1b6-409">Next Task in Lesson</span></span>  
 [<span data-ttu-id="dd1b6-410">探索呼叫中心模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="dd1b6-410">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="dd1b6-411">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd1b6-411">See Also</span></span>  
 [<span data-ttu-id="dd1b6-412">挖掘结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="dd1b6-412">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
