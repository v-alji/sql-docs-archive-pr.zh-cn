---
title: Analysis Services 数据库的扩展字段属性 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d7d87e2-bf0d-4ebb-a287-80b5a967a3f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5c0a8ebcb739cdf6b3fa34acf467309e7854db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694275"
---
# <a name="extended-field-properties-for-an-analysis-services-database-ssrs"></a><span data-ttu-id="3a5b9-102">Analysis Services 数据库的扩展字段属性 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-102">Extended Field Properties for an Analysis Services Database (SSRS)</span></span>
  <span data-ttu-id="3a5b9-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据处理扩展插件支持扩展字段属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension supports extended field properties.</span></span> <span data-ttu-id="3a5b9-104">扩展字段属性是除字段属性 `Value` 和 `IsMissing` 之外的属性，可用于数据源并受数据处理扩展插件支持。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-104">Extended field properties are properties in addition to the field properties `Value` and `IsMissing` that are available on the data source and supported by the data processing extension.</span></span> <span data-ttu-id="3a5b9-105">扩展属性并不作为报表数据集的字段集合的一部分显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-105">Extended properties do not appear in the Report Data pane as part of the field collection for a report dataset.</span></span> <span data-ttu-id="3a5b9-106">您可以通过编写通过使用内置集合按名称指定扩展字段属性值的表达式，在报表中包含这些值 `Fields` 。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-106">You can include extended field property values in your report by writing expressions that specify them by name using the built-in `Fields` collection.</span></span>  
  
 <span data-ttu-id="3a5b9-107">扩展属性包括预定义属性和自定义属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-107">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="3a5b9-108">预定义属性是多个数据源中通用的属性，它们映射到特定字段属性名称并可通过内置 `Fields` 集合按名称进行访问。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-108">Predefined properties are properties common to multiple data sources that are mapped to specific field property names and can be accessed through the built-in `Fields` collection by name.</span></span> <span data-ttu-id="3a5b9-109">自定义属性是特定于每个数据访问接口的属性，只能通过内置 `Fields` 集合，使用将扩展属性名称用作字符串的语法进行访问。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-109">Custom properties are specific to each data provider and can be accessed through the built-in `Fields` collection only through syntax using the extended property name as a string.</span></span>  
  
 <span data-ttu-id="3a5b9-110">在图形模式下使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX 查询设计器定义查询时，一组预定义的单元属性和维度属性会自动添加到 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-110">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] MDX query designer in graphical mode to define your query, a predefined set of cell properties and dimension properties are automatically added to the MDX query.</span></span> <span data-ttu-id="3a5b9-111">您只能使用在您的报表的 MDX 查询中专门列出的扩展属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-111">You can only use extended properties that are specifically listed in the MDX query in your report.</span></span> <span data-ttu-id="3a5b9-112">根据您的报表，可能需要修改默认 MDX 命令文本才能包含多维数据集中定义的其他维度或自定义属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-112">Depending on your report, you may want to modify the default MDX command text to include other dimension or custom properties defined in the cube.</span></span> <span data-ttu-id="3a5b9-113">有关 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据源中的可用扩展字段的详细信息，请参阅[创建和使用属性值 (MDX)](../../analysis-services/creating-and-using-property-values-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-113">For more information about extended fields available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data sources, see [Creating and Using Property Values &#40;MDX&#41;](../../analysis-services/creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="working-with-field-properties-in-a-report"></a><span data-ttu-id="3a5b9-114">在报表中使用字段属性</span><span class="sxs-lookup"><span data-stu-id="3a5b9-114">Working with Field Properties in a Report</span></span>  
 <span data-ttu-id="3a5b9-115">扩展字段属性包括预定义属性和数据访问接口特定属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-115">Extended field properties include predefined properties and data provider-specific properties.</span></span> <span data-ttu-id="3a5b9-116">即使字段属性位于为数据集生成的查询中，它们也不会与字段列表一起显示在 **“报表数据”** 窗格中，因此，不能将字段属性拖至报表设计图面中。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-116">Field properties do not appear with the field list in the **Report Data** pane, even though they are in the query built for a dataset; therefore, you cannot drag field properties onto your report design surface.</span></span> <span data-ttu-id="3a5b9-117">相反，您必须将字段拖至报表，然后将字段的 `Value` 属性更改为要使用的属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-117">Instead, you must drag the field onto the report and then change the `Value` property of the field to the property that you want to use.</span></span> <span data-ttu-id="3a5b9-118">例如，如果已设置多维数据集的单元格数据的格式，则可以通过表达式 `=Fields!FieldName.FormattedValue`，来使用 FormattedValue 字段属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-118">For example, if the cell data from a cube has already been formatted, you can use the FormattedValue field property by using the following expression: `=Fields!FieldName.FormattedValue`.</span></span>  
  
 <span data-ttu-id="3a5b9-119">若要引用未预定义的扩展属性，请在表达式中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="3a5b9-119">To refer to an extended property that is not predefined, use the following syntax in an expression:</span></span>  
  
-   <span data-ttu-id="3a5b9-120">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="3a5b9-120">*Fields!FieldName("PropertyName")*</span></span>  
  
## <a name="predefined-field-properties"></a><span data-ttu-id="3a5b9-121">预定义的字段属性</span><span class="sxs-lookup"><span data-stu-id="3a5b9-121">Predefined Field Properties</span></span>  
 <span data-ttu-id="3a5b9-122">在大多数情况下，预定义的字段属性应用于度量值、级别或维度。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-122">In most cases, predefined field properties apply to measures, levels, or dimensions.</span></span> <span data-ttu-id="3a5b9-123">预定义的字段属性必须在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据源中存储相应的值。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-123">A predefined field property must have a corresponding value stored in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="3a5b9-124">如果值不存在，或者（例如）对某个级别指定了仅适用于度量值的字段属性，则该属性将返回空值。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-124">If a value does not exist, or if you specify a measure-only field property on a level (for example), the property returns a null value.</span></span>  
  
 <span data-ttu-id="3a5b9-125">可以使用以下任一语法引用表达式中的预定义属性：</span><span class="sxs-lookup"><span data-stu-id="3a5b9-125">You can use either of the following syntaxes to refer to a predefined property from an expression:</span></span>  
  
-   <span data-ttu-id="3a5b9-126">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="3a5b9-126">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="3a5b9-127">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="3a5b9-127">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="3a5b9-128">下表提供了您可以使用的预定义字段属性的列表：</span><span class="sxs-lookup"><span data-stu-id="3a5b9-128">The following table provides a list of predefined field properties that you can use.</span></span>  
  
|<span data-ttu-id="3a5b9-129">**属性**</span><span class="sxs-lookup"><span data-stu-id="3a5b9-129">**Property**</span></span>|<span data-ttu-id="3a5b9-130">类型 </span><span class="sxs-lookup"><span data-stu-id="3a5b9-130">**Type**</span></span>|<span data-ttu-id="3a5b9-131">**说明或所需的值**</span><span class="sxs-lookup"><span data-stu-id="3a5b9-131">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="3a5b9-132">指定字段的数据值。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-132">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="3a5b9-133">指示是否在结果数据集中找到了该字段。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-133">Indicates whether the field was found in the resulting data set.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="3a5b9-134">返回级别的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-134">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="3a5b9-135">例如，雇员的 `UniqueName` 值可能是 *[employee]. [员工部]。[部门]. & [Sales]. & [北美销售经理]. & [272]*。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-135">For example, the `UniqueName` value for an employee might be *[Employee].[Employee Department].[Department].&[Sales].&[North American Sales Manager].&[272]*.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="3a5b9-136">返回数据库中为该字段定义的背景颜色。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-136">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="3a5b9-137">返回数据库中为该项定义的前景色。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-137">Returns the foreground color defined in the database for the item.</span></span>|  
|`FontFamily`|`String`|<span data-ttu-id="3a5b9-138">返回数据库中为该项定义的字体的名称。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-138">Returns the name of the font defined in the database for the item.</span></span>|  
|`FontSize`|`String`|<span data-ttu-id="3a5b9-139">返回数据库中为该项定义的字体的字号。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-139">Returns the point size of the font defined in the database for the item.</span></span>|  
|`FontWeight`|`String`|<span data-ttu-id="3a5b9-140">返回数据库中为该项定义的字体的粗细。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-140">Returns the weight of the font defined in the database for the item.</span></span>|  
|`FontStyle`|`String`|<span data-ttu-id="3a5b9-141">返回数据库中为该项定义的字体的样式。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-141">Returns the style of the font defined in the database for the item.</span></span>|  
|`TextDecoration`|`String`|<span data-ttu-id="3a5b9-142">返回数据库中为该项定义的特殊文本格式设置。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-142">Returns special text formatting defined in the database for the item.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="3a5b9-143">返回度量值或关键数字的格式值。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-143">Returns a formatted value for a measure or key figure.</span></span> <span data-ttu-id="3a5b9-144">例如，" `FormattedValue` **销售额配额**" 的属性返回货币格式，如 $1124400.00。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-144">For example, the `FormattedValue` property for **Sales Amount Quota** returns a currency format like $1,124,400.00.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="3a5b9-145">返回级别的键。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-145">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="3a5b9-146">针对父子层次结构返回级别号或维度编号。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-146">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="3a5b9-147">针对父子层次结构返回父级的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-147">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3a5b9-148">仅当数据源（如 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维数据集）在运行报表并检索报表数据集的数据时，为这些扩展字段属性提供值，这些值才存在。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-148">Values exist for these extended field properties only if the data source (for example, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cube) provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="3a5b9-149">然后，您可以使用下面介绍的语法从任意表达式引用这些字段属性值。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-149">You can then refer to those field property values from any expression using the syntax described in the following section.</span></span> <span data-ttu-id="3a5b9-150">但是，由于这些字段专用于此数据访问接口，因此，对这些值所做的更改不会随报表定义一同保存。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-150">However, because these fields are specific to this data provider, changes that you make to these values are not saved with the report definition.</span></span>  
  
### <a name="example-extended-properties"></a><span data-ttu-id="3a5b9-151">扩展属性示例</span><span class="sxs-lookup"><span data-stu-id="3a5b9-151">Example Extended Properties</span></span>  
 <span data-ttu-id="3a5b9-152">为了说明扩展属性，以下 MDX 查询和结果集包含了为多维数据集定义的某维度属性的多个可用成员属性。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-152">To illustrate extended properties, the following MDX query and result set include several member properties available from a dimension attribute defined for a cube.</span></span> <span data-ttu-id="3a5b9-153">包含的成员属性为 MEMBER_CAPTION、UNIQUENAME、Properties("Day Name")、MEMBER_VALUE、PARENT_UNIQUE_NAME 和 MEMBER_KEY。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-153">The member properties included are MEMBER_CAPTION, UNIQUENAME, Properties("Day Name"), MEMBER_VALUE, PARENT_UNIQUE_NAME, and MEMBER_KEY.</span></span>  
  
 <span data-ttu-id="3a5b9-154">此 MDX 查询针对 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW 数据库（随 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 示例数据库提供）中的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 多维数据集运行。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-154">This MDX query runs against the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] cube in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW database, included with the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample databases.</span></span>  
  
```  
WITH MEMBER [Measures].[DateCaption]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_CAPTION'   
   MEMBER [Measures].[DateUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.UNIQUENAME'   
   MEMBER [Measures].[DateDayName]   
      AS '[Date].[Date].Properties("Day Name")'   
   MEMBER [Measures].[DateValueinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_VALUE'   
   MEMBER [Measures].[DateParentUniqueName]   
      AS '[Date].[Date].CURRENTMEMBER.PARENT_UNIQUE_NAME'   
   MEMBER [Measures].[DateMemberKeyinOriginalDatatype]   
      AS '[Date].[Date].CURRENTMEMBER.MEMBER_KEY'   
SELECT {  
   [Measures].[DateCaption],   
   [Measures].[DateUniqueName],   
   [Measures].[DateDayName],   
   [Measures].[DateValueinOriginalDatatype],  
   [Measures].[DateParentUniqueName],  
   [Measures].[DateMemberKeyinOriginalDatatype]  
   } ON COLUMNS , [Date].[Date].ALLMEMBERS ON ROWS   
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="3a5b9-155">在 MDX 查询窗格中运行此查询时，您将获得一个包含 1158 行的结果集。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-155">When you run this query in an MDX query pane, you get a result set with 1158 rows.</span></span> <span data-ttu-id="3a5b9-156">下表显示了其中的前四行。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-156">The first four rows are shown in the following table.</span></span>  
  
|<span data-ttu-id="3a5b9-157">DateCaption</span><span class="sxs-lookup"><span data-stu-id="3a5b9-157">DateCaption</span></span>|<span data-ttu-id="3a5b9-158">DateUniqueName</span><span class="sxs-lookup"><span data-stu-id="3a5b9-158">DateUniqueName</span></span>|<span data-ttu-id="3a5b9-159">DateDayName</span><span class="sxs-lookup"><span data-stu-id="3a5b9-159">DateDayName</span></span>|<span data-ttu-id="3a5b9-160">DateValueinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="3a5b9-160">DateValueinOriginalDatatype</span></span>|<span data-ttu-id="3a5b9-161">DateParentUniqueName</span><span class="sxs-lookup"><span data-stu-id="3a5b9-161">DateParentUniqueName</span></span>|<span data-ttu-id="3a5b9-162">DateMemberKeyinOriginalDatatype</span><span class="sxs-lookup"><span data-stu-id="3a5b9-162">DateMemberKeyinOriginalDatatype</span></span>|  
|-----------------|--------------------|-----------------|---------------------------------|--------------------------|-------------------------------------|  
|<span data-ttu-id="3a5b9-163">All Periods</span><span class="sxs-lookup"><span data-stu-id="3a5b9-163">All Periods</span></span>|<span data-ttu-id="3a5b9-164">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-164">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="3a5b9-165">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-165">(null)</span></span>|<span data-ttu-id="3a5b9-166">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-166">(null)</span></span>|<span data-ttu-id="3a5b9-167">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-167">(null)</span></span>|<span data-ttu-id="3a5b9-168">0</span><span class="sxs-lookup"><span data-stu-id="3a5b9-168">0</span></span>|  
|<span data-ttu-id="3a5b9-169">1-Jul-01</span><span class="sxs-lookup"><span data-stu-id="3a5b9-169">1-Jul-01</span></span>|<span data-ttu-id="3a5b9-170">[Date].[Date].&[1]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-170">[Date].[Date].&[1]</span></span>|<span data-ttu-id="3a5b9-171">星期日</span><span class="sxs-lookup"><span data-stu-id="3a5b9-171">Sunday</span></span>|<span data-ttu-id="3a5b9-172">7/1/2001</span><span class="sxs-lookup"><span data-stu-id="3a5b9-172">7/1/2001</span></span>|<span data-ttu-id="3a5b9-173">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-173">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="3a5b9-174">1</span><span class="sxs-lookup"><span data-stu-id="3a5b9-174">1</span></span>|  
|<span data-ttu-id="3a5b9-175">2-Jul-01</span><span class="sxs-lookup"><span data-stu-id="3a5b9-175">2-Jul-01</span></span>|<span data-ttu-id="3a5b9-176">[Date].[Date].&[2]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-176">[Date].[Date].&[2]</span></span>|<span data-ttu-id="3a5b9-177">星期一</span><span class="sxs-lookup"><span data-stu-id="3a5b9-177">Monday</span></span>|<span data-ttu-id="3a5b9-178">7/2/2001</span><span class="sxs-lookup"><span data-stu-id="3a5b9-178">7/2/2001</span></span>|<span data-ttu-id="3a5b9-179">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-179">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="3a5b9-180">2</span><span class="sxs-lookup"><span data-stu-id="3a5b9-180">2</span></span>|  
|<span data-ttu-id="3a5b9-181">3-Jul-01</span><span class="sxs-lookup"><span data-stu-id="3a5b9-181">3-Jul-01</span></span>|<span data-ttu-id="3a5b9-182">[Date].[Date].&[3]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-182">[Date].[Date].&[3]</span></span>|<span data-ttu-id="3a5b9-183">星期二</span><span class="sxs-lookup"><span data-stu-id="3a5b9-183">Tuesday</span></span>|<span data-ttu-id="3a5b9-184">7/3/2001</span><span class="sxs-lookup"><span data-stu-id="3a5b9-184">7/3/2001</span></span>|<span data-ttu-id="3a5b9-185">[Date].[Date].[All Periods]</span><span class="sxs-lookup"><span data-stu-id="3a5b9-185">[Date].[Date].[All Periods]</span></span>|<span data-ttu-id="3a5b9-186">3</span><span class="sxs-lookup"><span data-stu-id="3a5b9-186">3</span></span>|  
  
 <span data-ttu-id="3a5b9-187">对于使用图形模式下的默认 MDX 查询设计器生成的 MDX 查询，其维度属性只包括 MEMBER_CAPTION 和 UNIQUENAME。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-187">Default MDX queries built using the MDX Query Designer in graphical mode only include MEMBER_CAPTION and UNIQUENAME for dimension properties.</span></span> <span data-ttu-id="3a5b9-188">默认情况下，这些值始终为 `String` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-188">By default, these values always are data type `String`.</span></span>  
  
 <span data-ttu-id="3a5b9-189">如果需要成员属性采用其原始数据类型，则可通过在基于文本的查询设计器中修改默认 MDX 语句，来包含附加属性 MEMBER_VALUE。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-189">If you need a member property in its original data type, you can include an additional property MEMBER_VALUE by modifying the default MDX statement in the text-based query designer.</span></span> <span data-ttu-id="3a5b9-190">在下面的简单 MDX 语句中，MEMBER_VALUE 已添加到要检索的维度属性列表中。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-190">In the following simple MDX statement, MEMBER_VALUE has been added to the list of dimension properties to retrieve.</span></span>  
  
```  
SELECT NON EMPTY {[Measures].[Order Count]} ON COLUMNS,   
NON EMPTY { ([Date].[Month of Year].[Month of Year] ) }   
DIMENSION PROPERTIES   
   MEMBER_CAPTION, MEMBER_UNIQUE_NAME, MEMBER_VALUE ON ROWS   
FROM [Adventure Works]  
CELL PROPERTIES   
   VALUE, BACK_COLOR, FORE_COLOR,   
   FORMATTED_VALUE, FORMAT_STRING,   
   FONT_NAME, FONT_SIZE, FONT_FLAGS  
```  
  
 <span data-ttu-id="3a5b9-191">下表显示了 MDX“结果”窗格中的前四行结果。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-191">The first four rows of the result in the MDX Results pane appear in the following table.</span></span>  
  
|<span data-ttu-id="3a5b9-192">Month of Year</span><span class="sxs-lookup"><span data-stu-id="3a5b9-192">Month of Year</span></span>|<span data-ttu-id="3a5b9-193">订单计数</span><span class="sxs-lookup"><span data-stu-id="3a5b9-193">Order Count</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="3a5b9-194">1 月</span><span class="sxs-lookup"><span data-stu-id="3a5b9-194">January</span></span>|<span data-ttu-id="3a5b9-195">2,481</span><span class="sxs-lookup"><span data-stu-id="3a5b9-195">2,481</span></span>|  
|<span data-ttu-id="3a5b9-196">February</span><span class="sxs-lookup"><span data-stu-id="3a5b9-196">February</span></span>|<span data-ttu-id="3a5b9-197">2,684</span><span class="sxs-lookup"><span data-stu-id="3a5b9-197">2,684</span></span>|  
|<span data-ttu-id="3a5b9-198">3 月</span><span class="sxs-lookup"><span data-stu-id="3a5b9-198">March</span></span>|<span data-ttu-id="3a5b9-199">2,749</span><span class="sxs-lookup"><span data-stu-id="3a5b9-199">2,749</span></span>|  
|<span data-ttu-id="3a5b9-200">April</span><span class="sxs-lookup"><span data-stu-id="3a5b9-200">April</span></span>|<span data-ttu-id="3a5b9-201">2,739</span><span class="sxs-lookup"><span data-stu-id="3a5b9-201">2,739</span></span>|  
  
 <span data-ttu-id="3a5b9-202">即使属性是 MDX 选择语句的一部分，它们也不会显示在结果集列中。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-202">Even though the properties are part of the MDX select statement, they do not appear in the result set columns.</span></span> <span data-ttu-id="3a5b9-203">尽管如此，使用扩展属性功能仍可将这些数据用于报表。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-203">Nevertheless, the data is available for a report by using the extended properties feature.</span></span> <span data-ttu-id="3a5b9-204">在的 MDX 查询结果窗格中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ，如果在多维数据集中设置了单元属性值，则可以双击该单元格并查看单元属性值。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-204">In an MDX query result pane in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can double-click on the cell and see the cell property values if they are set in the cube.</span></span> <span data-ttu-id="3a5b9-205">如果双击第一个包含 1,379 的 Order Count 单元，则会看到一个包含以下单元属性的弹出窗口：</span><span class="sxs-lookup"><span data-stu-id="3a5b9-205">If you double-click on the first Order Count cell that contains 1,379, you will see a pop-up window with the following cell properties:</span></span>  
  
|<span data-ttu-id="3a5b9-206">属性</span><span class="sxs-lookup"><span data-stu-id="3a5b9-206">Property</span></span>|<span data-ttu-id="3a5b9-207">值</span><span class="sxs-lookup"><span data-stu-id="3a5b9-207">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="3a5b9-208">CellOrdinal</span><span class="sxs-lookup"><span data-stu-id="3a5b9-208">CellOrdinal</span></span>|<span data-ttu-id="3a5b9-209">0</span><span class="sxs-lookup"><span data-stu-id="3a5b9-209">0</span></span>|  
|<span data-ttu-id="3a5b9-210">值</span><span class="sxs-lookup"><span data-stu-id="3a5b9-210">VALUE</span></span>|<span data-ttu-id="3a5b9-211">2481</span><span class="sxs-lookup"><span data-stu-id="3a5b9-211">2481</span></span>|  
|<span data-ttu-id="3a5b9-212">BACK_COLOR</span><span class="sxs-lookup"><span data-stu-id="3a5b9-212">BACK_COLOR</span></span>|<span data-ttu-id="3a5b9-213">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-213">(null)</span></span>|  
|<span data-ttu-id="3a5b9-214">FORE_COLOR</span><span class="sxs-lookup"><span data-stu-id="3a5b9-214">FORE_COLOR</span></span>|<span data-ttu-id="3a5b9-215">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-215">(null)</span></span>|  
|<span data-ttu-id="3a5b9-216">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="3a5b9-216">FORMATTED_VALUE</span></span>|<span data-ttu-id="3a5b9-217">2,481</span><span class="sxs-lookup"><span data-stu-id="3a5b9-217">2,481</span></span>|  
|<span data-ttu-id="3a5b9-218">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="3a5b9-218">FORMAT_STRING</span></span>|<span data-ttu-id="3a5b9-219">#,#</span><span class="sxs-lookup"><span data-stu-id="3a5b9-219">#,#</span></span>|  
|<span data-ttu-id="3a5b9-220">FONT_NAME</span><span class="sxs-lookup"><span data-stu-id="3a5b9-220">FONT_NAME</span></span>|<span data-ttu-id="3a5b9-221">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-221">(null)</span></span>|  
|<span data-ttu-id="3a5b9-222">FONT_SIZE</span><span class="sxs-lookup"><span data-stu-id="3a5b9-222">FONT_SIZE</span></span>|<span data-ttu-id="3a5b9-223">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-223">(null)</span></span>|  
|<span data-ttu-id="3a5b9-224">FONT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3a5b9-224">FONT_FLAGS</span></span>|<span data-ttu-id="3a5b9-225">(null)</span><span class="sxs-lookup"><span data-stu-id="3a5b9-225">(null)</span></span>|  
  
 <span data-ttu-id="3a5b9-226">如果使用此查询创建报表数据集，并将该数据集绑定到一个表，则可以看到字段的默认 VALUE 属性，例如 `=Fields!Month_of_Year!Value`。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-226">If you create a report dataset with this query and bind the dataset to a table, you can see the default VALUE property for a field, for example, `=Fields!Month_of_Year!Value`.</span></span> <span data-ttu-id="3a5b9-227">如果将此表达式设置为该表的排序表达式，则会按月份的字母顺序对表进行排序，因为“值”字段使用 `String` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-227">If you set this expression as the sort expression for the table, your results will be to sort the table alphabetically by month because the Value field uses a `String` data type.</span></span> <span data-ttu-id="3a5b9-228">若要按月份在一年中的顺序（即一月排在第一位，十二月排在最后）对该表进行排序，请使用以下表达式：</span><span class="sxs-lookup"><span data-stu-id="3a5b9-228">To sort the table in so that the months are in the order they occur in the year with January first and December last, use the following expression:</span></span>  
  
```  
=Fields!Month_of_Year("MEMBER_VALUE")  
```  
  
 <span data-ttu-id="3a5b9-229">这将使用数据源中字段的原始整数数据类型对其值进行排序。</span><span class="sxs-lookup"><span data-stu-id="3a5b9-229">This sorts the value of the field in its original integer data type from the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5b9-230">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a5b9-230">See Also</span></span>  
 <span data-ttu-id="3a5b9-231">[表达式（报表生成器和 SSRS）](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3a5b9-231">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3a5b9-232">[表达式中的内置集合 &#40;报表生成器和 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3a5b9-232">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="3a5b9-233">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3a5b9-233">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
