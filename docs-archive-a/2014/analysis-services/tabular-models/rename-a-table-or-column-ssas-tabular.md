---
title: " (SSAS 表格) 中重命名表或列 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3a2e9a9f41434e64f9ec5ea2180861b459e8f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692558"
---
# <a name="rename-a-table-or-column-ssas-tabular"></a><span data-ttu-id="a24f9-102">重命名表或列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="a24f9-102">Rename a Table or Column (SSAS Tabular)</span></span>
  <span data-ttu-id="a24f9-103">在导入过程中，您可以通过在 **“表导入向导”** 的 **“选择表和视图”** 页中键入 **“友好名称”**，更改表的名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-103">You can change the name of a table during the import process by typing a **Friendly Name** in the **Select Tables and Views** page of the **Table Import Wizard**.</span></span> <span data-ttu-id="a24f9-104">如果您通过在 **“表导入向导”** 的 **“指定 SQL 查询”** 页上指定查询来导入数据，也可以更改表和列名。</span><span class="sxs-lookup"><span data-stu-id="a24f9-104">You can also change table and column names if you import data by specifying a query on the **Specify a SQL Query** page of the **Table Import Wizard**.</span></span>  
  
 <span data-ttu-id="a24f9-105">在您将数据添加到模型中后，表的名称（或标题）将出现在模型设计器底部的表选项卡上。</span><span class="sxs-lookup"><span data-stu-id="a24f9-105">After you have added the data to the model, the name (or title) of a table appears on the table tab, at the bottom of the model designer.</span></span> <span data-ttu-id="a24f9-106">您可以更改表的名称，以便为其提供更为合适的名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-106">You can change the name of your table to give it a more appropriate name.</span></span> <span data-ttu-id="a24f9-107">您还可以在数据添加到模型中之后重命名列。</span><span class="sxs-lookup"><span data-stu-id="a24f9-107">You can also rename a column after the data has been added to the model.</span></span> <span data-ttu-id="a24f9-108">在您从多个源导入了数据，并且想要确保不同表中的列具有易于区分的名称时，此选项特别重要。</span><span class="sxs-lookup"><span data-stu-id="a24f9-108">This option is especially important when you have imported data from multiple sources, and want to ensure that columns in different tables have names that are easy to distinguish.</span></span>  
  
### <a name="to-rename-a-table"></a><span data-ttu-id="a24f9-109">重命名表</span><span class="sxs-lookup"><span data-stu-id="a24f9-109">To rename a table</span></span>  
  
1.  <span data-ttu-id="a24f9-110">在模型设计器中，右键单击包含要重命名的表的选项卡，然后单击 **“重命名”**。</span><span class="sxs-lookup"><span data-stu-id="a24f9-110">In the model designer, right-click the tab that contains the table that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="a24f9-111">键入新名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-111">Type the new name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a24f9-112">您可以通过使用 **“编辑表属性”** 对话框，编辑表的其他属性，包括连接信息和列映射。</span><span class="sxs-lookup"><span data-stu-id="a24f9-112">You can edit other properties of a table, including the connection information and column mappings, by using the **Edit Table Properties** dialog box.</span></span> <span data-ttu-id="a24f9-113">但无法在该对话框中更改名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-113">However, you cannot change the name in this dialog box.</span></span>  
  
### <a name="to-rename-a-column"></a><span data-ttu-id="a24f9-114">重命名列</span><span class="sxs-lookup"><span data-stu-id="a24f9-114">To rename a column</span></span>  
  
1.  <span data-ttu-id="a24f9-115">在模型设计器中，双击要重命名的列的标题，或者右键单击该标题，然后从上下文菜单中选择 **“重命名列”** 。</span><span class="sxs-lookup"><span data-stu-id="a24f9-115">In the model designer, double-click the header of the column that you want to rename, or right-click the header and select **Rename Column** from the context menu.</span></span>  
  
2.  <span data-ttu-id="a24f9-116">键入新名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-116">Type the new name.</span></span>  
  
## <a name="naming-requirements-for-columns-and-tables"></a><span data-ttu-id="a24f9-117">列和表的命名要求</span><span class="sxs-lookup"><span data-stu-id="a24f9-117">Naming Requirements for Columns and Tables</span></span>  
 <span data-ttu-id="a24f9-118">下面的单词和字符不能用于表或列的名称中：</span><span class="sxs-lookup"><span data-stu-id="a24f9-118">The following words and characters cannot be used in the name of a table or column:</span></span>  
  
-   <span data-ttu-id="a24f9-119">前导空格或尾随空格</span><span class="sxs-lookup"><span data-stu-id="a24f9-119">Leading or trailing spaces</span></span>  
  
-   <span data-ttu-id="a24f9-120">控制字符</span><span class="sxs-lookup"><span data-stu-id="a24f9-120">Control characters</span></span>  
  
-   <span data-ttu-id="a24f9-121">以下字符在 Analysis Services 对象的名称中无效 () ：.，; '：/ \\*|?&% $！ + = ( # A3 [] {}<></span><span class="sxs-lookup"><span data-stu-id="a24f9-121">The following characters (which are not valid in the names of Analysis Services objects): .,;':/\\*|?&%$!+=()[]{}<></span></span>  
  
-   <span data-ttu-id="a24f9-122">Analysis Services 保留关键字，包括多维表达式 (MDX) 和数据挖掘扩展插件 (DMX) 函数名称和运算符。</span><span class="sxs-lookup"><span data-stu-id="a24f9-122">Analysis Services reserved keywords, including Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) function names and operators.</span></span>  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a><span data-ttu-id="a24f9-123">重命名对现有表、列和计算的影响</span><span class="sxs-lookup"><span data-stu-id="a24f9-123">Effect of Renaming on Existing Tables, Columns, and Calculations</span></span>  
 <span data-ttu-id="a24f9-124">只要您更改某一表的名称，就会更改可能包含多个列或度量值的基础表对象的名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-124">Whenever you change the name of a table, you change the name of the underlying table object, which may contain multiple columns or measures.</span></span> <span data-ttu-id="a24f9-125">因此，该表中的所有列以及使用该表的所有关系也必须更新，以便在其定义中使用这个新名称。</span><span class="sxs-lookup"><span data-stu-id="a24f9-125">Therefore, any columns that are in the table, and any relationships that use the table, must be updated to use the new name in their definitions.</span></span> <span data-ttu-id="a24f9-126">在某些情况下此更新将自动发生。</span><span class="sxs-lookup"><span data-stu-id="a24f9-126">This update happens automatically in some cases.</span></span> <span data-ttu-id="a24f9-127">度量值不会自动更新。</span><span class="sxs-lookup"><span data-stu-id="a24f9-127">Measures are not updated automatically.</span></span>  
  
 <span data-ttu-id="a24f9-128">此外，使用重命名表的所有计算或者使用来自重命名表的列的所有计算也都必须更新，并且从这些计算派生的数据也必须刷新和重新计算。</span><span class="sxs-lookup"><span data-stu-id="a24f9-128">Moreover, any calculations that use the renamed table, or that use columns from the renamed table, must also be updated, and the data derived from those calculations must be refreshed and recalculated.</span></span> <span data-ttu-id="a24f9-129">根据受到影响的表和计算的数目，上述刷新和重新计算可能需要一些时间才能完成。</span><span class="sxs-lookup"><span data-stu-id="a24f9-129">Depending on how many tables and calculations are affected, this can take some time to complete.</span></span> <span data-ttu-id="a24f9-130">因此，重命名表的最佳时机是在导入过程中，或者是在开始生成复杂的关系和计算之前。</span><span class="sxs-lookup"><span data-stu-id="a24f9-130">Therefore, the best time to rename tables is either during the import process, or before you start to build complex relationships and calculations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24f9-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a24f9-131">See Also</span></span>  
 <span data-ttu-id="a24f9-132">[&#40;SSAS 表格&#41;的表和列](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a24f9-132">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="a24f9-133">[从 PowerPivot &#40;SSAS 表格&#41;导入](import-from-power-pivot-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a24f9-133">[Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="a24f9-134">从 Analysis Services 导入（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="a24f9-134">Import from Analysis Services &#40;SSAS Tabular&#41;</span></span>](import-from-analysis-services-ssas-tabular.md)  
  
  
