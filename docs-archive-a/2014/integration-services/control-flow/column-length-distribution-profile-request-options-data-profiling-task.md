---
title: 列长度分布配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c0ebb6f1e0a6df2c0e47311f7b8217c5ce6f2df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585935"
---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="732c2-102">列长度分布配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="732c2-102">Column Length Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="732c2-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选择的 **“列长度分布配置文件请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="732c2-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Length Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="732c2-104">列长度分布配置文件报告所选列中字符串值的所有不同长度，以及每个长度表示的行在表中的百分比。</span><span class="sxs-lookup"><span data-stu-id="732c2-104">A Column Length Distribution profile reports all the distinct lengths of string values in the selected column and the percentage of rows in the table that each length represents.</span></span> <span data-ttu-id="732c2-105">此配置文件有助于标识数据中的问题，如值无效。</span><span class="sxs-lookup"><span data-stu-id="732c2-105">This profile can help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="732c2-106">例如，在对以两个字符表示的美国州代码列进行事件探查，发现存在超过两个字符的值。</span><span class="sxs-lookup"><span data-stu-id="732c2-106">For example, you profile a column of two-character United States state codes and discover values longer than two characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="732c2-107">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="732c2-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="732c2-108">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="732c2-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="732c2-109">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="732c2-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="732c2-110">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="732c2-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="732c2-111">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="732c2-111">Request Properties Options</span></span>  
 <span data-ttu-id="732c2-112">对于 **“列长度分布配置文件请求”** ， **“请求属性”** 窗格显示下面的选项组：</span><span class="sxs-lookup"><span data-stu-id="732c2-112">For a **Column Length Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="732c2-113">**Data**，它包含 **TableOrView** 选项和 **Column** 选项</span><span class="sxs-lookup"><span data-stu-id="732c2-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="732c2-114">**常规**</span><span class="sxs-lookup"><span data-stu-id="732c2-114">**General**</span></span>  
  
-   <span data-ttu-id="732c2-115">**选项**</span><span class="sxs-lookup"><span data-stu-id="732c2-115">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="732c2-116">Data 选项</span><span class="sxs-lookup"><span data-stu-id="732c2-116">Data Options</span></span>  
 <span data-ttu-id="732c2-117">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="732c2-117">**ConnectionManager**</span></span>  
 <span data-ttu-id="732c2-118">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含要进行事件探查的表或视图的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="732c2-118">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="732c2-119">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="732c2-119">**TableOrView**</span></span>  
 <span data-ttu-id="732c2-120">选择包含要进行事件探查的列的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="732c2-120">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="732c2-121">有关详细信息，请参阅本主题中的“TableorView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="732c2-121">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="732c2-122">**列**</span><span class="sxs-lookup"><span data-stu-id="732c2-122">**Column**</span></span>  
 <span data-ttu-id="732c2-123">选择要进行事件探查的现有列。</span><span class="sxs-lookup"><span data-stu-id="732c2-123">Select the existing column to be profiled.</span></span> <span data-ttu-id="732c2-124">选择 **(\*)** 可对所有列进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="732c2-124">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="732c2-125">有关详细信息，请参阅本主题中的“Column 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="732c2-125">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="732c2-126">TableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="732c2-126">TableOrView Options</span></span>  
 <span data-ttu-id="732c2-127">**架构**</span><span class="sxs-lookup"><span data-stu-id="732c2-127">**Schema**</span></span>  
 <span data-ttu-id="732c2-128">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="732c2-128">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="732c2-129">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="732c2-129">This option is read-only.</span></span>  
  
 <span data-ttu-id="732c2-130">**表**</span><span class="sxs-lookup"><span data-stu-id="732c2-130">**Table**</span></span>  
 <span data-ttu-id="732c2-131">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="732c2-131">Displays the name of the selected table.</span></span> <span data-ttu-id="732c2-132">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="732c2-132">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="732c2-133">Column 选项</span><span class="sxs-lookup"><span data-stu-id="732c2-133">Column Options</span></span>  
 <span data-ttu-id="732c2-134">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="732c2-134">**IsWildCard**</span></span>  
 <span data-ttu-id="732c2-135">指定是否已选择通配符 **(\*)** 。</span><span class="sxs-lookup"><span data-stu-id="732c2-135">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="732c2-136">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="732c2-136">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="732c2-137">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="732c2-137">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="732c2-138">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="732c2-138">This option is read-only.</span></span>  
  
 <span data-ttu-id="732c2-139">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="732c2-139">**ColumnName**</span></span>  
 <span data-ttu-id="732c2-140">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="732c2-140">Displays the name of the selected column.</span></span> <span data-ttu-id="732c2-141">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项空白。</span><span class="sxs-lookup"><span data-stu-id="732c2-141">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="732c2-142">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="732c2-142">This option is read-only.</span></span>  
  
 <span data-ttu-id="732c2-143">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="732c2-143">**StringCompareOptions**</span></span>  
 <span data-ttu-id="732c2-144">此选项不适用于列长度分布配置文件。</span><span class="sxs-lookup"><span data-stu-id="732c2-144">This option does not apply to the Column Length Distribution Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="732c2-145">常规选项</span><span class="sxs-lookup"><span data-stu-id="732c2-145">General Options</span></span>  
 <span data-ttu-id="732c2-146">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="732c2-146">**RequestID**</span></span>  
 <span data-ttu-id="732c2-147">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="732c2-147">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="732c2-148">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="732c2-148">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="732c2-149">选项</span><span class="sxs-lookup"><span data-stu-id="732c2-149">Options</span></span>  
 <span data-ttu-id="732c2-150">**IgnoreLeadingSpaces**</span><span class="sxs-lookup"><span data-stu-id="732c2-150">**IgnoreLeadingSpaces**</span></span>  
 <span data-ttu-id="732c2-151">指示配置文件比较字符串值时是否忽略前导空格。</span><span class="sxs-lookup"><span data-stu-id="732c2-151">Indicate whether to ignore leading spaces when the profile compares string values.</span></span> <span data-ttu-id="732c2-152">此选项的默认值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="732c2-152">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="732c2-153">**IgnoreTrailingSpaces**</span><span class="sxs-lookup"><span data-stu-id="732c2-153">**IgnoreTrailingSpaces**</span></span>  
 <span data-ttu-id="732c2-154">指示配置文件比较字符串值时是否忽略尾随空格。</span><span class="sxs-lookup"><span data-stu-id="732c2-154">Indicate whether to ignore trailing spaces when the profile compares string values.</span></span> <span data-ttu-id="732c2-155">此选项的默认值为 **True**。</span><span class="sxs-lookup"><span data-stu-id="732c2-155">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="732c2-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="732c2-156">See Also</span></span>  
 <span data-ttu-id="732c2-157">[数据事件探查任务编辑器（“常规”页）](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="732c2-157">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="732c2-158">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="732c2-158">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
