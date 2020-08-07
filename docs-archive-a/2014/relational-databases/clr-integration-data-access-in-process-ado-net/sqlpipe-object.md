---
title: SqlPipe 对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 0044815a0b20d72b48b87bfe8f693d7196aaeaf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587864"
---
# <a name="sqlpipe-object"></a><span data-ttu-id="26264-102">SqlPipe 对象</span><span class="sxs-lookup"><span data-stu-id="26264-102">SqlPipe Object</span></span>
  <span data-ttu-id="26264-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本中，编写向调用客户端发送结果或输出参数的存储过程（或扩展存储过程）非常常见。</span><span class="sxs-lookup"><span data-stu-id="26264-103">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is very common to write a stored procedure (or an extended stored procedure) that sends results or output parameters to the calling client.</span></span>  
  
 <span data-ttu-id="26264-104">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程中，返回零个或多个行的所有 `SELECT` 语句将结果发送到连接调用方的“管道”中。</span><span class="sxs-lookup"><span data-stu-id="26264-104">In a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, any `SELECT` statement that returns zero or more rows sends the results to the connected caller's "pipe."</span></span>  
  
 <span data-ttu-id="26264-105">对于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中运行的公共语言运行时 (CLR) 数据库对象，您可以使用 `Send` 对象的 `SqlPipe` 方法将结果发送到连接的管道中。</span><span class="sxs-lookup"><span data-stu-id="26264-105">For common language runtime (CLR) database objects running in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can send results to the connected pipe using the `Send` methods of the `SqlPipe` object.</span></span> <span data-ttu-id="26264-106">访问 `Pipe` 对象的 `SqlContext` 属性可以获取 `SqlPipe` 对象。</span><span class="sxs-lookup"><span data-stu-id="26264-106">Access the `Pipe` property of the `SqlContext` object to obtain the `SqlPipe` object.</span></span> <span data-ttu-id="26264-107">从概念上来说，`SqlPipe` 类与 ASP.NET 中的 `Response` 类相似。</span><span class="sxs-lookup"><span data-stu-id="26264-107">The `SqlPipe` class is conceptually similar to the `Response` class found in ASP.NET.</span></span> <span data-ttu-id="26264-108">有关详细信息，请参阅 .NET Framework 软件开发包中的 SqlPipe 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="26264-108">For more information, see the SqlPipe Class reference documentation in the .NET Framework software development kit.</span></span>  
  
## <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="26264-109">返回表格结果和消息</span><span class="sxs-lookup"><span data-stu-id="26264-109">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="26264-110">`SqlPipe` 包含 `Send` 方法，该方法具有三次重载。</span><span class="sxs-lookup"><span data-stu-id="26264-110">The `SqlPipe` has a `Send` method, which has three overloads.</span></span> <span data-ttu-id="26264-111">它们分别是：</span><span class="sxs-lookup"><span data-stu-id="26264-111">They are:</span></span>  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 <span data-ttu-id="26264-112">`Send` 方法将数据直接发送到客户端或调用方。</span><span class="sxs-lookup"><span data-stu-id="26264-112">The `Send` method sends data straight to the client or caller.</span></span> <span data-ttu-id="26264-113">通常是客户端使用来自 `SqlPipe` 的输出，但在嵌套 CLR 存储过程的情况下，输出使用者也可以是存储过程。</span><span class="sxs-lookup"><span data-stu-id="26264-113">It is usually the client that consumes the output from the `SqlPipe`, but in the case of nested CLR stored procedures the output consumer can also be a stored procedure.</span></span> <span data-ttu-id="26264-114">例如，Procedure1 使用命令文本“EXEC Procedure2”调用 SqlCommand.ExecuteReader()。</span><span class="sxs-lookup"><span data-stu-id="26264-114">For example, Procedure1 calls SqlCommand.ExecuteReader() with the command text "EXEC Procedure2".</span></span> <span data-ttu-id="26264-115">Procedure2 也是托管存储过程。</span><span class="sxs-lookup"><span data-stu-id="26264-115">Procedure2 is also a managed stored procedure.</span></span> <span data-ttu-id="26264-116">如果现在 Procedure2 调用 SqlPipe.Send(SqlDataRecord)，则该行被发送到 Procedure1 的读取器，而不是客户端。</span><span class="sxs-lookup"><span data-stu-id="26264-116">If Procedure2 now calls SqlPipe.Send( SqlDataRecord ), the row is sent to Procedure1's reader, not the client.</span></span>  
  
 <span data-ttu-id="26264-117">`Send` 方法发送的字符串消息在客户端上显示为信息性消息，该方法等效于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的 PRINT。</span><span class="sxs-lookup"><span data-stu-id="26264-117">The `Send` method sends a string message that appears on the client as an information message, equivalent to PRINT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="26264-118">该方法还可以使用 `SqlDataRecord` 发送单行结果集，或者使用 `SqlDataReader` 发送多行结果集。</span><span class="sxs-lookup"><span data-stu-id="26264-118">It can also send a single-row result-set using `SqlDataRecord`, or a multi-row result-set using a `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="26264-119">`SqlPipe` 对象还具有 `ExecuteAndSend` 方法。</span><span class="sxs-lookup"><span data-stu-id="26264-119">The `SqlPipe` object also has an `ExecuteAndSend` method.</span></span> <span data-ttu-id="26264-120">可以使用此方法执行作为 `SqlCommand` 对象传递的命令，并将结果直接回发给调用方。</span><span class="sxs-lookup"><span data-stu-id="26264-120">This method can be used to execute a command (passed as a `SqlCommand` object) and send results directly back to the caller.</span></span> <span data-ttu-id="26264-121">如果已提交的命令中有错误，则将异常发送到管道，但同时将一个副本发送到调用托管代码。</span><span class="sxs-lookup"><span data-stu-id="26264-121">If there are errors in the command that was submitted, exceptions are sent to the pipe, but a copy is also sent to calling managed code.</span></span> <span data-ttu-id="26264-122">如果调用代码没有捕获异常，它会将堆栈传播到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码并两次出现在输出中。</span><span class="sxs-lookup"><span data-stu-id="26264-122">If the calling code does not catch the exception, it propagates up the stack to the [!INCLUDE[tsql](../../includes/tsql-md.md)] code and appears in the output twice.</span></span> <span data-ttu-id="26264-123">如果调用代码捕获了异常，则管道使用者仍将看到错误，但不会有重复错误。</span><span class="sxs-lookup"><span data-stu-id="26264-123">If the calling code does catch the exception, the pipe consumer still sees the error, but there is not a duplicate error.</span></span>  
  
 <span data-ttu-id="26264-124">该方法仅采用与上下文连接关联的 `SqlCommand`；但不能采用与非上下文连接关联的命令。</span><span class="sxs-lookup"><span data-stu-id="26264-124">It can only take a `SqlCommand` that is associated with the context connection; it cannot take a command that is associated with the non-context connection.</span></span>  
  
## <a name="returning-custom-result-sets"></a><span data-ttu-id="26264-125">返回自定义结果集</span><span class="sxs-lookup"><span data-stu-id="26264-125">Returning Custom Result Sets</span></span>  
 <span data-ttu-id="26264-126">托管存储过程可以发送并非来自于 `SqlDataReader` 的结果集。</span><span class="sxs-lookup"><span data-stu-id="26264-126">Managed stored procedures can send result sets that do not come from a `SqlDataReader`.</span></span> <span data-ttu-id="26264-127">`SendResultsStart` 方法以及 `SendResultsRow` 和 `SendResultsEnd` 允许存储过程将自定义结果集发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="26264-127">The `SendResultsStart` method, along with `SendResultsRow` and `SendResultsEnd`, allows stored procedures to send custom result sets to the client.</span></span>  
  
 <span data-ttu-id="26264-128">`SendResultsStart` 采用 `SqlDataRecord` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="26264-128">`SendResultsStart` takes a `SqlDataRecord` as an input.</span></span> <span data-ttu-id="26264-129">该方法标记结果集的开始，并使用记录元数据构造描述结果集的元数据。</span><span class="sxs-lookup"><span data-stu-id="26264-129">It marks the beginning of a result set and uses the record metadata to construct the metadata that describes the result set.</span></span> <span data-ttu-id="26264-130">它不会使用 `SendResultsStart` 发送记录的值。</span><span class="sxs-lookup"><span data-stu-id="26264-130">It does not send the value of the record with `SendResultsStart`.</span></span> <span data-ttu-id="26264-131">使用 `SendResultsRow` 发送的所有后续行都必须与该元数据定义相匹配。</span><span class="sxs-lookup"><span data-stu-id="26264-131">All the subsequent rows, sent using `SendResultsRow`, must match that metadata definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26264-132">在调用 `SendResultsStart` 方法之后，只能调用 `SendResultsRow` 和 `SendResultsEnd`。</span><span class="sxs-lookup"><span data-stu-id="26264-132">After calling the `SendResultsStart` method only `SendResultsRow` and `SendResultsEnd` can be called.</span></span> <span data-ttu-id="26264-133">在同一 `SqlPipe` 实例中调用任何其他方法将导致 `InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="26264-133">Calling any other method in the same instance of `SqlPipe` causes an `InvalidOperationException`.</span></span> <span data-ttu-id="26264-134">`SendResultsEnd` 将 `SqlPipe` 设置回初始状态，您可以在该状态下调用其他方法。</span><span class="sxs-lookup"><span data-stu-id="26264-134">`SendResultsEnd` sets `SqlPipe` back to the initial state in which other methods can be called.</span></span>  
  
### <a name="example"></a><span data-ttu-id="26264-135">示例</span><span class="sxs-lookup"><span data-stu-id="26264-135">Example</span></span>  
 <span data-ttu-id="26264-136">`uspGetProductLine` 存储过程返回指定产品系列中所有产品的名称、产品编号、颜色和标价。</span><span class="sxs-lookup"><span data-stu-id="26264-136">The `uspGetProductLine` stored procedure returns the name, product number, color, and list price of all products within a specified product line.</span></span> <span data-ttu-id="26264-137">此存储过程接受与*prodLine*完全匹配的项。</span><span class="sxs-lookup"><span data-stu-id="26264-137">This stored procedure accepts exact matches for *prodLine*.</span></span>  
  
 <span data-ttu-id="26264-138">C#</span><span class="sxs-lookup"><span data-stu-id="26264-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 <span data-ttu-id="26264-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26264-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="26264-140">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句执行 `uspGetProduct` 过程，这将返回旅行登山车产品的列表。</span><span class="sxs-lookup"><span data-stu-id="26264-140">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement executes the `uspGetProduct` procedure, which returns a list of touring bike products.</span></span>  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a><span data-ttu-id="26264-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26264-141">See Also</span></span>  
 <span data-ttu-id="26264-142">[SqlDataRecord 对象](sqldatarecord-object.md) </span><span class="sxs-lookup"><span data-stu-id="26264-142">[SqlDataRecord Object](sqldatarecord-object.md) </span></span>  
 <span data-ttu-id="26264-143">[CLR 存储过程](../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="26264-143">[CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="26264-144">SQL Server 进程内专用的 ADO.NET 扩展</span><span class="sxs-lookup"><span data-stu-id="26264-144">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
