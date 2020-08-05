---
title: 在数据源视图中定义命名查询 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- named queries [Analysis Services], creating
- modifying named queries
- data source views [Analysis Services], named queries
ms.assetid: f09ba8aa-950e-4c0d-961e-970de13200be
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfe2dbc6081e0c33f681ba894b16057c8890e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579850"
---
# <a name="define-named-queries-in-a-data-source-view-analysis-services"></a><span data-ttu-id="8296e-102">在数据源视图中定义命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8296e-102">Define Named Queries in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="8296e-103">命名查询是以表的形式表示的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="8296e-103">A named query is a SQL expression represented as a table.</span></span> <span data-ttu-id="8296e-104">在命名查询中，可以指定一个 SQL 表达式以选择从一个或多个数据源的一个或多个表返回的行和列。</span><span class="sxs-lookup"><span data-stu-id="8296e-104">In a named query, you can specify an SQL expression to select rows and columns returned from one or more tables in one or more data sources.</span></span> <span data-ttu-id="8296e-105">命名查询基于一个表达式，除此之外，它在行和关系方面都与数据源视图 (DSV) 中的其他表相似。</span><span class="sxs-lookup"><span data-stu-id="8296e-105">A named query is like any other table in a data source view (DSV) with rows and relationships, except that the named query is based on an expression.</span></span>  
  
 <span data-ttu-id="8296e-106">命名查询允许您不修改基础数据源即可扩展 DSV 中现有表的关系架构。</span><span class="sxs-lookup"><span data-stu-id="8296e-106">A named query lets you extend the relational schema of existing tables in DSV without modifying the underlying data source.</span></span> <span data-ttu-id="8296e-107">例如，可以使用一系列命名查询将一个复杂的维度表分割为几个较小、较简单的维度表以便在数据库维度中使用。</span><span class="sxs-lookup"><span data-stu-id="8296e-107">For example, a series of named queries can be used to split up a complex dimension table into smaller, simpler dimension tables for use in database dimensions.</span></span> <span data-ttu-id="8296e-108">命名查询还可以用来将来自一个或多个数据源的多个数据库表联接到单个数据源视图表。</span><span class="sxs-lookup"><span data-stu-id="8296e-108">A named query can also be used to join multiple database tables from one or more data sources into a single data source view table.</span></span>  
  
## <a name="creating-a-named-query"></a><span data-ttu-id="8296e-109">创建命名查询</span><span class="sxs-lookup"><span data-stu-id="8296e-109">Creating a Named Query</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8296e-110">您不能将命名计算添加到命名查询，也不能基于包含命名计算的表创建命名查询。</span><span class="sxs-lookup"><span data-stu-id="8296e-110">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>  
  
 <span data-ttu-id="8296e-111">创建命名查询时，需要为 SQL 查询返回的此表的列和数据指定名称，并根据需要对命名查询进行说明。</span><span class="sxs-lookup"><span data-stu-id="8296e-111">When you create a named query, you specify a name, the SQL query returning the columns and data for the table, and optionally, a description of the named query.</span></span> <span data-ttu-id="8296e-112">SQL 表达式可以引用数据源视图中的其他表。</span><span class="sxs-lookup"><span data-stu-id="8296e-112">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="8296e-113">定义命名查询后，命名查询中的 SQL 查询将发送到数据源提供程序并作为一个整体进行验证。</span><span class="sxs-lookup"><span data-stu-id="8296e-113">After the named query is defined, the SQL query in a named query is sent to the provider for the data source and validated as a whole.</span></span> <span data-ttu-id="8296e-114">如果提供程序在 SQL 查询中没有发现任何错误，则将该列添加到表中。</span><span class="sxs-lookup"><span data-stu-id="8296e-114">If the provider does not find any errors in the SQL query, the column is added to the table.</span></span>  
  
 <span data-ttu-id="8296e-115">SQL 查询中引用的表和列不应被限定或只应由表名限定。</span><span class="sxs-lookup"><span data-stu-id="8296e-115">Tables and columns referenced in the SQL query should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="8296e-116">例如，在引用某个表中的 SaleAmount 列时， `SaleAmount` 或 `Sales.SaleAmount` 是有效的，而 `dbo.Sales.SaleAmount` 则会生成错误。</span><span class="sxs-lookup"><span data-stu-id="8296e-116">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>  
  
 <span data-ttu-id="8296e-117">**请注意** 定义查询 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 数据源的命名查询时，包含相关子查询和 GROUP BY 子句的命名查询将失败。</span><span class="sxs-lookup"><span data-stu-id="8296e-117">**Note** When defining a named query that queries a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 data source, a named query that contains a correlated subquery and a GROUP BY clause will fail.</span></span> <span data-ttu-id="8296e-118">有关详细信息，请参阅 [知识库中的](https://support.microsoft.com/kb/274729) Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY [!INCLUDE[msCoName](../../includes/msconame-md.md)] （有关包含相关子查询和 GROUP BY 的 SELECT 语句的内部错误）。</span><span class="sxs-lookup"><span data-stu-id="8296e-118">For more information, see [Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY](https://support.microsoft.com/kb/274729) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.</span></span>  
  
## <a name="add-or-edit-a-named-query"></a><span data-ttu-id="8296e-119">添加或编辑命名查询</span><span class="sxs-lookup"><span data-stu-id="8296e-119">Add or Edit a Named Query</span></span>  
  
1.  <span data-ttu-id="8296e-120">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中添加命名查询的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="8296e-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to add a named query.</span></span>  
  
2.  <span data-ttu-id="8296e-121">在解决方案资源管理器中，展开“数据源视图”\*\*\*\* 文件夹，然后双击数据源视图。</span><span class="sxs-lookup"><span data-stu-id="8296e-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="8296e-122">在“表”\*\*\*\* 或“关系图”\*\*\*\* 窗格中，右键单击空白区域，再单击“新建命名查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8296e-122">In the **Tables** or **Diagram** pane, right-click an open area and then click **New Named Query**.</span></span>  
  
4.  <span data-ttu-id="8296e-123">在 **“创建命名查询”** 对话框中，执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="8296e-123">In the **Create Named Query** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="8296e-124">在 **“名称”** 文本框中，键入查询名称。</span><span class="sxs-lookup"><span data-stu-id="8296e-124">In the **Name** text box, type a query name.</span></span>  
  
    2.  <span data-ttu-id="8296e-125">还可以在 **“说明”** 文本框中键入对查询的说明。</span><span class="sxs-lookup"><span data-stu-id="8296e-125">Optionally, in the **Description** text box, type a description for the query.</span></span>  
  
    3.  <span data-ttu-id="8296e-126">在 **“数据源”** 列表框中，选择将对其执行命名查询的数据源。</span><span class="sxs-lookup"><span data-stu-id="8296e-126">In the **Data Source** list box, select the data source against which the named query will execute.</span></span>  
  
    4.  <span data-ttu-id="8296e-127">在底部窗格中键入此查询，或者使用图形查询生成工具创建查询。</span><span class="sxs-lookup"><span data-stu-id="8296e-127">Type the query in the bottom pane, or use the graphical query building tools to create a query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8296e-128">查询生成用户界面 (UI) 取决于数据源。</span><span class="sxs-lookup"><span data-stu-id="8296e-128">The query-building user interface (UI) depends on the data source.</span></span> <span data-ttu-id="8296e-129">您所得到的不是图形 UI，而是基于文本的一般 UI。</span><span class="sxs-lookup"><span data-stu-id="8296e-129">Instead of getting a graphical UI, you can get a generic UI, which is text-based.</span></span> <span data-ttu-id="8296e-130">您可以使用这些不同的 UI 来实现同样的功能，但必须以不同的方式来操作。</span><span class="sxs-lookup"><span data-stu-id="8296e-130">You can accomplish the same things with these different UIs, but you must do so in different ways.</span></span> <span data-ttu-id="8296e-131">有关详细信息，请参阅[“创建或编辑命名查询”对话框（Analysis Services - 多维数据）](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8296e-131">For more information, see [Create or Edit Named Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
5.  <span data-ttu-id="8296e-132">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="8296e-132">Click **OK**.</span></span> <span data-ttu-id="8296e-133">一个显示两个重叠表的图标出现在表格表头上，指示此表已被一个命名查询替代。</span><span class="sxs-lookup"><span data-stu-id="8296e-133">An icon showing two overlapping tables appears in the table header to indicate that the table has been replaced by a named query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8296e-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8296e-134">See Also</span></span>  
 <span data-ttu-id="8296e-135">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="8296e-135">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="8296e-136">在数据源视图中定义命名计算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8296e-136">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
