---
title: 访问当前事务 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b7e67d30cb9d89a02eb918fcd03651b2915955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693989"
---
# <a name="accessing-the-current-transaction"></a><span data-ttu-id="e803c-102">访问当前事务</span><span class="sxs-lookup"><span data-stu-id="e803c-102">Accessing the Current Transaction</span></span>
  <span data-ttu-id="e803c-103">如果在输入运行于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上的公共语言运行时 (CLR) 代码时某事务是活动的，则该事务通过 `System.Transactions.Transaction` 类公开。</span><span class="sxs-lookup"><span data-stu-id="e803c-103">If a transaction is active at the point at which common language runtime (CLR) code running on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is entered, the transaction is exposed through the `System.Transactions.Transaction` class.</span></span> <span data-ttu-id="e803c-104">`Transaction.Current` 属性用于访问当前事务。</span><span class="sxs-lookup"><span data-stu-id="e803c-104">The `Transaction.Current` property is used to access the current transaction.</span></span> <span data-ttu-id="e803c-105">在大多数情况下，不必显式访问事务。</span><span class="sxs-lookup"><span data-stu-id="e803c-105">In most cases it is not necessary to access the transaction explicitly.</span></span> <span data-ttu-id="e803c-106">对于数据库连接，ADO.NET 将在调用 `Transaction.Current` 方法时自动检查 `Connection.Open`，并在该事务中以透明方式登记连接（除非在连接字符串中将 `Enlist` 关键字设置为 false）。</span><span class="sxs-lookup"><span data-stu-id="e803c-106">For database connections, ADO.NET checks `Transaction.Current` automatically when the `Connection.Open` method is called, and transparently enlists the connection in that transaction (unless the `Enlist` keyword is set to false in the connection string).</span></span>  
  
 <span data-ttu-id="e803c-107">在以下情形中，可能需要直接使用 `Transaction` 对象：</span><span class="sxs-lookup"><span data-stu-id="e803c-107">You might want to use the `Transaction` object directly in the following scenarios:</span></span>  
  
-   <span data-ttu-id="e803c-108">如果您要登记未自动登记的资源或因为某个原因而未在初始化期间登记的资源。</span><span class="sxs-lookup"><span data-stu-id="e803c-108">If you want to enlist a resource that does not do automatic enlistment, or that for some reason was not enlisted during initialization.</span></span>  
  
-   <span data-ttu-id="e803c-109">如果您要显式登记事务中的资源。</span><span class="sxs-lookup"><span data-stu-id="e803c-109">If you want to explicitly enlist a resource in the transaction.</span></span>  
  
-   <span data-ttu-id="e803c-110">如果您要从存储过程或函数的内部终止外部事务。</span><span class="sxs-lookup"><span data-stu-id="e803c-110">If you want to terminate the external transaction from within your stored procedure or function.</span></span> <span data-ttu-id="e803c-111">在这种情况下，使用 <xref:System.Transactions.TransactionScope>。</span><span class="sxs-lookup"><span data-stu-id="e803c-111">In this case, you use <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="e803c-112">例如，以下代码将回滚当前事务：</span><span class="sxs-lookup"><span data-stu-id="e803c-112">For example, the following code will rollback the current transaction:</span></span>  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 <span data-ttu-id="e803c-113">本主题的其余内容介绍取消外部事务的其他方式。</span><span class="sxs-lookup"><span data-stu-id="e803c-113">The rest of this topic describes other ways to cancel an external transaction.</span></span>  
  
## <a name="canceling-an-external-transaction"></a><span data-ttu-id="e803c-114">取消外部事务</span><span class="sxs-lookup"><span data-stu-id="e803c-114">Canceling an External Transaction</span></span>  
 <span data-ttu-id="e803c-115">可以用以下方式从托管过程或函数取消外部事务：</span><span class="sxs-lookup"><span data-stu-id="e803c-115">You can cancel external transactions from a managed procedure or function in the following ways:</span></span>  
  
-   <span data-ttu-id="e803c-116">通过使用输出参数，托管过程或函数可以返回值。</span><span class="sxs-lookup"><span data-stu-id="e803c-116">The managed procedure or function can return a value by using an output parameter.</span></span> <span data-ttu-id="e803c-117">调用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 过程可以检查返回的值，如果适合，则执行 `ROLLBACK TRANSACTION`。</span><span class="sxs-lookup"><span data-stu-id="e803c-117">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can check the returned value and, if appropriate, execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="e803c-118">托管过程或函数可以引发自定义异常。</span><span class="sxs-lookup"><span data-stu-id="e803c-118">The managed procedure or function can throw a custom exception.</span></span> <span data-ttu-id="e803c-119">调用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 过程可以捕获由 try/catch 块中的托管过程或函数引发的异常并执行 `ROLLBACK TRANSACTION` 。</span><span class="sxs-lookup"><span data-stu-id="e803c-119">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can catch the exception thrown by the managed procedure or function in a try/catch block and execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="e803c-120">如果满足某个条件，则托管过程或函数可以通过调用 `Transaction.Rollback` 方法取消当前事务。</span><span class="sxs-lookup"><span data-stu-id="e803c-120">The managed procedure or function can cancel the current transaction by calling the `Transaction.Rollback` method if a certain condition is met.</span></span>  
  
 <span data-ttu-id="e803c-121">如果在管理过程或函数内调用 `Transaction.Rollback` 方法，则此方法将引发包含不明确错误消息的异常，并且可以包装在 try/catch 块中。</span><span class="sxs-lookup"><span data-stu-id="e803c-121">When it is called within a managed procedure or function, the `Transaction.Rollback` method throws an exception with an ambiguous error message and can be wrapped in a try/catch block.</span></span> <span data-ttu-id="e803c-122">错误消息类似于以下内容：</span><span class="sxs-lookup"><span data-stu-id="e803c-122">The error message thresembles similar to the following:</span></span>  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 <span data-ttu-id="e803c-123">应出现该异常，而且需要 try/catch 块才能继续执行代码。</span><span class="sxs-lookup"><span data-stu-id="e803c-123">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="e803c-124">如果没有 try/catch 块，则立即对调用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 过程引发异常，并将完成托管代码的执行。</span><span class="sxs-lookup"><span data-stu-id="e803c-124">Without the try/catch block, the exception will be immediately thrown to the calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure and managed code execution will finish.</span></span> <span data-ttu-id="e803c-125">执行完托管代码时，将引发另一个异常：</span><span class="sxs-lookup"><span data-stu-id="e803c-125">When the managed code finishes execution, another exception is raised:</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 <span data-ttu-id="e803c-126">也应出现该异常，并且为了让执行得以继续，在执行激发触发器的操作的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句周围必须有 try/catch 块。</span><span class="sxs-lookup"><span data-stu-id="e803c-126">This exception is also expected, and for execution to continue, you must have a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger.</span></span> <span data-ttu-id="e803c-127">尽管引发了两个异常，但事务将回滚，并且不提交更改。</span><span class="sxs-lookup"><span data-stu-id="e803c-127">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e803c-128">示例</span><span class="sxs-lookup"><span data-stu-id="e803c-128">Example</span></span>  
 <span data-ttu-id="e803c-129">下面是通过使用 `Transaction.Rollback` 方法从托管过程回滚事务的示例。</span><span class="sxs-lookup"><span data-stu-id="e803c-129">The following is an example of a transaction being rolled back from a managed procedure by using the `Transaction.Rollback` method.</span></span> <span data-ttu-id="e803c-130">请注意在托管代码中 `Transaction.Rollback` 方法周围的 try/catch 块。</span><span class="sxs-lookup"><span data-stu-id="e803c-130">Notice the try/catch block around the `Transaction.Rollback` method in the managed code.</span></span> <span data-ttu-id="e803c-131">此 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本创建了一个程序集和托管存储过程。</span><span class="sxs-lookup"><span data-stu-id="e803c-131">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates an assembly and managed stored procedure.</span></span> <span data-ttu-id="e803c-132">请注意，该 `EXEC uspRollbackFromProc` 语句包装在 try/catch 块中，以便捕获托管过程完成执行时引发的异常。</span><span class="sxs-lookup"><span data-stu-id="e803c-132">Be aware that the `EXEC uspRollbackFromProc` statement is wrapped in a try/catch block, so that the exception thrown when the managed procedure completes execution is caught.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="e803c-133">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="e803c-133">**Transact-SQL**</span></span>  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="e803c-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e803c-134">See Also</span></span>  
 [<span data-ttu-id="e803c-135">CLR 集成和事务</span><span class="sxs-lookup"><span data-stu-id="e803c-135">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
