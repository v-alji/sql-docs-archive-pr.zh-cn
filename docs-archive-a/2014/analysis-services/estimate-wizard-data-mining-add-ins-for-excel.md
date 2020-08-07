---
title: 估计向导 (Excel 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace9fa3a62690061677312d4f7dbb6b8a1d0ea5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690855"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="3ce77-102">估计向导（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="3ce77-102">Estimate Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="3ce77-103">![“数据挖掘”功能区中的估计向导](media/dmc-estimate.gif "“数据挖掘”功能区中的估计向导")</span><span class="sxs-lookup"><span data-stu-id="3ce77-103">![Estimate wizard in Data Mining ribbon](media/dmc-estimate.gif "Estimate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="3ce77-104">**估计**向导帮助您创建估计模型。</span><span class="sxs-lookup"><span data-stu-id="3ce77-104">The **Estimate** wizard helps you create an estimation model.</span></span> <span data-ttu-id="3ce77-105">估计模型从数据中提取模式，并使用这些模式预测将影响结果的因素。</span><span class="sxs-lookup"><span data-stu-id="3ce77-105">An estimation model extracts patterns from data and uses the patterns to predict the factors that affect outcomes.</span></span>  
  
 <span data-ttu-id="3ce77-106">估计用于预测数字结果。</span><span class="sxs-lookup"><span data-stu-id="3ce77-106">Estimation is used for predicting numeric outcomes.</span></span> <span data-ttu-id="3ce77-107">例如，如果目标列包含学校的升学率（升学率以百分比表示），则可分析有可能提高或降低升学率的因素，如每个学校的学生数量、学生与教师的比例以及教师数量。</span><span class="sxs-lookup"><span data-stu-id="3ce77-107">For example, if your target column contains graduation rates for schools, with graduation rates expressed as percentages, you could analyze factors that potentially increase or decrease graduation rates, such as the number of students per school, the student-teacher ratio, and the number of teachers.</span></span>  
  
## <a name="using-the-estimate-data-wizard"></a><span data-ttu-id="3ce77-108">使用估计数据向导</span><span class="sxs-lookup"><span data-stu-id="3ce77-108">Using the Estimate Data Wizard</span></span>  
  
1.  <span data-ttu-id="3ce77-109">在 "**数据挖掘**" 功能区上，单击 "**估计**"。</span><span class="sxs-lookup"><span data-stu-id="3ce77-109">On the **Data Mining** ribbon, click **Estimate**.</span></span>  
  
2.  <span data-ttu-id="3ce77-110">在 "**选择源数据**" 对话框中，选择要使用的源数据。</span><span class="sxs-lookup"><span data-stu-id="3ce77-110">In the **Select Source Data** dialog box, select the source data to use.</span></span> <span data-ttu-id="3ce77-111">您可以在 Excel**表**、Excel**数据区域**或**外部数据源**中使用数据。</span><span class="sxs-lookup"><span data-stu-id="3ce77-111">You can use data in an Excel **Table**, an Excel **Data Range**, or from an **External data source**.</span></span>  
  
     <span data-ttu-id="3ce77-112">如果使用外部数据源，您可以创建自定义视图或查询并将其另存为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源。</span><span class="sxs-lookup"><span data-stu-id="3ce77-112">If you use an external data source, you can create custom views or queries and save them as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="3ce77-113">在 "**估计**" 对话框中，选择**要分析的列**。</span><span class="sxs-lookup"><span data-stu-id="3ce77-113">In the **Estimation** dialog box, select the **Column to analyze**.</span></span>  
  
     <span data-ttu-id="3ce77-114">目标列必须包含连续的数值数据。</span><span class="sxs-lookup"><span data-stu-id="3ce77-114">The target column must contain continuous numeric data.</span></span>  
  
4.  <span data-ttu-id="3ce77-115">选中 "**输入列**" 复选框，选择要用作输入的列。</span><span class="sxs-lookup"><span data-stu-id="3ce77-115">Select columns to use as input by checking the **Input columns** checkbox.</span></span>  
  
     <span data-ttu-id="3ce77-116">这些列将用于创建模式。</span><span class="sxs-lookup"><span data-stu-id="3ce77-116">These columns will be used to create the patterns.</span></span> <span data-ttu-id="3ce77-117">您应当从分析中删除那些不可能有用的列（如 ID 号）或包含无关数据的列。</span><span class="sxs-lookup"><span data-stu-id="3ce77-117">You should eliminate from analysis any columns that are not likely to help, such as ID numbers, or columns that contain irrelevant data.</span></span>  
  
5.  <span data-ttu-id="3ce77-118">**估计**向导为您的数据集选择最佳算法。</span><span class="sxs-lookup"><span data-stu-id="3ce77-118">The **Estimate** wizard selects the optimum algorithm for your data set.</span></span> <span data-ttu-id="3ce77-119">不过，可以单击 "**参数**" 打开 "**算法参数**" 对话框并设置高级选项。</span><span class="sxs-lookup"><span data-stu-id="3ce77-119">However, you can click **Parameters** to open the **Algorithm Parameters** dialog box and set advanced options.</span></span>  
  
6.  <span data-ttu-id="3ce77-120">如果你的数据是数值，并且你可以使用 Microsoft 线性回归方法，则可以在**回归量**框中检查你知道 (或强烈怀疑) 与可预测值相关的任何数值列。</span><span class="sxs-lookup"><span data-stu-id="3ce77-120">If your data is numeric and you can use the Microsoft Linear Regression method, you can check the **Regressor** box for any numeric columns that you know (or strongly suspect) to be correlated with the predictable value.</span></span>  
  
     <span data-ttu-id="3ce77-121">然后，此算法将对该列中的值进行测试以确定它们是否会影响结果。</span><span class="sxs-lookup"><span data-stu-id="3ce77-121">The algorithm will then test the values in that column to determine if they affect the outcomes.</span></span> <span data-ttu-id="3ce77-122">如果不确定，请单击 "**建议**"，算法将测试所有列，并自动检测要用作回归量的最佳值。</span><span class="sxs-lookup"><span data-stu-id="3ce77-122">If you are unsure, click **Suggest** and the algorithm will test all column and automatically detect the best values to use as regressors.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ce77-123">回归量是创建估计所必需的。</span><span class="sxs-lookup"><span data-stu-id="3ce77-123">A regressor is required to create an estimate.</span></span> <span data-ttu-id="3ce77-124">向导总是基于最初传递的数据来推荐最佳回归量。</span><span class="sxs-lookup"><span data-stu-id="3ce77-124">The wizard always recommends the best regressor, based on an initial pass over the data.</span></span> <span data-ttu-id="3ce77-125">因此，如果您不能确定，最好接受向导所推荐的选择。</span><span class="sxs-lookup"><span data-stu-id="3ce77-125">Therefore, if you are not sure, it is best to accept the recommended selections.</span></span>  
  
7.  <span data-ttu-id="3ce77-126">在 "将**数据拆分为定型集和测试集**" 页上，指定是否要创建用于测试的一小部分数据。</span><span class="sxs-lookup"><span data-stu-id="3ce77-126">On the **Split data into training and testing sets** page, specify whether you want to create a small subset of the data for testing.</span></span>  
  
8.  <span data-ttu-id="3ce77-127">在 "**完成**" 页上，提供新挖掘结构和挖掘模式的名称，或接受提供的默认名称。</span><span class="sxs-lookup"><span data-stu-id="3ce77-127">On the **Finish** page, provide names for the new mining structure and mining mode, or accept the default names that are provided.</span></span>  
  
9. <span data-ttu-id="3ce77-128">设置模型使用选项。</span><span class="sxs-lookup"><span data-stu-id="3ce77-128">Set options for using the model.</span></span>  
  
    -   <span data-ttu-id="3ce77-129">选择 "**浏览**" 可立即在查看器中打开模型。</span><span class="sxs-lookup"><span data-stu-id="3ce77-129">Select **Browse** to immediately open the model in a viewer.</span></span>  
  
         <span data-ttu-id="3ce77-130">此图形查看器会显示一个依赖关系网络图形以及由该算法生成的决策树。</span><span class="sxs-lookup"><span data-stu-id="3ce77-130">This graphical viewer displays a dependency network graph and the decision tree generated by the algorithm.</span></span> <span data-ttu-id="3ce77-131">通过研究这些信息，您可以更好地理解影响估计值的因素。</span><span class="sxs-lookup"><span data-stu-id="3ce77-131">By exploring this information, you can better understand the factors that contribute to the estimated values.</span></span>  
  
    -   <span data-ttu-id="3ce77-132">选择 "**启用钻取**" 可允许分析的用户查看基础数据。</span><span class="sxs-lookup"><span data-stu-id="3ce77-132">Select **Enable drillthrough** to let users of your analysis view the underlying data.</span></span>  
  
         <span data-ttu-id="3ce77-133">此选项仅在您使用决策树或线性回归算法时可用。</span><span class="sxs-lookup"><span data-stu-id="3ce77-133">This option is available only if you use the Decision Trees opr Linear Regression algorithms.</span></span>  
  
    -   <span data-ttu-id="3ce77-134">**使用临时模型**。</span><span class="sxs-lookup"><span data-stu-id="3ce77-134">**Use temporary model**.</span></span> <span data-ttu-id="3ce77-135">如果您选择此选项，模型将不会被保存到服务器。</span><span class="sxs-lookup"><span data-stu-id="3ce77-135">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="3ce77-136">在您关闭 Excel 时，临时模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="3ce77-136">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-estimation-models"></a><span data-ttu-id="3ce77-137">有关估计模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="3ce77-137">More About Estimation Models</span></span>  
 <span data-ttu-id="3ce77-138">**估计**向导支持使用以下任何算法：</span><span class="sxs-lookup"><span data-stu-id="3ce77-138">The **Estimate** wizard supports the use of any of the following algorithms:</span></span>  
  
-   <span data-ttu-id="3ce77-139">Microsoft 决策树算法</span><span class="sxs-lookup"><span data-stu-id="3ce77-139">Microsoft Decision Tree algorithm</span></span>  
  
-   <span data-ttu-id="3ce77-140">Microsoft 线性回归算法</span><span class="sxs-lookup"><span data-stu-id="3ce77-140">Microsoft Linear Regression algorithm</span></span>  
  
-   <span data-ttu-id="3ce77-141">Microsoft 逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="3ce77-141">Microsoft Logistic Regression algorithm</span></span>  
  
-   <span data-ttu-id="3ce77-142">Microsoft 神经网络算法</span><span class="sxs-lookup"><span data-stu-id="3ce77-142">Microsoft Neural network algorithm</span></span>  
  
 <span data-ttu-id="3ce77-143">在 "**算法参数**" 对话框中，可以根据所选的算法设置其他高级选项。</span><span class="sxs-lookup"><span data-stu-id="3ce77-143">In the **Algorithm Parameters** dialog box, you can set additional advanced options, depending on which algorithm you chose.</span></span> <span data-ttu-id="3ce77-144">有关每种算法的选项的信息，请参阅 SQL Server 联机丛书中的下列主题：</span><span class="sxs-lookup"><span data-stu-id="3ce77-144">For information on the options for each algorithm see these topics in SQL Server Books Online:</span></span>  
  
 [<span data-ttu-id="3ce77-145">Microsoft 决策树算法技术参考</span><span class="sxs-lookup"><span data-stu-id="3ce77-145">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="3ce77-146">Microsoft 线性回归算法技术参考</span><span class="sxs-lookup"><span data-stu-id="3ce77-146">Microsoft Linear Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="3ce77-147">Microsoft 逻辑回归算法技术参考</span><span class="sxs-lookup"><span data-stu-id="3ce77-147">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="3ce77-148">Microsoft 神经网络算法技术参考</span><span class="sxs-lookup"><span data-stu-id="3ce77-148">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="3ce77-149">要求</span><span class="sxs-lookup"><span data-stu-id="3ce77-149">Requirements</span></span>  
 <span data-ttu-id="3ce77-150">若要使用估计数据向导，您必须连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="3ce77-150">To use the Estimate Data Wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="3ce77-151">有关如何创建连接的信息，请参阅[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce77-151">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="3ce77-152">若要使用估计算法，尝试预测的结果必须表示为数值，如货币、销售额、日期或时间。</span><span class="sxs-lookup"><span data-stu-id="3ce77-152">To use the estimation algorithm, the outcome that you are trying to predict must be expressed as a numeric value, such as a currency, sales amount, date, or time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce77-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ce77-153">See Also</span></span>  
 <span data-ttu-id="3ce77-154">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="3ce77-154">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="3ce77-155">决策树关系图演练 &#40;数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="3ce77-155">Decision Tree Diagram Walkthrough  &#40;Data Mining Add-ins&#41;</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
