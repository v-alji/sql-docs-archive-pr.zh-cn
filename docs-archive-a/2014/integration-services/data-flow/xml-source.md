---
title: XML 源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsource.f1
helpviewer_keywords:
- sources [Integration Services], XML
- XML source [Integration Services]
- XML Source Editor
ms.assetid: 68c27ea5-e93d-4e26-bfb2-d967ca0a5282
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13a1bf01729932eaa6b232ac7839d2e3001f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589769"
---
# <a name="xml-source"></a><span data-ttu-id="bd97e-102">XML 源</span><span class="sxs-lookup"><span data-stu-id="bd97e-102">XML Source</span></span>
  <span data-ttu-id="bd97e-103">XML 源读取 XML 数据文件，并用数据填充源输出中的列。</span><span class="sxs-lookup"><span data-stu-id="bd97e-103">The XML source reads an XML data file and populates the columns in the source output with the data.</span></span>  
  
 <span data-ttu-id="bd97e-104">XML 文件中的数据常常包含层次结构关系。</span><span class="sxs-lookup"><span data-stu-id="bd97e-104">The data in XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="bd97e-105">例如，XML 数据文件可以表示目录和目录中的项。</span><span class="sxs-lookup"><span data-stu-id="bd97e-105">For example, an XML data file can represent catalogs and items in catalogs.</span></span> <span data-ttu-id="bd97e-106">必须先确定 XML 数据文件中元素的关系，并且为文件中的每个元素都生成了一个输出，数据才能进入数据流。</span><span class="sxs-lookup"><span data-stu-id="bd97e-106">Before the data can enter the data flow, the relationship of the elements in XML data file must be determined, and an output must be generated for each element in the file.</span></span>  
  
## <a name="schemas"></a><span data-ttu-id="bd97e-107">架构</span><span class="sxs-lookup"><span data-stu-id="bd97e-107">Schemas</span></span>  
 <span data-ttu-id="bd97e-108">XML 源使用某种架构来解释 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="bd97e-108">The XML source uses a schema to interpret the XML data.</span></span> <span data-ttu-id="bd97e-109">XML 源支持使用 XML 架构定义 (XSD) 文件或内联架构将 XML 数据解释为表格格式。</span><span class="sxs-lookup"><span data-stu-id="bd97e-109">The XML source supports use of a XML Schema Definition (XSD) file or inline schemas to translate the XML data into a tabular format.</span></span> <span data-ttu-id="bd97e-110">如果使用 **“XML 源编辑器”** 对话框配置 XML 源，用户界面可以根据指定的 XML 数据文件生成 XSD。</span><span class="sxs-lookup"><span data-stu-id="bd97e-110">If you configure the XML source by using the **XML Source Editor** dialog box, the user interface can generate an XSD from the specified XML data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd97e-111">不支持 DTD。</span><span class="sxs-lookup"><span data-stu-id="bd97e-111">DTDs are not supported.</span></span>  
  
 <span data-ttu-id="bd97e-112">这些架构仅可以支持一个命名空间；不支持架构集合。</span><span class="sxs-lookup"><span data-stu-id="bd97e-112">The schemas can support a single namespace only; they do not support schema collections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd97e-113">XML 源并不根据 XSD 来验证 XML 文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="bd97e-113">The XML source does not validate the data in the XML file against the XSD.</span></span>  
  
## <a name="xml-source-editor"></a><span data-ttu-id="bd97e-114">XML 源编辑器</span><span class="sxs-lookup"><span data-stu-id="bd97e-114">XML Source Editor</span></span>  
 <span data-ttu-id="bd97e-115">XML 文件中的数据常常包含层次结构关系。</span><span class="sxs-lookup"><span data-stu-id="bd97e-115">The data in the XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="bd97e-116">**“XML 源编辑器”** 对话框使用指定的架构生成 XML 源输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-116">The **XML Source Editor** dialog box uses the specified schema to generate the XML source outputs.</span></span> <span data-ttu-id="bd97e-117">您可以指定 XSD 文件，使用内联架构或根据指定的 XML 数据文件生成 XSD。</span><span class="sxs-lookup"><span data-stu-id="bd97e-117">You can specify an XSD file, use an inline schema, or generate an XSD from the specified XML data file.</span></span> <span data-ttu-id="bd97e-118">该架构必须在设计时可用。</span><span class="sxs-lookup"><span data-stu-id="bd97e-118">The schema must be available at design time.</span></span>  
  
 <span data-ttu-id="bd97e-119">XML 源通过为 XML 文件中每个包含其他元素的元素创建一个输出，以便根据 XML 数据生成表格结构。</span><span class="sxs-lookup"><span data-stu-id="bd97e-119">The XML source generates tabular structures from the XML data by creating an output for every element that contains other elements in the XML files.</span></span> <span data-ttu-id="bd97e-120">例如，如果 XML 数据表示目录和目录中的项，则 XML 源将为目录创建一个输出，而且为目录包含的每种类型的项都创建一个输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-120">For example, if the XML data represents catalogs and items in catalogs, the XML source creates an output for catalogs and an output for each type of item that the catalogs contain.</span></span> <span data-ttu-id="bd97e-121">每项的输出将包含该项的属性的输出列。</span><span class="sxs-lookup"><span data-stu-id="bd97e-121">The output of each item will contain output columns for the attributes of that item.</span></span>  
  
 <span data-ttu-id="bd97e-122">为了在输出中提供关于数据层次结构关系的信息，XML 源在输出中添加了一个为各个子元素标识父元素的列。</span><span class="sxs-lookup"><span data-stu-id="bd97e-122">To provide information about the hierarchical relationship of the data in the outputs, the XML source adds a column in the outputs that identifies the parent element for each child element.</span></span> <span data-ttu-id="bd97e-123">通过使用带有不同类型项的目录示例，每个项将具有一个用于标识该项所属目录的列值。</span><span class="sxs-lookup"><span data-stu-id="bd97e-123">Using the example of catalogs with different types of items, each item would have a column value that identifies the catalog to which it belongs.</span></span>  
  
 <span data-ttu-id="bd97e-124">XML 源为每个元素创建一个输出，但您不需要使用所有输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-124">The XML source creates an output for every element, but it is not required that you use all the outputs.</span></span> <span data-ttu-id="bd97e-125">您可以删除不想使用的输出，或只是不将其连接到下游组件。</span><span class="sxs-lookup"><span data-stu-id="bd97e-125">You can delete any output that you do not want to use, or just not connect it to a downstream component.</span></span>  
  
 <span data-ttu-id="bd97e-126">XMl 源还生成输出名称，以确保输出名称明确。</span><span class="sxs-lookup"><span data-stu-id="bd97e-126">The XML source also generates the output names, to ensure that the names are unambiguous.</span></span> <span data-ttu-id="bd97e-127">这些名称可能比较长，而且可能没有以对您有用的方式标识输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-127">These names may be long and may not identify the outputs in a way that is useful to you.</span></span> <span data-ttu-id="bd97e-128">可以重命名输出，但是要保持其名称的唯一性。</span><span class="sxs-lookup"><span data-stu-id="bd97e-128">You can rename the outputs, as long as their names remain unique.</span></span> <span data-ttu-id="bd97e-129">还可以修改输出列的数据类型和长度。</span><span class="sxs-lookup"><span data-stu-id="bd97e-129">You can also modify the data type and the length of output columns.</span></span>  
  
 <span data-ttu-id="bd97e-130">对于每个输出，XML 源都会添加一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-130">For every output, the XML source adds an error output.</span></span> <span data-ttu-id="bd97e-131">默认情况下，错误输出中的列的数据类型为 Unicode 字符串数据类型 (DT_WSTR)，列的长度为 255 个字符，但您可以通过修改列的数据类型和长度来配置错误输出中的列。</span><span class="sxs-lookup"><span data-stu-id="bd97e-131">By default the columns in error outputs have Unicode string data type (DT_WSTR) with a length of 255, but you can configure the columns in the error outputs by modifying their data type and length.</span></span>  
  
 <span data-ttu-id="bd97e-132">如果 XML 数据文件包含 XSD 中没有的元素，则这些元素将被忽略，并且不会为其生成输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-132">If the XML data file contains elements that are not in the XSD, these elements are ignored and no output is generated for them.</span></span> <span data-ttu-id="bd97e-133">另一方面，如果 XML 数据文件缺少 XSD 中存在的元素，则输出将包含空值列。</span><span class="sxs-lookup"><span data-stu-id="bd97e-133">On the other hand, if the XML data file is missing elements that are represented in the XSD, the output will contain columns with null values.</span></span>  
  
 <span data-ttu-id="bd97e-134">从 XML 数据文件提取数据后，数据将转换为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="bd97e-134">When the data is extracted from the XML data file, it is converted to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="bd97e-135">不过，XML 源不能将 XML 数据转换为 DT_TIME2 或 DT_DBTIMESTAMP2 数据类型，这是因为源不支持这些数据类型。</span><span class="sxs-lookup"><span data-stu-id="bd97e-135">However, the XML source cannot convert the XML data to the DT_TIME2 or DT_DBTIMESTAMP2 data types because the source does not support these data types.</span></span> <span data-ttu-id="bd97e-136">有关详细信息，请参阅 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bd97e-136">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="bd97e-137">XSD 或内联架构可能为元素指定了数据类型，但如果未指定，则“XML 源编辑器”  对话框将为输出中包含该元素的列指定 Unicode 字符串数据类型 (DT_WSTR)，并将列长度设置为 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="bd97e-137">The XSD or inline schema may specify the data type for elements, but if it does not, the **XML Source Editor** dialog box assigns the Unicode string data type (DT_WSTR) to the column in the output that contains the element, and sets the column length to 255 characters.</span></span>  
  
 <span data-ttu-id="bd97e-138">如果该架构指定了元素的最大长度，则输出列的长度将设置为此值。</span><span class="sxs-lookup"><span data-stu-id="bd97e-138">If the schema specifies the maximum length of an element, the length of output column is set to this value.</span></span> <span data-ttu-id="bd97e-139">如果最大长度大于将元素转换为的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型所支持的长度，则数据将被截断为该数据类型的最大长度。</span><span class="sxs-lookup"><span data-stu-id="bd97e-139">If the maximum length is greater than the length supported by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to which the element is converted, then the data is truncated to the maximum length of the data type.</span></span> <span data-ttu-id="bd97e-140">例如，如果一个字符串的长度为 5000，则该字符串将因为 DT_WSTR 数据类型的最大长度而截断为 4000 字符；类似地，字节数据将截断为 DT_BYTES 数据类型的最大长度 8000 字符。</span><span class="sxs-lookup"><span data-stu-id="bd97e-140">For example, if a string has a length of 5000, it is truncated to 4000 characters because the maximum length of the DT_WSTR data type is 4000 characters; likewise, byte data is truncated to 8000 characters, the maximum length of the DT_BYTES data type.</span></span> <span data-ttu-id="bd97e-141">如果架构未指定最大长度，则具有任何一种数据类型的列的默认长度都设置为 255。</span><span class="sxs-lookup"><span data-stu-id="bd97e-141">If the schema specifies no maximum length, the default length of columns with either data type is set to 255.</span></span> <span data-ttu-id="bd97e-142">对 XML 源中的数据截断的处理方式与其他数据流组件中截断的处理方式相同。</span><span class="sxs-lookup"><span data-stu-id="bd97e-142">Data truncation in the XML source is handled the same way as truncation in other data flow components.</span></span> <span data-ttu-id="bd97e-143">有关详细信息，请参阅 [数据中的错误处理](error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bd97e-143">For more information, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="bd97e-144">您可以修改数据类型和列长度。</span><span class="sxs-lookup"><span data-stu-id="bd97e-144">You can modify the data type and the column length.</span></span> <span data-ttu-id="bd97e-145">有关详细信息，请参阅 [Integration Services 数据类型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bd97e-145">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="configuration-of-the-xml-source"></a><span data-ttu-id="bd97e-146">XML 源的配置</span><span class="sxs-lookup"><span data-stu-id="bd97e-146">Configuration of the XML Source</span></span>  
 <span data-ttu-id="bd97e-147">XML 源支持三种不同的数据访问模式。</span><span class="sxs-lookup"><span data-stu-id="bd97e-147">The XML source supports three different data access modes.</span></span> <span data-ttu-id="bd97e-148">您可以指定 XML 数据文件的文件位置、包含文件位置的变量或包含 XML 数据的变量。</span><span class="sxs-lookup"><span data-stu-id="bd97e-148">You can specify the file location of the XML data file, the variable that contains the file location, or the variable that contains the XML data.</span></span>  
  
 <span data-ttu-id="bd97e-149">XML 源包括可以在加载包时通过属性表达式进行更新的 `XMLData` 和 `XMLSchemaDefinition` 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="bd97e-149">The XML source includes the `XMLData` and `XMLSchemaDefinition` custom properties that can be updated by property expressions when the package is loaded.</span></span> <span data-ttu-id="bd97e-150">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../expressions/use-property-expressions-in-packages.md)和 [XML 源自定义属性](xml-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bd97e-150">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [XML Source Custom Properties](xml-source-custom-properties.md).</span></span>  
  
 <span data-ttu-id="bd97e-151">XML 源支持多个常规输出和多个错误输出。</span><span class="sxs-lookup"><span data-stu-id="bd97e-151">The XML source supports multiple regular outputs and multiple error outputs.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bd97e-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含用于配置 XML 源的“XML 源编辑器”对话框  。</span><span class="sxs-lookup"><span data-stu-id="bd97e-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes the **XML Source Edito**r dialog box for configuring the XML source.</span></span> <span data-ttu-id="bd97e-153">此对话框在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中可用。</span><span class="sxs-lookup"><span data-stu-id="bd97e-153">This dialog box is available in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="bd97e-154">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="bd97e-154">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bd97e-155">有关可以在 **“XML 源编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="bd97e-155">For more information about the properties that you can set in the **XML Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="bd97e-156">XML 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="bd97e-156">XML Source Editor &#40;Connection Manager Page&#41;</span></span>](../xml-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="bd97e-157">XML 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="bd97e-157">XML Source Editor &#40;Columns Page&#41;</span></span>](../xml-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="bd97e-158">XML 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="bd97e-158">XML Source Editor &#40;Error Output Page&#41;</span></span>](../xml-source-editor-error-output-page.md)  
  
 <span data-ttu-id="bd97e-159">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="bd97e-159">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="bd97e-160">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="bd97e-160">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="bd97e-161">Common Properties</span><span class="sxs-lookup"><span data-stu-id="bd97e-161">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="bd97e-162">XML 源自定义属性</span><span class="sxs-lookup"><span data-stu-id="bd97e-162">XML Source Custom Properties</span></span>](xml-source-custom-properties.md)  
  
 <span data-ttu-id="bd97e-163">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="bd97e-163">For more information about how to set the properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="bd97e-164">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="bd97e-164">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="bd97e-165">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bd97e-165">Related Tasks</span></span>  
 [<span data-ttu-id="bd97e-166">使用 XML 源提取数据</span><span class="sxs-lookup"><span data-stu-id="bd97e-166">Extract Data by Using the XML Source</span></span>](xml-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="bd97e-167">相关内容</span><span class="sxs-lookup"><span data-stu-id="bd97e-167">Related Content</span></span>  
 <span data-ttu-id="bd97e-168">技术文章，[使用 XML 文件配置 SSIS 包](https://www.sqlshack.com/using-xml-file-configure-ssis-package/)。</span><span class="sxs-lookup"><span data-stu-id="bd97e-168">Technical article, [Using an XML file to configure an SSIS package](https://www.sqlshack.com/using-xml-file-configure-ssis-package/).</span></span>  
  
  
