---
title: 从存储过程返回数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], returning data
- returning data from stored procedure
ms.assetid: 7a428ffe-cd87-4f42-b3f1-d26aa8312bf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 472ca5cf27f7e7ea2b18daa961c19faadcf2251f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591851"
---
# <a name="return-data-from-a-stored-procedure"></a><span data-ttu-id="d9d1d-102">从存储过程中返回数据</span><span class="sxs-lookup"><span data-stu-id="d9d1d-102">Return Data from a Stored Procedure</span></span>
  <span data-ttu-id="d9d1d-103">有两种方法可以将结果集或数据从过程返回给调用程序：输出参数和返回代码。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-103">There are two ways of returning result sets or data from a procedure to a calling program: output parameters and return codes.</span></span> <span data-ttu-id="d9d1d-104">本主题提供了有关这两种方法的信息。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-104">This topic provides information on both approaches.</span></span>  
  
## <a name="returning-data-using-an-output-parameter"></a><span data-ttu-id="d9d1d-105">使用输出参数返回数据</span><span class="sxs-lookup"><span data-stu-id="d9d1d-105">Returning Data Using an Output Parameter</span></span>  
 <span data-ttu-id="d9d1d-106">如果在过程定义中为参数指定 OUTPUT 关键字，则过程在退出时可将该参数的当前值返回给调用程序。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-106">If you specify the OUTPUT keyword for a parameter in the procedure definition, the procedure can return the current value of the parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="d9d1d-107">若要将参数值保存在可在调用程序中使用的变量中，调用程序在执行过程时必须使用 OUTPUT 关键字。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-107">To save the value of the parameter in a variable that can be used in the calling program, the calling program must use the OUTPUT keyword when executing the procedure.</span></span> <span data-ttu-id="d9d1d-108">有关可用作输出参数的数据类型的详细信息，请参阅 [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-108">For more information about what data types can be used as output parameters, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
### <a name="examples-of-output-parameter"></a><span data-ttu-id="d9d1d-109">输出参数的示例</span><span class="sxs-lookup"><span data-stu-id="d9d1d-109">Examples of Output Parameter</span></span>  
 <span data-ttu-id="d9d1d-110">以下示例显示有一个输入参数和一个输出参数的过程。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-110">The following example shows a procedure with an input and an output parameter.</span></span> <span data-ttu-id="d9d1d-111">`@SalesPerson` 参数将接收由调用程序指定的输入值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-111">The `@SalesPerson` parameter would receive an input value specified by the calling program.</span></span> <span data-ttu-id="d9d1d-112">SELECT 语句使用传递给输入参数的值来获取正确的 `SalesYTD` 值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-112">The SELECT statement uses the value passed into the input parameter to obtain the correct `SalesYTD` value.</span></span> <span data-ttu-id="d9d1d-113">SELECT 语句还将该值赋给 `@SalesYTD` 输出参数，该参数在过程退出时将值返回给调用程序。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-113">The SELECT statement also assigns the value to the `@SalesYTD` output parameter, which returns the value to the calling program when the procedure exits.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetEmployeeSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetEmployeeSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetEmployeeSalesYTD  
@SalesPerson nvarchar(50),  
@SalesYTD money OUTPUT  
AS    
  
    SET NOCOUNT ON;  
    SELECT @SalesYTD = SalesYTD  
    FROM Sales.SalesPerson AS sp  
    JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
    WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="d9d1d-114">以下示例调用在第一个示例中创建的过程并将从调用的过程返回的输出值保存在 `@SalesYTD` 变量中，该变量是调用程序的局部变量。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-114">The following example calls the procedure created in the first example and saves the output value returned from the called procedure in the `@SalesYTD` variable, which is local to the calling program.</span></span>  
  
```  
-- Declare the variable to receive the output value of the procedure.  
DECLARE @SalesYTDBySalesPerson money;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTDBySalesPerson  
EXECUTE Sales.uspGetEmployeeSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDBySalesPerson OUTPUT;  
-- Display the value returned by the procedure.  
PRINT 'Year-to-date sales for this employee is ' +   
    convert(varchar(10),@SalesYTDBySalesPerson);  
GO  
  
```  
  
 <span data-ttu-id="d9d1d-115">也可以在执行过程时为 OUTPUT 参数指定输入值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-115">Input values can also be specified for OUTPUT parameters when the procedure is executed.</span></span> <span data-ttu-id="d9d1d-116">这将允许过程从调用程序接收值，使用该值更改或执行操作，然后将新值返回给调用程序。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-116">This allows the procedure to receive a value from the calling program, change or perform operations with the value, and then return the new value to the calling program.</span></span> <span data-ttu-id="d9d1d-117">在上一个示例中，可以在程序调用 `@SalesYTDBySalesPerson` 过程前为 `Sales.uspGetEmployeeSalesYTD` 变量赋值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-117">In the previous example, the `@SalesYTDBySalesPerson` variable can be assigned a value before the program calls the `Sales.uspGetEmployeeSalesYTD` procedure.</span></span> <span data-ttu-id="d9d1d-118">execute 语句将 `@SalesYTDBySalesPerson` 变量值传递给 `@SalesYTD` OUTPUT 参数。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-118">The execute statement would pass the `@SalesYTDBySalesPerson` variable value into the `@SalesYTD` OUTPUT parameter.</span></span> <span data-ttu-id="d9d1d-119">然后，在过程主体中，可以将该值用于生成新值的计算。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-119">Then in the procedure body, the value could be used for calculations that generate a new value.</span></span> <span data-ttu-id="d9d1d-120">新值可以通过 OUTPUT 参数重新从过程传回，在过程退出时更新 `@SalesYTDBySalesPerson` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-120">The new value would be passed back out of the procedure through the OUTPUT parameter, updating the value in the `@SalesYTDBySalesPerson` variable when the procedure exits.</span></span> <span data-ttu-id="d9d1d-121">这常常被称作“传址调用功能”。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-121">This is often referred to as "pass-by-reference capability."</span></span>  
  
 <span data-ttu-id="d9d1d-122">如果在调用过程时为参数指定 OUTPUT，而在过程定义中该参数又不是用 OUTPUT 定义的，那么将收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-122">If you specify OUTPUT for a parameter when you call a procedure and that parameter is not defined by using OUTPUT in the procedure definition, you get an error message.</span></span> <span data-ttu-id="d9d1d-123">但是，在执行过程时，可以执行带有输出参数的过程而不指定 OUTPUT。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-123">However, you can execute a procedure with output parameters and not specify OUTPUT when executing the procedure.</span></span> <span data-ttu-id="d9d1d-124">这样不会返回错误，但将无法在调用程序中使用输出值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-124">No error is returned, but you cannot use the output value in the calling program.</span></span>  
  
### <a name="using-the-cursor-data-type-in-output-parameters"></a><span data-ttu-id="d9d1d-125">在 OUTPUT 参数中使用 cursor 数据类型</span><span class="sxs-lookup"><span data-stu-id="d9d1d-125">Using the Cursor Data Type in OUTPUT Parameters</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]<span data-ttu-id="d9d1d-126">过程只能将 `cursor` 数据类型用于 OUTPUT 参数。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-126">procedures can use the `cursor` data type only for OUTPUT parameters.</span></span> <span data-ttu-id="d9d1d-127">如果为 `cursor` 参数指定了数据类型，则必须在过程定义中为该参数指定不同和输出关键字。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-127">If the `cursor` data type is specified for a parameter, both the VARYING and OUTPUT keywords must be specified for that parameter in the procedure definition.</span></span> <span data-ttu-id="d9d1d-128">参数只能指定为 OUTPUT，但如果在参数声明中指定了不同的关键字，则数据类型必须为 `cursor` ，还必须指定 OUTPUT 关键字。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-128">A parameter can be specified as only OUTPUT but if the VARYING keyword is specified in the parameter declaration, the data type must be `cursor` and the OUTPUT keyword must also be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9d1d-129">`cursor` 数据类型不能通过数据库 API（例如 OLE DB、ODBC、ADO 和 DB-Library）绑定到应用程序变量上。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-129">The `cursor` data type cannot be bound to application variables through the database APIs such as OLE DB, ODBC, ADO, and DB-Library.</span></span> <span data-ttu-id="d9d1d-130">因为必须先绑定 OUTPUT 参数，应用程序才可以执行过程，所以带有 `cursor` OUTPUT 参数的过程不能通过数据库 API 调用。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-130">Because OUTPUT parameters must be bound before an application can execute a procedure, procedures with `cursor` OUTPUT parameters cannot be called from the database APIs.</span></span> <span data-ttu-id="d9d1d-131">只有将 `cursor` OUTPUT 变量分配给 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 局部 `cursor` 变量时，才可以通过 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 批处理、过程或触发器调用这些过程。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-131">These procedures can be called from [!INCLUDE[tsql](../../../includes/tsql-md.md)] batches, procedures, or triggers only when the `cursor` OUTPUT variable is assigned to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] local `cursor` variable.</span></span>  
  
### <a name="rules-for-cursor-output-parameters"></a><span data-ttu-id="d9d1d-132">cursor 输出参数的规则</span><span class="sxs-lookup"><span data-stu-id="d9d1d-132">Rules for Cursor Output Parameters</span></span>  
 <span data-ttu-id="d9d1d-133">在执行过程时，以下规则适用于 `cursor` 输出参数：</span><span class="sxs-lookup"><span data-stu-id="d9d1d-133">The following rules pertain to `cursor` output parameters when the procedure is executed:</span></span>  
  
-   <span data-ttu-id="d9d1d-134">对于只进游标，游标的结果集中返回的行只是那些过程执行结束时处于或超出游标位置的行，例如：</span><span class="sxs-lookup"><span data-stu-id="d9d1d-134">For a forward-only cursor, the rows returned in the cursor's result set are only those rows at and beyond the position of the cursor at the conclusion of the procedure execution, for example:</span></span>  
  
    -   <span data-ttu-id="d9d1d-135">在过程中的名为 RS 的 100 行结果集上打开一个非滚动游标。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-135">A nonscrollable cursor is opened in a procedure on a result set named RS of 100 rows.</span></span>  
  
    -   <span data-ttu-id="d9d1d-136">过程提取结果集 RS 的头 5 行。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-136">The procedure fetches the first 5 rows of result set RS.</span></span>  
  
    -   <span data-ttu-id="d9d1d-137">过程返回到其调用者。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-137">The procedure returns to its caller.</span></span>  
  
    -   <span data-ttu-id="d9d1d-138">返回到调用者的结果集 RS 由 RS 的第 6 到 100 行组成，调用者中的游标处于 RS 的第一行之前。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-138">The result set RS returned to the caller consists of rows from 6 through 100 of RS, and the cursor in the caller is positioned before the first row of RS.</span></span>  
  
-   <span data-ttu-id="d9d1d-139">对于只进游标，如果过程退出时游标位于第一行的前面，则整个结果集将返回给调用批处理、过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-139">For a forward-only cursor, if the cursor is positioned before the first row when the procedure exits, the entire result set is returned to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="d9d1d-140">返回时，游标将位于第一行的前面。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-140">When returned, the cursor position is set before the first row.</span></span>  
  
-   <span data-ttu-id="d9d1d-141">对于只进游标，如果过程退出时游标的位置超出最后一行的结尾，则为调用批处理、过程或触发器返回空结果集。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-141">For a forward-only cursor, if the cursor is positioned beyond the end of the last row when the procedure exits, an empty result set is returned to the calling batch, procedure, or trigger.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9d1d-142">空结果集与空值不同。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-142">An empty result set is not the same as a null value.</span></span>  
  
-   <span data-ttu-id="d9d1d-143">对于可滚动游标，在过程退出时，结果集中的所有行均会返回给调用批处理、过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-143">For a scrollable cursor, all the rows in the result set are returned to the calling batch, procedure, or trigger when the procedure exits.</span></span> <span data-ttu-id="d9d1d-144">返回时，游标保留在过程中最后一次执行提取时的位置。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-144">When returned, the cursor position is left at the position of the last fetch executed in the procedure.</span></span>  
  
-   <span data-ttu-id="d9d1d-145">对于任意类型的游标，如果游标关闭，则将 Null 值传递回调用批处理、过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-145">For any type of cursor, if the cursor is closed, then a null value is passed back to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="d9d1d-146">如果将游标指派给一个参数，但该游标从未打开过，也会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-146">This will also be the case if a cursor is assigned to a parameter, but that cursor is never opened.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9d1d-147">关闭状态只有在返回时才有影响。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-147">The closed state matters only at return time.</span></span> <span data-ttu-id="d9d1d-148">例如，可以在过程中关闭游标，稍后再打开游标，然后将该游标的结果集返回给调用批处理、过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-148">For example, it is valid to close a cursor part of the way through the procedure, to open it again later in the procedure, and return that cursor's result set to the calling batch, procedure, or trigger.</span></span>  
  
### <a name="examples-of-cursor-output-parameters"></a><span data-ttu-id="d9d1d-149">cursor 输出参数的示例</span><span class="sxs-lookup"><span data-stu-id="d9d1d-149">Examples of Cursor Output Parameters</span></span>  
 <span data-ttu-id="d9d1d-150">在下面的示例中，创建了 `@currency` `cursor` 使用数据类型指定输出参数 _ 的过程 `cursor` 。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-150">In the following example, a procedure is created that specified an output parameter, `@currency`_`cursor` using the `cursor` data type.</span></span> <span data-ttu-id="d9d1d-151">然后在批处理中调用该过程。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-151">The procedure is then called in a batch.</span></span>  
  
 <span data-ttu-id="d9d1d-152">首先，创建以下过程，在 Currency 表上声明并打开一个游标。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-152">First, create the procedure that declares and then opens a cursor on the Currency table.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspCurrencyCursor', 'P' ) IS NOT NULL  
    DROP PROCEDURE dbo.uspCurrencyCursor;  
GO  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
  
```  
  
 <span data-ttu-id="d9d1d-153">接下来，执行一个批处理，声明一个局部游标变量，执行上述过程以将游标赋值给局部变量，然后从该游标提取行。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-153">Next, execute a batch that declares a local cursor variable, executes the procedure to assign the cursor to the local variable, and then fetches the rows from the cursor.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
  
```  
  
## <a name="returning-data-using-a-return-code"></a><span data-ttu-id="d9d1d-154">使用返回代码返回数据</span><span class="sxs-lookup"><span data-stu-id="d9d1d-154">Returning Data Using a Return Code</span></span>  
 <span data-ttu-id="d9d1d-155">过程可以返回一个整数值（称为“返回代码”），以指示过程的执行状态。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-155">A procedure can return an integer value called a return code to indicate the execution status of a procedure.</span></span> <span data-ttu-id="d9d1d-156">使用 RETURN 语句指定过程的返回代码。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-156">You specify the return code for a procedure using the RETURN statement.</span></span> <span data-ttu-id="d9d1d-157">与 OUTPUT 参数一样，执行过程时必须将返回代码保存到变量中，才能在调用程序中使用返回代码值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-157">As with OUTPUT parameters, you must save the return code in a variable when the procedure is executed in order to use the return code value in the calling program.</span></span> <span data-ttu-id="d9d1d-158">例如，数据类型的赋值变量 `@result` `int` 用于存储来自过程的返回代码 `my_proc` ，如：</span><span class="sxs-lookup"><span data-stu-id="d9d1d-158">For example, the assignment variable `@result` of data type `int` is used to store the return code from the procedure `my_proc`, such as:</span></span>  
  
```  
DECLARE @result int;  
EXECUTE @result = my_proc;  
```  
  
 <span data-ttu-id="d9d1d-159">返回代码通常用在过程内的控制流块中，以便为每种可能的错误情况设置返回代码值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-159">Return codes are commonly used in control-of-flow blocks within procedures to set the return code value for each possible error situation.</span></span> <span data-ttu-id="d9d1d-160">可以在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句后使用 @@ERROR 函数，来检测该语句执行过程中是否有错误发生。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-160">You can use the @@ERROR function after a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to detect whether an error occurred during the execution of the statement.</span></span>  
  
### <a name="examples-of-return-codes"></a><span data-ttu-id="d9d1d-161">返回代码的示例</span><span class="sxs-lookup"><span data-stu-id="d9d1d-161">Examples of Return Codes</span></span>  
 <span data-ttu-id="d9d1d-162">下面的示例显示了带有错误处理设置（为各种错误设置特殊返回代码值）的 `usp_GetSalesYTD` 过程。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-162">The following example shows the `usp_GetSalesYTD` procedure with error handling that sets special return code values for various errors.</span></span> <span data-ttu-id="d9d1d-163">下表显示了由过程分配给每个可能错误的整数值，以及每个值的相应含义。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-163">The following table shows the integer value that is assigned by the procedure to each possible error, and the corresponding meaning for each value.</span></span>  
  
|<span data-ttu-id="d9d1d-164">返回代码值</span><span class="sxs-lookup"><span data-stu-id="d9d1d-164">Return code value</span></span>|<span data-ttu-id="d9d1d-165">含义</span><span class="sxs-lookup"><span data-stu-id="d9d1d-165">Meaning</span></span>|  
|-----------------------|-------------|  
|<span data-ttu-id="d9d1d-166">0</span><span class="sxs-lookup"><span data-stu-id="d9d1d-166">0</span></span>|<span data-ttu-id="d9d1d-167">成功执行。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-167">Successful execution.</span></span>|  
|<span data-ttu-id="d9d1d-168">1</span><span class="sxs-lookup"><span data-stu-id="d9d1d-168">1</span></span>|<span data-ttu-id="d9d1d-169">未指定所需参数值。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-169">Required parameter value is not specified.</span></span>|  
|<span data-ttu-id="d9d1d-170">2</span><span class="sxs-lookup"><span data-stu-id="d9d1d-170">2</span></span>|<span data-ttu-id="d9d1d-171">指定参数值无效。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-171">Specified parameter value is not valid.</span></span>|  
|<span data-ttu-id="d9d1d-172">3</span><span class="sxs-lookup"><span data-stu-id="d9d1d-172">3</span></span>|<span data-ttu-id="d9d1d-173">获取销售额数值时出错。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-173">Error has occurred getting sales value.</span></span>|  
|<span data-ttu-id="d9d1d-174">4</span><span class="sxs-lookup"><span data-stu-id="d9d1d-174">4</span></span>|<span data-ttu-id="d9d1d-175">该销售人员的销售额数值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-175">NULL sales value found for the salesperson.</span></span>|  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.usp_GetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.usp_GetSalesYTD;  
GO  
CREATE PROCEDURE Sales.usp_GetSalesYTD  
@SalesPerson nvarchar(50) = NULL,  -- NULL default value  
@SalesYTD money = NULL OUTPUT  
AS    
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
   BEGIN  
       PRINT 'ERROR: You must specify a last name for the sales person.'  
       RETURN(1)  
   END  
ELSE  
   BEGIN  
   -- Make sure the value is valid.  
   IF (SELECT COUNT(*) FROM HumanResources.vEmployee  
          WHERE LastName = @SalesPerson) = 0  
      RETURN(2)  
   END  
-- Get the sales for the specified name and   
-- assign it to the output parameter.  
SELECT @SalesYTD = SalesYTD   
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
-- Check for SQL Server errors.  
IF @@ERROR <> 0   
   BEGIN  
      RETURN(3)  
   END  
ELSE  
   BEGIN  
   -- Check to see if the ytd_sales value is NULL.  
     IF @SalesYTD IS NULL  
       RETURN(4)   
     ELSE  
      -- SUCCESS!!  
        RETURN(0)  
   END  
-- Run the stored procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the stored procedure with an input value.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTD  
EXECUTE Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
PRINT N'Year-to-date sales for this employee is ' +  
    CONVERT(varchar(10), @SalesYTDForSalesPerson);  
  
```  
  
 <span data-ttu-id="d9d1d-176">下面的示例创建了处理从 `usp_GetSalesYTD` 过程返回的返回代码的程序。</span><span class="sxs-lookup"><span data-stu-id="d9d1d-176">The following example creates a program to handle the return codes that are returned from the `usp_GetSalesYTD` procedure.</span></span>  
  
```  
-- Declare the variables to receive the output value and return code   
-- of the procedure.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
  
-- Execute the procedure with a title_id value  
-- and save the output value and return code in variables.  
EXECUTE @ret_code = Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
--  Check the return codes.  
IF @ret_code = 0  
BEGIN  
   PRINT 'Procedure executed successfully'  
   -- Display the value returned by the procedure.  
   PRINT 'Year-to-date sales for this employee is ' + CONVERT(varchar(10),@SalesYTDForSalesPerson)  
END  
ELSE IF @ret_code = 1  
   PRINT 'ERROR: You must specify a last name for the sales person.'  
ELSE IF @ret_code = 2   
   PRINT 'EERROR: You must enter a valid last name for the sales person.'  
ELSE IF @ret_code = 3  
   PRINT 'ERROR: An error occurred getting sales value.'  
ELSE IF @ret_code = 4  
   PRINT 'ERROR: No sales recorded for this employee.'     
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9d1d-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9d1d-177">See Also</span></span>  
 <span data-ttu-id="d9d1d-178">[DECLARE @local_variable (Transact-SQL)](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9d1d-178">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="d9d1d-179">[PRINT (Transact-SQL)](/sql/t-sql/language-elements/print-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9d1d-179">[PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span></span>  
 <span data-ttu-id="d9d1d-180">[SET @local_variable (Transact-SQL)](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9d1d-180">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="d9d1d-181">[游标](../cursors.md) </span><span class="sxs-lookup"><span data-stu-id="d9d1d-181">[Cursors](../cursors.md) </span></span>  
 <span data-ttu-id="d9d1d-182">[RETURN (Transact-SQL)](/sql/t-sql/language-elements/return-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9d1d-182">[RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span></span>  
 [<span data-ttu-id="d9d1d-183">@@ERROR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d9d1d-183">@@ERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-transact-sql)  
  
  
