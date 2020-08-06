---
title: 在数据源视图中定义逻辑关系 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding relationships
- relationships [Analysis Services], data source views
- data source views [Analysis Services], relationships
ms.assetid: a20d6dae-e769-4131-8a59-7ef56f174220
author: minewiskan
ms.author: owend
ms.openlocfilehash: c46c2b360a4528aeb0eb88348d0d1242b22d8ef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587083"
---
# <a name="define-logical-relationships-in-a-data-source-view-analysis-services"></a><span data-ttu-id="5ed9f-102">在数据源视图中定义逻辑关系 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="5ed9f-102">Define Logical Relationships in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="5ed9f-103">数据源视图向导和数据源视图设计器自动定义添加到数据源视图 (DSV) 的表之间的关系，定义过程基于基础数据库关系或指定的名称匹配条件。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-103">The Data Source View Wizard and Data Source View Designer automatically define relationships between tables added to a data source view (DSV) based on underlying database relationships or name matching criteria you specify.</span></span>  
  
 <span data-ttu-id="5ed9f-104">如果您在使用来自多个数据源的数据，则可能需要在 DSV 中手动定义逻辑关系，以便对自动定义的这些关系进行补充。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-104">In cases where you are working with data from multiple data sources, you may need to manually define logical relationships in the DSV to supplement those relationships that are defined automatically.</span></span> <span data-ttu-id="5ed9f-105">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，需要使用关系来标识事实数据表和维度表，以构建用于从基础数据源检索数据和元数据的查询，以及利用高级业务智能功能。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-105">Relationships are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to identify fact and dimension tables, to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="5ed9f-106">您可以在数据源视图设计器中定义下列关系类型：</span><span class="sxs-lookup"><span data-stu-id="5ed9f-106">You can define the following types of relationships in Data Source View Designer:</span></span>  
  
-   <span data-ttu-id="5ed9f-107">同一数据源中的两个表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-107">A relationship from one table to another table in the same data source.</span></span>  
  
-   <span data-ttu-id="5ed9f-108">一个表与其本身的关系，就像父子关系一样。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-108">A relationship from one table to itself, as in a parent-child relationship.</span></span>  
  
-   <span data-ttu-id="5ed9f-109">某数据源中的一个表与另一个数据源中的另一个表的关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-109">A relationship from one table in a data source to another table in a different data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ed9f-110">在 DSV 中定义的关系是逻辑关系，可能无法反映基础数据源中定义的实际关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-110">The relationships defined in a DSV are logical and may not reflect the actual relationships defined in the underlying data source.</span></span> <span data-ttu-id="5ed9f-111">在数据源视图设计器中，可以创建基础数据源中不存在的关系，也可以从基础数据源的现有外键关系中删除由数据源视图设计器所创建的关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-111">You can create relationships in Data Source View Designer that do not exist in the underlying data source, and remove relationships created by Data Source View Designer from existing foreign key relationships in the underlying data source.</span></span>  
  
 <span data-ttu-id="5ed9f-112">关系是有方向的。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-112">Relationships are directed.</span></span> <span data-ttu-id="5ed9f-113">对于源列中的每个值，在目标列中都有一个对应值。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-113">For every value in the source column, there is a corresponding value in the destination column.</span></span> <span data-ttu-id="5ed9f-114">在数据源视图关系图中（如 **“关系图”** 窗格中显示的关系图），两表之间连线上的箭头指示关系的方向。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-114">In a data source view diagram, such as the diagrams displayed in the **Diagram** pane, an arrow on the line between two tables indicates the direction of the relationship.</span></span>  
  
 <span data-ttu-id="5ed9f-115">本主题包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="5ed9f-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="5ed9f-116">在表、命名查询或视图之间添加关系</span><span class="sxs-lookup"><span data-stu-id="5ed9f-116">To add a relationship between tables, named queries, or views</span></span>](#bkmk_addRel)  
  
 [<span data-ttu-id="5ed9f-117">在 "关系图" 窗格中查看或修改关系</span><span class="sxs-lookup"><span data-stu-id="5ed9f-117">To view or modify a relationship in the Diagram pane</span></span>](#bkmk_diagrampane)  
  
 [<span data-ttu-id="5ed9f-118">在 "表" 窗格中查看或修改关系</span><span class="sxs-lookup"><span data-stu-id="5ed9f-118">To view or modify a relationship in the Tables pane</span></span>](#bkmk_tablespane)  
  
##  <a name="to-add-a-relationship-between-tables-named-queries-or-views"></a><a name="bkmk_addRel"></a><span data-ttu-id="5ed9f-119">添加表、命名查询或视图之间的关系</span><span class="sxs-lookup"><span data-stu-id="5ed9f-119">To add a relationship between tables, named queries, or views</span></span>  
  
1.  <span data-ttu-id="5ed9f-120">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中添加逻辑关系的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to add a logical relationship.</span></span>  
  
2.  <span data-ttu-id="5ed9f-121">在解决方案资源管理器中，展开“数据源视图”文件夹，然后双击数据源视图以便在“数据源视图设计器”中打开该视图\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view to open it in **Data Source View Designer**.</span></span>  
  
3.  <span data-ttu-id="5ed9f-122">在任一“表”\*\*\*\* 窗格中右键单击要添加关系的表、命名查询或视图，再单击“新建关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-122">Right-click the table, named query or view to which you want to add a relationship in either the **Tables** pane and then click **New Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5ed9f-123">若要查找表、视图或命名查询，可以通过单击“数据源视图”菜单或者右键单击“表”或“关系图”窗格的空白区域，以使用“查找表”选项\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-123">To locate a table, view or named query, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
4.  <span data-ttu-id="5ed9f-124">在 **“指定关系”** 对话框中，执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="5ed9f-124">In the **Specify Relationship** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="5ed9f-125">在“源(外键)表”\*\*\*\* 列表中选择适当的表、命名查询或视图。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-125">Select the appropriate table, named query, or view in the **Source (foreign key) table** list.</span></span>  
  
    2.  <span data-ttu-id="5ed9f-126">在“目标(主键)表”\*\*\*\* 列表中选择适当的表、命名查询或视图。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-126">Select the appropriate table, named query, or view in the **Destination (primary key) table** lists.</span></span>  
  
    3.  <span data-ttu-id="5ed9f-127">从 **“源列”** 和 **“目标列”** 列表中选择列，以创建两个表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-127">Select columns from the **Source Columns** and **Destination Columns** lists to create a relationship between the two tables.</span></span>  
  
         <span data-ttu-id="5ed9f-128">如果 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 通过抽样基础表、视图或命名查询中的数据检测到已按错误方向（从主键到外键而不是从外键到主键）定义了关系，则系统将提示反转顺序。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-128">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects, by sampling the data in the underlying table, view, or named query, that you have defined the relationship in the wrong direction (from the primary key to the foreign key rather than from the foreign key to the primary key), you will be prompted to reverse the order.</span></span> <span data-ttu-id="5ed9f-129">若要快速反转顺序，请单击 **“反转”**。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-129">To quickly reverse the order, click **Reverse**.</span></span>  
  
         <span data-ttu-id="5ed9f-130">如果 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 检测到所选列之间已存在关系，则系统将提示您。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-130">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects that a relationship already exists for the columns you have selected, you will be prompted.</span></span> <span data-ttu-id="5ed9f-131">您不能定义重复关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-131">You cannot define duplicate relationships.</span></span>  
  
    4.  <span data-ttu-id="5ed9f-132">还可以在 **“说明”** 框中键入对该关系的说明。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-132">Optionally, in the **Description** box, type a description for the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-diagram-pane"></a><a name="bkmk_diagrampane"></a> <span data-ttu-id="5ed9f-133">在“关系图”窗格中查看或修改关系</span><span class="sxs-lookup"><span data-stu-id="5ed9f-133">To view or modify a relationship in the Diagram pane</span></span>  
  
-   <span data-ttu-id="5ed9f-134">在“数据源视图设计器”的“关系图”窗格中，右键单击要查看的关系，再单击“编辑关系”（或者仅双击关系箭头）\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-134">In the **Diagram** pane in **Data Source View Designer**, right-click the relationship that you want to view and click **Edit Relationship** (or simply double-click the relationship arrow).</span></span>  <span data-ttu-id="5ed9f-135">使用 **“编辑属性关系”** 对话框可修改关系。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-135">Use the **Edit Relationship** dialog box to modify the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-tables-pane"></a><a name="bkmk_tablespane"></a> <span data-ttu-id="5ed9f-136">在“表”窗格中查看或修改关系</span><span class="sxs-lookup"><span data-stu-id="5ed9f-136">To view or modify a relationship in the Tables pane</span></span>  
  
1.  <span data-ttu-id="5ed9f-137">在 **“数据源视图设计器”** 的 **“表”** 窗格中，查找包含要查看或修改的关系的表、视图或命名查询，然后将其展开。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-137">In the **Tables** pane in **Data Source View Designer**, locate and then expand the table, view or named query containing the relationship that you wish to view or modify.</span></span>  
  
2.  <span data-ttu-id="5ed9f-138">展开 **“关系”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-138">Expand the **Relationships** folder.</span></span>  <span data-ttu-id="5ed9f-139">将显示所选表、视图或命名查询与其他表、视图和命名查询之间的关系，并列出关系列。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-139">The relationships between the selected table, view or named query and other tables, views and named queries appear with the relationship column listed.</span></span>  
  
3.  <span data-ttu-id="5ed9f-140">右键单击要修改的关系，然后单击“编辑关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ed9f-140">Right-click the relationship you want to modify, and then click **Edit Relationship**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed9f-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ed9f-141">See Also</span></span>  
 [<span data-ttu-id="5ed9f-142">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="5ed9f-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
