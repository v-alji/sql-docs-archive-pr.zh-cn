---
title: 创建计算成员 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated members [Analysis Services]
- custom measures [Analysis Services]
- members [Analysis Services], calculated
- calculations [Analysis Services], calculated members
ms.assetid: 820e4b18-9c3a-4b12-a126-ca16d8364a00
author: minewiskan
ms.author: owend
ms.openlocfilehash: c45ef3cf720e6a3cc43156b032d91d205d6334bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577890"
---
# <a name="create-calculated-members"></a><span data-ttu-id="d210b-102">创建计算成员</span><span class="sxs-lookup"><span data-stu-id="d210b-102">Create Calculated Members</span></span>
  <span data-ttu-id="d210b-103">可以组合使用多维数据集数据、算术运算符、数字和函数以创建自定义度量值或维度成员，这些度量值和维度成员称为计算成员。</span><span class="sxs-lookup"><span data-stu-id="d210b-103">You can create customized measures or dimension members, called calculated members, by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="d210b-104">例如，通过将换算比率和现有美元度量值相乘，可以创建将美元转换成欧元的计算成员 Euros。</span><span class="sxs-lookup"><span data-stu-id="d210b-104">For example, you can create a calculated member named Euros that converts dollars to euros by multiplying an existing dollar measure by a conversion rate.</span></span> <span data-ttu-id="d210b-105">然后，Euros 会在一个单独的行或列中显示给最终用户。</span><span class="sxs-lookup"><span data-stu-id="d210b-105">Euros can then be displayed to end users in a separate row or column.</span></span>  
  
 <span data-ttu-id="d210b-106">计算成员的定义将存储起来，而它们的值则只存在于内存中。</span><span class="sxs-lookup"><span data-stu-id="d210b-106">Calculated member definitions are stored, but their values exist only in memory.</span></span> <span data-ttu-id="d210b-107">在上面的示例中，虽然马克的值会显示给最终用户，但这些值并没有存储为多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="d210b-107">In the preceding example, values in marks are displayed to end users but are not stored as cube data.</span></span>  
  
 <span data-ttu-id="d210b-108">您可以创建多维数据集中的计算成员。</span><span class="sxs-lookup"><span data-stu-id="d210b-108">You create calculated members in cubes.</span></span> <span data-ttu-id="d210b-109">若要创建计算成员，请在多维数据集设计器的 **“计算”** 选项卡中，单击工具栏中的 **“新建计算成员”** 图标。</span><span class="sxs-lookup"><span data-stu-id="d210b-109">To create a calculated member, in Cube Designer, on the **Calculations** tab, click the **New Calculated Member** icon on the toolbar.</span></span> <span data-ttu-id="d210b-110">该命令显示了一个窗体，可指定下列计算成员选项：</span><span class="sxs-lookup"><span data-stu-id="d210b-110">This command displays a form to specify the following options for the calculated member:</span></span>  
  
 <span data-ttu-id="d210b-111">**名称**</span><span class="sxs-lookup"><span data-stu-id="d210b-111">**Name**</span></span>  
 <span data-ttu-id="d210b-112">选择计算成员的名称。</span><span class="sxs-lookup"><span data-stu-id="d210b-112">Select the name of the calculated member.</span></span> <span data-ttu-id="d210b-113">最终用户浏览多维数据集时，该名称显示为计算成员值的列或行标题。</span><span class="sxs-lookup"><span data-stu-id="d210b-113">This name appears as the column or row heading for the calculated member values when end users browse the cube.</span></span>  
  
 <span data-ttu-id="d210b-114">**父层次结构**</span><span class="sxs-lookup"><span data-stu-id="d210b-114">**Parent hierarchy**</span></span>  
 <span data-ttu-id="d210b-115">选择用于包含计算成员的父层次结构。</span><span class="sxs-lookup"><span data-stu-id="d210b-115">Select the parent hierarchy to include in the calculated member.</span></span> <span data-ttu-id="d210b-116">层次结构是一些说明性的维度类别，通过这些类别，可以对多维数据集中的数字数据（即度量值）进行划分以便分析。</span><span class="sxs-lookup"><span data-stu-id="d210b-116">Hierarchies are descriptive categories of a dimension by which the numeric data (that is, measures) in a cube can be separated for analysis.</span></span> <span data-ttu-id="d210b-117">在表格格式浏览器中，当最终用户浏览多维数据集中的数据时，层次结构提供显示给最终用户的列标题和行标题。</span><span class="sxs-lookup"><span data-stu-id="d210b-117">In tabular browsers, hierarchies provide the column and row headings displayed to end users when they browse data in a cube.</span></span> <span data-ttu-id="d210b-118">（在图形浏览器中，它们提供其他类型的说明性标签，但功能与表格格式浏览器中的标签相同。）计算成员在选定的父维度中提供一个新标题（或标签）。</span><span class="sxs-lookup"><span data-stu-id="d210b-118">(In graphical browsers, they provide other types of descriptive labels, but they have the same function as in tabular browsers.) A calculated member provides a new heading (or label) in the parent dimension you select.</span></span>  
  
 <span data-ttu-id="d210b-119">或者，可以让计算成员包含在度量值中，而不是包含在维度中。</span><span class="sxs-lookup"><span data-stu-id="d210b-119">Alternatively, you can include the calculated member in the measures instead of in a dimension.</span></span> <span data-ttu-id="d210b-120">该选项也提供一个新的列标题或行标题，但这个标题附加在浏览器的度量值中。</span><span class="sxs-lookup"><span data-stu-id="d210b-120">This option also provides a new column or row heading, but it is attached to measures in the browser.</span></span>  
  
 <span data-ttu-id="d210b-121">**父成员**</span><span class="sxs-lookup"><span data-stu-id="d210b-121">**Parent member**</span></span>  
 <span data-ttu-id="d210b-122">单击“更改”\*\*\*\* 可以选择用于包含计算成员的父成员。</span><span class="sxs-lookup"><span data-stu-id="d210b-122">Click **Change** to select a parent member to include the calculated member.</span></span> <span data-ttu-id="d210b-123">如果选择具有一个级别的层次结构或“MEASURES”作为父维度，则该选项不可用。</span><span class="sxs-lookup"><span data-stu-id="d210b-123">This option is unavailable if you select a one-level hierarchy or MEASURES as the parent dimension.</span></span>  
  
 <span data-ttu-id="d210b-124">层次结构划分为包含成员的不同级别。</span><span class="sxs-lookup"><span data-stu-id="d210b-124">Hierarchies are divided into levels that contain members.</span></span> <span data-ttu-id="d210b-125">每个成员都生成一个标题。</span><span class="sxs-lookup"><span data-stu-id="d210b-125">Each member produces a heading.</span></span> <span data-ttu-id="d210b-126">浏览多维数据集中的数据时，最终用户可以从选定的标题深化至先前未显示的副标题。</span><span class="sxs-lookup"><span data-stu-id="d210b-126">While browsing data in a cube, end users can drill down from a selected heading to previously undisplayed subordinate headings.</span></span> <span data-ttu-id="d210b-127">计算成员的标题将添加到选定的父成员下的第一个级别中。</span><span class="sxs-lookup"><span data-stu-id="d210b-127">The heading for the calculated member is added at the level directly below the parent member you select.</span></span>  
  
 <span data-ttu-id="d210b-128">**表达式**</span><span class="sxs-lookup"><span data-stu-id="d210b-128">**Expression**</span></span>  
 <span data-ttu-id="d210b-129">指定生成计算成员值的表达式。</span><span class="sxs-lookup"><span data-stu-id="d210b-129">Specify the expression that produces the values of the calculated member.</span></span> <span data-ttu-id="d210b-130">该表达式可使用多维表达式 (MDX) 编写。</span><span class="sxs-lookup"><span data-stu-id="d210b-130">This expression can be written in Multidimensional Expressions (MDX).</span></span> <span data-ttu-id="d210b-131">该表达式可以包含下列任何内容：</span><span class="sxs-lookup"><span data-stu-id="d210b-131">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="d210b-132">表示多维数据集的维度、级别、度量值等组件的数据表达式</span><span class="sxs-lookup"><span data-stu-id="d210b-132">Data expressions that represent cube components such as dimensions, levels, measures, and so on</span></span>  
  
-   <span data-ttu-id="d210b-133">算术运算符</span><span class="sxs-lookup"><span data-stu-id="d210b-133">Arithmetic operators</span></span>  
  
-   <span data-ttu-id="d210b-134">数字</span><span class="sxs-lookup"><span data-stu-id="d210b-134">Numbers</span></span>  
  
-   <span data-ttu-id="d210b-135">函数</span><span class="sxs-lookup"><span data-stu-id="d210b-135">Functions</span></span>  
  
 <span data-ttu-id="d210b-136">您可以从 **“计算工具”** 窗格的 **“元数据”** 选项卡拖动或复制多维数据集组件以快速将其添加到表达式中。</span><span class="sxs-lookup"><span data-stu-id="d210b-136">You can drag or copy cube components from the **Metadata** tab of the **Calculation Tools** pane to quickly add them to an expression.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d210b-137">任何要在另一计算成员的值表达式中使用的计算成员都必须在创建将使用它的计算成员之前创建。</span><span class="sxs-lookup"><span data-stu-id="d210b-137">Any calculated member that is to be used in the value expression of another calculated member must be created before the calculated member that uses it.</span></span>  
  
 <span data-ttu-id="d210b-138">格式字符串</span><span class="sxs-lookup"><span data-stu-id="d210b-138">Format String</span></span>  
 <span data-ttu-id="d210b-139">指定基于计算成员的单元值的格式。</span><span class="sxs-lookup"><span data-stu-id="d210b-139">Specifies the format of cell values that are based on the calculated member.</span></span> <span data-ttu-id="d210b-140">此属性与度量值的 `Display Format` 属性接受相同的值。</span><span class="sxs-lookup"><span data-stu-id="d210b-140">This property accepts the same values as the `Display Format` property for measures.</span></span> <span data-ttu-id="d210b-141">有关显示格式的详细信息，请参阅 [配置度量值属性](configure-measure-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d210b-141">For more information about display formats, see [Configure Measure Properties](configure-measure-properties.md).</span></span>  
  
 <span data-ttu-id="d210b-142">可见</span><span class="sxs-lookup"><span data-stu-id="d210b-142">Visible</span></span>  
 <span data-ttu-id="d210b-143">确定在检索多维数据集元数据时计算成员是可见还是隐藏。</span><span class="sxs-lookup"><span data-stu-id="d210b-143">Determines whether the calculated member is visible or hidden when cube metadata is retrieved.</span></span> <span data-ttu-id="d210b-144">如果计算成员处于隐藏状态，则仍然可以在 MDX 表达式、语句和脚本中使用它，但在客户端用户界面中它不会显示为可选择的对象。</span><span class="sxs-lookup"><span data-stu-id="d210b-144">If the calculated member is hidden, it can still be used in MDX expressions, statements, and scripts, but it is not displayed as a selectable object in client user interfaces.</span></span>  
  
 <span data-ttu-id="d210b-145">非空行为</span><span class="sxs-lookup"><span data-stu-id="d210b-145">Non-empty Behavior</span></span>  
 <span data-ttu-id="d210b-146">存储用于解析 MDX 中非空查询的度量值名称。</span><span class="sxs-lookup"><span data-stu-id="d210b-146">Stores the names of measures used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="d210b-147">如果此属性为空，则必须对计算成员进行重复计算，才能确定成员是否为空。</span><span class="sxs-lookup"><span data-stu-id="d210b-147">If this property is blank, the calculated member must be evaluated repeatedly to determine whether a member is empty.</span></span> <span data-ttu-id="d210b-148">如果此属性包含一个或多个度量值的名称，并且所有指定的度量值均为空，则计算成员将被视为空。</span><span class="sxs-lookup"><span data-stu-id="d210b-148">If this property contains the name of one or more measures, the calculated member is treated as empty if all the specified measures are empty.</span></span> <span data-ttu-id="d210b-149">此属性是对 Analysis Services 仅返回非空记录的优化提示。</span><span class="sxs-lookup"><span data-stu-id="d210b-149">This property is an optimization hint to Analysis Services to return only non-NULL records.</span></span> <span data-ttu-id="d210b-150">只返回非空记录可提高使用 NON EMPTY 运算符或 NonEmpty 函数或者需要计算单元值的 MDX 查询的性能。</span><span class="sxs-lookup"><span data-stu-id="d210b-150">Returning only non-NULL records improves the performance of MDX queries that utilize the NON EMPTY operator or the NonEmpty function, or that require the calculation of cell values.</span></span> <span data-ttu-id="d210b-151">为使单元计算取得最佳性能，应尽可能只指定一个成员。</span><span class="sxs-lookup"><span data-stu-id="d210b-151">For best performance with cell calculations, specify only a single member when possible.</span></span>  
  
 <span data-ttu-id="d210b-152">颜色表达式</span><span class="sxs-lookup"><span data-stu-id="d210b-152">Color Expressions</span></span>  
 <span data-ttu-id="d210b-153">指定基于计算成员的值动态设置单元前景色和背景色的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="d210b-153">Specifies MDX expressions that dynamically set the foreground and background colors of cells based on the value of the calculated member.</span></span> <span data-ttu-id="d210b-154">如果客户端应用程序不支持此属性，将忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="d210b-154">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="d210b-155">字体表达式</span><span class="sxs-lookup"><span data-stu-id="d210b-155">Font Expressions</span></span>  
 <span data-ttu-id="d210b-156">指定基于计算成员的值动态设置单元的字体、字号和字体属性的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="d210b-156">Specifies MDX expressions that dynamically set the font, font size, and font attributes for cells based on the value of the calculated member.</span></span> <span data-ttu-id="d210b-157">如果客户端应用程序不支持此属性，将忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="d210b-157">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="d210b-158">您可以将多维数据集组件从 **“计算工具”** 窗格的 **“元数据”** 选项卡拖动或复制到“计算表达式”窗格的 **“表达式”** 框中。</span><span class="sxs-lookup"><span data-stu-id="d210b-158">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span> <span data-ttu-id="d210b-159">您可以将函数从 **“计算工具”** 窗格的 **“函数”** 选项卡拖动或复制到“计算表达式”窗格的 **“表达式”** 框中。</span><span class="sxs-lookup"><span data-stu-id="d210b-159">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span>  
  
## <a name="addressing-calculated-members"></a><span data-ttu-id="d210b-160">寻址计算成员</span><span class="sxs-lookup"><span data-stu-id="d210b-160">Addressing Calculated Members</span></span>  
 <span data-ttu-id="d210b-161">在 **“多维数据集设计器”** 的 **“计算”** 选项卡中创建计算成员时，需要指定在其中存储计算成员的父层次结构。</span><span class="sxs-lookup"><span data-stu-id="d210b-161">When you create a calculated member on the **Calculations** tab of **Cube Designer**, you specify the parent hierarchy in which the calculated member is stored.</span></span> <span data-ttu-id="d210b-162">父层次结构按以下规则确定如何为计算成员寻址：</span><span class="sxs-lookup"><span data-stu-id="d210b-162">The parent hierarchy determines how a calculated member can be addressed, according to the following rules:</span></span>  
  
-   <span data-ttu-id="d210b-163">如果计算成员是在度量值维度中创建的，则计算成员在该维度中是可寻址的。</span><span class="sxs-lookup"><span data-stu-id="d210b-163">If a calculated member is created in the measures dimension, the calculated member is addressable in that dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d210b-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d210b-164">See Also</span></span>  
 [<span data-ttu-id="d210b-165">多维模型中的计算</span><span class="sxs-lookup"><span data-stu-id="d210b-165">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
