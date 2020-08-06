---
title: 为呼叫中心数据添加数据源视图 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6d3d9aa3153b39b9ef7f4a92af20e0e8791780bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691418"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="f7c97-102">为呼叫中心数据添加数据源视图（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="f7c97-102">Adding a Data Source View for Call Center Data (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="f7c97-103">在本任务中，添加一个将用于访问呼叫中心数据的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="f7c97-103">In this task, you add a data source view that will be used to access the call center data.</span></span> <span data-ttu-id="f7c97-104">将使用相同的数据来生成用于探索的初始神经网络模型以及用于提供建议的逻辑回归模型。</span><span class="sxs-lookup"><span data-stu-id="f7c97-104">The same data will be used to build both the initial neural network model for exploration, and the logistic regression model that you will use to make recommendations.</span></span>  
  
 <span data-ttu-id="f7c97-105">您还将使用数据源视图设计器向一周中某天添加列。</span><span class="sxs-lookup"><span data-stu-id="f7c97-105">You will also use the Data Source View Designer to add a column for the day of the week.</span></span> <span data-ttu-id="f7c97-106">这是因为尽管源数据按日期跟踪呼叫中心数据，您的经验告诉您呼叫量和服务质量存在重复模式，取决于该天是周末还是工作日。</span><span class="sxs-lookup"><span data-stu-id="f7c97-106">That is because, although the source data tracks call center data by dates, your experience tells you that there are recurring patterns both in terms of call volume and service quality, depending on whether the day is a weekend or a weekday.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f7c97-107">过程</span><span class="sxs-lookup"><span data-stu-id="f7c97-107">Procedures</span></span>  
  
#### <a name="to-add-a-data-source-view"></a><span data-ttu-id="f7c97-108">添加数据源视图</span><span class="sxs-lookup"><span data-stu-id="f7c97-108">To add a data source view</span></span>  
  
1.  <span data-ttu-id="f7c97-109">在**解决方案资源管理器**中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="f7c97-109">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="f7c97-110">系统将打开数据源视图向导。</span><span class="sxs-lookup"><span data-stu-id="f7c97-110">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="f7c97-111">在“欢迎使用数据源视图向导”  页上，单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="f7c97-111">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="f7c97-112">在 "**选择数据源**" 页的 "**关系数据源**" 下，选择 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 数据源。</span><span class="sxs-lookup"><span data-stu-id="f7c97-112">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span> <span data-ttu-id="f7c97-113">如果您没有此数据源，请参阅[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c97-113">If you do not have this data source, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="f7c97-114">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f7c97-114">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="f7c97-115">在 "**选择表和视图**" 页上，选择下表，然后单击右箭头将其添加到数据源视图：</span><span class="sxs-lookup"><span data-stu-id="f7c97-115">On the **Select Tables and Views** page, select the following table and then click the right arrow to add it to the data source view:</span></span>  
  
    -   <span data-ttu-id="f7c97-116">**FactCallCenter (dbo)**</span><span class="sxs-lookup"><span data-stu-id="f7c97-116">**FactCallCenter (dbo)**</span></span>  
  
    -   <span data-ttu-id="f7c97-117">**DimDate**</span><span class="sxs-lookup"><span data-stu-id="f7c97-117">**DimDate**</span></span>  
  
5.  <span data-ttu-id="f7c97-118">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f7c97-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f7c97-119">在 "**完成向导**" 页上，默认将数据源视图命名为 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f7c97-119">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="f7c97-120">将名称更改为**CallCenter**，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="f7c97-120">Change the name to **CallCenter**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="f7c97-121">数据源视图设计器将打开以显示**CallCenter**数据源视图。</span><span class="sxs-lookup"><span data-stu-id="f7c97-121">Data Source View Designer opens to display the **CallCenter** data source view.</span></span>  
  
7.  <span data-ttu-id="f7c97-122">在 "数据源视图" 窗格中右键单击，然后选择 "**添加/删除表**"。</span><span class="sxs-lookup"><span data-stu-id="f7c97-122">Right-click inside the Data Source View pane, and select **Add/Remove Tables**.</span></span> <span data-ttu-id="f7c97-123">选择表**DimDate** ，并单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="f7c97-123">Select the table, **DimDate** and click **OK**.</span></span>  
  
     <span data-ttu-id="f7c97-124">应在 `DateKey` 每个表中的列之间自动添加关系。</span><span class="sxs-lookup"><span data-stu-id="f7c97-124">A relationship should be automatically added between the `DateKey` columns in each table.</span></span> <span data-ttu-id="f7c97-125">您将使用此关系从**DimDate**表中获取列**EnglishDayNameOfWeek**，并在模型中使用它。</span><span class="sxs-lookup"><span data-stu-id="f7c97-125">You will use this relationship to get the column, **EnglishDayNameOfWeek**, from the **DimDate** table and use it in your model.</span></span>  
  
8.  <span data-ttu-id="f7c97-126">在数据源视图设计器中，右键单击表**FactCallCenter**，然后选择 "**新建命名计算**"。</span><span class="sxs-lookup"><span data-stu-id="f7c97-126">In the Data Source View designer, right-click the table, **FactCallCenter**, and select **New Named Calculation**.</span></span>  
  
     <span data-ttu-id="f7c97-127">在 "**创建命名计算**" 对话框中，键入以下值：</span><span class="sxs-lookup"><span data-stu-id="f7c97-127">In the **Create Named Calculation** dialog box, type the following values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="f7c97-128">**列名**</span><span class="sxs-lookup"><span data-stu-id="f7c97-128">**Column name**</span></span>|<span data-ttu-id="f7c97-129">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="f7c97-129">DayOfWeek</span></span>|  
    |<span data-ttu-id="f7c97-130">**说明**</span><span class="sxs-lookup"><span data-stu-id="f7c97-130">**Description**</span></span>|<span data-ttu-id="f7c97-131">从 DimDate 表获取一周中的某天</span><span class="sxs-lookup"><span data-stu-id="f7c97-131">Get day of week from DimDate table</span></span>|  
    |<span data-ttu-id="f7c97-132">**表达式**</span><span class="sxs-lookup"><span data-stu-id="f7c97-132">**Expression**</span></span>|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     <span data-ttu-id="f7c97-133">若要验证表达式是否创建了所需的数据，请右键单击表**FactCallCenter**，然后选择 "**浏览数据**"。</span><span class="sxs-lookup"><span data-stu-id="f7c97-133">To verify that the expression creates the data you need, right-click the table **FactCallCenter**, and then select **Explore Data**.</span></span>  
  
9. <span data-ttu-id="f7c97-134">花点时间查看可用的数据，以便您可以了解在数据挖掘中如何使用它：</span><span class="sxs-lookup"><span data-stu-id="f7c97-134">Take a minute to review the data that is available, so that you can understand how it is used in data mining:</span></span>  
  
|<span data-ttu-id="f7c97-135">列名称</span><span class="sxs-lookup"><span data-stu-id="f7c97-135">Column name</span></span>|<span data-ttu-id="f7c97-136">包含</span><span class="sxs-lookup"><span data-stu-id="f7c97-136">Contains</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="f7c97-137">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="f7c97-137">FactCallCenterID</span></span>|<span data-ttu-id="f7c97-138">数据导入到数据仓库中时创建的一个任意键。</span><span class="sxs-lookup"><span data-stu-id="f7c97-138">An arbitrary key created when the data was imported to the data warehouse.</span></span><br /><br /> <span data-ttu-id="f7c97-139">此列标识唯一的记录并应作为数据挖掘模型的事例键。</span><span class="sxs-lookup"><span data-stu-id="f7c97-139">This column identifies unique records and should be used as the case key for the data mining model.</span></span>|  
|<span data-ttu-id="f7c97-140">DateKey</span><span class="sxs-lookup"><span data-stu-id="f7c97-140">DateKey</span></span>|<span data-ttu-id="f7c97-141">呼叫中心运营的日期，以整数表示。</span><span class="sxs-lookup"><span data-stu-id="f7c97-141">The date of the call center operation, expressed as an integer.</span></span> <span data-ttu-id="f7c97-142">整数日期键在数据仓库中经常用到，但是如果要按日期值分组，您可能要获取日期/时间格式的日期。</span><span class="sxs-lookup"><span data-stu-id="f7c97-142">Integer date keys are often used in data warehouses, but you might want to obtain the date in date/time format if you were going to group by date values.</span></span><br /><br /> <span data-ttu-id="f7c97-143">请注意由于供应商为每个运营日中的每个班次都提供了一个单独的报表，因此日期不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f7c97-143">Note that dates are not unique because the vendor provides a separate report for each shift in each day of operation.</span></span>|  
|<span data-ttu-id="f7c97-144">WageType</span><span class="sxs-lookup"><span data-stu-id="f7c97-144">WageType</span></span>|<span data-ttu-id="f7c97-145">指示日期是工作日、周末还是假日。</span><span class="sxs-lookup"><span data-stu-id="f7c97-145">Indicates whether the day was a weekday, a weekend, or a holiday.</span></span><br /><br /> <span data-ttu-id="f7c97-146">与工作日相比，客户服务质量存在差异，因此，你将使用此列作为输入。</span><span class="sxs-lookup"><span data-stu-id="f7c97-146">It is possible that there is a difference in quality of customer service on weekends vs. weekdays so you will use this column as an input.</span></span>|  
|<span data-ttu-id="f7c97-147">移位</span><span class="sxs-lookup"><span data-stu-id="f7c97-147">Shift</span></span>|<span data-ttu-id="f7c97-148">指示为其记录呼叫的轮班时间。</span><span class="sxs-lookup"><span data-stu-id="f7c97-148">Indicates the shift for which calls are recorded.</span></span> <span data-ttu-id="f7c97-149">此呼叫中心将工作日划分为四个轮班时间：AM、PM1、PM2 和 Midnight。</span><span class="sxs-lookup"><span data-stu-id="f7c97-149">This call center divides the working day into four shifts: AM, PM1, PM2, and Midnight.</span></span><br /><br /> <span data-ttu-id="f7c97-150">班次可能影响客户服务质量，因此您将使用此列作为输入。</span><span class="sxs-lookup"><span data-stu-id="f7c97-150">It is possible that the shift influences the quality of customer service so you will use this as an input.</span></span>|  
|<span data-ttu-id="f7c97-151">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="f7c97-151">LevelOneOperators</span></span>|<span data-ttu-id="f7c97-152">指示值班的一级接线员的数量。</span><span class="sxs-lookup"><span data-stu-id="f7c97-152">Indicates the number of Level 1 operators on duty.</span></span><br /><br /> <span data-ttu-id="f7c97-153">呼叫中心的员工最低级别为 l 级，因此这些员工经验不足。</span><span class="sxs-lookup"><span data-stu-id="f7c97-153">Call center employees start at Level 1 so these employees are less experienced.</span></span>|  
|<span data-ttu-id="f7c97-154">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="f7c97-154">LevelTwoOperators</span></span>|<span data-ttu-id="f7c97-155">指示值班的二级接线员的数量。</span><span class="sxs-lookup"><span data-stu-id="f7c97-155">Indicates the number of Level 2 operators on duty.</span></span><br /><br /> <span data-ttu-id="f7c97-156">员工必须记录一定数量的服务小时才能限定为级别2操作员。</span><span class="sxs-lookup"><span data-stu-id="f7c97-156">An employee must log a certain number of service hours to qualify as a Level 2 operator.</span></span>|  
|<span data-ttu-id="f7c97-157">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="f7c97-157">TotalOperators</span></span>|<span data-ttu-id="f7c97-158">此轮班时间内存在的接线员的总数。</span><span class="sxs-lookup"><span data-stu-id="f7c97-158">The total number of operators present during the shift.</span></span>|  
|<span data-ttu-id="f7c97-159">调用</span><span class="sxs-lookup"><span data-stu-id="f7c97-159">Calls</span></span>|<span data-ttu-id="f7c97-160">此轮班时间内收到的呼叫数。</span><span class="sxs-lookup"><span data-stu-id="f7c97-160">Number of calls received during the shift.</span></span>|  
|<span data-ttu-id="f7c97-161">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="f7c97-161">AutomaticResponses</span></span>|<span data-ttu-id="f7c97-162">完全通过自动呼叫处理（交互式语音应答，即 IVR）来处理的呼叫数。</span><span class="sxs-lookup"><span data-stu-id="f7c97-162">The number of calls that were handled entirely by automated call processing (Interactive Voice Response, or IVR).</span></span>|  
|<span data-ttu-id="f7c97-163">Orders</span><span class="sxs-lookup"><span data-stu-id="f7c97-163">Orders</span></span>|<span data-ttu-id="f7c97-164">由呼叫产生的订单数。</span><span class="sxs-lookup"><span data-stu-id="f7c97-164">The number of orders that resulted from calls.</span></span>|  
|<span data-ttu-id="f7c97-165">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="f7c97-165">IssuesRaised</span></span>|<span data-ttu-id="f7c97-166">由呼叫产生的需要后续操作的问题的数量。</span><span class="sxs-lookup"><span data-stu-id="f7c97-166">The number of issues requiring follow-up that were generated by calls.</span></span>|  
|<span data-ttu-id="f7c97-167">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="f7c97-167">AverageTimePerIssue</span></span>|<span data-ttu-id="f7c97-168">应答一次来电所需的平均时间。</span><span class="sxs-lookup"><span data-stu-id="f7c97-168">The average time required to respond to an incoming call.</span></span>|  
|<span data-ttu-id="f7c97-169">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="f7c97-169">ServiceGrade</span></span>|<span data-ttu-id="f7c97-170">指示总体服务质量的指标，以整个班次的*放弃率*为衡量。</span><span class="sxs-lookup"><span data-stu-id="f7c97-170">A metric that indicates the general quality of service, measured as the *abandon rate* for the entire shift.</span></span> <span data-ttu-id="f7c97-171">挂断率越高，说明客户的满意度越差，因此丢失潜在订单的可能性也就越大。</span><span class="sxs-lookup"><span data-stu-id="f7c97-171">The higher the abandon rate, the more likely it is that customers are dissatisfied and that potential orders are being lost.</span></span>|  
  
 <span data-ttu-id="f7c97-172">请注意，数据包括四个基于单个日期列的不同列： `WageType` 、 **DayOfWeek**、 `Shift` 和 `DateKey` 。</span><span class="sxs-lookup"><span data-stu-id="f7c97-172">Note that the data includes four different columns that are based on a single date column: `WageType`, **DayOfWeek**, `Shift`, and `DateKey`.</span></span> <span data-ttu-id="f7c97-173">通常在数据挖掘中不要使用派生自同一数据的多个列，因为值之间的相关性太强，可能遮盖其他模式。</span><span class="sxs-lookup"><span data-stu-id="f7c97-173">Ordinarily in data mining it is not a good idea to use multiple columns that are derived from the same data, as the values correlate with each other too strongly and can obscure other patterns.</span></span>  
  
 <span data-ttu-id="f7c97-174">但是，我们不会 `DateKey` 在模型中使用，因为它包含的唯一值太多。</span><span class="sxs-lookup"><span data-stu-id="f7c97-174">However, we will not use `DateKey` in the model because it contains too many unique values.</span></span> <span data-ttu-id="f7c97-175">与 DayOfWeek 之间没有直接关系 `Shift` ， **DayOfWeek**and `WageType` 和**DayOfWeek**仅部分相关。</span><span class="sxs-lookup"><span data-stu-id="f7c97-175">There is no direct relationship between `Shift` and **DayOfWeek**, and `WageType` and **DayOfWeek** are only partly related.</span></span> <span data-ttu-id="f7c97-176">如果您担心共线性，可以使用所有可用列创建结构，然后在每个模型中忽略不同的列并测试效果。</span><span class="sxs-lookup"><span data-stu-id="f7c97-176">If you were worried about collinearity, you could create the structure using all of the available columns, and then ignore different columns in each model and test the effect.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f7c97-177">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="f7c97-177">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f7c97-178">创建神经网络结构和模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="f7c97-178">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7c97-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7c97-179">See Also</span></span>  
 [<span data-ttu-id="f7c97-180">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="f7c97-180">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
