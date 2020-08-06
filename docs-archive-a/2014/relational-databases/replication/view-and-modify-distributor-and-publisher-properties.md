---
title: 查看和修改分发服务器和发布服务器属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 571f6f3a0d44f0fc87c67885249fca441776946d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580113"
---
# <a name="view-and-modify-distributor-and-publisher-properties"></a><span data-ttu-id="4358c-102">查看和修改分发服务器和发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="4358c-102">View and Modify Distributor and Publisher Properties</span></span>
  <span data-ttu-id="4358c-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看和修改分发服务器和发布服务器属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-103">This topic describes how to view and modify Distributor and Publisher properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="4358c-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4358c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4358c-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4358c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4358c-106">建议</span><span class="sxs-lookup"><span data-stu-id="4358c-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="4358c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="4358c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4358c-108">**查看和修改分发服务器和发布服务器属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="4358c-108">**To view and modify Distributor and Publisher properties, using:**</span></span>  
  
     [<span data-ttu-id="4358c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4358c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4358c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4358c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4358c-111">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4358c-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4358c-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="4358c-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4358c-113">建议</span><span class="sxs-lookup"><span data-stu-id="4358c-113">Recommendations</span></span>  
  
-   <span data-ttu-id="4358c-114">对于运行低于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本的发布服务器，sysadmin 固定服务器角色中的用户可以在“订阅服务器”页上注册订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4358c-114">For Publishers running versions prior to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user in the **sysadmin** fixed server role can register Subscribers on the **Subscribers** page.</span></span> <span data-ttu-id="4358c-115">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]开始，不再需要为复制显式注册订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4358c-115">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], it is no longer necessary to explicitly register Subscribers for replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4358c-116">Security</span><span class="sxs-lookup"><span data-stu-id="4358c-116">Security</span></span>  
 <span data-ttu-id="4358c-117">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="4358c-117">When possible, prompt users to enter security credentials at runtime.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4358c-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4358c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="4358c-119">查看和修改分发服务器属性</span><span class="sxs-lookup"><span data-stu-id="4358c-119">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="4358c-120">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="4358c-120">Connect to the Distributor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="4358c-121">右键单击 **“复制”** 文件夹，然后单击 **“分发服务器属性”** 。</span><span class="sxs-lookup"><span data-stu-id="4358c-121">Right-click the **Replication** folder, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="4358c-122">在“分发服务器属性 - \<Distributor>”对话框中查看和修改属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-122">View and modify properties in the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
    -   <span data-ttu-id="4358c-123">若要查看和修改分发数据库的属性，请在该对话框的“常规”页上单击该数据库的属性按钮 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="4358c-123">To view and modify properties for a distribution database, click the properties button (**...**) for the database on the **General** page of thedialog box.</span></span>  
  
    -   <span data-ttu-id="4358c-124">若要查看和修改与分发服务器关联的发布服务器属性，请在该对话框的 **“发布服务器”** 页面上单击发布服务器的属性按钮 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="4358c-124">To view and modify Publisher properties associated with the Distributor, click the properties button (**...**) for the Publisher on the **Publishers** page of the dialog box.</span></span>  
  
    -   <span data-ttu-id="4358c-125">若要访问复制代理的配置文件，请单击此对话框的 **“常规”** 页上的 **“默认配置文件”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4358c-125">To access profiles for replication agents, click the **Profile Defaults** button on the **General** page of the dialog box.</span></span> <span data-ttu-id="4358c-126">有关详细信息，请参阅 [Replication Agent Profiles](agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4358c-126">For more information, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  
  
    -   <span data-ttu-id="4358c-127">若要更改管理存储过程在发布服务器上执行以及在分发服务器上更新信息时所用帐户的密码，请在该对话框的 **“发布服务器”** 页面上的 **“密码”** 和 **“确认密码”** 框中输入新密码。</span><span class="sxs-lookup"><span data-stu-id="4358c-127">To change the password for the account used when administrative stored procedures execute at the Publisher and update information at the Distributor, enter a new password in the **Password** and **Confirm password** boxes on the **Publishers** page of the dialog box.</span></span> <span data-ttu-id="4358c-128">有关详细信息，请参阅[保护分发服务器的安全](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="4358c-128">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
4.  <span data-ttu-id="4358c-129">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4358c-129">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="4358c-130">查看和修改发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="4358c-130">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="4358c-131">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="4358c-131">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="4358c-132">右键单击 **“复制”** 文件夹，然后单击 **“发布服务器属性”** 。</span><span class="sxs-lookup"><span data-stu-id="4358c-132">Right-click the **Replication** folder, and then click **Publisher Properties**.</span></span>  
  
3.  <span data-ttu-id="4358c-133">查看和修改 "\*\*发布服务器属性- \< Publisher > \*\* " 对话框中的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-133">View and modify properties in the **Publisher Properties - \< Publisher >** dialog box.</span></span>  
  
    -   <span data-ttu-id="4358c-134">**sysadmin** 固定服务器角色中的用户可以在 **“发布数据库”** 页上为复制启用数据库。</span><span class="sxs-lookup"><span data-stu-id="4358c-134">A user in the **sysadmin** fixed server role can enable databases for replication on the **Publication Databases** page.</span></span> <span data-ttu-id="4358c-135">启用数据库并不会发布该数据库，而是允许该数据库的 **db_owner** 固定数据库角色中的任何用户在该数据库中创建一个或多个发布。</span><span class="sxs-lookup"><span data-stu-id="4358c-135">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications in the database.</span></span>  
  
4.  <span data-ttu-id="4358c-136">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4358c-136">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4358c-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4358c-137">Using Transact-SQL</span></span>  
 <span data-ttu-id="4358c-138">可以使用复制存储过程以编程方式查看发布服务器和分发服务器属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-138">Publisher and Distributor properties can be viewed programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a><span data-ttu-id="4358c-139">查看分发服务器和分发数据库属性</span><span class="sxs-lookup"><span data-stu-id="4358c-139">To view Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="4358c-140">执行 [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) 可返回有关分发服务器、分发数据库和工作目录的信息。</span><span class="sxs-lookup"><span data-stu-id="4358c-140">Execute [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) to return information about the Distributor, distribution database, and working directory.</span></span>  
  
2.  <span data-ttu-id="4358c-141">执行 [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) 可返回指定的分发数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-141">Execute [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) to return properties of a specified distribution database.</span></span>  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a><span data-ttu-id="4358c-142">更改分发服务器和分发数据库属性</span><span class="sxs-lookup"><span data-stu-id="4358c-142">To change Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="4358c-143">在分发服务器上，执行 [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) 可修改分发服务器属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-143">At the Distributor, execute [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) to modify Distributor properties.</span></span>  
  
2.  <span data-ttu-id="4358c-144">在分发服务器上，执行 [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) 可修改分发数据库属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-144">At the Distributor, execute [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) to modify distribution database properties.</span></span>  
  
3.  <span data-ttu-id="4358c-145">在分发服务器上，执行 [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) 可更改分发服务器密码。</span><span class="sxs-lookup"><span data-stu-id="4358c-145">At the Distributor, execute [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) to change the Distributor password.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4358c-146">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="4358c-146">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="4358c-147">如果必须将凭据存储在脚本文件中，请确保该文件的安全以防受到未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="4358c-147">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
4.  <span data-ttu-id="4358c-148">在分发服务器上，执行 [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) ，以便使用分发服务器更改发布服务器的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-148">At the Distributor, execute [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) to change the properties of a Publisher using the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4358c-149">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4358c-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="4358c-150">下面的示例 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本返回有关分发服务器和分发数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="4358c-150">The following example [!INCLUDE[tsql](../../includes/tsql-md.md)] script returns information about the Distributor and distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_helpdistributor](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributor)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributiondb)]  
  
 <span data-ttu-id="4358c-151">该示例更改分发服务器的保持期、连接到分发服务器时使用的密码以及分发服务器检查各种复制代理的状态时采用的时间间隔（也称为检测信号时间间隔）。</span><span class="sxs-lookup"><span data-stu-id="4358c-151">This example changes retention periods for the Distributor, the password used when connecting to the Distributor, and the interval at which the Distributor checks the status of various replication agents (also known as the heartbeat interval).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4358c-152">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="4358c-152">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="4358c-153">如果必须将凭据存储在脚本文件中，请确保该文件的安全以防受到未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="4358c-153">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_property)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributiondb)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_password)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4358c-154">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4358c-154">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="4358c-155">查看和修改分发服务器属性</span><span class="sxs-lookup"><span data-stu-id="4358c-155">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="4358c-156">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4358c-157">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4358c-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="4358c-158">传递步骤 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="4358c-158">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="4358c-159">（可选）检查 <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> 属性以验证当前连接到的服务器是否为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="4358c-159">(Optional) Check the <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> property to verify that the currently connected server is a Distributor.</span></span>  
  
4.  <span data-ttu-id="4358c-160">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 方法获取该服务器的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties from the server.</span></span>  
  
5.  <span data-ttu-id="4358c-161">（可选）若要更改属性，请为一个或多个可在 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 对象上设置的分发服务器属性设置新值。</span><span class="sxs-lookup"><span data-stu-id="4358c-161">(Optional) To change properties, set a new value for one or more of the Distributor properties that can be set on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object.</span></span>  
  
6.  <span data-ttu-id="4358c-162">（可选）如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 对象的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 属性设置为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法来提交对服务器的更改。</span><span class="sxs-lookup"><span data-stu-id="4358c-162">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a><span data-ttu-id="4358c-163">查看和修改分发数据库属性</span><span class="sxs-lookup"><span data-stu-id="4358c-163">To view and modify distribution database properties</span></span>  
  
1.  <span data-ttu-id="4358c-164">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-164">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4358c-165">创建的 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4358c-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> class.</span></span> <span data-ttu-id="4358c-166">指定名称属性并传递步骤 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="4358c-166">Specify the name property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="4358c-167">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该服务器的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-167">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties from the server.</span></span> <span data-ttu-id="4358c-168">如果此方法返回 `false`，则该服务器上不存在指定名称的数据库。</span><span class="sxs-lookup"><span data-stu-id="4358c-168">If this method returns `false`, the database with the specified name does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="4358c-169">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 属性中的一个设置新值。</span><span class="sxs-lookup"><span data-stu-id="4358c-169">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> properties that can be set.</span></span>  
  
5.  <span data-ttu-id="4358c-170">（可选）如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 对象的 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 属性设置为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法来提交对服务器的更改。</span><span class="sxs-lookup"><span data-stu-id="4358c-170">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="4358c-171">查看和修改发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="4358c-171">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="4358c-172">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-172">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4358c-173">创建的 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4358c-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="4358c-174">指定 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> 属性并传递步骤 1 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="4358c-174">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="4358c-175">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 属性中的一个设置新值。</span><span class="sxs-lookup"><span data-stu-id="4358c-175">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> properties that can be set.</span></span>  
  
4.  <span data-ttu-id="4358c-176">（可选）如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 对象的 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 属性设置为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法来提交对服务器的更改。</span><span class="sxs-lookup"><span data-stu-id="4358c-176">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="4358c-177">更改从发布服务器到分发服务器的管理连接的密码</span><span class="sxs-lookup"><span data-stu-id="4358c-177">To change the password for the administrative connection from the Publisher to the Distributor</span></span>  
  
1.  <span data-ttu-id="4358c-178">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-178">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4358c-179">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4358c-179">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
3.  <span data-ttu-id="4358c-180">将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-180">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="4358c-181">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-181">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
5.  <span data-ttu-id="4358c-182">调用 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4358c-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="4358c-183">为 *password* 参数传递新的密码值。</span><span class="sxs-lookup"><span data-stu-id="4358c-183">Pass the new password value for the *password* parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4358c-184">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="4358c-184">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="4358c-185">如果必须存储凭据，请使用 [Windows .NET Framework 提供的](https://go.microsoft.com/fwlink/?LinkId=34733) Cryptographic Services [!INCLUDE[msCoName](../../includes/msconame-md.md)] （加密服务）。</span><span class="sxs-lookup"><span data-stu-id="4358c-185">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
6.  <span data-ttu-id="4358c-186">（可选）执行下列步骤以更改每个使用该分发服务器的远程发布服务器上的密码：</span><span class="sxs-lookup"><span data-stu-id="4358c-186">(Optional) Perform the following steps to change the password at each remote Publisher that uses this Distributor:</span></span>  
  
    1.  <span data-ttu-id="4358c-187">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
    2.  <span data-ttu-id="4358c-188">创建的 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4358c-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
    3.  <span data-ttu-id="4358c-189">将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 6a 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="4358c-189">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 6a.</span></span>  
  
    4.  <span data-ttu-id="4358c-190">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
    5.  <span data-ttu-id="4358c-191">调用 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4358c-191">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="4358c-192">为 *password* 参数传递步骤 5 中的新密码值。</span><span class="sxs-lookup"><span data-stu-id="4358c-192">Pass the new password value from Step 5 for the *password* parameter.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="4358c-193">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4358c-193">Example (RMO)</span></span>  
 <span data-ttu-id="4358c-194">此示例显示如何更改分发和分发数据库属性。</span><span class="sxs-lookup"><span data-stu-id="4358c-194">This example shows how to change Distribution and distribution database properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4358c-195">若要避免将凭据存储在代码中，应当在运行时提供新分发服务器密码。</span><span class="sxs-lookup"><span data-stu-id="4358c-195">To avoid storing credentials in the code, the new Distributor password is supplied at runtime.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a><span data-ttu-id="4358c-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4358c-196">See Also</span></span>  
 <span data-ttu-id="4358c-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4358c-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="4358c-198">[禁用发布和分发](disable-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="4358c-198">[Disable Publishing and Distribution](disable-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="4358c-199">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="4358c-199">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="4358c-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4358c-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="4358c-201">[分发服务器和发布服务器信息脚本](administration/distributor-and-publisher-information-script.md) </span><span class="sxs-lookup"><span data-stu-id="4358c-201">[Distributor and Publisher Information Script](administration/distributor-and-publisher-information-script.md) </span></span>  
 <span data-ttu-id="4358c-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4358c-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="4358c-203">使用复制监视器查看信息和执行任务</span><span class="sxs-lookup"><span data-stu-id="4358c-203">View Information and Perform Tasks using Replication Monitor</span></span>](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
  
