---
title: 用于 XML 报表数据的元素路径语法 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ElementPath syntax
- XML [Reporting Services], data retrieval
ms.assetid: 07bd7a4e-fd7a-4a72-9344-3258f7c286d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d66b39761dc278abff25a3b22ccd18ca74272b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694278"
---
# <a name="element-path-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="66e1a-102">用于 XML 报表数据的元素路径语法 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="66e1a-102">Element Path Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="66e1a-103">在报表设计器中，可以通过定义元素路径（区分大小写）来指定 XML 数据源中要用于报表的数据。</span><span class="sxs-lookup"><span data-stu-id="66e1a-103">In Report Designer, you specify the data to use for a report from an XML data source by defining a case-sensitive element path.</span></span> <span data-ttu-id="66e1a-104">元素路径指示如何遍历 XML 数据源中的 XML 层次结构节点及其属性。</span><span class="sxs-lookup"><span data-stu-id="66e1a-104">An element path indicates how to traverse the XML hierarchical nodes and their attributes in the XML data source.</span></span> <span data-ttu-id="66e1a-105">若要使用默认元素路径，请将数据集查询或 XML `ElementPath` 的 XML `Query` 保留为空。</span><span class="sxs-lookup"><span data-stu-id="66e1a-105">To use the default element path, leave the dataset query or the XML `ElementPath` of the XML `Query` empty.</span></span> <span data-ttu-id="66e1a-106">从 XML 数据源检索数据时，具有文本值的元素节点和元素节点属性将成为结果集中的列。</span><span class="sxs-lookup"><span data-stu-id="66e1a-106">When data is retrieved from the XML data source, element nodes that have text values and element node attributes become columns in the result set.</span></span> <span data-ttu-id="66e1a-107">运行查询时，节点值和属性将成为行数据。</span><span class="sxs-lookup"><span data-stu-id="66e1a-107">The values of the nodes and attributes become the row data when you run the query.</span></span> <span data-ttu-id="66e1a-108">该列在“报表数据”窗格中显示为数据集字段集合。</span><span class="sxs-lookup"><span data-stu-id="66e1a-108">The columns appear as the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="66e1a-109">本主题介绍元素路径语法。</span><span class="sxs-lookup"><span data-stu-id="66e1a-109">This topic describes the element path syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66e1a-110">元素路径语法与命名空间无关。</span><span class="sxs-lookup"><span data-stu-id="66e1a-110">Element path syntax is namespace-independent.</span></span> <span data-ttu-id="66e1a-111">若要在元素路径中使用命名空间，请使用 xml 查询语法，该语法包括 xml `ElementPath` 查询语法中所述的 xml 元素[&#40;SSRS&#41;的 Xml 报表数据](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66e1a-111">To use namespaces in an element path, use the XML query syntax that includes an XML `ElementPath` element described in [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="66e1a-112">下表介绍用于定义元素路径的约定。</span><span class="sxs-lookup"><span data-stu-id="66e1a-112">The following table describes conventions used to define an element path.</span></span>  
  
|<span data-ttu-id="66e1a-113">约定</span><span class="sxs-lookup"><span data-stu-id="66e1a-113">Convention</span></span>|<span data-ttu-id="66e1a-114">用于</span><span class="sxs-lookup"><span data-stu-id="66e1a-114">Used for</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="66e1a-115">**粗体**</span><span class="sxs-lookup"><span data-stu-id="66e1a-115">**bold**</span></span>|<span data-ttu-id="66e1a-116">必须完全按原样键入的文本。</span><span class="sxs-lookup"><span data-stu-id="66e1a-116">Text that must be typed exactly as shown.</span></span>|  
|<span data-ttu-id="66e1a-117">&#124; （垂直条）</span><span class="sxs-lookup"><span data-stu-id="66e1a-117">&#124; (vertical bar)</span></span>|<span data-ttu-id="66e1a-118">分隔语法项。</span><span class="sxs-lookup"><span data-stu-id="66e1a-118">Separates syntax items.</span></span> <span data-ttu-id="66e1a-119">只能选择其中一项。</span><span class="sxs-lookup"><span data-stu-id="66e1a-119">You can choose only one of the items.</span></span>|  
|`[ ] (brackets)`|<span data-ttu-id="66e1a-120">可选语法项。</span><span class="sxs-lookup"><span data-stu-id="66e1a-120">Optional syntax items.</span></span> <span data-ttu-id="66e1a-121">不要键入方括号。</span><span class="sxs-lookup"><span data-stu-id="66e1a-121">Do not type the brackets.</span></span>|  
|<span data-ttu-id="66e1a-122">**{}** (大括号) </span><span class="sxs-lookup"><span data-stu-id="66e1a-122">**{ }** (braces)</span></span>|<span data-ttu-id="66e1a-123">分隔语法项的参数。</span><span class="sxs-lookup"><span data-stu-id="66e1a-123">Delimits parameters of syntax items.</span></span>|  
|<span data-ttu-id="66e1a-124">[  ...*n*]</span><span class="sxs-lookup"><span data-stu-id="66e1a-124">[**,**...*n*]</span></span>|<span data-ttu-id="66e1a-125">指示前面的项可以重复 *n* 次。</span><span class="sxs-lookup"><span data-stu-id="66e1a-125">Indicates the preceding item can be repeated *n* number of times.</span></span> <span data-ttu-id="66e1a-126">匹配项由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="66e1a-126">The occurrences are separated by commas.</span></span>|  
  
## <a name="syntax"></a><span data-ttu-id="66e1a-127">语法</span><span class="sxs-lookup"><span data-stu-id="66e1a-127">Syntax</span></span>  
  
```  
  
Element path ::=  
    ElementNode[/Element path]  
ElementNode ::=  
    XMLName[(Encoding)][{[FieldList]}]  
XMLName ::=  
    [NamespacePrefix:]XMLLocalName  
Encoding ::=  
        HTMLEncoded | Base64Encoded  
FieldList ::=  
    Field[,FieldList]  
Field ::=  
    Attribute | Value | Element | ElementNode  
Attribute ::=  
        @XMLName[(Type)]  
Value ::=  
        @[(Type)]  
Element ::=  
    XMLName[(Type)]  
Type ::=  
        String | Integer | Boolean | Float | Decimal | Date | XML   
NamespacePrefix ::=  
    Identifier that specifies the namespace.  
XMLLocalName :: =  
    Identifier in the XML tag.   
```  
  
## <a name="remarks"></a><span data-ttu-id="66e1a-128">备注</span><span class="sxs-lookup"><span data-stu-id="66e1a-128">Remarks</span></span>  
 <span data-ttu-id="66e1a-129">下表总结了元素路径字词。</span><span class="sxs-lookup"><span data-stu-id="66e1a-129">The following table summarizes element path terms.</span></span> <span data-ttu-id="66e1a-130">该表中的示例引用示例 XML 文档 Customers.xml，该文档包含于本主题的“示例”部分中。</span><span class="sxs-lookup"><span data-stu-id="66e1a-130">Examples in the table refer to the example XML document Customers.xml, which is included in the Examples section of this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66e1a-131">XML 标记区分大小写。</span><span class="sxs-lookup"><span data-stu-id="66e1a-131">XML tags are case-sensitive.</span></span> <span data-ttu-id="66e1a-132">在元素路径中指定 ElementNode 时，必须完全匹配数据源中的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="66e1a-132">When you specify an ElementNode in the element path, you must exactly match the XML tags in the data source.</span></span>  
  
|<span data-ttu-id="66e1a-133">术语</span><span class="sxs-lookup"><span data-stu-id="66e1a-133">Term</span></span>|<span data-ttu-id="66e1a-134">定义</span><span class="sxs-lookup"><span data-stu-id="66e1a-134">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="66e1a-135">Element path</span><span class="sxs-lookup"><span data-stu-id="66e1a-135">Element path</span></span>|<span data-ttu-id="66e1a-136">定义为了使用 XML 数据源检索数据集的字段数据而要在 XML 文档中遍历的节点序列。</span><span class="sxs-lookup"><span data-stu-id="66e1a-136">Defines the sequence of nodes to traverse within the XML document in order to retrieve field data for a dataset with an XML data source.</span></span>|  
|`ElementNode`|<span data-ttu-id="66e1a-137">XML 文档中的 XML 节点。</span><span class="sxs-lookup"><span data-stu-id="66e1a-137">The XML node in the XML document.</span></span> <span data-ttu-id="66e1a-138">节点由标记指定，并与其他节点之间存在层次结构关系。</span><span class="sxs-lookup"><span data-stu-id="66e1a-138">Nodes are designated by tags and exist in a hierarchical relationship with other nodes.</span></span> <span data-ttu-id="66e1a-139">例如， \<Customers> 是根元素节点。</span><span class="sxs-lookup"><span data-stu-id="66e1a-139">For example, \<Customers> is the root element node.</span></span> <span data-ttu-id="66e1a-140">\<Customer>是的一个子元素 \<Customers> 。</span><span class="sxs-lookup"><span data-stu-id="66e1a-140">\<Customer> is a subelement of \<Customers>.</span></span>|  
|`XMLName`|<span data-ttu-id="66e1a-141">节点的名称。</span><span class="sxs-lookup"><span data-stu-id="66e1a-141">The name of the node.</span></span> <span data-ttu-id="66e1a-142">例如，Customers 节点的名称为 Customers。</span><span class="sxs-lookup"><span data-stu-id="66e1a-142">For example, the name of the Customers node is Customers.</span></span> <span data-ttu-id="66e1a-143">`XMLName` 可以使用命名空间标识符作为前缀，以唯一命名每个节点。</span><span class="sxs-lookup"><span data-stu-id="66e1a-143">An `XMLName` can be prefixed with a namespace identifier to uniquely name every node.</span></span>|  
|`Encoding`|<span data-ttu-id="66e1a-144">指示此元素的 `Value` 是编码的 XML，它需要解码并作为此元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="66e1a-144">Indicates that the `Value` for this element is encoded XML and needs to be decoded and included as a subelement of this element.</span></span>|  
|`FieldList`|<span data-ttu-id="66e1a-145">定义要用于检索数据的元素和属性集。</span><span class="sxs-lookup"><span data-stu-id="66e1a-145">Defines the set of elements and attributes to use to retrieve data.</span></span><br /><br /> <span data-ttu-id="66e1a-146">如果未指定，则所有属性和子元素都将用作字段。</span><span class="sxs-lookup"><span data-stu-id="66e1a-146">If not specified, all attributes and subelements are used as fields.</span></span> <span data-ttu-id="66e1a-147">如果 () 指定了空字段列表 **{}** ，则不会使用此节点中的任何字段。</span><span class="sxs-lookup"><span data-stu-id="66e1a-147">If the empty field list is specified (**{}**), no fields from this node are used.</span></span><br /><br /> <span data-ttu-id="66e1a-148">`FieldList` 不可以同时包含 `Value` 以及 `Element` 或 `ElementNode`。</span><span class="sxs-lookup"><span data-stu-id="66e1a-148">A `FieldList` may not contain both a `Value` and an `Element` or `ElementNode`.</span></span>|  
|`Field`|<span data-ttu-id="66e1a-149">指定作为数据集字段检索的数据。</span><span class="sxs-lookup"><span data-stu-id="66e1a-149">Specifies the data that is retrieved as a dataset field.</span></span>|  
|`Attribute`|<span data-ttu-id="66e1a-150">`ElementNode` 中的“名称-值”对。</span><span class="sxs-lookup"><span data-stu-id="66e1a-150">A name-value pair within the `ElementNode`.</span></span> <span data-ttu-id="66e1a-151">例如，在元素节点中 \<Customer ID="1"> ， `ID` 是一个属性，并 `@ID(Integer)` 在相应的数据字段中将 "1" 作为整数类型返回 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="66e1a-151">For example, in the element node \<Customer ID="1">, `ID` is an attribute and `@ID(Integer)` returns "1" as an integer type in the corresponding data field `ID`.</span></span>|  
|`Value`|<span data-ttu-id="66e1a-152">元素的值。</span><span class="sxs-lookup"><span data-stu-id="66e1a-152">The value of the element.</span></span> <span data-ttu-id="66e1a-153">`Value` 只能在元素路径的最后一个 `ElementNode` 中使用。</span><span class="sxs-lookup"><span data-stu-id="66e1a-153">`Value` can only be used on the last `ElementNode` in the element path.</span></span> <span data-ttu-id="66e1a-154">例如，由于 \<Return> 是一个叶节点，因此如果将其包含在元素路径的末尾，则的值 `Return {@}` 为 `Chair` 。</span><span class="sxs-lookup"><span data-stu-id="66e1a-154">For example, because \<Return> is a leaf node, if you include it at the end of an element path, the value of `Return {@}` is `Chair`.</span></span>|  
|`Element`|<span data-ttu-id="66e1a-155">命名子元素的值。</span><span class="sxs-lookup"><span data-stu-id="66e1a-155">The value of the named subelement.</span></span> <span data-ttu-id="66e1a-156">例如，Customers {}/Customer {}/LastName 仅检索 LastName 元素的值。</span><span class="sxs-lookup"><span data-stu-id="66e1a-156">For example, Customers {}/Customer {}/LastName retrieves values for only the LastName element.</span></span>|  
|`Type`|<span data-ttu-id="66e1a-157">用于从此元素创建的字段的可选数据类型。</span><span class="sxs-lookup"><span data-stu-id="66e1a-157">The optional data type to use for the field created from this element.</span></span>|  
|`NamespacePrefix`|<span data-ttu-id="66e1a-158">`NamespacePrefix` 在 XML 查询元素中定义。</span><span class="sxs-lookup"><span data-stu-id="66e1a-158">`NamespacePrefix` is defined in the XML Query element.</span></span> <span data-ttu-id="66e1a-159">如果不存在 XML 查询元素，则将忽略 XML `ElementPath` 中的命名空间。</span><span class="sxs-lookup"><span data-stu-id="66e1a-159">If no XML Query element exists, namespaces in the XML `ElementPath` are ignored.</span></span> <span data-ttu-id="66e1a-160">如果存在 XML 查询元素，则 XML `ElementPath` 具有可选属性 `IgnoreNamespaces`。</span><span class="sxs-lookup"><span data-stu-id="66e1a-160">If there is an XML Query element, the XML `ElementPath` has an optional attribute `IgnoreNamespaces`.</span></span> <span data-ttu-id="66e1a-161">如果 IgnoreNamespaces 为 `true` ，则 xml 和 xml 文档中的命名空间 `ElementPath` 将被忽略。</span><span class="sxs-lookup"><span data-stu-id="66e1a-161">If IgnoreNamespaces is `true`, namespaces in the XML `ElementPath` and the XML document are ignored.</span></span> <span data-ttu-id="66e1a-162">有关详细信息，请参阅[用于 XML 报表数据的 XML 查询语法 (SSRS)](report-data-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66e1a-162">For more information, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>|  
  
## <a name="example---no-namespaces"></a><span data-ttu-id="66e1a-163">示例 - 无命名空间</span><span class="sxs-lookup"><span data-stu-id="66e1a-163">Example - No Namespaces</span></span>  
 <span data-ttu-id="66e1a-164">以下示例使用 XML 文档 Customers.xml。</span><span class="sxs-lookup"><span data-stu-id="66e1a-164">The following examples use the XML document Customers.xml.</span></span> <span data-ttu-id="66e1a-165">此表以此 XML 文档作为数据源，在此基础上显示了元素路径语法的示例，以及在定义数据集的查询中使用相应元素路径所得到的结果。</span><span class="sxs-lookup"><span data-stu-id="66e1a-165">This table shows examples of element path syntax and the results of using the element path in a query that defines a dataset, based on the XML document as a data source.</span></span>  
  
 <span data-ttu-id="66e1a-166">请注意，当元素路径为空时，查询将使用默认元素路径：指向叶节点集合的第一个路径。</span><span class="sxs-lookup"><span data-stu-id="66e1a-166">Note that when the element path is empty, the query uses the default element path: the first path to a leaf node collection.</span></span> <span data-ttu-id="66e1a-167">在第一个示例中，将元素路径保留为空等效于指定元素路径 /Customers/Customer/Orders/Order。</span><span class="sxs-lookup"><span data-stu-id="66e1a-167">In the first example, leaving the element path empty is equivalent to specifying the element path /Customers/Customer/Orders/Order.</span></span> <span data-ttu-id="66e1a-168">将在结果集中返回沿该路径分布的所有节点值和属性，并且节点名和属性名将显示为数据集字段。</span><span class="sxs-lookup"><span data-stu-id="66e1a-168">All node value and attributes along the path are returned in the result set, and the node names and attributes names appear as dataset fields.</span></span>  
  
-   <span data-ttu-id="66e1a-169">*空*</span><span class="sxs-lookup"><span data-stu-id="66e1a-169">*Empty*</span></span>  
  
    |<span data-ttu-id="66e1a-170">订单</span><span class="sxs-lookup"><span data-stu-id="66e1a-170">Order</span></span>|<span data-ttu-id="66e1a-171">Qty</span><span class="sxs-lookup"><span data-stu-id="66e1a-171">Qty</span></span>|<span data-ttu-id="66e1a-172">ID</span><span class="sxs-lookup"><span data-stu-id="66e1a-172">ID</span></span>|<span data-ttu-id="66e1a-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="66e1a-173">FirstName</span></span>|<span data-ttu-id="66e1a-174">LastName</span><span class="sxs-lookup"><span data-stu-id="66e1a-174">LastName</span></span>|<span data-ttu-id="66e1a-175">Customer.ID</span><span class="sxs-lookup"><span data-stu-id="66e1a-175">Customer.ID</span></span>|<span data-ttu-id="66e1a-176">xmlns</span><span class="sxs-lookup"><span data-stu-id="66e1a-176">xmlns</span></span>|  
    |-----------|---------|--------|---------------|--------------|-----------------|-----------|  
    |<span data-ttu-id="66e1a-177">Chair</span><span class="sxs-lookup"><span data-stu-id="66e1a-177">Chair</span></span>|<span data-ttu-id="66e1a-178">6</span><span class="sxs-lookup"><span data-stu-id="66e1a-178">6</span></span>|<span data-ttu-id="66e1a-179">1</span><span class="sxs-lookup"><span data-stu-id="66e1a-179">1</span></span>|<span data-ttu-id="66e1a-180">Bobby</span><span class="sxs-lookup"><span data-stu-id="66e1a-180">Bobby</span></span>|<span data-ttu-id="66e1a-181">Moore</span><span class="sxs-lookup"><span data-stu-id="66e1a-181">Moore</span></span>|<span data-ttu-id="66e1a-182">11</span><span class="sxs-lookup"><span data-stu-id="66e1a-182">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="66e1a-183">表</span><span class="sxs-lookup"><span data-stu-id="66e1a-183">Table</span></span>|<span data-ttu-id="66e1a-184">1</span><span class="sxs-lookup"><span data-stu-id="66e1a-184">1</span></span>|<span data-ttu-id="66e1a-185">2</span><span class="sxs-lookup"><span data-stu-id="66e1a-185">2</span></span>|<span data-ttu-id="66e1a-186">Bobby</span><span class="sxs-lookup"><span data-stu-id="66e1a-186">Bobby</span></span>|<span data-ttu-id="66e1a-187">Moore</span><span class="sxs-lookup"><span data-stu-id="66e1a-187">Moore</span></span>|<span data-ttu-id="66e1a-188">11</span><span class="sxs-lookup"><span data-stu-id="66e1a-188">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="66e1a-189">Sofa</span><span class="sxs-lookup"><span data-stu-id="66e1a-189">Sofa</span></span>|<span data-ttu-id="66e1a-190">2</span><span class="sxs-lookup"><span data-stu-id="66e1a-190">2</span></span>|<span data-ttu-id="66e1a-191">8</span><span class="sxs-lookup"><span data-stu-id="66e1a-191">8</span></span>|<span data-ttu-id="66e1a-192">Crystal</span><span class="sxs-lookup"><span data-stu-id="66e1a-192">Crystal</span></span>|<span data-ttu-id="66e1a-193">Hu</span><span class="sxs-lookup"><span data-stu-id="66e1a-193">Hu</span></span>|<span data-ttu-id="66e1a-194">20</span><span class="sxs-lookup"><span data-stu-id="66e1a-194">20</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="66e1a-195">EndTables</span><span class="sxs-lookup"><span data-stu-id="66e1a-195">EndTables</span></span>|<span data-ttu-id="66e1a-196">2</span><span class="sxs-lookup"><span data-stu-id="66e1a-196">2</span></span>|<span data-ttu-id="66e1a-197">15</span><span class="sxs-lookup"><span data-stu-id="66e1a-197">15</span></span>|<span data-ttu-id="66e1a-198">Wyatt</span><span class="sxs-lookup"><span data-stu-id="66e1a-198">Wyatt</span></span>|<span data-ttu-id="66e1a-199">Diaz</span><span class="sxs-lookup"><span data-stu-id="66e1a-199">Diaz</span></span>|<span data-ttu-id="66e1a-200">33</span><span class="sxs-lookup"><span data-stu-id="66e1a-200">33</span></span>|http://www.adventure-works.com|  
  
-   `Customers {}/Customer`  
  
    |<span data-ttu-id="66e1a-201">FirstName</span><span class="sxs-lookup"><span data-stu-id="66e1a-201">FirstName</span></span>|<span data-ttu-id="66e1a-202">LastName</span><span class="sxs-lookup"><span data-stu-id="66e1a-202">LastName</span></span>|<span data-ttu-id="66e1a-203">ID</span><span class="sxs-lookup"><span data-stu-id="66e1a-203">ID</span></span>|  
    |---------------|--------------|--------|  
    |<span data-ttu-id="66e1a-204">Bobby</span><span class="sxs-lookup"><span data-stu-id="66e1a-204">Bobby</span></span>|<span data-ttu-id="66e1a-205">Moore</span><span class="sxs-lookup"><span data-stu-id="66e1a-205">Moore</span></span>|<span data-ttu-id="66e1a-206">11</span><span class="sxs-lookup"><span data-stu-id="66e1a-206">11</span></span>|  
    |<span data-ttu-id="66e1a-207">Crystal</span><span class="sxs-lookup"><span data-stu-id="66e1a-207">Crystal</span></span>|<span data-ttu-id="66e1a-208">Hu</span><span class="sxs-lookup"><span data-stu-id="66e1a-208">Hu</span></span>|<span data-ttu-id="66e1a-209">20</span><span class="sxs-lookup"><span data-stu-id="66e1a-209">20</span></span>|  
    |<span data-ttu-id="66e1a-210">Wyatt</span><span class="sxs-lookup"><span data-stu-id="66e1a-210">Wyatt</span></span>|<span data-ttu-id="66e1a-211">Diaz</span><span class="sxs-lookup"><span data-stu-id="66e1a-211">Diaz</span></span>|<span data-ttu-id="66e1a-212">33</span><span class="sxs-lookup"><span data-stu-id="66e1a-212">33</span></span>|  
  
-   `Customers {}/Customer {}/LastName`  
  
    |<span data-ttu-id="66e1a-213">LastName</span><span class="sxs-lookup"><span data-stu-id="66e1a-213">LastName</span></span>|  
    |--------------|  
    |<span data-ttu-id="66e1a-214">Moore</span><span class="sxs-lookup"><span data-stu-id="66e1a-214">Moore</span></span>|  
    |<span data-ttu-id="66e1a-215">Hu</span><span class="sxs-lookup"><span data-stu-id="66e1a-215">Hu</span></span>|  
    |<span data-ttu-id="66e1a-216">Diaz</span><span class="sxs-lookup"><span data-stu-id="66e1a-216">Diaz</span></span>|  
  
-   `Customers {}/Customer {}/Orders/Order {@,@Qty}`  
  
    |<span data-ttu-id="66e1a-217">订单</span><span class="sxs-lookup"><span data-stu-id="66e1a-217">Order</span></span>|<span data-ttu-id="66e1a-218">Qty</span><span class="sxs-lookup"><span data-stu-id="66e1a-218">Qty</span></span>|  
    |-----------|---------|  
    |<span data-ttu-id="66e1a-219">Chair</span><span class="sxs-lookup"><span data-stu-id="66e1a-219">Chair</span></span>|<span data-ttu-id="66e1a-220">6</span><span class="sxs-lookup"><span data-stu-id="66e1a-220">6</span></span>|  
    |<span data-ttu-id="66e1a-221">表</span><span class="sxs-lookup"><span data-stu-id="66e1a-221">Table</span></span>|<span data-ttu-id="66e1a-222">1</span><span class="sxs-lookup"><span data-stu-id="66e1a-222">1</span></span>|  
    |<span data-ttu-id="66e1a-223">Sofa</span><span class="sxs-lookup"><span data-stu-id="66e1a-223">Sofa</span></span>|<span data-ttu-id="66e1a-224">2</span><span class="sxs-lookup"><span data-stu-id="66e1a-224">2</span></span>|  
    |<span data-ttu-id="66e1a-225">EndTables</span><span class="sxs-lookup"><span data-stu-id="66e1a-225">EndTables</span></span>|<span data-ttu-id="66e1a-226">2</span><span class="sxs-lookup"><span data-stu-id="66e1a-226">2</span></span>|  
  
-   `Customers {}/Customer/Orders/Order{ @ID(Integer)}`  
  
    |<span data-ttu-id="66e1a-227">Order.ID</span><span class="sxs-lookup"><span data-stu-id="66e1a-227">Order.ID</span></span>|<span data-ttu-id="66e1a-228">FirstName</span><span class="sxs-lookup"><span data-stu-id="66e1a-228">FirstName</span></span>|<span data-ttu-id="66e1a-229">LastName</span><span class="sxs-lookup"><span data-stu-id="66e1a-229">LastName</span></span>|<span data-ttu-id="66e1a-230">ID</span><span class="sxs-lookup"><span data-stu-id="66e1a-230">ID</span></span>|  
    |--------------|---------------|--------------|--------|  
    |<span data-ttu-id="66e1a-231">1</span><span class="sxs-lookup"><span data-stu-id="66e1a-231">1</span></span>|<span data-ttu-id="66e1a-232">Bobby</span><span class="sxs-lookup"><span data-stu-id="66e1a-232">Bobby</span></span>|<span data-ttu-id="66e1a-233">Moore</span><span class="sxs-lookup"><span data-stu-id="66e1a-233">Moore</span></span>|<span data-ttu-id="66e1a-234">11</span><span class="sxs-lookup"><span data-stu-id="66e1a-234">11</span></span>|  
    |<span data-ttu-id="66e1a-235">2</span><span class="sxs-lookup"><span data-stu-id="66e1a-235">2</span></span>|<span data-ttu-id="66e1a-236">Bobby</span><span class="sxs-lookup"><span data-stu-id="66e1a-236">Bobby</span></span>|<span data-ttu-id="66e1a-237">Moore</span><span class="sxs-lookup"><span data-stu-id="66e1a-237">Moore</span></span>|<span data-ttu-id="66e1a-238">11</span><span class="sxs-lookup"><span data-stu-id="66e1a-238">11</span></span>|  
    |<span data-ttu-id="66e1a-239">8</span><span class="sxs-lookup"><span data-stu-id="66e1a-239">8</span></span>|<span data-ttu-id="66e1a-240">Crystal</span><span class="sxs-lookup"><span data-stu-id="66e1a-240">Crystal</span></span>|<span data-ttu-id="66e1a-241">Hu</span><span class="sxs-lookup"><span data-stu-id="66e1a-241">Hu</span></span>|<span data-ttu-id="66e1a-242">20</span><span class="sxs-lookup"><span data-stu-id="66e1a-242">20</span></span>|  
    |<span data-ttu-id="66e1a-243">15</span><span class="sxs-lookup"><span data-stu-id="66e1a-243">15</span></span>|<span data-ttu-id="66e1a-244">Wyatt</span><span class="sxs-lookup"><span data-stu-id="66e1a-244">Wyatt</span></span>|<span data-ttu-id="66e1a-245">Diaz</span><span class="sxs-lookup"><span data-stu-id="66e1a-245">Diaz</span></span>|<span data-ttu-id="66e1a-246">33</span><span class="sxs-lookup"><span data-stu-id="66e1a-246">33</span></span>|  
  
#### <a name="xml-document-customersxml"></a><span data-ttu-id="66e1a-247">XML 文档：Customers.xml</span><span class="sxs-lookup"><span data-stu-id="66e1a-247">XML document: Customers.xml</span></span>  
 <span data-ttu-id="66e1a-248">若要尝试前一节中的元素路径示例，可以复制此 XML 并将其保存到报表设计器可以访问的 URL，然后将该 XML 文档用作 XML 数据源：例如， `http://localhost/Customers.xml`。</span><span class="sxs-lookup"><span data-stu-id="66e1a-248">To try out the element path examples in the previous section, you can copy this XML and save it to a URL that is accessible by Report Designer, and then use the XML document as an XML data source: for example, `http://localhost/Customers.xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<Customers xmlns="http://www.adventure-works.com">  
   <Customer ID="11">  
      <FirstName>Bobby</FirstName>  
      <LastName>Moore</LastName>  
      <Orders>  
         <Order ID="1" Qty="6">Chair</Order>  
         <Order ID="2" Qty="1">Table</Order>  
      </Orders>  
      <Returns>  
         <Return ID="1" Qty="2">Chair</Return>  
      </Returns>  
   </Customer>  
   <Customer ID="20">  
      <FirstName>Crystal</FirstName>  
      <LastName>Hu</LastName>  
      <Orders>  
         <Order ID="8" Qty="2">Sofa</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
   <Customer ID="33">  
      <FirstName>Wyatt</FirstName>  
      <LastName>Diaz</LastName>  
      <Orders>  
         <Order ID="15" Qty="2">EndTables</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
</Customers>  
```  
  
 <span data-ttu-id="66e1a-249">还可以使用下列步骤，创建不包含连接字符串的 XML 数据源，并在查询中嵌入 Customers.XML：</span><span class="sxs-lookup"><span data-stu-id="66e1a-249">Alternatively, you can create an XML data source that has no connection string and embed Customers.XML in the query, using the following procedure:</span></span>  
  
###### <a name="to-embed-customersxml-in-a-query"></a><span data-ttu-id="66e1a-250">在查询中嵌入 Customers.XML</span><span class="sxs-lookup"><span data-stu-id="66e1a-250">To embed Customers.XML in a query</span></span>  
  
1.  <span data-ttu-id="66e1a-251">使用空连接字符串创建一个 XML 数据源。</span><span class="sxs-lookup"><span data-stu-id="66e1a-251">Create an XML data source with a blank connection string.</span></span>  
  
2.  <span data-ttu-id="66e1a-252">为 XML 数据源创建新的数据集。</span><span class="sxs-lookup"><span data-stu-id="66e1a-252">Create a new dataset for the XML data source.</span></span>  
  
3.  <span data-ttu-id="66e1a-253">在 **“数据集属性”** 对话框中，单击 **“查询设计器”**。</span><span class="sxs-lookup"><span data-stu-id="66e1a-253">In the **Dataset Properties** dialog box, click **Query Designer**.</span></span> <span data-ttu-id="66e1a-254">基于文本的查询设计器对话框打开。</span><span class="sxs-lookup"><span data-stu-id="66e1a-254">The text-based query designer dialog box opens.</span></span>  
  
4.  <span data-ttu-id="66e1a-255">在查询窗格中，输入以下两行：</span><span class="sxs-lookup"><span data-stu-id="66e1a-255">In the query pane, enter the following two lines:</span></span>  
  
     `<Query>`  
  
     `<XmlData>`  
  
5.  <span data-ttu-id="66e1a-256">复制 Customers.XML 并将文本粘贴到 `<XmlData>`之后的查询窗格中。</span><span class="sxs-lookup"><span data-stu-id="66e1a-256">Copy Customers.XML and paste the text in the query pane after `<XmlData>`.</span></span>  
  
6.  <span data-ttu-id="66e1a-257">在查询窗格中，删除从 Customers.XML 中复制的第一行： `<?xml version="1.0"?>`</span><span class="sxs-lookup"><span data-stu-id="66e1a-257">In the query pane, delete the first line that you copied from Customers.XML: `<?xml version="1.0"?>`</span></span>  
  
7.  <span data-ttu-id="66e1a-258">在查询的结尾添加以下两行：</span><span class="sxs-lookup"><span data-stu-id="66e1a-258">At the end of the query, add the following two lines:</span></span>  
  
     `<XmlData>`  
  
     `<Query>`  
  
8.  <span data-ttu-id="66e1a-259">单击“运行查询(!)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66e1a-259">Click **Run Query** (!).</span></span>  
  
     <span data-ttu-id="66e1a-260">结果集的以下列中显示 4 行数据： `xmlns`、 `Customer.ID`、 `FirstName`、 `LastName`、 `ID`、 `Qty`、 `Order`。</span><span class="sxs-lookup"><span data-stu-id="66e1a-260">The result set displays 4 lines of data with the following columns: `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="66e1a-261">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66e1a-261">See Also</span></span>  
 <span data-ttu-id="66e1a-262">[XML 连接类型 &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66e1a-262">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 <span data-ttu-id="66e1a-263">[Reporting Services 的教程 &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66e1a-263">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="66e1a-264">在“报表数据”窗格中添加、编辑和刷新字段（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="66e1a-264">Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;</span></span>](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
  
