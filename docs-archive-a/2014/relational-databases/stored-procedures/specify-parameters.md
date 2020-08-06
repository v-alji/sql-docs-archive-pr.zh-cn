---
title: 指定参数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- stored procedures [SQL Server], parameters
- output parameters [SQL Server]
- input parameters [SQL Server]
ms.assetid: 902314fe-5f9c-4d0d-a0b7-27e67c9c70ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: d93a04281839c4db26cbab16ac166af3cdb7c9a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591850"
---
# <a name="specify-parameters"></a><span data-ttu-id="995a0-102">指定参数</span><span class="sxs-lookup"><span data-stu-id="995a0-102">Specify Parameters</span></span>
  <span data-ttu-id="995a0-103">通过指定过程参数，调用程序可以将值传递给过程的主体。</span><span class="sxs-lookup"><span data-stu-id="995a0-103">By specifying procedure parameters, calling programs are able to pass values into the body of the procedure.</span></span> <span data-ttu-id="995a0-104">在执行过程期间，这些值可以用于各种目的。</span><span class="sxs-lookup"><span data-stu-id="995a0-104">Those values can be used for a variety of purposes during procedure execution.</span></span> <span data-ttu-id="995a0-105">如果将参数标记为 OUTPUT 参数，则过程参数还可以将值返回给调用程序。</span><span class="sxs-lookup"><span data-stu-id="995a0-105">Procedure parameters can also return values to the calling program if the parameter is marked as an OUTPUT parameter.</span></span>  
  
 <span data-ttu-id="995a0-106">一个过程最多可以有 2100 个参数，每个参数都有名称、数据类型和方向。</span><span class="sxs-lookup"><span data-stu-id="995a0-106">A procedure can have a maximum of 2100 parameters; each assigned a name, data type, and direction.</span></span> <span data-ttu-id="995a0-107">还可以为参数指定默认值（可选）。</span><span class="sxs-lookup"><span data-stu-id="995a0-107">Optionally, parameters can be assigned default values.</span></span>  
  
 <span data-ttu-id="995a0-108">下面的章节提供有关将值传递给参数以及在过程调用期间如何使用每个参数属性的信息。</span><span class="sxs-lookup"><span data-stu-id="995a0-108">The following section provides information about passing values into parameters and about how each of the parameter attributes is used during a procedure call.</span></span>  
  
## <a name="passing-values-into-parameters"></a><span data-ttu-id="995a0-109">将值传递给参数</span><span class="sxs-lookup"><span data-stu-id="995a0-109">Passing Values into Parameters</span></span>  
 <span data-ttu-id="995a0-110">使用过程调用提供的参数值必须为常量或变量，不能将函数名称作为参数值。</span><span class="sxs-lookup"><span data-stu-id="995a0-110">The parameter values supplied with a procedure call must be constants or a variable; a function name cannot be used as a parameter value.</span></span> <span data-ttu-id="995a0-111">变量可以是用户定义的变量或系统变量（如 \@\@spid）。</span><span class="sxs-lookup"><span data-stu-id="995a0-111">Variables can be user-defined or system variables such as \@\@spid.</span></span>  
  
 <span data-ttu-id="995a0-112">下列示例演示如何将参数值传递给过程 `uspGetWhereUsedProductID`。</span><span class="sxs-lookup"><span data-stu-id="995a0-112">The following examples demonstrate passing parameter values to the procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="995a0-113">它们说明了如何将参数作为常量和变量进行传递，以及如何使用变量传递函数值。</span><span class="sxs-lookup"><span data-stu-id="995a0-113">They illustrate how to pass parameters as constants and variables and also how to use a variable to pass the value of a function.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Passing values as constants.  
EXEC dbo.uspGetWhereUsedProductID 819, '20050225';  
GO  
-- Passing values as variables.  
DECLARE @ProductID int, @CheckDate datetime;  
SET @ProductID = 819;  
SET @CheckDate = '20050225';  
EXEC dbo.uspGetWhereUsedProductID @ProductID, @CheckDate;  
GO  
-- Try to use a function as a parameter value.  
-- This produces an error message.  
EXEC dbo.uspGetWhereUsedProductID 819, GETDATE();  
GO  
-- Passing the function value as a variable.  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
## <a name="specifying-parameter-names"></a><span data-ttu-id="995a0-114">指定参数名称</span><span class="sxs-lookup"><span data-stu-id="995a0-114">Specifying Parameter Names</span></span>  
 <span data-ttu-id="995a0-115">创建过程并声明参数名时，参数名必须以一个 \@ 字符开头，并且必须在过程范围内是唯一的。</span><span class="sxs-lookup"><span data-stu-id="995a0-115">When creating a procedure and declaring a parameter name, the parameter name must begin with a single \@ character and must be unique in the scope of the procedure.</span></span>  
  
 <span data-ttu-id="995a0-116">显式命名参数并将相应的值赋给过程调用中的每个参数允许按任意顺序提供参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-116">Explicitly naming the parameters and assigning the appropriate values to each parameter in a procedure call allows the parameters to be supplied in any order.</span></span> <span data-ttu-id="995a0-117">例如，如果过程 my_proc 需要使用三个参数，分别名为 \@first、\@second和 \@third，可以将传递到此过程的值赋给参数名，如：`EXECUTE my_proc @second = 2, @first = 1, @third = 3;`</span><span class="sxs-lookup"><span data-stu-id="995a0-117">For example, if the procedure **my_proc** expects three parameters named **\@first**, **\@second**, and **\@third**, the values passed to the procedure can be assigned to the parameter names, such as: `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="995a0-118">如果以 **\@parameter =** _value_ 格式提供参数值，必须按此格式提供所有后续参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-118">If one parameter value is supplied in the form **\@parameter =**_value_, all subsequent parameters must be supplied in this manner.</span></span> <span data-ttu-id="995a0-119">如果未按格式 **\@parameter =** _value_ 传递参数值，必须按 CREATE PROCEDURE 语句中所列参数顺序（从左到右）提供值。</span><span class="sxs-lookup"><span data-stu-id="995a0-119">If the parameter values are not passed in the form **\@parameter =**_value_, the values must be supplied in the identical order (left to right) as the parameters are listed in the CREATE PROCEDURE statement.</span></span>  
> 
> [!WARNING]
>  <span data-ttu-id="995a0-120">任何采用 **\@parameter =** _value_ 格式传入的参数如果拼写错误，就会导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成错误，并阻止过程执行。</span><span class="sxs-lookup"><span data-stu-id="995a0-120">Any parameter passed in the form **\@parameter =**_value_ with the parameter misspelled, will cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate an error and prevent procedure execution.</span></span>  
  
## <a name="specifying-parameter-data-types"></a><span data-ttu-id="995a0-121">指定参数数据类型</span><span class="sxs-lookup"><span data-stu-id="995a0-121">Specifying Parameter Data Types</span></span>  
 <span data-ttu-id="995a0-122">在 CREATE PROCEDURE 语句中声明时，必须使用数据类型定义参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-122">Parameters must be defined with a data type when they are declared in a CREATE PROCEDURE statement.</span></span> <span data-ttu-id="995a0-123">参数的数据类型确定了在调用过程时该参数所接受值的类型和范围。</span><span class="sxs-lookup"><span data-stu-id="995a0-123">The data type of a parameter determines the type and range of values that are accepted for the parameter when the procedure is called.</span></span> <span data-ttu-id="995a0-124">例如，如果用 `tinyint` 数据类型定义参数，则在传入该参数时只接受 0 到 255 之间的数值。</span><span class="sxs-lookup"><span data-stu-id="995a0-124">For example, if you define a parameter with a `tinyint` data type, only numeric values ranging from 0 to 255 are accepted when passed into that parameter.</span></span> <span data-ttu-id="995a0-125">如果用与数据类型不兼容的值执行过程，将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="995a0-125">An error is returned if a procedure is executed with a value incompatible with the data type.</span></span>  
  
## <a name="specifying-parameter-default-values"></a><span data-ttu-id="995a0-126">指定参数的默认值</span><span class="sxs-lookup"><span data-stu-id="995a0-126">Specifying Parameter Default Values</span></span>  
 <span data-ttu-id="995a0-127">如果在声明参数时指定了默认值，则参数被视为可选的。</span><span class="sxs-lookup"><span data-stu-id="995a0-127">A parameter is considered optional if the parameter has a default value specified when it is declared.</span></span> <span data-ttu-id="995a0-128">在过程调用中不需要为可选参数提供值。</span><span class="sxs-lookup"><span data-stu-id="995a0-128">It is not necessary to provide a value for an optional parameter in a procedure call.</span></span>  
  
 <span data-ttu-id="995a0-129">在以下情况下使用参数的默认值：</span><span class="sxs-lookup"><span data-stu-id="995a0-129">The default value of a parameter is used when:</span></span>  
  
-   <span data-ttu-id="995a0-130">在过程调用中未指定参数值。</span><span class="sxs-lookup"><span data-stu-id="995a0-130">No value for the parameter is specified in the procedure call.</span></span>  
  
-   <span data-ttu-id="995a0-131">在过程调用中将 DEFAULT 关键字指定为值。</span><span class="sxs-lookup"><span data-stu-id="995a0-131">The DEFAULT keyword is specified as the value in the procedure call.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="995a0-132">如果默认值是包含嵌入空格或标点符号的字符串，或者以数字开头（例如，6xxx），那么该默认值必须用直的单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="995a0-132">If the default value is a character string that contains embedded blanks or punctuation, or if it starts with a number (for example, 6xxx), it must be enclosed in single, straight quotation marks.</span></span>  
  
 <span data-ttu-id="995a0-133">如果没有合适的值可以指定为参数的默认值，则指定 NULL 为默认值。</span><span class="sxs-lookup"><span data-stu-id="995a0-133">If no value can be specified appropriately as a default for the parameter, specify NULL as the default.</span></span> <span data-ttu-id="995a0-134">如果在未提供参数值的情况下执行过程，最好让过程返回自定义的消息。</span><span class="sxs-lookup"><span data-stu-id="995a0-134">It is a good idea to have the procedure return a customized message if the procedure is executed without a value for the parameter.</span></span>  
  
 <span data-ttu-id="995a0-135">下列示例创建带有一个输入参数 `usp_GetSalesYTD` 的 `@SalesPerson`过程。</span><span class="sxs-lookup"><span data-stu-id="995a0-135">The following example creates the `usp_GetSalesYTD` procedure with one input parameter, `@SalesPerson`.</span></span> <span data-ttu-id="995a0-136">NULL 被指定为该参数的默认值并在错误处理语句中使用，以便在未指定 `@SalesPerson` 参数值的情况下执行过程时返回自定义错误消息。</span><span class="sxs-lookup"><span data-stu-id="995a0-136">NULL is assigned as the default value for the parameter and is used in error handling statements to return a custom error message for cases when the procedure is executed without a value for the `@SalesPerson` parameter.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetSalesYTD  
@SalesPerson nvarchar(50) = NULL  -- NULL default value  
AS   
    SET NOCOUNT ON;   
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
BEGIN  
   PRINT 'ERROR: You must specify the last name of the sales person.'  
   RETURN  
END  
-- Get the sales for the specified sales person and   
-- assign it to the output parameter.  
SELECT SalesYTD  
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="995a0-137">下列示例执行过程。</span><span class="sxs-lookup"><span data-stu-id="995a0-137">The following example executes the procedure.</span></span> <span data-ttu-id="995a0-138">第一个语句执行过程，而未指定输入值。</span><span class="sxs-lookup"><span data-stu-id="995a0-138">The first statement executes the procedure without specifying an input value.</span></span> <span data-ttu-id="995a0-139">这将导致过程中的错误处理语句返回自定义错误消息。</span><span class="sxs-lookup"><span data-stu-id="995a0-139">This causes the error handling statements in the procedure to return the custom error message.</span></span> <span data-ttu-id="995a0-140">第二个语句提供了输入值，所以返回了所需的结果集。</span><span class="sxs-lookup"><span data-stu-id="995a0-140">The second statement supplies an input value and returns the expected result set.</span></span>  
  
```  
-- Run the procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the procedure with an input value.  
EXEC Sales.usp_GetSalesYTD N'Blythe';  
GO  
```  
  
 <span data-ttu-id="995a0-141">虽然可以省略已提供默认值的参数，但只能截断参数列表。</span><span class="sxs-lookup"><span data-stu-id="995a0-141">Although parameters for which defaults have been supplied can be omitted, the list of parameters can only be truncated.</span></span> <span data-ttu-id="995a0-142">例如，如果过程有 5 个参数，可以省略第 4 个和第 5 个参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-142">For example, if a procedure has five parameters, both the fourth and the fifth parameters can be omitted.</span></span> <span data-ttu-id="995a0-143">不过，只要有第 5 个参数，就不能跳过第 4 个参数，除非采用 **\@parameter =** _value_ 格式提供参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-143">However the fourth parameter cannot be skipped as long as the fifth parameter is included, unless the parameters are supplied in the form **\@parameter =**_value_.</span></span>  
  
## <a name="specifying-parameter-direction"></a><span data-ttu-id="995a0-144">指定参数方向</span><span class="sxs-lookup"><span data-stu-id="995a0-144">Specifying Parameter Direction</span></span>  
 <span data-ttu-id="995a0-145">参数的方向可以为输入（表明将值传递给过程的主体），也可以为输出（表明过程将值返回给调用程序）。</span><span class="sxs-lookup"><span data-stu-id="995a0-145">The direction of a parameter is either input, a value is passed into the body of the procedure, or output, the procedure returns a value to the calling program.</span></span> <span data-ttu-id="995a0-146">默认为输入参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-146">The default is an input parameter.</span></span>  
  
 <span data-ttu-id="995a0-147">若要指定输出参数，必须在 CREATE PROCEDURE 语句的参数定义中指定 OUTPUT 关键字。</span><span class="sxs-lookup"><span data-stu-id="995a0-147">To specify an output parameter, the OUTPUT keyword must be specified in the definition of the parameter in the CREATE PROCEDURE statement.</span></span> <span data-ttu-id="995a0-148">当过程退出时，它向调用程序返回输出参数的当前值。</span><span class="sxs-lookup"><span data-stu-id="995a0-148">The procedure returns the current value of the output parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="995a0-149">执行过程时，调用程序也必须使用 OUTPUT 关键字，才能将该参数值保存到可以在调用程序中使用的变量中。</span><span class="sxs-lookup"><span data-stu-id="995a0-149">The calling program must also use the OUTPUT keyword when executing the procedure to save the parameter's value in a variable that can be used in the calling program.</span></span>  
  
 <span data-ttu-id="995a0-150">下面的示例创建了 `Production.usp`_`GetList` 过程，该过程返回价格不超过指定金额的产品的列表。</span><span class="sxs-lookup"><span data-stu-id="995a0-150">The following example creates the `Production.usp`_`GetList` procedure, which returns a list of products that have prices that do not exceed a specified amount.</span></span> <span data-ttu-id="995a0-151">此示例显示如何使用多个 SELECT 语句和多个 OUTPUT 参数。</span><span class="sxs-lookup"><span data-stu-id="995a0-151">The example shows using multiple SELECT statements and multiple OUTPUT parameters.</span></span> <span data-ttu-id="995a0-152">使用 OUTPUT 参数，外部过程、批或多个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句可以访问在过程执行期间设置的值。</span><span class="sxs-lookup"><span data-stu-id="995a0-152">OUTPUT parameters allow an external procedure, a batch, or more than one [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to access a value set during the procedure execution.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Production.uspGetList', 'P' ) IS NOT NULL   
    DROP PROCEDURE Production.uspGetList;  
GO  
CREATE PROCEDURE Production.uspGetList @Product varchar(40)   
    , @MaxPrice money   
    , @ComparePrice money OUTPUT  
    , @ListPrice money OUT  
AS  
    SET NOCOUNT ON;  
    SELECT p.[Name] AS Product, p.ListPrice AS 'List Price'  
    FROM Production.Product AS p  
    JOIN Production.ProductSubcategory AS s   
      ON p.ProductSubcategoryID = s.ProductSubcategoryID  
    WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice;  
-- Populate the output variable @ListPprice.  
SET @ListPrice = (SELECT MAX(p.ListPrice)  
        FROM Production.Product AS p  
        JOIN  Production.ProductSubcategory AS s   
          ON p.ProductSubcategoryID = s.ProductSubcategoryID  
        WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice);  
-- Populate the output variable @compareprice.  
SET @ComparePrice = @MaxPrice;  
GO  
  
```  
  
 <span data-ttu-id="995a0-153">执行 `usp_GetList` 以返回价格低于 $700 的 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 产品（自行车）的列表。</span><span class="sxs-lookup"><span data-stu-id="995a0-153">Execute `usp_GetList` to return a list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] products (Bikes) that cost less than $700.</span></span> <span data-ttu-id="995a0-154">输出参数 \@cost 和 \@compareprices 用于控制流语言，以便在“消息”窗口中返回消息。</span><span class="sxs-lookup"><span data-stu-id="995a0-154">The OUTPUT parameters **\@cost** and **\@compareprices** are used with control-of-flow language to return a message in the **Messages** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="995a0-155">OUTPUT 变量必须在过程创建和变量使用期间进行定义。</span><span class="sxs-lookup"><span data-stu-id="995a0-155">The OUTPUT variable must be defined during the procedure creation and also during the use of the variable.</span></span> <span data-ttu-id="995a0-156">参数名称和变量名称不一定要匹配。</span><span class="sxs-lookup"><span data-stu-id="995a0-156">The parameter name and variable name do not have to match.</span></span> <span data-ttu-id="995a0-157">不过，数据类型和参数定位必须匹配（除非使用的是 \@listprice= _variable_）。</span><span class="sxs-lookup"><span data-stu-id="995a0-157">However, the data type and parameter positioning must match (unless **\@listprice=** _variable_ is used).</span></span>  
  
```  
DECLARE @ComparePrice money, @Cost money ;  
EXECUTE Production.uspGetList '%Bikes%', 700,   
    @ComparePrice OUT,   
    @Cost OUTPUT  
IF @Cost <= @ComparePrice   
BEGIN  
    PRINT 'These products can be purchased for less than   
    $'+RTRIM(CAST(@ComparePrice AS varchar(20)))+'.'  
END  
ELSE  
    PRINT 'The prices for all products in this category exceed   
    $'+ RTRIM(CAST(@ComparePrice AS varchar(20)))+'.';  
  
```  
  
 <span data-ttu-id="995a0-158">下面是部分结果集：</span><span class="sxs-lookup"><span data-stu-id="995a0-158">Here is the partial result set:</span></span>  
  
```  
Product                                            List Price  
-------------------------------------------------- ------------------  
Road-750 Black, 58                                 539.99  
Mountain-500 Silver, 40                            564.99  
Mountain-500 Silver, 42                            564.99  
...  
Road-750 Black, 48                                 539.99  
Road-750 Black, 52                                 539.99  
  
(14 row(s) affected)  
  
These items can be purchased for less than $700.00.  
```  
  
## <a name="see-also"></a><span data-ttu-id="995a0-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="995a0-159">See Also</span></span>  
 [<span data-ttu-id="995a0-160">CREATE PROCEDURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="995a0-160">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
