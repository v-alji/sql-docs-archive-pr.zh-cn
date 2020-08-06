---
title: 为 AlwaysOn 可用性组配置复制 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 916458d2d6b8fbba81940257ee85ffe014d1f12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688232"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="4ba3e-102">为 AlwaysOn 可用性组配置复制 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-102">Configure Replication for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="4ba3e-103">配置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制和 AlwaysOn 可用性组涉及七个步骤。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-103">Configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication and AlwaysOn availability groups involves seven steps.</span></span> <span data-ttu-id="4ba3e-104">在下面的各节中将详细说明每个步骤。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-104">Each step is described in more detail in the following sections.</span></span>  

##  <a name="1-configure-the-database-publications-and-subscriptions"></a><a name="step1"></a> <span data-ttu-id="4ba3e-105">1.配置数据库发布和订阅</span><span class="sxs-lookup"><span data-stu-id="4ba3e-105">1. Configure the Database Publications and Subscriptions</span></span>  

### <a name="configure-the-distributor"></a><span data-ttu-id="4ba3e-106">配置分发服务器</span><span class="sxs-lookup"><span data-stu-id="4ba3e-106">Configure the distributor</span></span>
  
 <span data-ttu-id="4ba3e-107">分发服务器不应是发布数据库当前（或将来）所在的可用性组的任何当前（或目标）副本的主机。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-107">The distributor should not be a host for any of the current (or intended) replicas of the availability group that the publishing database is (or will become) a member of.</span></span>  
  
1.  <span data-ttu-id="4ba3e-108">在分发服务器上配置分发。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-108">Configure distribution at the distributor.</span></span> <span data-ttu-id="4ba3e-109">如果要使用存储过程来进行配置，则运行 `sp_adddistributor`。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-109">If stored procedures are being used for configuration, run `sp_adddistributor`.</span></span> <span data-ttu-id="4ba3e-110">使用 *@password* 参数来标识在远程发布服务器连接到分发服务器时将使用的密码。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-110">Use the *@password* parameter to identify the password that will be used when a remote publisher connects to the distributor.</span></span> <span data-ttu-id="4ba3e-111">在设置远程分发服务器时，每台远程发布服务器上也将需要密码。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-111">The password will also be needed at each remote publisher when the remote distributor is set up.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  <span data-ttu-id="4ba3e-112">在分发服务器上创建分发数据库。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-112">Create the distribution database at the distributor.</span></span> <span data-ttu-id="4ba3e-113">如果要使用存储过程来进行配置，则运行 `sp_adddistributiondb`。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-113">If stored procedures are being used for configuration, run `sp_adddistributiondb`.</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  <span data-ttu-id="4ba3e-114">配置远程发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-114">Configure the remote publisher.</span></span> <span data-ttu-id="4ba3e-115">如果要使用存储过程来配置分发服务器，则运行 `sp_adddistpublisher`。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-115">If stored procedures are being used to configure the distributor, run `sp_adddistpublisher`.</span></span> <span data-ttu-id="4ba3e-116">*@security_mode*参数用于确定如何将从复制代理运行的发布服务器验证存储过程连接到当前的主副本。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-116">The *@security_mode* parameter is used to determine how the publisher validation stored procedure that is run from the replication agents, connects to the current primary.</span></span> <span data-ttu-id="4ba3e-117">如果设置为 1，则使用 Windows 身份验证来连接到当前主副本。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-117">If set to 1 Windows authentication is used to connect to the current primary.</span></span> <span data-ttu-id="4ba3e-118">如果设置为0，则将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证与指定的 *@login* 和值一起使用 *@password* 。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-118">If set to 0, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authentication is used with the specified *@login* and *@password* values.</span></span> <span data-ttu-id="4ba3e-119">指定的登录名和密码必须在每个辅助副本上均有效才能让验证存储过程成功地连接到相应的副本。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-119">The login and password specified must be valid at each secondary replica for the validation stored procedure to successfully connect to that replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4ba3e-120">如果任何已修改的复制代理在分发服务器之外的计算机上运行，则使用 Windows 身份验证连接到主副本的方法将要求为副本主机之间的通信配置 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-120">If any modified replication agents run on a computer other than the distributor, use of Windows authentication for the connection to the primary will require Kerberos authentication to be configured for the communication between the replica host computers.</span></span> <span data-ttu-id="4ba3e-121">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名连接到当前主副本的方法无需 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-121">Use of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login for the connection to the current primary will not require Kerberos authentication.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 <span data-ttu-id="4ba3e-122">有关详细信息，请参阅 [sp_adddistpublisher (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-122">For more information, see [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).</span></span>  
  
### <a name="configure-the-publisher-at-the-original-publisher"></a><span data-ttu-id="4ba3e-123">在原始发布服务器上配置发布服务器</span><span class="sxs-lookup"><span data-stu-id="4ba3e-123">Configure the publisher at the original publisher</span></span>
  
1.  <span data-ttu-id="4ba3e-124">配置远程分发。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-124">Configure remote distribution.</span></span> <span data-ttu-id="4ba3e-125">如果要使用存储过程来配置发布服务器，则运行 `sp_adddistributor`。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-125">If stored procedures are being used to configure the publisher, run `sp_adddistributor`.</span></span> <span data-ttu-id="4ba3e-126">指定与在 *@password* 分发服务器上运行时使用的相同的值， `sp_adddistrbutor` 以设置分发。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-126">Specify the same value for *@password* as that used when `sp_adddistrbutor` was run at the distributor to set up distribution.</span></span>  
  
    ```sql
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  <span data-ttu-id="4ba3e-127">启用数据库复制。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-127">Enable the database for replication.</span></span> <span data-ttu-id="4ba3e-128">如果要使用存储过程来配置发布服务器，则运行 `sp_replicationdboption`。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-128">If stored procedures are being used to configure the publisher, run `sp_replicationdboption`.</span></span> <span data-ttu-id="4ba3e-129">如果要为数据库同时配置事务复制和合并复制，则必须分别启用它们。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-129">If both transactional and merge replication are to be configured for the database, each must be enabled.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  <span data-ttu-id="4ba3e-130">创建复制发布、文章和订阅。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-130">Create the replication publication, articles, and subscriptions.</span></span> <span data-ttu-id="4ba3e-131">有关如何配置复制的详细信息，请参阅“发布数据和数据库对象”。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-131">For more information about how to configure replication, see Publishing Data and Database objects.</span></span>  
  
##  <a name="2-configure-the-alwayson-availability-group"></a><a name="step2"></a><span data-ttu-id="4ba3e-132">2. 配置 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="4ba3e-132">2. Configure the AlwaysOn Availability Group</span></span>  
 <span data-ttu-id="4ba3e-133">在目标主副本上，创建包含已发布的（或即将要发布的）数据库作为成员数据库的可用性组。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-133">At the intended primary, create the availability group with the published (or to be published) database as a member database.</span></span> <span data-ttu-id="4ba3e-134">如果使用可用性组向导，则您可允许该向导最初同步辅助副本数据库，或者您可以使用备份和还原手动执行初始化。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-134">If using the Availability Group Wizard, you can either allow the wizard to initially synchronize the secondary replica databases or you can perform the initialization manually by using backup and restore.</span></span>  
  
 <span data-ttu-id="4ba3e-135">为可用性组创建一个 DNS 侦听器，复制代理将使用它连接到当前主副本。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-135">Create a DNS listener for the availability group that will be used by the replication agents to connect to the current primary.</span></span> <span data-ttu-id="4ba3e-136">指定的侦听器名称将用作原始发布服务器/已发布数据库对的重定向的目标。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-136">The listener name that is specified will be used as the target of redirection for the original publisher/published database pair.</span></span> <span data-ttu-id="4ba3e-137">例如，如果您使用 DDL 来配置可用性组，则可使用以下代码示例为名为 `MyAG` 的现有可用性组指定可用性组侦听器：</span><span class="sxs-lookup"><span data-stu-id="4ba3e-137">For example, if you are using DDL to configure the availability group, the following code example can be used to specify an availability group listener for an existing availability group named `MyAG`:</span></span>  
  
```sql
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 <span data-ttu-id="4ba3e-138">有关详细信息，请参阅[创建和配置可用性组 (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-138">For more information, see [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md).</span></span>  
  
##  <a name="3-insure-that-all-of-the-secondary-replica-hosts-are-configured-for-replication"></a><a name="step3"></a><span data-ttu-id="4ba3e-139">3. 确保所有辅助副本主机均已配置为进行复制</span><span class="sxs-lookup"><span data-stu-id="4ba3e-139">3. Insure that all of the Secondary Replica Hosts are Configured for Replication</span></span>  
 <span data-ttu-id="4ba3e-140">在每个辅助副本主机上，确保已将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 配置为支持复制。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-140">At each secondary replica host, verify that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been configured to support replication.</span></span> <span data-ttu-id="4ba3e-141">可在每个辅助副本主机上运行以下查询来确定是否安装了复制功能：</span><span class="sxs-lookup"><span data-stu-id="4ba3e-141">The following query can be run at each secondary replica host to determine whether replication is installed:</span></span>  
  
```sql
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 <span data-ttu-id="4ba3e-142">如果 *@installed* 为0，则必须将复制添加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装中。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-142">If *@installed* is 0, replication must be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span>  
  
##  <a name="4-configure-the-secondary-replica-hosts-as-replication-publishers"></a><a name="step4"></a> <span data-ttu-id="4ba3e-143">4.将辅助副本主机配置为复制发布服务器</span><span class="sxs-lookup"><span data-stu-id="4ba3e-143">4. Configure the Secondary Replica Hosts as Replication Publishers</span></span>  
 <span data-ttu-id="4ba3e-144">辅助副本不能充当复制发布服务器或重新发布服务器，但必须配置复制以便在故障转移之后辅助副本可以接管。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-144">A secondary replica cannot act as a replication publisher or republisher but replication must be configured so that the secondary can take over after a failover.</span></span> <span data-ttu-id="4ba3e-145">在分发服务器上，为每个辅助副本主机配置分发。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-145">At the distributor, configure distribution for each secondary replica host.</span></span> <span data-ttu-id="4ba3e-146">指定在向分发服务器添加原始发布服务器时所指定的相同的分发数据库和工作目录。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-146">Specify the same distribution database and working directory as was specified when the original publisher was added to the distributor.</span></span> <span data-ttu-id="4ba3e-147">如果您使用存储过程来配置分发，则使用 `sp_adddistpublisher` 以将远程发布服务器与分发服务器相关联。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-147">If you are using stored procedures to configure distribution, use `sp_adddistpublisher` to associate the remote publishers with the distributor.</span></span> <span data-ttu-id="4ba3e-148">如果 *@login* 对 *@password* 原始发布服务器使用了和，则在将辅助副本主机作为发布服务器添加时，为每个指定相同的值。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-148">If *@login* and *@password* were used for the original publisher, specify the same values for each when you add the secondary replica hosts as publishers.</span></span>  
  
```sql
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 <span data-ttu-id="4ba3e-149">在每个辅助副本主机上配置分发。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-149">At each secondary replica host, configure distribution.</span></span> <span data-ttu-id="4ba3e-150">将原始发布服务器的分发服务器标识为远程分发服务器。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-150">Identify the distributor of the original publisher as the remote distributor.</span></span> <span data-ttu-id="4ba3e-151">使用最初在分发服务器上运行 `sp_adddistributor` 时所使用的相同密码。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-151">Use the same password as that used when `sp_adddistributor` was run originally at the distributor.</span></span> <span data-ttu-id="4ba3e-152">如果要使用存储过程来配置分发，则 *@password* 使用的参数 `sp_adddistributor` 来指定密码。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-152">If stored procedures are being used to configure distribution, the *@password* parameter of `sp_adddistributor` is used to specify the password.</span></span>  
  
```sql
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 <span data-ttu-id="4ba3e-153">在每个辅助副本主机上，确保数据库发布的推送订阅服务器显示为链接服务器。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-153">At each secondary replica host, make sure that the push subscribers of the database publications appear as linked servers.</span></span> <span data-ttu-id="4ba3e-154">如果要使用存储过程来配置远程发布服务器，则使用 `sp_addlinkedserver` 将订阅服务器（如果尚未存在）作为链接服务器添加到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-154">If stored procedures are being used to configure the remote publishers, use `sp_addlinkedserver` to add the subscribers (if not already present) as linked servers to the publishers.</span></span>  
  
```sql
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="5-redirect-the-original-publisher-to-the-ag-listener-name"></a><a name="step5"></a> <span data-ttu-id="4ba3e-155">5.将原始发布服务器重定向到 AG 侦听器名称</span><span class="sxs-lookup"><span data-stu-id="4ba3e-155">5. Redirect the Original Publisher to the AG Listener Name</span></span>  
 <span data-ttu-id="4ba3e-156">在分发服务器上的分发数据库中，运行存储过程 `sp_redirect_publisher` 以将原始发布服务器和已发布的数据库与可用性组的可用性组侦听器名称相关联。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-156">At the distributor, in the distribution database, run the stored procedure `sp_redirect_publisher` to associate the original publisher and the published database with the availability group listener name of the availability group.</span></span>  
  
```sql
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="6-run-the-replication-validation-stored-procedure-to-verify-the-configuration"></a><a name="step6"></a> <span data-ttu-id="4ba3e-157">6.运行复制验证存储过程以验证配置</span><span class="sxs-lookup"><span data-stu-id="4ba3e-157">6. Run the Replication Validation Stored Procedure to Verify the Configuration</span></span>  
 <span data-ttu-id="4ba3e-158">在分发服务器上的分发数据库中，运行存储过程 `sp_validate_replica_hosts_as_publishers` 以确认现在已将所有副本主机配置为充当已发布的数据库的发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-158">At the distributor, in the distribution database, run the stored procedure `sp_validate_replica_hosts_as_publishers` to verify that all replica hosts are now configured to serve as publishers for the published database.</span></span>  
  
```sql
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 <span data-ttu-id="4ba3e-159">应在每个可用性组副本主机上使用具有足够授权的登录名来运行存储过程 `sp_validate_replica_hosts_as_publishers`，以查询有关可用性组的信息。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-159">The stored procedure `sp_validate_replica_hosts_as_publishers` should be run from a login with sufficient authorization at each availability group replica host to query for information about the availability group.</span></span> <span data-ttu-id="4ba3e-160">与不同 `sp_validate_redirected_publisher` ，它使用调用方的凭据，而不使用保存在 MSdistpublishers 中的登录名来连接到可用性组副本。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-160">Unlike `sp_validate_redirected_publisher`, it uses the credentials of the caller and does not use the login retained in msdb.dbo.MSdistpublishers to connect to the availability group replicas.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ba3e-161">在验证不允许读取访问或要求指定读取意图的辅助副本主机时，`sp_validate_replica_hosts_as_publishers` 将失败，并显示以下错误。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-161">`sp_validate_replica_hosts_as_publishers` will fail with the following error when validating secondary replica hosts that do not allow read access, or require read intent to be specified.</span></span>  
>   
>  <span data-ttu-id="4ba3e-162">消息 21899，级别 11，状态 1，过程 `sp_hadr_verify_subscribers_at_publisher`，第 109 行</span><span class="sxs-lookup"><span data-stu-id="4ba3e-162">Msg 21899, Level 11, State 1, Procedure `sp_hadr_verify_subscribers_at_publisher`, Line 109</span></span>  
>   
>  <span data-ttu-id="4ba3e-163">重定向的发布服务器“MyReplicaHostName”处的查询失败，该查询用于确定是否有原始发布服务器“MyOriginalPublisher”的订阅服务器的 sysserver 条目，出现错误“976”，错误消息“错误 976，级别 14，状态 1，消息：目标数据库‘MyPublishedDB’正参与某个可用性组，查询当前无法访问该数据库。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-163">The query at the redirected publisher 'MyReplicaHostName' to determine whether there were sysserver entries for the subscribers of the original publisher 'MyOriginalPublisher' failed with error '976', error message 'Error 976, Level 14, State 1, Message: The target database, 'MyPublishedDB', is participating in an availability group and is currently not accessible for queries.</span></span> <span data-ttu-id="4ba3e-164">数据移动被挂起，或者未启用可用性副本以便用于读访问。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-164">Either data movement is suspended or the availability replica is not enabled for read access.</span></span> <span data-ttu-id="4ba3e-165">若要允许对该可用性组中的这一数据库和其他数据库进行只读访问，请对组中一个或多个辅助可用性副本启用只读访问权限。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-165">To allow read-only access to this and other databases in the availability group, enable read access to one or more secondary availability replicas in the group.</span></span>  <span data-ttu-id="4ba3e-166">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书中的 `ALTER AVAILABILITY GROUP` 语句。”。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-166">For more information, see the `ALTER AVAILABILITY GROUP` statement in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.'.</span></span>  
>   
>  <span data-ttu-id="4ba3e-167">副本主机“MyReplicaHostName”遇到了一个或多个发布服务器验证错误。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-167">One or more publisher validation errors were encountered for replica host 'MyReplicaHostName'.</span></span>  
  
 <span data-ttu-id="4ba3e-168">这是预期的行为。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-168">This is expected behavior.</span></span> <span data-ttu-id="4ba3e-169">必须通过在主机上直接查询 sysserver 条目来验证这些次要副本主机上是否存在订阅服务器条目。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-169">You must verify the presence of the subscriber server entries at these secondary replica hosts by querying for the sysserver entries directly at the host.</span></span>  
  
##  <a name="7-add-the-original-publisher-to-replication-monitor"></a><a name="step7"></a> <span data-ttu-id="4ba3e-170">7.向复制监视器添加原始发布服务器</span><span class="sxs-lookup"><span data-stu-id="4ba3e-170">7. Add the Original Publisher to Replication Monitor</span></span>  
 <span data-ttu-id="4ba3e-171">在每个可用性组副本上，向复制监视器添加原始发布服务器。</span><span class="sxs-lookup"><span data-stu-id="4ba3e-171">At each availability group replica, add the original publisher to Replication Monitor.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4ba3e-172">相关任务</span><span class="sxs-lookup"><span data-stu-id="4ba3e-172">Related Tasks</span></span>  
 <span data-ttu-id="4ba3e-173">**复制**</span><span class="sxs-lookup"><span data-stu-id="4ba3e-173">**Replication**</span></span>  
  
-   [<span data-ttu-id="4ba3e-174">维护 AlwaysOn 发布数据库 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4ba3e-174">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [<span data-ttu-id="4ba3e-175">复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4ba3e-175">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="4ba3e-176">复制管理常见问题解答</span><span class="sxs-lookup"><span data-stu-id="4ba3e-176">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
 <span data-ttu-id="4ba3e-177">**创建和配置可用性组**</span><span class="sxs-lookup"><span data-stu-id="4ba3e-177">**To create and configure an availability group**</span></span>  
  
-   [<span data-ttu-id="4ba3e-178">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-178">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4ba3e-179">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-179">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4ba3e-180">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="4ba3e-181">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="4ba3e-182">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-182">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="4ba3e-183">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="4ba3e-183">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="4ba3e-184">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-184">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="4ba3e-185">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-185">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="4ba3e-186">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-186">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="4ba3e-187">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4ba3e-187">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4ba3e-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ba3e-188">See Also</span></span>  
 <span data-ttu-id="4ba3e-189">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="4ba3e-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="4ba3e-190">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4ba3e-190">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="4ba3e-191">[AlwaysOn 可用性组：互操作性 (SQL Server) ](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4ba3e-191">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="4ba3e-192">SQL Server 复制</span><span class="sxs-lookup"><span data-stu-id="4ba3e-192">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
