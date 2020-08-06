---
title: 多维模型中的计算 |Microsoft Docs
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], creating
- deleting calculations
- calculations [Analysis Services], scripts
- Cube Designer
- modifying scripts
- removing calculations
- calculations [Analysis Services], deleting
- scripts [Analysis Services], calculations
- cubes [Analysis Services], calculations
- solve orders [Analysis Services]
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64a9733c4fd198a9906e28c437f7ba4fb10dd39a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691998"
---
# <a name="calculations-in-multidimensional-models"></a><span data-ttu-id="bcd97-102">多维模型中的计算</span><span class="sxs-lookup"><span data-stu-id="bcd97-102">Calculations in Multidimensional Models</span></span>
  <span data-ttu-id="bcd97-103">可以使用多维数据集设计器的“计算”选项卡创建计算成员、命名集和其他多维表达式 (MDX) 计算。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bcd97-103">Use the **Calculations** tab of Cube Designer to create calculated members, named sets, and other Multidimensional Expressions (MDX) calculations.</span></span>  
  
 <span data-ttu-id="bcd97-104">**“计算”** 选项卡有以下三个窗格：</span><span class="sxs-lookup"><span data-stu-id="bcd97-104">The **Calculations** tab has the following three panes:</span></span>  
  
-   <span data-ttu-id="bcd97-105">**“脚本组织程序”** 窗格列出了多维数据集中的计算。</span><span class="sxs-lookup"><span data-stu-id="bcd97-105">The **Script Organizer** pane lists the calculations in a cube.</span></span> <span data-ttu-id="bcd97-106">使用此窗格可以创建、组织和选择计算，以便进行编辑。</span><span class="sxs-lookup"><span data-stu-id="bcd97-106">Use this pane to create, organize, and select calculations for editing.</span></span>  
  
-   <span data-ttu-id="bcd97-107">**“计算工具”** 窗格提供了创建计算所需的元数据、函数和模板。</span><span class="sxs-lookup"><span data-stu-id="bcd97-107">The **Calculation Tools** pane provides metadata, functions, and templates with which to create calculations.</span></span>  
  
-   <span data-ttu-id="bcd97-108">“计算表达式”窗格支持窗体视图和脚本视图。</span><span class="sxs-lookup"><span data-stu-id="bcd97-108">The Calculation Expressions pane supports a form view and a script view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcd97-109">有关 MDX 脚本编写的详细信息，请参阅 Microsoft TechNet 网站上[Analysis Services 2005 SQL Server](https://go.microsoft.com/fwlink/?LinkId=80853)的[Mdx 脚本编写介绍 Microsoft SQL Server 2005 中](https://go.microsoft.com/fwlink/?LinkId=81892)的 "其他资源" 部分。</span><span class="sxs-lookup"><span data-stu-id="bcd97-109">For more information about MDX scripting, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892), and see the Additional Resources section on the [SQL Server 2005 - Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) page on the Microsoft TechNet Web site.</span></span> <span data-ttu-id="bcd97-110">有关与多维数据集设计相关的性能问题的详细信息，请参阅 [SQL Server 2005 Analysis Services 性能指南](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc)。</span><span class="sxs-lookup"><span data-stu-id="bcd97-110">For more information about performance issues related to cube design, see the [SQL Server 2005 Analysis Services Performance Guide](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc).</span></span>  
  
## <a name="creating-a-new-calculation"></a><span data-ttu-id="bcd97-111">创建新计算</span><span class="sxs-lookup"><span data-stu-id="bcd97-111">Creating a New Calculation</span></span>  
 <span data-ttu-id="bcd97-112">若要创建新计算，请在多维数据集设计器的 **“计算”** 选项卡的 **“多维数据集”** 菜单中，单击 **“新建计算成员”**、 **“新建命名集”** 或 **“新建脚本命令”**，具体取决于希望创建的计算的类型。</span><span class="sxs-lookup"><span data-stu-id="bcd97-112">To create a new calculation, on the **Calculations** tab of Cube Designer, on the **Cube** menu, click either **New Calculated Member**, **New Named Set**, or **New Script Command**, depending on the type of calculation you want to create.</span></span> <span data-ttu-id="bcd97-113">还可以在工具栏上单击任何相应的按钮，或在“脚本组织程序”窗格中右键单击任何位置，再在快捷菜单中单击一个命令。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bcd97-113">You can also click any of the corresponding buttons on the toolbar, or right-click anywhere in the **Script Organizer** pane and then click one of the commands on the shortcut menu.</span></span> <span data-ttu-id="bcd97-114">此操作会在 **“脚本组织程序”** 窗格中添加新的计算，并在“计算表达式”窗格内的计算窗体中显示它的字段。</span><span class="sxs-lookup"><span data-stu-id="bcd97-114">This action adds a new calculation to the **Script Organizer** pane and displays fields for it in the calculations form in the Calculations Expressions pane.</span></span> <span data-ttu-id="bcd97-115">如果创建新脚本，则此操作将在“计算表达式”窗格中打开“脚本”视图。</span><span class="sxs-lookup"><span data-stu-id="bcd97-115">If you create a new script, this action opens the Script view in the Calculation Expressions pane.</span></span> <span data-ttu-id="bcd97-116">有关生成这三种计算类型的详细信息，请参阅 [创建计算成员](create-calculated-members.md)、 [创建命名集](create-named-sets.md)和 [定义赋值和其他脚本命令](define-assignments-and-other-script-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="bcd97-116">For more information about building the three types of calculations, see [Create Calculated Members](create-calculated-members.md), [Create Named Sets](create-named-sets.md), and [Define Assignments and Other Script Commands](define-assignments-and-other-script-commands.md).</span></span>  
  
## <a name="editing-scripts"></a><span data-ttu-id="bcd97-117">编辑脚本</span><span class="sxs-lookup"><span data-stu-id="bcd97-117">Editing Scripts</span></span>  
 <span data-ttu-id="bcd97-118">在 "**计算**" 选项卡的 "计算表达式" 窗格中编辑脚本。"计算表达式" 窗格有两个视图：脚本视图和窗体视图。</span><span class="sxs-lookup"><span data-stu-id="bcd97-118">Edit scripts in the Calculation Expressions pane of the **Calculations** tab. The Calculation Expressions pane has two views, Script view and Form view.</span></span> <span data-ttu-id="bcd97-119">窗体视图显示单个命令的表达式和属性。</span><span class="sxs-lookup"><span data-stu-id="bcd97-119">The Form view shows the expressions and properties for a single command.</span></span> <span data-ttu-id="bcd97-120">编辑 MDX 脚本时，表达式框将充满整个窗体视图。</span><span class="sxs-lookup"><span data-stu-id="bcd97-120">When you edit an MDX script, an expression box fills the entire Form view.</span></span>  
  
 <span data-ttu-id="bcd97-121">脚本视图提供了用来编辑脚本的代码编辑器。</span><span class="sxs-lookup"><span data-stu-id="bcd97-121">The Script view provides a code editor in which to edit the scripts.</span></span> <span data-ttu-id="bcd97-122">当“计算表达式”窗格在脚本视图中时， **“脚本组织程序”** 窗格将隐藏。</span><span class="sxs-lookup"><span data-stu-id="bcd97-122">While the Calculation Expressions pane is in Script view, the **Script Organizer** pane is hidden.</span></span> <span data-ttu-id="bcd97-123">脚本视图提供了彩色编码、括号匹配、自动完成和 MDX 代码区域。</span><span class="sxs-lookup"><span data-stu-id="bcd97-123">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="bcd97-124">MDX 代码区域可以折叠或展开，以便于进行编辑。</span><span class="sxs-lookup"><span data-stu-id="bcd97-124">The MDX code regions can be collapsed or expanded to facilitate editing.</span></span>  
  
 <span data-ttu-id="bcd97-125">通过单击 **“多维数据集”** 菜单，再指向 **“计算显示位置”**，再单击 **“脚本”** 或 **“窗体”**，可以在窗体视图和脚本视图之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="bcd97-125">You can switch between the Form view and the Script view by clicking the **Cube** menu, pointing to **Show Calculations in**, and then clicking **Script** or **Form**.</span></span> <span data-ttu-id="bcd97-126">还可以在工具栏上单击 **“窗体视图”** 或 **“脚本视图”** 。</span><span class="sxs-lookup"><span data-stu-id="bcd97-126">You can also click either **Form view** or **Script view** on the toolbar.</span></span>  
  
## <a name="changing-solve-order"></a><span data-ttu-id="bcd97-127">更改求解顺序</span><span class="sxs-lookup"><span data-stu-id="bcd97-127">Changing Solve Order</span></span>  
 <span data-ttu-id="bcd97-128">将按照计算在 **“脚本组织程序”** 窗格中的列出的顺序来对计算求解。</span><span class="sxs-lookup"><span data-stu-id="bcd97-128">Calculations are solved in the order listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="bcd97-129">通过右键单击任何计算，再在快捷菜单上单击“上移”或“下移”，可以让计算重新排序。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bcd97-129">You can reorder the calculations by right-clicking any calculation and then clicking **Move Up** or **Move Down** on the shortcut menu.</span></span> <span data-ttu-id="bcd97-130">还可以单击计算，再单击工具栏上的 **“上移”** 或 **“下移”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="bcd97-130">You can also click a calculation and then click the **Move Up** or **Move Down** button on the toolbar.</span></span>  
  
 <span data-ttu-id="bcd97-131">对于计算单元和计算成员，可以手动覆盖此顺序。</span><span class="sxs-lookup"><span data-stu-id="bcd97-131">You can override this order manually for calculated cells and calculated members.</span></span> <span data-ttu-id="bcd97-132">有关传递顺序和求解次序的详细信息，请参阅[理解传递顺序和求解次序 (MDX)](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)。</span><span class="sxs-lookup"><span data-stu-id="bcd97-132">For more information about pass order and solve order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
## <a name="deleting-a-calculation"></a><span data-ttu-id="bcd97-133">删除计算</span><span class="sxs-lookup"><span data-stu-id="bcd97-133">Deleting a Calculation</span></span>  
 <span data-ttu-id="bcd97-134">若要删除现有计算，请在 **“计算”** 选项卡中的 **“脚本组织程序”** 窗格中选择要删除的计算，再在 **“编辑”** 菜单中单击 **“删除”** ，或在工具栏上单击 **“删除”** 图标。</span><span class="sxs-lookup"><span data-stu-id="bcd97-134">To delete an existing calculation, on the **Calculations** tab, in the **Script Organizer** pane, select the calculation to be deleted, and then click **Delete** on the **Edit** menu or click the **Delete** icon on the toolbar.</span></span> <span data-ttu-id="bcd97-135">还可以在“脚本组织程序”窗格中右键单击计算，并从快捷菜单中选择“删除”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bcd97-135">You can also right-click the calculation in the **Script Organizer** pane and select **Delete** from the short-cut menu.</span></span>  
  
  
