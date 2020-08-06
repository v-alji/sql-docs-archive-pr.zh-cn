---
title: 使用嵌套 AUTO 模式查询生成同级 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- queries [XML in SQL Server], nested AUTO mode
- nested AUTO mode query
ms.assetid: 748d9899-589d-4420-8048-1258e9e67c20
author: rothja
ms.author: jroth
ms.openlocfilehash: 20362942bdd0f7e7537433b664e5e63461ded499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694368"
---
# <a name="generate-siblings-with-a-nested-auto-mode-query"></a><span data-ttu-id="a51a2-102">使用嵌套 AUTO 模式查询生成同级</span><span class="sxs-lookup"><span data-stu-id="a51a2-102">Generate Siblings with a Nested AUTO Mode Query</span></span>
  <span data-ttu-id="a51a2-103">以下示例显示了如何使用嵌套 AUTO 模式查询来生成同级。</span><span class="sxs-lookup"><span data-stu-id="a51a2-103">The following example shows how to generate siblings by using a nested AUTO mode query.</span></span> <span data-ttu-id="a51a2-104">生成此类 XML 的其他方式只有这一种，即使用 EXPLICIT 模式。</span><span class="sxs-lookup"><span data-stu-id="a51a2-104">The only other way to generate such XML is to use the EXPLICIT mode.</span></span> <span data-ttu-id="a51a2-105">但是，这样做可能会很麻烦。</span><span class="sxs-lookup"><span data-stu-id="a51a2-105">However, this can be cumbersome.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a51a2-106">示例</span><span class="sxs-lookup"><span data-stu-id="a51a2-106">Example</span></span>  
 <span data-ttu-id="a51a2-107">此查询将构造用于提供销售订单信息的 XML。</span><span class="sxs-lookup"><span data-stu-id="a51a2-107">This query constructs XML that provides sales order information.</span></span> <span data-ttu-id="a51a2-108">其中包括：</span><span class="sxs-lookup"><span data-stu-id="a51a2-108">This includes the following:</span></span>  
  
-   <span data-ttu-id="a51a2-109">销售订单表头信息、 `SalesOrderID`、 `SalesPersonID`和 `OrderDate`。</span><span class="sxs-lookup"><span data-stu-id="a51a2-109">Sales order header information, `SalesOrderID`, `SalesPersonID`, and `OrderDate`.</span></span> [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="a51a2-110">将此信息存储在 `SalesOrderHeader` 表中。</span><span class="sxs-lookup"><span data-stu-id="a51a2-110">stores this information in the `SalesOrderHeader` table.</span></span>  
  
-   <span data-ttu-id="a51a2-111">销售订单详细信息。</span><span class="sxs-lookup"><span data-stu-id="a51a2-111">Sales order detail information.</span></span> <span data-ttu-id="a51a2-112">这包括所订购的一个或多个产品、单价和订购数量。</span><span class="sxs-lookup"><span data-stu-id="a51a2-112">This includes one or more products ordered, the unit price, and the quantity ordered.</span></span> <span data-ttu-id="a51a2-113">此信息存储在 `SalesOrderDetail` 表中。</span><span class="sxs-lookup"><span data-stu-id="a51a2-113">This information is stored in the `SalesOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="a51a2-114">销售人员信息。</span><span class="sxs-lookup"><span data-stu-id="a51a2-114">Sales person information.</span></span> <span data-ttu-id="a51a2-115">这是获得订单的销售人员。</span><span class="sxs-lookup"><span data-stu-id="a51a2-115">This is the salesperson who took the order.</span></span> <span data-ttu-id="a51a2-116">`SalesPerson` 表提供 `SalesPersonID`。</span><span class="sxs-lookup"><span data-stu-id="a51a2-116">The `SalesPerson` table provides the `SalesPersonID`.</span></span> <span data-ttu-id="a51a2-117">对于此查询，必须将此表联接到 `Employee` 表以查找销售人员的姓名。</span><span class="sxs-lookup"><span data-stu-id="a51a2-117">For this query, you have to join this table to the `Employee` table to find the name of the sales person.</span></span>  
  
 <span data-ttu-id="a51a2-118">后面两个不同的 `SELECT` 查询生成外形略有不同的 XML。</span><span class="sxs-lookup"><span data-stu-id="a51a2-118">The two distinct `SELECT` queries that follow generate XML with a small difference in shape.</span></span>  
  
 <span data-ttu-id="a51a2-119">第一个查询生成的 XML 中的 <`SalesPerson`> 和 <`SalesOrderHeader`> 显示为 <`SalesOrder`> 的同级子成员。</span><span class="sxs-lookup"><span data-stu-id="a51a2-119">The first query generates XML in which <`SalesPerson`> and <`SalesOrderHeader`> appear as sibling children of <`SalesOrder`>:</span></span>  
  
```  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID =   
                   SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
        FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
        for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As   
                     SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="a51a2-120">在先前的查询中，最外面的 `SELECT` 语句执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a51a2-120">In the previous query, the outermost `SELECT` statement does the following:</span></span>  
  
-   <span data-ttu-id="a51a2-121">查询在 `SalesOrder` 子句中指定的行集 `FROM`。</span><span class="sxs-lookup"><span data-stu-id="a51a2-121">Queries the rowset, `SalesOrder`, specified in the `FROM` clause.</span></span> <span data-ttu-id="a51a2-122">结果是包含一个或多个 <`SalesOrder`> 元素的 XML。</span><span class="sxs-lookup"><span data-stu-id="a51a2-122">The result is an XML with one or more <`SalesOrder`> elements.</span></span>  
  
-   <span data-ttu-id="a51a2-123">指定 `AUTO` 模式和 `TYPE` 指令。</span><span class="sxs-lookup"><span data-stu-id="a51a2-123">Specifies `AUTO` mode and the `TYPE` directive.</span></span> <span data-ttu-id="a51a2-124">`AUTO`模式将查询结果转换为 XML，指令将 `TYPE` 结果作为 `xml` 类型返回。</span><span class="sxs-lookup"><span data-stu-id="a51a2-124">`AUTO` mode transforms the query result into XML, and the `TYPE` directive returns the result as `xml` type.</span></span>  
  
-   <span data-ttu-id="a51a2-125">包括两个以逗号分隔的嵌套 `SELECT` 语句。</span><span class="sxs-lookup"><span data-stu-id="a51a2-125">Includes two nested `SELECT` statements separated by a comma.</span></span> <span data-ttu-id="a51a2-126">第一个嵌套 `SELECT` 语句检索销售订单信息、表头和详细信息，第二个嵌套 `SELECT` 语句检索销售人员信息。</span><span class="sxs-lookup"><span data-stu-id="a51a2-126">The first nested `SELECT` retrieves sales order information, header and details, and the second nested `SELECT` statement retrieves salesperson information.</span></span>  
  
    -   <span data-ttu-id="a51a2-127">检索 `SELECT` 、 `SalesOrderID`和 `SalesPersonID`的 `CustomerID` 语句本身包括另一个返回销售订单详细信息的嵌套 `SELECT ... FOR XML` 语句（使用 `AUTO` 模式和 `TYPE` 指令）。</span><span class="sxs-lookup"><span data-stu-id="a51a2-127">The `SELECT` statement that retrieves `SalesOrderID`, `SalesPersonID`, and `CustomerID` itself includes another nested `SELECT ... FOR XML` statement (with `AUTO` mode and `TYPE` directive) that returns sales order detail information.</span></span>  
  
 <span data-ttu-id="a51a2-128">检索销售人员信息的 `SELECT` 语句查询在 `SalesPerson`子句中创建的行集 `FROM` 。</span><span class="sxs-lookup"><span data-stu-id="a51a2-128">The `SELECT` statement that retrieves the sales person information queries a rowset, `SalesPerson`, created in the `FROM` clause.</span></span> <span data-ttu-id="a51a2-129">若要使用 `FOR XML` 查询，必须提供在 `FROM` 子句中生成的匿名行集的名称。</span><span class="sxs-lookup"><span data-stu-id="a51a2-129">For `FOR XML` queries to work, you must provide a name for the anonymous rowset generated in the `FROM` clause.</span></span> <span data-ttu-id="a51a2-130">在本例中，提供的名称为 `SalesPerson`。</span><span class="sxs-lookup"><span data-stu-id="a51a2-130">In this case, the name provided is `SalesPerson`.</span></span>  
  
 <span data-ttu-id="a51a2-131">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="a51a2-131">This is the partial result:</span></span>  
  
```  
<SalesOrder>  
  <Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  </Sales.SalesOrderHeader>  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</SalesOrder>  
...  
```  
  
 <span data-ttu-id="a51a2-132">以下查询生成的销售订单信息基本相同，只是在结果 XML 中，<`SalesPerson`> 显示为 <`SalesOrderDetail`> 的同级：</span><span class="sxs-lookup"><span data-stu-id="a51a2-132">The following query generates the same sales order information, except that in the resulting XML, the <`SalesPerson`> appears as a sibling of <`SalesOrderDetail`>:</span></span>  
  
```  
<SalesOrder>  
    <SalesOrderHeader ...>  
          <SalesOrderDetail .../>  
          <SalesOrderDetail .../>  
          ...  
          <SalesPerson .../>  
    </SalesOrderHeader>  
  
</SalesOrder>  
<SalesOrder>  
  ...  
</SalesOrder>  
```  
  
 <span data-ttu-id="a51a2-133">以下是查询语句：</span><span class="sxs-lookup"><span data-stu-id="a51a2-133">This is the query:</span></span>  
  
```  
SELECT SalesOrderID, SalesPersonID, CustomerID,  
             (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
              from Sales.SalesOrderDetail  
              WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
              FOR XML AUTO, TYPE),  
              (SELECT *   
               FROM  (SELECT SalesPersonID, EmployeeID  
                    FROM Sales.SalesPerson, HumanResources.Employee  
                    WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
               WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
         FOR XML AUTO, TYPE)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID=43659 or SalesOrderID=43660  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="a51a2-134">结果如下：</span><span class="sxs-lookup"><span data-stu-id="a51a2-134">This is the result:</span></span>  
  
```  
<Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
<Sales.SalesOrderHeader SalesOrderID="43660" SalesPersonID="279" CustomerID="117">  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="762" OrderQty="1" UnitPrice="419.4589" />  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="758" OrderQty="1" UnitPrice="874.7940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
```  
  
 <span data-ttu-id="a51a2-135">由于 `TYPE` 指令将查询结果作为 `xml` 类型返回，因此，可以使用各种 `xml` 数据类型方法查询生成的 XML。</span><span class="sxs-lookup"><span data-stu-id="a51a2-135">Because the `TYPE` directive returns a query result as `xml` type, you can query the resulting XML by using various `xml` data type methods.</span></span> <span data-ttu-id="a51a2-136">有关详细信息，请参阅 [xml 数据类型方法](/sql/t-sql/xml/xml-data-type-methods)。</span><span class="sxs-lookup"><span data-stu-id="a51a2-136">For more information, see [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span> <span data-ttu-id="a51a2-137">在以下查询中，注意：</span><span class="sxs-lookup"><span data-stu-id="a51a2-137">In the following query, note the following:</span></span>  
  
-   <span data-ttu-id="a51a2-138">将先前的查询添加到 `FROM` 子句。</span><span class="sxs-lookup"><span data-stu-id="a51a2-138">The previous query is added in the `FROM` clause.</span></span> <span data-ttu-id="a51a2-139">查询结果返回为表。</span><span class="sxs-lookup"><span data-stu-id="a51a2-139">The query result is returned as a table.</span></span> <span data-ttu-id="a51a2-140">注意添加的 `XmlCol` 别名。</span><span class="sxs-lookup"><span data-stu-id="a51a2-140">Note the `XmlCol` alias that is added.</span></span>  
  
-   <span data-ttu-id="a51a2-141">`SELECT` 子句对 `XmlCol` 子句中返回的 `FROM` 指定 XQuery。</span><span class="sxs-lookup"><span data-stu-id="a51a2-141">The `SELECT` clause specifies an XQuery against the `XmlCol` returned in the `FROM` clause.</span></span> <span data-ttu-id="a51a2-142">`query()` 数据类型的 `xml` 方法用于指定 XQuery。</span><span class="sxs-lookup"><span data-stu-id="a51a2-142">The `query()` method of the `xml` data type is used in specifying the XQuery.</span></span> <span data-ttu-id="a51a2-143">有关详细信息，请参阅 [query() 方法（xml 数据类型）](/sql/t-sql/xml/query-method-xml-data-type)。</span><span class="sxs-lookup"><span data-stu-id="a51a2-143">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
    ```  
    SELECT XmlCol.query('<Root> { /* } </Root>')  
    FROM (  
    SELECT SalesOrderID, SalesPersonID, CustomerID,  
                 (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
                  from Sales.SalesOrderDetail  
                  WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
                  FOR XML AUTO, TYPE),  
                  (SELECT *   
                   FROM  (SELECT SalesPersonID, EmployeeID  
                        FROM Sales.SalesPerson, HumanResources.Employee  
                        WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
                   WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
             FOR XML AUTO, TYPE)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesOrderID='43659' or SalesOrderID='43660'  
    FOR XML AUTO, TYPE ) as T(XmlCol)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a51a2-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a51a2-144">See Also</span></span>  
 [<span data-ttu-id="a51a2-145">使用嵌套 FOR XML 查询</span><span class="sxs-lookup"><span data-stu-id="a51a2-145">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
