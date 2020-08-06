---
title: XML 任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.f1
helpviewer_keywords:
- XML [Integration Services]
- XML task [Integration Services]
ms.assetid: 9f761846-390e-46d5-9db7-858943d40849
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6c63a95f6972b53f88e4db1ab6f980971accac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587537"
---
# <a name="xml-task"></a><span data-ttu-id="87ae9-102">XML 任务</span><span class="sxs-lookup"><span data-stu-id="87ae9-102">XML Task</span></span>
  <span data-ttu-id="87ae9-103">XML 任务用于与 XML 数据配合使用。</span><span class="sxs-lookup"><span data-stu-id="87ae9-103">The XML task is used to work with XML data.</span></span> <span data-ttu-id="87ae9-104">使用此任务，包可以检索 XML 文档，使用可扩展样式表语言转换 (XSLT) 样式表和 XPath 表达式对文档应用运算，合并多个文档，还可以验证、比较更新的文档并将其保存到文件和变量。</span><span class="sxs-lookup"><span data-stu-id="87ae9-104">Using this task, a package can retrieve XML documents, apply operations to the documents by using Extensible Stylesheet Language Transformations (XSLT) style sheets and XPath expressions, merge multiple documents, or validate, compare, and save the updated documents to files and variables.</span></span>  
  
 <span data-ttu-id="87ae9-105">此任务使 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包能够在运行时动态修改 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-105">This task enables an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to dynamically modify XML documents at run time.</span></span> <span data-ttu-id="87ae9-106">可以将 XML 任务用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="87ae9-106">You can use the XML task for the following purposes:</span></span>  
  
-   <span data-ttu-id="87ae9-107">重新设置 XML 文档格式。</span><span class="sxs-lookup"><span data-stu-id="87ae9-107">Reformat an XML document.</span></span> <span data-ttu-id="87ae9-108">例如，XML 任务可以访问 XML 文件中的报表并动态应用 XSLT 样式表来自定义文档表示形式。</span><span class="sxs-lookup"><span data-stu-id="87ae9-108">For example, the task can access a report that resides in an XML file and dynamically apply an XSLT style sheet to customize the document presentation.</span></span>  
  
-   <span data-ttu-id="87ae9-109">选择 XML 文档部分。</span><span class="sxs-lookup"><span data-stu-id="87ae9-109">Select sections of an XML document.</span></span> <span data-ttu-id="87ae9-110">例如，XML 任务可以访问 XML 文件中的报表并动态应用 XPath 表达式来选择 XML 文档的一部分。</span><span class="sxs-lookup"><span data-stu-id="87ae9-110">For example, the task can access a report that resides in an XML file and dynamically apply an XPath expression to select a section of the document.</span></span> <span data-ttu-id="87ae9-111">此运算还可以获得并处理 XML 文档中的值。</span><span class="sxs-lookup"><span data-stu-id="87ae9-111">The operation can also get and process values in the document.</span></span>  
  
-   <span data-ttu-id="87ae9-112">合并来自多个源的文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-112">Merge documents from many sources.</span></span> <span data-ttu-id="87ae9-113">例如，XML 任务可从多个源下载报表并动态地将它们合并为一个综合的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-113">For example, the task can download reports from multiple sources and dynamically merge them into one comprehensive XML document.</span></span>  
  
-   <span data-ttu-id="87ae9-114">验证 XML 文档并选择性地获取详细错误输出。</span><span class="sxs-lookup"><span data-stu-id="87ae9-114">Validate an XML document and optionally get detailed error output.</span></span> <span data-ttu-id="87ae9-115">有关详细信息，请参阅 [Validate XML with the XML Task](xml-task.md)。</span><span class="sxs-lookup"><span data-stu-id="87ae9-115">For more info, see [Validate XML with the XML Task](xml-task.md).</span></span>  
  
 <span data-ttu-id="87ae9-116">通过使用 XML 源从 XML 文档中提取值的方法，可以将 XML 数据包含在数据流中。</span><span class="sxs-lookup"><span data-stu-id="87ae9-116">You can include XML data in a data flow by using an XML source to extract values from an XML document.</span></span> <span data-ttu-id="87ae9-117">有关详细信息，请参阅 [XML Source](../data-flow/xml-source.md)。</span><span class="sxs-lookup"><span data-stu-id="87ae9-117">For more information, see [XML Source](../data-flow/xml-source.md).</span></span>  
  
## <a name="xml-operations"></a><span data-ttu-id="87ae9-118">XML 操作</span><span class="sxs-lookup"><span data-stu-id="87ae9-118">XML Operations</span></span>  
 <span data-ttu-id="87ae9-119">XML 任务首先执行的运算是检索特定的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-119">The first action the XML task performs is to retrieve a specific XML document.</span></span> <span data-ttu-id="87ae9-120">此运算内置于 XML 任务中并可自动执行。</span><span class="sxs-lookup"><span data-stu-id="87ae9-120">This action is built into the XML task and occurs automatically.</span></span> <span data-ttu-id="87ae9-121">检索后的 XML 文档可用作 XML 任务执行运算的数据源。</span><span class="sxs-lookup"><span data-stu-id="87ae9-121">The retrieved XML document is used as the source of data for the operation that the XML task performs.</span></span>  
  
 <span data-ttu-id="87ae9-122">XML 的 Diff、Merge 和 Patch 运算需要两个操作数。</span><span class="sxs-lookup"><span data-stu-id="87ae9-122">The XML operations Diff, Merge, and Patch require two operands.</span></span> <span data-ttu-id="87ae9-123">第一个操作数指定源 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-123">The first operand specifies the source XML document.</span></span> <span data-ttu-id="87ae9-124">第二个操作数也指定一个 XML 文档，其内容取决于运算的要求。</span><span class="sxs-lookup"><span data-stu-id="87ae9-124">The second operand also specifies an XML document, the contents of which depend on the requirements of the operation.</span></span> <span data-ttu-id="87ae9-125">例如，Diff 运算要比较两个文档；因此第二个操作数指定另一个相似的 XML 文档，供源 XML 文档与之比较。</span><span class="sxs-lookup"><span data-stu-id="87ae9-125">For example, the Diff operation compares two documents; therefore, the second operand specifies another, similar XML document to which the source XML document is compared.</span></span>  
  
 <span data-ttu-id="87ae9-126">XML 任务可使用变量或文件连接管理器作为源，或将 XML 数据包含在任务属性中。</span><span class="sxs-lookup"><span data-stu-id="87ae9-126">The XML task can use a variable or a File connection manager as its source, or include the XML data in a task property.</span></span>  
  
 <span data-ttu-id="87ae9-127">如果源是变量，则该指定的变量包含 XML 文档的路径。</span><span class="sxs-lookup"><span data-stu-id="87ae9-127">If the source is a variable, the specified variable contains the path of the XML document.</span></span>  
  
 <span data-ttu-id="87ae9-128">如果源是文件连接管理器，则该指定的文件连接管理器提供源信息。</span><span class="sxs-lookup"><span data-stu-id="87ae9-128">If the source is a File connection manager, the specified File connection manager provides the source information.</span></span> <span data-ttu-id="87ae9-129">文件连接管理器与 XML 任务分开配置，并在 XML 任务中被引用。</span><span class="sxs-lookup"><span data-stu-id="87ae9-129">The File connection manager is configured separately from the XML task, and is referenced in the XML task.</span></span> <span data-ttu-id="87ae9-130">文件连接管理器的连接字符串可指定 XML 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="87ae9-130">The connection string of the File connection manager specifies the path of the XML file.</span></span> <span data-ttu-id="87ae9-131">有关详细信息，请参阅 [File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="87ae9-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="87ae9-132">XML 任务可以设置为将运算结果保存到变量或文件。</span><span class="sxs-lookup"><span data-stu-id="87ae9-132">The XML task can be configured to save the result of the operation to a variable or to a file.</span></span> <span data-ttu-id="87ae9-133">如果要保存到文件中，XML 任务将使用文件连接管理器访问该文件。</span><span class="sxs-lookup"><span data-stu-id="87ae9-133">If saving to a file, the XML task uses a File connection manager to access the file.</span></span> <span data-ttu-id="87ae9-134">您也可以将 Diff 运算生成的 Diffgram 结果保存到文件和变量中。</span><span class="sxs-lookup"><span data-stu-id="87ae9-134">You can also save the results of the Diffgram generated by the Diff operation to files and variables.</span></span>  
  
## <a name="predefined-xml-operations"></a><span data-ttu-id="87ae9-135">预定义的 XML 运算</span><span class="sxs-lookup"><span data-stu-id="87ae9-135">Predefined XML Operations</span></span>  
 <span data-ttu-id="87ae9-136">XML 任务包含一组用来处理 XML 文档的预定义运算。</span><span class="sxs-lookup"><span data-stu-id="87ae9-136">The XML task includes a predefined set of operations for working with XML documents.</span></span> <span data-ttu-id="87ae9-137">下表介绍了这些运算。</span><span class="sxs-lookup"><span data-stu-id="87ae9-137">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="87ae9-138">Operation</span><span class="sxs-lookup"><span data-stu-id="87ae9-138">Operation</span></span>|<span data-ttu-id="87ae9-139">说明</span><span class="sxs-lookup"><span data-stu-id="87ae9-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87ae9-140">差异</span><span class="sxs-lookup"><span data-stu-id="87ae9-140">Diff</span></span>|<span data-ttu-id="87ae9-141">比较两个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-141">Compares two XML documents.</span></span> <span data-ttu-id="87ae9-142">Diff 运算把源 XML 文档作为基准文档，将其与另一个 XML 文档进行比较，检测二者间的差异，并将差异写入 XML Diffgram 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-142">Using the source XML document as the base document, the Diff operation compares it to a second XML document, detects their differences, and writes the differences to an XML Diffgram document.</span></span> <span data-ttu-id="87ae9-143">此运算包含用来自定义比较的属性。</span><span class="sxs-lookup"><span data-stu-id="87ae9-143">This operation includes properties for customizing the comparison.</span></span>|  
|<span data-ttu-id="87ae9-144">合并</span><span class="sxs-lookup"><span data-stu-id="87ae9-144">Merge</span></span>|<span data-ttu-id="87ae9-145">合并两个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-145">Merges two XML documents.</span></span> <span data-ttu-id="87ae9-146">Merge 运算使用源 XML 文档作为基文档，将第二个文档的内容添加到其中。</span><span class="sxs-lookup"><span data-stu-id="87ae9-146">Using the source XML document as the base document, the Merge operation adds the content of a second document into the base document.</span></span> <span data-ttu-id="87ae9-147">此运算可以在基文档内指定合并位置。</span><span class="sxs-lookup"><span data-stu-id="87ae9-147">The operation can specify a merge location within the base document.</span></span>|  
|<span data-ttu-id="87ae9-148">修补程序</span><span class="sxs-lookup"><span data-stu-id="87ae9-148">Patch</span></span>|<span data-ttu-id="87ae9-149">将 Diff 运算的输出（称为 Diffgram 文档）应用到 XML 文档，以创建包含该 Diffgram 文档内容的新的父文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-149">Applies the output from the Diff operation, called a Diffgram document, to an XML document, to create a new parent document that includes content from the Diffgram document.</span></span>|  
|<span data-ttu-id="87ae9-150">验证</span><span class="sxs-lookup"><span data-stu-id="87ae9-150">Validate</span></span>|<span data-ttu-id="87ae9-151">根据文档类型定义 (DTD) 或 XML 架构定义 (XSD) 架构验证 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-151">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span>|  
|<span data-ttu-id="87ae9-152">XPath</span><span class="sxs-lookup"><span data-stu-id="87ae9-152">XPath</span></span>|<span data-ttu-id="87ae9-153">执行 XPath 查询和计算。</span><span class="sxs-lookup"><span data-stu-id="87ae9-153">Performs XPath queries and evaluations.</span></span>|  
|<span data-ttu-id="87ae9-154">XSLT</span><span class="sxs-lookup"><span data-stu-id="87ae9-154">XSLT</span></span>|<span data-ttu-id="87ae9-155">对 XML 文档执行 XSL 转换。</span><span class="sxs-lookup"><span data-stu-id="87ae9-155">Performs XSL transformations on XML documents.</span></span>|  
  
### <a name="diff-operation"></a><span data-ttu-id="87ae9-156">Diff 运算</span><span class="sxs-lookup"><span data-stu-id="87ae9-156">Diff Operation</span></span>  
 <span data-ttu-id="87ae9-157">根据比较要求必须是快速还是精确，可以将 Diff 运算配置为使用不同的比较算法。</span><span class="sxs-lookup"><span data-stu-id="87ae9-157">The Diff operation can be configured to use a different comparison algorithm depending on whether the comparison must be fast or precise.</span></span> <span data-ttu-id="87ae9-158">还可通过对 Diff 运算配置，使之可以根据当前比较文档的大小，自动选择使用快速比较或精确比较。</span><span class="sxs-lookup"><span data-stu-id="87ae9-158">The operation can also be configured to automatically select a fast or precise comparison based on the size of the documents being compared.</span></span>  
  
 <span data-ttu-id="87ae9-159">Diff 运算中包含一组用于自定义 XML 比较的选项。</span><span class="sxs-lookup"><span data-stu-id="87ae9-159">The Diff operation includes a set of options that customize the XML comparison.</span></span> <span data-ttu-id="87ae9-160">下表对这些选项进行说明：</span><span class="sxs-lookup"><span data-stu-id="87ae9-160">The following table describes the options.</span></span>  
  
|<span data-ttu-id="87ae9-161">选项</span><span class="sxs-lookup"><span data-stu-id="87ae9-161">Option</span></span>|<span data-ttu-id="87ae9-162">说明</span><span class="sxs-lookup"><span data-stu-id="87ae9-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="87ae9-163">**IgnoreComments**</span><span class="sxs-lookup"><span data-stu-id="87ae9-163">**IgnoreComments**</span></span>|<span data-ttu-id="87ae9-164">该值用于指定是否比较注释节点。</span><span class="sxs-lookup"><span data-stu-id="87ae9-164">A value that specifies whether comment nodes are compared.</span></span>|  
|<span data-ttu-id="87ae9-165">**IgnoreNamespaces**</span><span class="sxs-lookup"><span data-stu-id="87ae9-165">**IgnoreNamespaces**</span></span>|<span data-ttu-id="87ae9-166">该值用于指定是否将元素的命名空间统一资源标识符 (URI) 与其属性名称相比较。</span><span class="sxs-lookup"><span data-stu-id="87ae9-166">A value that specifies whether the namespace uniform resource identifier (URI) of an element and its attribute names are compared.</span></span> <span data-ttu-id="87ae9-167">如果将此选项设置为 `true`，则名称部分相同但命名空间不同的两个元素将被视为相同元素。</span><span class="sxs-lookup"><span data-stu-id="87ae9-167">If this option is set to `true`, two elements that have the same local name but a different namespace are considered to be identical.</span></span>|  
|<span data-ttu-id="87ae9-168">**IgnorePrefixes**</span><span class="sxs-lookup"><span data-stu-id="87ae9-168">**IgnorePrefixes**</span></span>|<span data-ttu-id="87ae9-169">该值用于指定是否比较元素前缀和属性名称。</span><span class="sxs-lookup"><span data-stu-id="87ae9-169">A value that specifies whether prefixes of element and attribute names are compared.</span></span> <span data-ttu-id="87ae9-170">如果将此选项设置为 `true,`，则本地名称相同但命名空间 URI 和前缀不同的两个元素将被视为相同元素。</span><span class="sxs-lookup"><span data-stu-id="87ae9-170">If this option is set to `true,` two elements that have the same local name but a different namespace URI and prefix are considered identical.</span></span>|  
|<span data-ttu-id="87ae9-171">**IgnoreXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="87ae9-171">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="87ae9-172">该值用于指定是否比较 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="87ae9-172">A value that specifies whether the XML declarations are compared.</span></span>|  
|<span data-ttu-id="87ae9-173">**IgnoreOrderOfChildElements**</span><span class="sxs-lookup"><span data-stu-id="87ae9-173">**IgnoreOrderOfChildElements**</span></span>|<span data-ttu-id="87ae9-174">该值用于指定是否比较子元素顺序。</span><span class="sxs-lookup"><span data-stu-id="87ae9-174">A value that specifies whether the order of child elements is compared.</span></span> <span data-ttu-id="87ae9-175">如果将此选项设置为 `true`，则在同级组成的列表中仅位置不同的子元素将被视为相同元素。</span><span class="sxs-lookup"><span data-stu-id="87ae9-175">If this option is set to `true`, child elements that differ only in their position in a list of siblings are considered to be identical.</span></span>|  
|<span data-ttu-id="87ae9-176">**IgnoreWhiteSpaces**</span><span class="sxs-lookup"><span data-stu-id="87ae9-176">**IgnoreWhiteSpaces**</span></span>|<span data-ttu-id="87ae9-177">该值用于指定是否比较空格。</span><span class="sxs-lookup"><span data-stu-id="87ae9-177">A value that specifies whether white spaces are compared.</span></span>|  
|<span data-ttu-id="87ae9-178">**IgnoreProcessingInstructions**</span><span class="sxs-lookup"><span data-stu-id="87ae9-178">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="87ae9-179">该值用于指定是否比较处理指令。</span><span class="sxs-lookup"><span data-stu-id="87ae9-179">A value that specifies whether processing instructions are compared.</span></span>|  
|<span data-ttu-id="87ae9-180">**IgnoreDTD**</span><span class="sxs-lookup"><span data-stu-id="87ae9-180">**IgnoreDTD**</span></span>|<span data-ttu-id="87ae9-181">该值用于指定是否忽略 DTD。</span><span class="sxs-lookup"><span data-stu-id="87ae9-181">A value that specifies whether the DTD is ignored.</span></span>|  
  
### <a name="merge-operation"></a><span data-ttu-id="87ae9-182">Merge 运算</span><span class="sxs-lookup"><span data-stu-id="87ae9-182">Merge Operation</span></span>  
 <span data-ttu-id="87ae9-183">使用 XPath 语句标识源文档中的合并位置时，此语句应返回一个节点。</span><span class="sxs-lookup"><span data-stu-id="87ae9-183">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="87ae9-184">如果该语句返回多个节点，则仅使用第一个节点。</span><span class="sxs-lookup"><span data-stu-id="87ae9-184">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="87ae9-185">第二个文档的内容在 XPath 查询返回的第一个节点下合并。</span><span class="sxs-lookup"><span data-stu-id="87ae9-185">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
### <a name="xpath-operation"></a><span data-ttu-id="87ae9-186">XPath 运算</span><span class="sxs-lookup"><span data-stu-id="87ae9-186">XPath Operation</span></span>  
 <span data-ttu-id="87ae9-187">可将 XPath 运算配置为使用不同类型的 XPath 功能。</span><span class="sxs-lookup"><span data-stu-id="87ae9-187">The XPath operation can be configured to use different types of XPath functionality.</span></span>  
  
-   <span data-ttu-id="87ae9-188">选择“计算”  选项，以实现各种 XPath 函数，如 sum()。</span><span class="sxs-lookup"><span data-stu-id="87ae9-188">Select the **Evaluation** option to implement XPath functions such as sum().</span></span>  
  
-   <span data-ttu-id="87ae9-189">选择 **“结点列表”** 选项，将选定节点以 XML 片段方式返回。</span><span class="sxs-lookup"><span data-stu-id="87ae9-189">Select the **Node list** option to return the selected nodes as an XML fragment.</span></span>  
  
-   <span data-ttu-id="87ae9-190">选择“值”  选项，以返回所有选定节点的内部文本值，这些值串联为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="87ae9-190">Select the **Values** option to return the inner text value of all the selected nodes, concatenated into a string.</span></span>  
  
### <a name="validation-operation"></a><span data-ttu-id="87ae9-191">Validation 运算</span><span class="sxs-lookup"><span data-stu-id="87ae9-191">Validation Operation</span></span>  
 <span data-ttu-id="87ae9-192">可以将 Validation 运算配置为使用文档类型定义 (DTD) 架构或 XML 架构定义 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="87ae9-192">The Validation operation can be configured to use either a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span>  
  
 <span data-ttu-id="87ae9-193">启用 `ValidationDetails` 以获取详细错误输出。</span><span class="sxs-lookup"><span data-stu-id="87ae9-193">Enable `ValidationDetails` to get detailed error output.</span></span> <span data-ttu-id="87ae9-194">有关详细信息，请参阅 [Validate XML with the XML Task](xml-task.md)。</span><span class="sxs-lookup"><span data-stu-id="87ae9-194">For more info, see [Validate XML with the XML Task](xml-task.md).</span></span>  
  
## <a name="xml-document-encoding"></a><span data-ttu-id="87ae9-195">XML 文档编码</span><span class="sxs-lookup"><span data-stu-id="87ae9-195">XML Document Encoding</span></span>  
 <span data-ttu-id="87ae9-196">XML 任务仅支持合并 Unicode 文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-196">The XML task supports merging of Unicode documents only.</span></span> <span data-ttu-id="87ae9-197">这表示 XML 任务只能对采用 Unicode 编码的文档应用 Merge 运算。</span><span class="sxs-lookup"><span data-stu-id="87ae9-197">This means the task can apply the Merge operation only to documents that have a Unicode encoding.</span></span> <span data-ttu-id="87ae9-198">使用其他编码将导致 XML 任务失败。</span><span class="sxs-lookup"><span data-stu-id="87ae9-198">Use of other encodings will cause the XML task to fail.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87ae9-199">Diff 和 Patch 运算中包含一个选项，可以忽略第二操作数 XML 数据中的 XML 声明，这就使得在这些运算中能够使用具有其他编码的文档。</span><span class="sxs-lookup"><span data-stu-id="87ae9-199">The Diff and Patch operations include an option to ignore the XML declaration in the second-operand XML data, making it possible to use documents that have other encodings in these operations.</span></span>  
  
 <span data-ttu-id="87ae9-200">若要验证是否可以使用 XML 文档，请查看 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="87ae9-200">To verify that the XML document can be used, review the XML declaration.</span></span> <span data-ttu-id="87ae9-201">该声明必须显式指定 UTF-8（即 8 位 Unicode 编码）。</span><span class="sxs-lookup"><span data-stu-id="87ae9-201">The declaration must explicitly specify UTF-8, which indicates 8-bit Unicode encoding.</span></span>  
  
 <span data-ttu-id="87ae9-202">下面的标记显示 Unicode 8 位编码。</span><span class="sxs-lookup"><span data-stu-id="87ae9-202">The following tag shows the Unicode 8-bit encoding.</span></span>  
  
 `<?xml version="1.0" encoding="UTF-8"?>`  
  
## <a name="custom-logging-messages-available-on-the-xml-task"></a><span data-ttu-id="87ae9-203">XML 任务可用的自定义日志记录消息</span><span class="sxs-lookup"><span data-stu-id="87ae9-203">Custom Logging Messages Available on the XML Task</span></span>  
 <span data-ttu-id="87ae9-204">下表介绍了 XML 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="87ae9-204">The following table describes the custom log entry for the XML task.</span></span> <span data-ttu-id="87ae9-205">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="87ae9-205">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="87ae9-206">日志项</span><span class="sxs-lookup"><span data-stu-id="87ae9-206">Log entry</span></span>|<span data-ttu-id="87ae9-207">说明</span><span class="sxs-lookup"><span data-stu-id="87ae9-207">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="87ae9-208">提供任务所执行的操作的相关信息</span><span class="sxs-lookup"><span data-stu-id="87ae9-208">Provides information about the operation that the task performs</span></span>|  
  
## <a name="configuration-of-the-xml-task"></a><span data-ttu-id="87ae9-209">XML 任务的配置</span><span class="sxs-lookup"><span data-stu-id="87ae9-209">Configuration of the XML Task</span></span>  
 <span data-ttu-id="87ae9-210">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="87ae9-210">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="87ae9-211">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="87ae9-211">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="87ae9-212">XML 任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="87ae9-212">XML Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="87ae9-213">使用 XML 任务验证 XML</span><span class="sxs-lookup"><span data-stu-id="87ae9-213">Validate XML with the XML Task</span></span>](xml-task.md)  
  
-   [<span data-ttu-id="87ae9-214">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="87ae9-214">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="87ae9-215">有关在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中如何设置属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="87ae9-215">For more information about how to set properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="87ae9-216">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="87ae9-216">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-xml-task"></a><span data-ttu-id="87ae9-217">XML 任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="87ae9-217">Programmatic Configuration of the XML Task</span></span>  
 <span data-ttu-id="87ae9-218">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="87ae9-218">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.XMLTask.XMLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="87ae9-219">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="87ae9-219">Related Tasks</span></span>  
 [<span data-ttu-id="87ae9-220">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="87ae9-220">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="87ae9-221">相关内容</span><span class="sxs-lookup"><span data-stu-id="87ae9-221">Related Content</span></span>  
  
-   <span data-ttu-id="87ae9-222">agilebi.com 上的博客文章 [XML 目标脚本组件](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/)</span><span class="sxs-lookup"><span data-stu-id="87ae9-222">Blog entry, [XML Destination Script Component](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/), on agilebi.com</span></span>  
  
-   <span data-ttu-id="87ae9-223">www.codeplex.com 上的 CodePlex 示例 [处理 XML 数据包示例](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples)</span><span class="sxs-lookup"><span data-stu-id="87ae9-223">CodePlex sample, [Process XML Data Package Sample](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples), on www.codeplex.com</span></span>  
  
