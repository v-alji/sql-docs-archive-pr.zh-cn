---
title: 将 EXPLICIT 模式与 FOR XML 一起使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT FOR XML mode
- FOR XML clause, EXPLICIT mode
- FOR XML EXPLICIT mode
ms.assetid: 8b26e8ce-5465-4e7a-b237-98d0f4578ab1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3db80333c74166301fcff7bb25edea4aca38a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581152"
---
# <a name="use-explicit-mode-with-for-xml"></a><span data-ttu-id="97b94-102">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="97b94-102">Use EXPLICIT Mode with FOR XML</span></span>
  <span data-ttu-id="97b94-103">如主题 [使用 FOR XML 构造 XML](../xml/for-xml-sql-server.md)中所述，使用 RAW 和 AUTO 模式不能很好地控制从查询结果生成的 XML 的形状。</span><span class="sxs-lookup"><span data-stu-id="97b94-103">As described in the topic, [Constructing XML Using FOR XML](../xml/for-xml-sql-server.md), RAW and AUTO mode do not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="97b94-104">但是，对于要从查询结果生成 XML，EXPLICIT 模式会提供非常好的灵活性。</span><span class="sxs-lookup"><span data-stu-id="97b94-104">However, EXPLICIT mode provides the most flexibility in generating the XML you want from a query result.</span></span>  
  
 <span data-ttu-id="97b94-105">必须以特定的方式编写 EXPLICIT 模式查询，以便将有关所需的 XML 的附加信息（如 XML 中的所需嵌套）显式指定为查询的一部分。</span><span class="sxs-lookup"><span data-stu-id="97b94-105">The EXPLICIT mode query must be written in a specific way so that the additional information about the required XML, such as expected nesting in the XML, is explicitly specified as part of the query.</span></span> <span data-ttu-id="97b94-106">根据所请求的 XML，编写 EXPLICIT 模式查询可能会很烦琐。</span><span class="sxs-lookup"><span data-stu-id="97b94-106">Depending on the XML you request, writing EXPLICIT mode queries can be cumbersome.</span></span> <span data-ttu-id="97b94-107">您会发现 [使用 PATH 模式](../xml/use-path-mode-with-for-xml.md) （具有嵌套）相对编写 EXPLICIT 模式查询而言更加简单。</span><span class="sxs-lookup"><span data-stu-id="97b94-107">You may find that [Using PATH Mode](../xml/use-path-mode-with-for-xml.md) with nesting is a simpler alternative to writing EXPLICIT mode queries.</span></span>  
  
 <span data-ttu-id="97b94-108">因为将所需的 XML 描述为 EXPLICIT 模式查询的一部分，所以必须确保生成的 XML 格式正确且有效。</span><span class="sxs-lookup"><span data-stu-id="97b94-108">Because you describe the XML you want as part of the query in EXPLICIT mode, you must ensure that the generated XML is well formed and valid.</span></span>  
  
## <a name="rowset-processing-in-explicit-mode"></a><span data-ttu-id="97b94-109">EXPLICIT 模式下的行集处理</span><span class="sxs-lookup"><span data-stu-id="97b94-109">Rowset Processing in EXPLICIT Mode</span></span>  
 <span data-ttu-id="97b94-110">EXPLICIT 模式会将由查询执行生成的行集转换为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="97b94-110">The EXPLICIT mode transforms the rowset that results from the query execution into an XML document.</span></span> <span data-ttu-id="97b94-111">为使 EXPLICIT 模式生成 XML 文档，行集必须具有特定的格式。</span><span class="sxs-lookup"><span data-stu-id="97b94-111">In order for EXPLICIT mode to produce the XML document, the rowset must have a specific format.</span></span> <span data-ttu-id="97b94-112">这需要您编写 SELECT 查询以生成具有特定格式的行集（通用表 ），以便处理逻辑随后可以生成所需的 XML。</span><span class="sxs-lookup"><span data-stu-id="97b94-112">This requires that you write the SELECT query to produce the rowset, the **universal table**, with a specific format so the processing logic can then produce the XML you want.</span></span>  
  
 <span data-ttu-id="97b94-113">首先，查询必须生成下列两个元数据列：</span><span class="sxs-lookup"><span data-stu-id="97b94-113">First, the query must produce the following two metadata columns:</span></span>  
  
-   <span data-ttu-id="97b94-114">第一列必须提供当前元素的标记号（整数类型），并且列名必须是 **Tag**。</span><span class="sxs-lookup"><span data-stu-id="97b94-114">The first column must provide the tag number, integer type, of the current element, and the column name must be **Tag**.</span></span> <span data-ttu-id="97b94-115">查询必须为从行集构造的每个元素提供唯一标记号。</span><span class="sxs-lookup"><span data-stu-id="97b94-115">Your query must provide a unique tag number for each element that will be constructed from the rowset.</span></span>  
  
-   <span data-ttu-id="97b94-116">第二列必须提供父元素的标记号，并且此列的列名必须是 **Parent**。</span><span class="sxs-lookup"><span data-stu-id="97b94-116">The second column must provide a tag number of the parent element, and this column name must be **Parent**.</span></span> <span data-ttu-id="97b94-117">这样，Tag 和 Parent 列将提供层次结构信息。</span><span class="sxs-lookup"><span data-stu-id="97b94-117">In this way, the Tag and the Parent column provide hierarchy information.</span></span>  
  
 <span data-ttu-id="97b94-118">这些元数据列值与列名中的信息一起都用于生成所需的 XML。</span><span class="sxs-lookup"><span data-stu-id="97b94-118">These metadata column values, together with the information in the column names, are used to produce the XML you want.</span></span> <span data-ttu-id="97b94-119">请注意，查询必须以特定的方式提供列名。</span><span class="sxs-lookup"><span data-stu-id="97b94-119">Note that your query must provide column names in a specific way.</span></span> <span data-ttu-id="97b94-120">同时请注意， **Parent** 列中的 0 或 NULL 表明相应的元素没有父级。</span><span class="sxs-lookup"><span data-stu-id="97b94-120">Also note that a 0 or NULL in the **Parent** column indicates that the corresponding element has no parent.</span></span> <span data-ttu-id="97b94-121">该元素将作为顶级元素添加到 XML。</span><span class="sxs-lookup"><span data-stu-id="97b94-121">The element is added to the XML as a top-level element.</span></span>  
  
 <span data-ttu-id="97b94-122">为了了解如何将查询生成的通用表处理为生成 XML 结果，假定您已经编写了一个生成此通用表的查询：</span><span class="sxs-lookup"><span data-stu-id="97b94-122">To understand how the universal table generated by a query is processed into generating XML result, assume that you have written a query that produces this universal table:</span></span>  
  
 <span data-ttu-id="97b94-123">![通用表示例](../../database-engine/media/xmlutable.gif "通用表示例")</span><span class="sxs-lookup"><span data-stu-id="97b94-123">![Sample universal table](../../database-engine/media/xmlutable.gif "Sample universal table")</span></span>  
  
 <span data-ttu-id="97b94-124">注意有关此通用表的以下事项：</span><span class="sxs-lookup"><span data-stu-id="97b94-124">Note the following about this universal table:</span></span>  
  
-   <span data-ttu-id="97b94-125">前两列是 **Tag** 和 **Parent** ，它们是元数据列。</span><span class="sxs-lookup"><span data-stu-id="97b94-125">The first two columns are **Tag** and **Parent** and are meta columns.</span></span> <span data-ttu-id="97b94-126">这些值确定层次结构。</span><span class="sxs-lookup"><span data-stu-id="97b94-126">These values determine the hierarchy.</span></span>  
  
-   <span data-ttu-id="97b94-127">列名是以特定的方式指定的，本主题的后面部分将进行介绍。</span><span class="sxs-lookup"><span data-stu-id="97b94-127">The column names are specified in a certain way, as described later in this topic.</span></span>  
  
-   <span data-ttu-id="97b94-128">从此通用表生成 XML 的过程中，此表中的数据被垂直分区到列组中。</span><span class="sxs-lookup"><span data-stu-id="97b94-128">In generating the XML from this universal table, the data in this table is partitioned vertically into column groups.</span></span> <span data-ttu-id="97b94-129">分组是根据 **Tag** 值和列名确定的。</span><span class="sxs-lookup"><span data-stu-id="97b94-129">The grouping is determined based on the **Tag** value and the column names.</span></span> <span data-ttu-id="97b94-130">在构造 XML 的过程中，处理逻辑为每行选择一组列，然后构造一个元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-130">In constructing XML, the processing logic selects one group of columns for each row and constructs an element.</span></span> <span data-ttu-id="97b94-131">在此示例中，将应用以下规则：</span><span class="sxs-lookup"><span data-stu-id="97b94-131">The following applies in this example:</span></span>  
  
    -   <span data-ttu-id="97b94-132">对于第一行中的 **Tag** 列值 1，名称中包括此相同标记号的列（ **Customer!1!cid** 和 **Customer!1!name**）形成一组。</span><span class="sxs-lookup"><span data-stu-id="97b94-132">For **Tag** column value 1 in the first row, the columns whose names include the same tag number, **Customer!1!cid** and **Customer!1!name**, form a group.</span></span> <span data-ttu-id="97b94-133">这些列用于处理行，您可能已经注意到所生成元素的形式为 <`Customer id=... name=...`>。</span><span class="sxs-lookup"><span data-stu-id="97b94-133">These columns are used in processing the row, and you may have noticed that the shape of the generated element is <`Customer id=... name=...`>.</span></span> <span data-ttu-id="97b94-134">列名格式在本主题的后面部分进行介绍。</span><span class="sxs-lookup"><span data-stu-id="97b94-134">Column name format is described later in this topic.</span></span>  
  
    -   <span data-ttu-id="97b94-135">对于 **Tag** 列值为 2 的行，列 **Order!2!id** 和 **Order!2!date** 形成一组，然后该组用于构造元素（形式为 <`Order id=... date=... /`>）。</span><span class="sxs-lookup"><span data-stu-id="97b94-135">For rows with **Tag** column value 2, columns **Order!2!id** and **Order!2!date** form a group that is then used in constructing elements, <`Order id=... date=... /`>.</span></span>  
  
    -   <span data-ttu-id="97b94-136">对于 **Tag** 列值为 3 的行，列 **OrderDetail!3!id!id** 和 **OrderDetail!3!pid!idref** 形成一组。</span><span class="sxs-lookup"><span data-stu-id="97b94-136">For rows with **Tag** column value 3, columns **OrderDetail!3!id!id** and **OrderDetail!3!pid!idref** form a group.</span></span> <span data-ttu-id="97b94-137">其中每一行都从这些列生成一个元素（形式为 <`OrderDetail id=... pid=...`>）。</span><span class="sxs-lookup"><span data-stu-id="97b94-137">Each of these rows generates an element, <`OrderDetail id=... pid=...`>, from these columns.</span></span>  
  
-   <span data-ttu-id="97b94-138">请注意，在生成 XML 层次结构的过程中，行是按顺序处理的。</span><span class="sxs-lookup"><span data-stu-id="97b94-138">Note that in generating XML hierarchy, the rows are processed in order.</span></span> <span data-ttu-id="97b94-139">XML 层次结构确定如下：</span><span class="sxs-lookup"><span data-stu-id="97b94-139">The XML hierarchy is determined as shown in the following:</span></span>  
  
    -   <span data-ttu-id="97b94-140">第一行指定 **Tag** 值为 1， **Parent** 值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="97b94-140">The first row specifies **Tag** value 1 and **Parent** value NULL.</span></span> <span data-ttu-id="97b94-141">因此，相应的元素（即 <`Customer`> 元素）将作为顶级元素添加在 XML 中。</span><span class="sxs-lookup"><span data-stu-id="97b94-141">Therefore, the corresponding element, <`Customer`> element, is added as a top-level element in the XML.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
        ```  
  
    -   <span data-ttu-id="97b94-142">第二行指定 **Tag** 值为 2， **Parent** 值为 1。</span><span class="sxs-lookup"><span data-stu-id="97b94-142">The second row identifies **Tag** value 2 and **Parent** value 1.</span></span> <span data-ttu-id="97b94-143">因此，将添加 <`Order`> 元素作为 <`Customer`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-143">Therefore, the element, <`Order`> element, is added as a child of the <`Customer`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
        ```  
  
    -   <span data-ttu-id="97b94-144">接下来的两行指定 **Tag** 值为 3， **Parent** 值为 2。</span><span class="sxs-lookup"><span data-stu-id="97b94-144">The next two rows identify **Tag** value 3 and **Parent** value 2.</span></span> <span data-ttu-id="97b94-145">因此，将添加两个 <`OrderDetail`> 元素作为 <`Order`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-145">Therefore, the two elements, <`OrderDetail`> elements, are added as children of the <`Order`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
        ```  
  
    -   <span data-ttu-id="97b94-146">最后一行确定 **Tag** 号为 2， **Parent** 标记号为 1。</span><span class="sxs-lookup"><span data-stu-id="97b94-146">The last row identifies 2 as the **Tag** number and 1 as the **Parent** tag number.</span></span> <span data-ttu-id="97b94-147">因此，另一个 <`Order`> 元素将作为 <`Customer`> 父元素的子元素添加。</span><span class="sxs-lookup"><span data-stu-id="97b94-147">Therefore, another <`Order`> element child is added to the <`Customer`> parent element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
           </Order>  
           <Order id="O2" date="3/29/1997">  
        </Customer>  
        ```  
  
 <span data-ttu-id="97b94-148">简言之，使用 EXPLICIT 模式时， **Tag** 和 **Parent** 元数据列中的值、列名中提供的信息以及正确的行顺序将生成所需的 XML。</span><span class="sxs-lookup"><span data-stu-id="97b94-148">To summarize, the values in the **Tag** and **Parent** meta columns, the information provided in the column names, and the correct ordering of the rows produce the XML you want when you use EXPLICIT mode.</span></span>  
  
### <a name="universal-table-row-ordering"></a><span data-ttu-id="97b94-149">通用表行顺序</span><span class="sxs-lookup"><span data-stu-id="97b94-149">Universal Table Row Ordering</span></span>  
 <span data-ttu-id="97b94-150">在构造 XML 过程中，通用表中的行是按顺序处理的。</span><span class="sxs-lookup"><span data-stu-id="97b94-150">In constructing the XML, the rows in the universal table are processed in order.</span></span> <span data-ttu-id="97b94-151">因此，若要检索到与其父级关联的正确的子级实例，必须对行集中的行进行排序，以便每个父节点后紧跟着其子节点。</span><span class="sxs-lookup"><span data-stu-id="97b94-151">Therefore, to retrieve the correct children instances associated with their parent, the rows in the rowset must be ordered so that each parent node is immediately followed by its children.</span></span>  
  
## <a name="specifying-column-names-in-a-universal-table"></a><span data-ttu-id="97b94-152">指定通用表中的列名</span><span class="sxs-lookup"><span data-stu-id="97b94-152">Specifying Column Names in a Universal Table</span></span>  
 <span data-ttu-id="97b94-153">在编写 EXPLICIT 模式查询时，必须使用以下格式指定所得到的行集中的列名。</span><span class="sxs-lookup"><span data-stu-id="97b94-153">When writing EXPLICIT mode queries, column names in the resulting rowset must be specified by using this format.</span></span> <span data-ttu-id="97b94-154">它们提供转换信息（包括元素名称和属性名称）以及用指令指定的其他附加信息。</span><span class="sxs-lookup"><span data-stu-id="97b94-154">They provide transformation information including element and attribute names and other additional information, specified by using directives.</span></span>  
  
 <span data-ttu-id="97b94-155">常用格式如下：</span><span class="sxs-lookup"><span data-stu-id="97b94-155">This is the general format:</span></span>  
  
```  
  
ElementName!TagNumber!AttributeName!Directive  
```  
  
 <span data-ttu-id="97b94-156">下面是对格式各部分的说明。</span><span class="sxs-lookup"><span data-stu-id="97b94-156">Following is the description of the parts of the format.</span></span>  
  
 <span data-ttu-id="97b94-157">*ElementName*</span><span class="sxs-lookup"><span data-stu-id="97b94-157">*ElementName*</span></span>  
 <span data-ttu-id="97b94-158">是所生成元素的通用标识符。</span><span class="sxs-lookup"><span data-stu-id="97b94-158">Is the resulting generic identifier of the element.</span></span> <span data-ttu-id="97b94-159">例如，如果将 Customers 指定为 ElementName，将生成 \<Customers> 元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-159">For example, if **Customers** is specified as *ElementName*, the \<Customers> element is generated.</span></span>  
  
 <span data-ttu-id="97b94-160">*TagNumber*</span><span class="sxs-lookup"><span data-stu-id="97b94-160">*TagNumber*</span></span>  
 <span data-ttu-id="97b94-161">是分配给元素的唯一标记值。</span><span class="sxs-lookup"><span data-stu-id="97b94-161">Is a unique tag value assigned to an element.</span></span> <span data-ttu-id="97b94-162">在两个元数据列（ **Tag** 和 **Parent**）的帮助下，此值将确定所得到的 XML 中的元素的嵌套。</span><span class="sxs-lookup"><span data-stu-id="97b94-162">This value, with the help of the two metadata columns, **Tag** and **Parent**, determines the nesting of the elements in the resulting XML.</span></span>  
  
 <span data-ttu-id="97b94-163">*AttributeName*</span><span class="sxs-lookup"><span data-stu-id="97b94-163">*AttributeName*</span></span>  
 <span data-ttu-id="97b94-164">提供要在指定的 *ElementName*中构造的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="97b94-164">Provides the name of the attribute to construct in the specified *ElementName*.</span></span> <span data-ttu-id="97b94-165">如果没有指定 *Directive* ，将发生这种行为。</span><span class="sxs-lookup"><span data-stu-id="97b94-165">This is the behavior if *Directive* is not specified.</span></span>  
  
 <span data-ttu-id="97b94-166">如果指定了 *Directive* 并且它是 **xml**、 **cdata**或 **element**，则此值用于构造 *ElementName*的子元素，并且此列值将添加到该子元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-166">If *Directive* is specified and it is **xml**, **cdata**, or **element**, this value is used to construct an element child of *ElementName*, and the column value is added to it.</span></span>  
  
 <span data-ttu-id="97b94-167">如果指定了 *Directive*，则 *AttributeName* 可以为空。</span><span class="sxs-lookup"><span data-stu-id="97b94-167">If you specify the *Directive*, the *AttributeName* can be empty.</span></span> <span data-ttu-id="97b94-168">例如 ElementName!TagNumber!!Directive。</span><span class="sxs-lookup"><span data-stu-id="97b94-168">For example, ElementName!TagNumber!!Directive.</span></span> <span data-ttu-id="97b94-169">在这种情况下，列值直接由 *ElementName*包含。</span><span class="sxs-lookup"><span data-stu-id="97b94-169">In this case, the column value is directly contained by the *ElementName*.</span></span>  
  
 <span data-ttu-id="97b94-170">*Directive*</span><span class="sxs-lookup"><span data-stu-id="97b94-170">*Directive*</span></span>  
 <span data-ttu-id="97b94-171">*Directive* 是可选的，可以使用它来提供有关 XML 构造的其他信息。</span><span class="sxs-lookup"><span data-stu-id="97b94-171">*Directive* is optional and you can use it to provide additional information for construction of the XML.</span></span> <span data-ttu-id="97b94-172">*Directive* 有两种用途。</span><span class="sxs-lookup"><span data-stu-id="97b94-172">*Directive* has two purposes.</span></span>  
  
 <span data-ttu-id="97b94-173">一种用途是将值编码为 ID、IDREF 和 IDREFS。</span><span class="sxs-lookup"><span data-stu-id="97b94-173">One of the purposes is to encode values as ID, IDREF, and IDREFS.</span></span> <span data-ttu-id="97b94-174">可以将 **ID**、 **IDREF**和 **IDREFS** 关键字指定为 *Directives*。</span><span class="sxs-lookup"><span data-stu-id="97b94-174">You can specify **ID**, **IDREF**, and **IDREFS** keywords as *Directives*.</span></span> <span data-ttu-id="97b94-175">这些指令将覆盖属性类型。</span><span class="sxs-lookup"><span data-stu-id="97b94-175">These directives overwrite the attribute types.</span></span> <span data-ttu-id="97b94-176">这使您能够创建文档内链接。</span><span class="sxs-lookup"><span data-stu-id="97b94-176">This allows you to create intra-document links.</span></span>  
  
 <span data-ttu-id="97b94-177">同时，可以使用 *Directive* 来指示如何将字符串数据映射到 XML。</span><span class="sxs-lookup"><span data-stu-id="97b94-177">Also, you can use *Directive* to indicate how to map the string data to XML.</span></span> <span data-ttu-id="97b94-178">可以将 **hide**、 **element、elementxsinil**、 **xml**、 **xmltext**和 **cdata** 关键字用作 *Directive*。</span><span class="sxs-lookup"><span data-stu-id="97b94-178">The **hide**, **element, elementxsinil**, **xml**, **xmltext**, and **cdata** keywords can be used as the *Directive*.</span></span> <span data-ttu-id="97b94-179">**hide** 指令会隐藏节点。</span><span class="sxs-lookup"><span data-stu-id="97b94-179">The **hide** directive hides the node.</span></span> <span data-ttu-id="97b94-180">当仅为排序目的而检索值，但又不想让它们出现在所得到的 XML 中时，此指令非常有用。</span><span class="sxs-lookup"><span data-stu-id="97b94-180">This is useful when you retrieve values only for sorting purposes, but you do not want them in the resulting XML.</span></span>  
  
 <span data-ttu-id="97b94-181">**element** 指令生成的结果中包含元素而不是属性。</span><span class="sxs-lookup"><span data-stu-id="97b94-181">The **element** directive generates a contained element instead of an attribute.</span></span> <span data-ttu-id="97b94-182">包含的数据被编码为实体。</span><span class="sxs-lookup"><span data-stu-id="97b94-182">The contained data is encoded as an entity.</span></span> <span data-ttu-id="97b94-183">例如， **<** 字符变成 &lt;。</span><span class="sxs-lookup"><span data-stu-id="97b94-183">For example, the **<** character becomes &lt;.</span></span> <span data-ttu-id="97b94-184">对于 NULL 列值，不会生成任何元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-184">For NULL column values, no element is generated.</span></span> <span data-ttu-id="97b94-185">如果要为 NULL 列值生成元素，可以指定 **elementxsinil** 指令。</span><span class="sxs-lookup"><span data-stu-id="97b94-185">If you want an element generated for null column values, you can specify the **elementxsinil** directive.</span></span> <span data-ttu-id="97b94-186">这将生成具有属性 xsi:nil=TRUE 的元素。</span><span class="sxs-lookup"><span data-stu-id="97b94-186">This will generate an element that has the attribute xsi:nil=TRUE.</span></span>  
  
 <span data-ttu-id="97b94-187">除不发生实体编码外， **xml** 指令与 **element** 指令相同。</span><span class="sxs-lookup"><span data-stu-id="97b94-187">The **xml** directive is the same as an **element** directive, except that no entity encoding occurs.</span></span> <span data-ttu-id="97b94-188">请注意，可以将 **element** 指令与 **ID**、 **IDREF**或 **IDREFS**结合使用，然而不允许 **xml** 指令与除 **hide**指令之外的任何其他指令结合使用。</span><span class="sxs-lookup"><span data-stu-id="97b94-188">Note that the **element** directive can be combined with **ID**, **IDREF**, or **IDREFS**, whereas the **xml** directive is not allowed with any other directive, except **hide**.</span></span>  
  
 <span data-ttu-id="97b94-189">**cdata** 指令通过将数据与 CDATA 部分包装在一起来包含数据。</span><span class="sxs-lookup"><span data-stu-id="97b94-189">The **cdata** directive contains the data by wrapping it with a CDATA section.</span></span> <span data-ttu-id="97b94-190">不对内容进行实体编码。</span><span class="sxs-lookup"><span data-stu-id="97b94-190">The content is not entity encoded.</span></span> <span data-ttu-id="97b94-191">原始数据类型必须是文本类型（如 **varchar**、 **nvarchar**、 **text**或 **ntext**）。</span><span class="sxs-lookup"><span data-stu-id="97b94-191">The original data type must be a text type such as **varchar**, **nvarchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="97b94-192">此指令只适用于 **hide**。</span><span class="sxs-lookup"><span data-stu-id="97b94-192">This directive can be used only with **hide**.</span></span> <span data-ttu-id="97b94-193">当使用此指令时，不能指定 *AttributeName* 。</span><span class="sxs-lookup"><span data-stu-id="97b94-193">When this directive is used, *AttributeName* must not be specified.</span></span>  
  
 <span data-ttu-id="97b94-194">大多数情况下，允许在这两个组之间组合指令，但不允许在它们自身当中组合指令。</span><span class="sxs-lookup"><span data-stu-id="97b94-194">Combining directives between these two groups is allowed in most cases, but combining them among themselves is not allowed.</span></span>  
  
 <span data-ttu-id="97b94-195">如果未指定 *Directive* 和 *AttributeName* （例如 **Customer!1**），则暗含一个 **element** 指令（如 **Customer!1!!element**），并且列数据包含在 *ElementName*中。</span><span class="sxs-lookup"><span data-stu-id="97b94-195">If the *Directive* and the *AttributeName* is not specified, for example, **Customer!1**, an **element** directive is implied, such as **Customer!1!!element**, and column data is contained in the *ElementName*.</span></span>  
  
 <span data-ttu-id="97b94-196">如果指定了 **xmltext** 指令，则列内容包装在与文档的其余部分集成在一起的单个标记中。</span><span class="sxs-lookup"><span data-stu-id="97b94-196">If the **xmltext** directive is specified, the column content is wrapped in a single tag that is integrated with the rest of the document.</span></span> <span data-ttu-id="97b94-197">在提取由 OPENXML 存储在列中的溢出（未用完的）XML 数据时，此指令很有用。</span><span class="sxs-lookup"><span data-stu-id="97b94-197">This directive is useful in fetching overflow, unconsumed, XML data stored in a column by OPENXML.</span></span> <span data-ttu-id="97b94-198">有关详细信息，请参阅 [OPENXML (SQL Server)](../xml/openxml-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97b94-198">For more information, see [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md).</span></span>  
  
 <span data-ttu-id="97b94-199">如果指定了 *AttributeName* ，将由指定的名称替换标记名。</span><span class="sxs-lookup"><span data-stu-id="97b94-199">If *AttributeName* is specified, the tag name is replaced by the specified name.</span></span> <span data-ttu-id="97b94-200">否则，将通过把内容置于包容的起始位置（不经过实体编码）将属性追加到闭合元素属性的当前列表中。</span><span class="sxs-lookup"><span data-stu-id="97b94-200">Otherwise, the attribute is appended to the current list of attributes of the enclosing elements by putting the content at the beginning of the containment without entity encoding.</span></span> <span data-ttu-id="97b94-201">包含此指令的列必须是文本类型（如 **varchar**、 **nvarchar**、 **char**、 **nchar**、 **text**或 **ntext**）。</span><span class="sxs-lookup"><span data-stu-id="97b94-201">The column with this directive must be a text type, such as **varchar**, **nvarchar**, **char**, **nchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="97b94-202">此指令只适用于 **hide**。</span><span class="sxs-lookup"><span data-stu-id="97b94-202">This directive can be used only with **hide**.</span></span> <span data-ttu-id="97b94-203">在提取列中存储的溢出数据时，此指令很有用。</span><span class="sxs-lookup"><span data-stu-id="97b94-203">This directive is useful in fetching overflow data stored in a column.</span></span> <span data-ttu-id="97b94-204">如果内容的 XML 格式不正确，则未定义该行为。</span><span class="sxs-lookup"><span data-stu-id="97b94-204">If the content is not a well-formed XML, the behavior is undefined.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97b94-205">本节内容</span><span class="sxs-lookup"><span data-stu-id="97b94-205">In This Section</span></span>  
 <span data-ttu-id="97b94-206">下列示例说明了 EXPLICIT 模式的用法。</span><span class="sxs-lookup"><span data-stu-id="97b94-206">The following examples illustrate the use of EXPLICIT mode.</span></span>  
  
-   [<span data-ttu-id="97b94-207">示例：检索员工信息</span><span class="sxs-lookup"><span data-stu-id="97b94-207">Example: Retrieving Employee Information</span></span>](../xml/example-retrieving-employee-information.md)  
  
-   [<span data-ttu-id="97b94-208">示例：指定 ELEMENT 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-208">Example: Specifying the ELEMENT Directive</span></span>](../xml/example-specifying-the-element-directive.md)  
  
-   [<span data-ttu-id="97b94-209">示例：指定 ELEMENTXSINIL 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-209">Example: Specifying the ELEMENTXSINIL Directive</span></span>](../xml/example-specifying-the-elementxsinil-directive.md)  
  
-   [<span data-ttu-id="97b94-210">示例：使用 EXPLICIT 模式构造同级</span><span class="sxs-lookup"><span data-stu-id="97b94-210">Example: Constructing Siblings with EXPLICIT Mode</span></span>](../xml/example-constructing-siblings-with-explicit-mode.md)  
  
-   [<span data-ttu-id="97b94-211">示例：指定 ID 和 IDREF 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-211">Example: Specifying the ID and IDREF Directives</span></span>](../xml/example-specifying-the-id-and-idref-directives.md)  
  
-   [<span data-ttu-id="97b94-212">示例：指定 ID 和 IDREFS 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-212">Example: Specifying the ID and IDREFS Directives</span></span>](../xml/example-specifying-the-id-and-idrefs-directives.md)  
  
-   [<span data-ttu-id="97b94-213">示例：指定 HIDE 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-213">Example: Specifying the HIDE Directive</span></span>](../xml/example-specifying-the-hide-directive.md)  
  
-   [<span data-ttu-id="97b94-214">示例：指定 ELEMENT 指令和实体编码</span><span class="sxs-lookup"><span data-stu-id="97b94-214">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>](../xml/example-specifying-the-element-directive-and-entity-encoding.md)  
  
-   [<span data-ttu-id="97b94-215">示例：指定 CDATA 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-215">Example: Specifying the CDATA Directive</span></span>](../xml/example-specifying-the-cdata-directive.md)  
  
-   [<span data-ttu-id="97b94-216">示例：指定 XMLTEXT 指令</span><span class="sxs-lookup"><span data-stu-id="97b94-216">Example: Specifying the XMLTEXT Directive</span></span>](../xml/example-specifying-the-xmltext-directive.md)  
  
## <a name="see-also"></a><span data-ttu-id="97b94-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97b94-217">See Also</span></span>  
 <span data-ttu-id="97b94-218">[将 RAW 模式与 FOR XML 一起使用](../xml/use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="97b94-218">[Use RAW Mode with FOR XML](../xml/use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="97b94-219">[将 AUTO 模式与 FOR XML 一起使用](../xml/use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="97b94-219">[Use AUTO Mode with FOR XML](../xml/use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="97b94-220">[将 PATH 模式与 FOR XML 一起使用](../xml/use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="97b94-220">[Use PATH Mode with FOR XML](../xml/use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="97b94-221">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97b94-221">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="97b94-222">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97b94-222">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
