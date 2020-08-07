---
title: 报表操作窗体编辑器 (操作 "选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.reportaction.f1
ms.assetid: cebfdd07-e376-46d6-86ef-b6f816a2f360
author: minewiskan
ms.author: owend
ms.openlocfilehash: a6e417f666ec5e6827763257eff19294e21543b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588089"
---
# <a name="report-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="53a4e-102">报表操作窗体编辑器（“操作”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="53a4e-102">Report Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="53a4e-103">可以使用多维数据集设计器中的 **“操作”** 选项卡上的 **“报表操作窗体编辑器”** 窗格，修改在 **“操作组织程序”** 窗格中选择的报表操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-103">Use the **Report Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the report action selected in the **Action Organizer** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="53a4e-104">选项</span><span class="sxs-lookup"><span data-stu-id="53a4e-104">Options</span></span>  
 <span data-ttu-id="53a4e-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="53a4e-105">**Name**</span></span>  
 <span data-ttu-id="53a4e-106">键入操作的名称。</span><span class="sxs-lookup"><span data-stu-id="53a4e-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="53a4e-107">**操作目标**</span><span class="sxs-lookup"><span data-stu-id="53a4e-107">**Action Target**</span></span>  
 <span data-ttu-id="53a4e-108">展开可查看“目标类型”和“目标对象”选项。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="53a4e-109">**目标类型**</span><span class="sxs-lookup"><span data-stu-id="53a4e-109">**Target type**</span></span>  
 <span data-ttu-id="53a4e-110">选择要与该操作关联的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="53a4e-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="53a4e-111">服务器只向客户端返回适用于指定类型的对象的操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="53a4e-112">如果满足 **“条件”** ，并且选择了下表中指定的对象，则客户端可使用该操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="53a4e-113">值</span><span class="sxs-lookup"><span data-stu-id="53a4e-113">Value</span></span>|<span data-ttu-id="53a4e-114">所选对象</span><span class="sxs-lookup"><span data-stu-id="53a4e-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="53a4e-115">属性成员</span><span class="sxs-lookup"><span data-stu-id="53a4e-115">Attribute members</span></span>|<span data-ttu-id="53a4e-116">从 **“目标对象”** 中的属性所处的级别中选择成员。</span><span class="sxs-lookup"><span data-stu-id="53a4e-116">A member is selected from a level based on the attribute in **Target object**.</span></span><br /><br /> <span data-ttu-id="53a4e-117">注意：使用所选属性的其他用户层次结构将继承报表操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-117">Note: Other user hierarchies that use the selected attribute inherit the report action.</span></span>|  
|<span data-ttu-id="53a4e-118">单元</span><span class="sxs-lookup"><span data-stu-id="53a4e-118">Cells</span></span>|<span data-ttu-id="53a4e-119">**“目标对象”** 中的命名集处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-119">The named set in **Target object** is selected.</span></span> <span data-ttu-id="53a4e-120">选择 **“所有单元”** 可以选择多维数据集中的所有单元。</span><span class="sxs-lookup"><span data-stu-id="53a4e-120">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="53a4e-121">多维数据集</span><span class="sxs-lookup"><span data-stu-id="53a4e-121">Cube</span></span>|<span data-ttu-id="53a4e-122">**“目标对象”** 中的多维数据集处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-122">The cube in **Target object** is selected.</span></span> <span data-ttu-id="53a4e-123">选择 CURRENTCUBE 可以使用当前多维数据集。</span><span class="sxs-lookup"><span data-stu-id="53a4e-123">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="53a4e-124">注意：在可能会重命名多维数据集或将该操作复制到其他多维数据集时，使用 CURRENTCUBE 更为方便。</span><span class="sxs-lookup"><span data-stu-id="53a4e-124">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="53a4e-125">建议您使用 CURRENTCUBE 表示当前多维数据集。</span><span class="sxs-lookup"><span data-stu-id="53a4e-125">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="53a4e-126">维度成员</span><span class="sxs-lookup"><span data-stu-id="53a4e-126">Dimension members</span></span>|<span data-ttu-id="53a4e-127">**“目标对象”** 中维度的成员处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-127">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="53a4e-128">层次结构</span><span class="sxs-lookup"><span data-stu-id="53a4e-128">Hierarchy</span></span>|<span data-ttu-id="53a4e-129">**“目标对象”** 中的层次结构处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-129">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="53a4e-130">层次结构成员</span><span class="sxs-lookup"><span data-stu-id="53a4e-130">Hierarchy members</span></span>|<span data-ttu-id="53a4e-131">**“目标对象”** 中层次结构的成员处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-131">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="53a4e-132">级别</span><span class="sxs-lookup"><span data-stu-id="53a4e-132">Level</span></span>|<span data-ttu-id="53a4e-133">**“目标对象”** 中的级别处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-133">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="53a4e-134">级别成员</span><span class="sxs-lookup"><span data-stu-id="53a4e-134">Level members</span></span>|<span data-ttu-id="53a4e-135">**“目标对象”** 中级别的成员处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="53a4e-135">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="53a4e-136">**目标对象**</span><span class="sxs-lookup"><span data-stu-id="53a4e-136">**Target object**</span></span>  
 <span data-ttu-id="53a4e-137">选择要与该操作关联的对象。</span><span class="sxs-lookup"><span data-stu-id="53a4e-137">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="53a4e-138">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例仅将应用于所选对象的操作返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="53a4e-138">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="53a4e-139">可用对象列表受所选 **“目标类型”** 的约束。</span><span class="sxs-lookup"><span data-stu-id="53a4e-139">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="53a4e-140">**条件(可选)**</span><span class="sxs-lookup"><span data-stu-id="53a4e-140">**Condition (Optional)**</span></span>  
 <span data-ttu-id="53a4e-141">输入描述可选条件（与“目标对象”一起使用）的多维表达式 (MDX) 表达式，以进一步限制该操作可用的时间。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-141">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="53a4e-142">表达式必须返回一个布尔值，如果为 True，指示该操作可用。</span><span class="sxs-lookup"><span data-stu-id="53a4e-142">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="53a4e-143">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="53a4e-143">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="53a4e-144">**报表服务器**</span><span class="sxs-lookup"><span data-stu-id="53a4e-144">**Report Server**</span></span>  
 <span data-ttu-id="53a4e-145">展开该选项可以查看“服务器名称”、“服务器路径”和“报表格式”选项。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-145">Expand to view the **Server name**, **Server path**, and **Report format** options.</span></span>  
  
 <span data-ttu-id="53a4e-146">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="53a4e-146">**Server name**</span></span>  
 <span data-ttu-id="53a4e-147">键入 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 操作在其上运行报表的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="53a4e-147">Type the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance on which the action runs the report.</span></span>  
  
 <span data-ttu-id="53a4e-148">**服务器路径**</span><span class="sxs-lookup"><span data-stu-id="53a4e-148">**Server path**</span></span>  
 <span data-ttu-id="53a4e-149">键入 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 实例上的报表的路径。</span><span class="sxs-lookup"><span data-stu-id="53a4e-149">Type the path to the report on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance.</span></span> <span data-ttu-id="53a4e-150">例如，键入 **Sales/YearlySalesByCategory**。</span><span class="sxs-lookup"><span data-stu-id="53a4e-150">For example, type **Sales/YearlySalesByCategory**.</span></span>  
  
 <span data-ttu-id="53a4e-151">**报表格式**</span><span class="sxs-lookup"><span data-stu-id="53a4e-151">**Report format**</span></span>  
 <span data-ttu-id="53a4e-152">选择返回报表时所采用的格式。</span><span class="sxs-lookup"><span data-stu-id="53a4e-152">Select the format in which the report is returned.</span></span> <span data-ttu-id="53a4e-153">下表对可用的格式进行了说明：</span><span class="sxs-lookup"><span data-stu-id="53a4e-153">The following table describes the available formats.</span></span>  
  
|<span data-ttu-id="53a4e-154">值</span><span class="sxs-lookup"><span data-stu-id="53a4e-154">Value</span></span>|<span data-ttu-id="53a4e-155">说明</span><span class="sxs-lookup"><span data-stu-id="53a4e-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="53a4e-156">HTML5</span><span class="sxs-lookup"><span data-stu-id="53a4e-156">HTML5</span></span>|<span data-ttu-id="53a4e-157">报表以 HTML 5.0 标准格式返回。</span><span class="sxs-lookup"><span data-stu-id="53a4e-157">Report is returned in an HTML 5.0-compliant format.</span></span>|  
|<span data-ttu-id="53a4e-158">HTML3</span><span class="sxs-lookup"><span data-stu-id="53a4e-158">HTML3</span></span>|<span data-ttu-id="53a4e-159">报表以 HTML 3.2 标准格式返回。</span><span class="sxs-lookup"><span data-stu-id="53a4e-159">Report is returned in an HTML 3.2-compliant format.</span></span>|  
|<span data-ttu-id="53a4e-160">Excel</span><span class="sxs-lookup"><span data-stu-id="53a4e-160">Excel</span></span>|<span data-ttu-id="53a4e-161">报表以 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 工作簿 (.xls) 文件的形式返回。</span><span class="sxs-lookup"><span data-stu-id="53a4e-161">Report is returned as a [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel workbook (.xls) file.</span></span>|  
|<span data-ttu-id="53a4e-162">PDF</span><span class="sxs-lookup"><span data-stu-id="53a4e-162">PDF</span></span>|<span data-ttu-id="53a4e-163">报表以 Adobe 可移植文档格式 (.pdf) 文件的形式返回。</span><span class="sxs-lookup"><span data-stu-id="53a4e-163">Report is returned as an Adobe Portable Document Format (.pdf) file.</span></span>|  
  
 <span data-ttu-id="53a4e-164">**参数(可选)**</span><span class="sxs-lookup"><span data-stu-id="53a4e-164">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="53a4e-165">展开该选项可以查看一个网格，在该网格中，可以为“报表”中指定的报表提供报表参数。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-165">Expand to view a grid in which report parameters can be supplied for the report specified in **Report**.</span></span> <span data-ttu-id="53a4e-166">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="53a4e-166">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="53a4e-167">列</span><span class="sxs-lookup"><span data-stu-id="53a4e-167">Column</span></span>|<span data-ttu-id="53a4e-168">说明</span><span class="sxs-lookup"><span data-stu-id="53a4e-168">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53a4e-169">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="53a4e-169">**Parameter Name**</span></span>|<span data-ttu-id="53a4e-170">键入要传递给报表的报表参数名称。</span><span class="sxs-lookup"><span data-stu-id="53a4e-170">Type the name of the report parameter to be passed to the report.</span></span>|  
|<span data-ttu-id="53a4e-171">**参数值**</span><span class="sxs-lookup"><span data-stu-id="53a4e-171">**Parameter Value**</span></span>|<span data-ttu-id="53a4e-172">键入要传递给报表的报表参数值。</span><span class="sxs-lookup"><span data-stu-id="53a4e-172">Type the value of the report parameter to be passed to the report.</span></span><br /><br /> <span data-ttu-id="53a4e-173">单击省略号按钮 (**...**) 可以显示“MDX 生成器”对话框，并创建提供报表参数值的 MDX 表达式。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-173">Click the ellipsis button (**...**) to display the **MDX Builder** dialog box and create an MDX expression that provides the value of the report parameter.</span></span> <span data-ttu-id="53a4e-174">有关\*\*\*\*“MDX 生成器”对话框的详细信息，请参阅[“MDX 生成器”（Analysis Services - 多维数据）](mdx-builder-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="53a4e-174">For more information about the **MDX Builder** dialog box, see [MDX Builder &#40;Analysis Services - Multidimensional Data&#41;](mdx-builder-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="53a4e-175">如果将参数设置为 MDX 表达式，在运行操作时将计算该表达式，否则将参数不做任何修改直接传递给报表。</span><span class="sxs-lookup"><span data-stu-id="53a4e-175">If the parameter is set to an MDX expression, then the expression is evaluated when the action is run, otherwise it is passed to the report without modification.</span></span>|  
  
 <span data-ttu-id="53a4e-176">**其他属性**</span><span class="sxs-lookup"><span data-stu-id="53a4e-176">**Additional Properties**</span></span>  
 <span data-ttu-id="53a4e-177">展开可查看“调用”、“应用程序”、“说明”、“标题”和“标题是 MDX”选项。\*\*\*\*, \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-177">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="53a4e-178">**调用**</span><span class="sxs-lookup"><span data-stu-id="53a4e-178">**Invocation**</span></span>  
 <span data-ttu-id="53a4e-179">选择相应设置，指示何时执行该操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-179">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53a4e-180">此选项只是向客户端应用程序提供何时执行某项操作的建议，并不直接控制对该操作的调用。</span><span class="sxs-lookup"><span data-stu-id="53a4e-180">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="53a4e-181">下表对可用的设置进行了说明：</span><span class="sxs-lookup"><span data-stu-id="53a4e-181">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="53a4e-182">值</span><span class="sxs-lookup"><span data-stu-id="53a4e-182">Value</span></span>|<span data-ttu-id="53a4e-183">说明</span><span class="sxs-lookup"><span data-stu-id="53a4e-183">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="53a4e-184">Batch</span><span class="sxs-lookup"><span data-stu-id="53a4e-184">Batch</span></span>|<span data-ttu-id="53a4e-185">操作应作为批处理操作或任务的一部分运行 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="53a4e-185">The action should run as part of a batch operation or a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="53a4e-186">交互</span><span class="sxs-lookup"><span data-stu-id="53a4e-186">Interactive</span></span>|<span data-ttu-id="53a4e-187">在用户调用该操作时运行。</span><span class="sxs-lookup"><span data-stu-id="53a4e-187">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="53a4e-188">处于打开状态</span><span class="sxs-lookup"><span data-stu-id="53a4e-188">On Open</span></span>|<span data-ttu-id="53a4e-189">第一次打开多维数据集时运行该操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-189">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="53a4e-190">**应用程序**</span><span class="sxs-lookup"><span data-stu-id="53a4e-190">**Application**</span></span>  
 <span data-ttu-id="53a4e-191">键入可以解释“操作表达式”所返回字符串的应用程序的名称。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-191">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="53a4e-192">还可以使用此选项来标识最常使用此操作的客户端应用程序，并在弹出菜单中该操作的旁边显示相应的图标。</span><span class="sxs-lookup"><span data-stu-id="53a4e-192">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53a4e-193">此选项只是向客户端应用程序提供使用哪一个客户端应用程序执行某项操作的建议，并不直接控制对该操作的访问。</span><span class="sxs-lookup"><span data-stu-id="53a4e-193">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="53a4e-194">客户端应用程序将隐藏与其他客户端应用程序关联的所有操作。</span><span class="sxs-lookup"><span data-stu-id="53a4e-194">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="53a4e-195">**描述**</span><span class="sxs-lookup"><span data-stu-id="53a4e-195">**Description**</span></span>  
 <span data-ttu-id="53a4e-196">键入操作说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="53a4e-196">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="53a4e-197">**Caption**</span><span class="sxs-lookup"><span data-stu-id="53a4e-197">**Caption**</span></span>  
 <span data-ttu-id="53a4e-198">当\*\*\*\*“标题是 MDX”设置为 **False** 时，在客户端应用程序中键入要为操作显示的标题。</span><span class="sxs-lookup"><span data-stu-id="53a4e-198">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="53a4e-199">当 **“标题是 MDX”** 设置为 **True**时，显示返回标题字符串的键入多维表达式 (MDX)。</span><span class="sxs-lookup"><span data-stu-id="53a4e-199">Type the MDX expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="53a4e-200">**标题是 MDX**</span><span class="sxs-lookup"><span data-stu-id="53a4e-200">**Caption is MDX**</span></span>  
 <span data-ttu-id="53a4e-201">选择 **False** 表示“标题”包含一个文字字符串，该字符串表示将在客户端应用程序中为该操作显示的标题。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="53a4e-201">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="53a4e-202">选择 **True** 表示 **“标题”** 包含一个 MDX 表达式，该表达式返回一个表示将在客户端应用程序中为该操作显示的标题的字符串。</span><span class="sxs-lookup"><span data-stu-id="53a4e-202">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="53a4e-203">必须在将该操作返回给客户端应用程序之前解析 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="53a4e-203">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a4e-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53a4e-204">See Also</span></span>  
 <span data-ttu-id="53a4e-205">[&#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据的操作&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="53a4e-205">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="53a4e-206">[工具栏 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="53a4e-206">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="53a4e-207">[操作管理器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="53a4e-207">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="53a4e-208">[计算工具 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="53a4e-208">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="53a4e-209">[操作窗体编辑器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="53a4e-209">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="53a4e-210">钻取操作窗体编辑器 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="53a4e-210">Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
