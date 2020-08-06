---
title: "\"数据集属性\" 对话框-\"字段 (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b766aa23cce390bc3ffdcf10efdb38efc91f3e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578730"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a><span data-ttu-id="ee4f8-102">“数据集属性”对话框 -&gt;“字段”（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="ee4f8-102">Dataset Properties Dialog Box, Fields (Report Builder)</span></span>
  <span data-ttu-id="ee4f8-103">在 **“数据集属性”** 对话框中选择 **“字段”** 可更改报表数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="ee4f8-104">尽管字段列表是自动填充的，但是可以使用 **“字段”** 来添加、编辑和删除查询及计算字段。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
 <span data-ttu-id="ee4f8-105">仅在嵌入数据集上支持计算字段。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-105">Calculated fields are supported only on embedded datasets.</span></span> <span data-ttu-id="ee4f8-106">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-106">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee4f8-107">选项</span><span class="sxs-lookup"><span data-stu-id="ee4f8-107">Options</span></span>  
 <span data-ttu-id="ee4f8-108">**添加**</span><span class="sxs-lookup"><span data-stu-id="ee4f8-108">**Add**</span></span>  
 <span data-ttu-id="ee4f8-109">向数据集添加新的查询或计算字段。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-109">Add a new query or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="ee4f8-110">**删除**</span><span class="sxs-lookup"><span data-stu-id="ee4f8-110">**Delete**</span></span>  
 <span data-ttu-id="ee4f8-111">从数据集中删除所选字段。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-111">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="ee4f8-112">**字段名称**</span><span class="sxs-lookup"><span data-stu-id="ee4f8-112">**Field Name**</span></span>  
 <span data-ttu-id="ee4f8-113">为字段键入名称。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-113">Type a name for the field.</span></span> <span data-ttu-id="ee4f8-114">该字段在数据集中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-114">The field must be unique within the dataset.</span></span> <span data-ttu-id="ee4f8-115">对于数据集中的每个现有字段，名称是预先填充的。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-115">For each existing field in the dataset, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="ee4f8-116">**字段源**</span><span class="sxs-lookup"><span data-stu-id="ee4f8-116">**Field Source**</span></span>  
 <span data-ttu-id="ee4f8-117">为字段输入一个值。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-117">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="ee4f8-118">对于计算字段，字段源必须是由数据集查询检索的现有字段的名称或您所创建的表达式。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-118">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="ee4f8-119">例如，若要创建表示 10 倍于查询字段 Sales 中值的字段，请使用表达式 `=10 * Fields!Sales.Value`。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-119">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="ee4f8-120">对于查询字段，字段源必须是由数据集查询检索的现有字段的名称。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-120">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="ee4f8-121">**表达式 (fx)**</span><span class="sxs-lookup"><span data-stu-id="ee4f8-121">**Expression (fx)**</span></span>  
 <span data-ttu-id="ee4f8-122">为新的计算字段添加或更改表达式。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-122">Add or change an expression for the new calculated field.</span></span> <span data-ttu-id="ee4f8-123">仅当单击 **“添加”** 并选择 **“计算字段”** 时，才会显示此按钮。</span><span class="sxs-lookup"><span data-stu-id="ee4f8-123">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4f8-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee4f8-124">See Also</span></span>  
 <span data-ttu-id="ee4f8-125">[数据集字段集合（报表生成器和 SSRS）](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-125">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ee4f8-126">[创建共享数据集或嵌入数据集 &#40;报表生成器和 SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-126">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ee4f8-127">[报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-127">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="ee4f8-128">["数据集属性" 对话框-"选项" &#40;报表生成器&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-128">[Dataset Properties Dialog Box, Options &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span></span>  
 <span data-ttu-id="ee4f8-129">["数据集属性" 对话框-> "筛选器" &#40;报表生成器&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-129">[Dataset Properties Dialog Box, Filters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span></span>  
 <span data-ttu-id="ee4f8-130">["数据集属性" 对话框-"参数" &#40;报表生成器&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-130">[Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span></span>  
 <span data-ttu-id="ee4f8-131">["数据集属性" 对话框-> "查询 &#40;报表生成器&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-131">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="ee4f8-132">[表达式（报表生成器和 SSRS）](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ee4f8-132">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ee4f8-133">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="ee4f8-133">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
