---
title: SqlContext 对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f036e274925f7b28b79f619f8e24b3e8804140
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690651"
---
# <a name="sqlcontext-object"></a><span data-ttu-id="302a9-102">SqlContext 对象</span><span class="sxs-lookup"><span data-stu-id="302a9-102">SqlContext Object</span></span>
  <span data-ttu-id="302a9-103">当您调用过程或函数，或对公共语言运行时 (CLR) 用户定义类型调用方法，或者当您所执行的操作激发任何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 语言中定义的触发器时，您就会调用服务器中的托管代码。</span><span class="sxs-lookup"><span data-stu-id="302a9-103">You invoke managed code in the server when you call a procedure or function, when you call a method on a common language runtime (CLR) user-defined type, or when your action fires a trigger defined in any of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework languages.</span></span> <span data-ttu-id="302a9-104">由于在用户连接过程中需要执行此代码，因此需要从服务器上运行的代码访问调用方的上下文。</span><span class="sxs-lookup"><span data-stu-id="302a9-104">Because execution of this code is requested as part of a user connection, access to the context of the caller from the code running in the server is required.</span></span> <span data-ttu-id="302a9-105">此外，某些数据访问操作只有在调用方的上下文中运行时才有效。</span><span class="sxs-lookup"><span data-stu-id="302a9-105">In addition, certain data access operations may only be valid if run under the context of the caller.</span></span> <span data-ttu-id="302a9-106">例如，访问触发器操作中使用的插入和删除的伪表只在调用方的上下文中有效。</span><span class="sxs-lookup"><span data-stu-id="302a9-106">For example, access to inserted and deleted pseudo-tables used in trigger operations is only valid under the context of the caller.</span></span>  
  
 <span data-ttu-id="302a9-107">调用方的上下文是在 `SqlContext` 对象中提取的。</span><span class="sxs-lookup"><span data-stu-id="302a9-107">The context of the caller is abstracted in a `SqlContext` object.</span></span> <span data-ttu-id="302a9-108">有关 `SqlTriggerContext` 方法和属性的详细信息，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 中的 `Microsoft.SqlServer.Server.SqlTriggerContext` 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="302a9-108">For more information about the `SqlTriggerContext` methods and properties, see the `Microsoft.SqlServer.Server.SqlTriggerContext` class reference documentation in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="302a9-109">`SqlContext` 提供了对以下组件的访问：</span><span class="sxs-lookup"><span data-stu-id="302a9-109">`SqlContext` provides access to the following components:</span></span>  
  
-   <span data-ttu-id="302a9-110">`SqlPipe`：`SqlPipe` 对象表示结果流向客户端时所使用的“管道”。</span><span class="sxs-lookup"><span data-stu-id="302a9-110">`SqlPipe`: The `SqlPipe` object represents the "pipe" through which results flow to the client.</span></span> <span data-ttu-id="302a9-111">有关对象的详细信息 `SqlPipe` ，请参阅[SqlPipe 对象](sqlpipe-object.md)。</span><span class="sxs-lookup"><span data-stu-id="302a9-111">For more information about the `SqlPipe` object, see [SqlPipe Object](sqlpipe-object.md).</span></span>  
  
-   <span data-ttu-id="302a9-112">`SqlTriggerContext`：`SqlTriggerContext` 对象只能从 CLR 触发器内部检索。</span><span class="sxs-lookup"><span data-stu-id="302a9-112">`SqlTriggerContext`: The `SqlTriggerContext` object can only be retrieved from within a CLR trigger.</span></span> <span data-ttu-id="302a9-113">它提供有关导致触发器被激发的操作的信息，以及所更新的列的映射。</span><span class="sxs-lookup"><span data-stu-id="302a9-113">It provides information about the operation that caused the trigger to fire and a map of the columns that were updated.</span></span> <span data-ttu-id="302a9-114">有关对象的详细信息 `SqlTriggerContext` ，请参阅[SqlTriggerContext 对象](sqltriggercontext-object.md)。</span><span class="sxs-lookup"><span data-stu-id="302a9-114">For more information about the `SqlTriggerContext` object, see [SqlTriggerContext Object](sqltriggercontext-object.md).</span></span>  
  
-   <span data-ttu-id="302a9-115">`IsAvailable`：`IsAvailable` 属性用于确定上下文的可用性。</span><span class="sxs-lookup"><span data-stu-id="302a9-115">`IsAvailable`: The `IsAvailable` property is used to determine context availability.</span></span>  
  
-   <span data-ttu-id="302a9-116">`WindowsIdentity`：`WindowsIdentity` 属性用于检索调用方的 Windows 标识。</span><span class="sxs-lookup"><span data-stu-id="302a9-116">`WindowsIdentity`: The `WindowsIdentity` property is used to retrieve the Windows identity of the caller.</span></span>  
  
## <a name="determining-context-availability"></a><span data-ttu-id="302a9-117">确定上下文可用性</span><span class="sxs-lookup"><span data-stu-id="302a9-117">Determining Context Availability</span></span>  
 <span data-ttu-id="302a9-118">查询 `SqlContext` 类可查看当前执行的代码是否在进程中运行。</span><span class="sxs-lookup"><span data-stu-id="302a9-118">Query the `SqlContext` class to see if the currently executing code is running in-process.</span></span> <span data-ttu-id="302a9-119">若要执行此项检查，请查看 `IsAvailable` 对象的 `SqlContext` 属性。</span><span class="sxs-lookup"><span data-stu-id="302a9-119">To do this, check the `IsAvailable` property of the `SqlContext` object.</span></span> <span data-ttu-id="302a9-120">`IsAvailable` 属性是只读的，如果调用代码正在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内运行，并且其他 `True` 成员可访问，该属性将返回 `SqlContext`。</span><span class="sxs-lookup"><span data-stu-id="302a9-120">The `IsAvailable` property is read-only, and returns `True` if the calling code is running inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and if other `SqlContext` members can be accessed.</span></span> <span data-ttu-id="302a9-121">如果 `IsAvailable` 属性返回 `False`，所有其他 `SqlContext` 成员都将在使用时引发 `InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="302a9-121">If the `IsAvailable` property returns `False`, all the other `SqlContext` members throw an `InvalidOperationException`, if used.</span></span> <span data-ttu-id="302a9-122">如果 `IsAvailable` 返回 `False`，打开连接字符串中具有“context connection=true”的连接对象的任何尝试都会失败。</span><span class="sxs-lookup"><span data-stu-id="302a9-122">If `IsAvailable` returns `False`, any attempt to open a connection object that has "context connection=true" in the connection string fails.</span></span>  
  
## <a name="retrieving-windows-identity"></a><span data-ttu-id="302a9-123">检索 Windows 标识</span><span class="sxs-lookup"><span data-stu-id="302a9-123">Retrieving Windows Identity</span></span>  
 <span data-ttu-id="302a9-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内执行的 CLR 代码始终在进程帐户的上下文中调用。</span><span class="sxs-lookup"><span data-stu-id="302a9-124">CLR code executing inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is always invoked in the context of the process account.</span></span> <span data-ttu-id="302a9-125">如果代码应使用执行调用的用户的标识而不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程标识来执行某些操作，则应通过 `WindowsIdentity` 对象的 `SqlContext` 属性获取模拟标记。</span><span class="sxs-lookup"><span data-stu-id="302a9-125">If the code should perform certain actions using the identity of the calling user, instead of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process identity, then an impersonation token should be obtained through the `WindowsIdentity` property of the `SqlContext` object.</span></span> <span data-ttu-id="302a9-126">`WindowsIdentity` 属性返回表示调用方的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 标识的 `WindowsIdentity` 实例；如果客户端是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行身份验证的，则返回 Null。</span><span class="sxs-lookup"><span data-stu-id="302a9-126">The `WindowsIdentity` property returns a `WindowsIdentity` instance representing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows identity of the caller, or null if the client was authenticated using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="302a9-127">只有用 `EXTERNAL_ACCESS` 或 `UNSAFE` 权限标记的程序集才能访问此属性。</span><span class="sxs-lookup"><span data-stu-id="302a9-127">Only assemblies marked with `EXTERNAL_ACCESS` or `UNSAFE` permissions can access this property.</span></span>  
  
 <span data-ttu-id="302a9-128">获取 `WindowsIdentity` 对象之后，调用方可以模拟客户端帐户并代表调用方执行操作。</span><span class="sxs-lookup"><span data-stu-id="302a9-128">After obtaining the `WindowsIdentity` object, callers can impersonate the client account and perform actions on their behalf.</span></span>  
  
 <span data-ttu-id="302a9-129">如果启动存储过程或函数执行的客户端是使用 Windows 身份验证连接到服务器的，则调用方的标识只能通过 `SqlContext.WindowsIdentity` 使用。</span><span class="sxs-lookup"><span data-stu-id="302a9-129">The identity of the caller is only available through `SqlContext.WindowsIdentity` if the client that initiated execution of the stored-procedure or function connected to the server using Windows Authentication.</span></span> <span data-ttu-id="302a9-130">如果使用的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则该属性将为 Null，并且该代码无法模拟调用方。</span><span class="sxs-lookup"><span data-stu-id="302a9-130">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication was used instead, this property is null and the code is unable to impersonate the caller.</span></span>  
  
### <a name="example"></a><span data-ttu-id="302a9-131">示例</span><span class="sxs-lookup"><span data-stu-id="302a9-131">Example</span></span>  
 <span data-ttu-id="302a9-132">下面的示例说明如何获取调用客户端的 Windows 标识并模拟该客户端。</span><span class="sxs-lookup"><span data-stu-id="302a9-132">The following example shows how to get the Windows identity of the calling client and impersonate the client.</span></span>  
  
 <span data-ttu-id="302a9-133">C#</span><span class="sxs-lookup"><span data-stu-id="302a9-133">C#</span></span>  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 <span data-ttu-id="302a9-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="302a9-134">Visual Basic</span></span>  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="302a9-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="302a9-135">See Also</span></span>  
 <span data-ttu-id="302a9-136">[SqlPipe 对象](sqlpipe-object.md) </span><span class="sxs-lookup"><span data-stu-id="302a9-136">[SqlPipe Object](sqlpipe-object.md) </span></span>  
 <span data-ttu-id="302a9-137">[SqlTriggerContext 对象](sqltriggercontext-object.md) </span><span class="sxs-lookup"><span data-stu-id="302a9-137">[SqlTriggerContext Object](sqltriggercontext-object.md) </span></span>  
 <span data-ttu-id="302a9-138">[CLR 触发器](../../database-engine/dev-guide/clr-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="302a9-138">[CLR Triggers](../../database-engine/dev-guide/clr-triggers.md) </span></span>  
 [<span data-ttu-id="302a9-139">SQL Server 进程内专用的 ADO.NET 扩展</span><span class="sxs-lookup"><span data-stu-id="302a9-139">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
