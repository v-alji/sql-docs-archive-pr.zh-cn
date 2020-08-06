---
title: 创建用户定义函数（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
author: rothja
ms.author: jroth
ms.openlocfilehash: 790fa1b969f933890e050311173fcde3f12c37ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590608"
---
# <a name="create-user-defined-functions-database-engine"></a><span data-ttu-id="1cdb9-102">创建用户定义函数（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="1cdb9-102">Create User-defined Functions (Database Engine)</span></span>
  <span data-ttu-id="1cdb9-103">本主题介绍了如何通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中创建用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-103">This topic describes how to create a user-defined function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1cdb9-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1cdb9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1cdb9-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1cdb9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1cdb9-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1cdb9-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1cdb9-107">安全性</span><span class="sxs-lookup"><span data-stu-id="1cdb9-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1cdb9-108">**创建用户定义函数：**</span><span class="sxs-lookup"><span data-stu-id="1cdb9-108">**To create a user-defined function:**</span></span>  
  
     [<span data-ttu-id="1cdb9-109">创建标量函数</span><span class="sxs-lookup"><span data-stu-id="1cdb9-109">Create a Scalar Function</span></span>](#Scalar)  
  
     [<span data-ttu-id="1cdb9-110">创建表值函数</span><span class="sxs-lookup"><span data-stu-id="1cdb9-110">Create a Table-valued Function</span></span>](#TVF)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1cdb9-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="1cdb9-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1cdb9-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1cdb9-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1cdb9-113">用户定义函数不能用于执行修改数据库状态的操作。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-113">User-defined functions cannot be used to perform actions that modify the database state.</span></span>  
  
-   <span data-ttu-id="1cdb9-114">用户定义函数不能包含将表作为其目标的 OUTPUT INTO 子句。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-114">User-defined functions cannot contain an OUTPUT INTO clause that has a table as its target.</span></span>  
  
-   <span data-ttu-id="1cdb9-115">用户定义函数不能返回多个结果集。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-115">User-defined functions can not return multiple result sets.</span></span> <span data-ttu-id="1cdb9-116">如果您需要返回多个结果集，请使用存储过程。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-116">Use a stored procedure if you need to return multiple result sets.</span></span>  
  
-   <span data-ttu-id="1cdb9-117">在用户定义函数中，错误处理受限制。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-117">Error handling is restricted in a user-defined function.</span></span> <span data-ttu-id="1cdb9-118">UDF 不支持 TRY .。。CATCH @ERROR 或 RAISERROR。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-118">A UDF does not support TRY...CATCH, @ERROR or RAISERROR.</span></span>  
  
-   <span data-ttu-id="1cdb9-119">用户定义函数不能调用存储过程，但是可调用扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-119">User-defined functions cannot call a stored procedure, but can call an extended stored procedure.</span></span>  
  
-   <span data-ttu-id="1cdb9-120">用户定义函数不能使用动态 SQL 或临时表。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-120">User-defined functions cannot make use of dynamic SQL or temp tables.</span></span> <span data-ttu-id="1cdb9-121">允许表变量。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-121">Table variables are allowed.</span></span>  
  
-   <span data-ttu-id="1cdb9-122">在用户定义函数中不允许 SET 语句。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-122">SET statements are not allowed in a user-defined function.</span></span>  
  
-   <span data-ttu-id="1cdb9-123">不允许 FOR XML 子句</span><span class="sxs-lookup"><span data-stu-id="1cdb9-123">The FOR XML clause is not allowed</span></span>  
  
-   <span data-ttu-id="1cdb9-124">用户定义函数可以嵌套；也就是说，用户定义函数可相互调用。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-124">User-defined functions can be nested; that is, one user-defined function can call another.</span></span> <span data-ttu-id="1cdb9-125">被调用函数开始执行时，嵌套级别将增加；被调用函数执行结束后，嵌套级别将减少。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-125">The nesting level is incremented when the called function starts execution, and decremented when the called function finishes execution.</span></span> <span data-ttu-id="1cdb9-126">用户定义函数的嵌套级别最多可达 32 级。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-126">User-defined functions can be nested up to 32 levels.</span></span> <span data-ttu-id="1cdb9-127">如果超出最大嵌套级别数，整个调用函数链将失败。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-127">Exceeding the maximum levels of nesting causes the whole calling function chain to fail.</span></span> <span data-ttu-id="1cdb9-128">从 Transact-SQL 用户定义函数对托管代码的任何引用都将根据 32 级嵌套限制计入一个级别。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-128">Any reference to managed code from a Transact-SQL user-defined function counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="1cdb9-129">从托管代码内部调用的方法不根据此限制进行计数。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-129">Methods invoked from within managed code do not count against this limit.</span></span>  
  
-   <span data-ttu-id="1cdb9-130">下列 Service Broker 语句不能包含在 Transact-SQL 用户定义函数的定义中：</span><span class="sxs-lookup"><span data-stu-id="1cdb9-130">The following Service Broker statements cannot be included in the definition of a Transact-SQL user-defined function:</span></span>  
  
    -   <span data-ttu-id="1cdb9-131">BEGIN DIALOG CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="1cdb9-131">BEGIN DIALOG CONVERSATION</span></span>  
  
    -   <span data-ttu-id="1cdb9-132">END CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="1cdb9-132">END CONVERSATION</span></span>  
  
    -   <span data-ttu-id="1cdb9-133">GET CONVERSATION GROUP</span><span class="sxs-lookup"><span data-stu-id="1cdb9-133">GET CONVERSATION GROUP</span></span>  
  
    -   <span data-ttu-id="1cdb9-134">MOVE CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="1cdb9-134">MOVE CONVERSATION</span></span>  
  
    -   <span data-ttu-id="1cdb9-135">RECEIVE</span><span class="sxs-lookup"><span data-stu-id="1cdb9-135">RECEIVE</span></span>  
  
    -   <span data-ttu-id="1cdb9-136">SEND</span><span class="sxs-lookup"><span data-stu-id="1cdb9-136">SEND</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1cdb9-137">Security</span><span class="sxs-lookup"><span data-stu-id="1cdb9-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1cdb9-138">权限</span><span class="sxs-lookup"><span data-stu-id="1cdb9-138">Permissions</span></span>  
 <span data-ttu-id="1cdb9-139">需要在数据库中具有 CREATE FUNCTION 权限，并对创建函数时所在的架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-139">Requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span> <span data-ttu-id="1cdb9-140">如果函数指定用户定义类型，则需要对该类型具有 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-140">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="scalar-functions"></a><a name="Scalar"></a><span data-ttu-id="1cdb9-141">标量函数</span><span class="sxs-lookup"><span data-stu-id="1cdb9-141">Scalar Functions</span></span>  
 <span data-ttu-id="1cdb9-142">下面的示例在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中创建一个多语句标量函数。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-142">The following example creates a multistatement scalar function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1cdb9-143">此函数输入一个值 `ProductID`，而返回一个单个数据值（指定库存产品的聚合量）。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-143">The function takes one input value, a `ProductID`, and returns a single data value, the aggregated quantity of the specified product in inventory.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END;  
GO  
  
```  
  
 <span data-ttu-id="1cdb9-144">下例使用 `ufnGetInventoryStock` 函数返回 `ProductModelID` 介于 75 和 80 之间的产品的当前库存量。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-144">The following example uses the `ufnGetInventoryStock` function to return the current inventory quantity for products that have a `ProductModelID` between 75 and 80.</span></span>  
  
```  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
  
```  
  
##  <a name="table-valued-functions"></a><a name="TVF"></a><span data-ttu-id="1cdb9-145">表值函数</span><span class="sxs-lookup"><span data-stu-id="1cdb9-145">Table-Valued Functions</span></span>  
 <span data-ttu-id="1cdb9-146">下面的示例在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中创建内联表值函数。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-146">The following example creates an inline table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1cdb9-147">此函数的输入参数为客户（商店）ID，而返回 `ProductID`、 `Name`以及 `YTD Total` （销售到商店的每种产品的本年度节截止到现在的销售总额）列。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-147">The function takes one input parameter, a customer (store) ID, and returns the columns `ProductID`, `Name`, and the aggregate of year-to-date sales as `YTD Total` for each product sold to the store.</span></span>  
  
```  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
  
```  
  
 <span data-ttu-id="1cdb9-148">下面的示例调用此函数并指定客户 ID 为 602。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-148">The following example invokes the function and specifies customer ID 602.</span></span>  
  
```  
SELECT * FROM Sales.ufn_SalesByStore (602);  
  
```  
  
 <span data-ttu-id="1cdb9-149">下面的示例在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中创建表值函数。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-149">The following example creates a table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1cdb9-150">此函数具有一个输入参数 `EmployeeID` ，它返回直接或间接向指定员工报告的所有员工的列表。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-150">The function takes a single input parameter, an `EmployeeID` and returns a list of all the employees who report to the specified employee directly or indirectly.</span></span> <span data-ttu-id="1cdb9-151">然后在指定雇员 ID 109 的情况下调用此函数。</span><span class="sxs-lookup"><span data-stu-id="1cdb9-151">The function is then invoked specifying employee ID 109.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cdb9-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1cdb9-152">See Also</span></span>  
 <span data-ttu-id="1cdb9-153">[用户定义函数](user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="1cdb9-153">[User-Defined Functions](user-defined-functions.md) </span></span>  
 [<span data-ttu-id="1cdb9-154">CREATE FUNCTION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1cdb9-154">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
