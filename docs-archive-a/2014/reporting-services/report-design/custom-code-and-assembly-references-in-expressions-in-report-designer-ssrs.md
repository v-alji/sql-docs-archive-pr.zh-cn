---
title: 报表设计器的表达式中的自定义代码和程序集引用 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- items [Reporting Services], expressions
- data [Reporting Services], expressions
- expressions [Reporting Services], about expressions
- expressions [Reporting Services]
- SSRS, expressions
- formulas [Reporting Services]
- data manipulation [Reporting Services]
- SQL Server Reporting Services, expressions
ms.assetid: ae8a0166-2ccc-45f4-8d28-c150da7b73de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f895d1ecc569092dfbae22b514d3470e020b94d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691634"
---
# <a name="custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs"></a><span data-ttu-id="2ad9e-102">报表设计器的表达式中的自定义代码和程序集引用 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="2ad9e-102">Custom Code and Assembly References in Expressions in Report Designer (SSRS)</span></span>
  <span data-ttu-id="2ad9e-103">您可以添加对报表中嵌入的自定义代码的引用，或添加对生成并保存到您的计算机并且部署到报表服务器的自定义程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-103">You can add references to custom code embedded in a report or to custom assemblies that you build and save to your computer and deploy to the report server.</span></span> <span data-ttu-id="2ad9e-104">对于自定义常量、复杂的函数，或在一个报表中多次使用的函数，可使用嵌入代码。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-104">Use embedded code for custom constants, complex functions or functions that are used multiple times in a single report.</span></span> <span data-ttu-id="2ad9e-105">可以使用自定义代码程序集在一个位置中维护代码，并共享该代码以便由多个报表使用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-105">Use custom code assemblies to maintain code in a single place and share it for use by multiple reports.</span></span> <span data-ttu-id="2ad9e-106">自定义代码可包含新的自定义常量、变量、函数或子例程。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-106">Custom code can include new custom constants, variables, functions, or subroutines.</span></span> <span data-ttu-id="2ad9e-107">可以包含对内置集合（例如，Parameters 集合）的只读引用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-107">You can include read-only references to built-in collections such as the Parameters collection.</span></span> <span data-ttu-id="2ad9e-108">但是，无法将报表数据值集传递给自定义函数；特别要指出的是，不支持自定义聚合。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-108">However, you cannot pass sets of report data values to custom functions; specifically, custom aggregates are not supported.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2ad9e-109">对于在运行时计算一次以及希望在整个报表处理期间都保留相同值的时效性计算，请考虑使用报表变量或组变量。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-109">For time-sensitive calculations that are evaluated once at run-time and that you want to remain the same value throughout report processing, consider whether to use a report variable or group variable.</span></span> <span data-ttu-id="2ad9e-110">有关详细信息，请参阅[报表和组变量集合引用（报表生成器和 SSRS）](built-in-collections-report-and-group-variables-references-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-110">For more information, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).</span></span>  
  
 <span data-ttu-id="2ad9e-111">报表设计器是用于向报表中添加自定义代码的首选创作环境。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-111">Report Designer is the preferred authoring environment to use to add custom code to a report.</span></span> <span data-ttu-id="2ad9e-112">报表生成器支持处理具有有效表达式的报表，也支持处理包括对报表服务器上自定义程序集的引用的报表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-112">Report Builder supports processing reports that have valid expressions, or that include references to custom assemblies on a report server.</span></span> <span data-ttu-id="2ad9e-113">报表生成器不提供添加对自定义程序集的引用的方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-113">Report Builder does not provide a way to add a reference to a custom assembly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ad9e-114">请注意，在报表服务器的升级过程中，依赖自定义程序集的报表可能需要额外的步骤才能完成升级。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-114">Be aware that during an upgrade of a report server, reports that depend on custom assemblies might require additional steps to complete the upgrade.</span></span> <span data-ttu-id="2ad9e-115">有关详细信息，请参阅 [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-115">For more information, see [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="working-with-custom-code-in-report-builder"></a><a name="RB3"></a><span data-ttu-id="2ad9e-116">在报表生成器中使用自定义代码</span><span class="sxs-lookup"><span data-stu-id="2ad9e-116">Working with Custom Code in Report Builder</span></span>  
 <span data-ttu-id="2ad9e-117">在报表生成器中，您可以从报表服务器中打开包含对自定义程序集的引用的报表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-117">In Report Builder, you can open a report from a report server that includes references to custom assemblies.</span></span> <span data-ttu-id="2ad9e-118">例如，您可以编辑通过使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的报表设计器创建和部署的报表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-118">For example, you can edit reports that are created and deployed by using Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="2ad9e-119">必须将自定义程序集部署到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-119">The custom assemblies must be deployed to the report server.</span></span>  
  
 <span data-ttu-id="2ad9e-120">您不能执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="2ad9e-120">You cannot do the following:</span></span>  
  
1.  <span data-ttu-id="2ad9e-121">向报表中添加引用或类成员实例。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-121">Add references or class member instances to a report.</span></span>  
  
2.  <span data-ttu-id="2ad9e-122">在本地模式下预览具有对自定义程序集的引用的报表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-122">Preview a report with references to custom assemblies in local mode.</span></span>  
  
##  <a name="including-references-to-commonly-used-functions"></a><a name="Common"></a><span data-ttu-id="2ad9e-123">包括对常用函数的引用</span><span class="sxs-lookup"><span data-stu-id="2ad9e-123">Including References to Commonly Used Functions</span></span>  
 <span data-ttu-id="2ad9e-124">使用 **“表达式”** 对话框查看内置到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的常见函数分类列表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-124">Use the **Expression** dialog box to view a categorized list of common functions built-in to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="2ad9e-125">展开 **“常见函数”** 并单击一个类别时， **“项”** 窗格显示表达式中包括的函数的列表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-125">When you expand **Common Functions** and click a category, the **Item** pane displays the list of functions that you include in an expression.</span></span> <span data-ttu-id="2ad9e-126">常见函数包括 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Math> 和 <xref:System.Convert> 命名空间和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 运行时库函数中的类。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-126">The common functions include classes from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Math> and <xref:System.Convert> namespaces and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library functions.</span></span> <span data-ttu-id="2ad9e-127">为方便起见，您可以在 **“表达式”** 对话框中查看最常用的函数，这些函数按以下类别排列：文本、日期和时间、数学函数、检查函数、程序流函数、聚合函数、财务函数、转换函数和杂项函数。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-127">For convenience, you can view the most commonly used functions in the **Expression** dialog box, where they are listed by category: Text, Date and Time, Math, Inspection, Program Flow, Aggregate, Financial, Conversion, and Miscellaneous.</span></span> <span data-ttu-id="2ad9e-128">不太常用的函数未显示在列表中，但仍然可以用在表达式中。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-128">Less commonly used functions do not appear in the list but can still be used in an expression.</span></span>  
  
 <span data-ttu-id="2ad9e-129">若要使用内置函数，请双击“项”窗格中的函数名称。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-129">To use a built-in function, double-click the function name in the Item pane.</span></span> <span data-ttu-id="2ad9e-130">“说明”窗格中显示该函数的说明，“示例”窗格中显示函数调用的示例。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-130">A description of the function appears in the Description pane and an example of the function call appears in the Example pane.</span></span> <span data-ttu-id="2ad9e-131">在 "代码" 窗格中，在键入函数名称后跟左括号\*\* (\*\* 后，IntelliSense 将帮助显示函数调用的每个有效语法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-131">In the code pane, when you type the function name followed by a left parenthesis **(**, the IntelliSense help displays each valid syntax for the function call.</span></span> <span data-ttu-id="2ad9e-132">例如，若要计算表中一个名为 `Quantity` 的字段的最大值，首先将简单表达式 `=Max(` 添加到“代码”窗格，然后使用智能标记查看该函数调用的所有可能的有效语法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-132">For example, to calculate the maximum value for a field named `Quantity` in a table, add the simple expression `=Max(` to the Code pane, and then use the smart tags to view all possible valid syntaxes for the function call.</span></span> <span data-ttu-id="2ad9e-133">若要完成本示例，请键入 `=Max(Fields!Quantity.Value)`。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-133">To complete this example, type `=Max(Fields!Quantity.Value)`.</span></span>  
  
 <span data-ttu-id="2ad9e-134">有关每个函数的详细信息，请参阅 <xref:System.Math>、 <xref:System.Convert>和 MSDN 中的 [Visual Basic 运行时库成员](https://go.microsoft.com/fwlink/?LinkId=198941) 。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-134">For more information about each function, see <xref:System.Math>, <xref:System.Convert>, and [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  
  
##  <a name="including-references-to-less-commonly-used-functions"></a><a name="NotCommon"></a><span data-ttu-id="2ad9e-135">包括对不太常用函数的引用</span><span class="sxs-lookup"><span data-stu-id="2ad9e-135">Including References to Less Commonly Used Functions</span></span>  
 <span data-ttu-id="2ad9e-136">若要包括一个对不太常用的 CLR 命名空间的引用，必须使用完全限定引用，例如 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-136">To include a reference to other less commonly used CLR namespaces, you must use a fully qualified reference, for example, <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="2ad9e-137">对于这些不太常用的函数， **“表达式”** 对话框的“代码”窗格不支持 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-137">IntelliSense is not supported in the code pane of the **Expression** dialog box for these less commonly used functions.</span></span>  
  
 <span data-ttu-id="2ad9e-138">有关详细信息，请参阅 [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) （Visual Basic 运行时库成员）。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-138">For more information, see [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  
  
##  <a name="including-references-to-external-assemblies"></a><a name="External"></a> <span data-ttu-id="2ad9e-139">包括对外部程序集的引用</span><span class="sxs-lookup"><span data-stu-id="2ad9e-139">Including References to External Assemblies</span></span>  
 <span data-ttu-id="2ad9e-140">若要包括对外部程序集中的类的引用，必须标识报表处理器的程序集。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-140">To include a reference to a class in an external assembly, you must identify the assembly for the report processor.</span></span> <span data-ttu-id="2ad9e-141">使用 **“报表属性”** 对话框的 **“引用”** 页指定要添加到报表中的程序集的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-141">Use the **References** page of the **Report Properties** dialog box to specify the fully qualified name of the assembly to add to the report.</span></span> <span data-ttu-id="2ad9e-142">在表达式中，必须使用程序集中的类的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-142">In your expression, you must use the fully qualified name for the class in the assembly.</span></span> <span data-ttu-id="2ad9e-143">外部程序集中的类不显示在 **“表达式”** 对话框中，您必须提供正确无误的类名称。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-143">Classes in an external assembly do not appear in the **Expression** dialog box; you must provide the correct name for the class.</span></span> <span data-ttu-id="2ad9e-144">完全限定名称包括命名空间、类名称和成员名称。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-144">A fully qualified name includes the namespace, the class name, and the member name.</span></span>  
  
##  <a name="including-embedded-code"></a><a name="Embedded"></a> <span data-ttu-id="2ad9e-145">包括嵌入代码</span><span class="sxs-lookup"><span data-stu-id="2ad9e-145">Including Embedded Code</span></span>  
 <span data-ttu-id="2ad9e-146">若要将嵌入代码添加到某个报表，请使用 **“报表属性”** 对话框的“代码”选项卡。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-146">To add embedded code to a report, use the Code tab of the **Report Properties** dialog box.</span></span> <span data-ttu-id="2ad9e-147">创建的代码块可以包含多个方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-147">The code block you create can contain multiple methods.</span></span> <span data-ttu-id="2ad9e-148">嵌入代码中的方法必须采用编写 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ，并且必须是基于实例的。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-148">Methods in embedded code must be written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] and must be instance-based.</span></span> <span data-ttu-id="2ad9e-149">对于 System.Convert 和 System.Math namespaces 命名空间，报表处理器会自动添加引用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-149">The report processor automatically adds references for the System.Convert and System.Math namespaces.</span></span> <span data-ttu-id="2ad9e-150">使用 **“报表属性”** 对话框的 **“引用”** 页添加其他程序集引用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-150">Use the **References** page of the **Report Properties** dialog box to add additional assembly references.</span></span> <span data-ttu-id="2ad9e-151">有关详细信息，请参阅 [向报表添加程序集引用 (SSRS)](add-an-assembly-reference-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-151">For more information, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md).</span></span>  
  
 <span data-ttu-id="2ad9e-152">嵌入代码中的方法可通过全局定义的 `Code` 成员使用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-152">Methods in embedded code are available through a globally defined `Code` member.</span></span> <span data-ttu-id="2ad9e-153">您可以通过引用 `Code` 成员和方法名称来访问这些方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-153">You access these by referring to the `Code` member and the method name.</span></span> <span data-ttu-id="2ad9e-154">下列示例调用 `ToUSD` 方法，该方法将 `StandardCost` 字段中的值转换为美元值：</span><span class="sxs-lookup"><span data-stu-id="2ad9e-154">The following example calls the method `ToUSD`, which converts the value in the `StandardCost` field to a dollar value:</span></span>  
  
```  
=Code.ToUSD(Fields!StandardCost.Value)  
```  
  
 <span data-ttu-id="2ad9e-155">若要引用自定义代码的内置集合，请包含对内置 `Report` 对象的引用：</span><span class="sxs-lookup"><span data-stu-id="2ad9e-155">To reference built-in collections in your custom code, include a reference to the built-in `Report` object:</span></span>  
  
```  
=Report.Parameters!Param1.Value  
```  
  
 <span data-ttu-id="2ad9e-156">下面的示例显示如何定义某些自定义常量和变量。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-156">The following examples show how to define some custom constants and variables.</span></span>  
  
```  
Public Const MyNote = "Authored by Bob"  
Public Const NCopies As Int32 = 2  
Public Dim  MyVersion As String = "123.456"  
Public Dim MyDoubleVersion As Double = 123.456  
```  
  
 <span data-ttu-id="2ad9e-157">尽管自定义常量不会出现在 **“表达式”** 对话框的 **“常量”** 类别（仅显示内置常量）中，但是可以从任何表达式向其中添加引用，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-157">Although custom constants do not appear in the **Constants** category in the **Expression** dialog box (which only displays built-in constants), you can add references to them from any expression, as shown in the following examples.</span></span> <span data-ttu-id="2ad9e-158">在表达式中，自定义常量被视为 `Variant`。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-158">In an expression, a custom constant is treated as a `Variant`.</span></span>  
  
```  
=Code.MyNote  
=Code.NCopies  
=Code.MyVersion  
=Code.MyDoubleVersion  
```  
  
 <span data-ttu-id="2ad9e-159">下面的示例包括 `FixSpelling` 函数的代码引用和代码实现，该函数用 `"Bicycle"` 文本替换 `SubCategory` 字段中出现的所有“Bike”文本。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-159">The following example includes both the code reference and the code implementation of the function `FixSpelling`, which substitutes the text `"Bicycle"` for all occurrences of the text "Bike" in the `SubCategory` field.</span></span>  
  
 `=Code.FixSpelling(Fields!SubCategory.Value)`  
  
 <span data-ttu-id="2ad9e-160">嵌入报表定义代码块后，以下代码显示 `FixSpelling` 方法的实现。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-160">The following code, when embedded in a report definition code block, shows an implementation of the `FixSpelling` method.</span></span> <span data-ttu-id="2ad9e-161">此示例演示如何对类使用完全限定引用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] `StringBuilder` 。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-161">This example shows you how to use a fully qualified reference to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] `StringBuilder` class.</span></span>  
  
```vb  
Public Function FixSpelling(ByVal s As String) As String  
   Dim strBuilder As New System.Text.StringBuilder(s)  
   If s.Contains("Bike") Then  
      strBuilder.Replace("Bike", "Bicycle")  
      Return strBuilder.ToString()  
      Else : Return s  
   End If  
End Function  
```  
  
 <span data-ttu-id="2ad9e-162">有关内置对象集合和初始化的详细信息，请参阅[内置的全局和用户引用（报表生成器和 SSRS）](built-in-collections-built-in-globals-and-users-references-report-builder.md)和[初始化自定义程序集对象](../custom-assemblies/initializing-custom-assembly-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-162">For more information about built-in object collections and initialization, see [Built-in Globals and Users References &#40;Report Builder and SSRS&#41;](built-in-collections-built-in-globals-and-users-references-report-builder.md) and [Initializing Custom Assembly Objects](../custom-assemblies/initializing-custom-assembly-objects.md).</span></span>  
  
##  <a name="including-references-to-parameters-from-code"></a><a name="Parameters"></a> <span data-ttu-id="2ad9e-163">包括对代码中的参数的引用</span><span class="sxs-lookup"><span data-stu-id="2ad9e-163">Including References to Parameters from Code</span></span>  
 <span data-ttu-id="2ad9e-164">可以通过所提供的报表定义代码块中或自定义程序集中的自定义代码来引用全局参数集合。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-164">You can reference the global parameters collection via custom code in a Code block of the report definition or in a custom assembly that you provide.</span></span> <span data-ttu-id="2ad9e-165">该参数集合是只读的，并且没有公共迭代器。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-165">The parameters collection is read-only and has no public iterators.</span></span> <span data-ttu-id="2ad9e-166">不能使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `For Each` 构造单步执行集合。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-166">You cannot use a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `For Each` construct to step through the collection.</span></span> <span data-ttu-id="2ad9e-167">您需要首先知道在报表定义中定义的参数名称，然后才能在代码中引用该参数。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-167">You need to know the name of the parameter defined in the report definition before you can reference it in your code.</span></span> <span data-ttu-id="2ad9e-168">但是，可以遍历多值参数的所有值。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-168">You can, however, iterate through all the values of a multivalue parameter.</span></span>  
  
 <span data-ttu-id="2ad9e-169">下表包含从自定义代码引用该内置集合 `Parameters` 的示例：</span><span class="sxs-lookup"><span data-stu-id="2ad9e-169">The following table includes examples of referencing the built-in collection `Parameters` from custom code:</span></span>  
  
|<span data-ttu-id="2ad9e-170">说明</span><span class="sxs-lookup"><span data-stu-id="2ad9e-170">Description</span></span>|<span data-ttu-id="2ad9e-171">表达式中的引用</span><span class="sxs-lookup"><span data-stu-id="2ad9e-171">Reference in Expression</span></span>|<span data-ttu-id="2ad9e-172">自定义代码定义</span><span class="sxs-lookup"><span data-stu-id="2ad9e-172">Custom Code definition</span></span>|  
|-----------------|-----------------------------|----------------------------|  
|<span data-ttu-id="2ad9e-173">将整个全局参数集合传递给自定义代码。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-173">Passing an entire global parameter collection to custom code.</span></span><br /><br /> <span data-ttu-id="2ad9e-174">该函数会返回特定报表参数 *MyParameter*的值。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-174">This function returns the value of a specific report parameter *MyParameter*.</span></span>|`=Code.DisplayAParameterValue(Parameters)`|`Public Function DisplayAParameterValue(`<br /><br /> `ByVal parameters as Parameters) as Object`<br /><br /> `Return parameters("MyParameter").Value`<br /><br /> `End Function`|  
|<span data-ttu-id="2ad9e-175">将单个参数传递给自定义代码。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-175">Passing an individual parameter to custom code.</span></span><br /><br /> <span data-ttu-id="2ad9e-176">此示例返回传入的参数的值。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-176">This example returns the value of the parameter passed in.</span></span> <span data-ttu-id="2ad9e-177">如果该参数是多值参数，则返回字符串将是所有值的串联。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-177">If the parameter is a multivalue parameter, the return string is a concatenation of all the values.</span></span>|`=Code.ShowParametersValues(Parameters!DayOfTheWeek)`|`Public Function ShowParameterValues(ByVal parameter as Parameter)` <br />  `as String` <br /> `Dim s as String`  <br />  `If parameter.IsMultiValue then` <br />  `s = "Multivalue: "`  <br /> `For i as integer = 0 to parameter.Count-1` <br />  `s = s + CStr(parameter.Value(i)) + " "`  <br />  `Next` <br /> `Else` <br /> `s = "Single value: " + CStr(parameter.Value)` <br /> `End If` <br />  `Return s` <br /> `End Function`|  
  
##  <a name="including-references-to-code-from-custom-assemblies"></a><a name="Custom"></a><span data-ttu-id="2ad9e-178">包括对自定义程序集中的代码的引用</span><span class="sxs-lookup"><span data-stu-id="2ad9e-178">Including References to Code from Custom Assemblies</span></span>  
 <span data-ttu-id="2ad9e-179">若要在报表中使用自定义程序集，您必须先创建程序集，使其可供报表设计器使用，然后在报表中添加对该程序集的引用，最后在报表中使用表达式来引用该程序集中包含的方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-179">To use custom assemblies in a report, you must first create the assembly, make it available to Report Designer, add a reference to the assembly in the report, and then use an expression in the report to refer to the methods contained in that assembly.</span></span> <span data-ttu-id="2ad9e-180">如果报表部署到报表服务器，您还必须向报表服务器部署该自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-180">When the report is deployed to the report server, you must also deploy the custom assembly to the report server.</span></span>  
  
 <span data-ttu-id="2ad9e-181">有关创建自定义程序集并使其可供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]使用的信息，请参阅 [将自定义程序集用于报表](../custom-assemblies/using-custom-assemblies-with-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-181">For information about creating a custom assembly and making it available to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).</span></span>  
  
 <span data-ttu-id="2ad9e-182">若要在表达式中引用自定义代码，您必须调用程序集中某个类的成员。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-182">To refer to custom code in an expression, you must call the member of a class within the assembly.</span></span> <span data-ttu-id="2ad9e-183">调用方式取决于该方法是静态方法还是基于实例的方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-183">How you do this depends on whether the method is static or instance-based.</span></span> <span data-ttu-id="2ad9e-184">自定义程序集中的静态方法可在报表内全局使用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-184">Static methods within a custom assembly are available globally within the report.</span></span> <span data-ttu-id="2ad9e-185">您可以在表达式中通过指定命名空间、类和方法名称来访问静态方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-185">You can access static methods in expressions by specifying the namespace, class, and method name.</span></span> <span data-ttu-id="2ad9e-186">下面的示例调用方法，该方法 `ToGBP` 将**StandardCost**值的值从美元转换为英镑：</span><span class="sxs-lookup"><span data-stu-id="2ad9e-186">The following example calls the method `ToGBP`, which converts the value of the **StandardCost** value from dollar to pounds sterling:</span></span>  
  
```  
=CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
```  
  
 <span data-ttu-id="2ad9e-187">基于实例的方法可通过全局定义的 `Code` 成员使用。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-187">Instance-based methods are available through a globally defined `Code` member.</span></span> <span data-ttu-id="2ad9e-188">您可以通过先引用 `Code` 成员，再引用实例和方法名称，来访问这些方法。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-188">You access these by referring to the `Code` member, followed by the instance and method name.</span></span> <span data-ttu-id="2ad9e-189">下面的示例调用实例方法 `ToEUR` ，该方法将**StandardCost**的值从美元转换为欧元：</span><span class="sxs-lookup"><span data-stu-id="2ad9e-189">The following example calls the instance method `ToEUR`, which converts the value of **StandardCost** from dollar to euro:</span></span>  
  
```  
=Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2ad9e-190">在报表设计器中，除非您关闭 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，否则一旦加载自定义程序集，就不会卸载该程序集。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-190">In Report Designer, a custom assembly is loaded once and is not unloaded until you close [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="2ad9e-191">如果预览报表后对报表所用的自定义程序集进行更改，然后再次预览该报表，则第二次预览结果中不会体现所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-191">If you preview a report, make changes to a custom assembly used in the report, and then preview the report again, the changes will not appear in the second preview.</span></span> <span data-ttu-id="2ad9e-192">若要重新加载程序集，请关闭 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，再将其重新打开，然后预览报表。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-192">To reload the assembly, close and reopen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and then preview the report.</span></span>  
  
 <span data-ttu-id="2ad9e-193">有关访问代码的详细信息，请参阅 [Accessing Custom Assemblies Through Expressions](../custom-assemblies/accessing-custom-assemblies-through-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-193">For more information about accessing your code, see [Accessing Custom Assemblies Through Expressions](../custom-assemblies/accessing-custom-assemblies-through-expressions.md).</span></span>  
  
##  <a name="passing-built-in-collections-into-custom-assemblies"></a><a name="collections"></a> <span data-ttu-id="2ad9e-194">将内置集合传递到自定义程序集</span><span class="sxs-lookup"><span data-stu-id="2ad9e-194">Passing Built-in Collections into Custom Assemblies</span></span>  
 <span data-ttu-id="2ad9e-195">如果要将内置集合（如 *Globals* 或 *Parameters* 集合）传递到自定义程序集进行处理，则必须将代码项目中的程序集引用添加到定义内置集合的程序集中并且访问正确的命名空间。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-195">If you want to pass built-in collections, such as the *Globals* or *Parameters* collection, into a custom assembly for processing, you must add an assembly reference in your code project to the assembly that defines the built-in collections and access the correct namespace.</span></span> <span data-ttu-id="2ad9e-196">根据您是为运行在报表服务器上的报表（服务器报表）开发自定义程序集，还是为在 .NET 应用程序中本地运行的报表（本地报表）开发自定义程序集，需要引用的程序集会有所不同。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-196">Depending on whether you are developing the custom assembly for a report that is run on a report server (server report) or a report that is run locally in a .NET application (local report), the assembly you need to reference is different.</span></span> <span data-ttu-id="2ad9e-197">请参见以下详细内容。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-197">See below for details.</span></span>  
  
-   <span data-ttu-id="2ad9e-198">**命名空间：** Microsoft.ReportingServices.ReportProcessing.ReportObjectModel</span><span class="sxs-lookup"><span data-stu-id="2ad9e-198">**Namespace:** Microsoft.ReportingServices.ReportProcessing.ReportObjectModel</span></span>  
  
-   <span data-ttu-id="2ad9e-199">**程序集（本地报表）：** Microsoft.ReportingServices.ProcessingObjectModel.dll</span><span class="sxs-lookup"><span data-stu-id="2ad9e-199">**Assembly (local report):** Microsoft.ReportingServices.ProcessingObjectModel.dll</span></span>  
  
-   <span data-ttu-id="2ad9e-200">**程序集（服务器报表）：** Microsoft.ReportViewer.ProcessingObjectModel.dll</span><span class="sxs-lookup"><span data-stu-id="2ad9e-200">**Assembly (server report):** Microsoft.ReportViewer.ProcessingObjectModel.dll</span></span>  
  
 <span data-ttu-id="2ad9e-201">因为 *Fields* 和 *ReportItems* 集合的内容可在运行时动态更改，所以不应阻止它们对自定义程序集的调用（例如，在成员变量中）。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-201">Since the content of the *Fields* and *ReportItems* collections can change dynamically at runtime, you should not hold onto them across calls into the custom assembly (for example, in a member variable).</span></span> <span data-ttu-id="2ad9e-202">同样的建议通常应用于所有内置集合。</span><span class="sxs-lookup"><span data-stu-id="2ad9e-202">The same recommendation applies generally to all built-in collections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad9e-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ad9e-203">See Also</span></span>  
 <span data-ttu-id="2ad9e-204">[将代码添加到报表 &#40;SSRS&#41;](add-code-to-a-report-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ad9e-204">[Add Code to a Report &#40;SSRS&#41;](add-code-to-a-report-ssrs.md) </span></span>  
 <span data-ttu-id="2ad9e-205">[将自定义程序集用于报表](../custom-assemblies/using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="2ad9e-205">[Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) </span></span>  
 <span data-ttu-id="2ad9e-206">[将程序集引用添加到报表 &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ad9e-206">[Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md) </span></span>  
 <span data-ttu-id="2ad9e-207">[Reporting Services 的教程 &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ad9e-207">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span></span>  
 <span data-ttu-id="2ad9e-208">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ad9e-208">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2ad9e-209">报表示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2ad9e-209">Report Samples (Report Builder and SSRS)</span></span>](https://go.microsoft.com/fwlink/?LinkId=198283)  
  
  
