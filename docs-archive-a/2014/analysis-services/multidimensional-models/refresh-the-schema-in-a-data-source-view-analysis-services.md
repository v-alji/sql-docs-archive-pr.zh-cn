---
title: 刷新数据源视图中的架构 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services], schema updates
- refreshing data source views
- data source views [Analysis Services], refreshing
ms.assetid: 634b0504-1437-43e7-8ac7-3248ac7989a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 808f6ea431592aaecadf6f20a1ae16850cdb20e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579138"
---
# <a name="refresh-the-schema-in-a-data-source-view-analysis-services"></a><span data-ttu-id="cf89f-102">刷新数据源视图中的架构 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="cf89f-102">Refresh the Schema in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="cf89f-103">在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 项目或数据库中定义数据源视图 (DSV) 后，基础数据源中的架构可能会更改。</span><span class="sxs-lookup"><span data-stu-id="cf89f-103">After defining a data source view (DSV) in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or database, the schema in an underlying data source may change.</span></span> <span data-ttu-id="cf89f-104">无法在开发项目中自动检测或更新这些更改。</span><span class="sxs-lookup"><span data-stu-id="cf89f-104">These changes are not automatically detected or updated in a development project.</span></span> <span data-ttu-id="cf89f-105">此外，如果您已将项目部署到服务器，当 Analysis Services 不再连接到外部数据源时，现在会遇到处理错误。</span><span class="sxs-lookup"><span data-stu-id="cf89f-105">Moreover, if you deployed the project to a server, you will now encounter processing errors if Analysis Services can no longer connect to the external data source.</span></span>

 <span data-ttu-id="cf89f-106">为了更新 DSV 以便它与外部数据源匹配，您可以在 Business Intelligence Development Studio (BIDS) 中刷新 DSV。</span><span class="sxs-lookup"><span data-stu-id="cf89f-106">To update the DSV so that it matches the external data source, you can refresh the DSV in Business Intelligence Development Studio (BIDS).</span></span> <span data-ttu-id="cf89f-107">刷新 DSV 会检测 DSV 所基于的外部数据源的更改，并生成枚举外部数据源中的添加或删除操作的更改列表。</span><span class="sxs-lookup"><span data-stu-id="cf89f-107">Refreshing the DSV detects changes to the external data sources upon which the DSV is based, and builds a change list that enumerates the additions or deletions in the external data source.</span></span> <span data-ttu-id="cf89f-108">然后您可以将这些更改集应用到 DSV，以便它与基础数据源重新对齐。</span><span class="sxs-lookup"><span data-stu-id="cf89f-108">You can then apply the set of changes to the DSV that will realign it to the underlying data source.</span></span> <span data-ttu-id="cf89f-109">请注意，在使用 DSV 的项目中，通常需要做其他工作以进一步更新多维数据集和维度。</span><span class="sxs-lookup"><span data-stu-id="cf89f-109">Note that additional work is often required to further update the cubes and dimensions in the project that use the DSV.</span></span>

 <span data-ttu-id="cf89f-110">本主题包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="cf89f-110">This topic includes the following sections:</span></span>

 [<span data-ttu-id="cf89f-111">刷新中支持的更改</span><span class="sxs-lookup"><span data-stu-id="cf89f-111">Changes Supported in Refresh</span></span>](#bkmk_changlist)

 [<span data-ttu-id="cf89f-112">在 SQL Server Data Tools 中刷新 DSV</span><span class="sxs-lookup"><span data-stu-id="cf89f-112">Refresh a DSV in SQL Server Data Tools</span></span>](#bkmk_DSVrefresh)

##  <a name="changes-supported-in-refresh"></a><a name="bkmk_changlist"></a><span data-ttu-id="cf89f-113">刷新中支持的更改</span><span class="sxs-lookup"><span data-stu-id="cf89f-113">Changes Supported in Refresh</span></span>
 <span data-ttu-id="cf89f-114">“DSV 刷新”可以包含以下任意操作：</span><span class="sxs-lookup"><span data-stu-id="cf89f-114">DSV Refresh can include any of the following the actions:</span></span>

-   <span data-ttu-id="cf89f-115">删除表、列和关系</span><span class="sxs-lookup"><span data-stu-id="cf89f-115">Deletion of tables, columns, and relationships</span></span>

-   <span data-ttu-id="cf89f-116">添加列和关系并应用到 DSV 中已包含的表</span><span class="sxs-lookup"><span data-stu-id="cf89f-116">Addition of columns and relationships, as applied to tables that are already included in the DSV</span></span>

-   <span data-ttu-id="cf89f-117">添加新的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="cf89f-117">Addition of new unique constraints.</span></span> <span data-ttu-id="cf89f-118">如果 DSV 中的表存在逻辑主键，那么，在数据源的表中添加物理键时，逻辑键将被删除并由物理键替换。</span><span class="sxs-lookup"><span data-stu-id="cf89f-118">If a logical primary key exists for a table in the DSV and a physical key is added to the table in the data source, the logical key is removed and replaced by the physical key.</span></span>

 <span data-ttu-id="cf89f-119">刷新永远不会将新表添加到 DSV 中。</span><span class="sxs-lookup"><span data-stu-id="cf89f-119">Refresh never adds new tables to a DSV.</span></span> <span data-ttu-id="cf89f-120">如果要添加新表，必须手动添加。</span><span class="sxs-lookup"><span data-stu-id="cf89f-120">If you want to add a new table, you must add it manually.</span></span> <span data-ttu-id="cf89f-121">有关详细信息，请参阅 [在数据源视图中添加或删除表或视图 (Analysis Services)](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)中的解决方案资源管理器运行数据源视图向导。</span><span class="sxs-lookup"><span data-stu-id="cf89f-121">For more information, see [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md).</span></span>

##  <a name="refresh-a-dsv-in-sql-server-data-tools"></a><a name="bkmk_DSVrefresh"></a><span data-ttu-id="cf89f-122">刷新 SQL Server Data Tools 中的 DSV</span><span class="sxs-lookup"><span data-stu-id="cf89f-122">Refresh a DSV in SQL Server Data Tools</span></span>
 <span data-ttu-id="cf89f-123">若要刷新 DSV，请在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的解决方案资源管理器中双击该 DSV，然后单击“刷新数据源视图”按钮或从“数据源视图”菜单选择“刷新”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf89f-123">To refresh a DSV, double-click the DSV from Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then click the Refresh Data Source View button or choose **Refresh** from the Data Source View menu.</span></span>

 <span data-ttu-id="cf89f-124">在刷新过程中， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 将查询所有基础关系数据源以确定 DSV 中包含的表/视图是否发生了更改。</span><span class="sxs-lookup"><span data-stu-id="cf89f-124">During refresh, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] queries all underlying relational data sources to determine whether there have been changes in tables/views which are included in the DSV.</span></span> <span data-ttu-id="cf89f-125">如果建立了到所有基础数据源的连接，并且发生了更改，则您会在 **“刷新数据源视图”** 对话框中看到这些更改。</span><span class="sxs-lookup"><span data-stu-id="cf89f-125">If connections can be established to all underlying data sources and there have been any changes, you will see them in the **Refresh Data Source View** dialog box.</span></span>

 <span data-ttu-id="cf89f-126">!["刷新数据源视图" 对话框](../media/ssas-olapdsv-refresh.gif "“刷新数据源视图”对话框")</span><span class="sxs-lookup"><span data-stu-id="cf89f-126">![Refresh Data Source View dialog box](../media/ssas-olapdsv-refresh.gif "Refresh Data Source View dialog box")</span></span>

 <span data-ttu-id="cf89f-127">该对话框将列出要在 DSV 中删除或添加的表、列、约束和关系。</span><span class="sxs-lookup"><span data-stu-id="cf89f-127">The dialog box lists tables, columns, constraints, and relationships that will be deleted or added in the DSV.</span></span> <span data-ttu-id="cf89f-128">该报表还将列出无法准备好的任意命名查询或计算。</span><span class="sxs-lookup"><span data-stu-id="cf89f-128">The report also lists any named query or calculation that cannot be successfully prepared.</span></span> <span data-ttu-id="cf89f-129">受影响的对象将列在树视图中，其中的列和关系嵌套在表下面，并且指示出每个对象的更改类型（删除或添加）。</span><span class="sxs-lookup"><span data-stu-id="cf89f-129">The affected objects are listed in a tree view with columns and relationships nested under tables and the type of change (deletion or addition) indicated for each object.</span></span> <span data-ttu-id="cf89f-130">标准数据源视图对象图标指示受影响的对象类型。</span><span class="sxs-lookup"><span data-stu-id="cf89f-130">The standard data source view object icons indicate the type of object affected.</span></span>

 <span data-ttu-id="cf89f-131">刷新操作完全基于基础对象的名称进行。</span><span class="sxs-lookup"><span data-stu-id="cf89f-131">Refresh is based completely on the names of the underlying objects.</span></span> <span data-ttu-id="cf89f-132">因此，如果在数据源中重命名基础对象，则数据源视图设计器会将重命名的对象视为两个单独的操作-删除和添加。</span><span class="sxs-lookup"><span data-stu-id="cf89f-132">Therefore, if an underlying object is renamed in the data source, Data Source View Designer treats the renamed object as two separate operations-a deletion and an addition.</span></span> <span data-ttu-id="cf89f-133">在这种情况下，必须手动将重命名后的对象重新添加到数据源视图中。</span><span class="sxs-lookup"><span data-stu-id="cf89f-133">In this case, you may have to manually add the renamed object back to the data source view.</span></span> <span data-ttu-id="cf89f-134">您还可能必须重新创建关系或逻辑主键。</span><span class="sxs-lookup"><span data-stu-id="cf89f-134">You may also have to re-create relationships or logical primary keys.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="cf89f-135">如果已经知道已在数据源中重命名了表，则可以在刷新数据源视图之前，使用 **“替换表”** 命令将表替换为重命名后的表。</span><span class="sxs-lookup"><span data-stu-id="cf89f-135">If you are aware that a table has been renamed in a data source, you may want to use the **Replace Table** command to replace the table with the renamed table before you refresh the data source view.</span></span> <span data-ttu-id="cf89f-136">有关详细信息，请参阅[在数据源视图中替换表或命名查询 (Analysis Services)](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cf89f-136">For more information, see [Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md).</span></span>

 <span data-ttu-id="cf89f-137">检查了报表之后，可以接受更改，也可以取消更新以拒绝任何更改。</span><span class="sxs-lookup"><span data-stu-id="cf89f-137">After you examine the report, you can either accept the changes or cancel the update to reject any changes.</span></span> <span data-ttu-id="cf89f-138">必须接受或拒绝所有更改。</span><span class="sxs-lookup"><span data-stu-id="cf89f-138">All changes must be accepted or rejected together.</span></span> <span data-ttu-id="cf89f-139">不能选择列表中的单个项。</span><span class="sxs-lookup"><span data-stu-id="cf89f-139">You cannot choose individual items in the list.</span></span> <span data-ttu-id="cf89f-140">您还可以保存更改报告。</span><span class="sxs-lookup"><span data-stu-id="cf89f-140">You can also save a report of the changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf89f-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf89f-141">See Also</span></span>
 [<span data-ttu-id="cf89f-142">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="cf89f-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)


