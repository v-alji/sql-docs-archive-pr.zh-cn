---
title: 将 AUTO 模式与 FOR XML 一起使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, AUTO mode
- ELEMENTS option
- FOR XML AUTO mode
- AUTO FOR XML mode
ms.assetid: 7140d656-1d42-4f01-a533-5251429f4450
author: rothja
ms.author: jroth
ms.openlocfilehash: 232cc046667c6d31cb9657a7abdc862204507d23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587262"
---
# <a name="use-auto-mode-with-for-xml"></a><span data-ttu-id="6360a-102">将 AUTO 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="6360a-102">Use AUTO Mode with FOR XML</span></span>
  <span data-ttu-id="6360a-103">如 [FOR XML (SQL Server)](for-xml-sql-server.md)中所述，AUTO 模式将查询结果以嵌套 XML 元素的方式返回。</span><span class="sxs-lookup"><span data-stu-id="6360a-103">As described in [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md), AUTO mode returns query results as nested XML elements.</span></span> <span data-ttu-id="6360a-104">这不能较好地控制从查询结果生成的 XML 的形式。</span><span class="sxs-lookup"><span data-stu-id="6360a-104">This does not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="6360a-105">如果要生成简单的层次结构，AUTO 模式查询很有用。</span><span class="sxs-lookup"><span data-stu-id="6360a-105">The AUTO mode queries are useful if you want to generate simple hierarchies.</span></span> <span data-ttu-id="6360a-106">但是， [将 EXPLICIT 模式与 FOR XML 一起使用](use-explicit-mode-with-for-xml.md) 和 [将 PATH 模式与 FOR XML 一起使用](use-path-mode-with-for-xml.md) 在确定从查询结果生成的 XML 的形式方面可提供更好的控制和更大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="6360a-106">However, [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) and [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) provide more control and flexibility in deciding the shape of the XML from a query result.</span></span>  
  
 <span data-ttu-id="6360a-107">在 FROM 子句内，每个在 SELECT 子句中至少有一列被列出的表都表示为一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="6360a-107">Each table in the FROM clause, from which at least one column is listed in the SELECT clause, is represented as an XML element.</span></span> <span data-ttu-id="6360a-108">如果在 FOR XML 子句中指定了可选的 ELEMENTS 选项，SELECT 子句中列出的列将映射到属性或子元素。</span><span class="sxs-lookup"><span data-stu-id="6360a-108">The columns listed in the SELECT clause are mapped to attributes or subelements, if the optional ELEMENTS option is specified in the FOR XML clause.</span></span>  
  
 <span data-ttu-id="6360a-109">生成的 XML 中的 XML 层次结构（即元素嵌套）基于由 SELECT 子句中指定的列所标识的表的顺序。</span><span class="sxs-lookup"><span data-stu-id="6360a-109">The XML hierarchy, nesting of the elements, in the resulting XML is based on the order of tables identified by the columns specified in the SELECT clause.</span></span> <span data-ttu-id="6360a-110">因此，在 SELECT 子句中指定的列名的顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="6360a-110">Therefore, the order in which column names are specified in the SELECT clause is significant.</span></span> <span data-ttu-id="6360a-111">最左侧第一个被标识的表形成所生成的 XML 文档中的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="6360a-111">The first, leftmost table that is identified forms the top element in the resulting XML document.</span></span> <span data-ttu-id="6360a-112">由 SELECT 语句中的列所标识的最左侧第二个表形成顶级元素内的子元素，依此类推。</span><span class="sxs-lookup"><span data-stu-id="6360a-112">The second leftmost table, identified by columns in the SELECT statement, forms a subelement within the top element, and so on.</span></span>  
  
 <span data-ttu-id="6360a-113">如果 SELECT 子句中列出的列名来自由 SELECT 子句中以前指定的列所标识的表，该列将作为已创建的元素的属性添加，而不是在层次结构中打开一个新级别。</span><span class="sxs-lookup"><span data-stu-id="6360a-113">If a column name listed in the SELECT clause is from a table that is already identified by a previously specified column in the SELECT clause, the column is added as an attribute of the element already created, instead of opening a new level of hierarchy.</span></span> <span data-ttu-id="6360a-114">如果已指定 ELEMENTS 选项，该列将作为属性添加。</span><span class="sxs-lookup"><span data-stu-id="6360a-114">If the ELEMENTS option is specified, the column is added as an attribute.</span></span>  
  
 <span data-ttu-id="6360a-115">例如，执行以下查询：</span><span class="sxs-lookup"><span data-stu-id="6360a-115">For example, execute this query:</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO  
```  
  
 <span data-ttu-id="6360a-116">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="6360a-116">This is the partial result:</span></span>  
  
```  
<Cust CustomerID="1" CustomerType="S">  
  <OrderHeader CustomerID="1" SalesOrderID="43860" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="44501" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="45283" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="46042" Status="5" />  
</Cust>  
...  
```  
  
 <span data-ttu-id="6360a-117">对于 SELECT 子句，注意下列内容：</span><span class="sxs-lookup"><span data-stu-id="6360a-117">Note the following in the SELECT clause:</span></span>  
  
-   <span data-ttu-id="6360a-118">CustomerID 引用 Cust 表。</span><span class="sxs-lookup"><span data-stu-id="6360a-118">The CustomerID references the Cust table.</span></span> <span data-ttu-id="6360a-119">因此，创建一个 <`Cust`> 元素，CustomerID 作为其属性添加。</span><span class="sxs-lookup"><span data-stu-id="6360a-119">Therefore, a <`Cust`> element is created and CustomerID is added as its attribute.</span></span>  
  
-   <span data-ttu-id="6360a-120">接下来的三列 OrderHeader.CustomerID、OrderHeader.SaleOrderID 和 OrderHeader.Status 引用 OrderHeader 表。</span><span class="sxs-lookup"><span data-stu-id="6360a-120">Next, three columns, OrderHeader.CustomerID, OrderHeader.SaleOrderID, and OrderHeader.Status, reference the OrderHeader table.</span></span> <span data-ttu-id="6360a-121">因此，为 <`Cust`> 元素添加 <`OrderHeader`> 子元素，这三列作为 <`OrderHeader`> 的属性添加。</span><span class="sxs-lookup"><span data-stu-id="6360a-121">Therefore, an <`OrderHeader`> element is added as a subelement of the <`Cust`> element and the three columns are added as attributes of <`OrderHeader`>.</span></span>  
  
-   <span data-ttu-id="6360a-122">接着，Cust.CustomerType 列再次引用 Cust 表，该表已由 Cust.CustomerID 列标识。</span><span class="sxs-lookup"><span data-stu-id="6360a-122">Next, the Cust.CustomerType column again references the Cust table that was already identified by the Cust.CustomerID column.</span></span> <span data-ttu-id="6360a-123">因此，不创建新元素，</span><span class="sxs-lookup"><span data-stu-id="6360a-123">Therefore, no new element is created.</span></span> <span data-ttu-id="6360a-124">而是为以前创建的 <`Cust`> 元素添加 CustomerType 属性。</span><span class="sxs-lookup"><span data-stu-id="6360a-124">Instead, the CustomerType attribute is added to the <`Cust`> element that was previously created.</span></span>  
  
-   <span data-ttu-id="6360a-125">查询为表名指定别名。</span><span class="sxs-lookup"><span data-stu-id="6360a-125">The query specifies aliases for the table names.</span></span> <span data-ttu-id="6360a-126">这些别名显示为相应的元素名。</span><span class="sxs-lookup"><span data-stu-id="6360a-126">These aliases appear as corresponding element names.</span></span>  
  
-   <span data-ttu-id="6360a-127">需要使用 ORDER BY 对一个父级下的所有子级分组。</span><span class="sxs-lookup"><span data-stu-id="6360a-127">ORDER BY is required to group all children under one parent.</span></span>  
  
 <span data-ttu-id="6360a-128">下面的查询与上一个查询类似，不同的是 SELECT 子句先指定 OrderHeader 表中的列，再指定 Cust 表中的列。</span><span class="sxs-lookup"><span data-stu-id="6360a-128">This query is similar to the previous one, except the SELECT clause specifies columns in the OrderHeader table before the columns in the Cust table.</span></span> <span data-ttu-id="6360a-129">因此，首先创建 <`OrderHeader`> 元素，然后为该元素添加 <`Cust`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="6360a-129">Therefore, first <`OrderHeader`> element is created and then the <`Cust`> child element is added to it.</span></span>  
  
```  
select OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerID,   
       Cust.CustomerType  
from Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
where Cust.CustomerID = OrderHeader.CustomerID  
for xml auto  
```  
  
 <span data-ttu-id="6360a-130">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="6360a-130">This is the partial result:</span></span>  
  
```  
<OrderHeader CustomerID="1" SalesOrderID="43860" Status="5">  
  <Cust CustomerID="1" CustomerType="S" />  
</OrderHeader>  
...  
```  
  
 <span data-ttu-id="6360a-131">如果在 FOR XML 子句中添加了 ELEMENTS 选项，将返回以元素为中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="6360a-131">If the ELEMENTS option is added in the FOR XML clause, element-centric XML is returned.</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="6360a-132">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="6360a-132">This is the partial result:</span></span>  
  
```  
<Cust>  
  <CustomerID>1</CustomerID>  
  <CustomerType>S</CustomerType>  
  <OrderHeader>  
    <CustomerID>1</CustomerID>  
    <SalesOrderID>43860</SalesOrderID>  
    <Status>5</Status>  
  </OrderHeader>  
   ...  
</Cust>  
...  
```  
  
 <span data-ttu-id="6360a-133">在此查询中，因为 CustomerID 是表的主键，所以在创建 \<Cust> 元素的过程中会逐行比较 CustomerID 值。</span><span class="sxs-lookup"><span data-stu-id="6360a-133">In this query, the CustomerID values are compared from one row to the next in creating the \<Cust> elements, because CustomerID is the primary key of the table.</span></span> <span data-ttu-id="6360a-134">如果未将 CustomerID 标识为表的主键，将逐行比较所有列值（此查询中的 CustomerID 和 CustomerType）。</span><span class="sxs-lookup"><span data-stu-id="6360a-134">If CustomerID is not identified as the primary key for the table, all the column values (CustomerID, CustomerType in this query) are compared from one row to the next.</span></span> <span data-ttu-id="6360a-135">如果值不同，将向 XML 添加新的 \<Cust> 元素。</span><span class="sxs-lookup"><span data-stu-id="6360a-135">If the values differ, a new \<Cust> element is added to the XML.</span></span>  
  
 <span data-ttu-id="6360a-136">在比较这些列值时，如果要比较的任何列是 **text**、 **ntext**、 **image**或 **xml**类型，即使它们的值可能相同，FOR XML 也将认为它们是不同的，并且不对其进行比较。</span><span class="sxs-lookup"><span data-stu-id="6360a-136">When comparing these column values, if any of the columns to be compared are of type **text**, **ntext**, **image**, or **xml**, FOR XML assumes that the values are different and not compared, even though they may be the same.</span></span> <span data-ttu-id="6360a-137">这是因为不支持大型对象的比较。</span><span class="sxs-lookup"><span data-stu-id="6360a-137">This is because comparing large objects is not supported.</span></span> <span data-ttu-id="6360a-138">这些元素将被添加到每个选定行的结果中。</span><span class="sxs-lookup"><span data-stu-id="6360a-138">Elements are added to the result for each row selected.</span></span> <span data-ttu-id="6360a-139">请注意，会比较 **(n)varchar(max)** 和 **varbinary(max)** 类型的列。</span><span class="sxs-lookup"><span data-stu-id="6360a-139">Note that columns of **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="6360a-140">如果 SELECT 子句中的某列无法与 FROM 子句中标识的任何表相关联（例如，该列是聚合列或计算列的情况下），则该列在列表中出现时，将添加到 XML 文档的最深嵌套级别中。</span><span class="sxs-lookup"><span data-stu-id="6360a-140">When a column in the SELECT clause cannot be associated with any of the tables identified in the FROM clause, as in the case of an aggregate column or computed column, the column is added in the XML document in the deepest nesting level in place when it is encountered in the list.</span></span> <span data-ttu-id="6360a-141">如果该列作为 SELECT 子句的第一列出现，将被添加到顶级元素。</span><span class="sxs-lookup"><span data-stu-id="6360a-141">If such a column appears as the first column in the SELECT clause, the column is added to the top element.</span></span>  
  
 <span data-ttu-id="6360a-142">如果 SELECT 子句中指定了星号 (\*) 通配符，则以前面所述的方式根据查询引擎所返回的行的顺序确定嵌套。</span><span class="sxs-lookup"><span data-stu-id="6360a-142">If the asterisk (\*) wildcard character is specified in the SELECT clause, the nesting is determined in the same way as previously described, based on the order that the rows are returned by the query engine.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6360a-143">本节内容</span><span class="sxs-lookup"><span data-stu-id="6360a-143">In This Section</span></span>  
 <span data-ttu-id="6360a-144">下面的主题提供有关 AUTO 模式的更多信息：</span><span class="sxs-lookup"><span data-stu-id="6360a-144">The following topics provide more information about AUTO mode:</span></span>  
  
-   [<span data-ttu-id="6360a-145">使用 BINARY BASE64 选项</span><span class="sxs-lookup"><span data-stu-id="6360a-145">Use the BINARY BASE64 Option</span></span>](use-the-binary-base64-option.md)  
  
-   [<span data-ttu-id="6360a-146">返回的 XML 成形过程中的 AUTO 模式试探方法</span><span class="sxs-lookup"><span data-stu-id="6360a-146">AUTO Mode Heuristics in Shaping Returned XML</span></span>](auto-mode-heuristics-in-shaping-returned-xml.md)  
  
-   [<span data-ttu-id="6360a-147">示例：使用 AUTO 模式</span><span class="sxs-lookup"><span data-stu-id="6360a-147">Examples: Using AUTO Mode</span></span>](examples-using-auto-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="6360a-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6360a-148">See Also</span></span>  
 <span data-ttu-id="6360a-149">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6360a-149">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="6360a-150">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6360a-150">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
