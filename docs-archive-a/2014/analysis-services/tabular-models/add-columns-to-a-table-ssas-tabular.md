---
title: 将列添加到 (SSAS 表格) 的表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5974a3cc-caf8-4558-8836-6e3c24b1ee23
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f329150e3b679e67ee65570efbca904a0570786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580419"
---
# <a name="add-columns-to-a-table-ssas-tabular"></a><span data-ttu-id="5b648-102">将列添加到表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5b648-102">Add Columns to a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="5b648-103">本主题介绍如何向现有表中添加列。</span><span class="sxs-lookup"><span data-stu-id="5b648-103">This topic describes how to add columns to an existing table.</span></span>  
  
## <a name="add-columns-from-the-data-source"></a><span data-ttu-id="5b648-104">从数据源添加列</span><span class="sxs-lookup"><span data-stu-id="5b648-104">Add Columns from the Data Source</span></span>  
 <span data-ttu-id="5b648-105">使用表导入向导从数据源表导入数据时，将在模型中创建一个新表，该表包含源表中的所有列，如果您选择使用“预览并筛选”功能来筛选出某些列，则仅包含您选择的那些列和已筛选数据。</span><span class="sxs-lookup"><span data-stu-id="5b648-105">When using the Table Import Wizard to import data from a data source table, a new table is created in the model which includes all of the columns in the source table, or if you choose to filter out certain columns by using the Preview and Filter feature, only those columns and filtered data you select.</span></span> <span data-ttu-id="5b648-106">您还可以编写一个指定要导入的那些列的 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="5b648-106">You can also write a SQL Query that specifies only certain columns to import.</span></span> <span data-ttu-id="5b648-107">但是，您可能以后决定源表具有要添加到模型表的其他列，或需要添加其值从 DAX 公式派生的计算列。</span><span class="sxs-lookup"><span data-stu-id="5b648-107">You may, however, later determine a source table has additional columns that you want to add to the model table, or you need to add a calculated column with values derived from a DAX formula.</span></span>  
  
 <span data-ttu-id="5b648-108">例如，如果在您最初从数据源导入时使用了表导入向导的“预览并筛选”功能以从源表选择有限数目的列，以后又决定添加在源表中存在而在模型表中不存在的另一个列。</span><span class="sxs-lookup"><span data-stu-id="5b648-108">If, for example, when you initially imported from a data source, you used the Preview and Filter feature in the Table Import Wizard to select a limited number of columns from the source table, you later determine that you need to add another column that exists at the source table, but does not yet exist in the model table.</span></span> <span data-ttu-id="5b648-109">或者，例如，在数据源将新的 AdjustedProfit 列添加到 FactSales 表，现在要向模型中的 Sales 表添加同样的 AdjustedProfit 列和数据。</span><span class="sxs-lookup"><span data-stu-id="5b648-109">Or, for example, a new AdjustedProfit column was added to the FactSales table at the data source, and you now want to add the same AdjustedProfit column and data to the Sales table in the model.</span></span>  
  
 <span data-ttu-id="5b648-110">在这些情况下，您可以使用“编辑表属性”对话框来从源表选择列并将它们添加到模型表。</span><span class="sxs-lookup"><span data-stu-id="5b648-110">In these cases, you can use the Edit Table Properties dialog box to select columns from the source table and add them to the model table.</span></span> <span data-ttu-id="5b648-111">“编辑表属性”对话框包含表预览窗口。</span><span class="sxs-lookup"><span data-stu-id="5b648-111">The Edit Table Properties dialog box includes the table preview window.</span></span> <span data-ttu-id="5b648-112">表预览窗口显示源中的表。</span><span class="sxs-lookup"><span data-stu-id="5b648-112">The table preview window displays the table at the source.</span></span> <span data-ttu-id="5b648-113">已包含在模型表定义中的列已被选中。</span><span class="sxs-lookup"><span data-stu-id="5b648-113">Columns that are already included in the model table definition are already checked.</span></span> <span data-ttu-id="5b648-114">未包含在模型表定义中的那些列未被选中。</span><span class="sxs-lookup"><span data-stu-id="5b648-114">Those columns that are not already included in the model table definition are not checked.</span></span> <span data-ttu-id="5b648-115">您可以通过选择列并单击“确定”，将源中的列添加到模型表定义。</span><span class="sxs-lookup"><span data-stu-id="5b648-115">You can add columns from the source to the model table definition by selecting the column and clicking OK.</span></span> <span data-ttu-id="5b648-116">“编辑表属性”对话框中的表预览窗口提供的视图和功能与表导入向导的“预览并筛选”页中表预览窗口提供的视图和功能相同。</span><span class="sxs-lookup"><span data-stu-id="5b648-116">The table preview window in the Edit Table Properties dialog box provides the same view and features as the table preview window in the Preview and Filter page of the Table Import Wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5b648-117">将列添加到包含两个或更多分区的表时，在使用“编辑表属性”对话框将该列添加到表定义前，必须首先使用分区管理器将该列添加到所有定义的分区。</span><span class="sxs-lookup"><span data-stu-id="5b648-117">When adding a column to a table that contains two or more partitions, before adding the column to the table definition by using the Edit Table Properties dialog box, you must first use Partition Manager to add the column to all defined partitions.</span></span> <span data-ttu-id="5b648-118">将该列添加到定义的分区后，可以使用“编辑表属性”对话框将相同的列添加到表定义中。</span><span class="sxs-lookup"><span data-stu-id="5b648-118">After you have added the column to the defined partitions, you can then add the same column to the table definition by using the Edit Table Properties dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b648-119">如果在最初使用表导入向导导入数据时使用了 SQL 查询来选择表和列，必须在“编辑表属性”对话框中再次使用 SQL 查询来将这些列添加到模型表。</span><span class="sxs-lookup"><span data-stu-id="5b648-119">If you used a SQL Query to select tables and columns when you initially used the Table Import Wizard to import data, you must again use a SQL Query in the Edit Table Properties dialog box to add columns to the model table.</span></span>  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a><span data-ttu-id="5b648-120">使用“编辑表属性”对话框从数据源添加列</span><span class="sxs-lookup"><span data-stu-id="5b648-120">To add a column from the data source by using the Edit Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="5b648-121">在模型设计器中，单击要将列添加到的表，单击 **“表”** 菜单，然后单击  **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="5b648-121">In the model designer, click on the table you want to add a column to, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="5b648-122">在 **“编辑表属性”** 对话框中，在表预览窗口中选择要添加的源列，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="5b648-122">In the **Edit Table Properties** dialog box, in the table preview window, select the source column you want to add, and then click OK.</span></span> <span data-ttu-id="5b648-123">已包含在表定义中的列将被选中。</span><span class="sxs-lookup"><span data-stu-id="5b648-123">Columns already included in the table definition will already be checked.</span></span>  
  
## <a name="add-a-calculated-column"></a><span data-ttu-id="5b648-124">添加计算列</span><span class="sxs-lookup"><span data-stu-id="5b648-124">Add a Calculated Column</span></span>  
 <span data-ttu-id="5b648-125">在计算列中，DAX 公式用于定义每一行的值。</span><span class="sxs-lookup"><span data-stu-id="5b648-125">In a calculated column, a DAX formula is used to define a value for each row.</span></span> <span data-ttu-id="5b648-126">例如，您可以创建一个计算列，该列包含简单的公式 (=1) 以将值 1 添加到每行。</span><span class="sxs-lookup"><span data-stu-id="5b648-126">For example, you can create a calculated column with a simple formula (=1) that adds a value of 1 to each row.</span></span> <span data-ttu-id="5b648-127">计算列还可以有更复杂的公式，以基于模型中的其他数据计算值。</span><span class="sxs-lookup"><span data-stu-id="5b648-127">Calculated columns can also have more complex formulas that calculate values based on other data in the model.</span></span> <span data-ttu-id="5b648-128">将在其他主题中更详细介绍计算列。</span><span class="sxs-lookup"><span data-stu-id="5b648-128">Calculated columns are covered in more detail in other topics.</span></span> <span data-ttu-id="5b648-129">有关详细信息，请参阅 [计算列（SSAS 表格）](ssas-calculated-columns.md)中创建的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="5b648-129">For more information, see [Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md).</span></span>  
  
#### <a name="to-create-a-calculated-column"></a><span data-ttu-id="5b648-130">创建计算列</span><span class="sxs-lookup"><span data-stu-id="5b648-130">To create a calculated column</span></span>  
  
1.  <span data-ttu-id="5b648-131">在模型设计器的“数据视图”中，选择要添加新的空白计算列的表，滚动到最右侧的列，或单击“列”\*\*\*\* 菜单，然后单击“添加列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b648-131">In the model designer, in Data View, select the table to which you want to add a new, blank calculated column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="5b648-132">若要在两个现有列之间创建新列，请右键单击某个现有列，然后单击“插入列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b648-132">To create a new column between two existing columns, right-click on an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="5b648-133">在公式栏中，键入 DAX 公式以便为每个行添加属性。</span><span class="sxs-lookup"><span data-stu-id="5b648-133">In the formula bar, type a DAX formula to add attributes for each row.</span></span>  
  
## <a name="add-a-blank-column"></a><span data-ttu-id="5b648-134">添加空白列</span><span class="sxs-lookup"><span data-stu-id="5b648-134">Add a Blank Column</span></span>  
 <span data-ttu-id="5b648-135">可以在模型表中创建命名的空白列。</span><span class="sxs-lookup"><span data-stu-id="5b648-135">You can create a named, blank column in a model table.</span></span> <span data-ttu-id="5b648-136">如果要从另一个源粘贴数据，空白列很有用。</span><span class="sxs-lookup"><span data-stu-id="5b648-136">Blank columns can be useful if you want to paste data from another source.</span></span> <span data-ttu-id="5b648-137">请记住，粘贴的数据的存储方式不同于导入的数据的存储方式。</span><span class="sxs-lookup"><span data-stu-id="5b648-137">Keep in-mind that pasted data is stored differently than imported data.</span></span> <span data-ttu-id="5b648-138">有关详细信息，请参阅[复制并粘贴数据（SSAS 表格）](../copy-and-paste-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="5b648-138">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
#### <a name="to-create-a-named-blank-column"></a><span data-ttu-id="5b648-139">创建命名的空白列</span><span class="sxs-lookup"><span data-stu-id="5b648-139">To create a named, blank column</span></span>  
  
1.  <span data-ttu-id="5b648-140">在模型设计器的“数据视图”中，选择要添加空白列的表，滚动到最右侧的列，或单击“列”\*\*\*\* 菜单，然后单击“添加列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b648-140">In the model designer, in Data View, select the table to which you want to add a blank column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="5b648-141">若要在两个现有列之间创建新列，请右键单击某个现有列，然后单击\*\*\*\*“插入列”。</span><span class="sxs-lookup"><span data-stu-id="5b648-141">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="5b648-142">单击顶部的单元，然后键入名称，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="5b648-142">Click on the top cell, then type a name, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b648-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b648-143">See Also</span></span>  
 <span data-ttu-id="5b648-144">["编辑表属性" 对话框 &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="5b648-144">[Edit Table Properties Dialog Box &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span></span>  
 [<span data-ttu-id="5b648-145">更改表、列或行筛选器映射（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5b648-145">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
