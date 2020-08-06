---
title: 文本框（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10134"
- sql12.rtp.rptdesigner.textproperties.general.f1
- "10120"
- sql12.rtp.rptdesigner.textboxproperties.general.f1
ms.assetid: df49e4e3-f279-4c63-a03b-b70c095f4ba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3bc9d9d645fe2a966197af9059eb90c64ce3954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586344"
---
# <a name="text-boxes-report-builder-and-ssrs"></a><span data-ttu-id="b4d8b-102">文本框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4d8b-102">Text Boxes (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b4d8b-103">在您考虑一个文本框时，可能要考虑在类似 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint 的图面上包含文本的独立框。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-103">When you think of a text box, you probably think of a stand-alone box containing text on a surface like [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint.</span></span> <span data-ttu-id="b4d8b-104">在报表生成器中，某些文本类似上述文本框，它们可显示标题、说明和标签的文字文本，或者基于表达式显示动态文本。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-104">In Report Builder, some text boxes are like that, and they can display literal text for titles, descriptions, and labels, or dynamic text based on expressions.</span></span> <span data-ttu-id="b4d8b-105">但表或矩阵（tablix 数据区域）中的每个单元也都包含文本框，可以使用您的报表中独立文本框的格式设置方式来设置这些文本框的格式。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-105">But every cell in a table or matrix (a tablix data region) also contains a text box, which can be formatted in the same way as stand-alone text boxes in your report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4d8b-106">如果将报表数据集字段值直接拖到报表设计图面或报表设计图面上的文本框中，则在运行报表时只能看到结果集中的第一个值。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-106">If you drag a report dataset field value directly to the report design surface, or to a text box on the report design surface, you only see the first value in the result set when you run the report.</span></span> <span data-ttu-id="b4d8b-107">若要看到某个字段的所有值，必须将该字段拖到表或矩阵内的单元中。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-107">To see all the values for a field, you must drag the field to a cell in a table or matrix.</span></span> <span data-ttu-id="b4d8b-108">这样，在您运行报表时，将看到该字段中的所有值。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-108">That way, when you run the report, you will see all the values in that field.</span></span>  
  
 <span data-ttu-id="b4d8b-109">若要以自由格式布局显示重复的文本，请在列表数据区域中放置一个文本框。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-109">To show repeating text in a free-form layout, place a text box in a list data region.</span></span> <span data-ttu-id="b4d8b-110">如果想对多个值重复某窗体，例如为每个客户重复一次客户发票窗体，请使用列表。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-110">Use a list when you want to repeat a form for multiple values, for example, a customer invoice form repeated once for each customer.</span></span> <span data-ttu-id="b4d8b-111">有关详细信息，请参阅[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-111">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b4d8b-112">如果想控制文本框布局和最后一个文本框下面的空白，请使用矩形容器。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-112">Use a rectangle container when you want to control the text box layout and white space below the last text box.</span></span> <span data-ttu-id="b4d8b-113">有关详细信息，请参阅[矩形和线条（报表生成器和 SSRS）](rectangles-and-lines-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-113">For more information, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b4d8b-114">文本框中的表达式可以包含文字文本、指向数据库中的字段或用来计算数据。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-114">The expressions in a text box can contain literal text, point to a field in the database, or calculate data.</span></span> <span data-ttu-id="b4d8b-115">所有表达式都显示为占位符文本，这样您就可以设置数字、颜色以及其他外观属性的格式。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-115">All expressions are shown as placeholder text so that you can format numbers, colors, and other appearance properties.</span></span> <span data-ttu-id="b4d8b-116">您还可以在同一文本框中将占位符与文字文本合并在一起。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-116">You can also combine placeholders with literal text in the same text box.</span></span>  
  
 <span data-ttu-id="b4d8b-117">您可以在任何单个文本框中以多种字体、颜色、样式和操作设置文本格式。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-117">You can format text in any single text box with multiple fonts, colors, styles, and actions.</span></span> <span data-ttu-id="b4d8b-118">有关详细信息，请参阅 [设置文本和占位符的格式（报表生成器和 SSRS）](formatting-text-and-placeholders-report-builder-and-ssrs.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-118">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="growing-and-shrinking-a-text-box"></a><a name="GrowShrinkTextBox"></a> <span data-ttu-id="b4d8b-119">扩大和收缩文本框</span><span class="sxs-lookup"><span data-stu-id="b4d8b-119">Growing and Shrinking a Text Box</span></span>  
 <span data-ttu-id="b4d8b-120">默认情况下，文本框的大小是固定的。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-120">By default, text boxes are a fixed size.</span></span> <span data-ttu-id="b4d8b-121">您可以允许文本框基于其内容垂直收缩或扩展。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-121">You can allow a text box to shrink or expand vertically based on its contents.</span></span> <span data-ttu-id="b4d8b-122">有关详细信息，请参阅 [允许文本框扩大或收缩（报表生成器和 SSRS）](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-122">For more information, see [Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md).</span></span>  
  
## <a name="orienting-a-text-box"></a><span data-ttu-id="b4d8b-123">确定文本框的方向</span><span class="sxs-lookup"><span data-stu-id="b4d8b-123">Orienting a Text Box</span></span>  
 <span data-ttu-id="b4d8b-124">确定文本框的方向可以帮助您创建更具可读性的报表、支持区域设置特定的文本方向、在具有固定页面大小的打印报表中放置更多的列，以及创建具有更吸引人的图形的报表。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-124">Orienting text boxes can help you create more readable reports, support locale-specific text orientation, fit more columns on a printed report that has fixed page size, and create reports with more graphical appeal.</span></span> <span data-ttu-id="b4d8b-125">文本框可采用不同的方向：水平、垂直或旋转 270 度。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-125">A text box can be oriented in different directions: horizontal, vertical, or rotated by 270 degrees.</span></span> <span data-ttu-id="b4d8b-126">垂直选项最常用于从上到下书写的东亚语言。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-126">The vertical option is most commonly used for East Asian languages that are written top to bottom.</span></span> <span data-ttu-id="b4d8b-127">在大多数呈现器中，垂直选项处理标志符号旋转属性，以便文本从上到下书写，但字符不在其两侧上。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-127">In most renderers the vertical option handles the glyph rotation property so that the text is written top to bottom, but the characters are not on their sides.</span></span> <span data-ttu-id="b4d8b-128">对于其他语言，在垂直和 270 度选项中，以横向书写文本。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-128">For other languages, in the vertical and 270-degree options the text is written sideways.</span></span>  
  
 <span data-ttu-id="b4d8b-129">您可以将方向应用于包含文字文本、来自报表数据集的字段或计算列的文本框。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-129">You can apply orientation to text boxes that contain literal text, fields from a report dataset, or calculated data.</span></span> <span data-ttu-id="b4d8b-130">在报表主体、表或矩阵或者报表页眉和页脚中，文本框可以是独立的。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-130">The text box can be stand-alone in the report body, in a table or matrix, or in a report header and footer.</span></span>  
  
 <span data-ttu-id="b4d8b-131">下图显示按月对数据进行分组的表报表的三个版本。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-131">The following picture shows three versions of a table report that groups data by month.</span></span> <span data-ttu-id="b4d8b-132">包含月份值的文本框使用不同的文本框方向。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-132">The text box that contains the month value uses a different text box orientation.</span></span>  
  
 <span data-ttu-id="b4d8b-133">![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")</span><span class="sxs-lookup"><span data-stu-id="b4d8b-133">![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")</span></span>  
  
 <span data-ttu-id="b4d8b-134">方向是对文本框设置的并且适用于文本框中的所有文本。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-134">Orientation is set on the text box and applies to all the text in the box.</span></span> <span data-ttu-id="b4d8b-135">不能为文本框的各个部分指定不同的方向。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-135">You cannot specify a different orientation for parts of the text box.</span></span>  
  
 <span data-ttu-id="b4d8b-136">若要快速开始更改文本方向，请参阅教程中有关旋转文本的部分[：设置文本格式 &#40;报表生成器&#41;](../tutorial-format-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-136">To quickly get started with changing text orientation, see the section on rotating text in the [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span> <span data-ttu-id="b4d8b-137">有关详细信息，请参阅[设置文本框方向 &#40;报表生成器和 SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d8b-137">For more information, see [Set Text Box Orientation &#40;Report Builder and SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="b4d8b-138">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="b4d8b-138">How-To Topics</span></span>  
 [<span data-ttu-id="b4d8b-139">添加、移动或删除文本框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4d8b-139">Add, Move, or Delete a Text Box &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-text-box-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="b4d8b-140">设置文本框中文本的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4d8b-140">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="b4d8b-141">设置文本框方向（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4d8b-141">Set Text Box Orientation &#40;Report Builder and SSRS&#41;</span></span>](set-text-box-orientation-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="b4d8b-142">允许文本框扩大或收缩（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4d8b-142">Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;</span></span>](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4d8b-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4d8b-143">See Also</span></span>  
 <span data-ttu-id="b4d8b-144">[设置文本和占位符的格式 &#40;报表生成器和 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4d8b-144">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b4d8b-145">设置数字和日期格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4d8b-145">Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;</span></span>](formatting-numbers-and-dates-report-builder-and-ssrs.md)  
  
  
