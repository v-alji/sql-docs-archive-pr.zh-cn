---
title: 列值分布配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: c1e5f5de-04f5-4d00-a9f0-55817186bdf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bba231bf46600d9608e1a55ad3a084534fec75e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585922"
---
# <a name="column-value-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="86690-102">列值分布配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="86690-102">Column Value Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="86690-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选定的 **“列值分布配置文件请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="86690-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Value Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="86690-104">列值分布配置文件将报告选定列中的所有非重复值以及表中每个值表示的行的百分比。</span><span class="sxs-lookup"><span data-stu-id="86690-104">A Column Value Distribution profile reports all the distinct values in the selected column and the percentage of rows in the table that each value represents.</span></span> <span data-ttu-id="86690-105">该配置文件还可以报告其表示内容超过表中指定的行百分比的值。</span><span class="sxs-lookup"><span data-stu-id="86690-105">The profile can also report values that represent more than a specified percentage of rows in the table.</span></span> <span data-ttu-id="86690-106">此配置文件可帮助您识别数据中的问题，例如，列中非重复值的数目不正确。</span><span class="sxs-lookup"><span data-stu-id="86690-106">This profile can help you identify problems in your data such as an incorrect number of distinct values in a column.</span></span> <span data-ttu-id="86690-107">例如，对表示美国州的列进行事件探查，发现有 50 多个非重复值。</span><span class="sxs-lookup"><span data-stu-id="86690-107">For example, you profile a United States state column and discover more than 50 distinct values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86690-108">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="86690-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="86690-109">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="86690-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="86690-110">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="86690-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="86690-111">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="86690-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="86690-112">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="86690-112">Request Properties Options</span></span>  
 <span data-ttu-id="86690-113">对于 **“列值分布配置文件请求”** ， **“请求属性”** 窗格显示下列选项组：</span><span class="sxs-lookup"><span data-stu-id="86690-113">For a **Column Value Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="86690-114">**Data**，它包含 **TableOrView** 选项和 **Column** 选项</span><span class="sxs-lookup"><span data-stu-id="86690-114">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="86690-115">**常规**</span><span class="sxs-lookup"><span data-stu-id="86690-115">**General**</span></span>  
  
-   <span data-ttu-id="86690-116">**选项**</span><span class="sxs-lookup"><span data-stu-id="86690-116">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="86690-117">Data 选项</span><span class="sxs-lookup"><span data-stu-id="86690-117">Data Options</span></span>  
 <span data-ttu-id="86690-118">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="86690-118">**ConnectionManager**</span></span>  
 <span data-ttu-id="86690-119">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含要进行事件探查的表或视图的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="86690-119">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="86690-120">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="86690-120">**TableOrView**</span></span>  
 <span data-ttu-id="86690-121">选择包含要进行事件探查的列的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="86690-121">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="86690-122">有关详细信息，请参阅本主题中的“TableorView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="86690-122">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="86690-123">**列**</span><span class="sxs-lookup"><span data-stu-id="86690-123">**Column**</span></span>  
 <span data-ttu-id="86690-124">选择要进行事件探查的现有列。</span><span class="sxs-lookup"><span data-stu-id="86690-124">Select the existing column to be profiled.</span></span> <span data-ttu-id="86690-125">选择 **(\*)** 可对所有列进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="86690-125">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="86690-126">有关详细信息，请参阅本主题中的“Column 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="86690-126">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="86690-127">TableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="86690-127">TableOrView Options</span></span>  
 <span data-ttu-id="86690-128">**架构**</span><span class="sxs-lookup"><span data-stu-id="86690-128">**Schema**</span></span>  
 <span data-ttu-id="86690-129">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="86690-129">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="86690-130">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="86690-130">This option is read-only.</span></span>  
  
 <span data-ttu-id="86690-131">**表**</span><span class="sxs-lookup"><span data-stu-id="86690-131">**Table**</span></span>  
 <span data-ttu-id="86690-132">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="86690-132">Displays the name of the selected table.</span></span> <span data-ttu-id="86690-133">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="86690-133">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="86690-134">Column 选项</span><span class="sxs-lookup"><span data-stu-id="86690-134">Column Options</span></span>  
 <span data-ttu-id="86690-135">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="86690-135">**IsWildCard**</span></span>  
 <span data-ttu-id="86690-136">指定是否已选择通配符 **(\*)** 。</span><span class="sxs-lookup"><span data-stu-id="86690-136">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="86690-137">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="86690-137">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="86690-138">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="86690-138">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="86690-139">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="86690-139">This option is read-only.</span></span>  
  
 <span data-ttu-id="86690-140">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="86690-140">**ColumnName**</span></span>  
 <span data-ttu-id="86690-141">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="86690-141">Displays the name of the selected column.</span></span> <span data-ttu-id="86690-142">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项空白。</span><span class="sxs-lookup"><span data-stu-id="86690-142">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="86690-143">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="86690-143">This option is read-only.</span></span>  
  
 <span data-ttu-id="86690-144">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="86690-144">**StringCompareOptions**</span></span>  
 <span data-ttu-id="86690-145">选择用于比较字符串值的选项。</span><span class="sxs-lookup"><span data-stu-id="86690-145">Select options for comparing string values.</span></span> <span data-ttu-id="86690-146">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="86690-146">This property has the options listed in the following table.</span></span> <span data-ttu-id="86690-147">此选项的默认值为 **Default**。</span><span class="sxs-lookup"><span data-stu-id="86690-147">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86690-148">如果将 **(\*)** 通配符用于 **ColumnName**，则 **CompareOptions** 为只读并设置为 **Default** 设置。</span><span class="sxs-lookup"><span data-stu-id="86690-148">If the **(\*)** wildcard is used for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="86690-149">值</span><span class="sxs-lookup"><span data-stu-id="86690-149">Value</span></span>|<span data-ttu-id="86690-150">说明</span><span class="sxs-lookup"><span data-stu-id="86690-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86690-151">**Default**</span><span class="sxs-lookup"><span data-stu-id="86690-151">**Default**</span></span>|<span data-ttu-id="86690-152">根据源表中列的排序规则对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="86690-152">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="86690-153">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="86690-153">**BinarySort**</span></span>|<span data-ttu-id="86690-154">根据为每个字符所定义的位模式对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="86690-154">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="86690-155">二进制排序顺序既区分大小写，也区分重音。</span><span class="sxs-lookup"><span data-stu-id="86690-155">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="86690-156">二进制排序顺序的速度也最快。</span><span class="sxs-lookup"><span data-stu-id="86690-156">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="86690-157">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="86690-157">**DictionarySort**</span></span>|<span data-ttu-id="86690-158">根据关联语言或文字字典中定义的排序和比较规则对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="86690-158">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="86690-159">如果选择 **DictionarySort**，还可以选择下表中列出的任意选项组合。</span><span class="sxs-lookup"><span data-stu-id="86690-159">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="86690-160">默认情况下，不会选择这些附加选项中的任何一个。</span><span class="sxs-lookup"><span data-stu-id="86690-160">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="86690-161">值</span><span class="sxs-lookup"><span data-stu-id="86690-161">Value</span></span>|<span data-ttu-id="86690-162">说明</span><span class="sxs-lookup"><span data-stu-id="86690-162">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86690-163">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="86690-163">**IgnoreCase**</span></span>|<span data-ttu-id="86690-164">指定比较是否区分大小写字母。</span><span class="sxs-lookup"><span data-stu-id="86690-164">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="86690-165">如果设置了此选项，字符串比较会忽略大小写。</span><span class="sxs-lookup"><span data-stu-id="86690-165">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="86690-166">例如，"ABC" 和 "abc" 没有区别。</span><span class="sxs-lookup"><span data-stu-id="86690-166">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="86690-167">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="86690-167">**IgnoreNonSpace**</span></span>|<span data-ttu-id="86690-168">指定比较是否区分空格字符和标注字符。</span><span class="sxs-lookup"><span data-stu-id="86690-168">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="86690-169">如果设置了此选项，则比较会忽略标注字符。</span><span class="sxs-lookup"><span data-stu-id="86690-169">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="86690-170">例如，"å" 与 "a" 相同。</span><span class="sxs-lookup"><span data-stu-id="86690-170">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="86690-171">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="86690-171">**IgnoreKanaType**</span></span>|<span data-ttu-id="86690-172">指定比较是否区分日语的两种假名字符类型：平假名和片假名。</span><span class="sxs-lookup"><span data-stu-id="86690-172">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="86690-173">如果设置了此选项，字符串比较会忽略假名类型。</span><span class="sxs-lookup"><span data-stu-id="86690-173">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="86690-174">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="86690-174">**IgnoreWidth**</span></span>|<span data-ttu-id="86690-175">指定比较是否区分字符的单字节形式和该字符的双字节形式。</span><span class="sxs-lookup"><span data-stu-id="86690-175">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="86690-176">如果设置了此选项，字符串比较将把同一字符的单字节形式和双字节形式视为相同。</span><span class="sxs-lookup"><span data-stu-id="86690-176">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="86690-177">常规选项</span><span class="sxs-lookup"><span data-stu-id="86690-177">General Options</span></span>  
 <span data-ttu-id="86690-178">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="86690-178">**RequestID**</span></span>  
 <span data-ttu-id="86690-179">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="86690-179">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="86690-180">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="86690-180">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="86690-181">选项</span><span class="sxs-lookup"><span data-stu-id="86690-181">Options</span></span>  
 <span data-ttu-id="86690-182">**ValueDistributionOption**</span><span class="sxs-lookup"><span data-stu-id="86690-182">**ValueDistributionOption**</span></span>  
 <span data-ttu-id="86690-183">指定是否计算所有列值的分布。</span><span class="sxs-lookup"><span data-stu-id="86690-183">Specify whether to compute the distribution for all column values.</span></span> <span data-ttu-id="86690-184">此选项的默认值为 **FrequentValues**。</span><span class="sxs-lookup"><span data-stu-id="86690-184">The default value of this option is **FrequentValues**.</span></span>  
  
|<span data-ttu-id="86690-185">值</span><span class="sxs-lookup"><span data-stu-id="86690-185">Value</span></span>|<span data-ttu-id="86690-186">说明</span><span class="sxs-lookup"><span data-stu-id="86690-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86690-187">**AllValues**</span><span class="sxs-lookup"><span data-stu-id="86690-187">**AllValues**</span></span>|<span data-ttu-id="86690-188">计算所有列值的分布。</span><span class="sxs-lookup"><span data-stu-id="86690-188">The distribution is computed for all column values.</span></span>|  
|<span data-ttu-id="86690-189">**FrequentValues**</span><span class="sxs-lookup"><span data-stu-id="86690-189">**FrequentValues**</span></span>|<span data-ttu-id="86690-190">仅计算其频率超出 **FrequentValueThreshold**中指定的最小值的值的分布。</span><span class="sxs-lookup"><span data-stu-id="86690-190">The distribution is computed only for values whose frequency exceeds the minimum value specified in **FrequentValueThreshold**.</span></span> <span data-ttu-id="86690-191">输出报告中将不包括未满足 **FrequentValueThreshold** 的值。</span><span class="sxs-lookup"><span data-stu-id="86690-191">Values that do not meet the **FrequentValueThreshold** are excluded from the output report.</span></span>|  
  
 <span data-ttu-id="86690-192">**FrequentValueThreshold**</span><span class="sxs-lookup"><span data-stu-id="86690-192">**FrequentValueThreshold**</span></span>  
 <span data-ttu-id="86690-193">使用 0 到 1 之间的值指定阈值，超过该阈值将报告列值。</span><span class="sxs-lookup"><span data-stu-id="86690-193">Specify the threshold (by using a value between 0 and 1) above which the column value should be reported.</span></span> <span data-ttu-id="86690-194">当选择 **AllValues** 作为 **ValueDistributionOption**时，将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="86690-194">This option is disabled when you select **AllValues** as the **ValueDistributionOption**.</span></span> <span data-ttu-id="86690-195">此选项的默认值为 0.001。</span><span class="sxs-lookup"><span data-stu-id="86690-195">The default value of this option is 0.001.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86690-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86690-196">See Also</span></span>  
 <span data-ttu-id="86690-197">[数据事件探查任务编辑器（“常规”页）](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="86690-197">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="86690-198">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="86690-198">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
