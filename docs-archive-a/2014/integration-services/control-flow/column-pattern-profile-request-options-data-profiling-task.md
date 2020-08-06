---
title: 列模式配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 9ccb8fc5-f65e-41a2-9511-7fa55586eb8b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9293d19baaee95cee77b075447dcfe1061d20bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585923"
---
# <a name="column-pattern-profile-request-options-data-profiling-task"></a><span data-ttu-id="3b18d-102">列模式信息配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="3b18d-102">Column Pattern Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="3b18d-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选定的 **“列模式信息配置文件请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="3b18d-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Pattern Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="3b18d-104">列模式配置文件报告一组涵盖指定字符串列中值的百分比的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="3b18d-104">A Column Pattern profile reports a set of regular expressions that cover the specified percentage of values in a string column.</span></span> <span data-ttu-id="3b18d-105">此配置文件可以帮助您识别数据中的问题（如无效字符串），还可以建议可用于以后验证新值的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="3b18d-105">This profile can help you identify problems in your data, such as invalid strings, and can suggest regular expressions that can be used in the future to validate new values.</span></span> <span data-ttu-id="3b18d-106">例如，美国邮政编码列的模式配置文件可能会生成正则表达式 \d{5}-\d{4}、\d{5} 和 \d{9}。</span><span class="sxs-lookup"><span data-stu-id="3b18d-106">For example, a pattern profile of a column of United States Zip Codes might produce the regular expressions \d{5}-\d{4}, \d{5}, and \d{9}.</span></span> <span data-ttu-id="3b18d-107">如果看到其他的正则表达式，则数据有可能包含无效或格式不正确的值。</span><span class="sxs-lookup"><span data-stu-id="3b18d-107">If you see other regular expressions, your data likely contains values that are invalid or in an incorrect format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b18d-108">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="3b18d-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="3b18d-109">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="3b18d-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="3b18d-110">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="3b18d-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="3b18d-111">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="3b18d-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-use-of-delimiters-and-symbols"></a><span data-ttu-id="3b18d-112">了解分隔符和符号的使用</span><span class="sxs-lookup"><span data-stu-id="3b18d-112">Understanding the Use of Delimiters and Symbols</span></span>  
 <span data-ttu-id="3b18d-113">在计算 **“列模式配置文件请求”** 的模式之前，数据事件探查任务先标记数据。</span><span class="sxs-lookup"><span data-stu-id="3b18d-113">Before computing the patterns for a **Column Pattern Profile Request**, the Data Profiling Task tokenizes the data.</span></span> <span data-ttu-id="3b18d-114">也就是说，该任务将字符串值分隔成称为标记的较小单元。</span><span class="sxs-lookup"><span data-stu-id="3b18d-114">That is, the task separates the string values into smaller units known as tokens.</span></span> <span data-ttu-id="3b18d-115">任务基于为 **“分隔符”** 和 **“符号”** 属性指定的分隔符和符号将字符串分隔成标记：</span><span class="sxs-lookup"><span data-stu-id="3b18d-115">The task separates strings into tokens based on the delimiters and symbols that you specify for the **Delimiters** and **Symbols** properties:</span></span>  
  
-   <span data-ttu-id="3b18d-116">**分隔符** 默认情况下，分隔符列表包含下列字符：空格、水平制表符 (\t)、换行符 (\n) 和回车符 (\r)。</span><span class="sxs-lookup"><span data-stu-id="3b18d-116">**Delimiters** By default, the list of delimiters contains the following characters: space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="3b18d-117">可以指定其他分隔符，但不能删除默认分隔符。</span><span class="sxs-lookup"><span data-stu-id="3b18d-117">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
-   <span data-ttu-id="3b18d-118">**符号**默认情况下，**符号**列表包含以下字符： `,.;:-"'` ~ =&/@！？ ( # A2 # A0 [] {} | # \* ^% `. For example, if the symbols are "` ( # A4-' "，值" (425) 123-4567 "被标记为 [" ( "、" 425 "、" ) "、" 123 "、"-"、" 4567 "、" ) "]。</span><span class="sxs-lookup"><span data-stu-id="3b18d-118">**Symbols** By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%`. For example, if the symbols are "`()-\`", the value "(425) 123-4567" is tokenized as ["(", "425", ")", "123", "-", "4567", ")"].</span></span>  
  
 <span data-ttu-id="3b18d-119">一个字符不能同时作为分隔符和符号。</span><span class="sxs-lookup"><span data-stu-id="3b18d-119">A character cannot be both a delimiter and a symbol.</span></span>  
  
 <span data-ttu-id="3b18d-120">作为标记化过程的一部分，所有分隔符都将规范为一个空格，但字符被保留。</span><span class="sxs-lookup"><span data-stu-id="3b18d-120">All delimiters are normalized to a single space as part of the tokenizing process, while symbols are retained.</span></span>  
  
## <a name="understanding-the-use-of-the-tag-table"></a><span data-ttu-id="3b18d-121">了解标记表的使用</span><span class="sxs-lookup"><span data-stu-id="3b18d-121">Understanding the Use of the Tag Table</span></span>  
 <span data-ttu-id="3b18d-122">根据需要，通过对在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中创建的特殊表中的标记和关联项进行排序，可以使用一个标记 (tag) 对关联标记 (token) 进行分组。</span><span class="sxs-lookup"><span data-stu-id="3b18d-122">You can optionally group related tokens with a single tag by storing tags and the related terms in a special table that you create in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="3b18d-123">标记表必须有两个字符串列，一个命名为“标记”，另一个命名为“术语”。</span><span class="sxs-lookup"><span data-stu-id="3b18d-123">The tag table must have two string columns, one named "Tag" and the other named "Term".</span></span> <span data-ttu-id="3b18d-124">这些列可以为 `char`、`nchar`、`varchar` 或 `nvarchar` 类型，但不可以为 `text` 或 `ntext`。</span><span class="sxs-lookup"><span data-stu-id="3b18d-124">These columns can be of type `char`, `nchar`, `varchar`, or `nvarchar`, but not `text` or `ntext`.</span></span> <span data-ttu-id="3b18d-125">可以将多个标记和相应的术语组合到一个表中。</span><span class="sxs-lookup"><span data-stu-id="3b18d-125">You can combine multiple tags and the corresponding terms in a single table.</span></span> <span data-ttu-id="3b18d-126">一个列模式配置文件请求仅可以使用一个标记表。</span><span class="sxs-lookup"><span data-stu-id="3b18d-126">A Column Pattern Profile Request can use only one tag table.</span></span> <span data-ttu-id="3b18d-127">可以使用单独的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器来连接到标记表。</span><span class="sxs-lookup"><span data-stu-id="3b18d-127">You can use a separate [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to the tag table.</span></span> <span data-ttu-id="3b18d-128">因此，标记表可以与源数据位于不同的数据库或不同的服务器。</span><span class="sxs-lookup"><span data-stu-id="3b18d-128">Therefore, the tag table can be located in a different database or on a different server than the source data.</span></span>  
  
 <span data-ttu-id="3b18d-129">例如，可以使用一个标记“方向”将可能出现在街道地址中的“东部”、“西部”、“北部”和“南部”值分为一组。</span><span class="sxs-lookup"><span data-stu-id="3b18d-129">For example, you could group the values "East", "West", "North", and "South" that might appear in street addresses by using the single tag, "Direction".</span></span> <span data-ttu-id="3b18d-130">下表就是这样一个标记表的示例。</span><span class="sxs-lookup"><span data-stu-id="3b18d-130">The following table is an example of such a tag table.</span></span>  
  
|<span data-ttu-id="3b18d-131">标记</span><span class="sxs-lookup"><span data-stu-id="3b18d-131">Tag</span></span>|<span data-ttu-id="3b18d-132">术语</span><span class="sxs-lookup"><span data-stu-id="3b18d-132">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="3b18d-133">方向</span><span class="sxs-lookup"><span data-stu-id="3b18d-133">Direction</span></span>|<span data-ttu-id="3b18d-134">东部</span><span class="sxs-lookup"><span data-stu-id="3b18d-134">East</span></span>|  
|<span data-ttu-id="3b18d-135">方向</span><span class="sxs-lookup"><span data-stu-id="3b18d-135">Direction</span></span>|<span data-ttu-id="3b18d-136">West</span><span class="sxs-lookup"><span data-stu-id="3b18d-136">West</span></span>|  
|<span data-ttu-id="3b18d-137">方向</span><span class="sxs-lookup"><span data-stu-id="3b18d-137">Direction</span></span>|<span data-ttu-id="3b18d-138">北部</span><span class="sxs-lookup"><span data-stu-id="3b18d-138">North</span></span>|  
|<span data-ttu-id="3b18d-139">方向</span><span class="sxs-lookup"><span data-stu-id="3b18d-139">Direction</span></span>|<span data-ttu-id="3b18d-140">南部</span><span class="sxs-lookup"><span data-stu-id="3b18d-140">South</span></span>|  
  
 <span data-ttu-id="3b18d-141">可以使用另一个标记将表示街道地址中“街道”概念的不同的词分为一组。</span><span class="sxs-lookup"><span data-stu-id="3b18d-141">You could use another tag to group the different words that express the notion of a "street" in street addresses:</span></span>  
  
|<span data-ttu-id="3b18d-142">标记</span><span class="sxs-lookup"><span data-stu-id="3b18d-142">Tag</span></span>|<span data-ttu-id="3b18d-143">术语</span><span class="sxs-lookup"><span data-stu-id="3b18d-143">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="3b18d-144">街道</span><span class="sxs-lookup"><span data-stu-id="3b18d-144">Street</span></span>|<span data-ttu-id="3b18d-145">街道</span><span class="sxs-lookup"><span data-stu-id="3b18d-145">Street</span></span>|  
|<span data-ttu-id="3b18d-146">街道</span><span class="sxs-lookup"><span data-stu-id="3b18d-146">Street</span></span>|<span data-ttu-id="3b18d-147">大街</span><span class="sxs-lookup"><span data-stu-id="3b18d-147">Avenue</span></span>|  
|<span data-ttu-id="3b18d-148">街道</span><span class="sxs-lookup"><span data-stu-id="3b18d-148">Street</span></span>|<span data-ttu-id="3b18d-149">位置</span><span class="sxs-lookup"><span data-stu-id="3b18d-149">Place</span></span>|  
|<span data-ttu-id="3b18d-150">街道</span><span class="sxs-lookup"><span data-stu-id="3b18d-150">Street</span></span>|<span data-ttu-id="3b18d-151">道路</span><span class="sxs-lookup"><span data-stu-id="3b18d-151">Way</span></span>|  
  
 <span data-ttu-id="3b18d-152">基于这种标记组合，街道地址的结果模式可能类似下列模式：</span><span class="sxs-lookup"><span data-stu-id="3b18d-152">Based on this combination of tags, the resulting pattern for a street address might resemble the following pattern:</span></span>  
  
 `\d+\ LookupTag=Direction \d+\p{L}+\ LookupTag=Street`  
  
> [!NOTE]  
>  <span data-ttu-id="3b18d-153">使用标记表会降低数据事件探查任务的性能。</span><span class="sxs-lookup"><span data-stu-id="3b18d-153">Using a tag table decreases the performance of the Data Profiling task.</span></span> <span data-ttu-id="3b18d-154">请勿使用 10 个以上的标记，而且每个标记不应超过 100 个术语。</span><span class="sxs-lookup"><span data-stu-id="3b18d-154">Do not use more than 10 tags or more than 100 terms per tag.</span></span>  
  
 <span data-ttu-id="3b18d-155">同一术语可属于多个标记。</span><span class="sxs-lookup"><span data-stu-id="3b18d-155">The same term can belong to more than one tag.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="3b18d-156">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-156">Request Properties Options</span></span>  
 <span data-ttu-id="3b18d-157">对于 **“列模式配置文件请求”**， **“请求属性”** 窗格显示下列选项组：</span><span class="sxs-lookup"><span data-stu-id="3b18d-157">For a **Column Pattern Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="3b18d-158">**Data**，它包含 **TableOrView** 选项和 **Column** 选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-158">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="3b18d-159">**常规**</span><span class="sxs-lookup"><span data-stu-id="3b18d-159">**General**</span></span>  
  
-   <span data-ttu-id="3b18d-160">**选项**</span><span class="sxs-lookup"><span data-stu-id="3b18d-160">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="3b18d-161">Data 选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-161">Data Options</span></span>  
 <span data-ttu-id="3b18d-162">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="3b18d-162">**ConnectionManager**</span></span>  
 <span data-ttu-id="3b18d-163">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含要进行事件探查的表或视图的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="3b18d-163">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="3b18d-164">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="3b18d-164">**TableOrView**</span></span>  
 <span data-ttu-id="3b18d-165">选择包含要进行事件探查的列的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="3b18d-165">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="3b18d-166">有关详细信息，请参阅本主题中的“TableorView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="3b18d-166">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="3b18d-167">**列**</span><span class="sxs-lookup"><span data-stu-id="3b18d-167">**Column**</span></span>  
 <span data-ttu-id="3b18d-168">选择要进行事件探查的现有列。</span><span class="sxs-lookup"><span data-stu-id="3b18d-168">Select the existing column to be profiled.</span></span> <span data-ttu-id="3b18d-169">选择要分析所有列\*\* (\*) \*\* 。</span><span class="sxs-lookup"><span data-stu-id="3b18d-169">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="3b18d-170">有关详细信息，请参阅本主题中的“Column 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="3b18d-170">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="3b18d-171">TableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-171">TableOrView Options</span></span>  
 <span data-ttu-id="3b18d-172">**架构**</span><span class="sxs-lookup"><span data-stu-id="3b18d-172">**Schema**</span></span>  
 <span data-ttu-id="3b18d-173">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="3b18d-173">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="3b18d-174">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="3b18d-174">This option is read-only.</span></span>  
  
 <span data-ttu-id="3b18d-175">**表**</span><span class="sxs-lookup"><span data-stu-id="3b18d-175">**Table**</span></span>  
 <span data-ttu-id="3b18d-176">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="3b18d-176">Displays the name of the selected table.</span></span> <span data-ttu-id="3b18d-177">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="3b18d-177">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="3b18d-178">Column 选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-178">Column Options</span></span>  
 <span data-ttu-id="3b18d-179">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="3b18d-179">**IsWildCard**</span></span>  
 <span data-ttu-id="3b18d-180">指定是否已选择\*\* (\*) \*\*通配符。</span><span class="sxs-lookup"><span data-stu-id="3b18d-180">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="3b18d-181">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="3b18d-181">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="3b18d-182">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="3b18d-182">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="3b18d-183">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="3b18d-183">This option is read-only.</span></span>  
  
 <span data-ttu-id="3b18d-184">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="3b18d-184">**ColumnName**</span></span>  
 <span data-ttu-id="3b18d-185">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="3b18d-185">Displays the name of the selected column.</span></span> <span data-ttu-id="3b18d-186">如果已选择 " \*\* (\*) \*\*对所有列进行事件探查，则此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="3b18d-186">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="3b18d-187">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="3b18d-187">This option is read-only.</span></span>  
  
 <span data-ttu-id="3b18d-188">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="3b18d-188">**StringCompareOptions**</span></span>  
 <span data-ttu-id="3b18d-189">此选项不适用于列模式配置文件。</span><span class="sxs-lookup"><span data-stu-id="3b18d-189">This option does not apply to the Column Pattern Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="3b18d-190">常规选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-190">General Options</span></span>  
 <span data-ttu-id="3b18d-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="3b18d-191">**RequestID**</span></span>  
 <span data-ttu-id="3b18d-192">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="3b18d-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="3b18d-193">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="3b18d-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="3b18d-194">选项</span><span class="sxs-lookup"><span data-stu-id="3b18d-194">Options</span></span>  
 <span data-ttu-id="3b18d-195">**MaxNumberOfPatterns**</span><span class="sxs-lookup"><span data-stu-id="3b18d-195">**MaxNumberOfPatterns**</span></span>  
 <span data-ttu-id="3b18d-196">指定需要配置文件计算的模式的最大值。</span><span class="sxs-lookup"><span data-stu-id="3b18d-196">Specify the maximum number of patterns that you want the profile to compute.</span></span> <span data-ttu-id="3b18d-197">此选项的默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="3b18d-197">The default value of this option is 10.</span></span> <span data-ttu-id="3b18d-198">最大值为 100。</span><span class="sxs-lookup"><span data-stu-id="3b18d-198">The maximum value is 100.</span></span>  
  
 <span data-ttu-id="3b18d-199">**PercentageDataCoverageDesired**</span><span class="sxs-lookup"><span data-stu-id="3b18d-199">**PercentageDataCoverageDesired**</span></span>  
 <span data-ttu-id="3b18d-200">指定需要计算模式覆盖的数据的百分比。</span><span class="sxs-lookup"><span data-stu-id="3b18d-200">Specify the percentage of the data that you want the computed patterns to cover.</span></span> <span data-ttu-id="3b18d-201">此选项的默认值为 95（百分比）。</span><span class="sxs-lookup"><span data-stu-id="3b18d-201">The default value of this option is 95 (percent).</span></span>  
  
 <span data-ttu-id="3b18d-202">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="3b18d-202">**CaseSensitive**</span></span>  
 <span data-ttu-id="3b18d-203">指示模式是否应区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3b18d-203">Indicate whether the patterns should be case-sensitive.</span></span> <span data-ttu-id="3b18d-204">此选项的默认值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="3b18d-204">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="3b18d-205">**分隔符**</span><span class="sxs-lookup"><span data-stu-id="3b18d-205">**Delimiters**</span></span>  
 <span data-ttu-id="3b18d-206">列出标记化文本时应视为与词之间的空格等效的字符。</span><span class="sxs-lookup"><span data-stu-id="3b18d-206">List the characters that should be treated as the equivalent of spaces between words when tokenizing text.</span></span> <span data-ttu-id="3b18d-207">在默认情况下，“分隔符”\*\*\*\* 列表包含下列字符：空格、水平制表符 (\t)、换行符 (\n) 和回车符 (\r)。</span><span class="sxs-lookup"><span data-stu-id="3b18d-207">By default, the list of **Delimiters** contains the following characters: the space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="3b18d-208">可以指定其他分隔符，但不能删除默认分隔符。</span><span class="sxs-lookup"><span data-stu-id="3b18d-208">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
 <span data-ttu-id="3b18d-209">有关详细信息，请参阅本主题前面的“了解分隔符和符号的使用”。</span><span class="sxs-lookup"><span data-stu-id="3b18d-209">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="3b18d-210">**符号**</span><span class="sxs-lookup"><span data-stu-id="3b18d-210">**Symbols**</span></span>  
 <span data-ttu-id="3b18d-211">列出应保留为模式一部分的符号。</span><span class="sxs-lookup"><span data-stu-id="3b18d-211">List the symbols that should be retained as part of patterns.</span></span> <span data-ttu-id="3b18d-212">可能包含：日期中的“/”、时间中的“:”以及电子邮件地址中的“@”。</span><span class="sxs-lookup"><span data-stu-id="3b18d-212">Examples might include "/" for dates, ":" for times, and "@" for e-mail addresses.</span></span> <span data-ttu-id="3b18d-213">默认情况下，**符号**列表包含以下字符： `,.;:-"'` ~ =&/@！？ ( # A2 # A0 [] {} | # \* ^% '。</span><span class="sxs-lookup"><span data-stu-id="3b18d-213">By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%\`.</span></span>  
  
 <span data-ttu-id="3b18d-214">有关详细信息，请参阅本主题前面的“了解分隔符和符号的使用”。</span><span class="sxs-lookup"><span data-stu-id="3b18d-214">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="3b18d-215">**TagTableConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="3b18d-215">**TagTableConnectionManager**</span></span>  
 <span data-ttu-id="3b18d-216">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含标记表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="3b18d-216">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the tag table.</span></span>  
  
 <span data-ttu-id="3b18d-217">有关详细信息，请参阅本主题前面的“了解分隔符和符号的使用”。</span><span class="sxs-lookup"><span data-stu-id="3b18d-217">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
 <span data-ttu-id="3b18d-218">**TagTableName**</span><span class="sxs-lookup"><span data-stu-id="3b18d-218">**TagTableName**</span></span>  
 <span data-ttu-id="3b18d-219">选择现有的标记表，该表必须有两个分别命名为“标记”和“术语”的字符串列。</span><span class="sxs-lookup"><span data-stu-id="3b18d-219">Select the existing tag table, which must have two string columns named Tag and Term.</span></span>  
  
 <span data-ttu-id="3b18d-220">有关详细信息，请参阅本主题前面的“了解分隔符和符号的使用”。</span><span class="sxs-lookup"><span data-stu-id="3b18d-220">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b18d-221">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b18d-221">See Also</span></span>  
 <span data-ttu-id="3b18d-222">[数据事件探查任务编辑器 &#40;常规 "页面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3b18d-222">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="3b18d-223">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="3b18d-223">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
