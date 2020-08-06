---
title: 派生列转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntrans.f1
helpviewer_keywords:
- multiple derived columns
- expressions [Integration Services], derived columns
- derived columns
- columns [Integration Services], derivations
- Derived Column transformation
ms.assetid: 8eba755e-8e48-4233-bd1e-09a46bf2692f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bbdc46f2e67b1b859fcfa446c584373cfbeca0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577760"
---
# <a name="derived-column-transformation"></a><span data-ttu-id="9026a-102">派生列转换</span><span class="sxs-lookup"><span data-stu-id="9026a-102">Derived Column Transformation</span></span>
  <span data-ttu-id="9026a-103">派生列转换通过对转换输入列应用表达式来创建新列值。</span><span class="sxs-lookup"><span data-stu-id="9026a-103">The Derived Column transformation creates new column values by applying expressions to transformation input columns.</span></span> <span data-ttu-id="9026a-104">表达式可以包含来自转换输入的变量、函数、运算符和列的任意组合。</span><span class="sxs-lookup"><span data-stu-id="9026a-104">An expression can contain any combination of variables, functions, operators, and columns from the transformation input.</span></span> <span data-ttu-id="9026a-105">结果可作为新列添加，也可作为替换值插入到现有列。</span><span class="sxs-lookup"><span data-stu-id="9026a-105">The result can be added as a new column or inserted into an existing column as a replacement value.</span></span> <span data-ttu-id="9026a-106">派生列转换可定义多个派生列，任何变量或输入列都可以出现在多个表达式中。</span><span class="sxs-lookup"><span data-stu-id="9026a-106">The Derived Column transformation can define multiple derived columns, and any variable or input columns can appear in multiple expressions.</span></span>  
  
 <span data-ttu-id="9026a-107">可以使用此转换执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="9026a-107">You can use this transformation to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9026a-108">将不同列的数据连接到一个派生列中。</span><span class="sxs-lookup"><span data-stu-id="9026a-108">Concatenate data from different columns into a derived column.</span></span> <span data-ttu-id="9026a-109">例如，可以使用表达式 **将** FirstName **和** LastName **列中的值组合到名为**FullName `FirstName + " " + LastName`的单个派生列中。</span><span class="sxs-lookup"><span data-stu-id="9026a-109">For example, you can combine values from the **FirstName** and **LastName** columns into a single derived column named **FullName**, by using the expression `FirstName + " " + LastName`.</span></span>  
  
-   <span data-ttu-id="9026a-110">通过使用 SUBSTRING 之类的函数从字符串数据中提取字符，然后将结果存储到派生列中。</span><span class="sxs-lookup"><span data-stu-id="9026a-110">Extract characters from string data by using functions such as SUBSTRING, and then store the result in a derived column.</span></span> <span data-ttu-id="9026a-111">例如，可以使用表达式 **从** FirstName `SUBSTRING(FirstName,1,1)`列提取人名的首字母。</span><span class="sxs-lookup"><span data-stu-id="9026a-111">For example, you can extract a person's initial from the **FirstName** column, by using the expression `SUBSTRING(FirstName,1,1)`.</span></span>  
  
-   <span data-ttu-id="9026a-112">对数值数据应用数学函数，然后将结果存储到派生列中。</span><span class="sxs-lookup"><span data-stu-id="9026a-112">Apply mathematical functions to numeric data and store the result in a derived column.</span></span> <span data-ttu-id="9026a-113">例如，可以使用表达式 **将数值列**SalesTax `ROUND(SalesTax, 2)`的值更改为精确到小数点后两位。</span><span class="sxs-lookup"><span data-stu-id="9026a-113">For example, you can change the length and precision of a numeric column, **SalesTax**, to a number with two decimal places, by using the expression `ROUND(SalesTax, 2)`.</span></span>  
  
-   <span data-ttu-id="9026a-114">创建比较输入列和变量的表达式。</span><span class="sxs-lookup"><span data-stu-id="9026a-114">Create expressions that compare input columns and variables.</span></span> <span data-ttu-id="9026a-115">例如，可以使用表达式 **来比较变量** Version **与**ProductVersion **列中的数据，然后根据比较结果决定选用** Version **还是**ProductVersion `ProductVersion == @Version? ProductVersion : @Version`的值。</span><span class="sxs-lookup"><span data-stu-id="9026a-115">For example, you can compare the variable **Version** against the data in the column **ProductVersion**, and depending on the comparison result, use the value of either **Version** or **ProductVersion**, by using the expression `ProductVersion == @Version? ProductVersion : @Version`.</span></span>  
  
-   <span data-ttu-id="9026a-116">提取日期时间值的某部分。</span><span class="sxs-lookup"><span data-stu-id="9026a-116">Extract parts of a datetime value.</span></span> <span data-ttu-id="9026a-117">例如，可以通过表达式 `DATEPART("year",GETDATE())`使用 GETDATE 和 DATEPART 函数提取当前年份。</span><span class="sxs-lookup"><span data-stu-id="9026a-117">For example, you can use the GETDATE and DATEPART functions to extract the current year, by using the expression `DATEPART("year",GETDATE())`.</span></span>  
  
-   <span data-ttu-id="9026a-118">使用表达式将日期字符串转换为特定格式。</span><span class="sxs-lookup"><span data-stu-id="9026a-118">Convert date strings to a specific format using an expression.</span></span>  
  
## <a name="configuration-of-the-derived-column-transformation"></a><span data-ttu-id="9026a-119">派生列转换的配置</span><span class="sxs-lookup"><span data-stu-id="9026a-119">Configuration of the Derived Column Transformation</span></span>  
 <span data-ttu-id="9026a-120">可以按照下列方式配置派生列转换：</span><span class="sxs-lookup"><span data-stu-id="9026a-120">You can configure the Derived column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="9026a-121">为每个输入列或即将更改的新列提供表达式。</span><span class="sxs-lookup"><span data-stu-id="9026a-121">Provide an expression for each input column or new column that will be changed.</span></span> <span data-ttu-id="9026a-122">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="9026a-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9026a-123">如果表达式引用了由派生列转换覆盖的输入列，则表达式使用列的原始值，而不是派生值。</span><span class="sxs-lookup"><span data-stu-id="9026a-123">If an expression references an input column that is overwritten by the Derived Column transformation, the expression uses the original value of the column, not the derived value.</span></span>  
  
-   <span data-ttu-id="9026a-124">如果向新列中添加结果并且数据类型为 `string`，则需指定代码页。</span><span class="sxs-lookup"><span data-stu-id="9026a-124">If adding results to new columns and the data type is `string`, specify a code page.</span></span> <span data-ttu-id="9026a-125">有关详细信息，请参阅 [Comparing String Data](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9026a-125">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="9026a-126">派生列转换包括 FriendlyExpression 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="9026a-126">The Derived Column transformation includes the FriendlyExpression custom property.</span></span> <span data-ttu-id="9026a-127">加载包时，可以通过属性表达式更新此属性。</span><span class="sxs-lookup"><span data-stu-id="9026a-127">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="9026a-128">有关详细信息，请参阅 [在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和 [转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9026a-128">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="9026a-129">此转换有一个输入、一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="9026a-129">This transformation has one input, one regular output, and one error output.</span></span>  
  
 <span data-ttu-id="9026a-130">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="9026a-130">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9026a-131">有关可以在 **“派生列转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Derived Column Transformation Editor](../../derived-column-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="9026a-131">For more information about the properties that you can set in the **Derived Column Transformation Editor** dialog box, see [Derived Column Transformation Editor](../../derived-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="9026a-132">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="9026a-132">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="9026a-133">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="9026a-133">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9026a-134">Common Properties</span><span class="sxs-lookup"><span data-stu-id="9026a-134">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="9026a-135">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="9026a-135">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="9026a-136">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="9026a-136">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9026a-137">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="9026a-137">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="9026a-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9026a-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9026a-139">使用派生列转换派生列值</span><span class="sxs-lookup"><span data-stu-id="9026a-139">Derive Column Values by Using the Derived Column Transformation</span></span>](derived-column-transformation.md)  
  
## <a name="related-content"></a><span data-ttu-id="9026a-140">相关内容</span><span class="sxs-lookup"><span data-stu-id="9026a-140">Related Content</span></span>  
 <span data-ttu-id="9026a-141">social.technet.microsoft.com 上的技术文章 [SSIS 表达式示例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="9026a-141">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
 <span data-ttu-id="9026a-142">博客，[如何使用 SSIS 拆分列数据](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html)。</span><span class="sxs-lookup"><span data-stu-id="9026a-142">Blog, [How to Split Column Data using SSIS](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html).</span></span>  
  
  
