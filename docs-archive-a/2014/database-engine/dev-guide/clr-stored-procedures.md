---
title: CLR 存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f8c69435e28bfa67c72e26b7a54e419cd91ef220
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579736"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="5543b-102">CLR 存储过程</span><span class="sxs-lookup"><span data-stu-id="5543b-102">CLR Stored Procedures</span></span>
  <span data-ttu-id="5543b-103">存储过程是不能用于标量表达式的例程。</span><span class="sxs-lookup"><span data-stu-id="5543b-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="5543b-104">与标量函数不同，存储过程可以向客户端返回表格结果和消息、调用数据定义语言 (DDL) 和数据操作语言 (DML) 语句并返回输出参数。</span><span class="sxs-lookup"><span data-stu-id="5543b-104">Unlike scalar functions, they can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span> <span data-ttu-id="5543b-105">有关 CLR 集成的优点以及如何在托管代码和之间进行选择的信息 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，请参阅[Clr 集成概述](../../relational-databases/clr-integration/clr-integration-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5543b-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-stored-procedures"></a><span data-ttu-id="5543b-106">CLR 存储过程的要求</span><span class="sxs-lookup"><span data-stu-id="5543b-106">Requirements for CLR Stored Procedures</span></span>  
 <span data-ttu-id="5543b-107">在公共语言运行时 (CLR) 中，存储过程作为程序集中类的公共静态方法实现 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5543b-107">In the common language runtime (CLR), stored procedures are implemented as public static methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assembly.</span></span> <span data-ttu-id="5543b-108">该静态方法可以声明为 void，或者返回整数值。</span><span class="sxs-lookup"><span data-stu-id="5543b-108">The static method can either be declared as void, or return an integer value.</span></span> <span data-ttu-id="5543b-109">如果它返回某一整数值，则返回的整数将视作来自该存储过程的返回代码。</span><span class="sxs-lookup"><span data-stu-id="5543b-109">If it returns an integer value, the integer returned is treated as the return code from the procedure.</span></span> <span data-ttu-id="5543b-110">例如：</span><span class="sxs-lookup"><span data-stu-id="5543b-110">For example:</span></span>  
  
 `EXECUTE @return_status = procedure_name`  
  
 <span data-ttu-id="5543b-111">@return_status变量将包含方法返回的值。</span><span class="sxs-lookup"><span data-stu-id="5543b-111">The @return_status variable will contain the value returned by the method.</span></span> <span data-ttu-id="5543b-112">如果该方法声明为 void，则返回代码是 0。</span><span class="sxs-lookup"><span data-stu-id="5543b-112">If the method is declared void, the return code is 0.</span></span>  
  
 <span data-ttu-id="5543b-113">如果该方法具有参数，则 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 实现中的参数数目应与该存储过程的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 声明中使用的参数数目相同。</span><span class="sxs-lookup"><span data-stu-id="5543b-113">If the method takes parameters, the number of parameters in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementation should be the same as the number of parameters used in the [!INCLUDE[tsql](../../includes/tsql-md.md)] declaration of the stored procedure.</span></span>  
  
 <span data-ttu-id="5543b-114">传递到 CLR 存储过程的参数可以是在托管代码中具有等效值的任何本机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型。</span><span class="sxs-lookup"><span data-stu-id="5543b-114">Parameters passed to a CLR stored procedure can be any of the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types that have an equivalent in managed code.</span></span> <span data-ttu-id="5543b-115">对于用于创建该过程的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法，应该使用最合适的等效本机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型指定这些类型。</span><span class="sxs-lookup"><span data-stu-id="5543b-115">For the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax to create the procedure, these types should be specified with the most appropriate native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type equivalent.</span></span> <span data-ttu-id="5543b-116">有关类型转换的详细信息，请参阅[映射 CLR 参数数据](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5543b-116">For more information about type conversions, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="5543b-117">表值参数</span><span class="sxs-lookup"><span data-stu-id="5543b-117">Table-Valued Parameters</span></span>  
 <span data-ttu-id="5543b-118">表值参数 (TVP) 即传递到某一过程或函数的用户定义表类型，它提供了一种将多行数据传递到服务器的高效方法。</span><span class="sxs-lookup"><span data-stu-id="5543b-118">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="5543b-119">TVP 提供与参数数组类似的功能，但灵活性更高并且与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的集成更紧密。</span><span class="sxs-lookup"><span data-stu-id="5543b-119">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5543b-120">它们还提供提升性能的潜力。</span><span class="sxs-lookup"><span data-stu-id="5543b-120">They also provide the potential for better performance.</span></span> <span data-ttu-id="5543b-121">TVP 还有助于减少到服务器的往返次数。</span><span class="sxs-lookup"><span data-stu-id="5543b-121">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="5543b-122">可以将数据作为 TVP 发送到服务器，而不是向服务器发送多个请求（例如，对于标量参数列表）。</span><span class="sxs-lookup"><span data-stu-id="5543b-122">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="5543b-123">用户定义表类型不能作为表值参数传递到在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程中执行的托管存储过程或函数，也不能从这些存储过程或函数中返回。</span><span class="sxs-lookup"><span data-stu-id="5543b-123">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="5543b-124">有关 Tvp 的详细信息，请参阅[&#40;数据库引擎使用表值参数&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="5543b-124">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="returning-results-from-clr-stored-procedures"></a><span data-ttu-id="5543b-125">从 CLR 存储过程中返回结果</span><span class="sxs-lookup"><span data-stu-id="5543b-125">Returning Results from CLR Stored Procedures</span></span>  
 <span data-ttu-id="5543b-126">信息可通过若干方式从 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 存储过程返回。</span><span class="sxs-lookup"><span data-stu-id="5543b-126">Information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures in several ways.</span></span> <span data-ttu-id="5543b-127">这包括输出参数、表格结果和消息。</span><span class="sxs-lookup"><span data-stu-id="5543b-127">This includes output parameters, tabular results, and messages.</span></span>  
  
### <a name="output-parameters-and-clr-stored-procedures"></a><span data-ttu-id="5543b-128">OUTPUT 参数和 CLR 存储过程</span><span class="sxs-lookup"><span data-stu-id="5543b-128">OUTPUT Parameters and CLR Stored Procedures</span></span>  
 <span data-ttu-id="5543b-129">与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程一样，信息可通过使用 OUTPUT 参数从 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 存储过程返回。</span><span class="sxs-lookup"><span data-stu-id="5543b-129">As with [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures using OUTPUT parameters.</span></span> <span data-ttu-id="5543b-130">用于创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] DML 语法与用于创建使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 撰写的存储过程相同。</span><span class="sxs-lookup"><span data-stu-id="5543b-130">The [!INCLUDE[tsql](../../includes/tsql-md.md)] DML syntax used for creating [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures is the same as that used for creating stored procedures written in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5543b-131">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类中实现代码的相应参数应将传址调用参数用作参数。</span><span class="sxs-lookup"><span data-stu-id="5543b-131">The corresponding parameter in the implementation code in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="5543b-132">请注意，Visual Basic 不支持采用与 c # 相同的方式来输出参数。</span><span class="sxs-lookup"><span data-stu-id="5543b-132">Note that Visual Basic does not support output parameters in the same way that C# does.</span></span> <span data-ttu-id="5543b-133">必须按引用指定参数，并应用 \<Out()> 属性以表示输出参数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5543b-133">You must specify the parameter by reference and apply the \<Out()> attribute to represent an OUTPUT parameter, as in the following:</span></span>  
  
```vb
Imports System.Runtime.InteropServices  
...  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 <span data-ttu-id="5543b-134">以下示例显示通过 OUTPUT 参数返回信息的存储过程。</span><span class="sxs-lookup"><span data-stu-id="5543b-134">The following shows a stored procedure returning information through an OUTPUT parameter:</span></span>  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5543b-135">在服务器上生成并创建了包含上述 CLR 存储过程的程序集后，将使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 方法在数据库中创建该过程，并将*sum*指定为输出参数。</span><span class="sxs-lookup"><span data-stu-id="5543b-135">Once the assembly containing the above CLR stored procedure has been built and created on the server, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] is used to create the procedure in the database, and specifies *sum* as an OUTPUT parameter.</span></span>  
  
```sql
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 <span data-ttu-id="5543b-136">请注意， *sum*声明为 `int` SQL Server 数据类型，并且 clr 存储过程中定义的*值*参数指定为 `SqlInt32` clr 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5543b-136">Note that *sum* is declared as an `int` SQL Server data type, and that the *value* parameter defined in the CLR stored procedure is specified as a `SqlInt32` CLR data type.</span></span> <span data-ttu-id="5543b-137">当调用程序执行 CLR 存储过程时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会自动将 `SqlInt32` clr 数据类型转换为 `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5543b-137">When a calling program executes the CLR stored procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically converts the `SqlInt32` CLR data type to an `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  <span data-ttu-id="5543b-138">有关可以转换和不能转换哪些 CLR 数据类型的详细信息，请参阅[映射 Clr 参数数据](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5543b-138">For more information about which CLR data types can and cannot be converted, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="5543b-139">返回表格结果和消息</span><span class="sxs-lookup"><span data-stu-id="5543b-139">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="5543b-140">将表格结果和消息返回到客户端通过 `SqlPipe` 对象执行，该对象通过使用 `Pipe` 类的 `SqlContext` 属性获取。</span><span class="sxs-lookup"><span data-stu-id="5543b-140">Returning tabular results and messages to the client is done through the `SqlPipe` object, which is obtained by using the `Pipe` property of the `SqlContext` class.</span></span> <span data-ttu-id="5543b-141">`SqlPipe` 对象具有 `Send` 方法。</span><span class="sxs-lookup"><span data-stu-id="5543b-141">The `SqlPipe` object has a `Send` method.</span></span> <span data-ttu-id="5543b-142">通过调用 `Send` 方法，您可以通过管道将数据传输到调用应用程序。</span><span class="sxs-lookup"><span data-stu-id="5543b-142">By calling the `Send` method, you can transmit data through the pipe to the calling application.</span></span>  
  
 <span data-ttu-id="5543b-143">下面是 `SqlPipe.Send` 方法的若干重载，包括发送 `SqlDataReader` 的一个方法以及只发送文本字符串的另一个方法。</span><span class="sxs-lookup"><span data-stu-id="5543b-143">These are several overloads of the `SqlPipe.Send` method, including one that sends a `SqlDataReader` and another that simply sends a text string.</span></span>  
  
###### <a name="returning-messages"></a><span data-ttu-id="5543b-144">返回消息</span><span class="sxs-lookup"><span data-stu-id="5543b-144">Returning Messages</span></span>  
 <span data-ttu-id="5543b-145">使用 `SqlPipe.Send(string)` 可以将消息发送到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="5543b-145">Use `SqlPipe.Send(string)` to send messages to the client application.</span></span> <span data-ttu-id="5543b-146">消息文本限制在 8000 个字符以内。</span><span class="sxs-lookup"><span data-stu-id="5543b-146">The text of the message is limited to 8000 characters.</span></span> <span data-ttu-id="5543b-147">如果消息超出 8000 个字符，该消息将被截断。</span><span class="sxs-lookup"><span data-stu-id="5543b-147">If the message exceeds 8000 characters, it will be truncated.</span></span>  
  
###### <a name="returning-tabular-results"></a><span data-ttu-id="5543b-148">返回表格结果</span><span class="sxs-lookup"><span data-stu-id="5543b-148">Returning Tabular Results</span></span>  
 <span data-ttu-id="5543b-149">若要将查询的结果直接发送到客户端，请对 `Execute` 对象使用 `SqlPipe` 方法的重载之一。</span><span class="sxs-lookup"><span data-stu-id="5543b-149">To send the results of a query directly to the client, use one of the overloads of the `Execute` method on the `SqlPipe` object.</span></span> <span data-ttu-id="5543b-150">这是将结果返回到客户端的最高效方法，因为数据不必复制到托管内存即传输到网络缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5543b-150">This is the most efficient way to return results to the client, since the data is transferred to the network buffers without being copied into managed memory.</span></span> <span data-ttu-id="5543b-151">例如：</span><span class="sxs-lookup"><span data-stu-id="5543b-151">For example:</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5543b-152">若要通过进程内提供程序发送以前已执行的查询结果（或者使用 `SqlDataReader` 的自定义实现对数据进行预处理），则使用采用 `Send` 的 `SqlDataReader` 方法的重载。</span><span class="sxs-lookup"><span data-stu-id="5543b-152">To send the results of a query that was executed previously through the in-process provider (or to pre-process the data using a custom implementation of `SqlDataReader`), use the overload of the `Send` method that takes a `SqlDataReader`.</span></span> <span data-ttu-id="5543b-153">此方法在速度上稍慢于前面所述的直接方法，但它提供更高的灵活性，以便在将数据发送到客户端之前操作数据。</span><span class="sxs-lookup"><span data-stu-id="5543b-153">This method is slightly slower than the direct method described previously, but it offers greater flexibility to manipulate the data before it is sent to the client.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
 
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5543b-154">若要创建动态结果集，请填充该结果集并将其发送到客户端，您可以通过当前连接创建记录并且使用 `SqlPipe.Send` 发送它们。</span><span class="sxs-lookup"><span data-stu-id="5543b-154">To create a dynamic result set, populate it and send it to the client, you can create records from the current connection and send them using `SqlPipe.Send`.</span></span>  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 <span data-ttu-id="5543b-155">下面是通过 `SqlPipe` 发送表格结果和消息的示例。</span><span class="sxs-lookup"><span data-stu-id="5543b-155">Here is an example of sending a tabular result and a message through `SqlPipe`.</span></span>  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 <span data-ttu-id="5543b-156">第一个 `Send` 将消息发送到客户端，第二个则使用 `SqlDataReader` 发送表格结果。</span><span class="sxs-lookup"><span data-stu-id="5543b-156">The first `Send` sends a message to the client, while the second sends a tabular result using `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="5543b-157">请注意，这些示例只用于说明用途。</span><span class="sxs-lookup"><span data-stu-id="5543b-157">Note that these examples are for illustrative purposes only.</span></span> <span data-ttu-id="5543b-158">对于执行大量计算的应用程序，CLR 函数比简单的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句更合适。</span><span class="sxs-lookup"><span data-stu-id="5543b-158">CLR functions are more appropriate than simple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for computation-intensive applications.</span></span> <span data-ttu-id="5543b-159">与前一示例几乎等效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程是：</span><span class="sxs-lookup"><span data-stu-id="5543b-159">An almost equivalent [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure to the previous example is:</span></span>  
  
```sql
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  <span data-ttu-id="5543b-160">消息和结果集在客户端应用程序中以不同的方式检索。</span><span class="sxs-lookup"><span data-stu-id="5543b-160">Messages and result sets are retrieved differently in the client application.</span></span> <span data-ttu-id="5543b-161">例如， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 结果集将显示在 "**结果**" 视图中，消息将显示在 "**消息**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="5543b-161">For instance, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] result sets appear in the **Results** view, and messages appear in the **Messages** pane.</span></span>  
  
 <span data-ttu-id="5543b-162">如果以上 Visual C# 代码保存在 MyFirstUdp.cs 文件中并且使用以下语句编译：</span><span class="sxs-lookup"><span data-stu-id="5543b-162">If the above Visual C# code is saved in a file MyFirstUdp.cs and compiled with:</span></span>  
  
```console
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 <span data-ttu-id="5543b-163">或者，如果以上 Visual Basic 代码保存在 MyFirstUdp.vb 文件中并且使用以下语句编译：</span><span class="sxs-lookup"><span data-stu-id="5543b-163">Or, if the above Visual Basic code is saved in a file MyFirstUdp.vb and compiled with:</span></span>  
  
```console
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  <span data-ttu-id="5543b-164">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，不再支持执行使用 `/clr:pure` 编译的 Visual C++ 数据库对象（例如存储过程）。</span><span class="sxs-lookup"><span data-stu-id="5543b-164">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], Visual C++ database objects (such as stored procedures) compiled with `/clr:pure` are not supported for execution.</span></span>  
  
 <span data-ttu-id="5543b-165">可以使用以下 DDL 注册最终生成的程序集，以及调用的入口点：</span><span class="sxs-lookup"><span data-stu-id="5543b-165">The resulting assembly can be registered, and the entry point invoked, with the following DDL:</span></span>  
  
```sql
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a><span data-ttu-id="5543b-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5543b-166">See Also</span></span>  
 <span data-ttu-id="5543b-167">[CLR 用户定义函数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="5543b-167">[CLR User-Defined Functions](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="5543b-168">[CLR 用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="5543b-168">[CLR User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 [<span data-ttu-id="5543b-169">CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="5543b-169">CLR Triggers</span></span>](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  
