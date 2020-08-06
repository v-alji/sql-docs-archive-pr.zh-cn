---
title: 在数据源视图中定义命名计算 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying named calculations
- data source views [Analysis Services], named calculations
- named calculations [Analysis Services]
ms.assetid: 729e7b12-6185-4b73-8bcb-cfe459b15355
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae901c340fe29c042430d928a4abaea8e8cfe84b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587078"
---
# <a name="define-named-calculations-in-a-data-source-view-analysis-services"></a><span data-ttu-id="32669-102">在数据源视图中定义命名计算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="32669-102">Define Named Calculations in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="32669-103">命名计算是一个表示为计算列的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="32669-103">A named calculation is a SQL expression represented as a calculated column.</span></span> <span data-ttu-id="32669-104">该表达式作为表内的列出现并发挥作用。</span><span class="sxs-lookup"><span data-stu-id="32669-104">This expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="32669-105">使用命名计算，您可以扩展数据源视图中现有表或视图的关系架构，而无需修改基础数据源中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="32669-105">A named calculation lets you extend the relational schema of existing tables or views in a data source view without modifying the tables or views in the underlying data source.</span></span> <span data-ttu-id="32669-106">请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="32669-106">Consider the following examples:</span></span>

-   <span data-ttu-id="32669-107">创建从事实表的多个列派生的单个命名计算（例如，通过将税率与销售价格相乘创建“税额”）。</span><span class="sxs-lookup"><span data-stu-id="32669-107">Create a single named calculation that is derived from multiple columns in a fact table (for example, creating Tax Amount by multiplying a tax rate by a sales price).</span></span>

-   <span data-ttu-id="32669-108">构建维度成员的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="32669-108">Construct a user friendly name for a dimension member.</span></span>

-   <span data-ttu-id="32669-109">作为一种查询性能增强方式，在 DSV 中创建命名查询而非在多维数据集中创建计算成员。</span><span class="sxs-lookup"><span data-stu-id="32669-109">As a query performance enhancement, create a named calculation in the DSV instead of creating a calculated member in a cube.</span></span> <span data-ttu-id="32669-110">命名计算在处理期间进行计算，而计算成员则在查询时进行计算。</span><span class="sxs-lookup"><span data-stu-id="32669-110">Named calculations are calculated during processing whereas calculated members are calculated at query time.</span></span>

## <a name="creating-named-calculations"></a><span data-ttu-id="32669-111">创建命名计算</span><span class="sxs-lookup"><span data-stu-id="32669-111">Creating Named Calculations</span></span>

> [!NOTE]
>  <span data-ttu-id="32669-112">您不能将命名计算添加到命名查询，也不能基于包含命名计算的表创建命名查询。</span><span class="sxs-lookup"><span data-stu-id="32669-112">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>

 <span data-ttu-id="32669-113">当您创建命名计算时，便会指定名称（SQL 表达式）以及可选地指定计算的说明。</span><span class="sxs-lookup"><span data-stu-id="32669-113">When you create a named calculation, you specify a name, the SQL expression, and, optionally, a description of the calculation.</span></span> <span data-ttu-id="32669-114">SQL 表达式可以引用数据源视图中的其他表。</span><span class="sxs-lookup"><span data-stu-id="32669-114">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="32669-115">定义完命名计算之后，便会将命名计算中的表达式发送到数据源的提供程序，然后将表达式作为以下 SQL 语句进行验证，在该语句中， `<Expression>` 包含定义命名计算的表达式。</span><span class="sxs-lookup"><span data-stu-id="32669-115">After the named calculation is defined, the expression in a named calculation is sent to the provider for the data source and validated as the following SQL statement in which `<Expression>` contains the expression that defines the named calculation.</span></span>

```
SELECT 
   <Table Name in Data Source>.*, 
   <Expression> AS <Column Name> 
FROM 
   <Table Name in Data Source> AS <Table Name in Data Source View>
```

 <span data-ttu-id="32669-116">列的数据类型由表达式返回的标量值的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="32669-116">The data type of the column is determined by the data type of the scalar value returned by the expression.</span></span> <span data-ttu-id="32669-117">如果提供程序没有在表达式中找到任何错误，则将该列添加到表内。</span><span class="sxs-lookup"><span data-stu-id="32669-117">If the provider does not find any errors in the expression, the column is added to the table.</span></span>

 <span data-ttu-id="32669-118">表达式中引用的列不应该被限定，或只能由表名进行限定。</span><span class="sxs-lookup"><span data-stu-id="32669-118">Columns referenced in the expression should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="32669-119">例如，在引用某个表中的 SaleAmount 列时， `SaleAmount` 或 `Sales.SaleAmount` 是有效的，而 `dbo.Sales.SaleAmount` 则会生成错误。</span><span class="sxs-lookup"><span data-stu-id="32669-119">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>

 <span data-ttu-id="32669-120">表达式不会自动由括号括住。</span><span class="sxs-lookup"><span data-stu-id="32669-120">The expression is not automatically enclosed between parentheses.</span></span> <span data-ttu-id="32669-121">因此，如果 SELECT 语句之类的表达式需要使用括号，则必须在 **“表达式”** 框中键入括号。</span><span class="sxs-lookup"><span data-stu-id="32669-121">Therefore, if an expression, such as a SELECT statement, requires parentheses, you must type the parentheses in the **Expression** box.</span></span> <span data-ttu-id="32669-122">例如，以下表达式只有在您键入括号之后才有效。</span><span class="sxs-lookup"><span data-stu-id="32669-122">For example, the following expression is valid only if you type the parentheses.</span></span>

```
(SELECT Description FROM Categories WHERE Categories.CategoryID = CategoryID)
```

## <a name="add-or-edit-a-named-calculation"></a><span data-ttu-id="32669-123">添加或编辑命名计算</span><span class="sxs-lookup"><span data-stu-id="32669-123">Add or Edit a Named Calculation</span></span>

1.  <span data-ttu-id="32669-124">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中定义命名计算的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="32669-124">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to define a named calculation.</span></span>

2.  <span data-ttu-id="32669-125">在解决方案资源管理器中，展开“数据源视图”\*\*\*\* 文件夹，然后双击数据源视图。</span><span class="sxs-lookup"><span data-stu-id="32669-125">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>

3.  <span data-ttu-id="32669-126">在“表”或“关系图”窗格中，右键单击要在其中定义命名计算的表，再单击“新建命名计算”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32669-126">Right-click the table in which you wish to define the named calculation in either the **Tables** or the **Diagram** pane, and then click **New Named Calculation**.</span></span> <span data-ttu-id="32669-127">请务必右键单击表名称而不是属性。</span><span class="sxs-lookup"><span data-stu-id="32669-127">Be sure to right-click on the table name, and not on an attribute.</span></span> <span data-ttu-id="32669-128">菜单应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="32669-128">The menu should look like the following:</span></span>

     <span data-ttu-id="32669-129">![“关系图”工作区的右键单击菜单的屏幕快照](../media/ssas-olapdsv-diagram.gif "“关系图”工作区的右键单击菜单的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="32669-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="32669-130">若要查找表或视图，可以通过单击“数据源视图”菜单或者右键单击“表”或“关系图”窗格的空白区域以使用“查找表”选项\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32669-130">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>

4.  <span data-ttu-id="32669-131">在 **“创建命名计算”** 对话框中，执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="32669-131">In the **Create Named Calculations** dialog box, do the following:</span></span>

    -   <span data-ttu-id="32669-132">在 **“列名”** 文本框中，键入新列的名称。</span><span class="sxs-lookup"><span data-stu-id="32669-132">In the **Column name** text box, type the name of the new column.</span></span>

    -   <span data-ttu-id="32669-133">在 **“说明”** 文本框中，键入对新列的说明。</span><span class="sxs-lookup"><span data-stu-id="32669-133">In the **Description** text box type a description for the new column.</span></span>

    -   <span data-ttu-id="32669-134">在 **“表达式”** 文本框中，使用适用于数据访问接口的 SQL 方言键入生成新列内容的表达式。</span><span class="sxs-lookup"><span data-stu-id="32669-134">In the **Expression** text box, type the expression that yields the content of the new column in the SQL dialect appropriate for the data provider.</span></span>

5.  <span data-ttu-id="32669-135">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="32669-135">Click **OK**.</span></span>

     <span data-ttu-id="32669-136">命名计算列显示为数据源视图表的最后一列。</span><span class="sxs-lookup"><span data-stu-id="32669-136">The named calculation column appears as the last column in the data source view table.</span></span> <span data-ttu-id="32669-137">计算器符号指示该列包含命名计算。</span><span class="sxs-lookup"><span data-stu-id="32669-137">A calculator symbol indicates that the column contains a named calculation.</span></span>

## <a name="delete-a-named-calculation"></a><span data-ttu-id="32669-138">删除命名计算</span><span class="sxs-lookup"><span data-stu-id="32669-138">Delete a Named Calculation</span></span>
 <span data-ttu-id="32669-139">尝试删除命名计算时，系统将提示您删除会使在项目或数据库中定义的对象列表失效。</span><span class="sxs-lookup"><span data-stu-id="32669-139">When you attempt to delete a named calculation, you are prompted with a list of the objects defined in the project or database that will be invalidated by the deletion.</span></span> <span data-ttu-id="32669-140">在删除计算之前仔细查看该列表。</span><span class="sxs-lookup"><span data-stu-id="32669-140">Review the list carefully before deleting the calculation.</span></span>

## <a name="see-also"></a><span data-ttu-id="32669-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32669-141">See Also</span></span>
 [<span data-ttu-id="32669-142">在数据源视图中定义命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="32669-142">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)


