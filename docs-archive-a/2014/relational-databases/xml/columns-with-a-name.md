---
title: 具有名称的列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: c994e089-4cfc-4e9b-b7fc-e74f6014b51a
author: rothja
ms.author: jroth
ms.openlocfilehash: 32cfe617b80ed216374249961b85eae401011a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687571"
---
# <a name="columns-with-a-name"></a><span data-ttu-id="8dd90-102">具有名称的列</span><span class="sxs-lookup"><span data-stu-id="8dd90-102">Columns with a Name</span></span>
  <span data-ttu-id="8dd90-103">下面是一些特定条件，在这些条件下具有名称的行集列将映射（区分大小写）到生成的 XML：</span><span class="sxs-lookup"><span data-stu-id="8dd90-103">The following are the specific conditions in which rowset columns with a name are mapped, case-sensitive, to the resulting XML:</span></span>  
  
-   <span data-ttu-id="8dd90-104">列名以 at 符号 (\@) 开头。</span><span class="sxs-lookup"><span data-stu-id="8dd90-104">The column name starts with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="8dd90-105">列名不以 at 符号 (\@) 开头。</span><span class="sxs-lookup"><span data-stu-id="8dd90-105">The column name does not start with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="8dd90-106">列名不以 at 符号 (\@) 开头，但包含斜线标记 (/)。</span><span class="sxs-lookup"><span data-stu-id="8dd90-106">The column name does not start with an at sign\@ and contains a slash mark (/).</span></span>  
  
-   <span data-ttu-id="8dd90-107">多个列共享同一前缀。</span><span class="sxs-lookup"><span data-stu-id="8dd90-107">Several columns share the same prefix.</span></span>  
  
-   <span data-ttu-id="8dd90-108">一列具有不同的名称。</span><span class="sxs-lookup"><span data-stu-id="8dd90-108">One column has a different name.</span></span>  
  
## <a name="column-name-starts-with-an-at-sign-"></a><span data-ttu-id="8dd90-109">列名以 at 符号 (\@) 开头</span><span class="sxs-lookup"><span data-stu-id="8dd90-109">Column Name Starts with an At Sign (\@)</span></span>  
 <span data-ttu-id="8dd90-110">如果列名称以 at 符号 (开头 \@) 并且不包含斜杠 (/) ，则 `row` 会创建一个具有相应列值的 <> 元素的特性。</span><span class="sxs-lookup"><span data-stu-id="8dd90-110">If the column name starts with an at sign (\@) and does not contain a slash mark (/), an attribute of the <`row`> element that has the corresponding column value is created.</span></span> <span data-ttu-id="8dd90-111">例如，下面的查询返回包含两列（\@PmId 和 Name）的行集。</span><span class="sxs-lookup"><span data-stu-id="8dd90-111">For example, the following query returns a two-column (\@PmId, Name) rowset.</span></span> <span data-ttu-id="8dd90-112">在生成的 XML 中，将向相应的 <`row`> 元素添加 **PmId** 属性并为其分配 ProductModelID 值。</span><span class="sxs-lookup"><span data-stu-id="8dd90-112">In the resulting XML, a **PmId** attribute is added to the corresponding <`row`> element and a value of ProductModelID is assigned to it.</span></span>  
  
```  
  
SELECT ProductModelID as "@PmId",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
  
```  
  
 <span data-ttu-id="8dd90-113">结果如下：</span><span class="sxs-lookup"><span data-stu-id="8dd90-113">This is the result:</span></span>  
  
```  
<row PmId="7">  
  <Name>HL Touring Frame</Name>  
</row>  
```  
  
 <span data-ttu-id="8dd90-114">请注意，在同一级别中，属性必须出现在其他任何节点类型（例如元素节点和文本节点）之前。</span><span class="sxs-lookup"><span data-stu-id="8dd90-114">Note that attributes must come before any other node types, such as element nodes and text nodes, in the same level.</span></span> <span data-ttu-id="8dd90-115">以下查询将返回一个错误：</span><span class="sxs-lookup"><span data-stu-id="8dd90-115">The following query will return an error:</span></span>  
  
```  
SELECT Name,  
       ProductModelID as "@PmId"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign-"></a><span data-ttu-id="8dd90-116">列名不以 at 符号 (\@) 开头</span><span class="sxs-lookup"><span data-stu-id="8dd90-116">Column Name Does Not Start with an At Sign (\@)</span></span>  
 <span data-ttu-id="8dd90-117">如果列名不以 at 符号 (开头 \@) ，则不是 XPath 节点测试之一，并且不包含斜杠标记 (/) ，默认情况下，将创建一个 XML 元素，该元素是行元素的子元素 <`row`>。</span><span class="sxs-lookup"><span data-stu-id="8dd90-117">If the column name does not start with an at sign (\@), is not one of the XPath node tests, and does not contain a slash mark (/), an XML element that is a subelement of the row element, <`row`> by default, is created.</span></span>  
  
 <span data-ttu-id="8dd90-118">以下查询指定了列名 result。</span><span class="sxs-lookup"><span data-stu-id="8dd90-118">The following query specifies the column name, the result.</span></span> <span data-ttu-id="8dd90-119">因此，将向 <`row`> 元素添加 <`result`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-119">Therefore, a <`result`> element child is added to the <`row`> element.</span></span>  
  
```  
SELECT 2+2 as result  
for xml PATH  
```  
  
 <span data-ttu-id="8dd90-120">结果如下：</span><span class="sxs-lookup"><span data-stu-id="8dd90-120">This is the result:</span></span>  
  
```  
<row>  
  <result>4</result>  
</row>  
```  
  
 <span data-ttu-id="8dd90-121">以下查询为针对 **xml** 类型的 Instructions 列指定的 XQuery 所返回的 XML 指定了列名 ManuWorkCenterInformation。</span><span class="sxs-lookup"><span data-stu-id="8dd90-121">The following query specifies the column name, ManuWorkCenterInformation, for the XML returned by the XQuery specified against Instructions column of **xml** type.</span></span> <span data-ttu-id="8dd90-122">因此，将添加 <`ManuWorkCenterInformation`> 元素来作为 <`row`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-122">Therefore, a <`ManuWorkCenterInformation`> element is added as a child of the <`row`> element.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') as ManuWorkCenterInformation  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
 <span data-ttu-id="8dd90-123">结果如下：</span><span class="sxs-lookup"><span data-stu-id="8dd90-123">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>7</ProductModelID>  
  <Name>HL Touring Frame</Name>  
  <ManuWorkCenterInformation>  
    <MI:Location ...LocationID="10" ...></MI:Location>  
    <MI:Location ...LocationID="20" ...></MI:Location>  
     ...  
  </ManuWorkCenterInformation>  
</row>  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign--and-contains-a-slash-mark-"></a><span data-ttu-id="8dd90-124">列名不以 at 符号 (\@) 开头，但包含斜线标记 (/)</span><span class="sxs-lookup"><span data-stu-id="8dd90-124">Column Name Does Not Start with an At Sign (\@) and Contains a Slash Mark (/)</span></span>  
 <span data-ttu-id="8dd90-125">如果列名不以 at 符号 (\@) 开头，但包含斜线标记 (/)，列名就指明了 XML 层次结构。</span><span class="sxs-lookup"><span data-stu-id="8dd90-125">If the column name does not start with an at sign (\@), but contains a slash mark (/), the column name indicates an XML hierarchy.</span></span> <span data-ttu-id="8dd90-126">例如，列名为“Name1/Name2/Name3.../Name***n*** ”，其中每个 Name***i*** 表示嵌套在当前行元素 (i=1) 中的元素名称或名为 Name***i-1***的元素下的元素名称。</span><span class="sxs-lookup"><span data-stu-id="8dd90-126">For example, if the column name is "Name1/Name2/Name3.../Name***n*** ", each Name***i*** represents an element name that is nested in the current row element (for i=1) or that is under the element that has the name Name***i-1***.</span></span> <span data-ttu-id="8dd90-127">如果 Namen 以“\@”开头，它就会映射到 Namen-1 元素的属性。</span><span class="sxs-lookup"><span data-stu-id="8dd90-127">If Name***n*** starts with '\@', it is mapped to an attribute of Name***n-1*** element.</span></span>  
  
 <span data-ttu-id="8dd90-128">例如，以下查询将返回雇员 ID 和表示为复杂元素 EmpName（包含名字、中间名和姓氏）的雇员名称。</span><span class="sxs-lookup"><span data-stu-id="8dd90-128">For example, the following query returns an employee ID and name that are represented as a complex element EmpName that contains a First, Middle, and Last name.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="8dd90-129">列名用作在 PATH 模式中构造 XML 时的路径。</span><span class="sxs-lookup"><span data-stu-id="8dd90-129">The column names are used as a path in constructing XML in the PATH mode.</span></span> <span data-ttu-id="8dd90-130">包含雇员 ID 值的列名以 " \@ " 开头。因此， **EmpID**属性添加到 <`row`> 元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-130">The column name that contains employee ID values, starts with '\@'.Therefore, an attribute, **EmpID**, is added to the <`row`> element.</span></span> <span data-ttu-id="8dd90-131">其他所有列的列名中均包含指明层次结构的斜杠标记 (/)。</span><span class="sxs-lookup"><span data-stu-id="8dd90-131">All other columns include a slash mark ('/') in the column name that indicates hierarchy.</span></span> <span data-ttu-id="8dd90-132">在生成的 XML 中，<`row`> 元素下将包含 <`EmpName`> 子元素，而 <`EmpName`> 子元素将包含 <`First`>、<`Middle`> 和 <`Last`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-132">The resulting XML will have the <`EmpName`> child under the <`row`> element, and the <`EmpName`> child will have <`First`>, <`Middle`> and <`Last`> element children.</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="8dd90-133">雇员的中间名为 Null，默认情况下，Null 值映射为“缺少相应的元素或属性”。</span><span class="sxs-lookup"><span data-stu-id="8dd90-133">The employee middle name is null and, by default, the null value maps to the absence of the element or attribute.</span></span> <span data-ttu-id="8dd90-134">如果希望针对 NULL 值生成元素，则可以指定带有 XSINIL 的 ELEMENTS 指令，如以下查询中所示。</span><span class="sxs-lookup"><span data-stu-id="8dd90-134">If you want elements generated for the NULL values, you can specify the ELEMENTS directive with XSINIL as shown in this query.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="8dd90-135">结果如下：</span><span class="sxs-lookup"><span data-stu-id="8dd90-135">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
      EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="8dd90-136">默认情况下，PATH 模式生成以元素为中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="8dd90-136">By default, the PATH mode generates element-centric XML.</span></span> <span data-ttu-id="8dd90-137">因此，在 PATH 模式中指定 ELEMENTS 指令将不起作用。</span><span class="sxs-lookup"><span data-stu-id="8dd90-137">Therefore, specifying the ELEMENTS directive in a PATH mode query has no effect.</span></span> <span data-ttu-id="8dd90-138">但是，如上一个示例所示，可以指定带有 XSINIL 的 ELEMENTS 指令来针对 Null 值生成元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-138">However, as shown in the previous example, the ELEMENTS directive is useful with XSINIL to generate elements for null values.</span></span>  
  
 <span data-ttu-id="8dd90-139">除了 ID 和名称以外，以下查询还将检索雇员地址。</span><span class="sxs-lookup"><span data-stu-id="8dd90-139">Besides the ID and name, the following query retrieves an employee address.</span></span> <span data-ttu-id="8dd90-140">按照地址列的列名中包含的路径，将向 <`row`> 元素添加 <`Address`> 子元素，并添加地址详细信息来作为 <`Address`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-140">As per the path in the column names for address columns, an <`Address`> element child is added to the <`row`> element and the address details are added as element children of the <`Address`> element.</span></span>  
  
```  
SELECT EmployeeID   "@EmpID",   
       FirstName    "EmpName/First",   
       MiddleName   "EmpName/Middle",   
       LastName     "EmpName/Last",  
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City         "Address/City"  
FROM   HumanResources.Employee E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="8dd90-141">结果如下：</span><span class="sxs-lookup"><span data-stu-id="8dd90-141">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
</row>  
```  
  
## <a name="several-columns-share-the-same-path-prefix"></a><span data-ttu-id="8dd90-142">若干列共享同一个路径前缀</span><span class="sxs-lookup"><span data-stu-id="8dd90-142">Several Columns Share the Same Path Prefix</span></span>  
 <span data-ttu-id="8dd90-143">如果若干后续列共享同一个路径前缀，则它们将被分组到同一名称下。</span><span class="sxs-lookup"><span data-stu-id="8dd90-143">If several subsequent columns share the same path prefix, they are grouped together under the same name.</span></span> <span data-ttu-id="8dd90-144">如果它们使用的是不同的命名空间前缀，则即使它们被绑定到同一命名空间，也被认为是不同的路径。</span><span class="sxs-lookup"><span data-stu-id="8dd90-144">If different namespace prefixes are being used even if they are bound to the same namespace, a path is considered different.</span></span> <span data-ttu-id="8dd90-145">在上一个查询中，FirstName、MiddleName 和 LastName 列共享同一个 EmpName 前缀。因此，它们被添加为 <`EmpName`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-145">In the previous query, the FirstName, MiddleName, and LastName columns share the same EmpName prefix.Therefore, they are added as children of the <`EmpName`> element.</span></span> <span data-ttu-id="8dd90-146">在上一个示例中创建 <`Address`> 元素时也是如此。</span><span class="sxs-lookup"><span data-stu-id="8dd90-146">This is also the case when you were creating the <`Address`> element in the previous example.</span></span>  
  
## <a name="one-column-has-a-different-name"></a><span data-ttu-id="8dd90-147">有一列具有不同的名称</span><span class="sxs-lookup"><span data-stu-id="8dd90-147">One Column Has a Different Name</span></span>  
 <span data-ttu-id="8dd90-148">如果列之间出现具有不同名称的列，则该列将会打破分组，如以下修改后的查询所示。</span><span class="sxs-lookup"><span data-stu-id="8dd90-148">If a column with a different name appears in between, it will break the grouping, as shown in the following modified query.</span></span> <span data-ttu-id="8dd90-149">该查询通过在 FirstName 和 MiddleName 列之间添加地址列，打破了 FirstName、MiddleName 和 LastName 的分组（如上一个查询中所指定）。</span><span class="sxs-lookup"><span data-stu-id="8dd90-149">The query breaks the grouping of FirstName, MiddleName, and LastName, as specified in the previous query, by adding address columns in between the FirstName and MiddleName columns.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName "EmpName/First",   
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City "Address/City",  
       MiddleName "EmpName/Middle",   
       LastName "EmpName/Last"  
FROM   HumanResources.EmployeeAddress E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="8dd90-150">结果，查询将创建两个 <`EmpName`> 元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-150">As a result, the query creates two <`EmpName`> elements.</span></span> <span data-ttu-id="8dd90-151">第一个 <`EmpName`> 元素包含 <`FirstName`> 子元素，第二个 <`EmpName`> 元素包含 <`MiddleName`> 和 <`LastName`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="8dd90-151">The first <`EmpName`> element has the <`FirstName`> element child and the second <`EmpName`> element has the <`MiddleName`> and <`LastName`> element children.</span></span>  
  
 <span data-ttu-id="8dd90-152">结果如下：</span><span class="sxs-lookup"><span data-stu-id="8dd90-152">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
  <EmpName>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dd90-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8dd90-153">See Also</span></span>  
 [<span data-ttu-id="8dd90-154">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="8dd90-154">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
