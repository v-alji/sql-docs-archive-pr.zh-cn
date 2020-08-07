---
title: 排序规则和代码页 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c626dcac-0474-432d-acc0-cfa643345372
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab904771fa8ac4acf25a624cbf3e1139f7e96434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588061"
---
# <a name="collations-and-code-pages"></a><span data-ttu-id="03a59-102">排序规则和代码页</span><span class="sxs-lookup"><span data-stu-id="03a59-102">Collations and Code Pages</span></span>
  [!INCLUDE[hek_2](../includes/hek-2-md.md)] <span data-ttu-id="03a59-103">对于内存优化表中的 (var)char 列的支持代码页，以及在索引和本机编译存储过程中使用的支持的排序规则方面存在限制。</span><span class="sxs-lookup"><span data-stu-id="03a59-103">has restrictions on supported code pages for (var)char columns in memory-optimized tables and supported collations used in indexes and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="03a59-104">(var)char 值的代码页决定着字符与存储在表中的字节表示之间的映射。</span><span class="sxs-lookup"><span data-stu-id="03a59-104">The code page for a (var)char value determines the mapping between characters and the byte representation that is stored in the table.</span></span> <span data-ttu-id="03a59-105">例如，使用 Windows Latin 1 代码页（1252；[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的默认代码页）时，字符 'a' 对应字节 0x61。</span><span class="sxs-lookup"><span data-stu-id="03a59-105">For example, with the Windows Latin 1 code page (1252; the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default), the character 'a' corresponds to the byte 0x61.</span></span>  
  
 <span data-ttu-id="03a59-106">(var)char 值的代码页由与该值关联的排序规则决定。</span><span class="sxs-lookup"><span data-stu-id="03a59-106">The code page of a (var)char value is determined by the collation associated with the value.</span></span> <span data-ttu-id="03a59-107">例如，排序规则 SQL_Latin1_General_CP1_CI_AS 的关联代码页为 1252。</span><span class="sxs-lookup"><span data-stu-id="03a59-107">For example, the collation SQL_Latin1_General_CP1_CI_AS has the associated code page 1252.</span></span>  
  
 <span data-ttu-id="03a59-108">值的排序规则继承自数据库的排序规则，也可使用 COLLATE 关键字显式指定。</span><span class="sxs-lookup"><span data-stu-id="03a59-108">The collation of a value is either inherited from the database collation, or can be specified explicitly using the COLLATE keyword.</span></span> <span data-ttu-id="03a59-109">如果数据库包含内存优化的表或本机编译的存储过程，则无法更改数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-109">Database collation cannot be changed if the database contains memory-optimized tables or natively compiled stored procedures.</span></span> <span data-ttu-id="03a59-110">下面的示例设置数据库的排序规则，并创建一个包含采用不同排序规则的列的表。</span><span class="sxs-lookup"><span data-stu-id="03a59-110">The following example sets the database collation and creates a table, which has a column with a different collation.</span></span> <span data-ttu-id="03a59-111">该数据库使用 Latin 不区分大小写的排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-111">The database uses Latin case-insensitive collation.</span></span>  
  
 <span data-ttu-id="03a59-112">如果字符串列采用 BIN2 排序规则，则只能在该列上创建索引。</span><span class="sxs-lookup"><span data-stu-id="03a59-112">Indexes can only be created on string columns if they use a BIN2 collation.</span></span> <span data-ttu-id="03a59-113">LastName 变量采用 BIN2 排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-113">The LastName variable uses BIN2 collation.</span></span> <span data-ttu-id="03a59-114">FirstName 采用数据库默认排序规则，即 CI_AS（不区分大小写，区分重音）。</span><span class="sxs-lookup"><span data-stu-id="03a59-114">FirstName uses the database default, which is CI_AS (case-insensitive, accent-sensitive).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03a59-115">无法对不使用 BIN2 排序规则的索引字符串列使用 order by 或 group by。</span><span class="sxs-lookup"><span data-stu-id="03a59-115">You cannot use order by or group by on index string columns that do not use BIN2 collation.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP  
  
ALTER DATABASE IMOLTP ADD FILEGROUP IMOLTP_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP ADD FILE( NAME = 'IMOLTP_mod' , FILENAME = 'c:\data\IMOLTP_mod') TO FILEGROUP IMOLTP_mod;  
--GO  
  
--  set the database collations  
ALTER DATABASE IMOLTP COLLATE Latin1_General_100_CI_AS  
GO  
  
--  
USE IMOLTP   
GO  
  
-- create a table with collation  
CREATE TABLE Employees (  
  EmployeeID int NOT NULL ,   
  LastName nvarchar(20) COLLATE Latin1_General_100_BIN2 NOT NULL INDEX IX_LastName NONCLUSTERED,   
  FirstName nvarchar(10) NOT NULL ,  
  CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED HASH(EmployeeID)  WITH (BUCKET_COUNT=1024)  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_AND_DATA)  
GO  
```  
  
 <span data-ttu-id="03a59-116">下述限制适用于内存优化的表和本机编译的存储过程：</span><span class="sxs-lookup"><span data-stu-id="03a59-116">The following restrictions apply to memory-optimized tables and natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="03a59-117">内存优化表中的 (var)char 列必须使用代码页 1252 排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-117">(var)char columns in memory-optimized tables must use code page 1252 collation.</span></span> <span data-ttu-id="03a59-118">此限制不适用于 n(var)char 列。</span><span class="sxs-lookup"><span data-stu-id="03a59-118">This restriction does not apply to n(var)char columns.</span></span> <span data-ttu-id="03a59-119">下列代码检索所有 1252 排序规则：</span><span class="sxs-lookup"><span data-stu-id="03a59-119">The following code retrieves all 1252 collations:</span></span>  
  
    ```sql  
    -- all supported collations for (var)char columns in memory-optimized tables  
    select * from sys.fn_helpcollations()  
    where collationproperty(name, 'codepage') = 1252;  
    ```  
  
     <span data-ttu-id="03a59-120">如果需要存储非拉丁字符，请使用 n(var)char 列。</span><span class="sxs-lookup"><span data-stu-id="03a59-120">If you need to store non-Latin characters, use n(var)char columns.</span></span>  
  
-   <span data-ttu-id="03a59-121">(n)(var)char 列的索引只能以 BIN2 排序规则指定（参阅第一个示例）。</span><span class="sxs-lookup"><span data-stu-id="03a59-121">Indexes on (n)(var)char columns can only be specified with BIN2 collations (see the first example).</span></span> <span data-ttu-id="03a59-122">下面的查询检索所有支持的 BIN2 排序规则：</span><span class="sxs-lookup"><span data-stu-id="03a59-122">The following query retrieves all supported BIN2 collations:</span></span>  
  
    ```sql  
    -- all supported collations for indexes on memory-optimized tables and   
    -- comparison/sorting in natively compiled stored procedures  
    select * from sys.fn_helpcollations() where name like '%BIN2'  
    ```  
  
     <span data-ttu-id="03a59-123">如果通过解释的 [!INCLUDE[tsql](../includes/tsql-md.md)] 访问表，则可借助 `COLLATE` 关键字通过表达式或排序操作更改排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-123">If you access the table through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)], you can use the `COLLATE` keyword to change the collation with expressions or sort operations.</span></span> <span data-ttu-id="03a59-124">相关示范见上一个示例。</span><span class="sxs-lookup"><span data-stu-id="03a59-124">See the last example for a sample of this.</span></span>  
  
-   <span data-ttu-id="03a59-125">如果数据库排序规则不是代码页 1252 排序规则，则本机编译的存储过程不能使用 (var)char 类型的参数、局部变量或字符串常量。</span><span class="sxs-lookup"><span data-stu-id="03a59-125">Natively compiled stored procedures cannot use parameters, local variables, or string constants of (var)char type if the database collation is not a code page 1252 collation.</span></span>  
  
-   <span data-ttu-id="03a59-126">本机编译存储过程中的所有表达式和排序操作都必须使用 BIN2 排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-126">All expressions and sort operations inside natively compiled stored procedures must use BIN2 collations.</span></span> <span data-ttu-id="03a59-127">也就是说，所有比较和排序操作都基于字符（二进制表）的 Unicode 码位。</span><span class="sxs-lookup"><span data-stu-id="03a59-127">The implication is that all comparisons and sort operations are based on the Unicode code points of the characters (binary representations).</span></span> <span data-ttu-id="03a59-128">例如，所有排序操作均区分大小写（“Z”位于“a”之前）。</span><span class="sxs-lookup"><span data-stu-id="03a59-128">For example all sorting is case sensitive ('Z' comes before 'a').</span></span> <span data-ttu-id="03a59-129">如有必要，可使用解释的 [!INCLUDE[tsql](../includes/tsql-md.md)] 进行不区分大小写的排序和比较。</span><span class="sxs-lookup"><span data-stu-id="03a59-129">If necessary, use interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] for case-insensitive sorting and comparison.</span></span>  
  
-   <span data-ttu-id="03a59-130">本机编译的存储过程内部不支持 UTF-16 数据截断。</span><span class="sxs-lookup"><span data-stu-id="03a59-130">Truncation of UTF-16 data is not supported inside natively compiled stored procedures.</span></span> <span data-ttu-id="03a59-131">这意味着 n (var) char (*n*) 值不能转换为类型 n (值。如果排序规则具有) 属性 *，则不*能转换*为 (。*  <  *n*</span><span class="sxs-lookup"><span data-stu-id="03a59-131">This means that n(var)char(*n*) values cannot be converted to type n(var)char(*i*), if *i* < *n*, if the collation has _SC property.</span></span> <span data-ttu-id="03a59-132">例如，不支持以下操作：</span><span class="sxs-lookup"><span data-stu-id="03a59-132">For example, the following is not supported:</span></span>  
  
    ```sql  
    -- column definition using an _SC collation  
     c2 nvarchar(200) collate Latin1_General_100_CS_AS_SC not null   
    -- assignment to a smaller variable, requiring truncation  
     declare @c2 nvarchar(100) = '';  
     select @c2 = c2  
    ```  
  
     <span data-ttu-id="03a59-133">在本机编译的存储过程中不支持字符串操作函数，例如 LEN、SUBSTRING、LTRIM 和具有 UTF-16 数据的 RTRIM。</span><span class="sxs-lookup"><span data-stu-id="03a59-133">String manipulation functions, such as LEN, SUBSTRING, LTRIM, and RTRIM with UTF-16 data are not supported inside natively compiled stored procedures.</span></span> <span data-ttu-id="03a59-134">不能将这些字符串操作函数用于具有 _SC 排序规则的 n(var)char 值。</span><span class="sxs-lookup"><span data-stu-id="03a59-134">You cannot use these string manipulation functions for n(var)char values that have an _SC collation.</span></span>  
  
     <span data-ttu-id="03a59-135">使用足够大的类型声明变量以避免截断。</span><span class="sxs-lookup"><span data-stu-id="03a59-135">Declare variables using types that are large enough to avoid truncation.</span></span>  
  
 <span data-ttu-id="03a59-136">下面的示例演示了内存中 OLTP 中排序规则限制的一些影响和解决方法。</span><span class="sxs-lookup"><span data-stu-id="03a59-136">The following example shows some of the implications and workarounds for the collation limitations in In-Memory OLTP.</span></span> <span data-ttu-id="03a59-137">该示例使用上面指定的 Employees 表。</span><span class="sxs-lookup"><span data-stu-id="03a59-137">The example uses the Employees table specified above.</span></span> <span data-ttu-id="03a59-138">此示例列出所有员工。</span><span class="sxs-lookup"><span data-stu-id="03a59-138">This sample list all employees .</span></span> <span data-ttu-id="03a59-139">注意，对于 LastName，出于二进制排序规则的原因，大写名称将排在小写名称之前。</span><span class="sxs-lookup"><span data-stu-id="03a59-139">Notice that for LastName, due to the binary collation, the upper case names are sorted before lower case.</span></span> <span data-ttu-id="03a59-140">因此，'Thomas' 排在 'nolan' 之前（因为大写字符的码位在前）。</span><span class="sxs-lookup"><span data-stu-id="03a59-140">Therefore, 'Thomas' comes before 'nolan' because upper case characters have lower code points.</span></span> <span data-ttu-id="03a59-141">FirstName 拥有不区分大小写的排序规则。</span><span class="sxs-lookup"><span data-stu-id="03a59-141">FirstName has a case-insensitive collation.</span></span> <span data-ttu-id="03a59-142">因此，字符以其在字母表中的位置而非该字符的码位进行排序。</span><span class="sxs-lookup"><span data-stu-id="03a59-142">So, sorting is by letter of the alphabet, not code point of the characters.</span></span>  
  
```sql  
-- insert a number of values  
INSERT Employees VALUES (1,'thomas', 'john')  
INSERT Employees VALUES (2,'Thomas', 'rupert')  
INSERT Employees VALUES (3,'Thomas', 'Jack')  
INSERT Employees VALUES (4,'Thomas', 'annie')  
INSERT Employees VALUES (5,'nolan', 'John')  
GO  
  
-- ===========  
SELECT EmployeeID, LastName, FirstName FROM Employees  
ORDER BY LastName, FirstName  
GO  
  
-- ===========  
-- specify collation: sorting uses case-insensitive collation, thus 'nolan' comes before 'Thomas'  
SELECT * FROM Employees  
ORDER BY LastName COLLATE Latin1_General_100_CI_AS, FirstName  
GO  
  
-- ===========  
-- retrieve employee by Name  
-- must use BIN2 collation for comparison in natively compiled stored procedures  
CREATE PROCEDURE usp_EmployeeByName @LastName nvarchar(20), @FirstName nvarchar(10)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = N'us_english'  
)  
  SELECT EmployeeID, LastName, FirstName FROM dbo.Employees  
  WHERE   
    LastName = @LastName AND  
    FirstName COLLATE Latin1_General_100_BIN2 = @FirstName  
  
END  
GO  
  
-- this does not return any rows, as EmployeeID 1 has first name 'john', which is not equal to 'John' in a binary collation  
EXEC usp_EmployeeByName 'thomas', 'John'  
  
-- this retrieves EmployeeID 1  
EXEC usp_EmployeeByName 'thomas', 'john'  
```  
  
## <a name="see-also"></a><span data-ttu-id="03a59-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03a59-143">See Also</span></span>  
 [<span data-ttu-id="03a59-144">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="03a59-144">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
