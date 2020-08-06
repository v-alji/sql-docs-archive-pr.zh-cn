---
title: 列 Null 比率配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e47c09a9a19eae4aed21c0c518430bc19a45648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585933"
---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a><span data-ttu-id="41a75-102">列 Null 比率配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="41a75-102">Column Null Ratio Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="41a75-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选定的 **“列 Null 比率请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="41a75-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Null Ratio Request** selected in the requests pane.</span></span> <span data-ttu-id="41a75-104">列 Null 比率配置文件报告选定列中 null 值的百分比。</span><span class="sxs-lookup"><span data-stu-id="41a75-104">A Column Null Ratio profile reports the percentage of null values in the selected column.</span></span> <span data-ttu-id="41a75-105">此配置文件可以帮助您识别数据中的问题，例如，列中 null 值的比率以外偏高。</span><span class="sxs-lookup"><span data-stu-id="41a75-105">This profile can help you identify problems in your data such as an unexpectedly high ratio of null values in a column.</span></span> <span data-ttu-id="41a75-106">例如，列 Null 比率配置文件对邮政编码列进行事件探查时发现，该列中缺少邮政编码的行所占的比例超出允许的范围。</span><span class="sxs-lookup"><span data-stu-id="41a75-106">For example, a Column Null Ratio profile can profile a ZIP Code/Postal Code column and discover an unacceptably high percentage of missing postal codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41a75-107">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="41a75-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="41a75-108">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="41a75-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="41a75-109">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="41a75-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="41a75-110">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="41a75-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="41a75-111">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="41a75-111">Request Properties Options</span></span>  
 <span data-ttu-id="41a75-112">对于 **“列 Null 比率请求”** ， **“请求属性”** 窗格显示下面的选项组：</span><span class="sxs-lookup"><span data-stu-id="41a75-112">For a **Column Null Ratio Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="41a75-113">**Data**，它包含 **TableOrView** 选项和 **Column** 选项</span><span class="sxs-lookup"><span data-stu-id="41a75-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="41a75-114">**常规**</span><span class="sxs-lookup"><span data-stu-id="41a75-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="41a75-115">Data 选项</span><span class="sxs-lookup"><span data-stu-id="41a75-115">Data Options</span></span>  
 <span data-ttu-id="41a75-116">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="41a75-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="41a75-117">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器来连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库，其中包含要进行事件探查的表或视图。</span><span class="sxs-lookup"><span data-stu-id="41a75-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="41a75-118">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="41a75-118">**TableOrView**</span></span>  
 <span data-ttu-id="41a75-119">选择包含要进行事件探查的列的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="41a75-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="41a75-120">有关详细信息，请参阅本主题中的“TableorView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="41a75-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="41a75-121">**列**</span><span class="sxs-lookup"><span data-stu-id="41a75-121">**Column**</span></span>  
 <span data-ttu-id="41a75-122">选择要进行事件探查的现有列。</span><span class="sxs-lookup"><span data-stu-id="41a75-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="41a75-123">选择 **(\*)** 可对所有列进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="41a75-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="41a75-124">有关详细信息，请参阅本主题中的“Column 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="41a75-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="41a75-125">TableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="41a75-125">TableOrView Options</span></span>  
 <span data-ttu-id="41a75-126">**架构**</span><span class="sxs-lookup"><span data-stu-id="41a75-126">**Schema**</span></span>  
 <span data-ttu-id="41a75-127">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="41a75-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="41a75-128">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="41a75-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="41a75-129">**表**</span><span class="sxs-lookup"><span data-stu-id="41a75-129">**Table**</span></span>  
 <span data-ttu-id="41a75-130">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="41a75-130">Displays the name of the selected table.</span></span> <span data-ttu-id="41a75-131">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="41a75-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="41a75-132">Column 选项</span><span class="sxs-lookup"><span data-stu-id="41a75-132">Column Options</span></span>  
 <span data-ttu-id="41a75-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="41a75-133">**IsWildCard**</span></span>  
 <span data-ttu-id="41a75-134">指定是否已选择通配符 **(\*)** 。</span><span class="sxs-lookup"><span data-stu-id="41a75-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="41a75-135">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="41a75-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="41a75-136">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="41a75-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="41a75-137">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="41a75-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="41a75-138">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="41a75-138">**ColumnName**</span></span>  
 <span data-ttu-id="41a75-139">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="41a75-139">Displays the name of the selected column.</span></span> <span data-ttu-id="41a75-140">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项空白。</span><span class="sxs-lookup"><span data-stu-id="41a75-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="41a75-141">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="41a75-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="41a75-142">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="41a75-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="41a75-143">此选项不适用于列 Null 比率配置文件。</span><span class="sxs-lookup"><span data-stu-id="41a75-143">This option does not apply to the Column Null Ratio Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="41a75-144">常规选项</span><span class="sxs-lookup"><span data-stu-id="41a75-144">General Options</span></span>  
 <span data-ttu-id="41a75-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="41a75-145">**RequestID**</span></span>  
 <span data-ttu-id="41a75-146">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="41a75-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="41a75-147">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="41a75-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a75-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41a75-148">See Also</span></span>  
 <span data-ttu-id="41a75-149">[数据事件探查任务编辑器（“常规”页）](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="41a75-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="41a75-150">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="41a75-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
