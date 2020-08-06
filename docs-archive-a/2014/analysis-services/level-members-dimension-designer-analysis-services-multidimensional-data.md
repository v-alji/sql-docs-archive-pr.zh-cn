---
title: 级别和成员 (浏览器选项卡，维度设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21680f00b82b5410e2c7a67122fdcfeb78c999dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694630"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="e78be-102">级别和成员（“浏览器”选项卡，维度设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="e78be-102">Level and Members (Browser Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e78be-103">可以使用此窗格浏览当前选择的层次结构和语言的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-103">Use this pane to browse the members of the currently selected hierarchy and language.</span></span> <span data-ttu-id="e78be-104">若要选择要浏览的层次结构或语言，请使用 **“工具栏”** 窗格上的 **“层次结构”** 和 **“语言”** 选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-104">To select a hierarchy or language to browse, use the **Hierarchy** and **Language** options on the **Toolbar** pane.</span></span> <span data-ttu-id="e78be-105">有关工具栏窗格的详细信息，请参阅[toolbar &#40;浏览器选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e78be-105">For more information about the Toolbar pane, see [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="writeback-mode"></a><span data-ttu-id="e78be-106">写回模式</span><span class="sxs-lookup"><span data-stu-id="e78be-106">Writeback Mode</span></span>  
 <span data-ttu-id="e78be-107">如果启用了写回模式，此窗格的功能将会更改。</span><span class="sxs-lookup"><span data-stu-id="e78be-107">The functionality of this pane changes if writeback mode is enabled.</span></span> <span data-ttu-id="e78be-108">所选的维度必须启用写操作（即维度的 `WriteEnabled` 属性必须设置为 True），并且维度必须部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例，以便启用写回模式。</span><span class="sxs-lookup"><span data-stu-id="e78be-108">The selected dimension must be write-enabled (in other words, the `WriteEnabled` property of the dimension must be set to true) and the dimension must be deployed to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in order to enable writeback mode.</span></span>  
  
 <span data-ttu-id="e78be-109">若要启用写回模式，可以从“工具栏”\*\*\*\* 窗格中选择“写回”\*\*\*\*，或者右键单击“级别和成员”\*\*\*\* 窗格，从上下文菜单中选择“写回”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e78be-109">To enable writeback mode, you can either select **Writeback** from the **Toolbar** pane, or right-click the **Level and Members** pane and select **Writeback** from the context menu.</span></span>  
  
 <span data-ttu-id="e78be-110">如果启用了写回模式，您可以在 **“级别和成员”** 窗格中执行以下其他操作：</span><span class="sxs-lookup"><span data-stu-id="e78be-110">If writeback mode is enabled, you can perform the following additional actions in the **Level and Members** pane:</span></span>  
  
|<span data-ttu-id="e78be-111">所需操作</span><span class="sxs-lookup"><span data-stu-id="e78be-111">To do</span></span>|<span data-ttu-id="e78be-112">执行</span><span class="sxs-lookup"><span data-stu-id="e78be-112">Perform</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="e78be-113">在所选的层次结构中创建同级成员和子成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-113">Create sibling and child members within the selected hierarchy.</span></span>|<span data-ttu-id="e78be-114">右键单击所选的成员，从上下文菜单中选择“创建同级”\*\*\*\* 可以创建同级成员，或选择“创建子级”\*\*\*\* 可以创建子成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-114">Right-click the selected member and select either **Create Sibling**, to create a sibling member, or **Create Child**, to create a child member, from the context menu.</span></span>|  
|<span data-ttu-id="e78be-115">在层次结构中上下移动所选成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-115">Move a selected member up or down the hierarchy.</span></span>|<span data-ttu-id="e78be-116">将所选的成员拖动到适合的父成员或子成员中，或者单击 **“工具栏”** 窗格上的 **“增加缩进”** 或 **“减少缩进”** ，上下移动所选成员的层次结构级别。</span><span class="sxs-lookup"><span data-stu-id="e78be-116">Either drag the selected member to the appropriate parent or child member, or click **Increase Indent** or **Decrease Indent** on the **Toolbar** pane to move the selected member up or down the levels of the hierarchy.</span></span>|  
|<span data-ttu-id="e78be-117">重命名所选的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-117">Rename a selected member.</span></span>|<span data-ttu-id="e78be-118">右键单击所选的成员，选择“重命名”\*\*\*\*，或单击已经选择的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-118">Either right-click the selected member and select **Rename**, or click an already-selected member.</span></span>|  
|<span data-ttu-id="e78be-119">编辑成员的属性值。</span><span class="sxs-lookup"><span data-stu-id="e78be-119">Edit member property values</span></span>|<span data-ttu-id="e78be-120">双击所选成员的所选成员属性的值，并编辑此值。</span><span class="sxs-lookup"><span data-stu-id="e78be-120">Double-click the value in the selected member property for the selected member to edit the value.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="e78be-121">选项</span><span class="sxs-lookup"><span data-stu-id="e78be-121">Options</span></span>  
 <span data-ttu-id="e78be-122">**当前级别**</span><span class="sxs-lookup"><span data-stu-id="e78be-122">**Current level**</span></span>  
 <span data-ttu-id="e78be-123">显示当前在“树”\*\*\*\* 中所选成员所属的级别。</span><span class="sxs-lookup"><span data-stu-id="e78be-123">Displays the level to which the currently selected member in **Tree** belongs.</span></span>  
  
 <span data-ttu-id="e78be-124">**视图**</span><span class="sxs-lookup"><span data-stu-id="e78be-124">**Tree**</span></span>  
 <span data-ttu-id="e78be-125">显示当前所选的层次结构和语言的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-125">Displays the members of the currently selected hierarchy and language.</span></span>  
  
 <span data-ttu-id="e78be-126">如果在工具栏窗格的 **“成员属性”** 选项中选择了成员属性，那么每个成员的属性将显示为一列。</span><span class="sxs-lookup"><span data-stu-id="e78be-126">If member properties are selected from the **Member Properties** option of the Toolbar pane, each member property is displayed as a column.</span></span>  
  
 <span data-ttu-id="e78be-127">如果启用了写回模式，则对于与维度中键属性相关联的每个键列，都将显示一列。</span><span class="sxs-lookup"><span data-stu-id="e78be-127">If writeback mode is enabled, one column for each key column associated with the key attribute in the dimension is displayed.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="e78be-128">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="e78be-128">Context Menu</span></span>  
 <span data-ttu-id="e78be-129">右键单击所选成员的“级别和成员”\*\*\*\* 窗格中的任意部分后，你可以从显示的上下文菜单中选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="e78be-129">The following options are available in the context menu displayed by right-clicking any part of the **Level and Members** pane for the selected member:</span></span>  
  
 <span data-ttu-id="e78be-130">**创建同级**</span><span class="sxs-lookup"><span data-stu-id="e78be-130">**Create sibling**</span></span>  
 <span data-ttu-id="e78be-131">在所选成员的同一级别上创建新的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-131">Creates a new member at the same level as the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-132">只有所选的成员不是处于“（全部）”级别的成员时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-132">This option is enabled only if a member at a level other than the (All) level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-133">只有启用了写回模式，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-133">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="e78be-134">**创建子级**</span><span class="sxs-lookup"><span data-stu-id="e78be-134">**Create child**</span></span>  
 <span data-ttu-id="e78be-135">在所选成员的下一级别创建新的成员，作为所选成员的子成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-135">Creates a new member at the next lower level as the selected member, as a child of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-136">只有选择了非最低级别的成员，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-136">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-137">只有启用了写回模式，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-137">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="e78be-138">**剪切**</span><span class="sxs-lookup"><span data-stu-id="e78be-138">**Cut**</span></span>  
 <span data-ttu-id="e78be-139">将所选成员复制到剪贴板，并且从层次结构中删除所选成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-139">Copies the selected members to the clipboard and removes them from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-140">只有所选的成员不是处于“全部”级别的成员时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-140">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-141">只有启用了写回模式，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-141">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="e78be-142">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="e78be-142">**Paste**</span></span>  
 <span data-ttu-id="e78be-143">将之前使用“剪切”\*\*\*\* 删除的成员粘贴到所选成员后紧邻的位置。</span><span class="sxs-lookup"><span data-stu-id="e78be-143">Pastes members previously removed using **Cut** immediately after the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-144">只有启用了写回模式，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-144">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="e78be-145">**删除**</span><span class="sxs-lookup"><span data-stu-id="e78be-145">**Delete**</span></span>  
 <span data-ttu-id="e78be-146">从层次结构中删除所选的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-146">Removes the selected members from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-147">只有所选的成员不是处于“全部”级别的成员时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-147">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-148">只有启用了写回模式，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-148">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="e78be-149">**重命名**</span><span class="sxs-lookup"><span data-stu-id="e78be-149">**Rename**</span></span>  
 <span data-ttu-id="e78be-150">选择此项可以编辑所选成员的名称。</span><span class="sxs-lookup"><span data-stu-id="e78be-150">Select to edit the name of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-151">只有所选的成员不是处于“全部”级别的成员时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-151">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-152">只有启用了写回模式，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-152">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="e78be-153">**筛选成员**</span><span class="sxs-lookup"><span data-stu-id="e78be-153">**Filter Members**</span></span>  
 <span data-ttu-id="e78be-154">显示“筛选成员”\*\*\*\* 对话框，以便筛选所选层次结构的“级别和成员”\*\*\*\* 中所显示的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-154">Displays the **Filter Members** dialog box to filter members displayed in **Level and Members** for the selected hierarchy.</span></span> <span data-ttu-id="e78be-155">有关“筛选成员”\*\*\*\* 对话框的详细信息，请参阅[“筛选成员”对话框（Analysis Services - 多维数据）](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e78be-155">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="e78be-156">**全部展开**</span><span class="sxs-lookup"><span data-stu-id="e78be-156">**Expand All**</span></span>  
 <span data-ttu-id="e78be-157">展开“树”\*\*\*\* 中的所有成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-157">Expands all members in **Tree**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78be-158">只有选择了非最低级别的成员，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e78be-158">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
 <span data-ttu-id="e78be-159">**全部折叠**</span><span class="sxs-lookup"><span data-stu-id="e78be-159">**Collapse All**</span></span>  
 <span data-ttu-id="e78be-160">折叠“树”\*\*\*\* 中的所有成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-160">Collapse all members in **Tree**.</span></span>  
  
 <span data-ttu-id="e78be-161">**展开成员**</span><span class="sxs-lookup"><span data-stu-id="e78be-161">**Expand Member**</span></span>  
 <span data-ttu-id="e78be-162">展开“树”\*\*\*\* 中所选的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-162">Expand the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="e78be-163">**折叠成员**</span><span class="sxs-lookup"><span data-stu-id="e78be-163">**Collapse Member**</span></span>  
 <span data-ttu-id="e78be-164">折叠“树”\*\*\*\* 中所选的成员。</span><span class="sxs-lookup"><span data-stu-id="e78be-164">Collapse the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="e78be-165">**写回**</span><span class="sxs-lookup"><span data-stu-id="e78be-165">**Writeback**</span></span>  
 <span data-ttu-id="e78be-166">选择此项将启用写回模式。</span><span class="sxs-lookup"><span data-stu-id="e78be-166">Select to enable writeback mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78be-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e78be-167">See Also</span></span>  
 <span data-ttu-id="e78be-168">[工具栏 &#40;浏览器选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e78be-168">[Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e78be-169">&#41; &#40;Analysis Services 多维&#41;数据的浏览器 &#40;维度设计器</span><span class="sxs-lookup"><span data-stu-id="e78be-169">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
