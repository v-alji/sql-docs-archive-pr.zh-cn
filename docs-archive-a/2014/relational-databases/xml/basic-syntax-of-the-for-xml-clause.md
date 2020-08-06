---
title: FOR XML 子句的基本语法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- BINARY BASE64 directive
- ROOT directive
- FOR XML clause, BINARY BASE64 directive
- FOR XML clause, syntax
- FOR XML clause, ROOT directive
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc0410e7a54674673f64442d8a3cf9476d250033
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577441"
---
# <a name="basic-syntax-of-the-for-xml-clause"></a><span data-ttu-id="1504c-102">FOR XML 子句的基本语法</span><span class="sxs-lookup"><span data-stu-id="1504c-102">Basic Syntax of the FOR XML Clause</span></span>
  <span data-ttu-id="1504c-103">FOR XML 模式可以是 RAW、AUTO、EXPLICIT 或 PATH。</span><span class="sxs-lookup"><span data-stu-id="1504c-103">The FOR XML mode can be RAW, AUTO, EXPLICIT, or PATH.</span></span> <span data-ttu-id="1504c-104">它确定产生的 XML 的形状。</span><span class="sxs-lookup"><span data-stu-id="1504c-104">It determines the shape of the resulting XML.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1504c-105">不推荐使用 FOR XML 选项的 XMLDATA 指令。</span><span class="sxs-lookup"><span data-stu-id="1504c-105">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="1504c-106">如果是 RAW 和 AUTO 模式，请使用 XSD 生成。</span><span class="sxs-lookup"><span data-stu-id="1504c-106">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="1504c-107">在 EXPLICT 模式下，没有可以代替 XMLDATA 指令的项。</span><span class="sxs-lookup"><span data-stu-id="1504c-107">There is no replacement for the XMLDATA directive in EXPLICT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="1504c-108">下面是 FOR 子句中所述的基本语法[ (transact-sql) ](/sql/t-sql/queries/select-for-clause-transact-sql)：</span><span class="sxs-lookup"><span data-stu-id="1504c-108">Following is the basic syntax that is described in [FOR Clause (Transact-SQL)](/sql/t-sql/queries/select-for-clause-transact-sql):</span></span>  
  
```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]   
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1504c-109">参数</span><span class="sxs-lookup"><span data-stu-id="1504c-109">Arguments</span></span>  
 <span data-ttu-id="1504c-110">RAW[('*ElementName*')]</span><span class="sxs-lookup"><span data-stu-id="1504c-110">RAW[('*ElementName*')]</span></span>  
 <span data-ttu-id="1504c-111">获得查询结果并将结果集内的每一行转换为以一般标识符 \<row /> 作为元素标记的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-111">Takes the query result and transforms each row in the result set into an XML element that has a generic identifier, \<row />, as the element tag.</span></span> <span data-ttu-id="1504c-112">使用此指令时，可以选择指定行元素的名称。</span><span class="sxs-lookup"><span data-stu-id="1504c-112">You can optionally specify a name for the row element when you use this directive.</span></span> <span data-ttu-id="1504c-113">产生的 XML 将把指定的 *ElementName* 用作为每行生成的行元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-113">The resulting XML will use the specified *ElementName* as the row element generated for each row.</span></span> <span data-ttu-id="1504c-114">有关详细信息，请参阅 [将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-114">For more information, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-115">AUTO</span><span class="sxs-lookup"><span data-stu-id="1504c-115">AUTO</span></span>  
 <span data-ttu-id="1504c-116">以简单的嵌套 XML 树返回查询结果。</span><span class="sxs-lookup"><span data-stu-id="1504c-116">Returns query results in a simple, nested XML tree.</span></span> <span data-ttu-id="1504c-117">FROM 子句中的每个表（在 SELECT 子句中至少为其列出了一列）都表示为一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-117">Each table in the FROM clause for which at least one column is listed in the SELECT clause is represented as an XML element.</span></span> <span data-ttu-id="1504c-118">SELECT 子句中列出的列映射到适当的元素属性。</span><span class="sxs-lookup"><span data-stu-id="1504c-118">The columns listed in the SELECT clause are mapped to the appropriate element attributes.</span></span> <span data-ttu-id="1504c-119">有关详细信息，请参阅 [将 AUTO 模式与 FOR XML 一起使用](use-auto-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-119">For more information, see [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-120">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="1504c-120">EXPLICIT</span></span>  
 <span data-ttu-id="1504c-121">指定显式定义产生的 XML 树的形状。</span><span class="sxs-lookup"><span data-stu-id="1504c-121">Specifies that the shape of the resulting XML tree is defined explicitly.</span></span> <span data-ttu-id="1504c-122">使用此模式时，必须以一种特定的方式编写查询，以便显式指定所需嵌套的其他信息。</span><span class="sxs-lookup"><span data-stu-id="1504c-122">By using this mode, queries must be written in a particular way so additional information about the nesting you want is specified explicitly.</span></span> <span data-ttu-id="1504c-123">有关详细信息，请参阅 [将 EXPLICIT 模式与 FOR XML 一起使用](use-explicit-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-123">For more information, see [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-124">PATH</span><span class="sxs-lookup"><span data-stu-id="1504c-124">PATH</span></span>  
 <span data-ttu-id="1504c-125">提供一种更简单的方式来混合元素和属性，并引入表示复杂属性的其他嵌套。</span><span class="sxs-lookup"><span data-stu-id="1504c-125">Provides a simpler way to mix elements and attributes, and to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="1504c-126">可以使用 FOR XML EXPLICIT 模式查询从行集中构造这种 XML，但 PATH 模式针对可能很烦琐的 EXPLICIT 模式查询提供了一种更简单的替代方式。</span><span class="sxs-lookup"><span data-stu-id="1504c-126">You can use FOR XML EXPLICIT mode queries to construct this kind of XML from a rowset, but the PATH mode provides a simpler alternative to the possibly cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="1504c-127">通过 PATH 模式，以及用于编写嵌套 FOR XML 查询的功能和返回 **xml** 类型实例的 TYPE 指令，您可以编写简单的查询。</span><span class="sxs-lookup"><span data-stu-id="1504c-127">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span> <span data-ttu-id="1504c-128">它为编写大多数 EXPLICIT 模式查询提供了一个替代方式。</span><span class="sxs-lookup"><span data-stu-id="1504c-128">It provides an alternative to writing most EXPLICIT mode queries.</span></span> <span data-ttu-id="1504c-129">默认情况下，PATH 模式为结果集中的每一行生成一个 \<row> 元素包装。</span><span class="sxs-lookup"><span data-stu-id="1504c-129">By default, PATH mode generates a \<row> element wrapper for each row in the result set.</span></span> <span data-ttu-id="1504c-130">您还可以选择指定元素名称。</span><span class="sxs-lookup"><span data-stu-id="1504c-130">You can optionally specify an element name.</span></span> <span data-ttu-id="1504c-131">如果这样，则指定的名称用作包装元素名称。</span><span class="sxs-lookup"><span data-stu-id="1504c-131">If you do, the specified name is used as the wrapper element name.</span></span> <span data-ttu-id="1504c-132">如果提供空字符串 (FOR XML PATH (''))，则不会生成任何包装元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-132">If you provide an empty string (FOR XML PATH ('')), no wrapper element is generated.</span></span> <span data-ttu-id="1504c-133">有关详细信息，请参阅 [将 PATH 模式与 FOR XML 一起使用](use-path-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-133">For more information, see [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-134">XMLDATA</span><span class="sxs-lookup"><span data-stu-id="1504c-134">XMLDATA</span></span>  
 <span data-ttu-id="1504c-135">指定应返回内联 XML 数据简化 (XDR) 架构。</span><span class="sxs-lookup"><span data-stu-id="1504c-135">Specifies that an inline XML-Data Reduced (XDR) schema should be returned.</span></span> <span data-ttu-id="1504c-136">文档的架构被预置为内联架构。</span><span class="sxs-lookup"><span data-stu-id="1504c-136">The schema is prepended to the document as an inline schema.</span></span> <span data-ttu-id="1504c-137">有关工作示例，请参阅 [将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-137">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-138">XMLSCHEMA</span><span class="sxs-lookup"><span data-stu-id="1504c-138">XMLSCHEMA</span></span>  
 <span data-ttu-id="1504c-139">返回内联 W3C XML 架构 (XSD)。</span><span class="sxs-lookup"><span data-stu-id="1504c-139">Returns an inline W3C XML Schema (XSD).</span></span> <span data-ttu-id="1504c-140">指定此指令时，可以选择指定目标命名空间 URI。</span><span class="sxs-lookup"><span data-stu-id="1504c-140">You can optionally specify a target namespace URI when specifying this directive.</span></span> <span data-ttu-id="1504c-141">这样将返回架构中指定的命名空间。</span><span class="sxs-lookup"><span data-stu-id="1504c-141">This returns the specified namespace in the schema.</span></span> <span data-ttu-id="1504c-142">有关详细信息，请参阅 [生成内联 XSD 架构](generate-an-inline-xsd-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-142">For more information, see [Generate an Inline XSD Schema](generate-an-inline-xsd-schema.md).</span></span> <span data-ttu-id="1504c-143">有关工作示例，请参阅 [将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-143">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-144">ELEMENTS</span><span class="sxs-lookup"><span data-stu-id="1504c-144">ELEMENTS</span></span>  
 <span data-ttu-id="1504c-145">如果指定 ELEMENTS 选项，则列作为子元素返回。</span><span class="sxs-lookup"><span data-stu-id="1504c-145">If the ELEMENTS option is specified, the columns are returned as subelements.</span></span> <span data-ttu-id="1504c-146">否则，列将映射到 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="1504c-146">Otherwise, they are mapped to XML attributes.</span></span> <span data-ttu-id="1504c-147">只在 RAW、AUTO 和 PATH 模式中支持此选项。</span><span class="sxs-lookup"><span data-stu-id="1504c-147">This option is supported in RAW, AUTO, and PATH modes only.</span></span> <span data-ttu-id="1504c-148">使用此指令时，可以选择指定 XSINIL 或 ABSENT。</span><span class="sxs-lookup"><span data-stu-id="1504c-148">You can optionally specify XSINIL or ABSENT when you use this directive.</span></span> <span data-ttu-id="1504c-149">XSINIL 指定为 NULL 列值创建 **xsi:nil** 属性设置为 True 的元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-149">XSINIL specifies that an element that has an **xsi:nil** attribute set to True be created for NULL column values.</span></span> <span data-ttu-id="1504c-150">默认情况下，或者与 ELEMENTS 一起指定了 ABSENT 时，不会为 NULL 值创建任何元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-150">By default or when ABSENT is specified together with ELEMENTS, no elements are created for NULL values.</span></span> <span data-ttu-id="1504c-151">有关工作示例，请参阅 [将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md) 和 [将 AUTO 模式与 FOR XML 一起使用](use-auto-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-151">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) and [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-152">BINARY BASE64</span><span class="sxs-lookup"><span data-stu-id="1504c-152">BINARY BASE64</span></span>  
 <span data-ttu-id="1504c-153">如果指定 BINARY Base64 选项，则查询所返回的任何二进制数据都用 base64 编码格式表示。</span><span class="sxs-lookup"><span data-stu-id="1504c-153">If the BINARY Base64 option is specified, any binary data returned by the query is represented in base64-encoded format.</span></span> <span data-ttu-id="1504c-154">若要使用 RAW 和 EXPLICIT 模式检索二进制数据，必须指定此选项。</span><span class="sxs-lookup"><span data-stu-id="1504c-154">To retrieve binary data by using RAW and EXPLICIT mode, this option must be specified.</span></span> <span data-ttu-id="1504c-155">在 AUTO 模式中，默认情况下将二进制数据作为引用返回。</span><span class="sxs-lookup"><span data-stu-id="1504c-155">In AUTO mode, binary data is returned as a reference by default.</span></span> <span data-ttu-id="1504c-156">有关工作示例，请参阅 [将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-156">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="1504c-157">TYPE</span><span class="sxs-lookup"><span data-stu-id="1504c-157">TYPE</span></span>  
 <span data-ttu-id="1504c-158">指定查询以 **xml** 类型返回结果。</span><span class="sxs-lookup"><span data-stu-id="1504c-158">Specifies that the query returns the results as the **xml** type.</span></span> <span data-ttu-id="1504c-159">有关详细信息，请参阅 [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="1504c-159">For more information, see [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="1504c-160">ROOT [('*RootName*')]</span><span class="sxs-lookup"><span data-stu-id="1504c-160">ROOT [('*RootName*')]</span></span>  
 <span data-ttu-id="1504c-161">指定向产生的 XML 中添加单个顶级元素。</span><span class="sxs-lookup"><span data-stu-id="1504c-161">Specifies that a single, top-level element be added to the resulting XML.</span></span> <span data-ttu-id="1504c-162">可以选择指定要生成的根元素名称。</span><span class="sxs-lookup"><span data-stu-id="1504c-162">You can optionally specify the root element name to generate.</span></span> <span data-ttu-id="1504c-163">默认值为“root”。</span><span class="sxs-lookup"><span data-stu-id="1504c-163">The default value is "root".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1504c-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1504c-164">See Also</span></span>  
 <span data-ttu-id="1504c-165">[将 RAW 模式与 FOR XML 一起使用](use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1504c-165">[Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="1504c-166">[将 AUTO 模式与 FOR XML 一起使用](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1504c-166">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="1504c-167">[将 EXPLICIT 模式与 FOR XML 一起使用](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1504c-167">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="1504c-168">[将 PATH 模式与 FOR XML 一起使用](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1504c-168">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="1504c-169">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1504c-169">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="1504c-170">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1504c-170">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
