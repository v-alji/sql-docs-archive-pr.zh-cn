---
title: CLR 表值函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- Transact-SQL table-valued functions
- table-valued functions [CLR integration]
- TVFs [CLR integration]
ms.assetid: 9a6133ea-36e9-45bf-b572-1c0df3d6c194
author: rothja
ms.author: jroth
ms.openlocfilehash: b700aba5a753ecd8ee50ee9b7679cafb2f1f8581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587432"
---
# <a name="clr-table-valued-functions"></a><span data-ttu-id="5e1fb-102">CLR 表值函数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-102">CLR Table-Valued Functions</span></span>
  <span data-ttu-id="5e1fb-103">表值函数是返回表的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-103">A table-valued function is a user-defined function that returns a table.</span></span>  
  
 <span data-ttu-id="5e1fb-104">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过允许您在任何托管语言中定义表值函数以扩展表值函数的功能。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extends the functionality of table-valued functions by allowing you to define a table-valued function in any managed language.</span></span> <span data-ttu-id="5e1fb-105">数据通过 `IEnumerable` 或 `IEnumerator` 对象从表值函数中返回。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-105">Data is returned from a table-valued function through an `IEnumerable` or `IEnumerator` object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e1fb-106">对于表值函数，返回表类型的列不能包含时间戳列或非 Unicode 字符串数据类型列（例如，`char`、`varchar` 和 `text`）。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-106">For table-valued functions, the columns of the return table type cannot include timestamp columns or non-Unicode string data type columns (such as `char`, `varchar`, and `text`).</span></span> <span data-ttu-id="5e1fb-107">不支持 NOT NULL 约束。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-107">The NOT NULL constraint is not supported.</span></span>  
  
## <a name="differences-between-transact-sql-and-clr-table-valued-functions"></a><span data-ttu-id="5e1fb-108">Transact-SQL 与 CLR 表值函数之间的差异</span><span class="sxs-lookup"><span data-stu-id="5e1fb-108">Differences Between Transact-SQL and CLR Table-Valued Functions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="5e1fb-109">表值函数将调用此函数的结果具体化到某个中间表中。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-109">table-valued functions materialize the results of calling the function into an intermediate table.</span></span> <span data-ttu-id="5e1fb-110">由于它们使用中间表，因此它们可以对于结果支持约束和唯一索引。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-110">Since they use an intermediate table, they can support constraints and unique indexes over the results.</span></span> <span data-ttu-id="5e1fb-111">当返回大型结果时，这些功能极其有用。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-111">These features can be extremely useful when large results are returned.</span></span>  
  
 <span data-ttu-id="5e1fb-112">相比较而言，CLR 表值函数表示一种流替代方法。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-112">In contrast, CLR table-valued functions represent a streaming alternative.</span></span> <span data-ttu-id="5e1fb-113">此时，不要求在单个表中具体化整个结果集。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-113">There is no requirement that the entire set of results be materialized in a single table.</span></span> <span data-ttu-id="5e1fb-114">调用表值函数的查询的执行计划直接调用由托管函数返回的 `IEnumerable` 对象，并且结果将以递增方式使用。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-114">The `IEnumerable` object returned by the managed function is directly called by the execution plan of the query that calls the table-valued function, and the results are consumed in an incremental manner.</span></span> <span data-ttu-id="5e1fb-115">这种流模型可确保在第一行可用之后立即使用结果，而不是等待填充整个表。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-115">This streaming model ensures that results can be consumed immediately after the first row is available, instead of waiting for the entire table to be populated.</span></span> <span data-ttu-id="5e1fb-116">如果返回的行非常多，则这还是一个更好的替代方法，因为它们不必在内存中作为一个整体进行具体化。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-116">It is also a better alternative if you have very large numbers of rows returned, because they do not have to be materialized in memory as a whole.</span></span> <span data-ttu-id="5e1fb-117">例如，可以使用托管表值函数分析文本文件并将其中的每行作为一行返回。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-117">For example, a managed table-valued function could be used to parse a text file and return each line as a row.</span></span>  
  
## <a name="implementing-table-valued-functions"></a><span data-ttu-id="5e1fb-118">实现表值函数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-118">Implementing Table-Valued Functions</span></span>  
 <span data-ttu-id="5e1fb-119">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 程序集中将表值函数作为类的方法实现。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-119">Implement table-valued functions as methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="5e1fb-120">表值函数代码必须实现 `IEnumerable` 接口。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-120">Your table-valued function code must implement the `IEnumerable` interface.</span></span> <span data-ttu-id="5e1fb-121">`IEnumerable` 接口在 .NET Framework 中定义。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-121">The `IEnumerable` interface is defined in the .NET Framework.</span></span> <span data-ttu-id="5e1fb-122">在 .NET Framework 中表示数组和集合的类型已经实现 `IEnumerable` 接口。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-122">Types representing arrays and collections in the .NET Framework already implement the `IEnumerable` interface.</span></span> <span data-ttu-id="5e1fb-123">这样，就可以轻松地编写将集合或数组转换为结果集的表值函数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-123">This makes it easy for writing table-valued functions that convert a collection or an array into a result set.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="5e1fb-124">表值参数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-124">Table-Valued Parameters</span></span>  
 <span data-ttu-id="5e1fb-125">表值参数即传递到某一过程或函数的用户定义表类型，它提供了一种将多行数据传递到服务器的高效方法。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-125">Table-valued parameters are user-defined table types that are passed into a procedure or function and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="5e1fb-126">表值参数提供与参数数组类似的功能，但灵活性更高并且与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的集成更紧密。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-126">Table-valued parameters provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5e1fb-127">它们还提供提升性能的潜力。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-127">They also provide the potential for better performance.</span></span> <span data-ttu-id="5e1fb-128">表值参数还有助于减少到服务器的往返次数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-128">Table-valued parameters also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="5e1fb-129">可以将数据作为表值参数发送到服务器，而不是向服务器发送多个请求（例如，对于标量参数列表）。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-129">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a table-valued parameter.</span></span> <span data-ttu-id="5e1fb-130">用户定义表类型不能作为表值参数传递到在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程中执行的托管存储过程或函数，也不能从这些存储过程或函数中返回。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-130">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="5e1fb-131">有关表值参数的详细信息，请参阅[使用表值参数（数据引擎）](../tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-131">For more information about table-valued parameters, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="output-parameters-and-table-valued-functions"></a><span data-ttu-id="5e1fb-132">输出参数和表值函数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-132">Output Parameters and Table-Valued Functions</span></span>  
 <span data-ttu-id="5e1fb-133">通过使用输出参数，可以从表值函数返回信息。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-133">Information may be returned from table-valued functions using output parameters.</span></span> <span data-ttu-id="5e1fb-134">在实现代码表值函数中的相应参数应将按引用传递参数用作参数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-134">The corresponding parameter in the implementation code table-valued function should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="5e1fb-135">请注意，Visual Basic 不支持采用与 Visual C# 的相同方法输出参数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-135">Note that Visual Basic does not support output parameters in the same way that Visual C# does.</span></span> <span data-ttu-id="5e1fb-136">必须按引用指定参数，并应用 \<Out()> 属性以表示输出参数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5e1fb-136">You must specify the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
...  
Public Shared Sub FillRow ( <Out()> ByRef value As SqlInt32)  
```  
  
### <a name="defining-a-table-valued-function-in-transact-sql"></a><span data-ttu-id="5e1fb-137">在 Transact-SQL 中定义表值函数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-137">Defining a Table-Valued Function in Transact-SQL</span></span>  
 <span data-ttu-id="5e1fb-138">定义 CLR 表值函数的语法与定义 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表值函数的语法类似，但增加了 `EXTERNAL NAME` 子句。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-138">The syntax for defining a CLR table-valued function is similar to that of a [!INCLUDE[tsql](../../includes/tsql-md.md)] table-valued function, with the addition of the `EXTERNAL NAME` clause.</span></span> <span data-ttu-id="5e1fb-139">例如：</span><span class="sxs-lookup"><span data-stu-id="5e1fb-139">For example:</span></span>  
  
```  
CREATE FUNCTION GetEmpFirstLastNames()  
RETURNS TABLE (FirstName NVARCHAR(4000), LastName NVARCHAR(4000))  
EXTERNAL NAME MyDotNETAssembly.[MyNamespace.MyClassname]. GetEmpFirstLastNames;  
```  
  
 <span data-ttu-id="5e1fb-140">表值函数用于以相关格式表示数据，以便在查询中进一步处理，例如：</span><span class="sxs-lookup"><span data-stu-id="5e1fb-140">Table-valued functions are used to represent data in relational form for further processing in queries such as:</span></span>  
  
```  
select * from function();  
select * from tbl join function() f on tbl.col = f.col;  
select * from table t cross apply function(t.column);  
```  
  
 <span data-ttu-id="5e1fb-141">在以下情况下，表值函数可以返回表：</span><span class="sxs-lookup"><span data-stu-id="5e1fb-141">Table-valued functions can return a table when:</span></span>  
  
-   <span data-ttu-id="5e1fb-142">当从标量输入参数中创建表值函数时。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-142">Created from scalar input arguments.</span></span> <span data-ttu-id="5e1fb-143">例如，使用以逗号分隔的数字字符串并将它们透视到某个表中的表值函数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-143">For example, a table-valued function that takes a comma-delimited string of numbers and pivots them into a table.</span></span>  
  
-   <span data-ttu-id="5e1fb-144">当从外部数据生成表值函数时。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-144">Generated from external data.</span></span> <span data-ttu-id="5e1fb-145">例如，读取事件日志并将其显示为表的表值函数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-145">For example, a table-valued function that reads the event log and exposes it as a table.</span></span>  
  
 <span data-ttu-id="5e1fb-146">**注意**表值函数只能通过 [!INCLUDE[tsql](../../includes/tsql-md.md)] `InitMethod` 方法（而不是方法）中的查询来执行数据访问 `FillRow` 。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-146">**Note** A table-valued function can only perform data access through a [!INCLUDE[tsql](../../includes/tsql-md.md)] query in the `InitMethod` method, and not in the `FillRow` method.</span></span> <span data-ttu-id="5e1fb-147">如果执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询，则应使用 `InitMethod` 属性标记 `SqlFunction.DataAccess.Read`。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-147">The `InitMethod` should be marked with the `SqlFunction.DataAccess.Read` attribute property if a [!INCLUDE[tsql](../../includes/tsql-md.md)] query is performed.</span></span>  
  
## <a name="a-sample-table-valued-function"></a><span data-ttu-id="5e1fb-148">示例表值函数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-148">A Sample Table-Valued Function</span></span>  
 <span data-ttu-id="5e1fb-149">下面的表值函数返回系统事件日志中的信息。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-149">The following table-valued function returns information from the system event log.</span></span> <span data-ttu-id="5e1fb-150">此函数采用单个字符串参数，其中包含要读取的事件日志的名称。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-150">The function takes a single string argument containing the name of the event log to read.</span></span>  
  
###### <a name="sample-code"></a><span data-ttu-id="5e1fb-151">代码示例</span><span class="sxs-lookup"><span data-stu-id="5e1fb-151">Sample Code</span></span>  
  
```csharp  
using System;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Collections;  
using System.Data.SqlTypes;  
using System.Diagnostics;  
  
public class TabularEventLog  
{  
    [SqlFunction(FillRowMethodName = "FillRow")]  
    public static IEnumerable InitMethod(String logname)  
    {  
        return new EventLog(logname).Entries;    }  
  
    public static void FillRow(Object obj, out SqlDateTime timeWritten, out SqlChars message, out SqlChars category, out long instanceId)  
    {  
        EventLogEntry eventLogEntry = (EventLogEntry)obj;  
        timeWritten = new SqlDateTime(eventLogEntry.TimeWritten);  
        message = new SqlChars(eventLogEntry.Message);  
        category = new SqlChars(eventLogEntry.Category);  
        instanceId = eventLogEntry.InstanceId;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.Sql  
Imports Microsoft.SqlServer.Server  
Imports System.Collections  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Public Class TabularEventLog  
    <SqlFunction(FillRowMethodName:="FillRow")> _  
    Public Shared Function InitMethod(ByVal logname As String) As IEnumerable  
        Return New EventLog(logname).Entries  
    End Function  
  
    Public Shared Sub FillRow(ByVal obj As Object, <Out()> ByRef timeWritten As SqlDateTime, <Out()> ByRef message As SqlChars, <Out()> ByRef category As SqlChars, <Out()> ByRef instanceId As Long)  
        Dim eventLogEnTry As EventLogEntry = CType(obj, EventLogEntry)  
        timeWritten = New SqlDateTime(eventLogEnTry.TimeWritten)  
        message = New SqlChars(eventLogEnTry.Message)  
        category = New SqlChars(eventLogEnTry.Category)  
        instanceId = eventLogEnTry.InstanceId  
    End Sub  
End Class  
```  
  
###### <a name="declaring-and-using-the-sample-table-valued-function"></a><span data-ttu-id="5e1fb-152">声明和使用示例表值函数</span><span class="sxs-lookup"><span data-stu-id="5e1fb-152">Declaring and Using the Sample Table-Valued Function</span></span>  
 <span data-ttu-id="5e1fb-153">在编译了示例表值函数后，就可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中声明它，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5e1fb-153">After the sample table-valued function has been compiled, it can be declared in [!INCLUDE[tsql](../../includes/tsql-md.md)] like this:</span></span>  
  
```  
use master;  
-- Replace SQL_Server_logon with your SQL Server user credentials.  
GRANT EXTERNAL ACCESS ASSEMBLY TO [SQL_Server_logon];   
-- Modify the following line to specify a different database.  
ALTER DATABASE master SET TRUSTWORTHY ON;  
  
-- Modify the next line to use the appropriate database.  
CREATE ASSEMBLY tvfEventLog   
FROM 'D:\assemblies\tvfEventLog\tvfeventlog.dll'   
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
CREATE FUNCTION ReadEventLog(@logname nvarchar(100))  
RETURNS TABLE   
(logTime datetime,Message nvarchar(4000),Category nvarchar(4000),InstanceId bigint)  
AS   
EXTERNAL NAME tvfEventLog.TabularEventLog.InitMethod;  
GO  
```  
  
 <span data-ttu-id="5e1fb-154">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中不再支持执行使用 /clr:pure 编译的 Visual C++ 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-154">Visual C++ database objects compiled with /clr:pure are not supported for execution on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="5e1fb-155">例如，此类数据库对象包含表值函数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-155">For example, such database objects include table-valued functions.</span></span>  
  
 <span data-ttu-id="5e1fb-156">若要测试此示例，请尝试以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码：</span><span class="sxs-lookup"><span data-stu-id="5e1fb-156">To test the sample, try the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
```  
-- Select the top 100 events,  
SELECT TOP 100 *  
FROM dbo.ReadEventLog(N'Security') as T;  
go  
  
-- Select the last 10 login events.  
SELECT TOP 10 T.logTime, T.Message, T.InstanceId   
FROM dbo.ReadEventLog(N'Security') as T  
WHERE T.Category = N'Logon/Logoff';  
go  
```  
  
## <a name="sample-returning-the-results-of-a-sql-server-query"></a><span data-ttu-id="5e1fb-157">示例：返回 SQL Server 查询的结果</span><span class="sxs-lookup"><span data-stu-id="5e1fb-157">Sample: Returning the Results of a SQL Server Query</span></span>  
 <span data-ttu-id="5e1fb-158">以下示例演示查询 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的表值函数。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-158">The following sample shows a table-valued function that queries a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="5e1fb-159">本示例使用 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中的 AdventureWorks 轻型数据库。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-159">This sample uses the AdventureWorks Light database from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="5e1fb-160">[https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843)有关下载 AdventureWorks 的详细信息，请参阅。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-160">See [https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843) for more information on downloading AdventureWorks.</span></span>  
  
 <span data-ttu-id="5e1fb-161">将源代码文件命名为 FindInvalidEmails.cs 或 FindInvalidEmails.vb。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-161">Name your source code file FindInvalidEmails.cs or FindInvalidEmails.vb.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
  
using Microsoft.SqlServer.Server;  
  
public partial class UserDefinedFunctions {  
   private class EmailResult {  
      public SqlInt32 CustomerId;  
      public SqlString EmailAdress;  
  
      public EmailResult(SqlInt32 customerId, SqlString emailAdress) {  
         CustomerId = customerId;  
         EmailAdress = emailAdress;  
      }  
   }  
  
   public static bool ValidateEmail(SqlString emailAddress) {  
      if (emailAddress.IsNull)  
         return false;  
  
      if (!emailAddress.Value.EndsWith("@adventure-works.com"))  
         return false;  
  
      // Validate the address. Put any more rules here.  
      return true;  
   }  
  
   [SqlFunction(  
       DataAccess = DataAccessKind.Read,  
       FillRowMethodName = "FindInvalidEmails_FillRow",  
       TableDefinition="CustomerId int, EmailAddress nvarchar(4000)")]  
   public static IEnumerable FindInvalidEmails(SqlDateTime modifiedSince) {  
      ArrayList resultCollection = new ArrayList();  
  
      using (SqlConnection connection = new SqlConnection("context connection=true")) {  
         connection.Open();  
  
         using (SqlCommand selectEmails = new SqlCommand(  
             "SELECT " +  
             "[CustomerID], [EmailAddress] " +  
             "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " +  
             "WHERE [ModifiedDate] >= @modifiedSince",  
             connection)) {  
            SqlParameter modifiedSinceParam = selectEmails.Parameters.Add(  
                "@modifiedSince",  
                SqlDbType.DateTime);  
            modifiedSinceParam.Value = modifiedSince;  
  
            using (SqlDataReader emailsReader = selectEmails.ExecuteReader()) {  
               while (emailsReader.Read()) {  
                  SqlString emailAddress = emailsReader.GetSqlString(1);  
                  if (ValidateEmail(emailAddress)) {  
                     resultCollection.Add(new EmailResult(  
                         emailsReader.GetSqlInt32(0),  
                         emailAddress));  
                  }  
               }  
            }  
         }  
      }  
  
      return resultCollection;  
   }  
  
   public static void FindInvalidEmails_FillRow(  
       object emailResultObj,  
       out SqlInt32 customerId,  
       out SqlString emailAdress) {  
      EmailResult emailResult = (EmailResult)emailResultObj;  
  
      customerId = emailResult.CustomerId;  
      emailAdress = emailResult.EmailAdress;  
   }  
};  
```  
  
```vb  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, ByRef customerId As SqlInt32, ByRef emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End ClassImports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, customerId As SqlInt32, emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="5e1fb-162">将源代码编译为 DLL 并将此 DLL 复制到 C 驱动器的根目录下。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-162">Compile the source code to a DLL and copy the DLL to the root directory of your C drive.</span></span>  <span data-ttu-id="5e1fb-163">然后，执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="5e1fb-163">Then, execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query.</span></span>  
  
```  
use AdventureWorksLT2008;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'FindInvalidEmails')  
   DROP FUNCTION FindInvalidEmails;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\FindInvalidEmails.dll'  
WITH PERMISSION_SET = SAFE -- EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION FindInvalidEmails(@ModifiedSince datetime)   
RETURNS TABLE (  
   CustomerId int,  
   EmailAddress nvarchar(4000)  
)  
AS EXTERNAL NAME MyClrCode.UserDefinedFunctions.[FindInvalidEmails];  
go  
  
SELECT * FROM FindInvalidEmails('2000-01-01');  
go  
```  
  
