---
title: " (SSAS 表格) 的表和列 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c428d717-05de-436c-b9dc-e8c1925a60ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f23b21ce492fd3160df727c1562ee706848fa99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692550"
---
# <a name="tables-and-columns-ssas-tabular"></a><span data-ttu-id="eb611-102">表和列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-102">Tables and Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="eb611-103">在您通过使用表导入向导将表和数据添加到某一模型后，可通过添加新的数据列、创建表之间的关系、定义对数据进行扩展的计算以及对表中的数据进行筛选和排序以便于查看，开始使用这些表。</span><span class="sxs-lookup"><span data-stu-id="eb611-103">After you have added tables and data into a model by using the Table Import Wizard, you can begin working with the tables by adding new columns of data, creating relationships between tables, defining calculations that extend the data, and filtering and sorting data in the tables for easier viewing.</span></span>  
  
 <span data-ttu-id="eb611-104">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="eb611-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="eb611-105">优点</span><span class="sxs-lookup"><span data-stu-id="eb611-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="eb611-106">使用表和列</span><span class="sxs-lookup"><span data-stu-id="eb611-106">Working with tables and columns</span></span>](#bkmk_working)  
  
-   [<span data-ttu-id="eb611-107">相关任务</span><span class="sxs-lookup"><span data-stu-id="eb611-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="eb611-108">优势</span><span class="sxs-lookup"><span data-stu-id="eb611-108">Benefits</span></span>  
 <span data-ttu-id="eb611-109">在表格模型中，表提供在其中定义列和其他元数据的框架。</span><span class="sxs-lookup"><span data-stu-id="eb611-109">Tables, in tabular models, provide the framework in which columns and other metadata are defined.</span></span> <span data-ttu-id="eb611-110">表包括：</span><span class="sxs-lookup"><span data-stu-id="eb611-110">Tables include:</span></span>  
  
 <span data-ttu-id="eb611-111">**表定义**</span><span class="sxs-lookup"><span data-stu-id="eb611-111">**Table Definition**</span></span>  
 <span data-ttu-id="eb611-112">表定义包括列组。</span><span class="sxs-lookup"><span data-stu-id="eb611-112">The table definition includes the set of columns.</span></span> <span data-ttu-id="eb611-113">列可以从数据源导入，也可以手动添加，例如使用计算列。</span><span class="sxs-lookup"><span data-stu-id="eb611-113">Columns can be imported from a data source or added manually, such as with calculated columns.</span></span>  
  
 <span data-ttu-id="eb611-114">**表元数据**</span><span class="sxs-lookup"><span data-stu-id="eb611-114">**Table Metadata**</span></span>  
 <span data-ttu-id="eb611-115">关系、度量值、角色、透视和粘贴的数据全都是在表的上下文内定义对象的元数据。</span><span class="sxs-lookup"><span data-stu-id="eb611-115">Relationships, measures, roles, perspectives, and pasted data are all metadata the define objects within the context of a table.</span></span>  
  
 <span data-ttu-id="eb611-116">**Data**</span><span class="sxs-lookup"><span data-stu-id="eb611-116">**Data**</span></span>  
 <span data-ttu-id="eb611-117">在您通过使用表导入向导或通过在计算列中创建新数据来首次导入表时，将数据填充到表列中。</span><span class="sxs-lookup"><span data-stu-id="eb611-117">Data is populated in table columns when you first import tables by using the Table Import Wizard or by creating new data in calculated columns.</span></span> <span data-ttu-id="eb611-118">当源中的数据发生更改时，或者在从内存中删除某一模型时，必须运行某一处理操作以便将数据重新填充到表中。</span><span class="sxs-lookup"><span data-stu-id="eb611-118">When data changes at the source, or when a model is removed from memory, you must run a process operation to re-populate the data into the tables.</span></span>  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_working"></a><span data-ttu-id="eb611-119">使用表和列</span><span class="sxs-lookup"><span data-stu-id="eb611-119">Working with tables and columns</span></span>  
 <span data-ttu-id="eb611-120">在模型设计器中，您不直接创建新的模型表。</span><span class="sxs-lookup"><span data-stu-id="eb611-120">In the model designer, you do not create new model tables directly.</span></span> <span data-ttu-id="eb611-121">在从其他数据源导入或复制数据时，会自动为您创建新选项卡。</span><span class="sxs-lookup"><span data-stu-id="eb611-121">A new tab is created automatically for you whenever data is imported or copied from another data source.</span></span> <span data-ttu-id="eb611-122">模型设计器中的每个选项卡都包含一个数据表，其中可能包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="eb611-122">Each tab (in the model designer) contains one table of data, which can include the following:</span></span>  
  
-   <span data-ttu-id="eb611-123">来自关系数据库或其他非关系源（如 Analysis Services 多维数据集）的单个表或视图。</span><span class="sxs-lookup"><span data-stu-id="eb611-123">A single table or view from a relational database, or from other non-relational sources, such as an Analysis Services cube.</span></span>  
  
-   <span data-ttu-id="eb611-124">从数据馈送或文本文件导入的表格形式的数据集合。</span><span class="sxs-lookup"><span data-stu-id="eb611-124">A tabular set of data imported from a feed or text file.</span></span>  
  
-   <span data-ttu-id="eb611-125">关系数据和表格 (HTML) 数据的组合复制并粘贴到表中。</span><span class="sxs-lookup"><span data-stu-id="eb611-125">A combination of both relational data and tabular (HTML) data copy and pasted into the table.</span></span>  
  
 <span data-ttu-id="eb611-126">当您导入数据时，每个表或视图、工作表或数据文件都将作为表添加到模型设计器中。</span><span class="sxs-lookup"><span data-stu-id="eb611-126">When you import data, each table or view, sheet, or file of data is added as a table in the model designer.</span></span> <span data-ttu-id="eb611-127">通常，来自不同数据源的数据添加到单独的选项卡上，但可以使用 **“粘贴”** 和 **“追加粘贴”** 将数据合并到一个表中。</span><span class="sxs-lookup"><span data-stu-id="eb611-127">You typically add data from various sources onto separate tabs, but you can combine data in a single table by using **Paste** and **Paste Append**.</span></span> <span data-ttu-id="eb611-128">有关详细信息，请参阅[复制并粘贴数据（SSAS 表格）](../copy-and-paste-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="eb611-128">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="eb611-129">在添加了所需的数据后，可以创建各表之间的其他关系，查找或引用其他表中的相关值，或者通过添加新的计算列创建派生值。</span><span class="sxs-lookup"><span data-stu-id="eb611-129">After you have added the data that you need, you can create additional relationships between the tables, look up or reference related values in other tables, or create derived values by adding new calculated columns.</span></span>  
  
 <span data-ttu-id="eb611-130">如果您在使用非常大的数据集，则可能要筛选出某些数据，以便这些数据不可见。</span><span class="sxs-lookup"><span data-stu-id="eb611-130">If you are working very large data sets, you may want to filter out certain data so it is not visible.</span></span> <span data-ttu-id="eb611-131">您还可能要按不同的顺序对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="eb611-131">You may also want to sort data in a different order.</span></span> <span data-ttu-id="eb611-132">通过使用模型设计器，您可以使用筛选、排序和隐藏功能来显示或不显示整个列或某些数据。</span><span class="sxs-lookup"><span data-stu-id="eb611-132">By using the model designer, you can use the filter, sort, and hide features to display, or not display, entire columns or certain data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="eb611-133">相关任务</span><span class="sxs-lookup"><span data-stu-id="eb611-133">Related Tasks</span></span>  
  
|<span data-ttu-id="eb611-134">主题</span><span class="sxs-lookup"><span data-stu-id="eb611-134">Topic</span></span>|<span data-ttu-id="eb611-135">说明</span><span class="sxs-lookup"><span data-stu-id="eb611-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="eb611-136">将列添加到表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-136">Add Columns to a Table &#40;SSAS Tabular&#41;</span></span>](add-columns-to-a-table-ssas-tabular.md)|<span data-ttu-id="eb611-137">介绍如何将源列添加到表定义。</span><span class="sxs-lookup"><span data-stu-id="eb611-137">Describes how to add a source column to a table definition.</span></span>|  
|[<span data-ttu-id="eb611-138">删除列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-138">Delete a Column &#40;SSAS Tabular&#41;</span></span>](delete-a-column-ssas-tabular.md)|<span data-ttu-id="eb611-139">说明如何使用模型设计器或“表属性”对话框删除模型表列。</span><span class="sxs-lookup"><span data-stu-id="eb611-139">Describes how to delete a model table column by using the model designer or by using the Table Properties dialog box.</span></span>|  
|[<span data-ttu-id="eb611-140">更改表、列或行筛选器映射（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-140">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)|<span data-ttu-id="eb611-141">介绍如何通过使用表预览或 SQL 查询编辑器在“编辑表属性”对话框中更改表、列或行筛选器映射。</span><span class="sxs-lookup"><span data-stu-id="eb611-141">Describes how to change table, column, or row filter mappings by using the table preview or SQL query editor in the Edit Table Properties dialog box.</span></span>|  
|[<span data-ttu-id="eb611-142">指定“标记为日期表”以便用于时间智能（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-142">Specify Mark as Date Table for use with Time Intelligence &#40;SSAS Tabular&#41;</span></span>](specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|<span data-ttu-id="eb611-143">介绍如何使用“标记为日期表”对话框指定日期表和唯一标识符列。</span><span class="sxs-lookup"><span data-stu-id="eb611-143">Describes how to use the Mark as Date Table dialog box to specify a date table and unique identifier column.</span></span> <span data-ttu-id="eb611-144">在 DAX 公式中使用时间智能函数时，必须指定日期表和唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="eb611-144">Specifying a date table and unique identifier is necessary when using time intelligence functions in DAX formulas.</span></span>|  
|[<span data-ttu-id="eb611-145">添加表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-145">Add a Table &#40;SSAS Tabular&#41;</span></span>](add-a-table-ssas-tabular.md)|<span data-ttu-id="eb611-146">介绍如何通过使用现有数据源连接从数据源中添加表。</span><span class="sxs-lookup"><span data-stu-id="eb611-146">Describes how to add a table from a data source by using an existing data source connection.</span></span>|  
|[<span data-ttu-id="eb611-147">删除表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-147">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)|<span data-ttu-id="eb611-148">介绍如何删除不再需要的模型工作区数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="eb611-148">Describes how to delete tables in your model workspace database that you no longer need.</span></span>|  
|[<span data-ttu-id="eb611-149">重命名表或列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-149">Rename a Table or Column &#40;SSAS Tabular&#41;</span></span>](rename-a-table-or-column-ssas-tabular.md)|<span data-ttu-id="eb611-150">介绍如何重命名表或列以使其在您的模型中更易于标识。</span><span class="sxs-lookup"><span data-stu-id="eb611-150">Describes how to rename a table or column to make it more identifiable in your model.</span></span>|  
|[<span data-ttu-id="eb611-151">设置列的数据类型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-151">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](set-the-data-type-of-a-column-ssas-tabular.md)|<span data-ttu-id="eb611-152">介绍如何更改列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="eb611-152">Describes how to change the data type of a column.</span></span> <span data-ttu-id="eb611-153">数据类型定义列中的数据是如何存储和展示的。</span><span class="sxs-lookup"><span data-stu-id="eb611-153">The data type defines how data in the column is stored and presented.</span></span>|  
|[<span data-ttu-id="eb611-154">隐藏或冻结列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-154">Hide or Freeze Columns &#40;SSAS Tabular&#41;</span></span>](hide-or-freeze-columns-ssas-tabular.md)|<span data-ttu-id="eb611-155">介绍如何隐藏您不想显示的列，以及如何在滚动到模型的其他区域时使模型的某一区域可见，方法是冻结 (锁定) 一个区域中的特定列。</span><span class="sxs-lookup"><span data-stu-id="eb611-155">Describes how to hide columns that you don't want to display and how to keep an area of a model visible while you scroll to another area of the model by freezing (locking) specific columns in one area.</span></span>|  
|[<span data-ttu-id="eb611-156">计算列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-156">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)|<span data-ttu-id="eb611-157">本节中的主题介绍了如何使用计算列向您的模型添加聚合数据。</span><span class="sxs-lookup"><span data-stu-id="eb611-157">Topics in this section describe how you can use calculated columns to add aggregated data to your model.</span></span>|  
|[<span data-ttu-id="eb611-158">对数据进行筛选和排序（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="eb611-158">Filter and Sort Data &#40;SSAS Tabular&#41;</span></span>](../filter-and-sort-data-ssas-tabular.md)|<span data-ttu-id="eb611-159">本节中的主题介绍了如何使用模型设计器中的控件对数据进行筛选或排序。</span><span class="sxs-lookup"><span data-stu-id="eb611-159">Topics in this section describe how you can filter or sort data by using controls in the model designer.</span></span>|  
  
  
