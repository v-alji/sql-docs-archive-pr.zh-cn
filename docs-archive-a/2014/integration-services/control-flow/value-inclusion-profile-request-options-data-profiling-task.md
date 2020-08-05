---
title: 值包含配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: ca94da82-a4c9-4e87-9cba-c2d85bd31f01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cbbd40dd4a2c0b1abca6dd18166f823d5fec8904
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578998"
---
# <a name="value-inclusion-profile-request-options-data-profiling-task"></a><span data-ttu-id="64fa6-102">值包含配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="64fa6-102">Value Inclusion Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="64fa6-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选定的 **“值包含配置文件请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="64fa6-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Value Inclusion Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="64fa6-104">值包含配置文件计算两列或列集之间的值的重叠</span><span class="sxs-lookup"><span data-stu-id="64fa6-104">A Value Inclusion profile computes the overlap in the values between two columns or sets of columns.</span></span> <span data-ttu-id="64fa6-105">因此，它可以确定一个列或列集是否适于用作两个选定表之间的外健。</span><span class="sxs-lookup"><span data-stu-id="64fa6-105">Thus, it can also determine whether a column or set of columns is appropriate to serve as a foreign key between the selected tables.</span></span> <span data-ttu-id="64fa6-106">此配置文件还有助于标识数据中的问题，如值无效。</span><span class="sxs-lookup"><span data-stu-id="64fa6-106">This profile can also help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="64fa6-107">例如，使用值包含配置文件对 Sales 表中的 ProductID 列进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="64fa6-107">For example, you use a value inclusion profile to profile the ProductID column of a Sales table.</span></span> <span data-ttu-id="64fa6-108">在配置文件中发现，该列所包含的某些值不能在 Products 表的 ProductID 列中找到。</span><span class="sxs-lookup"><span data-stu-id="64fa6-108">The profile discovers that the column contains values that are not found in the ProductID column of the Products table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64fa6-109">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="64fa6-109">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="64fa6-110">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="64fa6-110">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="64fa6-111">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="64fa6-111">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="64fa6-112">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="64fa6-112">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-columns-for-the-inclusioncolumns-property"></a><span data-ttu-id="64fa6-113">了解 InclusionColumns 属性列的选择。</span><span class="sxs-lookup"><span data-stu-id="64fa6-113">Understanding the Selection of Columns for the InclusionColumns Property</span></span>  
 <span data-ttu-id="64fa6-114">**“值包含配置文件请求”** 计算子集中的所有值是否在超集中显示。</span><span class="sxs-lookup"><span data-stu-id="64fa6-114">A **Value Inclusion Profile Request** computes whether all the values in a subset are present in the superset.</span></span> <span data-ttu-id="64fa6-115">超集通常是一个查找表或引用表。</span><span class="sxs-lookup"><span data-stu-id="64fa6-115">The superset is often a lookup or reference table.</span></span> <span data-ttu-id="64fa6-116">例如，地址表中的州列是子集表。</span><span class="sxs-lookup"><span data-stu-id="64fa6-116">For example, the state column in a table of addresses is the subset table.</span></span> <span data-ttu-id="64fa6-117">此列中以两个字符表示的每个州代码也应在超集表（美国邮政服务州代码表）中找到。</span><span class="sxs-lookup"><span data-stu-id="64fa6-117">Every two-character state code in this column should also be found in the table of United States Postal Service state codes, which is the superset table.</span></span>  
  
 <span data-ttu-id="64fa6-118">当将通配符 (\*) 用作子集列或超集列的值时，数据事件探查任务将该端的每个列与另一端上指定的列进行比较。</span><span class="sxs-lookup"><span data-stu-id="64fa6-118">When you use the (\*) wildcard as the value of the subset column or the superset column, the Data Profiling task compares each column on that side against the column specified on the other side.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64fa6-119">如果选择 (\*)，则此选项可能会导致大量计算并降低任务性能。</span><span class="sxs-lookup"><span data-stu-id="64fa6-119">If you select (\*), this option might result in a large number of computations and decrease the performance of the task.</span></span>  
  
## <a name="understanding-the-threshold-settings"></a><span data-ttu-id="64fa6-120">了解阈值设置</span><span class="sxs-lookup"><span data-stu-id="64fa6-120">Understanding the Threshold Settings</span></span>  
 <span data-ttu-id="64fa6-121">可以使用两个不同的阈值设置来优化值包含配置文件请求的输出。</span><span class="sxs-lookup"><span data-stu-id="64fa6-121">You can use two different threshold settings to refine the output of a Value Inclusion Profile Request.</span></span>  
  
 <span data-ttu-id="64fa6-122">当为 **InclusionThresholdSetting** 指定非 **None**的值时，该配置文件仅在以下条件之一报告超集中子集的包含强度：</span><span class="sxs-lookup"><span data-stu-id="64fa6-122">When you specify a value other than **None** for **InclusionThresholdSetting**, the profile reports the inclusion strength of the subset in the superset only under one of the following conditions:</span></span>  
  
-   <span data-ttu-id="64fa6-123">当包含强度超出 **InclusionStrengthThreshold**中指定的阈值时。</span><span class="sxs-lookup"><span data-stu-id="64fa6-123">When the inclusion strength exceeds the threshold specified in **InclusionStrengthThreshold**.</span></span>  
  
-   <span data-ttu-id="64fa6-124">当包含强度的值为 1.0，而 **InclusionStrengthThreshold** 设置为 **Exact**时。</span><span class="sxs-lookup"><span data-stu-id="64fa6-124">When the inclusion strength has a value of 1.0 and the **InclusionStrengthThreshold** is set to **Exact**.</span></span>  
  
 <span data-ttu-id="64fa6-125">由于为非唯一值，因此可以筛选出超集列不是超集表的适当的键的组合，从而更好地优化输出。</span><span class="sxs-lookup"><span data-stu-id="64fa6-125">You can refine the output more by filtering out combinations where the superset column is not an appropriate key for the superset table because of non-unique values.</span></span> <span data-ttu-id="64fa6-126">当为 **SupersetColumnsKeyThresholdSetting** 指定非 **None**的值时，配置文件仅在以下条件之一报告超集中子集的包含强度：</span><span class="sxs-lookup"><span data-stu-id="64fa6-126">When you specify a value other than **None** for **SupersetColumnsKeyThresholdSetting**, the profile reports the inclusion strength of the subset in the superset only under one of the following conditions:</span></span>  
  
-   <span data-ttu-id="64fa6-127">当超集列作为超集表中的键的适用性超出了 **SupersetColumnsKeyThreshold**中指定的阈值时。</span><span class="sxs-lookup"><span data-stu-id="64fa6-127">When the suitability of the superset columns as a key in the superset table exceeds the threshold specified in **SupersetColumnsKeyThreshold**</span></span>  
  
-   <span data-ttu-id="64fa6-128">当包含强度的值为 1.0，而 **SupersetColumnsKeyThreshold** 设置为 **Exact**时。</span><span class="sxs-lookup"><span data-stu-id="64fa6-128">When the inclusion strength has a value or 1.0 and the **SupersetColumnsKeyThreshold** is set to **Exact**.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="64fa6-129">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-129">Request Properties Options</span></span>  
 <span data-ttu-id="64fa6-130">对于 **“值包含配置文件请求”** ， **“请求属性”** 窗格显示下面的选项组：</span><span class="sxs-lookup"><span data-stu-id="64fa6-130">For a **Value Inclusion Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="64fa6-131">**Data**，它包含 **SubsetTableOrView**、 **SupersetTableOrView**和 **InclusionColumns** 选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-131">**Data**, which includes the **SubsetTableOrView**, **SupersetTableOrView**, and **InclusionColumns** options</span></span>  
  
-   <span data-ttu-id="64fa6-132">**常规**</span><span class="sxs-lookup"><span data-stu-id="64fa6-132">**General**</span></span>  
  
-   <span data-ttu-id="64fa6-133">**选项**</span><span class="sxs-lookup"><span data-stu-id="64fa6-133">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="64fa6-134">Data 选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-134">Data Options</span></span>  
 <span data-ttu-id="64fa6-135">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="64fa6-135">**ConnectionManager**</span></span>  
 <span data-ttu-id="64fa6-136">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含要进行事件探查的表或视图的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="64fa6-136">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="64fa6-137">**SubsetTableOrView**</span><span class="sxs-lookup"><span data-stu-id="64fa6-137">**SubsetTableOrView**</span></span>  
 <span data-ttu-id="64fa6-138">选择要进行事件探查的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="64fa6-138">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="64fa6-139">有关详细信息，请参阅本主题中的“SubsetTableOrView 和 SupersetTableOrView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-139">For more information, see the section, "SubsetTableOrView and SupersetTableOrView Options," in this topic.</span></span>  
  
 <span data-ttu-id="64fa6-140">**SupersetTableOrView**</span><span class="sxs-lookup"><span data-stu-id="64fa6-140">**SupersetTableOrView**</span></span>  
 <span data-ttu-id="64fa6-141">选择要进行事件探查的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="64fa6-141">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="64fa6-142">有关详细信息，请参阅本主题中的“SubsetTableOrView 和 SupersetTableOrView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-142">For more information, see the section, "SubsetTableOrView and SupersetTableOrView Options," in this topic.</span></span>  
  
 <span data-ttu-id="64fa6-143">**InclusionColumns**</span><span class="sxs-lookup"><span data-stu-id="64fa6-143">**InclusionColumns**</span></span>  
 <span data-ttu-id="64fa6-144">从子集和超集表选择列或列集。</span><span class="sxs-lookup"><span data-stu-id="64fa6-144">Select the columns or sets of columns from the subset and superset tables.</span></span>  
  
 <span data-ttu-id="64fa6-145">有关详细信息，请参阅本主题中的“了解 InclusionColumns 属性列的选择”和“InclusionColumns 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-145">For more information, see the sections, "Understanding the Selection of Columns for the InclusionColumns Property" and "InclusionColumns Options," in this topic.</span></span>  
  
#### <a name="subsettableorview-and-supersettableorview-options"></a><span data-ttu-id="64fa6-146">SubsetTableOrView 和 SupersetTableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-146">SubsetTableOrView and SupersetTableOrView Options</span></span>  
 <span data-ttu-id="64fa6-147">**架构**</span><span class="sxs-lookup"><span data-stu-id="64fa6-147">**Schema**</span></span>  
 <span data-ttu-id="64fa6-148">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="64fa6-148">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="64fa6-149">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="64fa6-149">This option is read-only.</span></span>  
  
 <span data-ttu-id="64fa6-150">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="64fa6-150">**TableOrView**</span></span>  
 <span data-ttu-id="64fa6-151">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="64fa6-151">Displays the name of the selected table.</span></span> <span data-ttu-id="64fa6-152">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="64fa6-152">This option is read-only.</span></span>  
  
#### <a name="inclusioncolumns-options"></a><span data-ttu-id="64fa6-153">InclusionColumns 选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-153">InclusionColumns Options</span></span>  
 <span data-ttu-id="64fa6-154">将针对在 **InclusionColumns**中进行探查的每个选定列集显示以下选项：</span><span class="sxs-lookup"><span data-stu-id="64fa6-154">The following options are presented for each set of columns selected for profiling in **InclusionColumns**.</span></span>  
  
 <span data-ttu-id="64fa6-155">有关详细信息，请参阅本主题前面的“了解 InclusionColumns 属性列的选择”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-155">For more information, see the section, "Understanding the Selection of Columns for the InclusionColumns Property," earlier in this topic.</span></span>  
  
 <span data-ttu-id="64fa6-156">**IsWildcard**</span><span class="sxs-lookup"><span data-stu-id="64fa6-156">**IsWildcard**</span></span>  
 <span data-ttu-id="64fa6-157">指定是否已选择通配符 **(\*)** 。</span><span class="sxs-lookup"><span data-stu-id="64fa6-157">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="64fa6-158">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="64fa6-158">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="64fa6-159">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="64fa6-159">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="64fa6-160">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="64fa6-160">This option is read-only.</span></span>  
  
 <span data-ttu-id="64fa6-161">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="64fa6-161">**ColumnName**</span></span>  
 <span data-ttu-id="64fa6-162">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="64fa6-162">Displays the name of the selected column.</span></span> <span data-ttu-id="64fa6-163">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项空白。</span><span class="sxs-lookup"><span data-stu-id="64fa6-163">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="64fa6-164">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="64fa6-164">This option is read-only.</span></span>  
  
 <span data-ttu-id="64fa6-165">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="64fa6-165">**StringCompareOptions**</span></span>  
 <span data-ttu-id="64fa6-166">选择用于比较字符串值的选项。</span><span class="sxs-lookup"><span data-stu-id="64fa6-166">Select options for comparing string values.</span></span> <span data-ttu-id="64fa6-167">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="64fa6-167">This property has the options listed in the following table.</span></span> <span data-ttu-id="64fa6-168">此选项的默认值为 **Default**。</span><span class="sxs-lookup"><span data-stu-id="64fa6-168">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64fa6-169">如果使用通配符 **(\*)** 作为 **ColumnName**，则 **CompareOptions** 将变为只读并设置为 **Default** 设置。</span><span class="sxs-lookup"><span data-stu-id="64fa6-169">When you use the **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="64fa6-170">值</span><span class="sxs-lookup"><span data-stu-id="64fa6-170">Value</span></span>|<span data-ttu-id="64fa6-171">说明</span><span class="sxs-lookup"><span data-stu-id="64fa6-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64fa6-172">**Default**</span><span class="sxs-lookup"><span data-stu-id="64fa6-172">**Default**</span></span>|<span data-ttu-id="64fa6-173">根据源表中列的排序规则对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="64fa6-173">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="64fa6-174">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="64fa6-174">**BinarySort**</span></span>|<span data-ttu-id="64fa6-175">根据为每个字符所定义的位模式对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="64fa6-175">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="64fa6-176">二进制排序顺序既区分大小写，也区分重音。</span><span class="sxs-lookup"><span data-stu-id="64fa6-176">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="64fa6-177">二进制排序顺序的速度也最快。</span><span class="sxs-lookup"><span data-stu-id="64fa6-177">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="64fa6-178">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="64fa6-178">**DictionarySort**</span></span>|<span data-ttu-id="64fa6-179">根据关联语言或文字字典中定义的排序和比较规则对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="64fa6-179">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="64fa6-180">如果选择 **DictionarySort**，还可以选择下表中列出的任意选项组合。</span><span class="sxs-lookup"><span data-stu-id="64fa6-180">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="64fa6-181">默认情况下，不会选择这些附加选项中的任何一个。</span><span class="sxs-lookup"><span data-stu-id="64fa6-181">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="64fa6-182">值</span><span class="sxs-lookup"><span data-stu-id="64fa6-182">Value</span></span>|<span data-ttu-id="64fa6-183">说明</span><span class="sxs-lookup"><span data-stu-id="64fa6-183">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64fa6-184">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="64fa6-184">**IgnoreCase**</span></span>|<span data-ttu-id="64fa6-185">指定比较是否区分大小写字母。</span><span class="sxs-lookup"><span data-stu-id="64fa6-185">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="64fa6-186">如果设置了此选项，字符串比较会忽略大小写。</span><span class="sxs-lookup"><span data-stu-id="64fa6-186">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="64fa6-187">例如，"ABC" 和 "abc" 没有区别。</span><span class="sxs-lookup"><span data-stu-id="64fa6-187">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="64fa6-188">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="64fa6-188">**IgnoreNonSpace**</span></span>|<span data-ttu-id="64fa6-189">指定比较是否区分空格字符和标注字符。</span><span class="sxs-lookup"><span data-stu-id="64fa6-189">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="64fa6-190">如果设置了此选项，则比较会忽略标注字符。</span><span class="sxs-lookup"><span data-stu-id="64fa6-190">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="64fa6-191">例如，"å" 与 "a" 相同。</span><span class="sxs-lookup"><span data-stu-id="64fa6-191">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="64fa6-192">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="64fa6-192">**IgnoreKanaType**</span></span>|<span data-ttu-id="64fa6-193">指定比较是否区分日语的两种假名字符类型：平假名和片假名。</span><span class="sxs-lookup"><span data-stu-id="64fa6-193">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="64fa6-194">如果设置了此选项，字符串比较会忽略假名类型。</span><span class="sxs-lookup"><span data-stu-id="64fa6-194">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="64fa6-195">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="64fa6-195">**IgnoreWidth**</span></span>|<span data-ttu-id="64fa6-196">指定比较是否区分字符的单字节形式和该字符的双字节形式。</span><span class="sxs-lookup"><span data-stu-id="64fa6-196">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="64fa6-197">如果设置了此选项，字符串比较将把同一字符的单字节形式和双字节形式视为相同。</span><span class="sxs-lookup"><span data-stu-id="64fa6-197">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="64fa6-198">常规选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-198">General Options</span></span>  
 <span data-ttu-id="64fa6-199">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="64fa6-199">**RequestID**</span></span>  
 <span data-ttu-id="64fa6-200">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="64fa6-200">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="64fa6-201">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-201">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="64fa6-202">选项</span><span class="sxs-lookup"><span data-stu-id="64fa6-202">Options</span></span>  
 <span data-ttu-id="64fa6-203">**None**</span><span class="sxs-lookup"><span data-stu-id="64fa6-203">**InclusionThresholdSetting**</span></span>  
 <span data-ttu-id="64fa6-204">选择阈值设置来优化配置文件的输出。</span><span class="sxs-lookup"><span data-stu-id="64fa6-204">Select the threshold setting to refine the output of the profile.</span></span> <span data-ttu-id="64fa6-205">此属性的默认值为 **Specified**。</span><span class="sxs-lookup"><span data-stu-id="64fa6-205">The default value of this property is **Specified**.</span></span> <span data-ttu-id="64fa6-206">有关详细信息，请参阅本主题前面的“了解阈值设置”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-206">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
|<span data-ttu-id="64fa6-207">值</span><span class="sxs-lookup"><span data-stu-id="64fa6-207">Value</span></span>|<span data-ttu-id="64fa6-208">说明</span><span class="sxs-lookup"><span data-stu-id="64fa6-208">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64fa6-209">无 </span><span class="sxs-lookup"><span data-stu-id="64fa6-209">**None**</span></span>|<span data-ttu-id="64fa6-210">不指定阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-210">Does not specify a threshold.</span></span> <span data-ttu-id="64fa6-211">不管键强度值如何，都会报告键强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-211">The key strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="64fa6-212">**Specified**</span><span class="sxs-lookup"><span data-stu-id="64fa6-212">**Specified**</span></span>|<span data-ttu-id="64fa6-213">使用 **InclusionStrengthThreshold**中指定的阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-213">Use the threshold that is specified in **InclusionStrengthThreshold**.</span></span> <span data-ttu-id="64fa6-214">只有在包含强度大于阈值时才报告该包含强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-214">The inclusion strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="64fa6-215">**Exact**</span><span class="sxs-lookup"><span data-stu-id="64fa6-215">**Exact**</span></span>|<span data-ttu-id="64fa6-216">不指定阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-216">Does not specify a threshold.</span></span> <span data-ttu-id="64fa6-217">只有在子集值完全包含在超集值中时才报告包含强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-217">The inclusion strength is reported only if the subset values are completedly included in the upserset values.</span></span>|  
  
 <span data-ttu-id="64fa6-218">**InclusionStrengthThreshold**</span><span class="sxs-lookup"><span data-stu-id="64fa6-218">**InclusionStrengthThreshold**</span></span>  
 <span data-ttu-id="64fa6-219">使用 0 到 1 之间的值指定阈值，高于此阈值将报告包含强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-219">Specify the threshold (by using a value between 0 and 1) above which the inclusion strength should be reported.</span></span> <span data-ttu-id="64fa6-220">此属性的默认值为 0.95。</span><span class="sxs-lookup"><span data-stu-id="64fa6-220">The default value of this property is 0.95.</span></span> <span data-ttu-id="64fa6-221">只有在选择 **Specified** 作为 **InclusionThresholdSetting**的值时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="64fa6-221">This option is enabled only when **Specified** is selected as the **InclusionThresholdSetting**.</span></span>  
  
 <span data-ttu-id="64fa6-222">有关详细信息，请参阅本主题前面的“了解阈值设置”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-222">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
 <span data-ttu-id="64fa6-223">**None**</span><span class="sxs-lookup"><span data-stu-id="64fa6-223">**SupersetColumnsKeyThresholdSetting**</span></span>  
 <span data-ttu-id="64fa6-224">指定超集阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-224">Specify the superset threshold.</span></span> <span data-ttu-id="64fa6-225">此属性的默认值为 **Specified**。</span><span class="sxs-lookup"><span data-stu-id="64fa6-225">The default value of this property is **Specified**.</span></span> <span data-ttu-id="64fa6-226">有关详细信息，请参阅本主题前面的“了解阈值设置”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-226">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
|<span data-ttu-id="64fa6-227">值</span><span class="sxs-lookup"><span data-stu-id="64fa6-227">Value</span></span>|<span data-ttu-id="64fa6-228">说明</span><span class="sxs-lookup"><span data-stu-id="64fa6-228">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64fa6-229">无 </span><span class="sxs-lookup"><span data-stu-id="64fa6-229">**None**</span></span>|<span data-ttu-id="64fa6-230">不指定阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-230">Does not specify a threshold.</span></span> <span data-ttu-id="64fa6-231">报告包含强度时不考虑超集列的键强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-231">The inclusion strength is reported regardless of the key strength of the superset column.</span></span>|  
|<span data-ttu-id="64fa6-232">**Specified**</span><span class="sxs-lookup"><span data-stu-id="64fa6-232">**Specified**</span></span>|<span data-ttu-id="64fa6-233">使用 **SupersetColumnsKeyThreshold**中指定的阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-233">Use the threshold that is specified in **SupersetColumnsKeyThreshold**.</span></span> <span data-ttu-id="64fa6-234">只有在超集列的键强度大于阈值时才报告包含强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-234">The inclusion strength is reported only if the key strength of the superset column is greater than the threshold.</span></span>|  
|<span data-ttu-id="64fa6-235">**Exact**</span><span class="sxs-lookup"><span data-stu-id="64fa6-235">**Exact**</span></span>|<span data-ttu-id="64fa6-236">不指定阈值。</span><span class="sxs-lookup"><span data-stu-id="64fa6-236">Does not specify a threshold.</span></span> <span data-ttu-id="64fa6-237">只有在超集列为超集表中的确切键时才报告包含强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-237">The inclusion strength is reported only if the supserset columns are an exact key in the superset table.</span></span>|  
  
 <span data-ttu-id="64fa6-238">**SupersetColumnsKeyThreshold**</span><span class="sxs-lookup"><span data-stu-id="64fa6-238">**SupersetColumnsKeyThreshold**</span></span>  
 <span data-ttu-id="64fa6-239">使用 0 到 1 之间的值指定阈值，高于此阈值将报告包含强度。</span><span class="sxs-lookup"><span data-stu-id="64fa6-239">Specify the threshold (by using a value between 0 and 1) above which the inclusion strength should be reported.</span></span> <span data-ttu-id="64fa6-240">此属性的默认值为 0.95。</span><span class="sxs-lookup"><span data-stu-id="64fa6-240">The default value of this property is 0.95.</span></span> <span data-ttu-id="64fa6-241">只有在选择 **Specified** 作为 **SupersetColumnsKeyThresholdSetting**的值时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="64fa6-241">This option is enabled only when **Specified** is selected as the **SupersetColumnsKeyThresholdSetting**.</span></span>  
  
 <span data-ttu-id="64fa6-242">有关详细信息，请参阅本主题前面的“了解阈值设置”部分。</span><span class="sxs-lookup"><span data-stu-id="64fa6-242">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
 <span data-ttu-id="64fa6-243">**MaxNumberOfViolations**</span><span class="sxs-lookup"><span data-stu-id="64fa6-243">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="64fa6-244">指定要在输出中报告的最大包含冲突数。</span><span class="sxs-lookup"><span data-stu-id="64fa6-244">Specify the maximum number of inclusion violations to report in the output.</span></span> <span data-ttu-id="64fa6-245">此属性的默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="64fa6-245">The default value of this property is 100.</span></span> <span data-ttu-id="64fa6-246">只有在选择 **Exact** 作为 **InclusionThresholdSetting**时，才会禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="64fa6-246">This option is disabled when **Exact** is selected as the **InclusionThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fa6-247">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64fa6-247">See Also</span></span>  
 <span data-ttu-id="64fa6-248">[数据事件探查任务编辑器（“常规”页）](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="64fa6-248">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="64fa6-249">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="64fa6-249">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
