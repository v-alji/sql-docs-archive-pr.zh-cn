---
title: 数据配置文件查看器 F1 帮助 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7003e1299938bd53a6d16a5597d4566ba5c46579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578969"
---
# <a name="data-profile-viewer-f1-help"></a><span data-ttu-id="cc2ba-102">数据配置文件查看器 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="cc2ba-102">Data Profile Viewer F1 Help</span></span>
  <span data-ttu-id="cc2ba-103">可以使用数据配置文件查看器查看数据事件探查任务的输出。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-103">Use the Data Profile Viewer to view the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="cc2ba-104">有关如何使用数据配置文件查看器的详细信息，请参阅 [数据配置文件查看器 (Data Profile Viewer)](control-flow/data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-104">For more information about how to use the Data Profile Viewer, see [Data Profile Viewer](control-flow/data-profile-viewer.md).</span></span> <span data-ttu-id="cc2ba-105">有关如何使用数据事件探查任务（该任务可创建在数据配置文件查看器中所分析的配置文件输出）的详细信息，请参阅 [设置数据事件探查任务](control-flow/data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-105">For more information about how to use the Data Profiling task, which creates the profile output that you analyze in the Data Profile Viewer, see [Setup of the Data Profiling Task](control-flow/data-profiling-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="cc2ba-106">静态选项</span><span class="sxs-lookup"><span data-stu-id="cc2ba-106">Static Options</span></span>  
 <span data-ttu-id="cc2ba-107">**打开**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-107">**Open**</span></span>  
 <span data-ttu-id="cc2ba-108">单击可查找包含数据事件探查任务输出的已保存文件。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-108">Click to browse for the saved file that contains the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="cc2ba-109">**“配置文件”** 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-109">**Profiles** pane</span></span>  
 <span data-ttu-id="cc2ba-110">展开“配置文件”窗格中的树可以查看输出中包含的配置文件。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-110">Expand the tree in the **Profiles** pane to see the profiles that are included in the output.</span></span> <span data-ttu-id="cc2ba-111">选择一个配置文件可以查看该配置文件的结果。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-111">Select a profile to view the results for that profile.</span></span>  
  
 <span data-ttu-id="cc2ba-112">“消息”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-112">**Message** pane</span></span>  
 <span data-ttu-id="cc2ba-113">显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-113">Displays status messages.</span></span>  
  
 <span data-ttu-id="cc2ba-114">“明细”  窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-114">**Drilldown** pane</span></span>  
 <span data-ttu-id="cc2ba-115">如果数据事件探查任务使用的数据源可用，则可显示与输出中的值匹配的数据行。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-115">Displays the rows of data that match a value in the output, if the data source that is used by the Data Profiling task is available.</span></span>  
  
 <span data-ttu-id="cc2ba-116">例如，如果在查看针对美国各州的列的列值分布配置文件的输出，则 **“详细值分布”** 窗格可能包含值为 "WA" 的行。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-116">For example, if you are viewing the output of a Column Value Distribution profile for a US State column, the **Detailed Value Distribution** pane might contain a row for "WA".</span></span> <span data-ttu-id="cc2ba-117">双击“详细值分布”窗格中的行可以在明细窗格中查看该州列中值为 "WA" 的数据行。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-117">Double-click the row in the **Detailed Value Distribution** pane to see the rows of data where the value of the state column is "WA" in the drilldown pane.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="cc2ba-118">动态选项</span><span class="sxs-lookup"><span data-stu-id="cc2ba-118">Dynamic Options</span></span>  
  
### <a name="profile-type--column-length-distribution-profile"></a><span data-ttu-id="cc2ba-119">配置文件类型 = 列长度分布配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-119">Profile Type = Column Length Distribution Profile</span></span>  
  
#### <a name="column-length-distribution-profile---column-pane"></a><span data-ttu-id="cc2ba-120">列长度分布配置文件 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-120">Column Length Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="cc2ba-121">**最小长度**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-121">**Minimum Length**</span></span>  
 <span data-ttu-id="cc2ba-122">显示此列中值的最小长度。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-122">Displays the minimum length of values in this column.</span></span>  
  
 <span data-ttu-id="cc2ba-123">**最大长度**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-123">**Maximum Length**</span></span>  
 <span data-ttu-id="cc2ba-124">显示此列中值的最大长度。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-124">Displays the maximum length of values in this column.</span></span>  
  
 <span data-ttu-id="cc2ba-125">**忽略前导空格**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-125">**Ignore Leading Spaces**</span></span>  
 <span data-ttu-id="cc2ba-126">显示计算此配置文件时 `IgnoreLeadingSpaces` 值是设置为 True 还是 False。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-126">Displays whether this profile was computed with an `IgnoreLeadingSpaces` value of True or False.</span></span> <span data-ttu-id="cc2ba-127">此属性已在数据事件探查任务编辑器的 **“配置文件请求”** 页中设置。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-127">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="cc2ba-128">**忽略尾随空格**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-128">**Ignore Trailing Spaces**</span></span>  
 <span data-ttu-id="cc2ba-129">显示计算此配置文件时 `IgnoreTrailingSpaces` 值是设置为 True 还是 False。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-129">Displays whether this profile was computed with an `IgnoreTrailingSpaces` value of True or False.</span></span> <span data-ttu-id="cc2ba-130">此属性已在数据事件探查任务编辑器的 **“配置文件请求”** 页中设置。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-130">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="cc2ba-131">**行计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-131">**Row Count**</span></span>  
 <span data-ttu-id="cc2ba-132">显示表或视图中的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-132">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-length-distribution-pane"></a><span data-ttu-id="cc2ba-133">“详细长度分布”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-133">Detailed Length Distribution pane</span></span>  
 <span data-ttu-id="cc2ba-134">**长度**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-134">**Length**</span></span>  
 <span data-ttu-id="cc2ba-135">显示在进行事件探查的列中找到的列长度。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-135">Displays the column lengths found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-136">**Count**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-136">**Count**</span></span>  
 <span data-ttu-id="cc2ba-137">显示进行事件探查的列的值为“长度”列中显示的长度的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-137">Displays the number of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
 <span data-ttu-id="cc2ba-138">**百分比**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-138">**Percentage**</span></span>  
 <span data-ttu-id="cc2ba-139">显示进行事件探查的列的值为“长度”列中显示的长度的行数百分比。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-139">Displays the percentage of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
### <a name="profile-type--column-null-ratio-profile"></a><span data-ttu-id="cc2ba-140">配置文件类型 = 列 Null 比率配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-140">Profile Type = Column Null Ratio Profile</span></span>  
  
#### <a name="column-null-ratio-profile---column-pane"></a><span data-ttu-id="cc2ba-141">列 Null 比率配置文件 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-141">Column Null Ratio Profile - \<column> pane</span></span>  
 <span data-ttu-id="cc2ba-142">**Null 计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-142">**Null Count**</span></span>  
 <span data-ttu-id="cc2ba-143">显示进行事件探查的列为 Null 值的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-143">Displays the number of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="cc2ba-144">**Null 百分比**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-144">**Null Percentage**</span></span>  
 <span data-ttu-id="cc2ba-145">显示进行事件探查的列为 Null 值的行数百分比。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-145">Displays the percentage of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="cc2ba-146">**行计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-146">**Row Count**</span></span>  
 <span data-ttu-id="cc2ba-147">显示表或视图中的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-147">Displays the number of rows in the table or view.</span></span>  
  
### <a name="profile-type--column-pattern-profile"></a><span data-ttu-id="cc2ba-148">配置文件类型 = 列模式配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-148">Profile Type = Column Pattern Profile</span></span>  
  
#### <a name="column-pattern-profile---column-pane"></a><span data-ttu-id="cc2ba-149">列模式配置文件 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-149">Column Pattern Profile - \<column> pane</span></span>  
 <span data-ttu-id="cc2ba-150">**行计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-150">**Row Count**</span></span>  
 <span data-ttu-id="cc2ba-151">显示表或视图中的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-151">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="pattern-distribution-pane"></a><span data-ttu-id="cc2ba-152">“模式分布”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-152">Pattern Distribution pane</span></span>  
 <span data-ttu-id="cc2ba-153">**模式**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-153">**Pattern**</span></span>  
 <span data-ttu-id="cc2ba-154">显示为进行事件探查的列计算的模式。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-154">Displays the patterns computed for the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-155">**百分比**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-155">**Percentage**</span></span>  
 <span data-ttu-id="cc2ba-156">显示行值与“模式”列中显示的模式匹配的行数百分比。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-156">Displays the percentage of rows whose values match the pattern displayed in the **Pattern** column.</span></span>  
  
### <a name="profile-type--column-statistics-profile"></a><span data-ttu-id="cc2ba-157">配置文件类型 = 列统计信息配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-157">Profile Type = Column Statistics Profile</span></span>  
  
#### <a name="column-statistics-profile---column-pane"></a><span data-ttu-id="cc2ba-158">列统计信息配置文件 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-158">Column Statistics Profile - \<column> pane</span></span>  
 <span data-ttu-id="cc2ba-159">**最低**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-159">**Minimum**</span></span>  
 <span data-ttu-id="cc2ba-160">显示在进行事件探查的列中发现的最小值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-160">Displays the minimum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-161">最大值</span><span class="sxs-lookup"><span data-stu-id="cc2ba-161">**Maximum**</span></span>  
 <span data-ttu-id="cc2ba-162">显示在进行事件探查的列中发现的最大值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-162">Displays the maximum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-163">**中间线**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-163">**Mean**</span></span>  
 <span data-ttu-id="cc2ba-164">显示在进行事件探查的列中发现的值的平均值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-164">Displays the mean of the values found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-165">**标准偏差**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-165">**Standard Deviation**</span></span>  
 <span data-ttu-id="cc2ba-166">显示在进行事件探查的列中发现的值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-166">Displays the standard deviation of the values found in the profiled column.</span></span>  
  
### <a name="profile-type--column-value-distribution-profile"></a><span data-ttu-id="cc2ba-167">配置文件类型 = 列值分布配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-167">Profile Type = Column Value Distribution Profile</span></span>  
  
#### <a name="column-value-distribution-profile---column-pane"></a><span data-ttu-id="cc2ba-168">列值分布配置文件 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-168">Column Value Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="cc2ba-169">**非重复值数目**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-169">**Number of Distinct Values**</span></span>  
 <span data-ttu-id="cc2ba-170">显示在进行事件探查的列中发现的非重复值的计数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-170">Displays the count of distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-171">**行计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-171">**Row Count**</span></span>  
 <span data-ttu-id="cc2ba-172">显示表或视图中的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-172">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-value-distribution-pane"></a><span data-ttu-id="cc2ba-173">“详细值分布”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-173">Detailed Value Distribution pane</span></span>  
 <span data-ttu-id="cc2ba-174">**值**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-174">**Value**</span></span>  
 <span data-ttu-id="cc2ba-175">显示在进行事件探查的列中发现的非重复值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-175">Displays the distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-176">**Count**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-176">**Count**</span></span>  
 <span data-ttu-id="cc2ba-177">显示进行事件探查的列具有“值”列中显示的值的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-177">Displays the number of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
 <span data-ttu-id="cc2ba-178">**百分比**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-178">**Percentage**</span></span>  
 <span data-ttu-id="cc2ba-179">显示进行事件探查的列具有“值”列中显示的值的行数的百分比。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-179">Displays the percentage of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
### <a name="profile-type--candidate-key-profile"></a><span data-ttu-id="cc2ba-180">配置文件类型 = 候选键配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-180">Profile Type = Candidate Key Profile</span></span>  
  
#### <a name="candidate-key-profile---table-pane"></a><span data-ttu-id="cc2ba-181">候选键配置文件 - \<table> 窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-181">Candidate Key Profile - \<table> pane</span></span>  
 <span data-ttu-id="cc2ba-182">**键列**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-182">**Key Columns**</span></span>  
 <span data-ttu-id="cc2ba-183">显示为作为候选键进行事件探查所选择的列。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-183">Displays the columns that were selected for profiling as a candidate key.</span></span>  
  
 <span data-ttu-id="cc2ba-184">**键强度**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-184">**Key Strength**</span></span>  
 <span data-ttu-id="cc2ba-185">显示候选键列或候选键列组合的强度（按百分比）。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-185">Displays the strength (as a percentage) of the candidate key column or combination of columns.</span></span> <span data-ttu-id="cc2ba-186">键强度小于 100% 指示存在重复值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-186">A key strength of less than 100% indicates that duplicate values exist.</span></span>  
  
#### <a name="key-violations-pane"></a><span data-ttu-id="cc2ba-187">“键冲突”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-187">Key Violations pane</span></span>  
 <span data-ttu-id="cc2ba-188">\<column1>、\<column2> 等</span><span class="sxs-lookup"><span data-stu-id="cc2ba-188">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="cc2ba-189">显示进行事件探查的列中找到的重复值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-189">Displays the duplicate values that were found in the profiled column.</span></span>  
  
 <span data-ttu-id="cc2ba-190">**Count**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-190">**Count**</span></span>  
 <span data-ttu-id="cc2ba-191">显示指定的列具有第一列中显示的值的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-191">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
### <a name="profile-type--functional-dependency-profile"></a><span data-ttu-id="cc2ba-192">配置文件类型 = 函数依赖关系配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-192">Profile Type = Functional Dependency Profile</span></span>  
  
#### <a name="functional-dependency-profile-pane"></a><span data-ttu-id="cc2ba-193">“函数依赖关系配置文件”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-193">Functional Dependency Profile pane</span></span>  
 <span data-ttu-id="cc2ba-194">**“决定列”**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-194">**Determinant Columns**</span></span>  
 <span data-ttu-id="cc2ba-195">显示选择作为决定列的单个列或多个列。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-195">Displays the column or columns selected as the determinant column.</span></span> <span data-ttu-id="cc2ba-196">在相同的美国邮政编码应总对应相同的州的示例中，邮政编码列就是决定列。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-196">In the example where the same United States Zip Code should always have the same state, the Zip Code is the determinant column.</span></span>  
  
 <span data-ttu-id="cc2ba-197">**依赖列**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-197">**Dependent Columns**</span></span>  
 <span data-ttu-id="cc2ba-198">显示选择作为依赖列的单个列或多个列。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-198">Displays the column or columns selected as the dependent column.</span></span> <span data-ttu-id="cc2ba-199">在相同的美国邮政编码应总对应相同的州的示例中，州列就是依赖列。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-199">In the example where the same United States Zip Code should always have the same state, the state is the dependent column.</span></span>  
  
 <span data-ttu-id="cc2ba-200">**函数依赖关系强度**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-200">**Functional Dependency Strength**</span></span>  
 <span data-ttu-id="cc2ba-201">显示列之间的函数依赖关系强度（按百分比）。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-201">Displays the strength (as a percentage) of the functional dependency between columns.</span></span> <span data-ttu-id="cc2ba-202">键强度小于 100% 指示存在决定值不能决定依赖值的情况。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-202">A key strength of less than 100% indicates that there are cases where the determinant value does not determine the dependent value.</span></span> <span data-ttu-id="cc2ba-203">在相同的美国邮政编码应总对应相同的州的示例中，这可能表示某些州值无效。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-203">In the example where the same United States Zip Code should always have the same state, this probably indicates some state values are not valid.</span></span>  
  
#### <a name="functional-dependency-violations-pane"></a><span data-ttu-id="cc2ba-204">“函数依赖关系冲突”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-204">Functional Dependency Violations pane</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc2ba-205">数据中的错误值的高百分比可能导致函数依赖关系配置文件产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-205">A high percentage of erroneous values in the data could lead to unexpected results from a Functional Dependency profile.</span></span> <span data-ttu-id="cc2ba-206">例如，在 90% 的行中，与邮政编码值“98052”对应的州值为“WI”。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-206">For example, 90% of the rows have a State value of "WI" for a Postal Code value of "98052."</span></span> <span data-ttu-id="cc2ba-207">配置文件将包含正确州值“WA”的行报告为冲突。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-207">The profile reports rows that contain the correct state value of "WA" as violations.</span></span>  
  
 **\<determinant column name>**  
 <span data-ttu-id="cc2ba-208">显示在此函数依赖关系冲突实例中决定列或决定列组合的值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-208">Displays the value of the determinant column or combination of columns in this instance of a functional dependency violation.</span></span>  
  
 **\<dependent column name>**  
 <span data-ttu-id="cc2ba-209">显示在此函数依赖关系冲突实例中依赖列的值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-209">Displays the value of the dependent column in this instance of a functional dependency violation.</span></span>  
  
 <span data-ttu-id="cc2ba-210">**支持计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-210">**Support Count**</span></span>  
 <span data-ttu-id="cc2ba-211">显示决定列值决定依赖列的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-211">Displays the number of rows in which the determinant column value determines the dependent column.</span></span>  
  
 <span data-ttu-id="cc2ba-212">**冲突计数**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-212">**Violation Count**</span></span>  
 <span data-ttu-id="cc2ba-213">显示决定列值不能决定依赖列的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-213">Displays the number of rows in which the determinant column value does not determine the dependent column.</span></span> <span data-ttu-id="cc2ba-214">（在这些行中，依赖值是 \<dependent column name> 列中显示的值。）</span><span class="sxs-lookup"><span data-stu-id="cc2ba-214">(These are the rows where the dependent value is the value shown in the **\<dependent column name>** column.)</span></span>  
  
 <span data-ttu-id="cc2ba-215">**支持百分比**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-215">**Support Percentage**</span></span>  
 <span data-ttu-id="cc2ba-216">显示决定列决定依赖列的行数的百分比。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-216">Displays the percentage of rows in which the determinant column determines the dependent column.</span></span>  
  
### <a name="profile-type--value-inclusion-profile"></a><span data-ttu-id="cc2ba-217">配置文件类型 = 值包含配置文件</span><span class="sxs-lookup"><span data-stu-id="cc2ba-217">Profile Type = Value Inclusion Profile</span></span>  
  
#### <a name="value-inclusion-profile-pane"></a><span data-ttu-id="cc2ba-218">“值包含配置文件”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-218">Value Inclusion Profile pane</span></span>  
 <span data-ttu-id="cc2ba-219">**“子集端列”**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-219">**Subset Side Columns**</span></span>  
 <span data-ttu-id="cc2ba-220">显示进行事件探查的列或列组合，以确定它们是否包含在超集列中。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-220">Displays the column or combination of columns that were profiled to determine whether they are in the superset columns.</span></span>  
  
 <span data-ttu-id="cc2ba-221">**“超集端列”**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-221">**Superset Side Columns**</span></span>  
 <span data-ttu-id="cc2ba-222">显示进行事件探查的列或列组合，以确定它们是否包含子集列中的值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-222">Displays the column or combination of columns that were profiled to determine whether they include the values in the subset columns.</span></span>  
  
 <span data-ttu-id="cc2ba-223">**包含强度**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-223">**Inclusion Strength**</span></span>  
 <span data-ttu-id="cc2ba-224">显示列之间的重叠强度（按百分比）。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-224">Displays the strength (as a percentage) of the overlap between columns.</span></span> <span data-ttu-id="cc2ba-225">键强度小于 100% 指示存在在超集值中找不到子集值的情况。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-225">A key strength of less than 100% indicates that there are cases where the subset value is not found among the superset values.</span></span>  
  
#### <a name="inclusion-violations-pane"></a><span data-ttu-id="cc2ba-226">“包含冲突”窗格</span><span class="sxs-lookup"><span data-stu-id="cc2ba-226">Inclusion Violations pane</span></span>  
 <span data-ttu-id="cc2ba-227">\<column1>、\<column2> 等</span><span class="sxs-lookup"><span data-stu-id="cc2ba-227">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="cc2ba-228">显示在单个或多个超集列中找不到的单个或多个子集列中的值。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-228">Displays the values in the subset column or columns that were not found in the superset column or columns.</span></span>  
  
 <span data-ttu-id="cc2ba-229">**Count**</span><span class="sxs-lookup"><span data-stu-id="cc2ba-229">**Count**</span></span>  
 <span data-ttu-id="cc2ba-230">显示指定的列具有第一列中显示的值的行数。</span><span class="sxs-lookup"><span data-stu-id="cc2ba-230">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc2ba-231">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc2ba-231">See Also</span></span>  
 <span data-ttu-id="cc2ba-232">[数据配置文件查看器](control-flow/data-profile-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="cc2ba-232">[Data Profile Viewer](control-flow/data-profile-viewer.md) </span></span>  
 [<span data-ttu-id="cc2ba-233">数据事件探查任务和查看器</span><span class="sxs-lookup"><span data-stu-id="cc2ba-233">Data Profiling Task and Viewer</span></span>](control-flow/data-profiling-task-and-viewer.md)  
  
  
