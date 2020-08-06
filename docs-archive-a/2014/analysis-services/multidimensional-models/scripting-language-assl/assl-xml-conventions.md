---
title: ASSL XML 约定 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b70742b07fd6450b01cf205147a05f40c4b6121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691936"
---
# <a name="assl-xml-conventions"></a><span data-ttu-id="73eae-102">ASSL XML 约定</span><span class="sxs-lookup"><span data-stu-id="73eae-102">ASSL XML Conventions</span></span>
  <span data-ttu-id="73eae-103">Analysis Services 脚本语言 (ASSL) 将对象层次结构表示为一组元素类型，其中的每个元素类型定义了可包含的子元素。</span><span class="sxs-lookup"><span data-stu-id="73eae-103">Analysis Services Scripting Language (ASSL) represents the hierarchy of objects as a set of element types, each of which defines the child elements they can contain.</span></span>  
  
 <span data-ttu-id="73eae-104">ASSL 使用以下 XML 约定来表示对象层次结构：</span><span class="sxs-lookup"><span data-stu-id="73eae-104">To represent the object hierarchy, ASSL uses the following XML conventions:</span></span>  
  
-   <span data-ttu-id="73eae-105">所有对象和属性都表示为元素，标准 XML 属性除外，如 "XML： lang"。</span><span class="sxs-lookup"><span data-stu-id="73eae-105">All objects and properties are represented as elements, except for standard XML attributes such as 'xml:lang'.</span></span>  
  
-   <span data-ttu-id="73eae-106">元素名称和枚举值都遵循使用 Pascal 大小写格式且无下划线的 Microsoft .NET Framework 命名约定。</span><span class="sxs-lookup"><span data-stu-id="73eae-106">Both element names and enumeration values follow the Microsoft .NET Framework naming convention of Pascal casing with no underscores.</span></span>  
  
-   <span data-ttu-id="73eae-107">保留所有值的大小写。</span><span class="sxs-lookup"><span data-stu-id="73eae-107">The case of all values is preserved.</span></span> <span data-ttu-id="73eae-108">枚举值也区分大小写。</span><span class="sxs-lookup"><span data-stu-id="73eae-108">Values for enumerations are also case-sensitive.</span></span>  
  
 <span data-ttu-id="73eae-109">除了此约定列表之外，Analysis Services 还遵循有关基数、继承、空格、数据类型和默认值的特定约定。</span><span class="sxs-lookup"><span data-stu-id="73eae-109">In addition to this list of conventions, Analysis Services also follows certain conventions regarding cardinality, inheritance, whitespace, data types, and default values.</span></span>  
  
## <a name="cardinality"></a><span data-ttu-id="73eae-110">基数</span><span class="sxs-lookup"><span data-stu-id="73eae-110">Cardinality</span></span>  
 <span data-ttu-id="73eae-111">当某个元素有一个大于 1 的基数时，将存在一个封装此元素的 XML 元素集合。</span><span class="sxs-lookup"><span data-stu-id="73eae-111">When an element has a cardinality that is greater than 1, there is an XML element collection that encapsulates this element.</span></span> <span data-ttu-id="73eae-112">该集合的名称使用集合中所包含元素的复数形式。</span><span class="sxs-lookup"><span data-stu-id="73eae-112">The name of collection uses the plural form of the elements contained in the collection.</span></span> <span data-ttu-id="73eae-113">例如，以下 XML 片段表示 `Dimensions` 元素内的 `Database` 集合：</span><span class="sxs-lookup"><span data-stu-id="73eae-113">For example, the following XML fragment represents the `Dimensions` collection within a `Database` element:</span></span>  
  
 `<Database>`  
  
 `...`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 <span data-ttu-id="73eae-114">元素的出现顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="73eae-114">The order in which elements appear is unimportant.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="73eae-115">继承</span><span class="sxs-lookup"><span data-stu-id="73eae-115">Inheritance</span></span>  
 <span data-ttu-id="73eae-116">存在具有重叠但有显著不同的属性集的不同对象时，会使用继承。</span><span class="sxs-lookup"><span data-stu-id="73eae-116">Inheritance is used when there are distinct objects that have overlapping but significantly different sets of properties.</span></span> <span data-ttu-id="73eae-117">这种重叠但又不同的对象示例有虚拟多维数据集、链接多维数据集和常规多维数据集。</span><span class="sxs-lookup"><span data-stu-id="73eae-117">Examples of such overlapping but distinct objects are virtual cubes, linked cubes, and regular cubes.</span></span> <span data-ttu-id="73eae-118">对于重叠但又不同的对象，Analysis Services 会使用 XML 实例命名空间的标准 `type` 属性来表示继承。</span><span class="sxs-lookup"><span data-stu-id="73eae-118">For overlapping but distinct object, Analysis Services uses the standard `type` attribute from the XML Instance Namespace to indicate the inheritance.</span></span> <span data-ttu-id="73eae-119">例如，以下 XML 片段显示 `type` 属性如何标识 `Cube` 元素是继承自常规多维数据集还是虚拟多维数据集：</span><span class="sxs-lookup"><span data-stu-id="73eae-119">For example, the following XML fragment shows how the `type` attribute identifies whether a `Cube` element inherits from a regular cube or from a virtual cube:</span></span>  
  
 `<Cubes>`  
  
 `<Cube xsi:type="RegularCube">`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type="VirtualCube">`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 <span data-ttu-id="73eae-120">当多个类型具有同一名称的属性时，通常不使用继承。</span><span class="sxs-lookup"><span data-stu-id="73eae-120">Inheritance is generally not used when multiple types have a property of the same name.</span></span> <span data-ttu-id="73eae-121">例如，`Name` 和 `ID` 属性出现在许多元素中，但这些属性尚未提升为抽象类型。</span><span class="sxs-lookup"><span data-stu-id="73eae-121">For example, the `Name` and `ID` properties appear on many elements, but these properties have not been promoted to an abstract type.</span></span>  
  
## <a name="whitespace"></a><span data-ttu-id="73eae-122">空格</span><span class="sxs-lookup"><span data-stu-id="73eae-122">Whitespace</span></span>  
 <span data-ttu-id="73eae-123">将保留元素值中的空格。</span><span class="sxs-lookup"><span data-stu-id="73eae-123">Whitespace within an element value is preserved.</span></span> <span data-ttu-id="73eae-124">但会始终删除前导空格和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="73eae-124">However, leading and trailing whitespace is always trimmed.</span></span> <span data-ttu-id="73eae-125">例如，下面的元素具有相同的文本，但该文本内的空格数量不同，因此，会将它们视为具有不同的值：</span><span class="sxs-lookup"><span data-stu-id="73eae-125">For example, the following elements have the same text but differing amounts of whitespace within that text, and are therefore treated as if they have different values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 <span data-ttu-id="73eae-126">然而，下面的元素仅前导空格和尾随空格不同，因此，会将它们视为具有等效值：</span><span class="sxs-lookup"><span data-stu-id="73eae-126">However, the following elements vary only in leading and trailing whitespace, and are therefore treated as if they have equivalent values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a><span data-ttu-id="73eae-127">数据类型</span><span class="sxs-lookup"><span data-stu-id="73eae-127">Data Types</span></span>  
 <span data-ttu-id="73eae-128">Analysis Services 使用以下标准 XML 架构定义语言 (XSD) 数据类型：</span><span class="sxs-lookup"><span data-stu-id="73eae-128">Analysis Services uses the following standard XML Schema definition language (XSD) data types:</span></span>  
  
 `Int`  
 <span data-ttu-id="73eae-129">范围为-231 到 231-1 的整数值。</span><span class="sxs-lookup"><span data-stu-id="73eae-129">An integer value in the range of -231 to 231 - 1.</span></span>  
  
 `Long`  
 <span data-ttu-id="73eae-130">范围为-263 到 263-1 的整数值。</span><span class="sxs-lookup"><span data-stu-id="73eae-130">An integer value in range of -263 to 263 - 1.</span></span>  
  
 `String`  
 <span data-ttu-id="73eae-131">符合以下全局规则的字符串值：</span><span class="sxs-lookup"><span data-stu-id="73eae-131">A string value that conforms to the following global rules:</span></span>  
  
-   <span data-ttu-id="73eae-132">去除控制字符。</span><span class="sxs-lookup"><span data-stu-id="73eae-132">Control characters are stripped out.</span></span>  
  
-   <span data-ttu-id="73eae-133">删除前导空格和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="73eae-133">Leading and trailing white space is trimmed.</span></span>  
  
-   <span data-ttu-id="73eae-134">保留内部空格。</span><span class="sxs-lookup"><span data-stu-id="73eae-134">Internal white space is preserved.</span></span>  
  
 <span data-ttu-id="73eae-135">`Name` 和 `ID` 属性对字符串元素中的有效字符具有特殊限制。</span><span class="sxs-lookup"><span data-stu-id="73eae-135">`Name` and `ID` properties have special limitations on valid characters in string elements.</span></span> <span data-ttu-id="73eae-136">有关和约定的其他信息 `Name` `ID` ，请参阅[ASSL 对象和对象特性](assl-objects-and-object-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="73eae-136">For additional information about `Name` and `ID` conventions, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
 `DateTime`  
 <span data-ttu-id="73eae-137">`DateTime`.NET Framework 中的结构。</span><span class="sxs-lookup"><span data-stu-id="73eae-137">A `DateTime` structure from the .NET Framework.</span></span> <span data-ttu-id="73eae-138"> 值不能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="73eae-138">A `DateTime` value cannot be NULL.</span></span> <span data-ttu-id="73eae-139">`DataTime` 数据类型支持的最早日期为 1601 年 1 月 1 日，程序员可将该日期作为 `DateTime.MinValue`。</span><span class="sxs-lookup"><span data-stu-id="73eae-139">The lowest date supported by the `DataTime` data type is January 1, 1601, which is available to programmers as `DateTime.MinValue`.</span></span> <span data-ttu-id="73eae-140">该最早支持日期指示缺少 `DateTime` 值。</span><span class="sxs-lookup"><span data-stu-id="73eae-140">The lowest supported date indicates that a `DateTime` value is missing.</span></span>  
  
 `Boolean`  
 <span data-ttu-id="73eae-141">仅具有两个值的枚举，例如 {true, false} 或 {0, 1}。</span><span class="sxs-lookup"><span data-stu-id="73eae-141">An enumeration with only two values, such as {true, false} or {0, 1}.</span></span>  
  
## <a name="default-values"></a><span data-ttu-id="73eae-142">默认值</span><span class="sxs-lookup"><span data-stu-id="73eae-142">Default Values</span></span>  
 <span data-ttu-id="73eae-143">Analysis Services 使用下表所列的默认值。</span><span class="sxs-lookup"><span data-stu-id="73eae-143">Analysis Services uses the defaults listed in the following table.</span></span>  
  
|<span data-ttu-id="73eae-144">XML 数据类型</span><span class="sxs-lookup"><span data-stu-id="73eae-144">XML data type</span></span>|<span data-ttu-id="73eae-145">默认值</span><span class="sxs-lookup"><span data-stu-id="73eae-145">Default value</span></span>|  
|-------------------|-------------------|  
|`Boolean`|<span data-ttu-id="73eae-146">错误</span><span class="sxs-lookup"><span data-stu-id="73eae-146">False</span></span>|  
|`String`|<span data-ttu-id="73eae-147">""（空字符串）</span><span class="sxs-lookup"><span data-stu-id="73eae-147">"" (empty string)</span></span>|  
|<span data-ttu-id="73eae-148">`Integer` 或 `Long`</span><span class="sxs-lookup"><span data-stu-id="73eae-148">`Integer` or `Long`</span></span>|<span data-ttu-id="73eae-149">0（零）</span><span class="sxs-lookup"><span data-stu-id="73eae-149">0 (zero)</span></span>|  
|`Timestamp`|<span data-ttu-id="73eae-150">12:00:00 AM、1/1/0001 (对应于 `System.DateTime` 具有0刻度的 .Net 框架) </span><span class="sxs-lookup"><span data-stu-id="73eae-150">12:00:00 AM, 1/1/0001 (corresponding to a the .NET Frameworks `System.DateTime` with 0 ticks)</span></span>|  
  
 <span data-ttu-id="73eae-151">存在但为空的元素被解释为具有 Null 字符串值，而非默认值。</span><span class="sxs-lookup"><span data-stu-id="73eae-151">An element that is present but empty is interpreted as having a value of a null string, not the default value.</span></span>  
  
### <a name="inherited-defaults"></a><span data-ttu-id="73eae-152">继承的默认值</span><span class="sxs-lookup"><span data-stu-id="73eae-152">Inherited Defaults</span></span>  
 <span data-ttu-id="73eae-153">对象上指定的某些属性可以向子对象或后代对象中的同一属性提供默认值。</span><span class="sxs-lookup"><span data-stu-id="73eae-153">Some properties that are specified on an object provide default values for the same property on child or descendant objects.</span></span> <span data-ttu-id="73eae-154">例如，`Cube.StorageMode` 可向 `Partition.StorageMode` 提供默认值。</span><span class="sxs-lookup"><span data-stu-id="73eae-154">For example, `Cube.StorageMode` provides the default value for `Partition.StorageMode`.</span></span> <span data-ttu-id="73eae-155">Analysis Services 应用于继承默认值的规则如下所示：</span><span class="sxs-lookup"><span data-stu-id="73eae-155">The rules that Analysis Services applies for inherited default values are as follows:</span></span>  
  
-   <span data-ttu-id="73eae-156">在 XML 中，如果子对象的属性为 Null，则该属性的值将默认为继承的值。</span><span class="sxs-lookup"><span data-stu-id="73eae-156">When the property for the child object is null in the XML, its value defaults to the inherited value.</span></span> <span data-ttu-id="73eae-157">但当您从服务器查询值时，服务器将会返回值为空的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="73eae-157">However, if you query the value from the server, the server returns the null value of the XML element.</span></span>  
  
-   <span data-ttu-id="73eae-158">无法通过编程方式来确定子对象属性是直接在子对象上设置的，还是直接继承的。</span><span class="sxs-lookup"><span data-stu-id="73eae-158">It is not possible to determine programmatically whether the property of a child object has been set directly on the child object or inherited.</span></span>  
  
 <span data-ttu-id="73eae-159">某些元素已定义当元素缺少时要应用的默认值。</span><span class="sxs-lookup"><span data-stu-id="73eae-159">Some elements have defined defaults that apply when the element is missing.</span></span> <span data-ttu-id="73eae-160">例如，以下 XML 片段中的 `Dimension` 元素是等效的，即使一个 `Dimension` 元素包含 `Visible` 元素，而另一个 `Dimension` 元素不包含。</span><span class="sxs-lookup"><span data-stu-id="73eae-160">For example, the `Dimension` elements in the following XML fragment are equivalent even though one `Dimension` element contains a `Visible` element, but the other `Dimension` element does not.</span></span>  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 <span data-ttu-id="73eae-161">有关继承的默认值的详细信息，请参阅[ASSL 对象和对象特性](assl-objects-and-object-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="73eae-161">For more information on inherited defaults, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
  
