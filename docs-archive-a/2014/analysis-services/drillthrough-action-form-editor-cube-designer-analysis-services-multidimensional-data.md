---
title: 钻取操作窗体编辑器 (操作 "选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.drillthroughaction.f1
ms.assetid: 225fd818-b5ea-494f-b67b-66e09798274a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 546448bd05f3af45b7093acb2dbb9d1e1a8f1bd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589944"
---
# <a name="drillthrough-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="fe342-102">钻取操作窗体编辑器（“操作”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fe342-102">Drillthrough Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fe342-103">可以使用多维数据集设计器中的 **“操作”** 选项卡上的 **“钻取操作窗体编辑器”** 窗格，修改在 **“操作组织程序”** 窗格中选择的钻取操作。</span><span class="sxs-lookup"><span data-stu-id="fe342-103">Use the **Drillthrough Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the drillthrough action selected in the **Action Organizer** pane.</span></span> <span data-ttu-id="fe342-104">有关钻取操作的详细信息，请参阅[操作（Analysis Services - 多维数据）](multidimensional-models/actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fe342-104">For more information about drillthrough actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe342-105">钻取操作不再深化到基础数据存储区。</span><span class="sxs-lookup"><span data-stu-id="fe342-105">Drillthrough actions no longer drill down to the underlying data store.</span></span> <span data-ttu-id="fe342-106">必须使用维度或层次结构成员在多维数据集中对钻取操作访问的信息进行建模。</span><span class="sxs-lookup"><span data-stu-id="fe342-106">The information that drillthrough actions access must be modeled within the cube by using dimension or hierarchy members.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe342-107">选项</span><span class="sxs-lookup"><span data-stu-id="fe342-107">Options</span></span>  
 <span data-ttu-id="fe342-108">name</span><span class="sxs-lookup"><span data-stu-id="fe342-108">**name**</span></span>  
 <span data-ttu-id="fe342-109">键入操作的名称。</span><span class="sxs-lookup"><span data-stu-id="fe342-109">Type the name of the action.</span></span>  
  
 <span data-ttu-id="fe342-110">**操作目标**</span><span class="sxs-lookup"><span data-stu-id="fe342-110">**Action Target**</span></span>  
 <span data-ttu-id="fe342-111">展开可查看“度量值组成员”选项。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe342-111">Expand to view the **Measure group members** option.</span></span>  
  
 <span data-ttu-id="fe342-112">**度量值组成员**</span><span class="sxs-lookup"><span data-stu-id="fe342-112">**Measure group members**</span></span>  
 <span data-ttu-id="fe342-113">选择要与钻取操作关联的度量值组。</span><span class="sxs-lookup"><span data-stu-id="fe342-113">Select the measure group to which the drillthrough action is to be associated.</span></span>  
  
 <span data-ttu-id="fe342-114">**条件(可选)**</span><span class="sxs-lookup"><span data-stu-id="fe342-114">**Condition (Optional)**</span></span>  
 <span data-ttu-id="fe342-115">输入描述可选条件（与“度量值组成员”一起使用）的多维表达式 (MDX) 表达式，以进一步限制操作可用的时间。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe342-115">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Measure group members**, which further restricts when the action is available.</span></span> <span data-ttu-id="fe342-116">表达式必须返回一个布尔值，如果为 True，指示该操作可用。</span><span class="sxs-lookup"><span data-stu-id="fe342-116">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="fe342-117">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fe342-117">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fe342-118">**钻取列**</span><span class="sxs-lookup"><span data-stu-id="fe342-118">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="fe342-119">展开可显示一个网格，指示在用户运行此操作时返回的属性。</span><span class="sxs-lookup"><span data-stu-id="fe342-119">Expand to display a grid in which to indicate the attributes that are returned when the user runs this action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe342-120">您可以选择多个维度，但在钻取操作中每个维度只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="fe342-120">You can select more than one dimension, but no dimension can be used more than once in a drillthrough action.</span></span>  
  
 <span data-ttu-id="fe342-121">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="fe342-121">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="fe342-122">列</span><span class="sxs-lookup"><span data-stu-id="fe342-122">Column</span></span>|<span data-ttu-id="fe342-123">说明</span><span class="sxs-lookup"><span data-stu-id="fe342-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fe342-124">**Dimensions**</span><span class="sxs-lookup"><span data-stu-id="fe342-124">**Dimensions**</span></span>|<span data-ttu-id="fe342-125">选择派生所返回属性的维度。</span><span class="sxs-lookup"><span data-stu-id="fe342-125">Select the dimension from which the returned attribute is derived.</span></span> <span data-ttu-id="fe342-126">选择 MEASURES 可以钻取度量值。</span><span class="sxs-lookup"><span data-stu-id="fe342-126">Select MEASURES to drillthrough on measures.</span></span>|  
|<span data-ttu-id="fe342-127">**返回列**</span><span class="sxs-lookup"><span data-stu-id="fe342-127">**Return Columns**</span></span>|<span data-ttu-id="fe342-128">从所选维度中选择将在操作运行时返回的属性或度量值。</span><span class="sxs-lookup"><span data-stu-id="fe342-128">Select the attribute or measure from the selected dimension to be returned when the action is run.</span></span>|  
  
 <span data-ttu-id="fe342-129">**其他属性**</span><span class="sxs-lookup"><span data-stu-id="fe342-129">**Additional Properties**</span></span>  
 <span data-ttu-id="fe342-130">展开可查看“默认值”、“最大行数”、“调用”、“应用程序”、“说明”、“标题”和“标题是 MDX”选项。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe342-130">Expand to view the **Default**, **Maximum rows**, **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="fe342-131">**Default**</span><span class="sxs-lookup"><span data-stu-id="fe342-131">**Default**</span></span>  
 <span data-ttu-id="fe342-132">若要将此钻取操作设置为默认的钻取操作，请选择 **True** ，否则选择 **False**。</span><span class="sxs-lookup"><span data-stu-id="fe342-132">Select **True** to include this drillthrough action as a default drillthrough action, otherwise, select **False**.</span></span>  
  
 <span data-ttu-id="fe342-133">如果 `RETURN` 从 `DRILLTHROUGH` 客户端应用程序所执行的 MDX 语句中省略子句，则 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例将评估所有默认钻取操作并运行返回非空集的第一个默认钻取操作。</span><span class="sxs-lookup"><span data-stu-id="fe342-133">If the `RETURN` clause is omitted from an MDX `DRILLTHROUGH` statement executed by a client application, the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance evaluates all default drillthrough actions and runs the first default drillthrough action that returns a non-empty set.</span></span> <span data-ttu-id="fe342-134">有关 MDX 语句的详细信息 `DRILLTHROUGH` ，请参阅[钻取语句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-drillthrough)。</span><span class="sxs-lookup"><span data-stu-id="fe342-134">For more information about the MDX `DRILLTHROUGH` statement, see [DRILLTHROUGH Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-drillthrough).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe342-135">使用此选项只是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="fe342-135">This option is used for backwards compatibility purposes.</span></span>  
  
 <span data-ttu-id="fe342-136">**最大行数**</span><span class="sxs-lookup"><span data-stu-id="fe342-136">**Maximum rows**</span></span>  
 <span data-ttu-id="fe342-137">键入钻取操作返回的最大行数。</span><span class="sxs-lookup"><span data-stu-id="fe342-137">Type the maximum number of rows to be returned by the drillthrough action.</span></span> <span data-ttu-id="fe342-138">将此选项设置为零或空值表示钻取操作将向客户端应用程序返回该操作检索到的所有行。</span><span class="sxs-lookup"><span data-stu-id="fe342-138">Setting this option to zero or an empty value indicates that the drillthrough action returns all rows retrieved by the action to the client application.</span></span>  
  
 <span data-ttu-id="fe342-139">**调用**</span><span class="sxs-lookup"><span data-stu-id="fe342-139">**Invocation**</span></span>  
 <span data-ttu-id="fe342-140">选择相应设置，指示何时执行该操作。</span><span class="sxs-lookup"><span data-stu-id="fe342-140">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe342-141">此选项只是向客户端应用程序提供何时执行某项操作的建议，并不直接控制对该操作的调用。</span><span class="sxs-lookup"><span data-stu-id="fe342-141">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="fe342-142">下表对可用的设置进行了说明：</span><span class="sxs-lookup"><span data-stu-id="fe342-142">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="fe342-143">值</span><span class="sxs-lookup"><span data-stu-id="fe342-143">Value</span></span>|<span data-ttu-id="fe342-144">说明</span><span class="sxs-lookup"><span data-stu-id="fe342-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe342-145">Batch</span><span class="sxs-lookup"><span data-stu-id="fe342-145">Batch</span></span>|<span data-ttu-id="fe342-146">该操作将作为批处理操作或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 任务的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="fe342-146">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="fe342-147">交互</span><span class="sxs-lookup"><span data-stu-id="fe342-147">Interactive</span></span>|<span data-ttu-id="fe342-148">在用户调用该操作时运行。</span><span class="sxs-lookup"><span data-stu-id="fe342-148">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="fe342-149">处于打开状态</span><span class="sxs-lookup"><span data-stu-id="fe342-149">On Open</span></span>|<span data-ttu-id="fe342-150">第一次打开多维数据集时运行该操作。</span><span class="sxs-lookup"><span data-stu-id="fe342-150">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="fe342-151">**应用程序**</span><span class="sxs-lookup"><span data-stu-id="fe342-151">**Application**</span></span>  
 <span data-ttu-id="fe342-152">键入可执行钻取操作的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="fe342-152">Type the name of the application that can execute the drillthrough action.</span></span>  
  
 <span data-ttu-id="fe342-153">还可以使用此选项来标识最常使用此操作的客户端应用程序，并在弹出菜单中该操作的旁边显示相应的图标。</span><span class="sxs-lookup"><span data-stu-id="fe342-153">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe342-154">此选项只是向客户端应用程序提供使用哪一个客户端应用程序执行某项操作的建议，并不直接控制对该操作的访问。</span><span class="sxs-lookup"><span data-stu-id="fe342-154">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="fe342-155">客户端应用程序将隐藏与其他客户端应用程序关联的所有操作。</span><span class="sxs-lookup"><span data-stu-id="fe342-155">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="fe342-156">**说明**</span><span class="sxs-lookup"><span data-stu-id="fe342-156">**Description**</span></span>  
 <span data-ttu-id="fe342-157">键入操作说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="fe342-157">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="fe342-158">**Caption**</span><span class="sxs-lookup"><span data-stu-id="fe342-158">**Caption**</span></span>  
 <span data-ttu-id="fe342-159">当\*\*\*\*“标题是 MDX”设置为 **False** 时，在客户端应用程序中键入要为操作显示的标题。</span><span class="sxs-lookup"><span data-stu-id="fe342-159">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="fe342-160">当\*\*\*\*“标题是 MDX”设置为 **True** 时，键入返回标题字符串的多维表达式 (MDX)。</span><span class="sxs-lookup"><span data-stu-id="fe342-160">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="fe342-161">**标题是 MDX**</span><span class="sxs-lookup"><span data-stu-id="fe342-161">**Caption Is MDX**</span></span>  
 <span data-ttu-id="fe342-162">选择 **False** 表示“标题”包含一个文字字符串，该字符串表示将在客户端应用程序中为该操作显示的标题。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe342-162">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="fe342-163">选择 **True** 表示 **“标题”** 包含一个 MDX 表达式，该表达式返回一个表示将在客户端应用程序中为该操作显示的标题的字符串。</span><span class="sxs-lookup"><span data-stu-id="fe342-163">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="fe342-164">必须在将该操作返回给客户端应用程序之前解析 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="fe342-164">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe342-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe342-165">See Also</span></span>  
 <span data-ttu-id="fe342-166">[MDX&#41; 引用 &#40;多维表达式](/sql/mdx/multidimensional-expressions-mdx-reference) </span><span class="sxs-lookup"><span data-stu-id="fe342-166">[Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference) </span></span>  
 <span data-ttu-id="fe342-167">[&#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据的操作&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe342-167">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe342-168">[工具栏 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe342-168">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe342-169">[操作管理器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe342-169">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe342-170">[计算工具 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe342-170">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe342-171">[操作窗体编辑器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe342-171">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fe342-172">报表操作窗体编辑器 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="fe342-172">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
