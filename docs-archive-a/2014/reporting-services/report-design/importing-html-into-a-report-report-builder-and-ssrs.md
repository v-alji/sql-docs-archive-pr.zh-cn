---
title: 将 HTML 导入报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dd0410ea-8839-4e8c-9944-8cdfe5465591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f978e67c67556184012db6b809e4f5754f2374c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688576"
---
# <a name="importing-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="422ff-102">将 HTML 导入报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="422ff-102">Importing HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="422ff-103">可以使用文本框向报表中插入从数据集字段中检索到的 HTML 格式的文本。</span><span class="sxs-lookup"><span data-stu-id="422ff-103">You can use a text box to insert HTML-formatted text that you have retrieved from a field in your dataset into a report.</span></span> <span data-ttu-id="422ff-104">文本可以来自于其计算结果为正确格式的 HTML 的任何简单或复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="422ff-104">The text can come from any simple or complex expression that evaluates to correctly formatted HTML.</span></span> <span data-ttu-id="422ff-105">格式化文本可以呈现为支持的所有输出格式，包括 PDF。</span><span class="sxs-lookup"><span data-stu-id="422ff-105">Formatted text can be rendered to all supported output formats, including PDF.</span></span>  
  
 <span data-ttu-id="422ff-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span><span class="sxs-lookup"><span data-stu-id="422ff-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span></span>  
  
 <span data-ttu-id="422ff-107">下图显示了在报表设计视图中显示 HTML 格式的文本，以及在运行报表时所呈现的相同文本。</span><span class="sxs-lookup"><span data-stu-id="422ff-107">This illustration shows text with HTML formatting in report design view, and the same text as it is rendered when the report is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="422ff-108">导入包含 HTML 标记的文本时，文本框必须始终首先分析数据。</span><span class="sxs-lookup"><span data-stu-id="422ff-108">When you import text that contains HTML markup, the data must always be parsed by the text box first.</span></span> <span data-ttu-id="422ff-109">由于仅支持 HTML 标记的子集，因此在呈现报表中显示的 HTML 可能不同于您的原始 HTML。</span><span class="sxs-lookup"><span data-stu-id="422ff-109">Because only a subset of HTML tags is supported, the HTML that is shown in the rendered report may differ from your original HTML.</span></span>  
  
 <span data-ttu-id="422ff-110">若要快速开始使用，请参阅[教程：设置文本格式（报表生成器）](../tutorial-format-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="422ff-110">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="supported-html-tags"></a><span data-ttu-id="422ff-111">支持的 HTML 标记</span><span class="sxs-lookup"><span data-stu-id="422ff-111">Supported HTML Tags</span></span>  
 <span data-ttu-id="422ff-112">以下是作为占位符文本定义时将呈现为 HTML 标记的完整列表：</span><span class="sxs-lookup"><span data-stu-id="422ff-112">The following is a complete list of tags that will render as HTML when defined as placeholder text:</span></span>  
  
-   <span data-ttu-id="422ff-113">标头、样式和块元素： \<H{n}> 、 \<DIV> 、 \<SPAN> 、 \<P> 、\<LI></span><span class="sxs-lookup"><span data-stu-id="422ff-113">Header, style and block elements: \<H{n}>, \<DIV>, \<SPAN>,\<P>, \<LI></span></span>  
  
 <span data-ttu-id="422ff-114">在报表处理期间，将忽略任何其他 HTML 标记。</span><span class="sxs-lookup"><span data-stu-id="422ff-114">Any other HTML markup tags will be ignored during report processing.</span></span> <span data-ttu-id="422ff-115">如果占位符文本中表达式所表示的 HTML 格式不正确，则将占位符呈现为纯文本。</span><span class="sxs-lookup"><span data-stu-id="422ff-115">If the HTML represented by the expression in the placeholder text is not well formed, the placeholder is rendered as plain text.</span></span> <span data-ttu-id="422ff-116">所有 HTML 标记都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="422ff-116">All HTML tags are case-insensitive.</span></span>  
  
 <span data-ttu-id="422ff-117">如果文本框中的文本仅包含一个文本块，将以正确方式呈现占位符中用于定义块元素的任何 HTML。</span><span class="sxs-lookup"><span data-stu-id="422ff-117">If the text in your text box contains only one block of text, any HTML in the placeholder that defines block elements will render correctly.</span></span> <span data-ttu-id="422ff-118">但是，如果文本框具有多个文本块，则忽略 HTML 标记，并通过文本块定义文本结构。</span><span class="sxs-lookup"><span data-stu-id="422ff-118">However, if the text box has multiple blocks of text, the HTML tags are ignored and the structure of the text is defined by the blocks of text.</span></span>  
  
 <span data-ttu-id="422ff-119">如果为文本定义了一个以上的标记，并且 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 检测到 HTML 与现有报表约束冲突，则只有最内部的 HTML 标记被视为 HTML。</span><span class="sxs-lookup"><span data-stu-id="422ff-119">If more than one tag is defined for text, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] detects a conflict between the HTML and existing report constraints, only the innermost HTML tag will be treated as HTML.</span></span>  
  
 <span data-ttu-id="422ff-120">使用列表处理标签时，所有项目符号和数字前缀的字体和样式都固定采用 Arial 黑色。</span><span class="sxs-lookup"><span data-stu-id="422ff-120">When using the list handling tags, the font and style of all bullets and number prefixes will be fixed to Arial black.</span></span>  
  
 <span data-ttu-id="422ff-121">有关详细信息，请参阅[向报表添加 HTML（报表生成器和 SSRS）](add-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="422ff-121">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="limitations-of-cascading-style-sheet-attributes"></a><span data-ttu-id="422ff-122">级联样式表属性的限制</span><span class="sxs-lookup"><span data-stu-id="422ff-122">Limitations of Cascading Style Sheet Attributes</span></span>  
 <span data-ttu-id="422ff-123">使用级联样式表 (CSS) 属性时，仅定义一组基本标记。</span><span class="sxs-lookup"><span data-stu-id="422ff-123">When using cascading style sheet (CSS) attributes, only a basic set of tags are defined.</span></span> <span data-ttu-id="422ff-124">以下是支持的属性列表：</span><span class="sxs-lookup"><span data-stu-id="422ff-124">The following is a list of attributes that are supported:</span></span>  
  
-   <span data-ttu-id="422ff-125">text-align、text-indent</span><span class="sxs-lookup"><span data-stu-id="422ff-125">text-align, text-indent</span></span>  
  
-   <span data-ttu-id="422ff-126">font-family</span><span class="sxs-lookup"><span data-stu-id="422ff-126">font-family</span></span>  
  
-   <span data-ttu-id="422ff-127">font-size</span><span class="sxs-lookup"><span data-stu-id="422ff-127">font-size</span></span>  
  
    -   <span data-ttu-id="422ff-128">仅支持采用绝对 CSS 长度单位的有效 RDL 大小值。</span><span class="sxs-lookup"><span data-stu-id="422ff-128">Only valid RDL size values, in absolute CSS length units are supported.</span></span> <span data-ttu-id="422ff-129">支持的单位为：in、cm、mm、pt、pc。</span><span class="sxs-lookup"><span data-stu-id="422ff-129">Supported units are: in, cm, mm, pt, pc.</span></span>  
  
    -   <span data-ttu-id="422ff-130">忽略相对 CSS 长度单位，不支持它们。</span><span class="sxs-lookup"><span data-stu-id="422ff-130">Relative CSS length units are ignored and not supported.</span></span> <span data-ttu-id="422ff-131">不支持的单位包括 em、ex、px、%、rem。</span><span class="sxs-lookup"><span data-stu-id="422ff-131">Unsupported units include em, ex, px,%,rem.</span></span>  
  
-   <span data-ttu-id="422ff-132">color</span><span class="sxs-lookup"><span data-stu-id="422ff-132">color</span></span>  
  
-   <span data-ttu-id="422ff-133">padding、padding-bottom、padding-top、padding-right、padding-left</span><span class="sxs-lookup"><span data-stu-id="422ff-133">padding, padding-bottom, padding-top, padding-right, padding-left</span></span>  
  
-   <span data-ttu-id="422ff-134">font-weight</span><span class="sxs-lookup"><span data-stu-id="422ff-134">font-weight</span></span>  
  
 <span data-ttu-id="422ff-135">以下是使用 CSS 的一些注意事项：</span><span class="sxs-lookup"><span data-stu-id="422ff-135">Here are some considerations for using CSS:</span></span>  
  
-   <span data-ttu-id="422ff-136">格式不正确的 CSS 值和 HTML 的忽略方式相同。</span><span class="sxs-lookup"><span data-stu-id="422ff-136">Malformed CSS values are ignored in the same way as malformed HTML.</span></span>  
  
-   <span data-ttu-id="422ff-137">如果同一标记中存在特性和 CSS 样式特性，则 CSS 属性具有较高优先级。</span><span class="sxs-lookup"><span data-stu-id="422ff-137">When both attribute and CSS style attributes exist in the same tag, the CSS property has a higher precedence.</span></span> <span data-ttu-id="422ff-138">例如，如果文本为，则 **\<p style="text-align: right" align="left">** 只会应用文本对齐属性，并将文本右对齐。</span><span class="sxs-lookup"><span data-stu-id="422ff-138">For example, if your text is **\<p style="text-align: right" align="left">**, only the text-align attribute will be applied and the text will be right-aligned.</span></span>  
  
-   <span data-ttu-id="422ff-139">对于特性和 CSS 样式，如果多次指定某一属性，则仅应用该属性的最后一个实例。</span><span class="sxs-lookup"><span data-stu-id="422ff-139">For attributes and CSS styles, if a property is specified more than once, only the last instance of the property is applied.</span></span> <span data-ttu-id="422ff-140">例如，如果文本为 **\<p align="left" align="right">** ，则文本将为右对齐。</span><span class="sxs-lookup"><span data-stu-id="422ff-140">For example, if your text is **\<p align="left" align="right">**, the text will be right-aligned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="422ff-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="422ff-141">See Also</span></span>  
 [<span data-ttu-id="422ff-142">以 HTML 格式呈现（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="422ff-142">Rendering to HTML &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/rendering-to-html-report-builder-and-ssrs.md)  
  
  
