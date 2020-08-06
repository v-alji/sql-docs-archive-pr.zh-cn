---
title: 实现合并项目的业务逻辑处理程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2996a8ca8471ef59d4781e21239a72262daa759
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578079"
---
# <a name="implement-a-business-logic-handler-for-a-merge-article"></a><span data-ttu-id="67d47-102">实现合并项目的业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="67d47-102">Implement a Business Logic Handler for a Merge Article</span></span>
  <span data-ttu-id="67d47-103">本主题说明如何使用复制编程方式或复制管理对象 (RMO) 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中实现合并项目的业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-103">This topic describes how to implement a business logic handler for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using replication programming or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="67d47-104"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 命名空间实现了一个可编写复杂业务逻辑以处理合并复制同步期间发生的事件的接口。</span><span class="sxs-lookup"><span data-stu-id="67d47-104">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="67d47-105">复制进程可以针对同步期间复制的每个已更改行调用业务逻辑处理程序中的方法。</span><span class="sxs-lookup"><span data-stu-id="67d47-105">Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization.</span></span>  
  
 <span data-ttu-id="67d47-106">实现业务逻辑处理程序的一般过程是：</span><span class="sxs-lookup"><span data-stu-id="67d47-106">The general process for implementing a business logic handler is:</span></span>  
  
1.  <span data-ttu-id="67d47-107">创建业务逻辑处理程序程序集。</span><span class="sxs-lookup"><span data-stu-id="67d47-107">Create the business logic hander assembly.</span></span>  
  
2.  <span data-ttu-id="67d47-108">在分发服务器上注册程序集。</span><span class="sxs-lookup"><span data-stu-id="67d47-108">Register the assembly at the Distributor.</span></span>  
  
3.  <span data-ttu-id="67d47-109">在运行合并代理的服务器上部署程序集。</span><span class="sxs-lookup"><span data-stu-id="67d47-109">Deploy the assembly at the server on which the Merge Agent runs.</span></span> <span data-ttu-id="67d47-110">对于请求订阅，代理在订阅服务器上运行，而对于推送订阅，代理在分发服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="67d47-110">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="67d47-111">使用 Web 同步时，代理在 Web 服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="67d47-111">When you are using Web synchronization, the agent runs on the Web server.</span></span>  
  
4.  <span data-ttu-id="67d47-112">创建使用业务逻辑处理程序的项目，或修改现有项目以使用业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-112">Create an article that uses the business logic handler or modify an existing article to use the business logic handler.</span></span>  
  
 <span data-ttu-id="67d47-113">指定的业务逻辑处理程序是针对每个同步的行来执行的，</span><span class="sxs-lookup"><span data-stu-id="67d47-113">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="67d47-114">因此复杂的逻辑以及对其他应用程序或网络服务的调用都可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="67d47-114">Complex logic and calls to other applications or network services can impact performance.</span></span> <span data-ttu-id="67d47-115">有关业务逻辑处理程序的详细信息，请参阅[在合并同步期间执行业务逻辑](merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="67d47-115">For more information about business logic handlers, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="67d47-116">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="67d47-116">**In This Topic**</span></span>  
  
-   <span data-ttu-id="67d47-117">**实现合并项目的业务逻辑处理程序，使用：**</span><span class="sxs-lookup"><span data-stu-id="67d47-117">**To implement a business logic handler for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="67d47-118">复制编程</span><span class="sxs-lookup"><span data-stu-id="67d47-118">Replication Programming</span></span>](#ReplProg)  
  
     [<span data-ttu-id="67d47-119">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="67d47-119">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-replication-programming"></a><a name="ReplProg"></a> <span data-ttu-id="67d47-120">使用复制编程</span><span class="sxs-lookup"><span data-stu-id="67d47-120">Using Replication Programming</span></span>  
  
#### <a name="to-create-and-deploy-a-business-logic-handler"></a><span data-ttu-id="67d47-121">创建和部署业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="67d47-121">To create and deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="67d47-122">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 中，为包含可实现业务逻辑处理程序的代码的 .NET 程序集创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="67d47-122">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="67d47-123">将对以下列命名空间的引用添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="67d47-123">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="67d47-124">程序集引用</span><span class="sxs-lookup"><span data-stu-id="67d47-124">Assembly Reference</span></span>|<span data-ttu-id="67d47-125">位置</span><span class="sxs-lookup"><span data-stu-id="67d47-125">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="67d47-126">COM（默认安装）</span><span class="sxs-lookup"><span data-stu-id="67d47-126">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="67d47-127">GAC（.NET Framework 的组件）</span><span class="sxs-lookup"><span data-stu-id="67d47-127">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="67d47-128">GAC（.NET Framework 的组件）</span><span class="sxs-lookup"><span data-stu-id="67d47-128">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="67d47-129">添加用于覆盖 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 类的类。</span><span class="sxs-lookup"><span data-stu-id="67d47-129">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="67d47-130">实现 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> 属性以指示处理的更改类型。</span><span class="sxs-lookup"><span data-stu-id="67d47-130">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="67d47-131">覆盖 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 类的以下一个或多个方法：</span><span class="sxs-lookup"><span data-stu-id="67d47-131">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="67d47-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 在同步期间提交数据更改时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="67d47-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - 在上载或下载 DELETE 语句过程中出现错误时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked when an error occurs when a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - 在上载或下载 DELETE 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - 在上载或下载 INSERT 语句过程中出现错误时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked when an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - 在上载或下载 INSERT 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - 当发布服务器和订阅服务器上出现冲突的 UPDATE 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="67d47-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - 当发布服务器和订阅服务器上的 UPDATE 语句与 DELETE 语句冲突时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="67d47-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - 在上载或下载 UPDATE 语句过程中出现错误时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - 在上载或下载 UPDATE 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
6.  <span data-ttu-id="67d47-141">生成该项目以创建业务逻辑处理程序程序集。</span><span class="sxs-lookup"><span data-stu-id="67d47-141">Build the project to create the business logic handler assembly.</span></span>  
  
7.  <span data-ttu-id="67d47-142">在包含合并代理可执行文件 (replmerg.exe) 的目录中部署该程序集，对默认安装来说，该目录为 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM，或将该程序集安装在 .NET 全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="67d47-142">Deploy the assembly in the directory that contains the Merge Agent executable file (replmerg.exe), which for a default installation is [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, or install it in the .NET global assembly cache (GAC).</span></span> <span data-ttu-id="67d47-143">如果合并代理之外的应用程序需要访问该程序集，您只能将该程序集安装在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="67d47-143">You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly.</span></span> <span data-ttu-id="67d47-144">可以使用 .NET Framework SDK 中提供的全局程序集缓存工具 (**Gacutil.exe)** 将该程序集安装到 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="67d47-144">The assembly can be installed into the GAC using the Global Assembly Cache tool (**Gacutil.exe)** provided in the .NET Framework SDK.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d47-145">必须在每个运行合并代理的服务器上部署业务逻辑处理程序，包括使用 Web 同步时 replisapi.dll 所驻留的 IIS 服务器。</span><span class="sxs-lookup"><span data-stu-id="67d47-145">A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="67d47-146">注册业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="67d47-146">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="67d47-147">在发布服务器中，执行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) 以验证该程序集是否尚未注册为业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-147">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the assembly has not already been registered as a business logic handler.</span></span>  
  
2.  <span data-ttu-id="67d47-148">在分发服务器上，执行[sp_registercustomresolver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)，为指定业务逻辑处理程序的友好名称，将的值指定为，为指定 **@article_resolver** `true` **@is_dotnet_assembly** 程序集的名称， **@dotnet_assembly_name** 并为重写的类的完全限定名称 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** 。</span><span class="sxs-lookup"><span data-stu-id="67d47-148">At the Distributor, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), specifying a friendly name for the business logic handler for **@article_resolver**, a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d47-149">如果该程序集未部署在与合并代理可执行文件相同的目录中、与同步启动合并代理的应用程序相同的目录中，或在全局程序集缓存 (GAC) ，则需要指定包含程序集名称的完整路径 **@dotnet_assembly_name** 。</span><span class="sxs-lookup"><span data-stu-id="67d47-149">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span> <span data-ttu-id="67d47-150">使用 Web 同步时，必须指定程序集在 Web 服务器中的位置。</span><span class="sxs-lookup"><span data-stu-id="67d47-150">When using Web synchronization, you must specify the location of assembly at the Web server.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="67d47-151">将业务逻辑处理程序与新的表项目一起使用</span><span class="sxs-lookup"><span data-stu-id="67d47-151">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="67d47-152">执行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 来定义项目，为 **@article_resolver** 指定业务逻辑处理程序的友好名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-152">Execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying the friendly name of the business logic handler for **@article_resolver**.</span></span> <span data-ttu-id="67d47-153">有关详细信息，请参阅 [定义项目](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="67d47-153">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="67d47-154">将业务逻辑处理程序用于现有的表项目</span><span class="sxs-lookup"><span data-stu-id="67d47-154">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="67d47-155">执行[sp_changemergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)，指定 **@publication** ， **@article** ，将的值指定为**article_resolver** **@property** ，并为指定业务逻辑处理程序的友好名称 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="67d47-155">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the business logic handler for **@value**.</span></span>  
  
###  <a name="examples-replication-programming"></a><a name="TsqlExample"></a> <span data-ttu-id="67d47-156">示例（复制编程方式）</span><span class="sxs-lookup"><span data-stu-id="67d47-156">Examples (Replication Programming)</span></span>  
 <span data-ttu-id="67d47-157">该示例演示了可创建审核日志的业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-157">This example shows a business logic handler that creates an audit log.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="67d47-158">以下示例在分发服务器中注册了业务逻辑处理程序程序集，并更改了一个现有合并项目以使用此自定义业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="67d47-158">The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.</span></span>  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../snippets/tsql/SQL15/replication/howto/tsql/registerblh_10.sql#sp_registerblh_10)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="67d47-159">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="67d47-159">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-create-a-business-logic-handler"></a><span data-ttu-id="67d47-160">创建业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="67d47-160">To create a business logic handler</span></span>  
  
1.  <span data-ttu-id="67d47-161">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 中，为包含可实现业务逻辑处理程序的代码的 .NET 程序集创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="67d47-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="67d47-162">将对以下列命名空间的引用添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="67d47-162">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="67d47-163">程序集引用</span><span class="sxs-lookup"><span data-stu-id="67d47-163">Assembly Reference</span></span>|<span data-ttu-id="67d47-164">位置</span><span class="sxs-lookup"><span data-stu-id="67d47-164">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="67d47-165">COM（默认安装）</span><span class="sxs-lookup"><span data-stu-id="67d47-165">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="67d47-166">GAC（.NET Framework 的组件）</span><span class="sxs-lookup"><span data-stu-id="67d47-166">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="67d47-167">GAC（.NET Framework 的组件）</span><span class="sxs-lookup"><span data-stu-id="67d47-167">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="67d47-168">添加用于覆盖 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 类的类。</span><span class="sxs-lookup"><span data-stu-id="67d47-168">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="67d47-169">实现 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> 属性以指示处理的更改类型。</span><span class="sxs-lookup"><span data-stu-id="67d47-169">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="67d47-170">覆盖 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 类的以下一个或多个方法：</span><span class="sxs-lookup"><span data-stu-id="67d47-170">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="67d47-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 在同步期间提交数据更改时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="67d47-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - 在上载或下载 DELETE 语句出错时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked if an error occurs while a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - 在上载或下载 DELETE 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - 在上载或下载 INSERT 语句出错时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked if an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - 在上载或下载 INSERT 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - 当发布服务器和订阅服务器上出现冲突的 UPDATE 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="67d47-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - 当发布服务器和订阅服务器上的 UPDATE 语句与 DELETE 语句冲突时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="67d47-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - 在上载或下载 UPDATE 语句出错时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="67d47-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - 在上载或下载 UPDATE 语句时调用。</span><span class="sxs-lookup"><span data-stu-id="67d47-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d47-180">自定义业务逻辑未显式处理的任何项目冲突都由项目的默认冲突解决程序进行处理。</span><span class="sxs-lookup"><span data-stu-id="67d47-180">Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.</span></span>  
  
6.  <span data-ttu-id="67d47-181">生成该项目以创建业务逻辑处理程序程序集。</span><span class="sxs-lookup"><span data-stu-id="67d47-181">Build the project to create the business logic handler assembly.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="67d47-182">注册业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="67d47-182">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="67d47-183">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="67d47-183">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="67d47-184">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="67d47-184">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="67d47-185">传递步骤 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="67d47-185">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
3.  <span data-ttu-id="67d47-186">调用 <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> 并检查返回的 <xref:System.Collections.ArrayList> 对象，以确保还未将该程序集注册为业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-186">Call <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> and check the returned <xref:System.Collections.ArrayList> object to ensure that the assembly has not already been registered as a business logic handler.</span></span>  
  
4.  <span data-ttu-id="67d47-187">创建的 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="67d47-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> class.</span></span> <span data-ttu-id="67d47-188">指定以下属性：</span><span class="sxs-lookup"><span data-stu-id="67d47-188">Specify the following properties:</span></span>  
  
    -   <span data-ttu-id="67d47-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - .NET 程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - the name of the .NET assembly.</span></span> <span data-ttu-id="67d47-190">如果该程序集未部署到与合并代理可执行文件相同的目录中、与同步启动合并代理的应用程序相同的目录中或 GAC 中，则必须随程序集名称提供完整的路径。</span><span class="sxs-lookup"><span data-stu-id="67d47-190">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name.</span></span> <span data-ttu-id="67d47-191">将业务逻辑处理程序与 Web 同步一起使用时，必须随程序集名称提供完整的路径。</span><span class="sxs-lookup"><span data-stu-id="67d47-191">You must include the full path with the assembly name when using a business logic handler with Web synchronization.</span></span>  
  
    -   <span data-ttu-id="67d47-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - 用于覆盖 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 并实现业务逻辑处理程序的类的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> and implements the business logic handler.</span></span>  
  
    -   <span data-ttu-id="67d47-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - 访问业务逻辑处理程序时使用的友好名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - a friendly name you use when you access the business logic handler.</span></span>  
  
    -   <span data-ttu-id="67d47-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - 值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="67d47-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - a value of `true`.</span></span>  
  
#### <a name="to-deploy-a-business-logic-handler"></a><span data-ttu-id="67d47-195">部署业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="67d47-195">To deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="67d47-196">将程序集部署到运行合并代理的服务器上，具体部署位置为在分发服务器上注册业务逻辑处理程序时所指定的文件位置。</span><span class="sxs-lookup"><span data-stu-id="67d47-196">Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor.</span></span> <span data-ttu-id="67d47-197">对于请求订阅，代理在订阅服务器上运行，而对于推送订阅，代理在分发服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="67d47-197">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="67d47-198">使用 Web 同步时，代理在 Web 服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="67d47-198">When you are using Web synchronization, the agent runs on the Web server.</span></span> <span data-ttu-id="67d47-199">如果注册业务逻辑处理程序时未对程序集名称提供完整的路径，则将程序集部署到与合并代理可执行文件相同的目录中、与同步启动合并代理的应用程序相同的目录中。</span><span class="sxs-lookup"><span data-stu-id="67d47-199">If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent.</span></span> <span data-ttu-id="67d47-200">如果有多个应用程序使用相同的程序集，则可以将程序集安装在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="67d47-200">You may install the assembly in the GAC if there are multiple applications that use the same assembly.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="67d47-201">将业务逻辑处理程序与新的表项目一起使用</span><span class="sxs-lookup"><span data-stu-id="67d47-201">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="67d47-202">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="67d47-202">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="67d47-203">创建的 <xref:Microsoft.SqlServer.Replication.MergeArticle> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="67d47-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span> <span data-ttu-id="67d47-204">设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="67d47-204">Set the following properties:</span></span>  
  
    -   <span data-ttu-id="67d47-205">将 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>设置为项目的名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-205">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="67d47-206">将 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>设置为发布的名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-206">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="67d47-207">为 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>设置发布数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-207">The name of the publication database for <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="67d47-208">为<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>设置业务逻辑处理程序的友好名称 ( <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>)。</span><span class="sxs-lookup"><span data-stu-id="67d47-208">The friendly name of the business logic handler (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span>  
  
3.  <span data-ttu-id="67d47-209">调用 <xref:Microsoft.SqlServer.Replication.Article.Create%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="67d47-209">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span> <span data-ttu-id="67d47-210">有关详细信息，请参阅 [定义项目](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="67d47-210">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="67d47-211">将业务逻辑处理程序用于现有的表项目</span><span class="sxs-lookup"><span data-stu-id="67d47-211">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="67d47-212">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="67d47-212">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="67d47-213">创建的 <xref:Microsoft.SqlServer.Replication.MergeArticle> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="67d47-213">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="67d47-214">设置 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="67d47-214">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="67d47-215">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="67d47-215">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="67d47-216">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="67d47-216">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="67d47-217">如果此方法返回 `false`，则说明步骤 3 中的项目属性定义不正确或此项目不存在。</span><span class="sxs-lookup"><span data-stu-id="67d47-217">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span> <span data-ttu-id="67d47-218">有关详细信息，请参阅 [View and Modify Article Properties](publish/view-and-modify-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="67d47-218">For more information, see [View and Modify Article Properties](publish/view-and-modify-article-properties.md).</span></span>  
  
6.  <span data-ttu-id="67d47-219">为 <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>设置业务逻辑处理程序的友好名称。</span><span class="sxs-lookup"><span data-stu-id="67d47-219">Set the friendly name of the business logic handler for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span> <span data-ttu-id="67d47-220">这是注册业务逻辑处理程序时指定的 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="67d47-220">This is the value of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> property specified when registering the business logic handler.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="67d47-221">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="67d47-221">Examples (RMO)</span></span>  
 <span data-ttu-id="67d47-222">此示例是一个业务逻辑处理程序，它记录有关订阅服务器上的插入、更新和删除操作的信息。</span><span class="sxs-lookup"><span data-stu-id="67d47-222">This example is a business logic handler that logs information about inserts, updates, and deletes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="67d47-223">此示例在分发服务器上注册业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-223">This example registers a business logic handler at the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 <span data-ttu-id="67d47-224">此示例更改现有项目以使用业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="67d47-224">This example changes an existing article to use the business logic handler.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="67d47-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67d47-225">See Also</span></span>  
 <span data-ttu-id="67d47-226">[为合并项目实现自定义冲突解决程序](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="67d47-226">[Implement a Custom Conflict Resolver for a Merge Article](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="67d47-227">[调试业务逻辑处理程序 &#40;复制编程&#41;](debug-a-business-logic-handler-replication-programming.md) </span><span class="sxs-lookup"><span data-stu-id="67d47-227">[Debug a Business Logic Handler &#40;Replication Programming&#41;](debug-a-business-logic-handler-replication-programming.md) </span></span>  
 <span data-ttu-id="67d47-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="67d47-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="67d47-229">复制管理对象概念</span><span class="sxs-lookup"><span data-stu-id="67d47-229">Replication Management Objects Concepts</span></span>](concepts/replication-management-objects-concepts.md)  
  
  
