---
title: 向报表添加书签（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f130562e-5673-40e3-8e01-de7227a21d41
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fae543dd1b071ff38853637a3da57ffd2410c3a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692738"
---
# <a name="add-a-bookmark-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="389e8-102">向报表添加书签（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="389e8-102">Add a Bookmark to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="389e8-103">若要在报表中提供自定义目录或自定义内部导航链接，可以向报表中添加书签或书签链接。</span><span class="sxs-lookup"><span data-stu-id="389e8-103">Add bookmarks and bookmark links to a report when you want to provide a customized table of contents or to provide customized internal navigation links in the report.</span></span> <span data-ttu-id="389e8-104">通常情况下，如果要引导用户到报表中的某一位置，例如表、图表以及表或矩阵中显示的唯一组值，可以向该位置添加书签。</span><span class="sxs-lookup"><span data-stu-id="389e8-104">Typically, you add bookmarks to locations in the report to which you want to direct users, such as to each table or chart or to the unique group values displayed in a table or matrix.</span></span> <span data-ttu-id="389e8-105">可以创建用作书签的字符串；或者，对于组而言，可以将书签设置为组表达式。</span><span class="sxs-lookup"><span data-stu-id="389e8-105">You can create your own strings to use as bookmarks, or, for groups, you can set the bookmark to the group expression.</span></span>  
  
 <span data-ttu-id="389e8-106">创建书签后，可以添加用户通过单击即可转到书签的报表项。</span><span class="sxs-lookup"><span data-stu-id="389e8-106">After you create bookmarks, you can add report items that the user can click to go to each bookmark.</span></span> <span data-ttu-id="389e8-107">这些项通常为文本框或图像。</span><span class="sxs-lookup"><span data-stu-id="389e8-107">These items are typically text boxes or images.</span></span>  
  
 <span data-ttu-id="389e8-108">例如，如果报表显示按颜色分组的表，则可以向组头中添加基于组表达式的书签。</span><span class="sxs-lookup"><span data-stu-id="389e8-108">For example, if your report displays a table grouped by color, you would add a bookmark based on the group expression to the group header.</span></span> <span data-ttu-id="389e8-109">然后，即可在报表的开头处添加带有显示颜色值的单个文本框的表，并在该文本框上设置书签链接。</span><span class="sxs-lookup"><span data-stu-id="389e8-109">Then you would add a table with a single text box at the beginning of the report that displayed the color values, and set the bookmark link on that text box.</span></span> <span data-ttu-id="389e8-110">单击某种颜色时，报表就会跳至显示具有该颜色的组头行的页。</span><span class="sxs-lookup"><span data-stu-id="389e8-110">When you click the color, the report jumps to the page that displays the group header row for that color.</span></span>  
  
 <span data-ttu-id="389e8-111">可以向任何报表项添加书签，也可以向具有 **“操作”** 属性的任何项添加书签链接，例如文本框、图像或图表中的计算序列。</span><span class="sxs-lookup"><span data-stu-id="389e8-111">You can add a bookmark to any report item and add a bookmark link to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="389e8-112">有关详细信息，请参阅[“操作属性”对话框（报表生成器和 SSRS）](../action-properties-dialog-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="389e8-112">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-bookmark"></a><span data-ttu-id="389e8-113">添加书签</span><span class="sxs-lookup"><span data-stu-id="389e8-113">To add a bookmark</span></span>  
  
1.  <span data-ttu-id="389e8-114">在报表设计视图中，选择要向其添加书签的文本框、图像、图表或其他报表项。</span><span class="sxs-lookup"><span data-stu-id="389e8-114">In report design view, select the text box, image, chart, or other report item to which you want to add a bookmark.</span></span> <span data-ttu-id="389e8-115">所选项的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="389e8-115">The properties for the selected item appear in the Properties pane.</span></span>  
  
2.  <span data-ttu-id="389e8-116">在 **“书签”** 旁的文本框中，键入作为此书签的标签的字符串。</span><span class="sxs-lookup"><span data-stu-id="389e8-116">In the text box next to **Bookmark**, type a string that is the label for this bookmark.</span></span> <span data-ttu-id="389e8-117">例如，可以键入 **BikePhoto** 作为报表中图像的书签。</span><span class="sxs-lookup"><span data-stu-id="389e8-117">For example, you could type **BikePhoto** as the bookmark for an image in your report.</span></span> <span data-ttu-id="389e8-118">此外，也可以单击表达式 (fx) 按钮打开“表达式”对话框，指定一个计算结果为标签的表达式   。</span><span class="sxs-lookup"><span data-stu-id="389e8-118">Alternatively, click the Expression (**fx**) button to open the **Expression** dialog box to specify an expression that evaluates to a label.</span></span> <span data-ttu-id="389e8-119">对于组，键入的表达式应为组表达式。</span><span class="sxs-lookup"><span data-stu-id="389e8-119">For a group, the expression you type should be the group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="389e8-120">书签可以为任意字符串，但在报表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="389e8-120">The bookmark can be any string, but it must be unique in the report.</span></span> <span data-ttu-id="389e8-121">如果书签不是唯一的，则指向该书签的链接将跳至第一个匹配书签。</span><span class="sxs-lookup"><span data-stu-id="389e8-121">If the bookmark is not unique, a link to the bookmark finds the first matching bookmark.</span></span>  
  
### <a name="to-add-a-bookmark-link"></a><span data-ttu-id="389e8-122">添加书签链接</span><span class="sxs-lookup"><span data-stu-id="389e8-122">To add a bookmark link</span></span>  
  
1.  <span data-ttu-id="389e8-123">在“设计”视图中，右键单击要向其添加链接的文本框、图像或图表，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="389e8-123">In Design view, right-click the text box, image, chart, to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="389e8-124">在该报表项的 **“属性”** 对话框中，单击 **“操作”** 。</span><span class="sxs-lookup"><span data-stu-id="389e8-124">In The **Properties** dialog box for that report item, click **Action**.</span></span>  
  
3.  <span data-ttu-id="389e8-125">选择 **“转到书签”** 。</span><span class="sxs-lookup"><span data-stu-id="389e8-125">Select **Go to bookmark**.</span></span> <span data-ttu-id="389e8-126">其他部分将显示在此选项的对话框中。</span><span class="sxs-lookup"><span data-stu-id="389e8-126">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="389e8-127">在 **“选择书签”** 框中，键入或选择一个书签或一个计算结果为书签的表达式。</span><span class="sxs-lookup"><span data-stu-id="389e8-127">In the **Select bookmark** box, type or select a bookmark or an expression that evaluates to a bookmark.</span></span> <span data-ttu-id="389e8-128">在上一个示例中，可以键入 **BikePhoto** 为报表中的图像创建链接。</span><span class="sxs-lookup"><span data-stu-id="389e8-128">Using the previous example, type **BikePhoto** to create a link to the image in your report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="389e8-129">（可选）文本的格式不会自动设置为链接。</span><span class="sxs-lookup"><span data-stu-id="389e8-129">(Optional) The text is not automatically formatted like a link.</span></span> <span data-ttu-id="389e8-130">对于文本，很有必要更改文本的颜色和效果以指示该文本是一个链接。</span><span class="sxs-lookup"><span data-stu-id="389e8-130">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="389e8-131">例如，在功能区的“主页”选项卡中的 **“字体”** 部分中，将颜色更改为蓝色，并将效果更改为下划线。</span><span class="sxs-lookup"><span data-stu-id="389e8-131">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="389e8-132">若要测试该链接，请单击 **“运行”** 以预览报表，然后单击对其设置此链接的报表项。</span><span class="sxs-lookup"><span data-stu-id="389e8-132">To test the link, click **Run** to preview the report, and then click the report item that you set this link on..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="389e8-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="389e8-133">See Also</span></span>  
 <span data-ttu-id="389e8-134">[交互式排序、文档结构图和链接（报表生成器和 SSRS）](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="389e8-134">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="389e8-135">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="389e8-135">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="389e8-136">对数据进行筛选、分组和排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="389e8-136">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
