---
title: 列统计信息配置文件请求选项（数据事件探查任务）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce5c062a12e38d147f3cef95ea09b4c80f7c256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585930"
---
# <a name="column-statistics-profile-request-options-data-profiling-task"></a><span data-ttu-id="4cd80-102">列统计信息配置文件请求选项（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="4cd80-102">Column Statistics Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="4cd80-103">可以使用 **“配置文件请求”** 页的 **“请求属性”** 窗格，为请求窗格中选择的 **“列统计信息配置文件请求”** 设置选项。</span><span class="sxs-lookup"><span data-stu-id="4cd80-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Statistics Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="4cd80-104">列统计信息配置文件报告以下统计信息：数值列的最小值、最大值、平均值和标准偏差以及 `datetime` 列的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="4cd80-104">A Column Statistics profile reports statistics such as minimum, maximum, average, and standard deviation for numeric columns, and minimum and maximum for `datetime` columns.</span></span> <span data-ttu-id="4cd80-105">此配置文件可以帮助您识别数据中的问题，如无效日期。</span><span class="sxs-lookup"><span data-stu-id="4cd80-105">This profile can help you identify problems in your data such as invalid dates.</span></span> <span data-ttu-id="4cd80-106">例如，您对历史日期列进行事件探查，却发现最近的日期是一个将来的日期。</span><span class="sxs-lookup"><span data-stu-id="4cd80-106">For example, you profile a column of historical dates and discover a maximum date that is in the future.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd80-107">本主题中介绍的选项显示在 **“数据事件探查任务编辑器”** 的 **“配置文件请求”** 页中。</span><span class="sxs-lookup"><span data-stu-id="4cd80-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="4cd80-108">有关此编辑器页的详细信息，请参阅[数据事件探查任务编辑器（“配置文件请求”页）](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd80-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="4cd80-109">有关如何使用数据事件探查任务的详细信息，请参阅 [设置数据事件探查任务](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd80-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="4cd80-110">有关如何使用数据配置文件查看器分析数据事件探查任务输出的详细信息，请参阅 [数据配置文件查看器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd80-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="4cd80-111">请求属性选项</span><span class="sxs-lookup"><span data-stu-id="4cd80-111">Request Properties Options</span></span>  
 <span data-ttu-id="4cd80-112">对于 **“列统计信息配置文件请求”** ， **“请求属性”** 窗格显示下面的选项组：</span><span class="sxs-lookup"><span data-stu-id="4cd80-112">For a **Column Statistics Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="4cd80-113">**Data**，它包含 **TableOrView** 选项和 **Column** 选项</span><span class="sxs-lookup"><span data-stu-id="4cd80-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="4cd80-114">**常规**</span><span class="sxs-lookup"><span data-stu-id="4cd80-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="4cd80-115">Data 选项</span><span class="sxs-lookup"><span data-stu-id="4cd80-115">Data Options</span></span>  
 <span data-ttu-id="4cd80-116">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="4cd80-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="4cd80-117">选择使用 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接管理器连接到包含要进行事件探查的表或视图的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="4cd80-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="4cd80-118">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="4cd80-118">**TableOrView**</span></span>  
 <span data-ttu-id="4cd80-119">选择包含要进行事件探查的列的现有表或视图。</span><span class="sxs-lookup"><span data-stu-id="4cd80-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="4cd80-120">有关详细信息，请参阅本主题中的“TableorView 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="4cd80-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="4cd80-121">**列**</span><span class="sxs-lookup"><span data-stu-id="4cd80-121">**Column**</span></span>  
 <span data-ttu-id="4cd80-122">选择要进行事件探查的现有列。</span><span class="sxs-lookup"><span data-stu-id="4cd80-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="4cd80-123">选择 **(\*)** 可对所有列进行事件探查。</span><span class="sxs-lookup"><span data-stu-id="4cd80-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="4cd80-124">有关详细信息，请参阅本主题中的“Column 选项”部分。</span><span class="sxs-lookup"><span data-stu-id="4cd80-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="4cd80-125">TableOrView 选项</span><span class="sxs-lookup"><span data-stu-id="4cd80-125">TableOrView Options</span></span>  
 <span data-ttu-id="4cd80-126">**架构**</span><span class="sxs-lookup"><span data-stu-id="4cd80-126">**Schema**</span></span>  
 <span data-ttu-id="4cd80-127">指定选定表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="4cd80-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="4cd80-128">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="4cd80-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="4cd80-129">**表**</span><span class="sxs-lookup"><span data-stu-id="4cd80-129">**Table**</span></span>  
 <span data-ttu-id="4cd80-130">显示所选表的名称。</span><span class="sxs-lookup"><span data-stu-id="4cd80-130">Displays the name of the selected table.</span></span> <span data-ttu-id="4cd80-131">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="4cd80-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="4cd80-132">Column 选项</span><span class="sxs-lookup"><span data-stu-id="4cd80-132">Column Options</span></span>  
 <span data-ttu-id="4cd80-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="4cd80-133">**IsWildCard**</span></span>  
 <span data-ttu-id="4cd80-134">指定是否已选择通配符 **(\*)** 。</span><span class="sxs-lookup"><span data-stu-id="4cd80-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="4cd80-135">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="4cd80-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="4cd80-136">如果您已选择要对单独列进行事件探查，则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="4cd80-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="4cd80-137">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="4cd80-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="4cd80-138">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="4cd80-138">**ColumnName**</span></span>  
 <span data-ttu-id="4cd80-139">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="4cd80-139">Displays the name of the selected column.</span></span> <span data-ttu-id="4cd80-140">如果已选择 **(\*)** 来对所有列进行事件探查，则此选项空白。</span><span class="sxs-lookup"><span data-stu-id="4cd80-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="4cd80-141">此选项是只读的。</span><span class="sxs-lookup"><span data-stu-id="4cd80-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="4cd80-142">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="4cd80-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="4cd80-143">此选项不适用于列统计信息配置文件。</span><span class="sxs-lookup"><span data-stu-id="4cd80-143">This option does not apply to the Column Statistics Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="4cd80-144">常规选项</span><span class="sxs-lookup"><span data-stu-id="4cd80-144">General Options</span></span>  
 <span data-ttu-id="4cd80-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="4cd80-145">**RequestID**</span></span>  
 <span data-ttu-id="4cd80-146">键入一个标识此配置文件请求的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="4cd80-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="4cd80-147">通常无需更改自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="4cd80-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd80-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cd80-148">See Also</span></span>  
 <span data-ttu-id="4cd80-149">[数据事件探查任务编辑器（“常规”页）](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="4cd80-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="4cd80-150">单个表快速配置文件窗体（数据事件探查任务）</span><span class="sxs-lookup"><span data-stu-id="4cd80-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
