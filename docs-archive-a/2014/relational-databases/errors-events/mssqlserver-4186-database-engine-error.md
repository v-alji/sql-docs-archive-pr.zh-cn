---
title: MSSQLSERVER_4186 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4186 (Database Engine error)
ms.assetid: 1ae88554-f291-45bc-a186-6f41d9cd0fca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525c1c3bd6e631044b8bc7f17b2c2a01aeb1ef8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577716"
---
# <a name="mssqlserver_4186"></a><span data-ttu-id="d7fae-102">MSSQLSERVER_4186</span><span class="sxs-lookup"><span data-stu-id="d7fae-102">MSSQLSERVER_4186</span></span>
    
## <a name="details"></a><span data-ttu-id="d7fae-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d7fae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7fae-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d7fae-104">Product Name</span></span>|<span data-ttu-id="d7fae-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7fae-105">SQL Server</span></span>|  
|<span data-ttu-id="d7fae-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d7fae-106">Event ID</span></span>|<span data-ttu-id="d7fae-107">4186</span><span class="sxs-lookup"><span data-stu-id="d7fae-107">4186</span></span>|  
|<span data-ttu-id="d7fae-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d7fae-108">Event Source</span></span>|<span data-ttu-id="d7fae-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7fae-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7fae-110">组件</span><span class="sxs-lookup"><span data-stu-id="d7fae-110">Component</span></span>|<span data-ttu-id="d7fae-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7fae-111">SQLEngine</span></span>|  
|<span data-ttu-id="d7fae-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d7fae-112">Symbolic Name</span></span>||  
|<span data-ttu-id="d7fae-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="d7fae-113">Message Text</span></span>|<span data-ttu-id="d7fae-114">无法在 OUTPUT 子句中引用列 '%ls.%.\*ls'，因为该列的定义中包含一个子查询或者引用一个执行用户或系统数据访问的函数。</span><span class="sxs-lookup"><span data-stu-id="d7fae-114">Column '%ls.%.\*ls' cannot be referenced in the OUTPUT clause because the column definition contains a subquery or references a function that performs user or system data access.</span></span> <span data-ttu-id="d7fae-115">默认情况下，如果函数未绑定到架构，则会认为该函数执行数据访问。</span><span class="sxs-lookup"><span data-stu-id="d7fae-115">A function is assumed by default to perform data access if it is not schemabound.</span></span> <span data-ttu-id="d7fae-116">请考虑从列定义中删除子查询或函数，或者从 OUTPUT 子句中删除该列。</span><span class="sxs-lookup"><span data-stu-id="d7fae-116">Consider removing the subquery or function from the column definition or removing the column from the OUTPUT clause.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7fae-117">说明</span><span class="sxs-lookup"><span data-stu-id="d7fae-117">Explanation</span></span>  
 <span data-ttu-id="d7fae-118">为了防止出现不确定的行为，当某个列是通过下列方法之一定义时，OUTPUT 子句不能通过视图或内联表值函数引用该列：</span><span class="sxs-lookup"><span data-stu-id="d7fae-118">To prevent nondeterministic behavior, the OUTPUT clause cannot reference a column from a view or inline table-valued function when that column is defined by one of the following methods:</span></span>  
  
-   <span data-ttu-id="d7fae-119">子查询。</span><span class="sxs-lookup"><span data-stu-id="d7fae-119">A subquery.</span></span>  
  
-   <span data-ttu-id="d7fae-120">执行用户数据访问或系统数据访问或者被认为执行此种访问的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="d7fae-120">A user-defined function that performs user or system data access, or is assumed to perform such access.</span></span>  
  
-   <span data-ttu-id="d7fae-121">定义中包含执行用户数据访问或系统数据访问的用户定义函数的计算列。</span><span class="sxs-lookup"><span data-stu-id="d7fae-121">A computed column that contains a user-defined function that performs user or system data access in its definition.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d7fae-122">示例</span><span class="sxs-lookup"><span data-stu-id="d7fae-122">Examples</span></span>  
 <span data-ttu-id="d7fae-123">**子查询定义的视图列**</span><span class="sxs-lookup"><span data-stu-id="d7fae-123">**View Column Defined by a Subquery**</span></span>  
  
 <span data-ttu-id="d7fae-124">以下示例创建使用选择列表中的子查询定义 `State` 列的视图。</span><span class="sxs-lookup"><span data-stu-id="d7fae-124">The following example creates a view that uses a subquery in the select list to define the column `State`.</span></span> <span data-ttu-id="d7fae-125">然后，UPDATE 语句在 OUTPUT 子句中引用 `State` 列，并且因为选择列表中的子查询而失败。</span><span class="sxs-lookup"><span data-stu-id="d7fae-125">An UPDATE statement then references the `State` column in the OUTPUT clause and fails because ob the subquery in the select list.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.V1  
AS  
    SELECT City,  
-- subquery to return the State name  
           (SELECT Name FROM Person.StateProvince AS sp   
            WHERE sp.StateProvinceID = a.StateProvinceID) AS State  
    FROM Person.Address AS a;  
GO  
--Reference the State column in the OUTPUT clause of an UPDATE statement  
UPDATE dbo.V1   
SET City = City + 'Test'   
OUTPUT deleted.City, deleted.State, inserted.City, inserted.State  
WHERE State = 'Texas';  
GO  
```  
  
 <span data-ttu-id="d7fae-126">**函数定义的视图列**</span><span class="sxs-lookup"><span data-stu-id="d7fae-126">**View Column Defined by a Function**</span></span>  
  
 <span data-ttu-id="d7fae-127">以下示例创建使用选择列表中的 `dbo.ufnGetStock` 数据访问标量函数定义 `CurrentInventory` 列的视图。</span><span class="sxs-lookup"><span data-stu-id="d7fae-127">The following example creates a view that uses the data accessing, scalar function `dbo.ufnGetStock` in the select list to define the column `CurrentInventory`.</span></span> <span data-ttu-id="d7fae-128">然后，UPDATE 语句在 OUTPUT 子句中引用此 `CurrentInventory` 列。</span><span class="sxs-lookup"><span data-stu-id="d7fae-128">An UPDATE statement then references the `CurrentInventory` column in the OUTPUT clause .</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ReorderLevels  
AS  
    SELECT ProductID, ProductModelID, ReorderPoint,  
           dbo.ufnGetStock(ProductID) AS CurrentInventory  
    FROM Production.Product;  
GO  
  
UPDATE Production.ReorderLevels  
SET ReorderPoint += CurrentInventory  
OUTPUT deleted.ReorderPoint, deleted.CurrentInventory,  
       inserted.ReorderPoint, inserted.CurrentInventory  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
## <a name="user-action"></a><span data-ttu-id="d7fae-129">用户操作</span><span class="sxs-lookup"><span data-stu-id="d7fae-129">User Action</span></span>  
 <span data-ttu-id="d7fae-130">若要更正 4186 错误，可以使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="d7fae-130">Error 4186 can be corrected in one of the following ways:</span></span>  
  
-   <span data-ttu-id="d7fae-131">使用联接（而不是子查询）定义视图或函数中的列。</span><span class="sxs-lookup"><span data-stu-id="d7fae-131">Use joins instead of subqueries to define the column in the view or function.</span></span> <span data-ttu-id="d7fae-132">例如，您可以重写 `dbo.V1` 视图，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d7fae-132">For example, you can rewrite the view `dbo.V1` as follows.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE VIEW dbo.V1  
    AS  
        SELECT City, sp.Name AS State  
        FROM Person.Address AS a   
        JOIN Person.StateProvince AS sp   
        ON sp.StateProvinceID = a.StateProvinceID;  
    ```  
  
-   <span data-ttu-id="d7fae-133">检查用户定义函数的定义。</span><span class="sxs-lookup"><span data-stu-id="d7fae-133">Examine the definition of the user-defined function.</span></span> <span data-ttu-id="d7fae-134">如果函数未执行用户数据访问或系统数据访问，请更改此函数，使其包含 WITH SCHEMABINDING 子句。</span><span class="sxs-lookup"><span data-stu-id="d7fae-134">If the function does not perform user or system data access, alter the function to include the WITH SCHEMABINDING clause.</span></span>  
  
-   <span data-ttu-id="d7fae-135">从 OUTPUT 子句中删除列。</span><span class="sxs-lookup"><span data-stu-id="d7fae-135">Remove the column from the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fae-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7fae-136">See Also</span></span>  
 [<span data-ttu-id="d7fae-137">OUTPUT 子句 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d7fae-137">OUTPUT Clause &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/output-clause-transact-sql)  
  
  
