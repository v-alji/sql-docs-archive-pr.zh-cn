---
title: 为合并项目实现自定义冲突解决程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e684213114f3c9bb2f1ad56de06fcfc89b819a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578077"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a><span data-ttu-id="12558-102">为合并项目实现自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="12558-102">Implement a Custom Conflict Resolver for a Merge Article</span></span>
  <span data-ttu-id="12558-103">本主题说明如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或[基于 COM 的自定义解决程序](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中为合并项目实现自定义冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="12558-103">This topic describes how to implement custom conflict resolver for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or a [COM-based custom resolver](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
 <span data-ttu-id="12558-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="12558-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="12558-105">**为合并项目实现自定义冲突解决程序，使用：**</span><span class="sxs-lookup"><span data-stu-id="12558-105">**To implement custom conflict resolver for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="12558-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12558-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="12558-107">基于 COM 的冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="12558-107">COM-based Resolver</span></span>](#COM)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="12558-108">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12558-108">Using Transact-SQL</span></span>  
 <span data-ttu-id="12558-109">您可以编写自己的自定义冲突解决程序以作为每个发布服务器上的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程。</span><span class="sxs-lookup"><span data-stu-id="12558-109">You can write your own custom conflict resolver as a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure at each Publisher.</span></span> <span data-ttu-id="12558-110">在同步过程中，如果在注册了冲突解决程序的项目中遇到冲突，则将调用此存储过程，并且合并代理会将有关冲突行的信息传递到该存储过程的所需参数中。</span><span class="sxs-lookup"><span data-stu-id="12558-110">During synchronization, this stored procedure is invoked when conflicts are encountered in an article to which the resolver was registered, and information on the conflict row is passed by the Merge Agent to the required parameters of the procedure.</span></span> <span data-ttu-id="12558-111">基于存储过程的自定义冲突解决程序将始终在发布服务器上创建。</span><span class="sxs-lookup"><span data-stu-id="12558-111">Stored procedure-based custom conflict resolvers are always created at the Publisher.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="12558-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]只调用存储过程冲突解决程序来处理基于行更改的冲突。</span><span class="sxs-lookup"><span data-stu-id="12558-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure resolvers are only invoked to handle row change-based conflicts.</span></span> <span data-ttu-id="12558-113">它们不能用于处理其他类型的冲突，例如由于 PRIMARY KEY 冲突或唯一索引约束冲突而造成的插入失败。</span><span class="sxs-lookup"><span data-stu-id="12558-113">They cannot be used to handle other types of conflicts such as insert failures due to PRIMARY KEY violations or unique index constraint violations.</span></span>  
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a><span data-ttu-id="12558-114">创建基于存储过程的自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="12558-114">To create a stored procedure-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="12558-115">在发布服务器的发布数据库或 **msdb** 数据库中，创建用于实现以下所需参数的新系统存储过程：</span><span class="sxs-lookup"><span data-stu-id="12558-115">At the Publisher in either the publication or **msdb** database, create a new system stored procedure that implements the following required parameters:</span></span>  
  
    |<span data-ttu-id="12558-116">参数</span><span class="sxs-lookup"><span data-stu-id="12558-116">Parameter</span></span>|<span data-ttu-id="12558-117">数据类型</span><span class="sxs-lookup"><span data-stu-id="12558-117">Data type</span></span>|<span data-ttu-id="12558-118">说明</span><span class="sxs-lookup"><span data-stu-id="12558-118">Description</span></span>|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|`sysname`|<span data-ttu-id="12558-119">冲突被解决的表的所有者名称。</span><span class="sxs-lookup"><span data-stu-id="12558-119">Name of the owner of the table for which a conflict is being resolved.</span></span> <span data-ttu-id="12558-120">这是发布数据库中的表的所有者。</span><span class="sxs-lookup"><span data-stu-id="12558-120">This is the owner for the table in the publication database.</span></span>|  
    |**@tablename**|`sysname`|<span data-ttu-id="12558-121">冲突被解决的表的名称。</span><span class="sxs-lookup"><span data-stu-id="12558-121">Name of the table for which a conflict is being resolved.</span></span>|  
    |**@rowguid**|`uniqueidentifier`|<span data-ttu-id="12558-122">具有冲突的行的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="12558-122">Unique identifier for the row having the conflict.</span></span>|  
    |**@subscriber**|`sysname`|<span data-ttu-id="12558-123">传播冲突更改的源服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="12558-123">Name of the server from where a conflicting change is being propagated.</span></span>|  
    |**@subscriber_db**|`sysname`|<span data-ttu-id="12558-124">传播冲突更改的源数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="12558-124">Name of the database from where conflicting change is being propagated.</span></span>|  
    |<span data-ttu-id="12558-125">**@log_conflict输出**</span><span class="sxs-lookup"><span data-stu-id="12558-125">**@log_conflict OUTPUT**</span></span>|`int`|<span data-ttu-id="12558-126">合并进程是否应记录冲突以便以后进行解决：</span><span class="sxs-lookup"><span data-stu-id="12558-126">Whether the merge process should log a conflict for later resolution:</span></span><br /><br /> <span data-ttu-id="12558-127">**0** = 不记录冲突。</span><span class="sxs-lookup"><span data-stu-id="12558-127">**0** = Do not log the conflict.</span></span><br /><br /> <span data-ttu-id="12558-128">**1** = 订阅服务器是冲突解决落选方。</span><span class="sxs-lookup"><span data-stu-id="12558-128">**1** = Subscriber is the conflict loser.</span></span><br /><br /> <span data-ttu-id="12558-129">**2** = 发布服务器是冲突解决落选方。</span><span class="sxs-lookup"><span data-stu-id="12558-129">**2** = Publisher is the conflict loser.</span></span>|  
    |<span data-ttu-id="12558-130">**@conflict_message输出**</span><span class="sxs-lookup"><span data-stu-id="12558-130">**@conflict_message OUTPUT**</span></span>|`nvarchar(512)`|<span data-ttu-id="12558-131">记录冲突时要提供的有关解决方法的消息。</span><span class="sxs-lookup"><span data-stu-id="12558-131">Message to be given about the resolution if the conflict is logged.</span></span>|  
    |**@destowner**|`sysname`|<span data-ttu-id="12558-132">订阅服务器上的已发布表的所有者。</span><span class="sxs-lookup"><span data-stu-id="12558-132">The owner of the published table at the Subscriber.</span></span>|  
  
     <span data-ttu-id="12558-133">此存储过程使用合并代理传递给这些参数的值来实现自定义冲突解决逻辑；它必须返回结构与基表结构相同的单行结果集，并且包含该行的入选版本的数据值。</span><span class="sxs-lookup"><span data-stu-id="12558-133">This stored procedure uses the values passed by the Merge Agent to these parameters to implement your custom conflict resolution logic; it must return a single row result set that is identical in structure to the base table and contains the data values for the winning version of the row.</span></span>  
  
2.  <span data-ttu-id="12558-134">向订阅服务器用来连接到发布服务器的任何登录名授予对存储过程的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="12558-134">Grant EXECUTE permissions on the stored procedure to any logins used by Subscribers to connect to the Publisher.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="12558-135">将自定义冲突解决程序用于新的表项目</span><span class="sxs-lookup"><span data-stu-id="12558-135">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="12558-136">执行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 以定义一个项目，为 **@article_resolver** **参数指定值** MicrosoftSQL **@article_resolver** ，并为 **@resolver_info** 参数指定用于实现冲突解决程序逻辑的存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="12558-136">Execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying a value of **MicrosoftSQL** **Server Stored Procedure Resolver** for the **@article_resolver** parameter and the name of the stored procedure that implements the conflict resolver logic for the **@resolver_info** parameter.</span></span> <span data-ttu-id="12558-137">有关详细信息，请参阅 [定义项目](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="12558-137">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="12558-138">将自定义冲突解决程序用于现有表项目</span><span class="sxs-lookup"><span data-stu-id="12558-138">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="12558-139">执行[sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)，指定 **@publication** ， **@article** ，将的**article_resolver**值指定为，并将 ProcedureResolver 的值指定为 **@property** **MicrosoftSQL** **Server** **@value** 。</span><span class="sxs-lookup"><span data-stu-id="12558-139">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and a value of **MicrosoftSQL** **Server Stored ProcedureResolver** for **@value**.</span></span>  
  
2.  <span data-ttu-id="12558-140">执行[sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)， **@publication** 同时指定、 **@article** 、的**resolver_info**值为 **@property** ，并为实现冲突解决程序逻辑的存储过程的名称 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="12558-140">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **resolver_info** for **@property**, and the name of the stored procedure that implements the conflict resolver logic for **@value**.</span></span>  
  
##  <a name="using-a-com-based-custom-resolver"></a><a name="COM"></a><span data-ttu-id="12558-141">使用基于 COM 的自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="12558-141">Using a COM-based Custom Resolver</span></span>  
 <span data-ttu-id="12558-142"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 命名空间实现了一个接口，可以利用该接口编写复杂的业务逻辑以处理事件并解决在合并复制同步过程中发生的冲突。</span><span class="sxs-lookup"><span data-stu-id="12558-142">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events and resolve conflicts that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="12558-143">有关详细信息，请参阅 [为合并项目实现业务逻辑处理程序](implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="12558-143">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span> <span data-ttu-id="12558-144">您也可以编写自己的基于本机代码的自定义业务逻辑以解决冲突。</span><span class="sxs-lookup"><span data-stu-id="12558-144">You can also write your own native code-based custom business logic to resolve conflicts.</span></span> <span data-ttu-id="12558-145">使用诸如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++ 之类的产品，此逻辑可作为 COM 组件生成并编译到动态链接库 (DLL) 中。</span><span class="sxs-lookup"><span data-stu-id="12558-145">This logic is built as a COM component and compiled into dynamic-link libraries (DLL), using products such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++.</span></span> <span data-ttu-id="12558-146">这类基于 COM 的自定义冲突解决程序必须实现 ICustomResolver 接口，该接口是专为解决冲突而设计的\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="12558-146">Such a COM-based custom conflict resolver must implement the **ICustomResolver** interface, which is designed specifically for conflict resolution.</span></span>  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a><span data-ttu-id="12558-147">创建和注册基于 COM 的自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="12558-147">To create and register a COM-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="12558-148">在与 COM 兼容的创作环境中，添加对自定义冲突解决程序库的引用。</span><span class="sxs-lookup"><span data-stu-id="12558-148">In a COM-compatible authoring environment, add references to the Custom Conflict Resolver library.</span></span>  
  
2.  <span data-ttu-id="12558-149">对于 Visual C++ 项目，请使用 #import 命令将该库导入项目中。</span><span class="sxs-lookup"><span data-stu-id="12558-149">For a Visual C++ project, use the #import directive to import this library into your project.</span></span>  
  
3.  <span data-ttu-id="12558-150">创建一个用于实现 **ICustomResolver** 接口的类。</span><span class="sxs-lookup"><span data-stu-id="12558-150">Create a class that implements the **ICustomResolver** interface.</span></span>  
  
4.  <span data-ttu-id="12558-151">实现某些特定的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="12558-151">Implement certain methods and properties.</span></span>  
  
5.  <span data-ttu-id="12558-152">生成项目以创建自定义冲突解决程序库文件。</span><span class="sxs-lookup"><span data-stu-id="12558-152">Build the project to create the custom conflict resolver library file.</span></span>  
  
6.  <span data-ttu-id="12558-153">将该库部署在包含合并代理可执行文件的目录（通常为 \Microsoft SQL Server\100\COM）中。</span><span class="sxs-lookup"><span data-stu-id="12558-153">Deploy the library in the directory containing the merge agent executable (usually \Microsoft SQL Server\100\COM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12558-154">对于请求订阅，必须在订阅服务器上部署自定义冲突解决程序；对于推送订阅，必须在分发服务器上部署；或者部署在使用 Web 同步的 Web 服务器上。</span><span class="sxs-lookup"><span data-stu-id="12558-154">A custom conflict resolver must be deployed at the Subscriber for a pull subscription, at the Distributor for a push subscription, or at the Web server used with Web synchronization.</span></span>  
  
7.  <span data-ttu-id="12558-155">使用 regsvr32.exe 注册部署目录中的自定义冲突解决程序库，如下所示：</span><span class="sxs-lookup"><span data-stu-id="12558-155">Register the custom conflict resolver library using regsvr32.exe from the deployment directory as follows:</span></span>  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  <span data-ttu-id="12558-156">在发布服务器上，执行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) 以验证该库尚未注册为自定义冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="12558-156">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the library is not already registered as a custom conflict resolver.</span></span>  
  
9. <span data-ttu-id="12558-157">若要将该库注册为自定义冲突解决程序，请在分发服务器上执行[&#40;transact-sql&#41;sp_registercustomresolver ](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="12558-157">To register the library as a custom conflict resolver, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), at the Distributor.</span></span> <span data-ttu-id="12558-158">为指定 COM 对象的友好名称，为指定 **@article_resolver** 库 ID (CLSID) **@resolver_clsid** ，并将值指定 `false` 为 **@is_dotnet_assembly** 。</span><span class="sxs-lookup"><span data-stu-id="12558-158">Specify the friendly name of the COM object for **@article_resolver**, the library's ID (CLSID) for **@resolver_clsid**, and a value of `false` for **@is_dotnet_assembly**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12558-159">当不再需要某个自定义冲突解决程序时，可使用 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) 将其取消注册。</span><span class="sxs-lookup"><span data-stu-id="12558-159">When no longer needed, a custom conflict resolver can be unregistered using [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql).</span></span>  
  
10. <span data-ttu-id="12558-160">（可选）在集群上，对集群的所有节点重复步骤 5-8 来注册自定义冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="12558-160">(Optional) On a cluster, repeat steps 5-8 to register the custom resolver on all nodes of the cluster.</span></span> <span data-ttu-id="12558-161">为了确保在故障转移之后自定义冲突解决程序能够正确载入协调器，此操作是必需的。</span><span class="sxs-lookup"><span data-stu-id="12558-161">This is required to ensure that the custom resolver will be able to properly load the reconciler following a failover.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="12558-162">将自定义冲突解决程序用于新的表项目</span><span class="sxs-lookup"><span data-stu-id="12558-162">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="12558-163">在发布服务器上，执行[sp_enumcustomresolvers &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) ，并记下所需冲突解决程序的友好名称。</span><span class="sxs-lookup"><span data-stu-id="12558-163">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="12558-164">在发布服务器上，对发布数据库执行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 来定义项目。</span><span class="sxs-lookup"><span data-stu-id="12558-164">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article.</span></span> <span data-ttu-id="12558-165">为指定步骤1中项目冲突解决程序的友好名称 **@article_resolver** 。</span><span class="sxs-lookup"><span data-stu-id="12558-165">Specify the friendly name of the article resolver from step 1 for **@article_resolver**.</span></span> <span data-ttu-id="12558-166">有关详细信息，请参阅 [定义项目](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="12558-166">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="12558-167">将自定义冲突解决程序用于现有表项目</span><span class="sxs-lookup"><span data-stu-id="12558-167">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="12558-168">在发布服务器上，执行[sp_enumcustomresolvers &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) ，并记下所需冲突解决程序的友好名称。</span><span class="sxs-lookup"><span data-stu-id="12558-168">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="12558-169">执行[sp_changemergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)，指定 **@publication** ， **@article** ，将的值指定为**article_resolver** **@property** ，并为提供步骤1中项目冲突解决程序的友好名称 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="12558-169">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the article resolver from step 1 for **@value**.</span></span>  
  
#### <a name="viewing-a-sample-custom-resolver"></a><span data-ttu-id="12558-170">查看示例自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="12558-170">Viewing a Sample Custom Resolver</span></span>  
  
1.  <span data-ttu-id="12558-171">SQL Server 2000 示例文件中提供了示例。</span><span class="sxs-lookup"><span data-stu-id="12558-171">A sample is available in the SQL Server 2000 sample files.</span></span> <span data-ttu-id="12558-172">下载[**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip)。</span><span class="sxs-lookup"><span data-stu-id="12558-172">Download the [**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip).</span></span> <span data-ttu-id="12558-173">这会下载3个文件，共6.9 至 6.9 MB。</span><span class="sxs-lookup"><span data-stu-id="12558-173">This downloads 3 files amounting to 6.9 MB.</span></span>  
  
2.  <span data-ttu-id="12558-174">从下载的压缩 .cab 文件中提取文件。</span><span class="sxs-lookup"><span data-stu-id="12558-174">Extract the files from downloaded compressed .cab file.</span></span>  
  
3.  <span data-ttu-id="12558-175">运行**setup.exe**</span><span class="sxs-lookup"><span data-stu-id="12558-175">Run **setup.exe**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12558-176">选择安装选项时，仅需安装 **复制** 示例。</span><span class="sxs-lookup"><span data-stu-id="12558-176">When choosing the installation options, it is only necessary to install the **Replication** samples.</span></span> <span data-ttu-id="12558-177"> (默认的安装路径\是\** (x86) \microsoft SQL Server 2000 \\ Samples\1033 的 C:\Program 文\件\**) </span><span class="sxs-lookup"><span data-stu-id="12558-177">(The default installation path is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\\**)</span></span>  
  
4.  <span data-ttu-id="12558-178">转至安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="12558-178">Go to installation folder.</span></span> <span data-ttu-id="12558-179">（默认文件夹为 **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**）</span><span class="sxs-lookup"><span data-stu-id="12558-179">(The default folder is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)</span></span>  
  
5.  <span data-ttu-id="12558-180">运行 **unzip_sqlreplSP3.exe** 程序。</span><span class="sxs-lookup"><span data-stu-id="12558-180">Run the **unzip_sqlreplSP3.exe** program.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12558-181">默认情况下，com 冲突解决程序示例将安装到 **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="12558-181">The sample com resolver will install (by default) to the **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** folder.</span></span>  
  
6.  <span data-ttu-id="12558-182">在 **subspres** 文件夹中，在所有源文件中查找所有出现的 **#include sqlres.h** ，将其替换为 **#import "replrec.dll" no_namespace, raw_interfaces_only**</span><span class="sxs-lookup"><span data-stu-id="12558-182">In the **subspres** folder, find all occurrences of **#include sqlres.h** in all of the source files and replace them with **#import "replrec.dll" no_namespace, raw_interfaces_only**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12558-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12558-183">See Also</span></span>  
 <span data-ttu-id="12558-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="12558-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 <span data-ttu-id="12558-185">[基于 COM 的自定义冲突解决程序](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span><span class="sxs-lookup"><span data-stu-id="12558-185">[COM-Based Custom Resolvers](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span></span>  
 [<span data-ttu-id="12558-186">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="12558-186">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
