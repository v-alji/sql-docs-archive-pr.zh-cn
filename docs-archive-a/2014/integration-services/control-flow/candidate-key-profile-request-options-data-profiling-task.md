---
title: 候选键配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 8632dbc4-4394-4dc7-b19c-f9adeb21ba52
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86d7135059a315ad6504beb8e7a9408ef20e4fcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578997"
---
# <a name="candidate-key-profile-request-options-data-profiling-task"></a><span data-ttu-id="b223a-102">候选键配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="b223a-102">Candidate Key Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="b223a-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选定的 **“候选键配置文件请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Candidate Key Profile Request** that is selected in the requests pane.</span></span> <span data-ttu-id="b223a-104">候选键配置文件报告某个列或列集对于选定的表是键还是近似键。</span><span class="sxs-lookup"><span data-stu-id="b223a-104">A Candidate Key profile reports whether a column or set of columns is a key, or an approximate key, for the selected table.</span></span> <span data-ttu-id="b223a-105">此配置文件还有助于标识数据中的问题，如潜在键列中存在重复值。</span><span class="sxs-lookup"><span data-stu-id="b223a-105">This profile can also help you identify problems in your data such as duplicate values in a potential key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b223a-106">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="b223a-106">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="b223a-107">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="b223a-107">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="b223a-108">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="b223a-108">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="b223a-109">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="b223a-109">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-columns-for-the-keycolumns-property"></a><span data-ttu-id="b223a-110">了解如何为 KeyColumns 属性选择列</span><span class="sxs-lookup"><span data-stu-id="b223a-110">Understanding the Selection of Columns for the KeyColumns Property</span></span>  
 <span data-ttu-id="b223a-111">每个 **“候选键配置文件请求”** 都会计算由单个列或多个列组成的单个候选键的键强度：</span><span class="sxs-lookup"><span data-stu-id="b223a-111">Each **Candidate Key Profile Request** computes the key strength of a single key candidate that consists of a single column or of multiple columns:</span></span>  
  
-   <span data-ttu-id="b223a-112">如果仅在 **KeyColumns**中选择了一个列，则该任务将计算那一个列的键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-112">When you select only one column in **KeyColumns**, the task computes the key strength of that one column.</span></span>  
  
-   <span data-ttu-id="b223a-113">如果在 **KeyColumns**中选择了多个列，则该任务将计算由所有选定列组成的组合键的键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-113">When you select multiple columns in **KeyColumns**, the task computes the key strength of the composite key that consists of all the selected columns.</span></span>  
  
-   <span data-ttu-id="b223a-114">如果在 **KeyColumns** 中选择通配符 **(\*)**，则该任务将计算表或视图中的每个列的键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-114">When you select the wildcard character, **(\*)**, in **KeyColumns**, the task computers the key strength of each column in the table or view.</span></span>  
  
 <span data-ttu-id="b223a-115">例如，假定有一个包含列 A、B 和 C 的示例表，则您可以在 **KeyColumns**中进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="b223a-115">For example, consider a sample table that contains columns A, B, and C. You make the following selections for **KeyColumns**:</span></span>  
  
-   <span data-ttu-id="b223a-116">在\*KeyColumns **中选择 (** ) 和 列 C。</span><span class="sxs-lookup"><span data-stu-id="b223a-116">You select (\*) and column C in **KeyColumns**.</span></span> <span data-ttu-id="b223a-117">该任务将计算列 C 的键强度，然后计算组合候选键 (A, C) 和 (B, C) 的键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-117">The task computes the key strength of column C, and then of composite key candidates (A, C) and (B, C).</span></span>  
  
-   <span data-ttu-id="b223a-118">在\*KeyColumns\*中选择 ( **) 和 (** )。</span><span class="sxs-lookup"><span data-stu-id="b223a-118">You select (\*) and (\*) in **KeyColumns**.</span></span> <span data-ttu-id="b223a-119">该任务将计算单个列 A、B 和 C 的键强度，然后计算组合候选键 (A, B)、(A, C) 和 (B, C) 的键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-119">The task computes the key strength of individual columns A, B, and C, and then of composite key candidates (A, B), (A, C) and (B, C).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b223a-120">如果选择 (\*)，则此选项可能会导致大量计算并降低任务性能。</span><span class="sxs-lookup"><span data-stu-id="b223a-120">If you select (\*), this option might result in a large number of computations and decrease the performance of the task.</span></span> <span data-ttu-id="b223a-121">但是，如果任务找到满足键阈值的子集，则它不会再分析其他的组合。</span><span class="sxs-lookup"><span data-stu-id="b223a-121">However, if the task finds a subset that satisfies the threshold for a key, the task does not analyze additional combinations.</span></span> <span data-ttu-id="b223a-122">例如，在上述示例表中，如果任务确定列 C 是一个键，则不会再继续分析组合候选键。</span><span class="sxs-lookup"><span data-stu-id="b223a-122">For example, in the sample table described above, if the task determines that column C is a key, the task does not continue to analyze the composite key candidates.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="b223a-123">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="b223a-123">Request Properties Options</span></span>  
 <span data-ttu-id="b223a-124">对于 **“候选键配置文件请求”** ， **“请求属性”** 窗格将显示以下选项组：</span><span class="sxs-lookup"><span data-stu-id="b223a-124">For a **Candidate Key Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="b223a-125">**Data**，它包含 **TableOrView** 选项和 **KeyColumns** 选项</span><span class="sxs-lookup"><span data-stu-id="b223a-125">**Data**, which includes the **TableOrView** and **KeyColumns** options</span></span>  
  
-   <span data-ttu-id="b223a-126">**常规**</span><span class="sxs-lookup"><span data-stu-id="b223a-126">**General**</span></span>  
  
-   <span data-ttu-id="b223a-127">**选项**</span><span class="sxs-lookup"><span data-stu-id="b223a-127">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="b223a-128">Data 选项</span><span class="sxs-lookup"><span data-stu-id="b223a-128">Data Options</span></span>  
 <span data-ttu-id="b223a-129">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="b223a-129">**ConnectionManager**</span></span>  
 <span data-ttu-id="b223a-130">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含要进行事件探查的表或视图的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="b223a-130">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="b223a-131">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="b223a-131">**TableOrView**</span></span>  
 <span data-ttu-id="b223a-132">选择要进行事件探查的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="b223a-132">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="b223a-133">有关详细信息，请参阅本主题中的“TableorView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="b223a-133">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="b223a-134">**KeyColumns**</span><span class="sxs-lookup"><span data-stu-id="b223a-134">**KeyColumns**</span></span>  
 <span data-ttu-id="b223a-135">选择要进行事件探查的一个或多个现有列。</span><span class="sxs-lookup"><span data-stu-id="b223a-135">Select the existing column or columns to be profiled.</span></span> <span data-ttu-id="b223a-136">选择 **(\*)** 可对所有列进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="b223a-136">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="b223a-137">有关详细信息，请参阅本主题中的“了解如何为 KeyColumns 属性选择列”和“KeyColumns 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="b223a-137">For more information, see the sections, "Understanding the Selection of Columns for the KeyColumns Property" and "KeyColumns Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="b223a-138">TableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="b223a-138">TableOrView Options</span></span>  
 <span data-ttu-id="b223a-139">**架构**</span><span class="sxs-lookup"><span data-stu-id="b223a-139">**Schema**</span></span>  
 <span data-ttu-id="b223a-140">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="b223a-140">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="b223a-141">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="b223a-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="b223a-142">**表**</span><span class="sxs-lookup"><span data-stu-id="b223a-142">**Table**</span></span>  
 <span data-ttu-id="b223a-143">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="b223a-143">Displays the name of the selected table.</span></span> <span data-ttu-id="b223a-144">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="b223a-144">This option is read-only.</span></span>  
  
#### <a name="keycolumns-options"></a><span data-ttu-id="b223a-145">KeyColumns 选项</span><span class="sxs-lookup"><span data-stu-id="b223a-145">KeyColumns Options</span></span>  
 <span data-ttu-id="b223a-146">对于在 **KeyColumns**中选定进行分析的每个列或针对 **(\*)** 选项，将显示以下选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-146">The following options are presented for each column selected for profiling in **KeyColumns**, or for the **(\*)** option.</span></span>  
  
 <span data-ttu-id="b223a-147">有关详细信息，请参阅本主题前面的“了解如何为 KeyColumns 属性选择列”部分。</span><span class="sxs-lookup"><span data-stu-id="b223a-147">For more information, see the section, "Understanding the Selection of Columns for the KeyColumns Property," earlier in this topic.</span></span>  
  
 <span data-ttu-id="b223a-148">**IsWildcard**</span><span class="sxs-lookup"><span data-stu-id="b223a-148">**IsWildcard**</span></span>  
 <span data-ttu-id="b223a-149">指定是否已选择通配符 **(\*)** 。</span><span class="sxs-lookup"><span data-stu-id="b223a-149">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="b223a-150">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="b223a-150">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="b223a-151">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="b223a-151">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="b223a-152">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="b223a-152">This option is read-only.</span></span>  
  
 <span data-ttu-id="b223a-153">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="b223a-153">**ColumnName**</span></span>  
 <span data-ttu-id="b223a-154">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="b223a-154">Displays the name of the selected column.</span></span> <span data-ttu-id="b223a-155">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项空白。</span><span class="sxs-lookup"><span data-stu-id="b223a-155">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="b223a-156">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="b223a-156">This option is read-only.</span></span>  
  
 <span data-ttu-id="b223a-157">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="b223a-157">**StringCompareOptions**</span></span>  
 <span data-ttu-id="b223a-158">选择用于比较字符串值的选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-158">Select options for comparing string values.</span></span> <span data-ttu-id="b223a-159">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-159">This property has the options listed in the following table.</span></span> <span data-ttu-id="b223a-160">此选项的默认值为 **Default**。</span><span class="sxs-lookup"><span data-stu-id="b223a-160">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b223a-161">如果使用通配符 **(\*)** 作为 **ColumnName**，则 **CompareOptions** 将变为只读并设置为 **Default** 设置。</span><span class="sxs-lookup"><span data-stu-id="b223a-161">When you use a **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="b223a-162">值</span><span class="sxs-lookup"><span data-stu-id="b223a-162">Value</span></span>|<span data-ttu-id="b223a-163">说明</span><span class="sxs-lookup"><span data-stu-id="b223a-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b223a-164">**Default**</span><span class="sxs-lookup"><span data-stu-id="b223a-164">**Default**</span></span>|<span data-ttu-id="b223a-165">根据源表中列的排序规则对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="b223a-165">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="b223a-166">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="b223a-166">**BinarySort**</span></span>|<span data-ttu-id="b223a-167">根据为每个字符所定义的位模式对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="b223a-167">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="b223a-168">二进制排序顺序既区分大小写，也区分重音。</span><span class="sxs-lookup"><span data-stu-id="b223a-168">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="b223a-169">二进制排序顺序的速度也最快。</span><span class="sxs-lookup"><span data-stu-id="b223a-169">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="b223a-170">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="b223a-170">**DictionarySort**</span></span>|<span data-ttu-id="b223a-171">根据关联语言或文字字典中定义的排序和比较规则对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="b223a-171">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="b223a-172">如果选择 **DictionarySort**，还可以选择下表中列出的任意选项组合。</span><span class="sxs-lookup"><span data-stu-id="b223a-172">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="b223a-173">默认情况下，不会选择这些附加选项中的任何一个。</span><span class="sxs-lookup"><span data-stu-id="b223a-173">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="b223a-174">值</span><span class="sxs-lookup"><span data-stu-id="b223a-174">Value</span></span>|<span data-ttu-id="b223a-175">说明</span><span class="sxs-lookup"><span data-stu-id="b223a-175">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b223a-176">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="b223a-176">**IgnoreCase**</span></span>|<span data-ttu-id="b223a-177">指定比较是否区分大小写字母。</span><span class="sxs-lookup"><span data-stu-id="b223a-177">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="b223a-178">如果设置了此选项，字符串比较会忽略大小写。</span><span class="sxs-lookup"><span data-stu-id="b223a-178">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="b223a-179">例如，"ABC" 和 "abc" 没有区别。</span><span class="sxs-lookup"><span data-stu-id="b223a-179">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="b223a-180">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="b223a-180">**IgnoreNonSpace**</span></span>|<span data-ttu-id="b223a-181">指定比较是否区分空格字符和标注字符。</span><span class="sxs-lookup"><span data-stu-id="b223a-181">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="b223a-182">如果设置了此选项，则比较会忽略标注字符。</span><span class="sxs-lookup"><span data-stu-id="b223a-182">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="b223a-183">例如，"å" 与 "a" 相同。</span><span class="sxs-lookup"><span data-stu-id="b223a-183">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="b223a-184">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="b223a-184">**IgnoreKanaType**</span></span>|<span data-ttu-id="b223a-185">指定比较是否区分日语的两种假名字符类型：平假名和片假名。</span><span class="sxs-lookup"><span data-stu-id="b223a-185">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="b223a-186">如果设置了此选项，字符串比较会忽略假名类型。</span><span class="sxs-lookup"><span data-stu-id="b223a-186">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="b223a-187">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="b223a-187">**IgnoreWidth**</span></span>|<span data-ttu-id="b223a-188">指定比较是否区分字符的单字节形式和该字符的双字节形式。</span><span class="sxs-lookup"><span data-stu-id="b223a-188">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="b223a-189">如果设置了此选项，字符串比较将把同一字符的单字节形式和双字节形式视为相同。</span><span class="sxs-lookup"><span data-stu-id="b223a-189">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="b223a-190">常规选项</span><span class="sxs-lookup"><span data-stu-id="b223a-190">General Options</span></span>  
 <span data-ttu-id="b223a-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="b223a-191">**RequestID**</span></span>  
 <span data-ttu-id="b223a-192">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="b223a-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="b223a-193">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="b223a-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b223a-194">选项</span><span class="sxs-lookup"><span data-stu-id="b223a-194">Options</span></span>  
 <span data-ttu-id="b223a-195">**ThresholdSetting**</span><span class="sxs-lookup"><span data-stu-id="b223a-195">**ThresholdSetting**</span></span>  
 <span data-ttu-id="b223a-196">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-196">This property has the options listed in the following table.</span></span> <span data-ttu-id="b223a-197">此属性的默认值为 **Specified**。</span><span class="sxs-lookup"><span data-stu-id="b223a-197">The default value of this property is **Specified**.</span></span>  
  
|<span data-ttu-id="b223a-198">值</span><span class="sxs-lookup"><span data-stu-id="b223a-198">Value</span></span>|<span data-ttu-id="b223a-199">说明</span><span class="sxs-lookup"><span data-stu-id="b223a-199">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b223a-200">无 </span><span class="sxs-lookup"><span data-stu-id="b223a-200">**None**</span></span>|<span data-ttu-id="b223a-201">未指定阈值。</span><span class="sxs-lookup"><span data-stu-id="b223a-201">No threshold is specified.</span></span> <span data-ttu-id="b223a-202">不管键强度值如何，都会报告键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-202">The key strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="b223a-203">**Specified**</span><span class="sxs-lookup"><span data-stu-id="b223a-203">**Specified**</span></span>|<span data-ttu-id="b223a-204">在 **KeyStrengthThreshold**中指定了阈值。</span><span class="sxs-lookup"><span data-stu-id="b223a-204">A threshold is specified in **KeyStrengthThreshold**.</span></span> <span data-ttu-id="b223a-205">仅当键强度大于阈值时，才会报告键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-205">The key strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="b223a-206">**Exact**</span><span class="sxs-lookup"><span data-stu-id="b223a-206">**Exact**</span></span>|<span data-ttu-id="b223a-207">未指定阈值。</span><span class="sxs-lookup"><span data-stu-id="b223a-207">No threshold is specified.</span></span> <span data-ttu-id="b223a-208">仅当选定列为完全匹配的键时，才报告键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-208">The key strength is reported only if the selected columns are an exact key.</span></span>|  
  
 <span data-ttu-id="b223a-209">**KeyStrengthThreshold**</span><span class="sxs-lookup"><span data-stu-id="b223a-209">**KeyStrengthThreshold**</span></span>  
 <span data-ttu-id="b223a-210">指定阈值（使用介于 0 和 1 之间的值），仅当键强度大于该阈值时，才会报告键强度。</span><span class="sxs-lookup"><span data-stu-id="b223a-210">Specify the threshold (by using a value between 0 and 1) above which the key strength should be reported.</span></span> <span data-ttu-id="b223a-211">此属性的默认值为 0.95。</span><span class="sxs-lookup"><span data-stu-id="b223a-211">The default value of this property is 0.95.</span></span> <span data-ttu-id="b223a-212">仅当选择了 **Specified** 作为 **KeyStrengthThresholdSetting**时，才会启用该选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-212">This option is enabled only when **Specified** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
 <span data-ttu-id="b223a-213">**MaxNumberOfViolations**</span><span class="sxs-lookup"><span data-stu-id="b223a-213">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="b223a-214">指定要在输出中报告的候选键冲突的最大数量。</span><span class="sxs-lookup"><span data-stu-id="b223a-214">Specify the maximum number of candidate key violations to report in the output.</span></span> <span data-ttu-id="b223a-215">此属性的默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="b223a-215">The default value of this property is 100.</span></span> <span data-ttu-id="b223a-216">只有在选择 **Exact** 作为 **KeyStrengthThresholdSetting**时，才会禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="b223a-216">This option is disabled when **Exact** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b223a-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b223a-217">See Also</span></span>  
 <span data-ttu-id="b223a-218">[数据事件探查任务编辑器（“常规”页）](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="b223a-218">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="b223a-219">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="b223a-219">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
