---
title: 表达式示例（报表生成器和 SSRS）| Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/08/2017
ms.openlocfilehash: c7ef06143dafdb5034d0f6202fdc16bc51f74ca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580601"
---
# <a name="expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="37dbb-102">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-102">Expression Examples (Report Builder and SSRS)</span></span>

<span data-ttu-id="37dbb-103">表达式通常在报表中使用，以控制报表的内容和外观。</span><span class="sxs-lookup"><span data-stu-id="37dbb-103">Expressions are used frequently in reports to control content and report appearance.</span></span> <span data-ttu-id="37dbb-104">表达式是用编写的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ，可以使用内置函数自定义代码、报表和组变量以及用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="37dbb-104">Expressions are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], and can use built-in functions custom code, report and group variables, and user-defined variables.</span></span> <span data-ttu-id="37dbb-105">表达式通常以等号 (=) 开头。</span><span class="sxs-lookup"><span data-stu-id="37dbb-105">Expressions begin with an equal sign (=).</span></span> <span data-ttu-id="37dbb-106">有关表达式编辑器和可以包括的引用类型的详细信息，请参阅[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md)和[添加表达式（报表生成器和 SSRS）](add-an-expression-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-106">For more information about the expression editor and the types of references that you can include, see [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md), and [Add an Expression &#40;Report Builder and SSRS&#41;](add-an-expression-report-builder-and-ssrs.md).</span></span>  

> [!IMPORTANT]  
>  <span data-ttu-id="37dbb-107">启用 RDL 沙盒处理后，在报表发布时，只能在表达式文本中使用某些类型与成员。</span><span class="sxs-lookup"><span data-stu-id="37dbb-107">When RDL Sandboxing is enabled, only certain types and members can be used in expression text at report publish time.</span></span> <span data-ttu-id="37dbb-108">有关详细信息，请参阅 [Enable and Disable RDL Sandboxing](../enable-and-disable-rdl-sandboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-108">For more information, see [Enable and Disable RDL Sandboxing](../enable-and-disable-rdl-sandboxing.md).</span></span>  

<span data-ttu-id="37dbb-109">本主题提供了可用于报表中常见任务的表达式的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-109">This topic provides examples of expressions that can be used for common tasks in a report.</span></span>  

-   <span data-ttu-id="37dbb-110">[Visual Basic 函数](#VisualBasicFunctions) ：日期、字符串、转换和条件 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-110">[Visual Basic Functions](#VisualBasicFunctions) Examples for date, string, conversion and conditional [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions.</span></span>  

-   <span data-ttu-id="37dbb-111">[报表函数](#ReportFunctions) ：聚合函数和其他内置报表函数的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-111">[Report Functions](#ReportFunctions) Examples for aggregates and other built-in report functions.</span></span>  

-   <span data-ttu-id="37dbb-112">[报表数据的外观](#AppearanceofReportData) ：更改报表外观的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-112">[Appearance of Report Data](#AppearanceofReportData) Examples for changing the appearance of a report.</span></span>  

-   <span data-ttu-id="37dbb-113">[属性](#Properties) ：通过设置报表项属性来控制格式或可见性的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-113">[Properties](#Properties) Examples for setting report item properties to control format or visibility.</span></span>  

-   <span data-ttu-id="37dbb-114">[参数](#Parameters) ：在表达式中使用参数的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-114">[Parameters](#Parameters) Examples for using parameters in an expression.</span></span>  

-   <span data-ttu-id="37dbb-115">[自定义代码](#CustomCode) ：嵌入自定义代码的示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-115">[Custom Code](#CustomCode) Examples of embedded custom code.</span></span>  

<span data-ttu-id="37dbb-116">有关特定用途的表达式示例，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="37dbb-116">For expression examples for specific uses, see the following topics:</span></span>  

-   [<span data-ttu-id="37dbb-117">组表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-117">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="37dbb-118">筛选器公式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-118">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="37dbb-119">常用筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-119">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="37dbb-120">报表和组变量集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-120">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  

<span data-ttu-id="37dbb-121">有关简单表达式和复杂表达式、使用表达式的位置、以及表达式中可以包含的引用类型的详细信息，请参阅 [表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-121">For more information about simple and complex expressions, where you can use expressions, and the types of references that you can include in an expression, see topics under [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="37dbb-122">有关为计算聚合而计算表达式时所处上下文的详细信息，请参阅[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-122">For more information about the context in which expressions are evaluated for calculating aggregates, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  

<span data-ttu-id="37dbb-123">若要了解如何编写使用许多本主题中的表达式示例所用的函数和运算符的表达式，请参阅 [Tutorial: Introducing Expressions](../tutorial-introducing-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-123">To learn how to write expressions that use many of the functions and operators also used by expression examples in this topic, but in the context of writing a report, see [Tutorial: Introducing Expressions](../tutorial-introducing-expressions.md).</span></span>  

<span data-ttu-id="37dbb-124">表达式编辑器包含内置函数的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="37dbb-124">The expression editor includes a hierarchical view of built-in functions.</span></span> <span data-ttu-id="37dbb-125">选择函数时，“值”窗格中会显示代码示例。</span><span class="sxs-lookup"><span data-stu-id="37dbb-125">When you select the function, a code example appears in the Values pane.</span></span> <span data-ttu-id="37dbb-126">有关详细信息，请参阅 "[表达式" 对话框](../expression-dialog-box.md)或 "表达式"[对话框 &#40;报表生成器&#41;](../expression-dialog-box-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-126">For more information, see the [Expression Dialog Box](../expression-dialog-box.md) or [Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md).</span></span>  

## <a name="functions"></a><span data-ttu-id="37dbb-127">函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-127">Functions</span></span>  

<span data-ttu-id="37dbb-128">报表中的许多表达式都包含函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-128">Many expressions in a report contain functions.</span></span> <span data-ttu-id="37dbb-129">您可以使用这些函数来设置数据格式、应用逻辑和访问报表元数据。</span><span class="sxs-lookup"><span data-stu-id="37dbb-129">You can format data, apply logic, and access report metadata using these functions.</span></span> <span data-ttu-id="37dbb-130">您可以编写使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 运行时库中的函数，以及 <xref:System.Convert> 和 <xref:System.Math> 命名空间中的函数的表达式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-130">You can write expressions that use functions from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library, and from the <xref:System.Convert> and <xref:System.Math> namespaces.</span></span> <span data-ttu-id="37dbb-131">您可以从其他程序集或自定义代码中向函数添加引用。</span><span class="sxs-lookup"><span data-stu-id="37dbb-131">You can add references to functions from other assemblies or custom code.</span></span> <span data-ttu-id="37dbb-132">你还可以使用中的类 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，其中包括 <xref:System.Text.RegularExpressions> 。</span><span class="sxs-lookup"><span data-stu-id="37dbb-132">You can also use classes from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], including <xref:System.Text.RegularExpressions>.</span></span>  

###  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> <span data-ttu-id="37dbb-133">Visual Basic 函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-133">Visual Basic Functions</span></span>  
<span data-ttu-id="37dbb-134">您可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数来处理文本框中所显示的数据，或者处理参数、属性或报表其他区域中所用的数据。</span><span class="sxs-lookup"><span data-stu-id="37dbb-134">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to manipulate the data that is displayed in text boxes or that is used for parameters, properties, or other areas of the report.</span></span> <span data-ttu-id="37dbb-135">本部分举例说明了其中的一些函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-135">This section provides examples demonstrating some of these functions.</span></span> <span data-ttu-id="37dbb-136">有关详细信息，请参阅 [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) （Visual Basic 运行时库成员）。</span><span class="sxs-lookup"><span data-stu-id="37dbb-136">For more information, see [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  

<span data-ttu-id="37dbb-137">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供了许多自定义格式选项，例如，特定日期格式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-137">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides many custom format options, for example, for specific date formats.</span></span> <span data-ttu-id="37dbb-138">有关详细信息，请参阅 MSDN 上的 [格式化类型](https://go.microsoft.com/fwlink/?LinkId=112024) 。</span><span class="sxs-lookup"><span data-stu-id="37dbb-138">For more information, see [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) on MSDN.</span></span>  

#### <a name="math-functions"></a><span data-ttu-id="37dbb-139">数学函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-139">Math Functions</span></span>  

-   <span data-ttu-id="37dbb-140">`Round` 函数可用于将数字舍入为最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-140">The `Round` function is useful to round numbers to the nearest integer.</span></span> <span data-ttu-id="37dbb-141">下面的表达式将 1.3 舍入为 1：</span><span class="sxs-lookup"><span data-stu-id="37dbb-141">The following expression rounds a 1.3 to 1:</span></span>  

```  
= Round(1.3)  
```  

<span data-ttu-id="37dbb-142">您也可以编写表达式以将某个值舍入到您指定的倍数，类似于 Excel 中的 `MRound` 函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-142">You can also write an expression to round a value to a multiple that you specify, similar to the `MRound` function in Excel.</span></span> <span data-ttu-id="37dbb-143">用某个生成整数的因子乘以该值，对数字进行舍入，然后除以同一因子。</span><span class="sxs-lookup"><span data-stu-id="37dbb-143">Multiply the value by a factor that creates an integer, round the number, and then divide by the same factor.</span></span> <span data-ttu-id="37dbb-144">例如，若要将 1.3 舍入到 .2 (1.4) 的最接近的倍数，请使用下面的表达式：</span><span class="sxs-lookup"><span data-stu-id="37dbb-144">For example, to round 1.3 to the nearest multiple of .2 (1.4), use the following expression:</span></span>  

```  
= Round(1.3*5)/5  
```  

####  <a name="date-functions"></a><a name="DateFunctions"></a><span data-ttu-id="37dbb-145">日期函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-145">Date Functions</span></span>  

-   <span data-ttu-id="37dbb-146">`Today` 函数可提供当前日期。</span><span class="sxs-lookup"><span data-stu-id="37dbb-146">The `Today` function provides the current date.</span></span> <span data-ttu-id="37dbb-147">此表达式可用在文本框中以在报表上显示日期，或用在参数中以根据当前日期筛选数据。</span><span class="sxs-lookup"><span data-stu-id="37dbb-147">This expression can be used in a text box to display the date on the report, or in a parameter to filter data based on the current date.</span></span>  

```  
=Today()  
```  

-   <span data-ttu-id="37dbb-148">若要基于单个参数提供日期范围，可使用 `DateAdd` 函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-148">The `DateAdd` function is useful for supplying a range of dates based on a single parameter.</span></span> <span data-ttu-id="37dbb-149">下面的表达式提供名为 *StartDate*的参数日期之后六个月的日期。</span><span class="sxs-lookup"><span data-stu-id="37dbb-149">The following expression provides a date that is six months after the date from a parameter named *StartDate*.</span></span>  

```  
=DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
```  

-   <span data-ttu-id="37dbb-150">`Year` 函数可显示某个特定的日期的年份。</span><span class="sxs-lookup"><span data-stu-id="37dbb-150">The `Year` function displays the year for a particular date.</span></span> <span data-ttu-id="37dbb-151">您可以使用此表达式将日期组合在一起，或者将年份显示为一组日期的标签。</span><span class="sxs-lookup"><span data-stu-id="37dbb-151">You can use this to group dates together or to display the year as a label for a set of dates.</span></span> <span data-ttu-id="37dbb-152">此表达式可以提供一组给定的销售订单日期的年份。</span><span class="sxs-lookup"><span data-stu-id="37dbb-152">This expression provides the year for a given group of sales order dates.</span></span> <span data-ttu-id="37dbb-153">`Month` 函数和其他函数也可用于日期操作。</span><span class="sxs-lookup"><span data-stu-id="37dbb-153">The `Month` function and other functions can also be used to manipulate dates.</span></span> <span data-ttu-id="37dbb-154">有关详细信息，请参阅 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="37dbb-154">For more information, see the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] documentation.</span></span>  

```  
=Year(Fields!OrderDate.Value)  
```  

-   <span data-ttu-id="37dbb-155">您可以在表达式中组合函数，以自定义格式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-155">You can combine functions in an expression to customize the format.</span></span> <span data-ttu-id="37dbb-156">下面的表达式将“月-日-年”的日期格式更改为“月-周-周数”。</span><span class="sxs-lookup"><span data-stu-id="37dbb-156">The following expression changes the format of a date in the form month-day-year to month-week-week number.</span></span> <span data-ttu-id="37dbb-157">例如，将“12/23/2009”更改为“December Week 3”：</span><span class="sxs-lookup"><span data-stu-id="37dbb-157">For example, 12/23/2009 to December Week 3:</span></span>  

```  
=Format(Fields!MyDate.Value, "MMMM") & " Week " &   
(Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
```  

<span data-ttu-id="37dbb-158">当此表达式在数据集中用作计算字段时，您可以在图表上使用该表达式来按每个月内的周聚合值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-158">When used as a calculated field in a dataset, you can use this expression on a chart to aggregate values by week within each month.</span></span>  

-   <span data-ttu-id="37dbb-159">以下表达式将 SellStartDate 值的格式设置为 MMM-YY。</span><span class="sxs-lookup"><span data-stu-id="37dbb-159">The following expression formats the SellStartDate value as MMM-YY.</span></span> <span data-ttu-id="37dbb-160">SellStartDate 字段为 datetime 数据类型。</span><span class="sxs-lookup"><span data-stu-id="37dbb-160">SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
```  

-   <span data-ttu-id="37dbb-161">以下表达式将 SellStartDate 值的格式设置为 dd/MM/yyyy。</span><span class="sxs-lookup"><span data-stu-id="37dbb-161">The following expression formats the SellStartDate value as dd/MM/yyyy.</span></span> <span data-ttu-id="37dbb-162">SellStartDate 字段为 datetime 数据类型。</span><span class="sxs-lookup"><span data-stu-id="37dbb-162">The SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
```  

-   <span data-ttu-id="37dbb-163">`CDate` 函数将值转换为日期。</span><span class="sxs-lookup"><span data-stu-id="37dbb-163">The `CDate` function converts the value to a date.</span></span> <span data-ttu-id="37dbb-164">`Now` 函数根据您的系统返回包含当前日期和时间的日期值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-164">The `Now` function returns a date value containing the current date and time according to your system.</span></span> <span data-ttu-id="37dbb-165">`DateDiff` 返回一个指定两个日期值之间的时间间隔数的长整型值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-165">`DateDiff` returns a Long value specifying the number of time intervals between two Date values.</span></span>  

<span data-ttu-id="37dbb-166">以下示例显示了当前年份的开始日期</span><span class="sxs-lookup"><span data-stu-id="37dbb-166">The following example displays the start date of the current year</span></span>  

```  
=DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
```  

-   <span data-ttu-id="37dbb-167">以下示例显示了基于当前月的上一个月的开始日期。</span><span class="sxs-lookup"><span data-stu-id="37dbb-167">The following example displays the start date for the previous month based on the current month.</span></span>  

```  
=DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
```  

-   <span data-ttu-id="37dbb-168">以下表达式生成介于 SellStartDate 和 LastReceiptDate 之间的间隔年。</span><span class="sxs-lookup"><span data-stu-id="37dbb-168">The following expression generates the interval years between SellStartDate and LastReceiptDate.</span></span> <span data-ttu-id="37dbb-169">这些字段在两个不同的数据集内，即 DataSet1 和 DataSet2。</span><span class="sxs-lookup"><span data-stu-id="37dbb-169">These fields are in two different datasets, DataSet1 and DataSet2.</span></span> <span data-ttu-id="37dbb-170">[First 函数（报表生成器和 SSRS）](report-builder-functions-first-function.md)是一个聚合函数，它返回 DataSet1 中 SellStartDate 的第一个值和 DataSet2 中 LastReceiptDate 的第一个值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-170">The [First Function &#40;Report Builder and SSRS&#41;](report-builder-functions-first-function.md), which is an aggregate function, returns the first value of SellStartDate in DataSet1 and the first value of LastReceiptDate in DataSet2.</span></span>  

```  
=DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
```  

-   <span data-ttu-id="37dbb-171">`DatePart` 函数返回一个整型值，该值包含给定日期值的指定组件。以下表达式返回 DataSet1 中 SellStartDate 的第一个值的年份。</span><span class="sxs-lookup"><span data-stu-id="37dbb-171">The `DatePart` function returns an Integer value containing the specified component of a given Date value.The following expression returns the year for the first value of the SellStartDate in DataSet1.</span></span> <span data-ttu-id="37dbb-172">指定数据集作用域是因为报表中有多个数据集。</span><span class="sxs-lookup"><span data-stu-id="37dbb-172">The dataset scope is specified because there are multiple datasets in the report.</span></span>  

```  
=Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  

```  

-   <span data-ttu-id="37dbb-173">`DateSerial` 函数返回一个代表指定年、月和日的日期值，其时间信息设置为午夜。</span><span class="sxs-lookup"><span data-stu-id="37dbb-173">The `DateSerial` function returns a Date value representing a specified year, month, and day, with the time information set to midnight.</span></span> <span data-ttu-id="37dbb-174">以下示例显示了基于当前月的上一个月的结束日期。</span><span class="sxs-lookup"><span data-stu-id="37dbb-174">The following example displays the ending date for the prior month, based on the current month.</span></span>  

```  
=DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
```  

-   <span data-ttu-id="37dbb-175">以下表达式基于用户选定的日期参数值显示不同日期。</span><span class="sxs-lookup"><span data-stu-id="37dbb-175">The following expressions display various dates based on a date parameter value selected by the user.</span></span>  

|<span data-ttu-id="37dbb-176">示例说明</span><span class="sxs-lookup"><span data-stu-id="37dbb-176">Example Description</span></span>|<span data-ttu-id="37dbb-177">示例</span><span class="sxs-lookup"><span data-stu-id="37dbb-177">Example</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="37dbb-178">昨天</span><span class="sxs-lookup"><span data-stu-id="37dbb-178">Yesterday</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|<span data-ttu-id="37dbb-179">两天前</span><span class="sxs-lookup"><span data-stu-id="37dbb-179">Two Days Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|<span data-ttu-id="37dbb-180">一个月前</span><span class="sxs-lookup"><span data-stu-id="37dbb-180">One Month Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="37dbb-181">两个月前</span><span class="sxs-lookup"><span data-stu-id="37dbb-181">Two Months Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="37dbb-182">一年前</span><span class="sxs-lookup"><span data-stu-id="37dbb-182">One Year Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="37dbb-183">两年前</span><span class="sxs-lookup"><span data-stu-id="37dbb-183">Two Years Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  

####  <a name="string-functions"></a><a name="StringFunctions"></a><span data-ttu-id="37dbb-184">字符串函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-184">String Functions</span></span>  

-   <span data-ttu-id="37dbb-185">使用串联运算符和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 常量可将多个字段组合在一起。</span><span class="sxs-lookup"><span data-stu-id="37dbb-185">Combine more than one field by using concatenation operators and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] constants.</span></span> <span data-ttu-id="37dbb-186">以下表达式返回两个字段，它们分别位于同一文本框的不同行中：</span><span class="sxs-lookup"><span data-stu-id="37dbb-186">The following expression returns two fields, each on a separate line in the same text box:</span></span>  

```  
=Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
```  

-   <span data-ttu-id="37dbb-187">使用 `Format` 函数可设置字符串中日期和数字的格式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-187">Format dates and numbers in a string with the `Format` function.</span></span> <span data-ttu-id="37dbb-188">下面的表达式以长日期格式显示 *StartDate* 和 *EndDate* 参数的值：</span><span class="sxs-lookup"><span data-stu-id="37dbb-188">The following expression displays values of the *StartDate* and *EndDate* parameters in long date format:</span></span>  

```  
=Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
```  

<span data-ttu-id="37dbb-189">如果文本框仅包含日期或数字，则应使用文本框的 "格式" 属性来应用格式设置，而不是在 `Format` 文本框中应用函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-189">If the text box contains only a date or number, you should use the Format property of the text box to apply formatting instead of the `Format` function within the text box.</span></span>  

-   <span data-ttu-id="37dbb-190">`Right`、 `Len` 和 `InStr` 函数对于返回子字符串十分有用，例如，仅将*域* \\ *用户名*修整为用户名即可。</span><span class="sxs-lookup"><span data-stu-id="37dbb-190">The `Right`, `Len`, and `InStr` functions are useful for returning a substring, for example, trimming *DOMAIN*\\*username* to just the user name.</span></span> <span data-ttu-id="37dbb-191">下面的表达式从名为 User\*\* 的参数返回反斜杠 (\\) 字符右侧的字符串部分：</span><span class="sxs-lookup"><span data-stu-id="37dbb-191">The following expression returns the part of the string to the right of a backslash (\\) character from a parameter named *User*:</span></span>  

```  
=Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
```  

<span data-ttu-id="37dbb-192">下面的表达式使用类的成员 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> 而不是函数，从而生成与上一个表达式相同的值 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="37dbb-192">The following expression results in the same value as the previous one, using members of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> class instead of [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions:</span></span>  

```  
=Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
```  

-   <span data-ttu-id="37dbb-193">显示多值参数的所选值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-193">Display the selected values from a multivalue parameter.</span></span> <span data-ttu-id="37dbb-194">下面的示例使用 `Join` 函数将参数*MySelection*的所选值串联到单个字符串中，该字符串可设置为报表项中文本框值的表达式：</span><span class="sxs-lookup"><span data-stu-id="37dbb-194">The following example uses the `Join` function to concatenate the selected values of the parameter *MySelection* into a single string that can be set as an expression for the value of a text box in a report item:</span></span>  

```  
= Join(Parameters!MySelection.Value)  
```  

<span data-ttu-id="37dbb-195">以下示例的作用与上面的示例相同，另外在所选值列表之前显示文本字符串。</span><span class="sxs-lookup"><span data-stu-id="37dbb-195">The following example does the same as the above example, as well as displays a text string prior to the list of selected values.</span></span>  

```  
="Report for " & JOIN(Parameters!MySelection.Value, " & ")  

```  

-   <span data-ttu-id="37dbb-196">`Regex`中的函数 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> 对更改现有字符串的格式很有用，例如，格式化电话号码。</span><span class="sxs-lookup"><span data-stu-id="37dbb-196">The `Regex` functions from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> are useful for changing the format of existing strings, for example, formatting a telephone number.</span></span> <span data-ttu-id="37dbb-197">以下表达式使用 `Replace` 函数将字段中的十位电话号码格式从 "*nnn* - *nnn* - *nnnn*" 更改为 " (*nnn*) *nnn* - *nnnn*"：</span><span class="sxs-lookup"><span data-stu-id="37dbb-197">The following expression uses the `Replace` function to change the format of a ten-digit telephone number in a field from "*nnn*-*nnn*-*nnnn*" to "(*nnn*) *nnn*-*nnnn*":</span></span>  

```  
=System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
```  

> [!NOTE]  
>  <span data-ttu-id="37dbb-198">验证 Fields!Phone.Value 的值没有多余的空格并且类型为 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="37dbb-198">Verify that the value for Fields!Phone.Value has no extra spaces and is of type <xref:System.String>.</span></span>  

#### <a name="lookup"></a><span data-ttu-id="37dbb-199">查找</span><span class="sxs-lookup"><span data-stu-id="37dbb-199">Lookup</span></span>  

-   <span data-ttu-id="37dbb-200">通过指定键字段，您可以使用 `Lookup` 函数为一对一关系（例如键值对）从数据集检索值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-200">By specifying a key field, you can use the `Lookup` function to retrieve a value from a dataset for a one-to-one relationship, for example, a key-value pair.</span></span> <span data-ttu-id="37dbb-201">下面的表达式通过提供用于匹配的产品标识符，显示来自数据集（“Product”）的产品名称：</span><span class="sxs-lookup"><span data-stu-id="37dbb-201">The following expression displays the product name from a dataset ("Product"), given the product identifier to match on:</span></span>  

```  
=Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields!ProductName.Value, "Product")  
```  

#### <a name="lookupset"></a><span data-ttu-id="37dbb-202">LookupSet</span><span class="sxs-lookup"><span data-stu-id="37dbb-202">LookupSet</span></span>  

-   <span data-ttu-id="37dbb-203">通过指定键字段，您可以使用 `LookupSet` 函数为一对多关系从数据集检索一组值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-203">By specifying a key field, you can use the `LookupSet` function to retrieve a set of values from a dataset for a one-to-many relationship.</span></span> <span data-ttu-id="37dbb-204">例如，一个人可以有多个电话号码。</span><span class="sxs-lookup"><span data-stu-id="37dbb-204">For example, a person can have multiple telephone numbers.</span></span> <span data-ttu-id="37dbb-205">在下面的示例中，假定数据集 PhoneList 在每一行中包含一个人员标识符和电话号码。</span><span class="sxs-lookup"><span data-stu-id="37dbb-205">In the following example, assume the dataset PhoneList contains a person identifier and a telephone number in each row.</span></span> <span data-ttu-id="37dbb-206">`LookupSet` 返回值的数组。</span><span class="sxs-lookup"><span data-stu-id="37dbb-206">`LookupSet` returns an array of values.</span></span> <span data-ttu-id="37dbb-207">下面的表达式将返回值合并到单个字符串中，并且显示 ContactID 指定的人士的电话号码的列表：</span><span class="sxs-lookup"><span data-stu-id="37dbb-207">The following expression combines the return values into a single string and displays the list of telephone numbers for the person specified by ContactID:</span></span>  

```  
=Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
```  

####  <a name="conversion-functions"></a><a name="ConversionFunctions"></a><span data-ttu-id="37dbb-208">转换函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-208">Conversion Functions</span></span>  
<span data-ttu-id="37dbb-209">使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数可以将字段从一种数据类型转换为另一种不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="37dbb-209">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to convert a field from the one data type to a different data type.</span></span> <span data-ttu-id="37dbb-210">转换函数可用于将字段的默认数据类型转换为计算所需的数据类型或用于组合文本。</span><span class="sxs-lookup"><span data-stu-id="37dbb-210">Conversion functions can be used to convert the default data type for a field to the data type needed for calculations or to combine text.</span></span>  

-   <span data-ttu-id="37dbb-211">以下表达式将常量 500 转换为十进制类型，以便将其与筛选表达式值字段中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] money 数据类型进行比较。</span><span class="sxs-lookup"><span data-stu-id="37dbb-211">The following expression converts the constant 500 to type Decimal in order to compare it to a [!INCLUDE[tsql](../../includes/tsql-md.md)] money data type in the Value field for a filter expression.</span></span>  

```  
=CDec(500)  
```  

-   <span data-ttu-id="37dbb-212">下面的表达式显示为多值参数 *MySelection*选择的值的数目。</span><span class="sxs-lookup"><span data-stu-id="37dbb-212">The following expression displays the number of values selected for the multivalue parameter *MySelection*.</span></span>  

```  
=CStr(Parameters!MySelection.Count)  
```  

####  <a name="decision-functions"></a><a name="DecisionFunctions"></a><span data-ttu-id="37dbb-213">决策函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-213">Decision Functions</span></span>  

-   <span data-ttu-id="37dbb-214">`Iif` 函数可根据表达式的计算结果（True 或 False）返回两个值中的一个。</span><span class="sxs-lookup"><span data-stu-id="37dbb-214">The `Iif` function returns one of two values depending on whether the expression is true or not.</span></span> <span data-ttu-id="37dbb-215">下面的表达式使用 `Iif` 函数在 `LineTotal` 的值超过 100 时返回布尔值 `True`。</span><span class="sxs-lookup"><span data-stu-id="37dbb-215">The following expression uses the `Iif` function to return a Boolean value of `True` if the value of `LineTotal` exceeds 100.</span></span> <span data-ttu-id="37dbb-216">否则，它将返回 `False`：</span><span class="sxs-lookup"><span data-stu-id="37dbb-216">Otherwise it returns `False`:</span></span>  

```  
=IIF(Fields!LineTotal.Value > 100, True, False)  
```  

-   <span data-ttu-id="37dbb-217">使用多个 `IIF` 函数（也称为“嵌套 IIF”）可以根据 `PctComplete` 的值返回三个值中的一个。</span><span class="sxs-lookup"><span data-stu-id="37dbb-217">Use multiple `IIF` functions (also known as "nested IIFs") to return one of three values depending on the value of `PctComplete`.</span></span> <span data-ttu-id="37dbb-218">下面的表达式可放置在文本框的填充颜色中，从而根据文本框中的值更改背景色。</span><span class="sxs-lookup"><span data-stu-id="37dbb-218">The following expression can be placed in the fill color of a text box to change the background color depending on the value in the text box.</span></span>  

```  
=IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
```  

<span data-ttu-id="37dbb-219">值大于或等于 10 时，显示绿色背景；介于 1 和 9 之间时，显示蓝色背景；小于 1 时，显示红色背景。</span><span class="sxs-lookup"><span data-stu-id="37dbb-219">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, and less than 1 display with a red background.</span></span>  

-   <span data-ttu-id="37dbb-220">还有另一种方法可以实现相同功能，即使用 `Switch` 函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-220">A different way to get the same functionality uses the `Switch` function.</span></span> <span data-ttu-id="37dbb-221">如果您要测试三个或更多条件，`Switch` 函数将非常有用。</span><span class="sxs-lookup"><span data-stu-id="37dbb-221">The `Switch` function is useful when you have three or more conditions to test.</span></span> <span data-ttu-id="37dbb-222">`Switch` 函数可返回与序列中计算结果为 True 的第一个表达式相关联的值：</span><span class="sxs-lookup"><span data-stu-id="37dbb-222">The `Switch` function returns the value associated with the first expression in a series that evaluates to true:</span></span>  

```  
=Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red",)  
```  

<span data-ttu-id="37dbb-223">值大于或等于 10 时，显示绿色背景；介于 1 和 9 之间时，显示蓝色背景；等于 1 时显示黄色背景；小于或等于 0 时，显示红色背景。</span><span class="sxs-lookup"><span data-stu-id="37dbb-223">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, equal to 1 display with a yellow background, and 0 or less display with a red background.</span></span>  

-   <span data-ttu-id="37dbb-224">测试 `ImportantDate` 字段的值，如果该值大于一周，则返回“Red”；否则返回“Blue”。</span><span class="sxs-lookup"><span data-stu-id="37dbb-224">Test the value of the `ImportantDate` field and return "Red" if it is more than a week old, and "Blue" otherwise.</span></span> <span data-ttu-id="37dbb-225">此表达式可用于控制报表项中的文本框的 Color 属性：</span><span class="sxs-lookup"><span data-stu-id="37dbb-225">This expression can be used to control the Color property of a text box in a report item:</span></span>  

```  
=IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
```  

-   <span data-ttu-id="37dbb-226">测试 `PhoneNumber` 字段的值，如果为 `null`（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`），则返回“无值”；否则返回电话号码值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-226">Test the value of the `PhoneNumber` field and return "No Value" if it is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]); otherwise return the phone number value.</span></span> <span data-ttu-id="37dbb-227">此表达式可用于控制报表项中的文本框的值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-227">This expression can be used to control the value of a text box in a report item.</span></span>  

```  
=IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
```  

-   <span data-ttu-id="37dbb-228">测试 `Department` 字段的值，然后返回子报表名称或 `null`（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="37dbb-228">Test the value of the `Department` field and return either a subreport name or a `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="37dbb-229">此表达式可用于条件性钻取子报表。</span><span class="sxs-lookup"><span data-stu-id="37dbb-229">This expression can be used for conditional drillthrough subreports.</span></span>  

```  
=IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
```  

-   <span data-ttu-id="37dbb-230">测试字段值是否为空。</span><span class="sxs-lookup"><span data-stu-id="37dbb-230">Test if a field value is null.</span></span> <span data-ttu-id="37dbb-231">此表达式可用于控制图像报表项的 `Hidden` 属性。</span><span class="sxs-lookup"><span data-stu-id="37dbb-231">This expression can be used to control the `Hidden` property of an image report item.</span></span> <span data-ttu-id="37dbb-232">在下面的示例中，字段 [LargePhoto] 指定的图像仅当字段值非空时才会显示。</span><span class="sxs-lookup"><span data-stu-id="37dbb-232">In the following example, the image specified by the field [LargePhoto] is displayed only if the value of the field is not null.</span></span>  

```  
=IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
```  

-   <span data-ttu-id="37dbb-233">`MonthName` 函数返回一个包含指定月的名称的字符串值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-233">The `MonthName` function returns a string value containing the name of the specified month.</span></span> <span data-ttu-id="37dbb-234">以下示例在“月”字段（当该字段包含的值为 0 时）中显示 NA。</span><span class="sxs-lookup"><span data-stu-id="37dbb-234">The following example displays NA in the Month field when the field contains the value of 0.</span></span>  

```  
IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  

```  

###  <a name="report-functions"></a><a name="ReportFunctions"></a><span data-ttu-id="37dbb-235">报表函数</span><span class="sxs-lookup"><span data-stu-id="37dbb-235">Report Functions</span></span>  
<span data-ttu-id="37dbb-236">在表达式中，您可以添加对使用报表中数据的附加报表函数的引用。</span><span class="sxs-lookup"><span data-stu-id="37dbb-236">In an expression, you can add a reference to additional report functions that manipulate data in a report.</span></span> <span data-ttu-id="37dbb-237">本部分举例说明了其中两个函数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-237">This section provides examples for two of these functions.</span></span> <span data-ttu-id="37dbb-238">有关报表函数和示例的详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-238">For more information about report functions and examples, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  

#####  <a name="sum"></a><a name="Sum"></a><span data-ttu-id="37dbb-239">长度</span><span class="sxs-lookup"><span data-stu-id="37dbb-239">Sum</span></span>  

-   <span data-ttu-id="37dbb-240">`Sum` 函数可以对某个组或数据区域中的值求和。</span><span class="sxs-lookup"><span data-stu-id="37dbb-240">The `Sum` function can total the values in a group or data region.</span></span> <span data-ttu-id="37dbb-241">此函数在组的组头或组尾中非常有用。</span><span class="sxs-lookup"><span data-stu-id="37dbb-241">This function can be useful in the header or footer of a group.</span></span> <span data-ttu-id="37dbb-242">下面的表达式显示 Order 组或数据区域中的数据之和：</span><span class="sxs-lookup"><span data-stu-id="37dbb-242">The following expression displays the sum of data in the Order group or data region:</span></span>  

```  
=Sum(Fields!LineTotal.Value, "Order")  
```  

-   <span data-ttu-id="37dbb-243">还可以使用 `Sum` 函数进行条件聚合计算。</span><span class="sxs-lookup"><span data-stu-id="37dbb-243">You can also use the `Sum` function for conditional aggregate calculations.</span></span> <span data-ttu-id="37dbb-244">例如，如果数据集包含名为 State 的字段，其可能的值为 Not Started、Started、Finished，则将下列表达式放置在组头中时将只计算 Finished 值的聚合总数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-244">For example, if a dataset has a field that is named State with possible values Not Started, Started, Finished, the following expression, when placed in a group header, calculates the aggregate sum for only the value Finished:</span></span>  

```  
=Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
```  

#####  <a name="rownumber"></a><a name="RowNumber"></a><span data-ttu-id="37dbb-245">RowNumber</span><span class="sxs-lookup"><span data-stu-id="37dbb-245">RowNumber</span></span>  

-   <span data-ttu-id="37dbb-246">`RowNumber` 函数，如果用在数据区域内的文本框中，则显示表达式所在文本框中的每个实例的行号。</span><span class="sxs-lookup"><span data-stu-id="37dbb-246">The `RowNumber` function, when used in a text box within a data region, displays the row number for each instance of the text box in which the expression appears.</span></span> <span data-ttu-id="37dbb-247">此函数可用于为表中的各行编号。</span><span class="sxs-lookup"><span data-stu-id="37dbb-247">This function can be useful to number rows in a table.</span></span> <span data-ttu-id="37dbb-248">还可以用于更复杂的情况，如根据行数插入分页符。</span><span class="sxs-lookup"><span data-stu-id="37dbb-248">It can also be useful for more complex tasks, such as providing page breaks based on number of rows.</span></span> <span data-ttu-id="37dbb-249">有关详细信息，请参阅本主题中的 [分页符](#PageBreaks) 。</span><span class="sxs-lookup"><span data-stu-id="37dbb-249">For more information, see [Page Breaks](#PageBreaks) in this topic.</span></span>  

<span data-ttu-id="37dbb-250">为 `RowNumber` 指定的作用域可控制开始重新计数的时间。</span><span class="sxs-lookup"><span data-stu-id="37dbb-250">The scope you specify for `RowNumber` controls when renumbering begins.</span></span> <span data-ttu-id="37dbb-251">`Nothing` 关键字表示该函数将从最外面的数据区域中的第一行开始计数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-251">The `Nothing` keyword indicates that the function will start counting at the first row in the outermost data region.</span></span> <span data-ttu-id="37dbb-252">若要在嵌套数据区域中开始计数，可使用该数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="37dbb-252">To start counting within nested data regions, use the name of the data region.</span></span> <span data-ttu-id="37dbb-253">若要在某个组中开始计数，可使用该组的名称。</span><span class="sxs-lookup"><span data-stu-id="37dbb-253">To start counting within a group, use the name of the group.</span></span>  

```  
=RowNumber(Nothing)  
```  

##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a><span data-ttu-id="37dbb-254">报表数据的外观</span><span class="sxs-lookup"><span data-stu-id="37dbb-254">Appearance of Report Data</span></span>  
<span data-ttu-id="37dbb-255">您可以使用表达式来控制数据在报表中的显示形式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-255">You can use expressions to manipulate how data appears on a report.</span></span> <span data-ttu-id="37dbb-256">例如，可以在一个文本框中显示两个字段的值，显示报表的相关信息，或设置报表中分页符的插入方式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-256">For example, you can display the values of two fields in a single text box, display information about the report, or affect how page breaks are inserted in the report.</span></span>  

###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a><span data-ttu-id="37dbb-257">页眉和页脚</span><span class="sxs-lookup"><span data-stu-id="37dbb-257">Page Headers and Footers</span></span>  
<span data-ttu-id="37dbb-258">在设计报表时，可能需要在报表表尾中显示报表名称和页码。</span><span class="sxs-lookup"><span data-stu-id="37dbb-258">When designing a report, you may want to display the name of the report and page number in the report footer.</span></span> <span data-ttu-id="37dbb-259">为此，可使用以下表达式：</span><span class="sxs-lookup"><span data-stu-id="37dbb-259">To do this, you can use the following expressions:</span></span>  

-   <span data-ttu-id="37dbb-260">下面的表达式提供报表的名称及其运行时间。</span><span class="sxs-lookup"><span data-stu-id="37dbb-260">The following expression provides the name of the report and the time it was run.</span></span> <span data-ttu-id="37dbb-261">可以将该表达式放置在报表表尾或表体的文本框中。</span><span class="sxs-lookup"><span data-stu-id="37dbb-261">It can be placed in a text box in the report footer or in the body of the report.</span></span> <span data-ttu-id="37dbb-262">其时间格式为短日期形式的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 格式设置字符串：</span><span class="sxs-lookup"><span data-stu-id="37dbb-262">The time is formatted with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] formatting string for short date:</span></span>  

```  
=Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
```  

-   <span data-ttu-id="37dbb-263">下面的表达式放置在报表表尾的文本框中，提供报表的页码和总页数：</span><span class="sxs-lookup"><span data-stu-id="37dbb-263">The following expression, placed in a text box in the footer of a report, provides page number and total pages in the report:</span></span>  

```  
=Globals.PageNumber & " of " & Globals.TotalPages  
```  

<span data-ttu-id="37dbb-264">下面的示例说明如何在表头中显示页面中的第一个值和最后一个值，类似于目录列表的形式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-264">The following examples describe how to display the first and last values from a page in the page header, similar to what you might find in a directory listing.</span></span> <span data-ttu-id="37dbb-265">该示例假设存在一个包含名为 `LastName`的文本框的数据区域。</span><span class="sxs-lookup"><span data-stu-id="37dbb-265">The example assumes a data region that contains a text box named `LastName`.</span></span>  

-   <span data-ttu-id="37dbb-266">下面的表达式放置在表头左侧的文本框中，提供页面中 `LastName` 文本框的第一个值：</span><span class="sxs-lookup"><span data-stu-id="37dbb-266">The following expression, placed in a text box on the left side of the page header, provides the first value of the `LastName` text box on the page:</span></span>  

```  
=First(ReportItems("LastName").Value)  
```  

-   <span data-ttu-id="37dbb-267">下面的表达式放置在表头右侧的文本框中，提供页面中的 `LastName` 文本框的最后一个值：</span><span class="sxs-lookup"><span data-stu-id="37dbb-267">The following expression, placed in a text box on the right side of the page header, provides the last value of the `LastName` text box on the page:</span></span>  

```  
=Last(ReportItems("LastName").Value)  
```  

<span data-ttu-id="37dbb-268">下面的示例说明如何显示页总页数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-268">The following example describes how to display a page total.</span></span> <span data-ttu-id="37dbb-269">该示例假设存在一个包含名为 `Cost`的文本框的数据区域。</span><span class="sxs-lookup"><span data-stu-id="37dbb-269">The example assumes a data region that contains a text box named `Cost`.</span></span>  

-   <span data-ttu-id="37dbb-270">下面的表达式放置在表头或表尾中，提供页面上 `Cost` 文本框中的值的总和：</span><span class="sxs-lookup"><span data-stu-id="37dbb-270">The following expression, placed in the page header or footer, provides the sum of the values in the `Cost` text box for the page:</span></span>  

```  
=Sum(ReportItems("Cost").Value)  
```  

> [!NOTE]  
>  <span data-ttu-id="37dbb-271">对于表头或表尾中的每个表达式，只能引用一个报表项。</span><span class="sxs-lookup"><span data-stu-id="37dbb-271">You can refer to only one report item per expression in a page header or footer.</span></span> <span data-ttu-id="37dbb-272">还可以引用表头和表尾表达式中的文本框名称，但不能引用文本框中的实际数据表达式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-272">Also, you can refer to the text box name, but not the actual data expression within the text box, in page header and footer expressions.</span></span>  

###  <a name="page-breaks"></a><a name="PageBreaks"></a><span data-ttu-id="37dbb-273">分页符</span><span class="sxs-lookup"><span data-stu-id="37dbb-273">Page Breaks</span></span>  
<span data-ttu-id="37dbb-274">在某些报表中，可能需要在指定行数之后、特定的组或报表项中插入分页符。</span><span class="sxs-lookup"><span data-stu-id="37dbb-274">In some reports, you may want to place a page break at the end of a specified number of rows instead of, or in addition to, on groups or report items.</span></span> <span data-ttu-id="37dbb-275">为此，您可以创建一个包含组或您希望的详细记录的组，然后在该组中添加一个分页符，再添加一个组表达式以按指定的行数进行分组。</span><span class="sxs-lookup"><span data-stu-id="37dbb-275">To do this, create a group that contains the groups or detail records you want, add a page break to the group, and then add a group expression to group by a specified number of rows.</span></span>  

-   <span data-ttu-id="37dbb-276">下面的表达式放置在组表达式中，为每 25 行指定一个编号。</span><span class="sxs-lookup"><span data-stu-id="37dbb-276">The following expression, when placed in the group expression, assigns a number to each set of 25 rows.</span></span> <span data-ttu-id="37dbb-277">如果为组定义了分页符，则此表达式会每隔 25 行插入一个分页符。</span><span class="sxs-lookup"><span data-stu-id="37dbb-277">When a page break is defined for the group, this expression results in a page break every 25 rows.</span></span>  

```  
=Ceiling(RowNumber(Nothing)/25)  
```  

<span data-ttu-id="37dbb-278">若要允许用户设置每页行数的值，请按创建一个名称为 `RowsPerPage` 的参数，并基于该参数生成组表达式，如下面的表达式所示：</span><span class="sxs-lookup"><span data-stu-id="37dbb-278">To allow the user to set a value for the number of rows per page, create a parameter named `RowsPerPage` and base the group expression on the parameter, as shown in the following expression:</span></span>  

```  
=Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
```  

<span data-ttu-id="37dbb-279">有关为组设置分页符的详细信息，请参阅[添加分页符（报表生成器和 SSRS）](add-a-page-break-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-279">For more information about setting page breaks for a group, see [Add a Page Break &#40;Report Builder and SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md).</span></span>  

##  <a name="properties"></a><a name="Properties"></a><span data-ttu-id="37dbb-280">属性</span><span class="sxs-lookup"><span data-stu-id="37dbb-280">Properties</span></span>  
<span data-ttu-id="37dbb-281">表达式不仅用于显示文本框中的数据。</span><span class="sxs-lookup"><span data-stu-id="37dbb-281">Expressions are not only used to display data in text boxes.</span></span> <span data-ttu-id="37dbb-282">还可以用于更改将属性应用于报表项的方式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-282">They can also be used to change how properties are applied to report items.</span></span> <span data-ttu-id="37dbb-283">您可以更改报表项的样式信息，或更改其可见性。</span><span class="sxs-lookup"><span data-stu-id="37dbb-283">You can change style information for a report item, or change its visibility.</span></span>  

###  <a name="formatting"></a><a name="Formatting"></a><span data-ttu-id="37dbb-284">样式</span><span class="sxs-lookup"><span data-stu-id="37dbb-284">Formatting</span></span>  

-   <span data-ttu-id="37dbb-285">如果下面的表达式用于文本框的 Color 属性中，则可以根据 `Profit` 字段的值更改文本的颜色：</span><span class="sxs-lookup"><span data-stu-id="37dbb-285">The following expression, when used in the Color property of a text box, changes the color of the text depending on the value of the `Profit` field:</span></span>  

```  
=Iif(Fields!Profit.Value < 0, "Red", "Black")  
```  

<span data-ttu-id="37dbb-286">还可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 对象变量 `Me`。</span><span class="sxs-lookup"><span data-stu-id="37dbb-286">You can also use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] object variable `Me`.</span></span> <span data-ttu-id="37dbb-287">此变量是另一种引用文本框的值的方法。</span><span class="sxs-lookup"><span data-stu-id="37dbb-287">This variable is another way of referring to the value of a text box.</span></span>  

`=Iif(Me.Value < 0, "Red", "Black")`  

-   <span data-ttu-id="37dbb-288">如果下面的表达式用于数据区域中的报表项的 BackgroundColor 属性中，则可以将每一行的背景色在淡绿色与白色之间变换：</span><span class="sxs-lookup"><span data-stu-id="37dbb-288">The following expression, when used in the BackgroundColor property of a report item in a data region, alternates the background color of each row between pale green and white:</span></span>  

```  
=Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
```  

<span data-ttu-id="37dbb-289">如果将表达式用于指定的作用域，则可能必须指明聚合函数的数据集：</span><span class="sxs-lookup"><span data-stu-id="37dbb-289">If you are using an expression for a specified scope, you may have to indicate the dataset for the aggregate function:</span></span>  

```  
=Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
```  

> [!NOTE]  
>  <span data-ttu-id="37dbb-290">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor 枚举的可用颜色。</span><span class="sxs-lookup"><span data-stu-id="37dbb-290">Available colors come from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor enumeration.</span></span>  

### <a name="chart-colors"></a><span data-ttu-id="37dbb-291">图表颜色</span><span class="sxs-lookup"><span data-stu-id="37dbb-291">Chart Colors</span></span>  
<span data-ttu-id="37dbb-292">若要指定形状图的颜色，可以使用自定义代码控制颜色映射为数据点值的顺序。</span><span class="sxs-lookup"><span data-stu-id="37dbb-292">To specify colors for a Shape chart, you can use custom code to control the order that colors are mapped to data point values.</span></span> <span data-ttu-id="37dbb-293">这有助于您对具有相同类别组的多个图表使用一致的颜色。</span><span class="sxs-lookup"><span data-stu-id="37dbb-293">This helps you use consistent colors for multiple charts that have the same category groups.</span></span> <span data-ttu-id="37dbb-294">有关详细信息，请参阅[对多个形状图指定一致的颜色（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-294">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  

###  <a name="visibility"></a><a name="Visibility"></a><span data-ttu-id="37dbb-295">可见</span><span class="sxs-lookup"><span data-stu-id="37dbb-295">Visibility</span></span>  
<span data-ttu-id="37dbb-296">您可以使用报表项的可见性属性来显示和隐藏报表中的项。</span><span class="sxs-lookup"><span data-stu-id="37dbb-296">You can show and hide items in a report using the visibility properties for the report item.</span></span> <span data-ttu-id="37dbb-297">在诸如表的数据区域中，可以根据表达式中的值在一开始隐藏详细信息行。</span><span class="sxs-lookup"><span data-stu-id="37dbb-297">In a data region such as a table, you can initially hide detail rows based on the value in an expression.</span></span>  

-   <span data-ttu-id="37dbb-298">如果下面的表达式用于组中详细信息行的初始可见性，则可以在 `PctQuota` 字段中显示超过 90% 的所有销售的详细信息行：</span><span class="sxs-lookup"><span data-stu-id="37dbb-298">The following expression, when used for initial visibility of detail rows in a group, shows the detail rows for all sales exceeding 90 percent in the `PctQuota` field:</span></span>  

```  
=Iif(Fields!PctQuota.Value>.9, False, True)  
```  

-   <span data-ttu-id="37dbb-299">如果在表的 Hidden 属性中设置下面的表达式，则仅当该表多于 12 行时才会显示：</span><span class="sxs-lookup"><span data-stu-id="37dbb-299">The following expression, when set in the Hidden property of a table, shows the table only if it has more than 12 rows:</span></span>  

```  
=IIF(CountRows()>12,false,true)  
```  

-   <span data-ttu-id="37dbb-300">如果在列的属性中设置了下面的表达式 `Hidden` ，则只有在从数据源中检索到数据后，该字段存在于报表数据集中时才显示该列：</span><span class="sxs-lookup"><span data-stu-id="37dbb-300">The following expression, when set in the `Hidden` property of a column, shows the column only if the field exists in the report dataset after the data is retrieved from the data source:</span></span>  

```  
=IIF(Fields!Column_1.IsMissing, true, false)  
```  

###  <a name="urls"></a><a name="Hyperlinks"></a><span data-ttu-id="37dbb-301">Url</span><span class="sxs-lookup"><span data-stu-id="37dbb-301">URLs</span></span>  
<span data-ttu-id="37dbb-302">可以使用报表数据自定义 URL，还可以有条件地控制是否将 URL 添加为对文本框的操作。</span><span class="sxs-lookup"><span data-stu-id="37dbb-302">You can customize URLs by using report data and also conditionally control whether URLs are added as an action for a text box.</span></span>  

-   <span data-ttu-id="37dbb-303">如果将下面的表达式用作对文本框的操作，则可以生成一个自定义 URL，它可将数据集字段 `EmployeeID` 指定为 URL 参数。</span><span class="sxs-lookup"><span data-stu-id="37dbb-303">The following expression, when used as an action on a text box, generates a customized URL that specifies the dataset field `EmployeeID` as a URL parameter.</span></span>  

```  
="http://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
```  

<span data-ttu-id="37dbb-304">有关详细信息，请参阅[向 URL 添加超链接（报表生成器和 SSRS）](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-304">For more information, see [Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md).</span></span>  

-   <span data-ttu-id="37dbb-305">下面的表达式可以有条件地控制是否要在文本框中添加 URL。</span><span class="sxs-lookup"><span data-stu-id="37dbb-305">The following expression conditionally controls whether to add a URL in a text box.</span></span> <span data-ttu-id="37dbb-306">此表达式的计算结果取决于一个名为 `IncludeURLs` 的参数，该参数允许用户决定是否在报表中包括活动 URL。</span><span class="sxs-lookup"><span data-stu-id="37dbb-306">This expression depends on a parameter named `IncludeURLs` that allows a user to decide whether to include active URLs in a report.</span></span> <span data-ttu-id="37dbb-307">此表达式设置为一个对文本框的操作。</span><span class="sxs-lookup"><span data-stu-id="37dbb-307">This expression is set as an action on a text box.</span></span> <span data-ttu-id="37dbb-308">通过将参数设置为 False，然后再查看报表，可以导出不包含超链接的 Microsoft Excel 报表。</span><span class="sxs-lookup"><span data-stu-id="37dbb-308">By setting the parameter to False and then viewing the report, you can export the report Microsoft Excel without hyperlinks.</span></span>  

```  
=IIF(Parameters!IncludeURLs.Value,"http://adventure-works.com/productcatalog",Nothing)  
```  

##  <a name="report-data"></a><a name="ReportData"></a><span data-ttu-id="37dbb-309">报表数据</span><span class="sxs-lookup"><span data-stu-id="37dbb-309">Report Data</span></span>  
<span data-ttu-id="37dbb-310">您可使用表达式来处理报表中所使用的数据。</span><span class="sxs-lookup"><span data-stu-id="37dbb-310">Expressions can be used to manipulate the data that is used in the report.</span></span> <span data-ttu-id="37dbb-311">可以引用参数和其他报表信息。</span><span class="sxs-lookup"><span data-stu-id="37dbb-311">You can refer to parameters and other report information.</span></span> <span data-ttu-id="37dbb-312">甚至可以更改用于检索报表数据的查询。</span><span class="sxs-lookup"><span data-stu-id="37dbb-312">You can even change the query that is used to retrieve data for the report.</span></span>  

###  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="37dbb-313">Parameters</span><span class="sxs-lookup"><span data-stu-id="37dbb-313">Parameters</span></span>  
<span data-ttu-id="37dbb-314">您可以在参数中使用表达式来更改参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-314">You can use expressions in a parameter to vary the default value for the parameter.</span></span> <span data-ttu-id="37dbb-315">例如，可以根据用于运行报表的用户 ID，使用参数来筛选某个特定用户的数据。</span><span class="sxs-lookup"><span data-stu-id="37dbb-315">For example, you can use a parameter to filter data to a particular user based on the user ID that is used to run the report.</span></span>  

-   <span data-ttu-id="37dbb-316">下面的表达式如果用作参数的默认值，可以收集运行报表的用户的 ID：</span><span class="sxs-lookup"><span data-stu-id="37dbb-316">The following expression, when used as the default value for a parameter, collects the user ID of the person running the report:</span></span>  

```  
=User!UserID  
```  

-   <span data-ttu-id="37dbb-317">若要在查询参数、筛选表达式、文本框或其他报表区域中引用参数，请使用 `Parameters` 全局集合。</span><span class="sxs-lookup"><span data-stu-id="37dbb-317">To refer to a parameter in a query parameter, filter expression, text box, or other area of the report, use the `Parameters` global collection.</span></span> <span data-ttu-id="37dbb-318">此示例假定参数的名称为 *Department*：</span><span class="sxs-lookup"><span data-stu-id="37dbb-318">This example assumes that the parameter is named *Department*:</span></span>  

```  
=Parameters!Department.Value  
```  

-   <span data-ttu-id="37dbb-319">可在报表中创建参数，但需要设置为隐藏。</span><span class="sxs-lookup"><span data-stu-id="37dbb-319">Parameters can be created in a report but set to hidden.</span></span> <span data-ttu-id="37dbb-320">报表在报表服务器上运行时，该参数不会显示在工具栏中，并且报表读者无法更改默认值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-320">When the report runs on the report server, the parameter does not appear in the toolbar and the report reader cannot change the default value.</span></span> <span data-ttu-id="37dbb-321">您可以将设置为默认值的隐藏参数用作自定义常量。</span><span class="sxs-lookup"><span data-stu-id="37dbb-321">You can use a hidden parameter set to a default value as custom constant.</span></span> <span data-ttu-id="37dbb-322">可以在任何表达式中使用此值，包括字段表达式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-322">You can use this value in any expression, including a field expression.</span></span> <span data-ttu-id="37dbb-323">下面的表达式标识由 *ParameterField*参数的默认参数值指定的字段：</span><span class="sxs-lookup"><span data-stu-id="37dbb-323">The following expression identifies the field specified by the default parameter value for the parameter named *ParameterField*:</span></span>  

```  
=Fields(Parameters!ParameterField.Value).Value  
```  

## <a name="custom-code"></a><a name="CustomCode"></a><span data-ttu-id="37dbb-324">自定义代码</span><span class="sxs-lookup"><span data-stu-id="37dbb-324">Custom Code</span></span>

<span data-ttu-id="37dbb-325">您可以在报表中使用自定义代码。</span><span class="sxs-lookup"><span data-stu-id="37dbb-325">You can use custom code in a report.</span></span> <span data-ttu-id="37dbb-326">自定义代码嵌入在报表中，或存储在报表使用的自定义程序集中。</span><span class="sxs-lookup"><span data-stu-id="37dbb-326">Custom code is either embedded in a report or stored in a custom assembly which is used in the report.</span></span> <span data-ttu-id="37dbb-327">有关自定义代码的详细信息，请参阅[报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-327">For more information about custom code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  

### <a name="using-group-variables-for-custom-aggregation"></a><span data-ttu-id="37dbb-328">使用组变量自定义聚合</span><span class="sxs-lookup"><span data-stu-id="37dbb-328">Using Group Variables for Custom Aggregation</span></span>

<span data-ttu-id="37dbb-329">您可以初始化特定组作用域的本地组变量的值，然后在表达式中包含对该变量的引用。</span><span class="sxs-lookup"><span data-stu-id="37dbb-329">You can initialize the value for a group variable that is local to a particular group scope and then include a reference to that variable in expressions.</span></span> <span data-ttu-id="37dbb-330">可以将组变量和自定义代码一起使用的方法之一是实现自定义聚合。</span><span class="sxs-lookup"><span data-stu-id="37dbb-330">One of the ways that you can use a group variable with custom code is to implement a custom aggregate.</span></span> <span data-ttu-id="37dbb-331">有关详细信息，请参阅 [Using Group Variables in Reporting Services 2008 for Custom Aggregation](https://go.microsoft.com/fwlink/?LinkId=128714)（在 Reporting Services 2008 使用组变量自定义聚合）。</span><span class="sxs-lookup"><span data-stu-id="37dbb-331">For more information, see [Using Group Variables in Reporting Services 2008 for Custom Aggregation](https://go.microsoft.com/fwlink/?LinkId=128714).</span></span>  

<span data-ttu-id="37dbb-332">有关变量的详细信息，请参阅 [报表和组变量集合引用（报表生成器和 SSRS）](built-in-collections-report-and-group-variables-references-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbb-332">For more information about variables, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).</span></span>  

## <a name="suppressing-null-or-zero-values-at-run-time"></a><span data-ttu-id="37dbb-333">取消运行时的 Null 值或零值</span><span class="sxs-lookup"><span data-stu-id="37dbb-333">Suppressing Null or Zero Values at Run Time</span></span>

<span data-ttu-id="37dbb-334">处理报表时，表达式中某些值的计算结果可能为 Null 值或未定义。</span><span class="sxs-lookup"><span data-stu-id="37dbb-334">Some values in an expression can evaluate to null or undefined at report processing time.</span></span> <span data-ttu-id="37dbb-335">这将创建运行时错误，从而导致在文本框中显示 **#Error** ，而不是计算后的表达式。</span><span class="sxs-lookup"><span data-stu-id="37dbb-335">This can create run-time errors that result in **#Error** displaying in the text box instead of the evaluated expression.</span></span> <span data-ttu-id="37dbb-336">`IIF` 函数对此行为特别敏感，因为它不同于 If-Then-Else 语句，`IIF` 语句的每一部分在传递到测试 `true` 或 `false` 的例程之前，都要进行计算（包括函数调用）。</span><span class="sxs-lookup"><span data-stu-id="37dbb-336">The `IIF` function is particularly sensitive to this behavior because, unlike an If-Then-Else statement, each part of the `IIF` statement is evaluated (including function calls) before being passed to the routine that tests for `true` or `false`.</span></span> <span data-ttu-id="37dbb-337">如果 `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 为 NOTHING，则语句 **将在所呈现的报表中生成** #Error `Fields!Sales.Value` 。</span><span class="sxs-lookup"><span data-stu-id="37dbb-337">The statement `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` generates **#Error** in the rendered report if `Fields!Sales.Value` is NOTHING.</span></span>  

<span data-ttu-id="37dbb-338">若要避免此情况，请使用以下策略之一：</span><span class="sxs-lookup"><span data-stu-id="37dbb-338">To avoid this condition, use one of the following strategies:</span></span>  

-   <span data-ttu-id="37dbb-339">如果字段 B 的值为 0 或未定义，则将分子设置为 0，分母设置为 1；否则将分子设置为字段 A 的值，将分母设置为字段 B 的值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-339">Set the numerator to 0 and the denominator to 1 if the value for field B is 0 or undefined; otherwise, set the numerator to the value for field A and the denominator to the value for field B.</span></span>  

```  
=IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
```  

-   <span data-ttu-id="37dbb-340">使用自定义代码函数返回表达式的值。</span><span class="sxs-lookup"><span data-stu-id="37dbb-340">Use a custom code function to return the value for the expression.</span></span> <span data-ttu-id="37dbb-341">下面的示例返回当前值和先前值之间的百分比差异。</span><span class="sxs-lookup"><span data-stu-id="37dbb-341">The following example returns the percentage difference between a current value and a previous value.</span></span> <span data-ttu-id="37dbb-342">这不但可用于计算任意两个连续值之间的差异，还可以处理第一次比较（无先前值的情况）的边界情况以及先前值与当前值中有一个为 `null`（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`）的情况。</span><span class="sxs-lookup"><span data-stu-id="37dbb-342">This can be used to calculate the difference between any two successive values and it handles the edge case of the first comparison (when there is no previous value) and cases whether either the previous value or the current value is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  

```  
Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
     If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
          Return Nothing  
     Else if PreviousValue = 0 OR CurrentValue = 0 Then  
          Return Nothing  
     Else
          Return (CurrentValue - PreviousValue) / CurrentValue  
     End If  
End Function  
```  

<span data-ttu-id="37dbb-343">下面的表达式显示如何针对“ColumnGroupByYear”容器（组或数据区域）从文本框调用此自定义代码。</span><span class="sxs-lookup"><span data-stu-id="37dbb-343">The following expression shows how to call this custom code from a text box, for the "ColumnGroupByYear" container (group or data region).</span></span>  

```  
=Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
```  

<span data-ttu-id="37dbb-344">这有助于避免发生运行时异常。</span><span class="sxs-lookup"><span data-stu-id="37dbb-344">This helps to avoid run-time exceptions.</span></span> <span data-ttu-id="37dbb-345">您现在可以在文本框的 `Color` 属性中使用 `=IIF(Me.Value < 0, "red", "black")` 之类的表达式，以便有条件地基于这些值是大于还是小于 0 来显示文本。</span><span class="sxs-lookup"><span data-stu-id="37dbb-345">You can now use an expression like `=IIF(Me.Value < 0, "red", "black")` in the `Color` property of the text box to conditionally the display text based on whether the values are greater than or less than 0.</span></span>  

## <a name="see-also"></a><span data-ttu-id="37dbb-346">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37dbb-346">See Also</span></span>

- [<span data-ttu-id="37dbb-347">筛选器公式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-347">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="37dbb-348">组表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-348">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="37dbb-349">在报表中使用表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-349">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)
- [<span data-ttu-id="37dbb-350">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-350">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)
- [<span data-ttu-id="37dbb-351">常用筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37dbb-351">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)