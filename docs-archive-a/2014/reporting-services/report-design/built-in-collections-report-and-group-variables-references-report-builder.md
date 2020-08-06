---
title: 报表和组变量集合引用（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10404"
- sql12.rtp.rptdesigner.categorygroupproperties.variables.f1
- "10083"
- sql12.rtp.rptdesigner.seriesgroupproperties.variables.f1
- sql12.rtp.rptdesigner.reportproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- "10292"
- "10412"
ms.assetid: 4be5b463-3ce2-483d-a3c6-dae752cb543e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 41dd652bf39721b13801131a5ec268495edf9d29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682735"
---
# <a name="report-and-group-variables-collections-references-report-builder-and-ssrs"></a><span data-ttu-id="c2dc0-102">报表和组变量集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c2dc0-102">Report and Group Variables Collections References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c2dc0-103">在报表的表达式中需要多次使用某个复杂计算时，您可能需要创建一个变量。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-103">When you have a complex calculation that is used more than once in expressions in a report, you might want to create a variable.</span></span> <span data-ttu-id="c2dc0-104">您可以创建一个报表变量或组变量。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-104">You can create a report variable or a group variable.</span></span> <span data-ttu-id="c2dc0-105">变量名称在报表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-105">Variable names must be unique in a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-variables"></a><span data-ttu-id="c2dc0-106">报表变量</span><span class="sxs-lookup"><span data-stu-id="c2dc0-106">Report Variables</span></span>  
 <span data-ttu-id="c2dc0-107">使用报表变量可保存时间相关的计算的值（例如货币汇率或时间戳），或者保存多次引用的复杂计算的值。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-107">Use a report variable to hold a value for time-dependent calculations, such as currency rates or time stamps, or for a complex calculation that is referenced multiple times.</span></span> <span data-ttu-id="c2dc0-108">默认情况下，报表变量计算一次即可在报表中的表达式中使用。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-108">By default, a report variable is calculated once and can be used in expressions throughout a report.</span></span> <span data-ttu-id="c2dc0-109">报表变量默认为只读。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-109">Report variables are read-only by default.</span></span> <span data-ttu-id="c2dc0-110">您可以更改该默认设置以使报表变量成为读写的。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-110">You can change the default to enable a report variable as read-write.</span></span> <span data-ttu-id="c2dc0-111">在再次处理该报表之前，报表变量中的值将保留在整个会话中。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-111">The value in a report variable is preserved throughout a session, until the report is processed again.</span></span>  
  
 <span data-ttu-id="c2dc0-112">若要添加报表变量，请打开“报表属性”  对话框，单击“变量”  ，然后提供名称和值。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-112">To add a report variable, open the **ReportProperties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="c2dc0-113">名称是区分大小写的字符串，以字母开头，不含空格。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-113">Names are case-sensitive strings that begin with a letter and have no spaces.</span></span> <span data-ttu-id="c2dc0-114">名称可以包含字母、数字或下划线 (_)。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-114">A name can include letters, numbers, or underscores (_).</span></span>  
  
 <span data-ttu-id="c2dc0-115">若要引用表达式中的变量，请使用全局集合语法，例如 `=Variables!CustomTimeStamp.Value`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-115">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!CustomTimeStamp.Value`.</span></span> <span data-ttu-id="c2dc0-116">在设计图面上，文本框中的值显示为 `<<Expr>>`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-116">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
 <span data-ttu-id="c2dc0-117">可以按下列方式使用报表变量：</span><span class="sxs-lookup"><span data-stu-id="c2dc0-117">You can use report variables in the following ways:</span></span>  
  
-   <span data-ttu-id="c2dc0-118">**只读使用** ：设置值一次以便为报表会话创建一个常量，例如创建一个时间戳。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-118">**Read-only use** Set a value once to create a constant for the report session, for example, to create a time stamp.</span></span>  
  
     <span data-ttu-id="c2dc0-119">因为当用户在报表中翻页时，文本框中的表达式将按需计算，所以，如果用户通过使用“上一页”按钮向前和向后翻页，动态值（例如，包括返回时间的 `Now()` 函数的表达式）可以返回不同的值。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-119">Because expressions in text boxes are evaluated on-demand as a user pages through a report, dynamic values (for example, an expression that includes the `Now()` function, which returns the time of day) can return different values if you page forward and backward by using the **Back** button.</span></span> <span data-ttu-id="c2dc0-120">通过将报表变量的值设置为表达式 `=Now()`，然后在表达式中添加变量，可确保整个报表处理过程中使用相同的值。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-120">By setting a the value of a report variable to the expression `=Now()`, and then adding the variable to your expression, you ensure the same value is used throughout report processing.</span></span>  
  
-   <span data-ttu-id="c2dc0-121">**读写使用** ：设置值一次并在报表会话中序列化该值。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-121">**Read-write use** Set a value once and serialize the value within a report session.</span></span> <span data-ttu-id="c2dc0-122">变量的读写选项提供了一个比在报表定义的代码块中使用静态变量更好的选择。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-122">The read-write option for variables provides a better alternative than using a static variable in the Code block in the report definition.</span></span>  
  
     <span data-ttu-id="c2dc0-123">如果清除某个变量的**只读**选项，则该变量的可写属性将设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-123">When you clear the **Read-Only** option for a variable, the Writable property for the variable is set to `true`.</span></span> <span data-ttu-id="c2dc0-124">若要从某一表达式更新值，请使用 SetValue 方法，例如 `=Variables!MyVariable.SetValue("123")`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-124">To update the value from an expression, use the SetValue method, for example, `=Variables!MyVariable.SetValue("123")`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2dc0-125">您不能控制报表处理器何时初始化一个变量或何时对更新变量的表达式进行计算。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-125">You cannot control when the report processor initializes a variable or evaluates an expression that updates a variable.</span></span> <span data-ttu-id="c2dc0-126">变量初始化的执行顺序未定义。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-126">The order of execution for variable initialization is undefined.</span></span>  
  
 <span data-ttu-id="c2dc0-127">有关会话的详细信息，请参阅 [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-127">For more information about sessions, see [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md).</span></span>  
  
## <a name="group-variables"></a><span data-ttu-id="c2dc0-128">组变量</span><span class="sxs-lookup"><span data-stu-id="c2dc0-128">Group Variables</span></span>  
 <span data-ttu-id="c2dc0-129">使用组变量可在组的作用域中计算一次复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-129">Use a group variable to calculate a complex expression once in the scope of a group.</span></span> <span data-ttu-id="c2dc0-130">组变量仅在组及其子组的作用域中有效。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-130">A group variable is valid only in the scope of the group and its child groups.</span></span>  
  
 <span data-ttu-id="c2dc0-131">例如，假定一个数据区域显示不同税收类别项目的库存数据，您希望对每种类别分别采用不同的税率。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-131">For example, suppose a data region displays inventory data for items that are in different tax categories and you want to apply different tax rates for each category.</span></span> <span data-ttu-id="c2dc0-132">可以对 Category 中的数据进行分组，并对父组定义一个 *Tax* 变量。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-132">You would group the data on Category and define a *Tax* variable on the parent group.</span></span> <span data-ttu-id="c2dc0-133">然后为每个税收类别的 *ItemTax* 定义一个组变量，再将每个不同的 Category 子组分配给正确的组变量。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-133">Then you would define a group variable for *ItemTax* for each tax category and assign each of the different Category subgroups to the correct group variable.</span></span> <span data-ttu-id="c2dc0-134">例如：</span><span class="sxs-lookup"><span data-stu-id="c2dc0-134">For example:</span></span>  
  
-   <span data-ttu-id="c2dc0-135">对于基于 `[Category]`的父组，使用 *值定义变量* Tax `[Tax]`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-135">For the parent group based on `[Category]`, define the variable *Tax* with a value `[Tax]`.</span></span> <span data-ttu-id="c2dc0-136">假定类别值为 Food 和 Clothing。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-136">Assume the category values are Food and Clothing.</span></span>  
  
-   <span data-ttu-id="c2dc0-137">对于基于 `[Subcategory]`的子组，将变量 *ItemsTax* 定义为 `=Variables!Tax.Value * Sum(Fields!Price.Value)`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-137">For the child group based on `[Subcategory]`, define the variable *ItemsTax* as `=Variables!Tax.Value * Sum(Fields!Price.Value)`.</span></span> <span data-ttu-id="c2dc0-138">假定 Food 类别中的子类别值为 Beverages 和 Bread。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-138">Assume the subcategory values for the category Food are Beverages and Bread.</span></span> <span data-ttu-id="c2dc0-139">假定 Clothing 类别中的子类别值为 Shirts 和 Hats。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-139">Assume the subcategory values for Clothing are Shirts and Hats.</span></span>  
  
-   <span data-ttu-id="c2dc0-140">在子组行中的文本框添加表达式 `=Variables!ItemsTax.Value`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-140">For a text box in a row in the child group, add the expression `=Variables!ItemsTax.Value`.</span></span>  
  
     <span data-ttu-id="c2dc0-141">文本框中显示按照 Food 税计算的 Beverages 和 Bread 以及按照 Clothing 税计算的 Shirts 和 Hats 的总税额。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-141">The text box displays the total tax for Beverages and Bread using the Food tax and for Shirts and Hats using the Clothing tax.</span></span>  
  
 <span data-ttu-id="c2dc0-142">若要添加组变量，打开 **“Tablix 组属性”** 对话框，单击 **“变量”** ，然后输入一个名称和一个值。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-142">To add a group variable, open the **Tablix Group Properties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="c2dc0-143">组变量在每个唯一组值中计算一次。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-143">The group variable is calculated once per unique group value.</span></span>  
  
 <span data-ttu-id="c2dc0-144">若要引用表达式中的变量，请使用全局集合语法，例如 `=Variables!GroupDescription.Value`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-144">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!GroupDescription.Value`.</span></span> <span data-ttu-id="c2dc0-145">在设计图面上，文本框中的值显示为 `<<Expr>>`。</span><span class="sxs-lookup"><span data-stu-id="c2dc0-145">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2dc0-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2dc0-146">See Also</span></span>  
 <span data-ttu-id="c2dc0-147">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2dc0-147">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2dc0-148">[表达式中的内置集合（报表生成器和 SSRS）](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="c2dc0-148">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="c2dc0-149">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c2dc0-149">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
