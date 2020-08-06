---
title: 数据源视图设计器 (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.f1
helpviewer_keywords:
- Data Source View Designer
ms.assetid: 6f40a074-761f-440b-a999-09b755bd86ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 31e70f3f9b577f44b9ebb61b5ae2975c0a129828
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690228"
---
# <a name="data-source-view-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="8ebdf-102">数据源视图设计器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="8ebdf-102">Data Source View Designer (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8ebdf-103">数据源视图 (DSV) 是用于在多维模型中创建多维数据集和维度的外部关系数据源的逻辑视图。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-103">A data source view (DSV) is a logical view of an external relational data source used to create cubes and dimensions in a multidimensional model.</span></span>

 <span data-ttu-id="8ebdf-104">在生成 DSV 后，您可以在 **中使用** 数据源视图设计器 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 直接在 DSV 中工作，这在基础数据源缺少多维模型所需的数据元素时很有用。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-104">After a DSV is generated, you can use the **Data Source View Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to work directly on the DSV, which can be useful if the underlying data source is missing data elements needed in a multidimensional model.</span></span>

 <span data-ttu-id="8ebdf-105">打开 **数据源视图设计器** ：</span><span class="sxs-lookup"><span data-stu-id="8ebdf-105">To open **Data Source View Designer** :</span></span>

-   <span data-ttu-id="8ebdf-106">双击“解决方案资源管理器”\*\*\*\* 中的某个数据源视图。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-106">Double-click a data source view in **Solution Explorer**.</span></span>

-   <span data-ttu-id="8ebdf-107">在“解决方案资源管理器”\*\*\*\* 中右键单击某个数据源视图，选择“打开”或“视图设计器”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-107">Right-click a data source view in **Solution Explorer** and select **Open** or **View Designer**.</span></span>

 <span data-ttu-id="8ebdf-108">**数据源视图设计器** 包含一个工具栏、一个显示 DSV 中对象及关系的图表、一个按字母顺序列出表和命名查询的表窗格，以及用于创建和查看 DSV 的特定图表的“关系图组织程序”窗格。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-108">The **Data Source View Designer** contains a toolbar, a diagram showing the objects and relationships in the DSV, a table pane listing tables and named queries in alphabetical order, and a Diagram Organizer pane used to create and view specific diagrams of the DSV.</span></span> <span data-ttu-id="8ebdf-109">您可以通过右键单击某个表或关系来访问上下文相关命令。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-109">You can right-click a table or relationship to access context-sensitive commands.</span></span>

 <span data-ttu-id="8ebdf-110">![数据源视图设计器](media/ssas-dsvdesigner.PNG "数据源视图设计器")</span><span class="sxs-lookup"><span data-stu-id="8ebdf-110">![Data Source View Designer](media/ssas-dsvdesigner.PNG "Data Source View Designer")</span></span>

 <span data-ttu-id="8ebdf-111">DSV 中至少会显示将用于在处理期间填充模型对象的关系数据库表。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-111">At a minimum, a DSV shows the relational database tables that will be used to populate model objects during processing.</span></span> <span data-ttu-id="8ebdf-112">通常可使用数据源视图向导生成 DSV。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-112">A DSV is generated, usually by using the Data Source View wizard.</span></span> <span data-ttu-id="8ebdf-113">DSV 中的表、列和关系将成为多维数据集中维度和度量值的基础。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-113">Tables, columns, and relationships in the DSV become the basis for dimensions and measures in a cube.</span></span> <span data-ttu-id="8ebdf-114">在创建 DSV 后，可以使用数据源视图设计器修改它。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-114">Once the DSV is created, you can use the Data Source View Designer to modify it.</span></span>

 <span data-ttu-id="8ebdf-115">大多数 Analysis Services 开发人员都会使用已生成的现有 DSV，并进行少量自定义。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-115">Most Analysis Services developers use a generated DSV as is, with few customizations.</span></span> <span data-ttu-id="8ebdf-116">特别是在源数据来自 SQL Server 数据库中的视图时尤其如此。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-116">This is especially common if source data originates from a view in a SQL Server database.</span></span> <span data-ttu-id="8ebdf-117">在这种情况下，您可能更希望在 T-SQL 视图（而不是在 Analysis Services DSV）中管理数据关系和计算。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-117">In this case, you might prefer to manage data relationships and calculations in a T-SQL view rather than an Analysis Services DSV.</span></span> <span data-ttu-id="8ebdf-118">但是，如果您不是基础数据库的所有者，则可以在 Analysis Services 中修改 DSV 以便进一步开发您的模型中使用的数据结构。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-118">However, if you are not the owner of the underlying database, you can modify the DSV in Analysis Services to further develop the data structures used in your model.</span></span>

## <a name="tasks-in-data-source-view-designer"></a><span data-ttu-id="8ebdf-119">数据源视图设计器中的任务</span><span class="sxs-lookup"><span data-stu-id="8ebdf-119">Tasks in Data Source View Designer</span></span>
 <span data-ttu-id="8ebdf-120">使用数据源视图设计器，您可以对 DSV 进行以下编辑：</span><span class="sxs-lookup"><span data-stu-id="8ebdf-120">Using Data Source View Designer, you can make the following edits to a DSV:</span></span>

|||
|-|-|
|<span data-ttu-id="8ebdf-121">重命名列或表，或者创建新的计算列。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-121">Rename columns or tables, or create new calculated columns.</span></span> <span data-ttu-id="8ebdf-122">例如，可将名字和姓氏连接到新的全名列。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-122">For example, concatenate a first name and last name into a new full-name column.</span></span>|[<span data-ttu-id="8ebdf-123">在数据源视图中定义命名计算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8ebdf-123">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="8ebdf-124">手动添加表关系</span><span class="sxs-lookup"><span data-stu-id="8ebdf-124">Manually add table relationships</span></span>|[<span data-ttu-id="8ebdf-125">在数据源视图中定义逻辑关系 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8ebdf-125">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="8ebdf-126">创建命名查询以定义基于 T-SQL 查询的新对象。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-126">Create a named query to define a new object based on a T-SQL query.</span></span>|[<span data-ttu-id="8ebdf-127">在数据源视图中定义命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8ebdf-127">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="8ebdf-128">研究基础数据以查看模型对象表示的实际数据值。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-128">Explore underlying data to view actual data values represented by model objects.</span></span><br /><br /> <span data-ttu-id="8ebdf-129">通过数据浏览，您可以直观地检查和复制从基础维度表或查询返回的数据。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-129">Data exploration lets you visually inspect and copy data that is returned from the underlying dimensional table or query.</span></span> <span data-ttu-id="8ebdf-130">默认情况下，数据浏览使用靠前计数抽样方法，具有 5000 个抽样计数，但您可以修正这些设置。</span><span class="sxs-lookup"><span data-stu-id="8ebdf-130">By default, data exploration uses the top count sampling methodology, with a sample count of 5000, but you can revise these settings.</span></span>|[<span data-ttu-id="8ebdf-131">在数据源视图中浏览数据 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8ebdf-131">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="8ebdf-132">为 DSV 中的所有或部分表和关系绘制关系图</span><span class="sxs-lookup"><span data-stu-id="8ebdf-132">Diagram all or part of the tables and relationships in a DSV</span></span>|[<span data-ttu-id="8ebdf-133">使用数据源视图设计器中的关系图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8ebdf-133">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)|

## <a name="see-also"></a><span data-ttu-id="8ebdf-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ebdf-134">See Also</span></span>
 <span data-ttu-id="8ebdf-135">[多维模型中的数据源视图在](multidimensional-models/data-source-views-in-multidimensional-models.md)[数据源视图中添加或删除表或视图的 &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="8ebdf-135">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span></span>


