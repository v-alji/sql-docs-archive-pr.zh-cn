---
title: 示例：检索员工信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT mode
ms.assetid: 63cd6569-2600-485b-92b4-1f6ba09db219
author: rothja
ms.author: jroth
ms.openlocfilehash: ae4578aedb7dbcc63388d5ef797e3a0bf5d8c306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587265"
---
# <a name="example-retrieving-employee-information"></a><span data-ttu-id="47f49-102">示例：检索员工信息</span><span class="sxs-lookup"><span data-stu-id="47f49-102">Example: Retrieving Employee Information</span></span>
  <span data-ttu-id="47f49-103">此示例检索每个雇员的雇员 ID 和雇员姓名。</span><span class="sxs-lookup"><span data-stu-id="47f49-103">This example retrieves an employee ID and employee name for each employee.</span></span> <span data-ttu-id="47f49-104">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中，可从 Employee 表的 BusinessEntityID 列获得 employeeID。</span><span class="sxs-lookup"><span data-stu-id="47f49-104">In the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, the employeeID can be obtained from the BusinessEntityID column in the Employee table.</span></span> <span data-ttu-id="47f49-105">可从 Person 表中获得雇员姓名。</span><span class="sxs-lookup"><span data-stu-id="47f49-105">Employee names can be obtained from the Person table.</span></span> <span data-ttu-id="47f49-106">可使用 BusinessEntityID 列来联接表。</span><span class="sxs-lookup"><span data-stu-id="47f49-106">The BusinessEntityID column can be used to join the tables.</span></span>  
  
 <span data-ttu-id="47f49-107">假定要让 FOR XML EXPLICIT 转换生成 XML，如下所示：</span><span class="sxs-lookup"><span data-stu-id="47f49-107">Assume that you want FOR XML EXPLICIT transformation to generate XML as shown in the following:</span></span>  
  
```  
<Employee EmpID="1" >  
  <Name FName="Ken" LName="S??nchez" />  
</Employee>  
...  
```  
  
 <span data-ttu-id="47f49-108">因为层次结构中有两个级别，所以应编写两个 `SELECT` 查询并应用 UNION ALL。</span><span class="sxs-lookup"><span data-stu-id="47f49-108">Because there are two levels in the hierarchy, you would write two `SELECT` queries and apply UNION ALL.</span></span> <span data-ttu-id="47f49-109">下面是检索 <`Employee`> 元素及其属性的值的第一个查询。</span><span class="sxs-lookup"><span data-stu-id="47f49-109">This is the first query that retrieves values for the <`Employee`> element and its attributes.</span></span> <span data-ttu-id="47f49-110">该查询将值 `1` 赋给 <`Employee`> 元素的 `Tag`，将 NULL 赋给 `Parent`，因为它是一个顶级元素。</span><span class="sxs-lookup"><span data-stu-id="47f49-110">The query assigns `1` as `Tag` value for the <`Employee`> element and NULL as `Parent`, because it is the top-level element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID AS [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="47f49-111">下面是第二个查询。</span><span class="sxs-lookup"><span data-stu-id="47f49-111">This is the second query.</span></span> <span data-ttu-id="47f49-112">它检索 <`Name`> 元素的值。</span><span class="sxs-lookup"><span data-stu-id="47f49-112">It retrieves values for the <`Name`> element.</span></span> <span data-ttu-id="47f49-113">它将值 `2` 赋给 <`Name`> 元素的 `Tag`，将值 `1` 赋给 `Parent` 标记，从而将 <`Employee`> 标识为父元素。</span><span class="sxs-lookup"><span data-stu-id="47f49-113">It assigns `2` as `Tag` value for the <`Name`> element and `1` as `Parent` tag value identifying <`Employee`> as the parent.</span></span>  
  
```  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="47f49-114">可以使用 `UNION AL`L 组合这些查询，应用 `FOR XML EXPLICIT`，并指定所需的 `ORDER BY` 子句。</span><span class="sxs-lookup"><span data-stu-id="47f49-114">You combine these queries with `UNION AL`L, apply `FOR XML EXPLICIT`, and specify the required `ORDER BY` clause.</span></span> <span data-ttu-id="47f49-115">您必须先按 `BusinessEntityID` 、再按姓名对行集进行排序，以便先显示姓名中的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="47f49-115">You must sort the rowset first by `BusinessEntityID` and then by name so that the NULL values in the name appear first.</span></span> <span data-ttu-id="47f49-116">通过执行下面这个不带 FOR XML 子句的查询，可以看到生成的通用表。</span><span class="sxs-lookup"><span data-stu-id="47f49-116">By executing the following query without the FOR XML clause, you can see the universal table generated.</span></span>  
  
 <span data-ttu-id="47f49-117">下面是最终查询：</span><span class="sxs-lookup"><span data-stu-id="47f49-117">This is the final query:</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
ORDER BY [Employee!1!EmpID],[Name!2!FName]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="47f49-118">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="47f49-118">This is the partial result:</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name FName="Ken" LName="S??nchez" />`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name FName="Terri" LName="Duffy" />`  
  
 `</Employee>`  
  
 `...`  
  
 <span data-ttu-id="47f49-119">第一个 `SELECT` 指定所得到的行集中的列名。</span><span class="sxs-lookup"><span data-stu-id="47f49-119">The first `SELECT` specifies names for columns in the resulting rowset.</span></span> <span data-ttu-id="47f49-120">这些名称形成两个列组。</span><span class="sxs-lookup"><span data-stu-id="47f49-120">These names form two column groups.</span></span> <span data-ttu-id="47f49-121">列名中 `Tag` 值为 `1` 的组将 `Employee` 标识为元素，将 `EmpID` 标识为属性。</span><span class="sxs-lookup"><span data-stu-id="47f49-121">The group that has `Tag` value `1` in the column name identifies `Employee` as an element and `EmpID` as the attribute.</span></span> <span data-ttu-id="47f49-122">另一个列组的列中的 `Tag` 值为 `2`，它将 <`Name`> 标识为元素，将 `FName` 和 `LName` 标识为属性。</span><span class="sxs-lookup"><span data-stu-id="47f49-122">The other column group has `Tag` value `2` in the column and identifies <`Name`> as the element and `FName` and `LName` as the attributes.</span></span>  
  
 <span data-ttu-id="47f49-123">下表显示了查询生成的部分行集：</span><span class="sxs-lookup"><span data-stu-id="47f49-123">The following table shows the partial rowset generated by the query:</span></span>  
  
 `Tag Parent  Employee!1!EmpID Name!2!FName Name!2!LName`  
  
 `--- ------  ---------------- ------------ ------------`  
  
 `1   NULL    1                NULL         NULL`  
  
 `2   1       1                Ken          S??nchez`  
  
 `1   NULL    2                NULL         NULL`  
  
 `2   1       2                Terri        Duffy`  
  
 `1   NULL    3                NULL         NULL`  
  
 `2   1       3                Roberto      Tamburello`  
  
 `...`  
  
 <span data-ttu-id="47f49-124">下面说明了如何处理通用表中的行以生成所得到的 XML 树：</span><span class="sxs-lookup"><span data-stu-id="47f49-124">This is how the rows in the universal table are processed to produce the resulting XML tree:</span></span>  
  
 <span data-ttu-id="47f49-125">第一个行标识 `Tag` 值 `1`。</span><span class="sxs-lookup"><span data-stu-id="47f49-125">The first row identifies `Tag` value `1`.</span></span> <span data-ttu-id="47f49-126">因此，标识了 `Tag` 值为 `1` 的列组 `Employee!1!EmpID`。</span><span class="sxs-lookup"><span data-stu-id="47f49-126">Therefore, the column group that has the `Tag` value `1` is identified, `Employee!1!EmpID`.</span></span> <span data-ttu-id="47f49-127">此列将 `Employee` 标识为元素名称。</span><span class="sxs-lookup"><span data-stu-id="47f49-127">This column identifies `Employee` as the element name.</span></span> <span data-ttu-id="47f49-128">然后，将创建一个带有 `EmpID` 属性的 <`Employee`> 元素。</span><span class="sxs-lookup"><span data-stu-id="47f49-128">An <`Employee`> element is then created that has `EmpID` attributes.</span></span> <span data-ttu-id="47f49-129">将为这些属性分配相应的列值。</span><span class="sxs-lookup"><span data-stu-id="47f49-129">Corresponding column values are assigned to these attributes.</span></span>  
  
 <span data-ttu-id="47f49-130">第二个行具有 `Tag` 值 `2`。</span><span class="sxs-lookup"><span data-stu-id="47f49-130">The second row has the `Tag` value `2`.</span></span> <span data-ttu-id="47f49-131">因此，标识了列名（ `Tag` 和 `2` ）中具有 `Name!2!FName`值 `Name!2!LName`的列组。</span><span class="sxs-lookup"><span data-stu-id="47f49-131">Therefore, the column group that has the `Tag` value `2` in the column name, `Name!2!FName`, `Name!2!LName`, is identified.</span></span> <span data-ttu-id="47f49-132">这些列名将 `Name` 标识为元素名称。</span><span class="sxs-lookup"><span data-stu-id="47f49-132">These column names identify `Name` as element name.</span></span> <span data-ttu-id="47f49-133">将创建一个带有 `FName` 和 `LName` 属性的 <`Name`> 元素。</span><span class="sxs-lookup"><span data-stu-id="47f49-133">A <`Name`> element is created that has `FName` and `LName` attributes.</span></span> <span data-ttu-id="47f49-134">然后，将为这些属性分配相应的列值。</span><span class="sxs-lookup"><span data-stu-id="47f49-134">Corresponding column values are then assigned to these attributes.</span></span> <span data-ttu-id="47f49-135">此行将 `1` 作为 `Parent`标识。</span><span class="sxs-lookup"><span data-stu-id="47f49-135">This row identifies `1` as `Parent`.</span></span> <span data-ttu-id="47f49-136">此子元素将添加到上一个 <`Employee`> 元素。</span><span class="sxs-lookup"><span data-stu-id="47f49-136">This element child is added to the previous <`Employee`> element.</span></span>  
  
 <span data-ttu-id="47f49-137">对于行集中的其余行，重复此过程。</span><span class="sxs-lookup"><span data-stu-id="47f49-137">This process is repeated for rest of the rows in the rowset.</span></span> <span data-ttu-id="47f49-138">请注意，对通用表中的行进行排序很重要，因为这使得 FOR XML EXPLICIT 可以按顺序处理行集并生成所需的 XML。</span><span class="sxs-lookup"><span data-stu-id="47f49-138">Note the importance of ordering the rows in the universal table so that FOR XML EXPLICIT can process the rowset in order and generate the XML you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f49-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47f49-139">See Also</span></span>  
 [<span data-ttu-id="47f49-140">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="47f49-140">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
