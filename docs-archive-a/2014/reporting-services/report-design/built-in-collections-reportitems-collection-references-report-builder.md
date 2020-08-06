---
title: ReportItems 集合引用（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61c89002adafb030288535debfe72de061945640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682734"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="9c3e3-102">ReportItems 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9c3e3-102">ReportItems Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9c3e3-103">`ReportItems` 内置集合是来自报表项（如报表设计图面上的数据区域行或文本框）的文本框集合。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-103">The `ReportItems` built-in collection is the set of text boxes from report items such as rows of a data region or text boxes on the report design surface.</span></span> <span data-ttu-id="9c3e3-104">`ReportItems` 集合包括位于表头、表尾或表体的当前作用域中的文本框。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-104">The `ReportItems` collection includes text boxes that are in the current scope of a page header, page footer, or report body.</span></span> <span data-ttu-id="9c3e3-105">此集合在运行时由报表处理器和报表呈现器确定。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-105">This collection is determined at run time by the report processor and the report renderer.</span></span> <span data-ttu-id="9c3e3-106">用户查看报表页面时，如果报表处理器连续组合报表数据和报表项布局元素，则当前作用域将随之变化。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-106">The current scope changes as the report processor successively combines report data and the report item layout elements as the user views pages of a report.</span></span> <span data-ttu-id="9c3e3-107">可以使用 `ReportItems` 内置集合在每个页面中生成显示首项和尾项的字典样式表头。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-107">You can use the `ReportItems` built-in collection to produce dictionary-style page headers that show the first and last items on each page.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a><span data-ttu-id="9c3e3-108">使用 ReportItems 值属性</span><span class="sxs-lookup"><span data-stu-id="9c3e3-108">Using the ReportItems Value Property</span></span>  
 <span data-ttu-id="9c3e3-109">`ReportItems` 集合内的项只有一个属性：Value。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-109">Items within the `ReportItems` collection have only one property: Value.</span></span> <span data-ttu-id="9c3e3-110">`ReportItems` 项的值可用于显示或计算报表中其他字段的数据。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-110">The value for a `ReportItems` item can be used to display or calculate data from another field in the report.</span></span> <span data-ttu-id="9c3e3-111">若要访问当前文本框的值，可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 内置全局 Me.Value 或仅使用 Value。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-111">To access the value of the current text box, you can use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] built-in global Me.Value or simply Value.</span></span> <span data-ttu-id="9c3e3-112">在报表函数（如 First）和聚合函数中使用完全限定语法。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-112">In report functions such as First and aggregate functions, use the fully qualified syntax.</span></span>  
  
 <span data-ttu-id="9c3e3-113">例如：</span><span class="sxs-lookup"><span data-stu-id="9c3e3-113">For example:</span></span>  
  
-   <span data-ttu-id="9c3e3-114">此表达式放置在文本框中时，显示名为 `Textbox1` 的 `ReportItem` 文本框的值：</span><span class="sxs-lookup"><span data-stu-id="9c3e3-114">This expression, placed in a text box, displays the value of a `ReportItem` text box named `Textbox1`:</span></span>  
  
     `=ReportItems!Textbox1.Value`  
  
-   <span data-ttu-id="9c3e3-115">此表达式放置在 `ReportItem` 文本框颜色属性中，当值为 > 0 时，将以黑色显示文本; 否则，该值将显示为红色：</span><span class="sxs-lookup"><span data-stu-id="9c3e3-115">This expression, placed in a `ReportItem` text box Color property, displays the text in black when the value is > 0; otherwise, the value is displayed in red:</span></span>  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   <span data-ttu-id="9c3e3-116">此表达式放置在表头或表尾的文本框中时，显示所呈现的报表每一页中名为 `LastName`的文本框的第一个值：</span><span class="sxs-lookup"><span data-stu-id="9c3e3-116">This expression, placed in a text box in the page header or page footer, displays the first value per page of the rendered report, for a text box named `LastName`:</span></span>  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a><span data-ttu-id="9c3e3-117">字典样式表头表达式</span><span class="sxs-lookup"><span data-stu-id="9c3e3-117">Dictionary-Style Page Header Expressions</span></span>  
 <span data-ttu-id="9c3e3-118">可以创建一个表头，显示此页第一个客户和最后一个客户。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-118">You can create a page header to display the first customer on the page and the last customer on the page.</span></span> <span data-ttu-id="9c3e3-119">因为在一个表达式中，表头中的文本框只能引用一次 `ReportItems` 内置集合，所以需要在表头添加两个文本框：一个用于第一个客户名称 (`=First(ReportItems!textboxLastName.Value`)，另一个用于最后一个客户名称 (`=Last(ReportItems!textboxLastName.Value`)。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-119">Because a text box in the page header can only refer to the `ReportItems` built-in collection once in an expression, you need to add two text boxes to the page header: one for the first customer name (`=First(ReportItems!textboxLastName.Value`) and one for the last customer name (`=Last(ReportItems!textboxLastName.Value`).</span></span>  
  
 <span data-ttu-id="9c3e3-120">在表头或表尾部分，只有当前页中的文本框才能作为 `ReportItems` 集合的成员。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-120">In a page header or page footer section, only text boxes on the current page are available as a member of the `ReportItems` collection.</span></span> <span data-ttu-id="9c3e3-121">例如，在多页数据区域中，如果 `ReportItems!textboxLastName.Value` 引用一个只显示在首页的文本框，则可以在首页看到一个值，其他页则显示 **#Error** ，表明该表达式不能按本文所述进行计算。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-121">For example, if `ReportItems!textboxLastName.Value` refers to a text box that only appears on the first page for a multipage data region, you see a value for the first page, but all other pages display **#Error** to show the expression could not be evaluated as written.</span></span>  
  
## <a name="scope-for-the-reportitems-collection"></a><span data-ttu-id="9c3e3-122">ReportItems 集合的作用域</span><span class="sxs-lookup"><span data-stu-id="9c3e3-122">Scope for the ReportItems Collection</span></span>  
 <span data-ttu-id="9c3e3-123">处理报表时，文本框所在数据集、数据区域和组关联的上下文将计算表体或数据区域中的所有文本框。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-123">As the report is processed, each text box in the report body or in a data region is evaluated in the context of its dataset, data region, and group associations.</span></span> <span data-ttu-id="9c3e3-124">对 `ReportItems` 集合的引用的作用域为当前作用域或高于当前作用域的任何点。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-124">The scope for a reference to the `ReportItems` collection is the current scope or any point higher than the current scope.</span></span>  
  
 <span data-ttu-id="9c3e3-125">例如，位于父组行的文本框不能包含引用子组行的文本框名称的表达式。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-125">For example, a text box in a row that is in a parent group must not contain an expression that refers to the name of a text box in a child group row.</span></span> <span data-ttu-id="9c3e3-126">此类表达式不会解析报表中的值，因为子行文本框超出了作用域。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-126">Such an expression does not resolve to a value in the report because the child row text box is out of scope.</span></span> <span data-ttu-id="9c3e3-127">有关详细信息，请参阅 [聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3e3-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c3e3-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c3e3-128">See Also</span></span>  
 <span data-ttu-id="9c3e3-129">[表达式中的内置集合（报表生成器和 SSRS）](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="9c3e3-129">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 <span data-ttu-id="9c3e3-130">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9c3e3-130">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9c3e3-131">[Reporting Services 中的分页（报表生成器和 SSRS）](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9c3e3-131">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9c3e3-132">对数据进行筛选、分组和排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9c3e3-132">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
