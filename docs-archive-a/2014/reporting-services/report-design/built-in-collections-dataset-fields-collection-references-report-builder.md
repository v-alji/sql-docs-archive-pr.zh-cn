---
title: 数据集字段集合引用（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 006c6bd3-d776-4c20-9092-32e40688ac49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e4140c35f8035e3ac8fae37aefb9d7f2afcaecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590077"
---
# <a name="dataset-fields-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="662b2-102">数据集字段集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="662b2-102">Dataset Fields Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="662b2-103">报表中的每个数据集都包含一个字段集合。</span><span class="sxs-lookup"><span data-stu-id="662b2-103">Each dataset in a report contains one Fields collection.</span></span> <span data-ttu-id="662b2-104">字段集合由数据集查询指定的字段集以及你创建的任何其他计算字段组成。</span><span class="sxs-lookup"><span data-stu-id="662b2-104">The Fields collection is the set of fields specified by the dataset query plus any additional calculated fields that you create.</span></span> <span data-ttu-id="662b2-105">创建数据集后，字段集合将显示在 **“报表数据”** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="662b2-105">After you create a dataset, the field collection appears in the **Report Data** pane.</span></span>  
  
 <span data-ttu-id="662b2-106">表达式中的简单字段引用在设计图面上显示为简单表达式。</span><span class="sxs-lookup"><span data-stu-id="662b2-106">A simple field reference in an expression displays on the design surface as a simple expression.</span></span> <span data-ttu-id="662b2-107">例如，将字段 `Sales` 从“报表数据”窗格拖到设计图面上的表单元时，将显示 `[Sales]` 。</span><span class="sxs-lookup"><span data-stu-id="662b2-107">For example, when you drag the field `Sales` from the Report Data pane to a table cell on the design surface, `[Sales]` is displayed.</span></span> <span data-ttu-id="662b2-108">这表示对文本框 Value 属性设置的是基础表达式 `=Fields!Sales.Value` 。</span><span class="sxs-lookup"><span data-stu-id="662b2-108">This represents the underlying expression `=Fields!Sales.Value` that is set on the text box Value property.</span></span> <span data-ttu-id="662b2-109">运行报表时，报表处理器会计算此表达式，并在表单元的文本框中显示数据源中的实际数据。</span><span class="sxs-lookup"><span data-stu-id="662b2-109">When the report runs, the report processor evaluates this expression and displays the actual data from the data source in the text box in the table cell.</span></span> <span data-ttu-id="662b2-110">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)和[数据集字段集合（报表生成器和 SSRS）](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="662b2-110">For more, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) and [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-the-field-collection-for-a-dataset"></a><span data-ttu-id="662b2-111">显示数据集的字段集合</span><span class="sxs-lookup"><span data-stu-id="662b2-111">Displaying the Field Collection for a Dataset</span></span>  
 <span data-ttu-id="662b2-112">若要显示字段集合的各个值，可将每个字段拖到表详细信息行，并运行报表。</span><span class="sxs-lookup"><span data-stu-id="662b2-112">To display the individual values for a field collection, drag each field to a table detail row and run the report.</span></span> <span data-ttu-id="662b2-113">表详细信息行或列表数据区域中的引用将显示数据集中每一行的值。</span><span class="sxs-lookup"><span data-stu-id="662b2-113">References from the detail row of a table or list data region display a value for each row in the dataset.</span></span>  
  
 <span data-ttu-id="662b2-114">若要显示字段的汇总值，可将每个数值字段都拖到矩阵的数据区域中。</span><span class="sxs-lookup"><span data-stu-id="662b2-114">To display summarized values for a field, drag each numeric field to the data area of a matrix.</span></span> <span data-ttu-id="662b2-115">总计行的默认聚合函数为 Sum，例如， `=Sum(Fields!Sales.Value)`。</span><span class="sxs-lookup"><span data-stu-id="662b2-115">The default aggregate function for the total row is Sum, for example, `=Sum(Fields!Sales.Value)`.</span></span> <span data-ttu-id="662b2-116">可以更改默认函数以便计算不同的总计。</span><span class="sxs-lookup"><span data-stu-id="662b2-116">You can change the default function in order to calculate different totals.</span></span> <span data-ttu-id="662b2-117">有关详细信息，请参阅 [聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="662b2-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="662b2-118">若要在设计图面（而非数据区域的一部分）的文本框中直接显示字段集合的汇总值，必须指定数据集名称作为聚合函数的作用域。</span><span class="sxs-lookup"><span data-stu-id="662b2-118">To display summarized values for a field collection in a text box directly on the design surface (not part of a data region), you must specify the dataset name as a scope for the aggregate function.</span></span> <span data-ttu-id="662b2-119">例如，对于名为 `SalesData`的数据集，以下表达式指定了字段 `Sales`所有值的总计： `=Sum(Fields!Sales,"SalesData")`。</span><span class="sxs-lookup"><span data-stu-id="662b2-119">For example, for a dataset named `SalesData`, the following expression specifies the total of all values for the field `Sales`: `=Sum(Fields!Sales,"SalesData")`.</span></span>  
  
 <span data-ttu-id="662b2-120">使用“表达式”对话框定义简单字段引用时，可以在“类别”窗格中选择字段集合，并查看“字段”窗格中的可用字段列表   。</span><span class="sxs-lookup"><span data-stu-id="662b2-120">When you use the **Expression** dialog box to define a simple field reference, you can select the Fields collection in the Category pane and see the list of available fields in the **Field** pane.</span></span> <span data-ttu-id="662b2-121">每个字段都具有多个属性，包括 Value 和 IsMissing。</span><span class="sxs-lookup"><span data-stu-id="662b2-121">Each field has several properties, including Value and IsMissing.</span></span> <span data-ttu-id="662b2-122">其余属性是数据集可能可用的预定义扩展字段属性，具体取决于数据源类型。</span><span class="sxs-lookup"><span data-stu-id="662b2-122">The remaining properties are predefined extended field properties that may be available to the dataset depending on the data source type.</span></span>  
  
### <a name="detecting-nulls-for-a-dataset-field"></a><span data-ttu-id="662b2-123">检测数据集字段的 Null 值</span><span class="sxs-lookup"><span data-stu-id="662b2-123">Detecting Nulls for a Dataset Field</span></span>  
 <span data-ttu-id="662b2-124">若要检测为 Null（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`）的字段值，可使用函数 `IsNothing`。</span><span class="sxs-lookup"><span data-stu-id="662b2-124">To detect a field value that is null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), you can use the function `IsNothing`.</span></span> <span data-ttu-id="662b2-125">当以下表达式放置在表详细信息行的文本框中时，将测试字段 `MiddleName` 。如果值为 Null，则显示文本“No Middle Name”，如果值不为 Null，则使用该字段值本身：</span><span class="sxs-lookup"><span data-stu-id="662b2-125">When placed in a text box in a table details row, the following expression tests the field `MiddleName` and substitutes the text "No Middle Name" when the value is null, and the field value itself when the value is not null:</span></span>  
  
 `=IIF(IsNothing(Fields!MiddleName.Value),"No Middle Name",Fields!MiddleName.Value)`  
  
### <a name="detecting-missing-fields-for-dynamic-queries-at-run-time"></a><span data-ttu-id="662b2-126">在运行时检测动态字段的缺失字段</span><span class="sxs-lookup"><span data-stu-id="662b2-126">Detecting Missing Fields for Dynamic Queries at Run Time</span></span>  
 <span data-ttu-id="662b2-127">默认情况下，字段集合中的项有两个属性：Value 和 IsMissing。</span><span class="sxs-lookup"><span data-stu-id="662b2-127">By default, items in the Fields collection have two properties: Value and IsMissing.</span></span> <span data-ttu-id="662b2-128">IsMissing 属性指示设计时为数据集定义的字段是否包含在运行时检索到的字段中。</span><span class="sxs-lookup"><span data-stu-id="662b2-128">The IsMissing property indicates whether a field that is defined for a dataset at design time is contained in the fields retrieved at run time.</span></span> <span data-ttu-id="662b2-129">例如，您的查询可能调用一个结果集随输入参数变化的存储过程，或者查询可能是 `SELECT * FROM` *\<table>* 表定义发生更改的位置。</span><span class="sxs-lookup"><span data-stu-id="662b2-129">For example, your query might call a stored procedure in which the result set varies with an input parameter, or your query might be `SELECT * FROM` *\<table>* where the table definition changed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="662b2-130">IsMissing 可针对任何类型的数据源检测在设计时和运行时数据集架构中的更改。</span><span class="sxs-lookup"><span data-stu-id="662b2-130">IsMissing detects changes in the dataset schema between design time and run time for any type of data source.</span></span> <span data-ttu-id="662b2-131">IsMissing 不能用于检测多维数据集中的空成员，并且与和的 MDX 查询语言概念无关 `EMPTY` `NON EMPTY` 。</span><span class="sxs-lookup"><span data-stu-id="662b2-131">IsMissing cannot be used to detect empty members in a multidimensional cube and is not related to the MDX query language concepts of `EMPTY` and `NON EMPTY`.</span></span>  
  
 <span data-ttu-id="662b2-132">可以使用自定义代码测试 IsMissing 属性以确定某个字段是否存在于结果集中。</span><span class="sxs-lookup"><span data-stu-id="662b2-132">You can test the IsMissing property in custom code to determine if a field is present in the result set.</span></span> <span data-ttu-id="662b2-133">不能使用包含 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数调用（如 `IIF` 或 `SWITCH`）的表达式测试字段是否存在，因为 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 会计算函数调用中的所有参数，这将导致计算对缺失字段的引用时出错。</span><span class="sxs-lookup"><span data-stu-id="662b2-133">You cannot test for its presence using an expression with a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function call such as `IIF` or `SWITCH`, because [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] evaluates all parameters in the call to the function, which results in an error when the reference to the missing is evaluated.</span></span>  
  
#### <a name="example-for-controlling-the-visibility-of-a-dynamic-column-for-a-missing-field"></a><span data-ttu-id="662b2-134">控制缺失字段动态列的可见性的示例</span><span class="sxs-lookup"><span data-stu-id="662b2-134">Example for Controlling the Visibility of a Dynamic Column for a Missing Field</span></span>  
 <span data-ttu-id="662b2-135">若要设置一个表达式，用于控制显示数据集中某个字段的列的可见性，必须首先定义一个自定义代码函数，该函数根据该字段是否缺失返回一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="662b2-135">To set an expression that controls the visibility of a column that displays a field in a dataset, you must first define a custom code function that returns a Boolean value based on whether the field is missing.</span></span> <span data-ttu-id="662b2-136">例如，如果该字段缺失，则以下自定义代码函数将返回 True；如果该字段存在，则返回 False。</span><span class="sxs-lookup"><span data-stu-id="662b2-136">For example, the following custom code function returns true if the field is missing and false if the field exists.</span></span>  
  
```  
Public Function IsFieldMissing(field as Field) as Boolean  
 If (field.IsMissing) Then  
 Return True  
  Else   
  Return False  
 End If  
End Function  
```  
  
 <span data-ttu-id="662b2-137">若要将此函数用于控制列的可见性，请将列的 Hidden 属性设置为以下表达式：</span><span class="sxs-lookup"><span data-stu-id="662b2-137">To use this function to control visibility of a column, set the Hidden property of the column to the following expression:</span></span>  
  
 `=Code.IsFieldMissing(Fields!FieldName)`  
  
 <span data-ttu-id="662b2-138">当字段不存在时将隐藏该列。</span><span class="sxs-lookup"><span data-stu-id="662b2-138">The column is hidden when the field does not exist.</span></span>  
  
#### <a name="example-for-controlling-the-text-box-value-for-a-missing-field"></a><span data-ttu-id="662b2-139">控制缺失字段的文本框值的示例</span><span class="sxs-lookup"><span data-stu-id="662b2-139">Example for Controlling the Text Box Value for a Missing Field</span></span>  
 <span data-ttu-id="662b2-140">若要使用您编写的文本来代替缺失字段的值，必须编写自定义代码，以便在字段缺失时返回可用于代替字段值的文本。</span><span class="sxs-lookup"><span data-stu-id="662b2-140">To substitute text that you write in place of the value of a missing field, you must write custom code that returns text you can use in place of a field value when the field is missing.</span></span> <span data-ttu-id="662b2-141">例如，如果该字段存在，则以下自定义代码函数将返回该字段的值，如果该字段不存在，则返回指定为第二个参数的消息：</span><span class="sxs-lookup"><span data-stu-id="662b2-141">For example, the following custom code function returns the value of the field if the field exists, and the message that you specify as the second parameter if the field does not exist:</span></span>  
  
```  
Public Function IsFieldMissingThenString(field as Field, strMessage as String) as String  
 If (field.IsMissing) Then  
  Return strMessage  
 Else   
  Return field.Value  
  End If  
End Function  
```  
  
 <span data-ttu-id="662b2-142">若要在文本框中使用此函数，请将以下表达式添加到 Value 属性：</span><span class="sxs-lookup"><span data-stu-id="662b2-142">To use this function in a text box, add the following expression to the Value property:</span></span>  
  
 `=Code.IsFieldMissingThenString(Fields!FieldName,"Missing")`  
  
 <span data-ttu-id="662b2-143">文本框显示字段值或您指定的文本。</span><span class="sxs-lookup"><span data-stu-id="662b2-143">The text box displays either the field value or the text that you specified.</span></span>  
  
### <a name="using-extended-field-properties"></a><span data-ttu-id="662b2-144">使用扩展字段属性</span><span class="sxs-lookup"><span data-stu-id="662b2-144">Using Extended Field Properties</span></span>  
 <span data-ttu-id="662b2-145">扩展字段属性是由数据处理扩展插件为字段定义的其他属性，这些属性由数据集的数据源类型确定。</span><span class="sxs-lookup"><span data-stu-id="662b2-145">Extended field properties are additional properties defined on a field by the data processing extension, which is determined by the data source type for the dataset.</span></span> <span data-ttu-id="662b2-146">扩展字段属性可以是预定义的，也可以特定于某个数据源类型。</span><span class="sxs-lookup"><span data-stu-id="662b2-146">Extended field properties are predefined or specific to a data source type.</span></span> <span data-ttu-id="662b2-147">有关详细信息，请参阅 [Analysis Services 数据库的扩展字段属性 (SSRS)](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="662b2-147">For more information, see [Extended Field Properties for an Analysis Services Database &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).</span></span>  
  
 <span data-ttu-id="662b2-148">如果指定了该字段不支持的属性，则表达式的计算结果为 `null`（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="662b2-148">If you specify a property that is not supported for that field, the expression evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="662b2-149">如果数据访问接口不支持扩展字段属性，或在执行查询时找不到该字段，则对于 `null` 和 `Nothing` 类型的属性，属性值为 `String`（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Object`）；对于 `Integer` 类型的属性，属性值为零 (0)。</span><span class="sxs-lookup"><span data-stu-id="662b2-149">If a data provider does not support extended field properties, or if the field is not found when the query is executed, the value for the property is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) for properties of type `String` and `Object`, and zero (0) for properties of type `Integer`.</span></span> <span data-ttu-id="662b2-150">数据处理扩展插件可以通过优化包括此语法的查询来充分利用预定义属性。</span><span class="sxs-lookup"><span data-stu-id="662b2-150">A data processing extension may take advantage of predefined properties by optimizing queries that include this syntax.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662b2-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="662b2-151">See Also</span></span>  
 <span data-ttu-id="662b2-152">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="662b2-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="662b2-153">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="662b2-153">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-datasets-ssrs.md)  
  
  
