---
title: 在数据源视图中替换表或命名查询 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- replacing tables
- data source views [Analysis Services], tables
- named queries [Analysis Services], replacing tables
- tables [Analysis Services], data source views
- partitions [Analysis Services], named queries
ms.assetid: 60c2a018-1299-4915-b60e-e73316524def
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b5055de60ba757c9dcfa118e4e2c4748c6534e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588102"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a><span data-ttu-id="c7b88-102">在数据源视图中替换表或命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="c7b88-102">Replace a Table or a Named Query in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="c7b88-103">在数据源视图设计器中，可以将数据源视图 (DSV) 中的表、视图或命名查询替换为来自相同数据源或不同数据源的其他表或视图，或者替换为 DSV 中定义的命名查询。</span><span class="sxs-lookup"><span data-stu-id="c7b88-103">In Data Source View Designer, you can replace a table, view, or named query in a data source view (DSV) with a different table or view from the same or a different data source, or with a named query defined in the DSV.</span></span> <span data-ttu-id="c7b88-104">替换表时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中的所有其他对象或引用了该表的项目将继续引用该表，因为 DSV 中表的对象 ID 不会发生更改。</span><span class="sxs-lookup"><span data-stu-id="c7b88-104">When you replace a table, all other objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project that have references to the table continue to reference the table because the object ID for the table in the DSV does not change.</span></span> <span data-ttu-id="c7b88-105">任何仍然相关（基于名称和列类型匹配）的关系仍然保留。</span><span class="sxs-lookup"><span data-stu-id="c7b88-105">Any relationships that are still relevant (based on name and column-type matching) are retained.</span></span> <span data-ttu-id="c7b88-106">与此不同的是，如果删除后再添加表，则将丢失引用和关系，因此必须重新创建引用和关系。</span><span class="sxs-lookup"><span data-stu-id="c7b88-106">In contrast, if you delete and then add a table, references and relationships are lost and must be recreated.</span></span>  
  
 <span data-ttu-id="c7b88-107">若要使用其他表替换表，必须在项目模式下与数据源视图设计器中的源数据建立活动连接。</span><span class="sxs-lookup"><span data-stu-id="c7b88-107">To replace a table with another table, you must have an active connection to the source data in Data Source View Designer in project mode.</span></span>  
  
 <span data-ttu-id="c7b88-108">最常用的替换是使用数据源中的其他表替换该数据源视图中的表。</span><span class="sxs-lookup"><span data-stu-id="c7b88-108">You most frequently replace a table in the data source view with another table in the data source.</span></span> <span data-ttu-id="c7b88-109">但是，也可以使用表替换命名查询。</span><span class="sxs-lookup"><span data-stu-id="c7b88-109">However, you can also replace a named query with a table.</span></span> <span data-ttu-id="c7b88-110">例如，以前使用命名查询替换了一个表，现在想要恢复为表。</span><span class="sxs-lookup"><span data-stu-id="c7b88-110">For example, you previously replaced a table with a named query, and now want to revert to a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7b88-111">如果要重命名数据源中的表，请按以下步骤替换表，并在刷新 DSV 之前，指定重命名后的表作为 DSV 中对应的表的源。</span><span class="sxs-lookup"><span data-stu-id="c7b88-111">If you rename a table in a data source, follow the steps for replacing a table and specify the renamed table as the source of the corresponding table in the DSV before you refresh a DSV.</span></span> <span data-ttu-id="c7b88-112">完成替换和重命名处理后，将在 DSV 中保存表、表的引用和表的关系。</span><span class="sxs-lookup"><span data-stu-id="c7b88-112">Completing the replacement and renaming process preserves the table, the table's references, and the table's relationships in the DSV.</span></span> <span data-ttu-id="c7b88-113">否则，在刷新 DSV 时，数据源中重命名后的表将被解释为已删除。</span><span class="sxs-lookup"><span data-stu-id="c7b88-113">Otherwise, when you refresh the DSV, a renamed table in data source is interpreted as being deleted.</span></span> <span data-ttu-id="c7b88-114">有关详细信息，请参阅[刷新数据源视图中的架构 (Analysis Services)](refresh-the-schema-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c7b88-114">For more information, see [Refresh the Schema in a Data Source View &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md).</span></span>  
  
##  <a name="replace-a-table-with-a-named-query"></a><a name="bkmk_nq"></a> <span data-ttu-id="c7b88-115">使用命名查询替换表</span><span class="sxs-lookup"><span data-stu-id="c7b88-115">Replace a table with a named query</span></span>  
  
1.  <span data-ttu-id="c7b88-116">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中替换表或命名查询的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="c7b88-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="c7b88-117">在解决方案资源管理器中，展开“数据源视图”\*\*\*\* 文件夹，然后双击数据源视图。</span><span class="sxs-lookup"><span data-stu-id="c7b88-117">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="c7b88-118">将打开 **“创建命名查询”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c7b88-118">Open the **Create Named Query** dialog box.</span></span> <span data-ttu-id="c7b88-119">在“表”或“关系图”窗格中，右键单击要替换的表，指向“替换表”，再单击“使用新建命名查询”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c7b88-119">In either **Tables** or **Diagram** pane, right-click the table that you wish to replace, point to **Replace Table** and then click **With New Named Query**.</span></span>  
  
4.  <span data-ttu-id="c7b88-120">在 **“创建命名查询”** 对话框中，定义命名查询，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="c7b88-120">In the **Create Named Query** dialog box, define the named query and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c7b88-121">保存已修改的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="c7b88-121">Save the modified data source view.</span></span>  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a><span data-ttu-id="c7b88-122">使用表替换表或命名查询</span><span class="sxs-lookup"><span data-stu-id="c7b88-122">Replace a table or named query with a table</span></span>  
  
1.  <span data-ttu-id="c7b88-123">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中替换表或命名查询的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="c7b88-123">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="c7b88-124">在解决方案资源管理器中，展开“数据源视图”\*\*\*\* 文件夹，然后双击数据源视图。</span><span class="sxs-lookup"><span data-stu-id="c7b88-124">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="c7b88-125">将打开 **“用其他表替换该表”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c7b88-125">Open the **Replace Table with Other Table** dialog box.</span></span> <span data-ttu-id="c7b88-126">在“表”或“关系图”窗格中，右键单击要替换的表或命名查询，指向“替换表”，再单击“使用其他表”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c7b88-126">In either **Tables** or **Diagram** pane, right-click the table or named query that you wish to replace, point to **Replace Table** and then click **With Other Table**.</span></span>  
  
4.  <span data-ttu-id="c7b88-127">在 **“用其他表替换该表”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="c7b88-127">In the **Replace Table with Other Table** dialog box:</span></span>  
  
    1.  <span data-ttu-id="c7b88-128">在“数据源”下拉列表框中，选择所需数据源\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c7b88-128">In the **DataSource** drop-down list box, select the desired data source</span></span>  
  
    2.  <span data-ttu-id="c7b88-129">选择要用以替换表或命名查询的表</span><span class="sxs-lookup"><span data-stu-id="c7b88-129">Select the table with which you wish to replace the table or named query</span></span>  
  
5.  <span data-ttu-id="c7b88-130">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c7b88-130">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c7b88-131">保存已修改的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="c7b88-131">Save the modified data source view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b88-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7b88-132">See Also</span></span>  
 [<span data-ttu-id="c7b88-133">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="c7b88-133">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
