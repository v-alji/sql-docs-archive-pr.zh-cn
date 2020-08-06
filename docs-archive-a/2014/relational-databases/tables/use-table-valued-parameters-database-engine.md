---
title: 使用表值参数（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- DECLARE
- CREATE TYPE
helpviewer_keywords:
- table-valued parameters
- table-valued parameters, about table-valued parameters
- parameters [SQL Server], table-valued
- TVP See table-valued parameters
ms.assetid: 5e95a382-1e01-4c74-81f5-055612c2ad99
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa7013fddc6b2ce12ad9ad0f9fcb511d93915e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586560"
---
# <a name="use-table-valued-parameters-database-engine"></a><span data-ttu-id="642d7-102">使用表值参数（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="642d7-102">Use Table-Valued Parameters (Database Engine)</span></span>
  <span data-ttu-id="642d7-103">表值参数是使用用户定义的表类型来声明的。</span><span class="sxs-lookup"><span data-stu-id="642d7-103">Table-valued parameters are declared by using user-defined table types.</span></span> <span data-ttu-id="642d7-104">使用表值参数，可以不必创建临时表或许多参数，即可向 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或例程（如存储过程或函数）发送多行数据。</span><span class="sxs-lookup"><span data-stu-id="642d7-104">You can use table-valued parameters to send multiple rows of data to a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a routine, such as a stored procedure or function, without creating a temporary table or many parameters.</span></span>  
  
 <span data-ttu-id="642d7-105">表值参数与 OLE DB 和 ODBC 中的参数数组类似，但具有更高的灵活性，且与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的集成更紧密。</span><span class="sxs-lookup"><span data-stu-id="642d7-105">Table-valued parameters are like parameter arrays in OLE DB and ODBC, but offer more flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="642d7-106">表值参数的另一个优势是能够参与基于数据集的操作。</span><span class="sxs-lookup"><span data-stu-id="642d7-106">Table-valued parameters also have the benefit of being able to participate in set-based operations.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="642d7-107">通过引用向例程传递表值参数，以避免创建输入数据的副本。</span><span class="sxs-lookup"><span data-stu-id="642d7-107">passes table-valued parameters to routines by reference to avoid making a copy of the input data.</span></span> <span data-ttu-id="642d7-108">可以使用表值参数创建和执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 例程，并且可以使用任何托管语言从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码、托管客户端以及本机客户端调用它们。</span><span class="sxs-lookup"><span data-stu-id="642d7-108">You can create and execute [!INCLUDE[tsql](../../includes/tsql-md.md)] routines with table-valued parameters, and call them from [!INCLUDE[tsql](../../includes/tsql-md.md)] code, managed and native clients in any managed language.</span></span>  
  
 <span data-ttu-id="642d7-109">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="642d7-109">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="642d7-110">优点</span><span class="sxs-lookup"><span data-stu-id="642d7-110">Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="642d7-111">限制</span><span class="sxs-lookup"><span data-stu-id="642d7-111">Restrictions</span></span>](#Restrictions)  
  
 [<span data-ttu-id="642d7-112">表值参数与 BULK INSERT 操作</span><span class="sxs-lookup"><span data-stu-id="642d7-112">Table-Valued Parameters vs. BULK INSERT Operations</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="642d7-113">示例</span><span class="sxs-lookup"><span data-stu-id="642d7-113">Example</span></span>](#Example)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="642d7-114">优势</span><span class="sxs-lookup"><span data-stu-id="642d7-114">Benefits</span></span>  
 <span data-ttu-id="642d7-115">就像其他参数一样，表值参数的作用域也是存储过程、函数或动态 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文本。</span><span class="sxs-lookup"><span data-stu-id="642d7-115">A table-valued parameter is scoped to the stored procedure, function, or dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] text, exactly like other parameters.</span></span> <span data-ttu-id="642d7-116">同样，表类型变量也与使用 DECLARE 语句创建的其他任何局部变量一样具有作用域。</span><span class="sxs-lookup"><span data-stu-id="642d7-116">Similarly, a variable of table type has scope like any other local variable that is created by using a DECLARE statement.</span></span> <span data-ttu-id="642d7-117">可以在动态 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句内声明表值变量，并且可以将这些变量作为表值参数传递到存储过程和函数。</span><span class="sxs-lookup"><span data-stu-id="642d7-117">You can declare table-valued variables within dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and pass these variables as table-valued parameters to stored procedures and functions.</span></span>  
  
 <span data-ttu-id="642d7-118">表值参数具有更高的灵活性，在某些情况下，可比临时表或其他传递参数列表的方法提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="642d7-118">Table-valued parameters offer more flexibility and in some cases better performance than temporary tables or other ways to pass a list of parameters.</span></span> <span data-ttu-id="642d7-119">表值参数具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="642d7-119">Table-valued parameters offer the following benefits:</span></span>  
  
-   <span data-ttu-id="642d7-120">首次从客户端填充数据时，不获取锁。</span><span class="sxs-lookup"><span data-stu-id="642d7-120">Do not acquire locks for the initial population of data from a client.</span></span>  
  
-   <span data-ttu-id="642d7-121">提供简单的编程模型。</span><span class="sxs-lookup"><span data-stu-id="642d7-121">Provide a simple programming model.</span></span>  
  
-   <span data-ttu-id="642d7-122">允许在单个例程中包括复杂的业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="642d7-122">Enable you to include complex business logic in a single routine.</span></span>  
  
-   <span data-ttu-id="642d7-123">减少到服务器的往返。</span><span class="sxs-lookup"><span data-stu-id="642d7-123">Reduce round trips to the server.</span></span>  
  
-   <span data-ttu-id="642d7-124">可以具有不同基数的表结构。</span><span class="sxs-lookup"><span data-stu-id="642d7-124">Can have a table structure of different cardinality.</span></span>  
  
-   <span data-ttu-id="642d7-125">是强类型。</span><span class="sxs-lookup"><span data-stu-id="642d7-125">Are strongly typed.</span></span>  
  
-   <span data-ttu-id="642d7-126">使客户端可以指定排序顺序和唯一键。</span><span class="sxs-lookup"><span data-stu-id="642d7-126">Enable the client to specify sort order and unique keys.</span></span>  
  
-   <span data-ttu-id="642d7-127">在用于存储过程时像临时表一样被缓存。</span><span class="sxs-lookup"><span data-stu-id="642d7-127">Are cached like a temp table when used in a stored procedure.</span></span> <span data-ttu-id="642d7-128">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，对于参数化查询，表值参数也被缓存。</span><span class="sxs-lookup"><span data-stu-id="642d7-128">Starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], table-valued parameters are also cached for parameterized queries.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="642d7-129">限制</span><span class="sxs-lookup"><span data-stu-id="642d7-129">Restrictions</span></span>  
 <span data-ttu-id="642d7-130">表值参数有下面的限制：</span><span class="sxs-lookup"><span data-stu-id="642d7-130">Table-valued parameters have the following restrictions:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="642d7-131">不维护表值参数列的统计信息。</span><span class="sxs-lookup"><span data-stu-id="642d7-131">does not maintain statistics on columns of table-valued parameters.</span></span>  
  
-   <span data-ttu-id="642d7-132">表值参数必须作为输入 READONLY 参数传递到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 例程。</span><span class="sxs-lookup"><span data-stu-id="642d7-132">Table-valued parameters must be passed as input READONLY parameters to [!INCLUDE[tsql](../../includes/tsql-md.md)] routines.</span></span> <span data-ttu-id="642d7-133">不能在例程体中对表值参数执行诸如 UPDATE、DELETE 或 INSERT 这样的 DML 操作。</span><span class="sxs-lookup"><span data-stu-id="642d7-133">You cannot perform DML operations such as UPDATE, DELETE, or INSERT on a table-valued parameter in the body of a routine.</span></span>  
  
-   <span data-ttu-id="642d7-134">不能将表值参数用作 SELECT INTO 或 INSERT EXEC 语句的目标。</span><span class="sxs-lookup"><span data-stu-id="642d7-134">You cannot use a table-valued parameter as target of a SELECT INTO or INSERT EXEC statement.</span></span> <span data-ttu-id="642d7-135">表值参数可以在 SELECT INTO 的 FROM 子句中，也可以在 INSERT EXEC 字符串或存储过程中。</span><span class="sxs-lookup"><span data-stu-id="642d7-135">A table-valued parameter can be in the FROM clause of SELECT INTO or in the INSERT EXEC string or stored procedure.</span></span>  
  
##  <a name="table-valued-parameters-vs-bulk-insert-operations"></a><a name="BulkInsert"></a><span data-ttu-id="642d7-136">表值参数与 BULK INSERT 操作</span><span class="sxs-lookup"><span data-stu-id="642d7-136">Table-Valued Parameters vs. BULK INSERT Operations</span></span>  
 <span data-ttu-id="642d7-137">表值参数的使用方法与其他基于数据集的变量的使用方法相似；但是，频繁使用表值参数将比大型数据集要快。</span><span class="sxs-lookup"><span data-stu-id="642d7-137">Using table-valued parameters is comparable to other ways of using set-based variables; however, using table-valued parameters frequently can be faster for large data sets.</span></span> <span data-ttu-id="642d7-138">大容量操作的启动开销比表值参数大，与之相比，表值参数在插入数目少于 1000 的行时具有很好的执行性能。</span><span class="sxs-lookup"><span data-stu-id="642d7-138">Compared to bulk operations that have a greater startup cost than table-valued parameters, table-valued parameters perform well for inserting less than 1000 rows.</span></span>  
  
 <span data-ttu-id="642d7-139">重用的表值参数可从临时表缓存中受益。</span><span class="sxs-lookup"><span data-stu-id="642d7-139">Table-valued parameters that are reused benefit from temporary table caching.</span></span> <span data-ttu-id="642d7-140">这一表缓存功能可比对等的 BULK INSERT 操作提供更好的伸缩性。</span><span class="sxs-lookup"><span data-stu-id="642d7-140">This table caching enables better scalability than equivalent BULK INSERT operations.</span></span> <span data-ttu-id="642d7-141">使用小型行插入操作时，可以通过使用参数列表或批量语句（而不是 BULK INSERT 操作或表值参数）来获得小的性能改进。</span><span class="sxs-lookup"><span data-stu-id="642d7-141">By using small row-insert operations a small performance benefit might be gained by using parameter lists or batched statements instead of BULK INSERT operations or table-valued parameters.</span></span> <span data-ttu-id="642d7-142">但是，这些方法在编程上不太方便，并且随着行的增加，性能会迅速下降。</span><span class="sxs-lookup"><span data-stu-id="642d7-142">However, these methods are less convenient to program, and performance decreases quickly as rows increase.</span></span>  
  
 <span data-ttu-id="642d7-143">表值参数在执行性能上与对等的参数阵列实现相当甚至更好。</span><span class="sxs-lookup"><span data-stu-id="642d7-143">Table-valued parameters perform equally well or better than an equivalent parameter array implementation.</span></span>  
  
##  <a name="example"></a><a name="Example"></a> <span data-ttu-id="642d7-144">示例</span><span class="sxs-lookup"><span data-stu-id="642d7-144">Example</span></span>  
 <span data-ttu-id="642d7-145">下面的示例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 并演示如何执行以下操作：创建表值参数类型，声明变量来引用它，填充参数列表，然后将值传递到存储过程。</span><span class="sxs-lookup"><span data-stu-id="642d7-145">The following example uses [!INCLUDE[tsql](../../includes/tsql-md.md)] and shows you how to create a table-valued parameter type, declare a variable to reference it, fill the parameter list, and then pass the values to a stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE dbo. usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO AdventureWorks2012.Production.Location  
           (Name  
           ,CostRate  
           ,Availability  
           ,ModifiedDate)  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
        GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT Name, 0.00  
    FROM AdventureWorks2012.Person.StateProvince;  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="642d7-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="642d7-146">See Also</span></span>  
 <span data-ttu-id="642d7-147">[CREATE TYPE (Transact-SQL)](/sql/t-sql/statements/create-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642d7-147">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span></span>  
 <span data-ttu-id="642d7-148">[DECLARE @local_variable (Transact-SQL)](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642d7-148">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="642d7-149">[sys.databases &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642d7-149">[sys.types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span></span>  
 <span data-ttu-id="642d7-150">[sys. parameters &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642d7-150">[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span></span>  
 <span data-ttu-id="642d7-151">[sys. parameter_type_usages &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642d7-151">[sys.parameter_type_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span></span>  
 <span data-ttu-id="642d7-152">[CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="642d7-152">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="642d7-153">CREATE FUNCTION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="642d7-153">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
