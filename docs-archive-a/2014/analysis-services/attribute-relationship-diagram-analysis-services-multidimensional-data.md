---
title: 属性关系图 (属性关系设计器选项卡，维度设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.ardiagram.f1
ms.assetid: 320989ad-bd95-43f4-a2e7-b262d66dbda7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 49be94564a52a6347c35f28f9a1dd659980fd46c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579359"
---
# <a name="attribute-relationship-diagram-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="cba95-102">属性关系图（“属性关系”设计器选项卡，维度设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="cba95-102">Attribute Relationship Diagram (Attribute Relationship Designer Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="cba95-103">可以使用 **“属性关系”** 选项卡上的工具栏紧下方的窗格查看属性关系图，以及创建、修改和删除属性关系。</span><span class="sxs-lookup"><span data-stu-id="cba95-103">Use the pane immediately under the toolbar on the **Attribute Relationships** tab to view the attribute relationship diagram, and to create, modify, and delete attribute relationships.</span></span>  
  
 <span data-ttu-id="cba95-104">**查看包含属性关系图的窗格**</span><span class="sxs-lookup"><span data-stu-id="cba95-104">**To view the pane that contains the attribute relationship diagram**</span></span>  
  
-   <span data-ttu-id="cba95-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的解决方案资源管理器中，双击维度以打开维度设计器，然后单击“属性关系”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cba95-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
## <a name="using-the-attribute-relationship-diagram"></a><span data-ttu-id="cba95-106">使用属性关系图</span><span class="sxs-lookup"><span data-stu-id="cba95-106">Using the Attribute Relationship Diagram</span></span>  
 <span data-ttu-id="cba95-107">使用属性关系图可以创建、编辑或删除属性关系。</span><span class="sxs-lookup"><span data-stu-id="cba95-107">Use the attribute relationship diagram to create, edit or delete attribute relationships.</span></span> <span data-ttu-id="cba95-108">属性关系图还将突出显示有问题的属性关系并在工具提示中显示该问题的说明。</span><span class="sxs-lookup"><span data-stu-id="cba95-108">The attribute relationship diagram will also highlight problematic attribute relationships and display a description of the issue in a tooltip.</span></span>  
  
 <span data-ttu-id="cba95-109">关系图中有三个独立的快捷菜单：关系图快捷菜单、属性快捷菜单和关系快捷菜单。</span><span class="sxs-lookup"><span data-stu-id="cba95-109">There are three separate shortcut menus available in the diagram: the diagram shortcut menu, the attribute shortcut menu, and the relationship shortcut menu.</span></span>  
  
### <a name="diagram-shortcut-menu"></a><span data-ttu-id="cba95-110">关系图快捷菜单</span><span class="sxs-lookup"><span data-stu-id="cba95-110">Diagram Shortcut Menu</span></span>  
 <span data-ttu-id="cba95-111">若要打开属性关系图的快捷菜单，请右键单击关系图的背景。</span><span class="sxs-lookup"><span data-stu-id="cba95-111">To open the shortcut menu for the attribute relationship diagram, right-click the background of the diagram.</span></span> <span data-ttu-id="cba95-112">关系图快捷菜单包含以下命令：</span><span class="sxs-lookup"><span data-stu-id="cba95-112">The diagram shortcut menu has the following commands:</span></span>  
  
 <span data-ttu-id="cba95-113">**新建属性关系**</span><span class="sxs-lookup"><span data-stu-id="cba95-113">**New Attribute Relationship**</span></span>  
 <span data-ttu-id="cba95-114">打开“创建属性关系”\*\*\*\* 对话框，可以在其中定义新的属性关系。</span><span class="sxs-lookup"><span data-stu-id="cba95-114">Opens the **Create Attribute Relationship** dialog box in which you can define a new attribute relationship.</span></span>  
  
 <span data-ttu-id="cba95-115">有关详细信息，请参阅[“创建属性关系”和“编辑属性关系”对话框（“属性关系设计器”选项卡，维度设计器）（Analysis Services - 多维数据）](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md)和[定义属性关系](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="cba95-115">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="cba95-116">**排列形状**</span><span class="sxs-lookup"><span data-stu-id="cba95-116">**Arrange Shapes**</span></span>  
 <span data-ttu-id="cba95-117">根据维度设计器使用的布局算法排列形状。</span><span class="sxs-lookup"><span data-stu-id="cba95-117">Arranges the shapes according to the layout algorithm that Dimension Designer uses.</span></span>  
  
 <span data-ttu-id="cba95-118">**自动排列形状**</span><span class="sxs-lookup"><span data-stu-id="cba95-118">**Auto Arrange Shapes**</span></span>  
 <span data-ttu-id="cba95-119">根据维度设计器使用的布局算法，自动排列关系图中的形状。</span><span class="sxs-lookup"><span data-stu-id="cba95-119">Automatically arranges the shapes in the diagram according to the layout algorithm that Dimension Designer uses.</span></span> <span data-ttu-id="cba95-120">默认情况下，启用 **“自动排列形状”** 。</span><span class="sxs-lookup"><span data-stu-id="cba95-120">By default, **Auto Arrange Shapes** is enabled.</span></span>  
  
 <span data-ttu-id="cba95-121">**显示列表视图**</span><span class="sxs-lookup"><span data-stu-id="cba95-121">**Show List Views**</span></span>  
 <span data-ttu-id="cba95-122">显示或隐藏“属性”\*\*\*\* 和“属性关系”\*\*\*\* 列表。</span><span class="sxs-lookup"><span data-stu-id="cba95-122">Displays or hides the **Attributes** and **Attribute Relationships** lists.</span></span> <span data-ttu-id="cba95-123">这些列表立即出现在包含属性关系图的窗格下的自己的窗格中。</span><span class="sxs-lookup"><span data-stu-id="cba95-123">These lists appear in their own panes immediately under the pane that contains the attribute relationship diagram.</span></span>  
  
 <span data-ttu-id="cba95-124">**展开所有形状**</span><span class="sxs-lookup"><span data-stu-id="cba95-124">**Expand All Shapes**</span></span>  
 <span data-ttu-id="cba95-125">显示与顶级属性相关联的分组属性。</span><span class="sxs-lookup"><span data-stu-id="cba95-125">Displays the grouped attributes that are associated with the top-level attributes.</span></span> <span data-ttu-id="cba95-126">分组属性仅在展开属性关系图中的形状时可见。</span><span class="sxs-lookup"><span data-stu-id="cba95-126">Grouped attributes are only visible when the shapes in the attribute relationship diagram are expanded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cba95-127">如果单击此属性，维度设计器会将属性关系图中的形状返回到该设计器使用的默认布局中。</span><span class="sxs-lookup"><span data-stu-id="cba95-127">If you click this option, the Dimension Designer will return the shapes in the attribute relationship diagram back to the default layout that the designer uses.</span></span>  
  
 <span data-ttu-id="cba95-128">**折叠所有形状**</span><span class="sxs-lookup"><span data-stu-id="cba95-128">**Collapse All Shapes**</span></span>  
 <span data-ttu-id="cba95-129">隐藏与顶级属性相关联的分组属性。</span><span class="sxs-lookup"><span data-stu-id="cba95-129">Hides the grouped attributes that are associated with the top-level attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cba95-130">如果单击此属性，维度设计器会将属性关系图中的形状返回到该设计器使用的默认布局中。</span><span class="sxs-lookup"><span data-stu-id="cba95-130">If you click this option, the Dimension Designer will return the shapes in the attribute relationship diagram back to the default layout that the designer uses.</span></span>  
  
 <span data-ttu-id="cba95-131">**缩放**</span><span class="sxs-lookup"><span data-stu-id="cba95-131">**Zoom**</span></span>  
 <span data-ttu-id="cba95-132">显示可用的缩放选项列表。</span><span class="sxs-lookup"><span data-stu-id="cba95-132">Displays a list of available zoom options.</span></span>  
  
### <a name="attribute-shortcut-menu"></a><span data-ttu-id="cba95-133">属性快捷菜单</span><span class="sxs-lookup"><span data-stu-id="cba95-133">Attribute Shortcut Menu</span></span>  
 <span data-ttu-id="cba95-134">若要打开属性快捷菜单，请右键单击属性关系图中的属性。</span><span class="sxs-lookup"><span data-stu-id="cba95-134">To open the attribute shortcut menu, right-click an attribute in the attribute relationship diagram.</span></span> <span data-ttu-id="cba95-135">属性快捷菜单包含以下命令：</span><span class="sxs-lookup"><span data-stu-id="cba95-135">The attribute shortcut menu has the following commands:</span></span>  
  
 <span data-ttu-id="cba95-136">**新建属性关系**</span><span class="sxs-lookup"><span data-stu-id="cba95-136">**New Attribute Relationship**</span></span>  
 <span data-ttu-id="cba95-137">打开“创建属性关系”\*\*\*\* 对话框，可以在其中定义新的属性关系。</span><span class="sxs-lookup"><span data-stu-id="cba95-137">Opens the **Create Attribute Relationship** dialog box in which you can define a new attribute relationship.</span></span>  
  
 <span data-ttu-id="cba95-138">有关详细信息，请参阅[“创建属性关系”和“编辑属性关系”对话框（“属性关系设计器”选项卡，维度设计器）（Analysis Services - 多维数据）](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md)和[定义属性关系](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="cba95-138">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="cba95-139">**属性**</span><span class="sxs-lookup"><span data-stu-id="cba95-139">**Properties**</span></span>  
 <span data-ttu-id="cba95-140">在“属性”\*\*\*\* 窗口中显示特性的属性。</span><span class="sxs-lookup"><span data-stu-id="cba95-140">Displays the attribute's properties in the **Properties** window.</span></span>  
  
### <a name="relationship-shortcut-menu"></a><span data-ttu-id="cba95-141">关系快捷菜单</span><span class="sxs-lookup"><span data-stu-id="cba95-141">Relationship Shortcut Menu</span></span>  
 <span data-ttu-id="cba95-142">若要打开关系快捷菜单，请右键单击标识两个属性之间关系的箭头。</span><span class="sxs-lookup"><span data-stu-id="cba95-142">To open the relationship shortcut menu, right-click the arrow that identifies the relationship between two attributes.</span></span> <span data-ttu-id="cba95-143">关系快捷菜单包含以下命令：</span><span class="sxs-lookup"><span data-stu-id="cba95-143">The relationship shortcut menu has the following commands:</span></span>  
  
 <span data-ttu-id="cba95-144">**编辑属性关系**</span><span class="sxs-lookup"><span data-stu-id="cba95-144">**Edit Attribute Relationship**</span></span>  
 <span data-ttu-id="cba95-145">打开“编辑属性关系”\*\*\*\* 对话框，可以在其中修改属性关系。</span><span class="sxs-lookup"><span data-stu-id="cba95-145">Opens the **Edit Attribute Relationship** dialog box in which you can modify the attribute relationship.</span></span>  
  
 <span data-ttu-id="cba95-146">有关详细信息，请参阅[“创建属性关系”和“编辑属性关系”对话框（“属性关系设计器”选项卡，维度设计器）（Analysis Services - 多维数据）](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md)和[定义属性关系](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="cba95-146">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="cba95-147">**关系类型**</span><span class="sxs-lookup"><span data-stu-id="cba95-147">**Relationship Type**</span></span>  
 <span data-ttu-id="cba95-148">将关系类型设置为“柔性”\*\*\*\* 或“刚性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cba95-148">Sets the relationship type to either **Flexible** or **Rigid**.</span></span> <span data-ttu-id="cba95-149">在柔性关系中，成员之间的关系会随时间而变化。</span><span class="sxs-lookup"><span data-stu-id="cba95-149">In a flexible relationship, relationships between members change over time.</span></span> <span data-ttu-id="cba95-150">在刚性关系中，成员之间的关系不随时间而变化。</span><span class="sxs-lookup"><span data-stu-id="cba95-150">In a rigid relationship, relationships between members do not change over time.</span></span>  
  
 <span data-ttu-id="cba95-151">**删除**</span><span class="sxs-lookup"><span data-stu-id="cba95-151">**Delete**</span></span>  
 <span data-ttu-id="cba95-152">删除属性关系。</span><span class="sxs-lookup"><span data-stu-id="cba95-152">Deletes the attribute relationship.</span></span>  
  
 <span data-ttu-id="cba95-153">**属性**</span><span class="sxs-lookup"><span data-stu-id="cba95-153">**Properties**</span></span>  
 <span data-ttu-id="cba95-154">在“属性”\*\*\*\* 窗口中显示关系的属性。</span><span class="sxs-lookup"><span data-stu-id="cba95-154">Displays the relationship's properties in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba95-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cba95-155">See Also</span></span>  
 <span data-ttu-id="cba95-156">[&#41; &#40;Analysis Services 多维数据 &#40;维度设计器的属性关系&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cba95-156">[Attribute Relationships &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="cba95-157">[工具栏 &#40;属性关系设计器选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cba95-157">[Toolbar &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="cba95-158">[属性 &#40;属性关系设计器选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cba95-158">[Attributes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="cba95-159">属性关系 &#40;属性关系设计器选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="cba95-159">Attribute Relationships &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](attribute-relationships-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
