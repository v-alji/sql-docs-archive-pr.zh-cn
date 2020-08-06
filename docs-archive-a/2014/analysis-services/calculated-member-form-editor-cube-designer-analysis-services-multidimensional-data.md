---
title: 计算成员窗体编辑器 (计算 "选项卡、多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dd45ece03fd81e0e7356e7bdcd0ec8dc53287bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579285"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="fa02f-102">计算成员窗体编辑器（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fa02f-102">Calculated Member Form Editor (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fa02f-103">可以使用多维数据集设计器中的 **“计算”** 选项卡上的 **“计算成员窗体编辑器”** 窗格创建或修改计算成员。</span><span class="sxs-lookup"><span data-stu-id="fa02f-103">Use the **Calculated Member Form Editor** pane on the **Calculations** tab in Cube Designer to create or modify a calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-104">**注意** 此窗格仅显示在窗体视图中。</span><span class="sxs-lookup"><span data-stu-id="fa02f-104">**Note** This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa02f-105">选项</span><span class="sxs-lookup"><span data-stu-id="fa02f-105">Options</span></span>  
 <span data-ttu-id="fa02f-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="fa02f-106">**Name**</span></span>  
 <span data-ttu-id="fa02f-107">键入计算成员的名称。</span><span class="sxs-lookup"><span data-stu-id="fa02f-107">Type the name of the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-108">**父属性**</span><span class="sxs-lookup"><span data-stu-id="fa02f-108">**Parent Properties**</span></span>  
 <span data-ttu-id="fa02f-109">展开此项可以查看“父层次结构”、“父成员”和“更改”选项\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa02f-109">Expand to view the **Parent hierarchy**, **Parent member**, and **Change** options.</span></span>  
  
 <span data-ttu-id="fa02f-110">**父层次结构**</span><span class="sxs-lookup"><span data-stu-id="fa02f-110">**Parent hierarchy**</span></span>  
 <span data-ttu-id="fa02f-111">在选定的多维数据集中选择要包含计算成员的维度和层次结构。</span><span class="sxs-lookup"><span data-stu-id="fa02f-111">Select the dimension and hierarchy in the selected cube that is to include the calculated member.</span></span> <span data-ttu-id="fa02f-112">选择 MEASURES 可以定义计算度量值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-112">Select MEASURES to define a calculated measure.</span></span>  
  
 <span data-ttu-id="fa02f-113">**父成员**</span><span class="sxs-lookup"><span data-stu-id="fa02f-113">**Parent member**</span></span>  
 <span data-ttu-id="fa02f-114">选择在其下面将显示计算成员的成员。</span><span class="sxs-lookup"><span data-stu-id="fa02f-114">Select the member beneath which the calculated member is to appear.</span></span>  
  
 <span data-ttu-id="fa02f-115">**注意** 只有在 **“父层次结构”** 指定了 MEASURES 以外的层次结构时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="fa02f-115">**Note** This option is available if **Parent hierarchy** specifies a hierarchy other than MEASURES.</span></span>  
  
 <span data-ttu-id="fa02f-116">**更改**</span><span class="sxs-lookup"><span data-stu-id="fa02f-116">**Change**</span></span>  
 <span data-ttu-id="fa02f-117">选择此项可以显示“选择父成员”对话框并为“父成员”选择成员\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa02f-117">Select to display the **Select Parent Member** dialog box and choose a member for **Parent member**.</span></span> <span data-ttu-id="fa02f-118">有关\*\*\*\*“选择父成员”对话框的详细信息，请参阅[“选择父成员”对话框（Analysis Services - 多维数据）](select-parent-member-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-118">For more information about the **Select Parent Member** dialog box, see [Select Parent Member Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="fa02f-119">**表达式**</span><span class="sxs-lookup"><span data-stu-id="fa02f-119">**Expression**</span></span>  
 <span data-ttu-id="fa02f-120">展开此项可以查看或编辑计算成员的多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="fa02f-120">Expand to view or edit the Multidimensional Expressions (MDX) expression for the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-121">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fa02f-121">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa02f-122">建议此表达式的计算结果为字符串或数值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-122">It is recommended that this expression evaluate to a string or to a numeric value.</span></span>  
  
 <span data-ttu-id="fa02f-123">**其他属性**</span><span class="sxs-lookup"><span data-stu-id="fa02f-123">**Additional Properties**</span></span>  
 <span data-ttu-id="fa02f-124">展开此项可以查看“格式字符串”、“可见”、“非空行为”、“颜色表达式”和“字体表达式”选项\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa02f-124">Expand to view the **Format string**, **Visible**, **Non-empty behavior**, **Color Expressions**, and **Font Expressions** options.</span></span>  
  
 <span data-ttu-id="fa02f-125">**格式字符串**</span><span class="sxs-lookup"><span data-stu-id="fa02f-125">**Format string**</span></span>  
 <span data-ttu-id="fa02f-126">键入用于对计算成员所返回的值进行格式设置的 MDX 格式字符串，或选择预定义的格式字符串。</span><span class="sxs-lookup"><span data-stu-id="fa02f-126">Type the MDX format string used to format the value returned by the calculated member, or select a predefined format string.</span></span>  
  
 <span data-ttu-id="fa02f-127">有关 MDX 格式字符串的详细信息，请参阅 [FORMAT_STRING 内容 (MDX)](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-127">For more information about MDX format strings, see [FORMAT_STRING Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).</span></span>  
  
 <span data-ttu-id="fa02f-128">**可见**</span><span class="sxs-lookup"><span data-stu-id="fa02f-128">**Visible**</span></span>  
 <span data-ttu-id="fa02f-129">选择 **True** 将允许计算成员对客户端应用程序可见。</span><span class="sxs-lookup"><span data-stu-id="fa02f-129">Select **True** to allow the calculated member to be visible to client applications.</span></span>  
  
 <span data-ttu-id="fa02f-130">**非空行为**</span><span class="sxs-lookup"><span data-stu-id="fa02f-130">**Non-empty behavior**</span></span>  
 <span data-ttu-id="fa02f-131">选择用于为计算成员解析 MDX 中的 NON EMPTY 查询的度量值名称。</span><span class="sxs-lookup"><span data-stu-id="fa02f-131">Select the name of the measure used to resolve NON EMPTY queries in MDX for the calculated member.</span></span> <span data-ttu-id="fa02f-132">如果 **“非空行为”** 属性为空白，则必须对计算成员进行反复计算以确定成员是否为空。</span><span class="sxs-lookup"><span data-stu-id="fa02f-132">If the **Non Empty Behavior** property is blank, the calculated member must be evaluated repeatedly to determine if a member is empty.</span></span> <span data-ttu-id="fa02f-133">如果 **“非空行为”** 属性包含度量值的名称，则在指定的度量值为空的情况下将计算成员视为空。</span><span class="sxs-lookup"><span data-stu-id="fa02f-133">If the **Non Empty Behavior** property contains the name of a measure, the calculated member is treated as empty if the specified measure is empty.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fa02f-134">此属性已弃用。</span><span class="sxs-lookup"><span data-stu-id="fa02f-134">This property is deprecated.</span></span> <span data-ttu-id="fa02f-135">避免将其设置。</span><span class="sxs-lookup"><span data-stu-id="fa02f-135">Avoid setting it.</span></span> <span data-ttu-id="fa02f-136">有关详细信息，请参阅[SQL Server 2014 中不推荐使用的 Analysis Services 功能](deprecated-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-136">See [Deprecated Analysis Services Features in SQL Server 2014](deprecated-analysis-services-features-in-sql-server-2014.md) for details.</span></span>  
  
 <span data-ttu-id="fa02f-137">**颜色表达式**</span><span class="sxs-lookup"><span data-stu-id="fa02f-137">**Color Expressions**</span></span>  
 <span data-ttu-id="fa02f-138">展开此项可以查看“前景色”和“背景色”选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa02f-138">Expand to view the **Fore color** and **Back color** options.</span></span>  
  
 <span data-ttu-id="fa02f-139">**前景色**</span><span class="sxs-lookup"><span data-stu-id="fa02f-139">**Fore color**</span></span>  
 <span data-ttu-id="fa02f-140">键入提供计算成员的前景色的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="fa02f-140">Type the MDX expression that provides the foreground color of the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-141">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fa02f-141">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fa02f-142">单击颜色选择按钮可显示\*\*\*\*“颜色”对话框，使用该对话框可以向 MDX 表达式中插入指定颜色的 RGB（红-绿-蓝）值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-142">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="fa02f-143">有关 RGB 值的详细信息，请参阅 [FORE_COLOR 和 BACK_COLOR 内容 (MDX)](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-143">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="fa02f-144">**背景色**</span><span class="sxs-lookup"><span data-stu-id="fa02f-144">**Back color**</span></span>  
 <span data-ttu-id="fa02f-145">键入提供计算成员的背景色的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="fa02f-145">Type the MDX expression that provides the background color of the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-146">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fa02f-146">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fa02f-147">单击颜色选择按钮可显示\*\*\*\*“颜色”对话框，使用该对话框可以向 MDX 表达式中插入指定颜色的 RGB（红-绿-蓝）值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-147">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="fa02f-148">有关 RGB 值的详细信息，请参阅 [FORE_COLOR 和 BACK_COLOR 内容 (MDX)](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-148">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="fa02f-149">**字体表达式**</span><span class="sxs-lookup"><span data-stu-id="fa02f-149">**Font Expressions**</span></span>  
 <span data-ttu-id="fa02f-150">展开此项可以查看“字体名称”、“字号”和“字体标志”选项\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa02f-150">Expand to view the **Font name**, **Font size**, and **Font flags** options.</span></span>  
  
 <span data-ttu-id="fa02f-151">**字体名称**</span><span class="sxs-lookup"><span data-stu-id="fa02f-151">**Font name**</span></span>  
 <span data-ttu-id="fa02f-152">键入提供计算成员所用字体名称的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="fa02f-152">Type the MDX expression that provides the name of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-153">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fa02f-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fa02f-154">单击字体选择按钮可显示 **“字体”** 对话框，使用该对话框可以向 MDX 表达式中插入指定字体的属性值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-154">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="fa02f-155">有关属性值的详细信息，请参阅[创建和使用属性值 (MDX)](creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-155">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="fa02f-156">**字号**</span><span class="sxs-lookup"><span data-stu-id="fa02f-156">**Font size**</span></span>  
 <span data-ttu-id="fa02f-157">键入提供计算成员所用字体大小的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="fa02f-157">Type the MDX expression that provides the size of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-158">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fa02f-158">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fa02f-159">单击字体选择按钮可显示 **“字体”** 对话框，使用该对话框可以向 MDX 表达式中插入指定字体的属性值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-159">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="fa02f-160">有关属性值的详细信息，请参阅[创建和使用属性值 (MDX)](creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-160">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="fa02f-161">**字体标志**</span><span class="sxs-lookup"><span data-stu-id="fa02f-161">**Font flags**</span></span>  
 <span data-ttu-id="fa02f-162">键入提供计算成员所用字体的位图化值（包含下划线或加粗等之类的字体标志）的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="fa02f-162">Type the MDX expression that provides the bitmapped value containing the font flags, such as underline or bold, of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="fa02f-163">将所选元素从 **“计算工具”** 窗格拖至此选项中，可包含所选元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="fa02f-163">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fa02f-164">单击字体选择按钮可显示 **“字体”** 对话框，使用该对话框可以向 MDX 表达式中插入指定字体的属性值。</span><span class="sxs-lookup"><span data-stu-id="fa02f-164">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="fa02f-165">有关属性值的详细信息，请参阅[创建和使用属性值 (MDX)](creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="fa02f-165">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa02f-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa02f-166">See Also</span></span>  
 <span data-ttu-id="fa02f-167">[考虑](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-167">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="fa02f-168">[创建计算成员](multidimensional-models/create-calculated-members.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-168">[Create Calculated Members](multidimensional-models/create-calculated-members.md) </span></span>  
 <span data-ttu-id="fa02f-169">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-169">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fa02f-170">[多维数据集设计器&#41; &#40;&#40;计算 Analysis Services 多维数据&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-170">[Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fa02f-171">[工具栏 &#40;"计算" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-171">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fa02f-172">[脚本组织程序 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-172">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fa02f-173">[计算工具 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-173">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fa02f-174">[命名集窗体编辑器 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa02f-174">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fa02f-175">脚本编辑器 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="fa02f-175">Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
