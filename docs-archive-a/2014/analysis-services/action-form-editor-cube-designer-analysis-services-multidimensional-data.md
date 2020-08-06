---
title: 操作窗体编辑器 ("操作" 选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.action.f1
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08ed03e843ba206f22969f9ada0da5a590a5811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578542"
---
# <a name="action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="5346f-102">操作窗体编辑器（“操作”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="5346f-102">Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5346f-103">可以使用多维数据集设计器中的 **“操作”** 选项卡上的“操作窗体编辑器”窗格创建和修改标准操作。</span><span class="sxs-lookup"><span data-stu-id="5346f-103">Use the Action Form Editor pane on the **Actions** tab in Cube Designer to create and modify standard actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5346f-104">选项</span><span class="sxs-lookup"><span data-stu-id="5346f-104">Options</span></span>  
 <span data-ttu-id="5346f-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="5346f-105">**Name**</span></span>  
 <span data-ttu-id="5346f-106">键入操作的名称。</span><span class="sxs-lookup"><span data-stu-id="5346f-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="5346f-107">**操作目标**</span><span class="sxs-lookup"><span data-stu-id="5346f-107">**Action Target**</span></span>  
 <span data-ttu-id="5346f-108">展开可查看“目标类型”和“目标对象”选项。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5346f-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="5346f-109">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="5346f-109">**Target type**</span></span>  
 <span data-ttu-id="5346f-110">选择要与该操作关联的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="5346f-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="5346f-111">服务器只向客户端返回适用于指定类型的对象的操作。</span><span class="sxs-lookup"><span data-stu-id="5346f-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="5346f-112">如果满足 **“条件”** ，并且选择了下表中指定的对象，则客户端可使用该操作。</span><span class="sxs-lookup"><span data-stu-id="5346f-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="5346f-113">值</span><span class="sxs-lookup"><span data-stu-id="5346f-113">Value</span></span>|<span data-ttu-id="5346f-114">所选对象</span><span class="sxs-lookup"><span data-stu-id="5346f-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="5346f-115">属性成员</span><span class="sxs-lookup"><span data-stu-id="5346f-115">Attribute members</span></span>|<span data-ttu-id="5346f-116">从 **“目标对象”** 中的属性所处的级别中选择成员。</span><span class="sxs-lookup"><span data-stu-id="5346f-116">A member is selected from a level based on the attribute in **Target object**.</span></span>|  
|<span data-ttu-id="5346f-117">单元</span><span class="sxs-lookup"><span data-stu-id="5346f-117">Cells</span></span>|<span data-ttu-id="5346f-118">**“目标对象”** 中的命名集处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-118">The named set in **Target object** is selected.</span></span> <span data-ttu-id="5346f-119">选择 **“所有单元”** 可以选择多维数据集中的所有单元。</span><span class="sxs-lookup"><span data-stu-id="5346f-119">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="5346f-120">多维数据集</span><span class="sxs-lookup"><span data-stu-id="5346f-120">Cube</span></span>|<span data-ttu-id="5346f-121">**“目标对象”** 中的多维数据集处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-121">The cube in **Target object** is selected.</span></span> <span data-ttu-id="5346f-122">选择 CURRENTCUBE 可以使用当前多维数据集。</span><span class="sxs-lookup"><span data-stu-id="5346f-122">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="5346f-123">注意：在可能会重命名多维数据集或将该操作复制到其他多维数据集时，使用 CURRENTCUBE 更为方便。</span><span class="sxs-lookup"><span data-stu-id="5346f-123">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="5346f-124">建议您使用 CURRENTCUBE 表示当前多维数据集。</span><span class="sxs-lookup"><span data-stu-id="5346f-124">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="5346f-125">维度成员</span><span class="sxs-lookup"><span data-stu-id="5346f-125">Dimension members</span></span>|<span data-ttu-id="5346f-126">**“目标对象”** 中维度的成员处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-126">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5346f-127">层次结构</span><span class="sxs-lookup"><span data-stu-id="5346f-127">Hierarchy</span></span>|<span data-ttu-id="5346f-128">**“目标对象”** 中的层次结构处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-128">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5346f-129">层次结构成员</span><span class="sxs-lookup"><span data-stu-id="5346f-129">Hierarchy members</span></span>|<span data-ttu-id="5346f-130">**“目标对象”** 中层次结构的成员处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-130">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5346f-131">级别</span><span class="sxs-lookup"><span data-stu-id="5346f-131">Level</span></span>|<span data-ttu-id="5346f-132">**“目标对象”** 中的级别处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-132">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5346f-133">级别成员</span><span class="sxs-lookup"><span data-stu-id="5346f-133">Level members</span></span>|<span data-ttu-id="5346f-134">**“目标对象”** 中级别的成员处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="5346f-134">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="5346f-135">**目标对象**</span><span class="sxs-lookup"><span data-stu-id="5346f-135">**Target object**</span></span>  
 <span data-ttu-id="5346f-136">选择要与该操作关联的对象。</span><span class="sxs-lookup"><span data-stu-id="5346f-136">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="5346f-137">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例仅将应用于所选对象的操作返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="5346f-137">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="5346f-138">可用对象列表受所选 **“目标类型”** 的约束。</span><span class="sxs-lookup"><span data-stu-id="5346f-138">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="5346f-139">**条件(可选)**</span><span class="sxs-lookup"><span data-stu-id="5346f-139">**Condition (Optional)**</span></span>  
 <span data-ttu-id="5346f-140">输入描述可选条件（与“目标对象”一起使用）的多维表达式 (MDX) 表达式，以进一步限制该操作可用的时间。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5346f-140">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="5346f-141">表达式必须返回一个布尔值，如果为 True，指示该操作可用。</span><span class="sxs-lookup"><span data-stu-id="5346f-141">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="5346f-142">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="5346f-142">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="5346f-143">**操作内容**</span><span class="sxs-lookup"><span data-stu-id="5346f-143">**Action Content**</span></span>  
 <span data-ttu-id="5346f-144">展开此项可以查看“类型”和“操作表达式”选项。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5346f-144">Expand to view the **Type** and **Action expression** options.</span></span>  
  
 <span data-ttu-id="5346f-145">**Type**</span><span class="sxs-lookup"><span data-stu-id="5346f-145">**Type**</span></span>  
 <span data-ttu-id="5346f-146">选择在运行操作时要执行的操作类型。</span><span class="sxs-lookup"><span data-stu-id="5346f-146">Select the type of action to take when the action is run.</span></span> <span data-ttu-id="5346f-147">可用的操作类型包括：</span><span class="sxs-lookup"><span data-stu-id="5346f-147">The following action types are available:</span></span>  
  
|<span data-ttu-id="5346f-148">值</span><span class="sxs-lookup"><span data-stu-id="5346f-148">Value</span></span>|<span data-ttu-id="5346f-149">说明</span><span class="sxs-lookup"><span data-stu-id="5346f-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5346f-150">数据集</span><span class="sxs-lookup"><span data-stu-id="5346f-150">Dataset</span></span>|<span data-ttu-id="5346f-151">返回将由客户端应用程序运行和显示的表示多维数据集的多维表达式 (MDX) 语句。</span><span class="sxs-lookup"><span data-stu-id="5346f-151">Returns a Multidimensional Expressions (MDX) statement, representing a multidimensional dataset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="5346f-152">专有</span><span class="sxs-lookup"><span data-stu-id="5346f-152">Proprietary</span></span>|<span data-ttu-id="5346f-153">对于此操作的 **“应用程序”** 设置所关联的客户端应用程序，返回该程序能够解释的专有字符串。</span><span class="sxs-lookup"><span data-stu-id="5346f-153">Returns a proprietary string that can be interpreted by client applications associated with the **Application** setting for this action.</span></span>|  
|<span data-ttu-id="5346f-154">行集</span><span class="sxs-lookup"><span data-stu-id="5346f-154">Rowset</span></span>|<span data-ttu-id="5346f-155">返回将由客户端应用程序运行和显示的表示表格格式行集的多维表达式 (MDX) 语句。</span><span class="sxs-lookup"><span data-stu-id="5346f-155">Returns a Multidimensional Expressions (MDX) statement, representing a tabular rowset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="5346f-156">Statement</span><span class="sxs-lookup"><span data-stu-id="5346f-156">Statement</span></span>|<span data-ttu-id="5346f-157">返回将由客户端应用程序运行的命令字符串。</span><span class="sxs-lookup"><span data-stu-id="5346f-157">Returns a command string to be run by the client application.</span></span>|  
|<span data-ttu-id="5346f-158">URL</span><span class="sxs-lookup"><span data-stu-id="5346f-158">URL</span></span>|<span data-ttu-id="5346f-159">返回将由客户端应用程序通常使用 Internet 浏览器打开的统一资源定位器 (URL) 字符串。</span><span class="sxs-lookup"><span data-stu-id="5346f-159">Returns a Uniform Resource Location (URL) string to be opened by the client application, typically with an Internet browser.</span></span>|  
  
 <span data-ttu-id="5346f-160">有关操作类型的详细信息，请参阅[操作（Analysis Services - 多维数据）](multidimensional-models/actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5346f-160">For more information about action types, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5346f-161">**操作表达式**</span><span class="sxs-lookup"><span data-stu-id="5346f-161">**Action expression**</span></span>  
 <span data-ttu-id="5346f-162">键入用于将操作所返回的字符串返回到客户端应用程序进行执行的多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="5346f-162">Type the Multidimensional Expressions (MDX) expression that returns the string returned by the action to the client application for execution.</span></span>  
  
 <span data-ttu-id="5346f-163">**其他属性**</span><span class="sxs-lookup"><span data-stu-id="5346f-163">**Additional Properties**</span></span>  
 <span data-ttu-id="5346f-164">展开可查看“调用”、“应用程序”、“说明”、“标题”和“标题是 MDX”选项。\*\*\*\*, \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5346f-164">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="5346f-165">**调用**</span><span class="sxs-lookup"><span data-stu-id="5346f-165">**Invocation**</span></span>  
 <span data-ttu-id="5346f-166">选择相应设置，指示何时执行该操作。</span><span class="sxs-lookup"><span data-stu-id="5346f-166">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5346f-167">此选项只是向客户端应用程序提供何时执行某项操作的建议，并不直接控制对该操作的调用。</span><span class="sxs-lookup"><span data-stu-id="5346f-167">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="5346f-168">下表对可用的设置进行了说明：</span><span class="sxs-lookup"><span data-stu-id="5346f-168">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="5346f-169">值</span><span class="sxs-lookup"><span data-stu-id="5346f-169">Value</span></span>|<span data-ttu-id="5346f-170">说明</span><span class="sxs-lookup"><span data-stu-id="5346f-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5346f-171">Batch</span><span class="sxs-lookup"><span data-stu-id="5346f-171">Batch</span></span>|<span data-ttu-id="5346f-172">该操作将作为批处理操作或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 任务的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="5346f-172">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="5346f-173">交互</span><span class="sxs-lookup"><span data-stu-id="5346f-173">Interactive</span></span>|<span data-ttu-id="5346f-174">在用户调用该操作时运行。</span><span class="sxs-lookup"><span data-stu-id="5346f-174">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="5346f-175">处于打开状态</span><span class="sxs-lookup"><span data-stu-id="5346f-175">On Open</span></span>|<span data-ttu-id="5346f-176">第一次打开多维数据集时运行该操作。</span><span class="sxs-lookup"><span data-stu-id="5346f-176">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="5346f-177">**应用程序**</span><span class="sxs-lookup"><span data-stu-id="5346f-177">**Application**</span></span>  
 <span data-ttu-id="5346f-178">键入可以解释“操作表达式”所返回字符串的应用程序的名称。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5346f-178">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="5346f-179">还可以使用此选项来标识最常使用此操作的客户端应用程序，并在弹出菜单中该操作的旁边显示相应的图标。</span><span class="sxs-lookup"><span data-stu-id="5346f-179">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5346f-180">此选项只是向客户端应用程序提供使用哪一个客户端应用程序执行某项操作的建议，并不直接控制对该操作的访问。</span><span class="sxs-lookup"><span data-stu-id="5346f-180">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="5346f-181">客户端应用程序将隐藏与其他客户端应用程序关联的所有操作。</span><span class="sxs-lookup"><span data-stu-id="5346f-181">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="5346f-182">**说明**</span><span class="sxs-lookup"><span data-stu-id="5346f-182">**Description**</span></span>  
 <span data-ttu-id="5346f-183">键入操作说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="5346f-183">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="5346f-184">**Caption**</span><span class="sxs-lookup"><span data-stu-id="5346f-184">**Caption**</span></span>  
 <span data-ttu-id="5346f-185">当\*\*\*\*“标题是 MDX”设置为 **False** 时，在客户端应用程序中键入要为操作显示的标题。</span><span class="sxs-lookup"><span data-stu-id="5346f-185">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="5346f-186">当\*\*\*\*“标题是 MDX”设置为 **True** 时，键入返回标题字符串的多维表达式 (MDX)。</span><span class="sxs-lookup"><span data-stu-id="5346f-186">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="5346f-187">**标题是 MDX**</span><span class="sxs-lookup"><span data-stu-id="5346f-187">**Caption is MDX**</span></span>  
 <span data-ttu-id="5346f-188">选择 **False** 表示“标题”包含一个文字字符串，该字符串表示将在客户端应用程序中为该操作显示的标题。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5346f-188">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="5346f-189">选择 **True** 表示 **“标题”** 包含一个 MDX 表达式，该表达式返回一个表示将在客户端应用程序中为该操作显示的标题的字符串。</span><span class="sxs-lookup"><span data-stu-id="5346f-189">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="5346f-190">必须在将该操作返回给客户端应用程序之前解析 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="5346f-190">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5346f-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5346f-191">See Also</span></span>  
 <span data-ttu-id="5346f-192">[&#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据的操作&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5346f-192">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5346f-193">[工具栏 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5346f-193">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5346f-194">[操作管理器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5346f-194">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5346f-195">[计算工具 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5346f-195">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5346f-196">[钻取操作窗体编辑器 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5346f-196">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5346f-197">报表操作窗体编辑器 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="5346f-197">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
