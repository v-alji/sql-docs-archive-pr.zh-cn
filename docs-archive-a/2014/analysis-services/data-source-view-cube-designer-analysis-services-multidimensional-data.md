---
title: 数据源视图 (多维数据集结构 "选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.datasourcepane.f1
ms.assetid: 1e39c910-5c10-4624-be27-ca02a461b46b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c949eaa17ec9d8bf585a5d595f31779382c41ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690227"
---
# <a name="data-source-view-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="dcc0f-102">数据源视图（“多维数据集结构”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="dcc0f-102">Data Source View (Cube Structure Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="dcc0f-103">可以使用 **“数据源视图”** 窗格，查看与所选多维数据集关联的数据源视图中的表和列。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-103">Use the **Data Source View** pane to view tables and columns from the data source view associated with the selected cube.</span></span> <span data-ttu-id="dcc0f-104">此窗格用于创建度量值组和度量值，方法是将列从 **“数据源视图”** 窗格拖动到 **“度量值”** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-104">This pane is used to create measure groups and measures by dragging columns from the **Data Source View** pane to the **Measures** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcc0f-105">选项</span><span class="sxs-lookup"><span data-stu-id="dcc0f-105">Options</span></span>  
 <span data-ttu-id="dcc0f-106">**“数据源视图”**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-106">**Data Source View**</span></span>  
 <span data-ttu-id="dcc0f-107">显示与所选多维数据集关联的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-107">Displays the data source view associated with the selected cube.</span></span>  
  
 <span data-ttu-id="dcc0f-108">**(移动视点)**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-108">**(Move viewpoint)**</span></span>  
 <span data-ttu-id="dcc0f-109">单击窗格右下角滚动条之间的位置，即可选择要查看的“数据源视图”\*\*\*\* 窗格区域。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-109">Click the lower right corner of the pane, between the scrollbars, to select an area of the **Data Source View** pane to view.</span></span>  
  
## <a name="diagram-context-menu"></a><span data-ttu-id="dcc0f-110">关系图上下文菜单</span><span class="sxs-lookup"><span data-stu-id="dcc0f-110">Diagram Context Menu</span></span>  
 <span data-ttu-id="dcc0f-111">右键单击“数据源视图”\*\*\*\* 窗格的关系图背景后显示的上下文菜单中包含下列选项：</span><span class="sxs-lookup"><span data-stu-id="dcc0f-111">The following options are available in the context menu displayed by right-clicking the diagram background of the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="dcc0f-112">**显示表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-112">**Show Tables**</span></span>  
 <span data-ttu-id="dcc0f-113">显示“显示表”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-113">Displays the **Show Table** dialog box.</span></span> <span data-ttu-id="dcc0f-114">有关“显示表”\*\*\*\* 对话框的详细信息，请参阅[“显示表”对话框（Analysis Services - 多维数据）](show-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-114">For more information about the **Show Table** dialog box, see [Show Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="dcc0f-115">**显示所有表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-115">**Show All Tables**</span></span>  
 <span data-ttu-id="dcc0f-116">在窗格中显示与多维数据集相关联的数据源视图中包含的所有表。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-116">Displays in the pane all tables included in the data source view associated with the cube.</span></span>  
  
 <span data-ttu-id="dcc0f-117">**仅显示已用表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-117">**Show Only Used Tables**</span></span>  
 <span data-ttu-id="dcc0f-118">在窗格中仅显示关联的数据源视图中多维数据集所使用的那些表。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-118">Displays in the pane only those tables used by the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="dcc0f-119">**显示友好名称**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-119">**Show Friendly Names**</span></span>  
 <span data-ttu-id="dcc0f-120">选择此选项可以显示窗格中对象的友好名称。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-120">Selects to show friendly names for the objects in the pane.</span></span>  
  
 <span data-ttu-id="dcc0f-121">**全选**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-121">**Select All**</span></span>  
 <span data-ttu-id="dcc0f-122">选择窗格中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-122">Selects all of the objects in the pane.</span></span>  
  
 <span data-ttu-id="dcc0f-123">**查找表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-123">**Find Table**</span></span>  
 <span data-ttu-id="dcc0f-124">显示“查找表”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-124">Displays the **Find Table** dialog box.</span></span> <span data-ttu-id="dcc0f-125">有关“查找表”\*\*\*\* 对话框的详细信息，请参阅[“查找表”对话框（Analysis Services - 多维数据）](find-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-125">For more information about the **Find Table** dialog box, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="dcc0f-126">**排列表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-126">**Arrange Tables**</span></span>  
 <span data-ttu-id="dcc0f-127">根据通过选择“切换到对角线布局”\*\*\*\* 或“切换到矩形布局”\*\*\*\* 指定的布局，排列窗格中的对象。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-127">Arranges the objects in the pane according to the layout specified by selecting either **Switch to Diagonal Layout** or **Switch to Rectangular Layout**.</span></span>  
  
 <span data-ttu-id="dcc0f-128">**切换到对角线布局**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-128">**Switch to Diagonal Layout**</span></span>  
 <span data-ttu-id="dcc0f-129">选择此项将按对角线模式排列对象。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-129">Select to arrange objects in a diagonal pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcc0f-130">只有在选择了“切换到矩形布局”\*\*\*\* 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-130">This option is displayed only if **Switch to Rectangular Layout** is selected.</span></span>  
  
 <span data-ttu-id="dcc0f-131">**切换到矩形布局**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-131">**Switch to Rectangular Layout**</span></span>  
 <span data-ttu-id="dcc0f-132">选择此项将按矩形模式排列对象。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-132">Select to arrange objects in a rectangular pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcc0f-133">只有在选择了“切换到对角线布局”\*\*\*\* 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-133">This option is displayed only if **Switch to Diagonal Layout** is selected.</span></span>  
  
 <span data-ttu-id="dcc0f-134">**编辑数据源视图**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-134">**Edit Data Source View**</span></span>  
 <span data-ttu-id="dcc0f-135">显示与对象关联的数据源视图的数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-135">Displays Data Source View Designer for the data source view associated with the object.</span></span> <span data-ttu-id="dcc0f-136">有关数据源视图设计器的详细信息，请参阅[数据源视图设计器（Analysis Services - 多维数据）](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-136">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="dcc0f-137">**数据源视图显示方式**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-137">**Show Data Source View In**</span></span>  
 <span data-ttu-id="dcc0f-138">通过选择下列选项之一，可以在“数据源视图”\*\*\*\* 窗格的以下查看模式之间切换：</span><span class="sxs-lookup"><span data-stu-id="dcc0f-138">Select one of the following options to toggle between viewing the **Data Source View** pane in the following modes:</span></span>  
  
-   <span data-ttu-id="dcc0f-139">图表</span><span class="sxs-lookup"><span data-stu-id="dcc0f-139">Diagram</span></span>  
  
     <span data-ttu-id="dcc0f-140">显示与当前多维数据集关联的表和列的关系图。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-140">Displays a diagram of the tables and columns associated with the current cube.</span></span>  
  
-   <span data-ttu-id="dcc0f-141">树</span><span class="sxs-lookup"><span data-stu-id="dcc0f-141">Tree</span></span>  
  
     <span data-ttu-id="dcc0f-142">显示包含与当前多维数据集关联的表和列的树视图。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-142">Displays a tree view containing the tables and columns associated with the current cube.</span></span>  
  
 <span data-ttu-id="dcc0f-143">**关系图复制源**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-143">**Copy Diagram From**</span></span>  
 <span data-ttu-id="dcc0f-144">选择与多维数据集关联的数据源视图所包含的一个关系图，可以在“数据源视图”\*\*\*\* 窗格中显示该关系图。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-144">Select one of the diagrams included in the data source view associated with the cube to display it in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="dcc0f-145">**缩放**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-145">**Zoom**</span></span>  
 <span data-ttu-id="dcc0f-146">选择可用的缩放选项。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-146">Select an available zoom option.</span></span>  
  
 <span data-ttu-id="dcc0f-147">**属性**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-147">**Properties**</span></span>  
 <span data-ttu-id="dcc0f-148">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，显示与多维数据集关联的数据源视图的“属性”\*\*\*\* 窗口。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-148">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the data source view associated with the cube.</span></span>  
  
## <a name="table-context-menu"></a><span data-ttu-id="dcc0f-149">表上下文菜单</span><span class="sxs-lookup"><span data-stu-id="dcc0f-149">Table Context Menu</span></span>  
 <span data-ttu-id="dcc0f-150">右键单击“数据源视图”\*\*\*\* 窗格中表或视图的名称后显示的上下文菜单中包含下列选项：</span><span class="sxs-lookup"><span data-stu-id="dcc0f-150">The following options are available in the context menu displayed by right-clicking the name of a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="dcc0f-151">**显示相关表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-151">**Show Related Tables**</span></span>  
 <span data-ttu-id="dcc0f-152">在窗格中显示与数据源视图中的所选表相关的表。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-152">Displays in the pane the tables related to the selected table in the data source view.</span></span>  
  
 <span data-ttu-id="dcc0f-153">**隐藏表**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-153">**Hide Table**</span></span>  
 <span data-ttu-id="dcc0f-154">从窗格中删除相应的表。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-154">Removes the table from the pane.</span></span>  
  
 <span data-ttu-id="dcc0f-155">**浏览数据**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-155">**Explore Data**</span></span>  
 <span data-ttu-id="dcc0f-156">显示所选表的“浏览数据”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-156">Display the **Explore Data** dialog box for the selected table.</span></span>  
  
 <span data-ttu-id="dcc0f-157">**编辑数据源视图**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-157">**Edit Data Source View**</span></span>  
 <span data-ttu-id="dcc0f-158">显示包含所选表的数据源视图的数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-158">Displays Data Source View Designer for the data source view that contains the selected table.</span></span> <span data-ttu-id="dcc0f-159">有关数据源视图设计器的详细信息，请参阅[数据源视图设计器（Analysis Services - 多维数据）](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-159">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="dcc0f-160">**从表新建度量值组**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-160">**New Measure Group from Table**</span></span>  
 <span data-ttu-id="dcc0f-161">基于所选表在“度量值”\*\*\*\* 窗格中定义新的度量值组。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-161">Defines a new measure group in the **Measures** pane based on the selected table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcc0f-162">只有当“度量值”\*\*\*\* 窗格中的度量值组尚未引用该表时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-162">This option is enabled only if the table is not yet referenced by a measure group in the **Measures** pane.</span></span>  
  
 <span data-ttu-id="dcc0f-163">**属性**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-163">**Properties**</span></span>  
 <span data-ttu-id="dcc0f-164">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中显示所选表的“属性”\*\*\*\* 窗口。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-164">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected table.</span></span>  
  
## <a name="column-context-menu"></a><span data-ttu-id="dcc0f-165">列上下文菜单</span><span class="sxs-lookup"><span data-stu-id="dcc0f-165">Column Context Menu</span></span>  
 <span data-ttu-id="dcc0f-166">右键单击“数据源视图”\*\*\*\* 窗格内表或视图中的列名称后显示的上下文菜单中包含下列选项：</span><span class="sxs-lookup"><span data-stu-id="dcc0f-166">The following options are available in the context menu displayed by right-clicking the name of a column in a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="dcc0f-167">**从列新建度量值**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-167">**New Measure from Column**</span></span>  
 <span data-ttu-id="dcc0f-168">基于所选列在“度量值”\*\*\*\* 窗格中定义新的度量值。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-168">Defines a new measure in the **Measures** pane based on the selected column.</span></span>  
  
 <span data-ttu-id="dcc0f-169">**浏览数据**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-169">**Explore Data**</span></span>  
 <span data-ttu-id="dcc0f-170">显示包含所选列的表的“浏览数据”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-170">Display the **Explore Data** dialog box for the table that contains the selected column.</span></span>  
  
 <span data-ttu-id="dcc0f-171">**编辑数据源视图**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-171">**Edit Data Source View**</span></span>  
 <span data-ttu-id="dcc0f-172">显示包含所选列的数据源视图的数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-172">Displays Data Source View Designer for the data source view that contains the selected column.</span></span> <span data-ttu-id="dcc0f-173">有关数据源视图设计器的详细信息，请参阅[数据源视图设计器（Analysis Services - 多维数据）](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-173">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="dcc0f-174">**属性**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-174">**Properties**</span></span>  
 <span data-ttu-id="dcc0f-175">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中显示所选列的“属性”\*\*\*\* 窗口。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-175">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected column.</span></span>  
  
## <a name="relationship-context-menu"></a><span data-ttu-id="dcc0f-176">关系上下文菜单</span><span class="sxs-lookup"><span data-stu-id="dcc0f-176">Relationship Context Menu</span></span>  
 <span data-ttu-id="dcc0f-177">右键单击“数据源视图”\*\*\*\* 窗格中的关系后显示的上下文菜单中包含下列选项：</span><span class="sxs-lookup"><span data-stu-id="dcc0f-177">The following options are available in the context menu displayed by right-clicking a relationship in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="dcc0f-178">**编辑数据源视图**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-178">**Edit Data Source View**</span></span>  
 <span data-ttu-id="dcc0f-179">显示包含所选关系的数据源视图的数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-179">Displays Data Source View Designer for the data source view that contains the selected relationship.</span></span> <span data-ttu-id="dcc0f-180">有关数据源视图设计器的详细信息，请参阅[数据源视图设计器（Analysis Services - 多维数据）](data-source-view-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-180">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="dcc0f-181">**属性**</span><span class="sxs-lookup"><span data-stu-id="dcc0f-181">**Properties**</span></span>  
 <span data-ttu-id="dcc0f-182">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中显示所选关系的“属性”\*\*\*\* 窗口。</span><span class="sxs-lookup"><span data-stu-id="dcc0f-182">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc0f-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcc0f-183">See Also</span></span>  
 <span data-ttu-id="dcc0f-184">["多维数据集结构" 选项卡、多维数据集设计器&#41; &#40;的工具栏 &#40;Analysis Services 多维数据&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dcc0f-184">[Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dcc0f-185">[度量值 &#40;"多维数据集结构" 选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dcc0f-185">[Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dcc0f-186">[维度 &#40;多维数据集结构选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dcc0f-186">[Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="dcc0f-187">多维数据集设计器的多维数据集结构 &#40;&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="dcc0f-187">Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-structure-cube-designer-analysis-services-multidimensional-data.md)  
  
  
