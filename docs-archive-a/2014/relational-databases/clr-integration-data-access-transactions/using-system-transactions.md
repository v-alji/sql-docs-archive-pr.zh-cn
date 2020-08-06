---
title: 使用 system.exception |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
author: rothja
ms.author: jroth
ms.openlocfilehash: 277edd75ea0437dc532ed5672e3c7b8a0569af8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693980"
---
# <a name="using-systemtransactions"></a><span data-ttu-id="e7c69-102">使用 System.Transactions</span><span class="sxs-lookup"><span data-stu-id="e7c69-102">Using System.Transactions</span></span>
  <span data-ttu-id="e7c69-103">`System.Transactions` 命名空间提供与 ADO.NET 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公共语言运行时 (CLR) 集成完全集成的新事务框架。</span><span class="sxs-lookup"><span data-stu-id="e7c69-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="e7c69-104">`System.Transactions.TransactionScope` 类通过在分布式事务中隐式登记连接，使代码块成为事务代码。</span><span class="sxs-lookup"><span data-stu-id="e7c69-104">The `System.Transactions.TransactionScope` class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="e7c69-105">您必须在 `Complete` 标记的代码块的末尾调用 `TransactionScope` 方法。</span><span class="sxs-lookup"><span data-stu-id="e7c69-105">You must call the `Complete` method at the end of the code block marked by the `TransactionScope`.</span></span> <span data-ttu-id="e7c69-106">如果未调用 `Dispose` 方法，将在程序执行离开代码块时调用 `Complete` 方法，从而导致停止使用该事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-106">The `Dispose` method is invoked when program execution leaves a code block, causing the transaction to be discontinued if the `Complete` method is not called.</span></span> <span data-ttu-id="e7c69-107">如果已引发导致代码离开范围的异常，则将该事务视为停止使用。</span><span class="sxs-lookup"><span data-stu-id="e7c69-107">If an exception has been thrown that causes the code to leave scope, the transaction is considered to be discontinued.</span></span>  
  
 <span data-ttu-id="e7c69-108">建议您使用 `using` 块，以便确保在退出 `Dispose` 块时对 `TransactionScope` 对象调用 `using` 方法。</span><span class="sxs-lookup"><span data-stu-id="e7c69-108">We recommend that you employ a `using` block to ensure that the `Dispose` method is called on the `TransactionScope` object when the `using` block is exited.</span></span> <span data-ttu-id="e7c69-109">提交或回滚挂起事务失败可能会严重降低性能，因为 `TransactionScope` 的默认超时值为 1 分钟。</span><span class="sxs-lookup"><span data-stu-id="e7c69-109">Failure to commit or roll back pending transactions can seriously degrade performance because the default time-out for the `TransactionScope` is one minute.</span></span> <span data-ttu-id="e7c69-110">如果未使用 `using` 语句，必须在 `Try` 块中执行所有工作，并在 `Dispose` 块中显式调用 `Finally` 方法。</span><span class="sxs-lookup"><span data-stu-id="e7c69-110">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the `Dispose` method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="e7c69-111">如果在 `TransactionScope` 内发生异常，则将该事务标记为不一致，并放弃使用该事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-111">If an exception occurs within the `TransactionScope`, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="e7c69-112">释放 `TransactionScope` 时将回滚该事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-112">It is rolled back when the `TransactionScope` is disposed.</span></span> <span data-ttu-id="e7c69-113">如果未发生异常，则提交参与的事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-113">If no exception occurs, participating transactions commit.</span></span>  
  
 <span data-ttu-id="e7c69-114">仅当正在访问本机和远程数据源或外部资源管理器时，才应使用 `TransactionScope`。</span><span class="sxs-lookup"><span data-stu-id="e7c69-114">`TransactionScope` should be used only when local and remote data sources or external resource managers are being accessed.</span></span> <span data-ttu-id="e7c69-115">这是因为 `TransactionScope` 始终导致提升事务，即使仅在上下文连接内使用该事务也是如此。</span><span class="sxs-lookup"><span data-stu-id="e7c69-115">This is because `TransactionScope` always causes transactions to promote, even if it is being used only within a context connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7c69-116">默认情况下，`TransactionScope` 类创建 `System.Transactions.Transaction.IsolationLevel` 为 `Serializable` 的事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-116">The `TransactionScope` class creates a transaction with a `System.Transactions.Transaction.IsolationLevel` of `Serializable` by default.</span></span> <span data-ttu-id="e7c69-117">根据您的应用程序，您可能希望考虑降低隔离级别，以避免在应用程序中发生争用激烈的情况。</span><span class="sxs-lookup"><span data-stu-id="e7c69-117">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7c69-118">建议您在分布式事务内针对远程服务器仅执行更新、插入和删除操作，因为这些操作占用大量数据库资源。</span><span class="sxs-lookup"><span data-stu-id="e7c69-118">We recommend that you perform only updates, inserts, and deletes within distributed transactions against remote servers because they consume significant database resources.</span></span> <span data-ttu-id="e7c69-119">如果将在本地服务器上执行该操作，则不需要分布式事务，而使用本地事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-119">If the operation is going to be performed on the local server, a distributed transaction is not necessary and a local transaction will suffice.</span></span> <span data-ttu-id="e7c69-120">SELECT 语句可能会不必要地锁定数据库资源，在某些情况下，可能必须使用事务进行选择。</span><span class="sxs-lookup"><span data-stu-id="e7c69-120">SELECT statements may lock database resources unnecessarily, and in some scenarios it may be necessary to use transactions for selects.</span></span> <span data-ttu-id="e7c69-121">应在事务范围之外执行任何非数据库工作，除非它涉及其他事务资源管理器。</span><span class="sxs-lookup"><span data-stu-id="e7c69-121">Any non-database work should be done outside of the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="e7c69-122">虽然事务范围内的异常可以避免提交该事务，但是 `TransactionScope` 类无法回滚在该事务自身范围之外对代码所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="e7c69-122">Although an exception within the scope of the transaction prevents the transaction from committing, the `TransactionScope` class has no provision for rolling back any changes your code has made outside of the scope of the transaction itself.</span></span> <span data-ttu-id="e7c69-123">如果需要在事务回滚时采取某一操作，必须写入您自己的 `System.Transactions.IEnlistmentNotification` 接口实现，并在该事务中显式登记。</span><span class="sxs-lookup"><span data-stu-id="e7c69-123">If you need to take some action when the transaction is rolled back, you must write your own implementation of the `System.Transactions.IEnlistmentNotification` interface, and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7c69-124">示例</span><span class="sxs-lookup"><span data-stu-id="e7c69-124">Example</span></span>  
 <span data-ttu-id="e7c69-125">若要使用 `System.Transactions`，必须引用 System.Transactions.dll 文件。</span><span class="sxs-lookup"><span data-stu-id="e7c69-125">To work with `System.Transactions`, you must have a reference to the System.Transactions.dll file.</span></span>  
  
 <span data-ttu-id="e7c69-126">下面的代码演示如何创建可根据两个不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例进行提升的事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-126">The following code demonstrates how to create a transaction that can be promoted against two different instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7c69-127">这些实例由两个不同的 `System.Data.SqlClient.SqlConnection` 对象表示，它们包装在 `TransactionScope` 块中。</span><span class="sxs-lookup"><span data-stu-id="e7c69-127">These instances are represented by two different `System.Data.SqlClient.SqlConnection` objects, which are wrapped in a `TransactionScope` block.</span></span> <span data-ttu-id="e7c69-128">该代码创建带有 `TransactionScope` 语句的 `using` 块，并打开第一个在 `TransactionScope` 中自动登记的连接。</span><span class="sxs-lookup"><span data-stu-id="e7c69-128">The code creates the `TransactionScope` block with a `using` statement, and opens the first connection, which automatically enlists it in the `TransactionScope`.</span></span> <span data-ttu-id="e7c69-129">该事务最初作为轻型事务登记，而不是完全分布式事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-129">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="e7c69-130">代码假定存在条件逻辑（为简洁起见，已省略该逻辑）。</span><span class="sxs-lookup"><span data-stu-id="e7c69-130">The code assumes the existence of conditional logic (which has been omitted for brevity).</span></span> <span data-ttu-id="e7c69-131">代码仅在需要时打开第二个连接，并在 `TransactionScope` 中登记。</span><span class="sxs-lookup"><span data-stu-id="e7c69-131">It opens the second connection only if it is needed, enlisting it in the `TransactionScope`.</span></span> <span data-ttu-id="e7c69-132">打开该连接后，事务将自动提升为完全分布式事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-132">When the connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="e7c69-133">该代码随后调用 `TransactionScope.Complete`，这将提交事务。</span><span class="sxs-lookup"><span data-stu-id="e7c69-133">The code then invokes `TransactionScope.Complete`, which commits the transaction.</span></span> <span data-ttu-id="e7c69-134">当退出连接的 `using` 语句时，代码释放两个连接。</span><span class="sxs-lookup"><span data-stu-id="e7c69-134">The code disposes of the two connections when exiting the `using` statements for the connections.</span></span> <span data-ttu-id="e7c69-135">`TransactionScope.Dispose` 的 `TransactionScope` 块终止时，将自动调用 `using` 的 `TransactionScope` 方法。</span><span class="sxs-lookup"><span data-stu-id="e7c69-135">The `TransactionScope.Dispose` method for the `TransactionScope` is automatically called at the termination of the `using` block for the `TransactionScope`.</span></span> <span data-ttu-id="e7c69-136">如果在 `TransactionScope` 块的任一点引发异常，则不会调用 `Complete`，并且分布式事务将在释放 `TransactionScope` 时回滚。</span><span class="sxs-lookup"><span data-stu-id="e7c69-136">If an exception has been thrown at any point in the `TransactionScope` block, `Complete` does not get called, and the distributed transaction will roll back when the `TransactionScope` is disposed.</span></span>  
  
 <span data-ttu-id="e7c69-137">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7c69-137">Visual Basic</span></span>  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 <span data-ttu-id="e7c69-138">C#</span><span class="sxs-lookup"><span data-stu-id="e7c69-138">C#</span></span>  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7c69-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7c69-139">See Also</span></span>  
 [<span data-ttu-id="e7c69-140">CLR 集成和事务</span><span class="sxs-lookup"><span data-stu-id="e7c69-140">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
