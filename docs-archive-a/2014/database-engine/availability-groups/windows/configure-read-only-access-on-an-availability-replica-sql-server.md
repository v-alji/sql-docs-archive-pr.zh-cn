---
title: 配置对可用性副本的只读访问 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab13081396aff46d193c1b0449d6b93042ee60d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688235"
---
# <a name="configure-read-only-access-on-an-availability-replica-sql-server"></a><span data-ttu-id="512f9-102">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="512f9-102">Configure Read-Only Access on an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="512f9-103">默认情况下，允许对主副本进行读写和读意向访问，不允许连接到 AlwaysOn 可用性组的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="512f9-103">By default both read-write and read-intent access are allowed to the primary replica and no connections are allowed to secondary replicas of an AlwaysOn availability group.</span></span> <span data-ttu-id="512f9-104">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell 来配置 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中 AlwaysOn 可用性组的可用性副本的连接访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-104">This topic describes how to configure connection access on an availability replica of an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="512f9-105">有关对次要副本允许只读访问的含义的信息以及有关对连接访问的介绍，请参阅[关于对可用性副本的客户端连接访问 (SQL Server)](about-client-connection-access-to-availability-replicas-sql-server.md) 和[活动次要副本：可读次要副本（AlwaysOn 可用性组）](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-105">For information about the implications of enabling read-only access for a secondary replica and for an introduction to connection access, see [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) and [Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="512f9-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="512f9-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="512f9-107">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="512f9-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="512f9-108">若要配置不同的连接访问，您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="512f9-108">To configure different connection access, you must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="512f9-109">Security</span><span class="sxs-lookup"><span data-stu-id="512f9-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="512f9-110">权限</span><span class="sxs-lookup"><span data-stu-id="512f9-110">Permissions</span></span>  
  
|<span data-ttu-id="512f9-111">任务</span><span class="sxs-lookup"><span data-stu-id="512f9-111">Task</span></span>|<span data-ttu-id="512f9-112">权限</span><span class="sxs-lookup"><span data-stu-id="512f9-112">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="512f9-113">在创建可用性组时配置副本</span><span class="sxs-lookup"><span data-stu-id="512f9-113">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="512f9-114">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="512f9-114">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="512f9-115">修改可用性副本</span><span class="sxs-lookup"><span data-stu-id="512f9-115">To modify an availability replica</span></span>|<span data-ttu-id="512f9-116">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="512f9-116">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="512f9-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="512f9-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="512f9-118">**配置对可用性副本的访问**</span><span class="sxs-lookup"><span data-stu-id="512f9-118">**To configure access on an availability replica**</span></span>  
  
1.  <span data-ttu-id="512f9-119">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="512f9-119">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="512f9-120">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="512f9-120">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="512f9-121">单击要更改其副本的可用性组。</span><span class="sxs-lookup"><span data-stu-id="512f9-121">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="512f9-122">右键单击该可用性副本，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="512f9-122">Right-click the availability replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="512f9-123">在 **“可用性副本属性”** 对话框中，可以更改主角色和辅助角色的连接访问设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="512f9-123">In the **Availability Replica Properties** dialog box, you can change the connection access for the primary role and for the secondary role, as follows:</span></span>  
  
    -   <span data-ttu-id="512f9-124">对于辅助角色，从 **“可读取辅助角色”** 下拉列表中选择一个新值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="512f9-124">For the secondary role, select a new value from the **Readable secondary** drop list, as follows:</span></span>  
  
         <span data-ttu-id="512f9-125">**是**</span><span class="sxs-lookup"><span data-stu-id="512f9-125">**No**</span></span>  
         <span data-ttu-id="512f9-126">不允许与此副本的辅助数据库的用户连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-126">No user connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="512f9-127">它们不可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-127">They are not available for read access.</span></span> <span data-ttu-id="512f9-128">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="512f9-128">This is the default setting.</span></span>  
  
         <span data-ttu-id="512f9-129">**仅限读意向**</span><span class="sxs-lookup"><span data-stu-id="512f9-129">**Read-intent only**</span></span>  
         <span data-ttu-id="512f9-130">仅允许与此副本的辅助数据库的只读连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-130">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="512f9-131">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-131">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="512f9-132">**是**</span><span class="sxs-lookup"><span data-stu-id="512f9-132">**Yes**</span></span>  
         <span data-ttu-id="512f9-133">允许与此副本的辅助数据库的所有连接，但仅限读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-133">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="512f9-134">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-134">The secondary database(s) are all available for read access.</span></span>  
  
    -   <span data-ttu-id="512f9-135">对于主角色，从 **“主角色中的连接”** 下拉列表中选择一个新值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="512f9-135">For the primary role, select a new value from the **Connections in primary role** drop list, as follows:</span></span>  
  
         <span data-ttu-id="512f9-136">**允许所有连接**</span><span class="sxs-lookup"><span data-stu-id="512f9-136">**Allow all connections**</span></span>  
         <span data-ttu-id="512f9-137">主副本中的数据库允许所有连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-137">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="512f9-138">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="512f9-138">This is the default setting.</span></span>  
  
         <span data-ttu-id="512f9-139">**允许读/写连接**</span><span class="sxs-lookup"><span data-stu-id="512f9-139">**Allow read/write connections**</span></span>  
         <span data-ttu-id="512f9-140">在 Application Intent 属性设置为 **ReadWrite** 或者未设置 Application Intent 连接属性时，将允许连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-140">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="512f9-141">不允许 Application Intent 连接属性设置为 **ReadOnly** 的连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-141">Connections where the Application Intent connection property is set to **ReadOnly** are not allowed.</span></span> <span data-ttu-id="512f9-142">这可帮助阻止客户错误地将读意向工作负荷连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="512f9-142">This can help prevent customers from connecting a read-intent work load to the primary replica by mistake.</span></span> <span data-ttu-id="512f9-143">有关 Application Intent 连接属性的详细信息，请参阅 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-143">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="512f9-144">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="512f9-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="512f9-145">**配置对可用性副本的访问**</span><span class="sxs-lookup"><span data-stu-id="512f9-145">**To configure access on an availability replica**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="512f9-146">有关此过程的示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="512f9-146">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="512f9-147">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="512f9-147">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="512f9-148">若要指定的是新可用性组的副本，请使用 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="512f9-148">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="512f9-149">如果正在添加或修改现有可用性组的副本，请使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="512f9-149">If you are adding or modifying a replica of an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="512f9-150">若要配置辅助角色的连接访问，请在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 SECONDARY_ROLE 选项，如下所示：</span><span class="sxs-lookup"><span data-stu-id="512f9-150">To configure connection access for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="512f9-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="512f9-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span></span>  
  
         <span data-ttu-id="512f9-152">其中：</span><span class="sxs-lookup"><span data-stu-id="512f9-152">where,</span></span>  
  
         <span data-ttu-id="512f9-153">是</span><span class="sxs-lookup"><span data-stu-id="512f9-153">NO</span></span>  
         <span data-ttu-id="512f9-154">不允许与此副本的辅助数据库的直接连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-154">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="512f9-155">它们不可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-155">They are not available for read access.</span></span> <span data-ttu-id="512f9-156">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="512f9-156">This is the default setting.</span></span>  
  
         <span data-ttu-id="512f9-157">READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="512f9-157">READ_ONLY</span></span>  
         <span data-ttu-id="512f9-158">仅允许与此副本的辅助数据库的只读连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-158">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="512f9-159">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-159">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="512f9-160">ALL</span><span class="sxs-lookup"><span data-stu-id="512f9-160">ALL</span></span>  
         <span data-ttu-id="512f9-161">允许与此副本的辅助数据库的所有连接，但仅限读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-161">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="512f9-162">辅助数据库全都可用于读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-162">The secondary database(s) are all available for read access.</span></span>  
  
3.  <span data-ttu-id="512f9-163">若要配置主角色的连接访问，请在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 PRIMARY_ROLE 选项，如下所示：</span><span class="sxs-lookup"><span data-stu-id="512f9-163">To configure connection access for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
     <span data-ttu-id="512f9-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="512f9-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span></span>  
  
     <span data-ttu-id="512f9-165">其中：</span><span class="sxs-lookup"><span data-stu-id="512f9-165">where,</span></span>  
  
     <span data-ttu-id="512f9-166">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="512f9-166">READ_WRITE</span></span>  
     <span data-ttu-id="512f9-167">不允许 Application Intent 连接属性设置为 **ReadOnly** 的连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-167">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span>  <span data-ttu-id="512f9-168">在 Application Intent 属性设置为 **ReadWrite** 或者未设置 Application Intent 连接属性时，将允许连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-168">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="512f9-169">有关 Application Intent 连接属性的详细信息，请参阅 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-169">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
     <span data-ttu-id="512f9-170">ALL</span><span class="sxs-lookup"><span data-stu-id="512f9-170">ALL</span></span>  
     <span data-ttu-id="512f9-171">主副本中的数据库允许所有连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-171">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="512f9-172">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="512f9-172">This is the default setting.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="512f9-173">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="512f9-173">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="512f9-174">下面的示例将辅助副本添加到名为 *AG2*的可用性组。</span><span class="sxs-lookup"><span data-stu-id="512f9-174">The following example adds a secondary replica to an availability group named *AG2*.</span></span> <span data-ttu-id="512f9-175">一个独立服务器实例 *COMPUTER03\HADR_INSTANCE*被指定为承载新的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="512f9-175">A stand-alone server instance, *COMPUTER03\HADR_INSTANCE*, is specified to host the new availability replica.</span></span> <span data-ttu-id="512f9-176">将此副本配置为对主角色允许读写连接，对辅助角色仅允许读意向连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-176">This replica configured to allow only read-write connections for the primary role and to allow only read-intent connections for secondary role.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="512f9-177">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="512f9-177">Using PowerShell</span></span>  

### <a name="to-configure-access-on-an-availability-replica"></a><span data-ttu-id="512f9-178">配置对可用性副本的访问</span><span class="sxs-lookup"><span data-stu-id="512f9-178">To configure access on an availability replica</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="512f9-179">有关代码示例，请参阅本节后面的 PowerShell 示例。</span><span class="sxs-lookup"><span data-stu-id="512f9-179">For a code example, see the PowerShell examples later in this section.</span></span>  
  
1.  <span data-ttu-id="512f9-180">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="512f9-180">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="512f9-181">在将可用性副本添加到可用性组中时，请使用 `New-SqlAvailabilityReplica` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="512f9-181">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="512f9-182">在修改现有可用性副本时，请使用 `Set-SqlAvailabilityReplica` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="512f9-182">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="512f9-183">相关参数如下：</span><span class="sxs-lookup"><span data-stu-id="512f9-183">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="512f9-184">若要配置辅助角色的连接访问，请指定 `ConnectionModeInSecondaryRole` *secondary_role_keyword*参数，其中*secondary_role_keyword*等于以下值之一：</span><span class="sxs-lookup"><span data-stu-id="512f9-184">To configure connection access for the secondary role, specify the `ConnectionModeInSecondaryRole`*secondary_role_keyword* parameter, where *secondary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowNoConnections`  
         <span data-ttu-id="512f9-185">不允许直接连接到辅助副本中的数据库，且不支持读取这些数据库。</span><span class="sxs-lookup"><span data-stu-id="512f9-185">No direct connections are allowed to the databases in the secondary replica and the databases are not available for read access.</span></span> <span data-ttu-id="512f9-186">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="512f9-186">This is the default setting.</span></span>  
  
         `AllowReadIntentConnectionsOnly`  
         <span data-ttu-id="512f9-187">只允许连接应用程序意向属性设置为 **ReadOnly**的辅助副本中的数据库。</span><span class="sxs-lookup"><span data-stu-id="512f9-187">Connections are allowed only to the databases in the secondary replica where the Application Intent property is set to **ReadOnly**.</span></span> <span data-ttu-id="512f9-188">有关此属性的详细信息，请参阅 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-188">For more information about this property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="512f9-189">允许针对辅助副本中的数据库的所有连接进行只读访问。</span><span class="sxs-lookup"><span data-stu-id="512f9-189">All connections are allowed to the databases in the secondary replica for read-only access.</span></span>  
  
    -   <span data-ttu-id="512f9-190">若要为主要角色配置连接访问，请指定 `ConnectionModeInPrimaryRole` *primary_role_keyword*，其中*primary_role_keyword*等于以下值之一：</span><span class="sxs-lookup"><span data-stu-id="512f9-190">To configure connection access for the primary role, specify `ConnectionModeInPrimaryRole`*primary_role_keyword*, where *primary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowReadWriteConnections`  
         <span data-ttu-id="512f9-191">不允许 Application Intent 连接属性设置为 ReadOnly 的连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-191">Connections where the Application Intent connection property is set to ReadOnly are disallowed.</span></span> <span data-ttu-id="512f9-192">在 Application Intent 属性设置为 ReadWrite 或者未设置 Application Intent 连接属性时，将允许连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-192">When the Application Intent property is set to ReadWrite or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="512f9-193">有关 Application Intent 连接属性的详细信息，请参阅 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-193">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="512f9-194">主副本中的数据库允许所有连接。</span><span class="sxs-lookup"><span data-stu-id="512f9-194">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="512f9-195">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="512f9-195">This is the default setting.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="512f9-196">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="512f9-196">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="512f9-197">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-197">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="512f9-198">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="512f9-198">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
<span data-ttu-id="512f9-199">下面的示例将 `ConnectionModeInSecondaryRole` 和 `ConnectionModeInPrimaryRole` 参数均设置为 `AllowAllConnections`。</span><span class="sxs-lookup"><span data-stu-id="512f9-199">The following example, sets the both the `ConnectionModeInSecondaryRole` and `ConnectionModeInPrimaryRole` parameters to `AllowAllConnections`.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  

Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `
 -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `
-InputObject $primaryReplica
```  

##  <a name="follow-up-after-configuring-read-only-access-for-an-availability-replica"></a><a name="FollowUp"></a> <span data-ttu-id="512f9-200">跟进：为可用性副本配置只读访问后</span><span class="sxs-lookup"><span data-stu-id="512f9-200">Follow Up: After Configuring Read-Only Access for an Availability Replica</span></span>  
 <span data-ttu-id="512f9-201">**对可读取辅助副本的只读访问**</span><span class="sxs-lookup"><span data-stu-id="512f9-201">**Read-only access to a readable secondary replica**</span></span>  
  
-   <span data-ttu-id="512f9-202">使用[Bcp 实用工具](../../../tools/bcp-utility.md)或[sqlcmd 实用工具](../../../tools/sqlcmd-utility.md)时，可以通过指定开关来指定对启用了只读访问权限的任何辅助副本的只读访问 `-K ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="512f9-202">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
-   <span data-ttu-id="512f9-203">使客户端应用程序能够连接到可读取辅助副本：</span><span class="sxs-lookup"><span data-stu-id="512f9-203">To enable client applications to connect to readable secondary replicas:</span></span>  
  
    ||<span data-ttu-id="512f9-204">先决条件</span><span class="sxs-lookup"><span data-stu-id="512f9-204">Prerequisite</span></span>|<span data-ttu-id="512f9-205">链接</span><span class="sxs-lookup"><span data-stu-id="512f9-205">Link</span></span>|  
    |-|------------------|----------|  
    |<span data-ttu-id="512f9-206">![复选框](../../media/checkboxemptycenterxtraspacetopandright.gif "复选框")</span><span class="sxs-lookup"><span data-stu-id="512f9-206">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="512f9-207">确保可用性组具有侦听器。</span><span class="sxs-lookup"><span data-stu-id="512f9-207">Ensure that the availability group has a listener.</span></span>|[<span data-ttu-id="512f9-208">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="512f9-208">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)|  
    |<span data-ttu-id="512f9-209">![复选框](../../media/checkboxemptycenterxtraspacetopandright.gif "复选框")</span><span class="sxs-lookup"><span data-stu-id="512f9-209">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="512f9-210">为可用性组配置只读路由。</span><span class="sxs-lookup"><span data-stu-id="512f9-210">Configure read-only routing for the availability group.</span></span>|[<span data-ttu-id="512f9-211">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="512f9-211">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 <span data-ttu-id="512f9-212">**在故障转移后可能会影响触发器和作业的因素**</span><span class="sxs-lookup"><span data-stu-id="512f9-212">**Factors that might affect triggers and jobs after a failover**</span></span>  
  
 <span data-ttu-id="512f9-213">如果您在非可读取辅助数据库或可读取辅助数据库上正运行时具有将失败的触发器和作业，则需要编写针对这些触发器和作业的脚本，以便对给定副本进行检查以确定该数据库是主数据库还是可读取辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="512f9-213">If you have triggers and jobs that will fail when running on a non-readable secondary database or on a readable secondary database, you need to script the triggers and jobs to check on a given replica to determine whether the database is a primary database or is a readable secondary database.</span></span> <span data-ttu-id="512f9-214">若要获取该信息，请使用 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 函数以返回数据库的 **Updatability** 属性。</span><span class="sxs-lookup"><span data-stu-id="512f9-214">To obtain this information, use the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **Updatability** property of the database.</span></span> <span data-ttu-id="512f9-215">若要标识只读数据库，请按如下所示将 READ_ONLY 指定为值：</span><span class="sxs-lookup"><span data-stu-id="512f9-215">To identify a read-only database, specify READ_ONLY as the value, as follows:</span></span>  
  
```  
DATABASEPROPERTYEX([db name],'Updatability') = N'READ_ONLY'  
```  
  
 <span data-ttu-id="512f9-216">若要标识读写数据库，请将 READ_WRITE 指定为值：</span><span class="sxs-lookup"><span data-stu-id="512f9-216">To identify a read-write database, specify READ_WRITE as the value.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="512f9-217">相关任务</span><span class="sxs-lookup"><span data-stu-id="512f9-217">Related Tasks</span></span>  
  
-   [<span data-ttu-id="512f9-218">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="512f9-218">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="512f9-219">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="512f9-219">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="512f9-220">相关内容</span><span class="sxs-lookup"><span data-stu-id="512f9-220">Related Content</span></span>  
  
-   [<span data-ttu-id="512f9-221">Always On：可读次要副本的价值主张</span><span class="sxs-lookup"><span data-stu-id="512f9-221">Always On: Value Proposition of Readable Secondary</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-value-proposition-of-readable-secondary)  
  
-   [<span data-ttu-id="512f9-222">Always On：为什么存在两个选项用于为读取工作负荷启用辅助副本？</span><span class="sxs-lookup"><span data-stu-id="512f9-222">Always On: Why there are two options to enable a secondary replica for read workload?</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload)  
  
-   [<span data-ttu-id="512f9-223">Always On：设置可读次要副本</span><span class="sxs-lookup"><span data-stu-id="512f9-223">Always On: Setting up Readable Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-setting-up-readable-seconary-replica)  
  
-   [<span data-ttu-id="512f9-224">Always On：我启用了可读次要副本，但我的查询却受阻？</span><span class="sxs-lookup"><span data-stu-id="512f9-224">Always On: I just enabled Readable Secondary but my query is blocked?</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-i-just-enabled-readable-secondary-but-my-query-is-blocked)  
  
-   [<span data-ttu-id="512f9-225">Always On：在可读次要副本、只读数据库和数据库快照上提供最新统计信息</span><span class="sxs-lookup"><span data-stu-id="512f9-225">Always On: Making latest statistics available on Readable Secondary, Read-Only database and Database Snapshot</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-making-latest-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot)  
  
-   [<span data-ttu-id="512f9-226">Always On：使用只读数据库、数据库快照和次要副本上的统计信息的挑战</span><span class="sxs-lookup"><span data-stu-id="512f9-226">Always On: Challenges with statistics on ReadOnly database, Database Snapshot and Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica)  
  
-   [<span data-ttu-id="512f9-227">Always On：在次要副本上运行报表工作负荷时对主工作负荷的影响</span><span class="sxs-lookup"><span data-stu-id="512f9-227">Always On: Impact on the primary workload when you run reporting workload on the secondary replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica)  
  
-   [<span data-ttu-id="512f9-228">Always On：将可读次要副本上的报表工作负荷映射到快照隔离的影响</span><span class="sxs-lookup"><span data-stu-id="512f9-228">Always On: Impact of mapping reporting workload on Readable Secondary to Snapshot Isolation</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-of-mapping-reporting-workload-on-readable-secondary-to-snapshot-isolation)  
  
-   [<span data-ttu-id="512f9-229">Always On：最大程度减少在次要副本上运行工作负荷时对 REDO 线程的阻止</span><span class="sxs-lookup"><span data-stu-id="512f9-229">Always On: Minimizing blocking of REDO thread when running reporting workload on Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica)  
  
-   [<span data-ttu-id="512f9-230">Always On：可读次要副本和数据延迟</span><span class="sxs-lookup"><span data-stu-id="512f9-230">Always On: Readable Secondary and data latency</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-readable-secondary-and-data-latency)  
  
## <a name="see-also"></a><span data-ttu-id="512f9-231">另请参阅</span><span class="sxs-lookup"><span data-stu-id="512f9-231">See Also</span></span>  
 <span data-ttu-id="512f9-232">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="512f9-232">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="512f9-233">活动辅助副本：可读辅助副本 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="512f9-233">Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)  
 [<span data-ttu-id="512f9-234">关于对可用性副本的客户端连接访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="512f9-234">About Client Connection Access to Availability Replicas &#40;SQL Server&#41;</span></span>](about-client-connection-access-to-availability-replicas-sql-server.md)  
