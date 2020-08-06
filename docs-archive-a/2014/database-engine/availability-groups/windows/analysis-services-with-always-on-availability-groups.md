---
title: 含有 AlwaysOn 可用性组的 Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 14d16bfd-228c-4870-b463-a283facda965
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9ea0c7f30fd8f431f70284122df7e2a036658f4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577870"
---
# <a name="analysis-services-with-always-on-availability-groups"></a><span data-ttu-id="03428-102">含有 AlwaysOn 可用性组的 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="03428-102">Analysis Services with Always On Availability Groups</span></span>
  <span data-ttu-id="03428-103">AlwaysOn 可用性组是预定义的 SQL Server 关系数据库集合；当有条件触发任一个数据库进行故障转移时，这些数据库将执行集体故障转移，使请求重定向到同一可用性组中其他实例上的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="03428-103">An AlwaysOn availability group is a predefined collection of SQL Server relational databases that failover together when conditions trigger a failover in any one database, redirecting requests to a mirrored database on another instance in the same availability group.</span></span> <span data-ttu-id="03428-104">如果将可用性组用作高可用性解决方案，您可以将该组中的数据库用作 Analysis Services 表格或多维解决方案中的数据源。</span><span class="sxs-lookup"><span data-stu-id="03428-104">If you are using availability groups as your high availability solution, you can use a database in that group as a data source in an Analysis Services tabular or multidimensional solution.</span></span> <span data-ttu-id="03428-105">使用可用性数据库时，以下所有 Analysis Services 操作都能按预期工作：处理或导入数据、直接查询关系数据（使用 ROLAP 存储或 DirectQuery 模式）以及写回。</span><span class="sxs-lookup"><span data-stu-id="03428-105">All of the following Analysis Services operations work as expected when using an availability database: processing or importing data, querying relational data directly (using ROLAP storage or DirectQuery mode), and writeback.</span></span>  
  
 <span data-ttu-id="03428-106">处理和查询属于只读工作负荷。</span><span class="sxs-lookup"><span data-stu-id="03428-106">Processing and querying are read-only workloads.</span></span> <span data-ttu-id="03428-107">您可以通过将这些工作负荷转移到可读辅助副本来改善性能，</span><span class="sxs-lookup"><span data-stu-id="03428-107">You can improve performance by offloading these workloads to a readable secondary replica.</span></span> <span data-ttu-id="03428-108">但这需要执行额外配置。</span><span class="sxs-lookup"><span data-stu-id="03428-108">Additional configuration is required for this scenario.</span></span> <span data-ttu-id="03428-109">请使用本主题中的核对清单来确保遵循所有步骤。</span><span class="sxs-lookup"><span data-stu-id="03428-109">Use the checklist in this topic to ensure you follow all the steps.</span></span>  
  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="03428-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="03428-110">Prerequisites</span></span>  
 <span data-ttu-id="03428-111">您必须具有针对所有副本的 SQL Server 登录名。</span><span class="sxs-lookup"><span data-stu-id="03428-111">You must have a SQL Server login on all replicas.</span></span> <span data-ttu-id="03428-112">必须具有 **sysadmin** 权限才能配置可用性组、侦听器和数据库；但用户只需要 **db_datareader** 权限即可从 Analysis Services 客户端访问数据库。</span><span class="sxs-lookup"><span data-stu-id="03428-112">You must be a **sysadmin** to configure availability groups, listeners, and databases, but users only need **db_datareader** permissions to access the database from an Analysis Services client.</span></span>  
  
 <span data-ttu-id="03428-113">请使用支持表格格式数据流 (TDS) 协议版本 7.4 或更高版本的数据访问接口（如 SQL Server Native Client 11.0），或 .NET Framework 4.02 中用于 SQL Server 的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="03428-113">Use a data provider that supports the tabular data stream (TDS) protocol version 7.4 or newer, such as the SQL Server Native Client 11.0 or the Data Provider for SQL Server in .NET Framework 4.02.</span></span>  
  
 <span data-ttu-id="03428-114">**（仅限只读工作负荷）**。</span><span class="sxs-lookup"><span data-stu-id="03428-114">**(For read-only workloads)**.</span></span> <span data-ttu-id="03428-115">必须为只读连接配置辅助副本角色，可用性组必须具备路由列表，并且 Analysis Services 数据源中的连接必须指定可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="03428-115">The secondary replica role must be configured for read-only connections, the availability group must have a routing list, and the connection in the Analysis Services data source must specify the availability group listener.</span></span> <span data-ttu-id="03428-116">本主题中提供了相关说明。</span><span class="sxs-lookup"><span data-stu-id="03428-116">Instructions are provided in this topic.</span></span>  
  
##  <a name="checklist-use-a-secondary-replica-for-read-only-operations"></a><a name="bkmk_UseSecondary"></a> <span data-ttu-id="03428-117">核对清单：使用辅助副本执行只读操作</span><span class="sxs-lookup"><span data-stu-id="03428-117">Checklist: Use a secondary replica for read-only operations</span></span>  
 <span data-ttu-id="03428-118">除非您的 Analysis Services 解决方案包括写回功能，否则您可以配置数据源连接使用可读的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-118">Unless your Analysis Services solution includes writeback, you can configure a data source connection to use a readable secondary replica.</span></span> <span data-ttu-id="03428-119">如果您的网络连接速度很快，那么辅助副本的数据滞后时间很短，可提供与主副本几乎相同的数据。</span><span class="sxs-lookup"><span data-stu-id="03428-119">If you have a fast network connection, the secondary replica has very low data latency, providing nearly identical data as the primary replica.</span></span> <span data-ttu-id="03428-120">通过将辅助副本用于 Analysis Services 操作，您可以减少主副本上的读写争用，并且更充分地利用可用性组中的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-120">By using the secondary replica for Analysis Services operations, you can reduce read-write contention on the primary replica and get better utilization of secondary replicas in your availability group.</span></span>  
  
 <span data-ttu-id="03428-121">默认情况下，允许对主副本进行读写和读意向访问，同时不允许连接辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-121">By default, both read-write and read-intent access are allowed to the primary replica and no connections are allowed to secondary replicas.</span></span> <span data-ttu-id="03428-122">需要进行额外配置，才能建立与辅助副本的只读客户端连接。</span><span class="sxs-lookup"><span data-stu-id="03428-122">Additional configuration is required to set up a read-only client connection to a secondary replica.</span></span> <span data-ttu-id="03428-123">配置要求对辅助副本设置属性，并运行定义只读路由列表的 T-SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="03428-123">Configuration requires setting properties on the secondary replica and running a T-SQL script that defines a read-only routing list.</span></span> <span data-ttu-id="03428-124">请使用以下过程来确保已执行以上两个步骤。</span><span class="sxs-lookup"><span data-stu-id="03428-124">Use the following procedures to ensure you have performed both steps.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03428-125">以下步骤假定已存在 AlwaysOn 可用性组和数据库。</span><span class="sxs-lookup"><span data-stu-id="03428-125">The following steps assume an existing AlwaysOn availability group and databases.</span></span> <span data-ttu-id="03428-126">如果要配置新组，请使用“新建可用性组向导”创建该组并联接数据库。</span><span class="sxs-lookup"><span data-stu-id="03428-126">If you are configuring a new group, use the New Availability Group Wizard to create the group and join the databases.</span></span> <span data-ttu-id="03428-127">该向导检查先决条件，为每一步提供指导，并执行初始同步。</span><span class="sxs-lookup"><span data-stu-id="03428-127">The wizard checks for prerequisites, provides guidance for each step, and performs the initial synchronization.</span></span> <span data-ttu-id="03428-128">有关详细信息，请参阅[使用可用性组向导 (SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="03428-128">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
#### <a name="step-1-configure-access-on-an-availability-replica"></a><span data-ttu-id="03428-129">第 1 步：配置对可用性副本的访问</span><span class="sxs-lookup"><span data-stu-id="03428-129">Step 1: Configure access on an availability replica</span></span>  
  
1.  <span data-ttu-id="03428-130">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="03428-130">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03428-131">这些步骤来自[配置对可用性副本的只读访问 (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)，为执行此任务提供了其他信息和说明。</span><span class="sxs-lookup"><span data-stu-id="03428-131">These steps are taken from [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md), which provides additional information and alternative instructions for performing this task.</span></span>  
  
2.  <span data-ttu-id="03428-132">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="03428-132">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="03428-133">单击要更改其副本的可用性组。</span><span class="sxs-lookup"><span data-stu-id="03428-133">Click the availability group whose replica you want to change.</span></span> <span data-ttu-id="03428-134">展开 **“可用性副本”**。</span><span class="sxs-lookup"><span data-stu-id="03428-134">Expand **Availability Replicas**.</span></span>  
  
4.  <span data-ttu-id="03428-135">右键单击次要副本，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-135">Right-click the secondary replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="03428-136">在 **“可用性副本属性”** 对话框中，更改辅助角色的连接访问设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="03428-136">In the **Availability Replica Properties** dialog box, change the connection access for the secondary role, as follows:</span></span>  
  
    -   <span data-ttu-id="03428-137">在“可读次要副本”\*\*\*\* 下拉列表中，选择“仅读意向”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-137">In the **Readable secondary** drop list, select **Read-intent only**.</span></span>  
  
    -   <span data-ttu-id="03428-138">在 **“主角色中的连接”** 下拉列表中，选择 **“允许所有连接”**。</span><span class="sxs-lookup"><span data-stu-id="03428-138">In the **Connections in primary role** drop list, select **Allow all connections**.</span></span> <span data-ttu-id="03428-139">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="03428-139">This is the default.</span></span>  
  
    -   <span data-ttu-id="03428-140">或者，在 **“可用性模式”** 下拉列表中，选择 **“同步提交”**。</span><span class="sxs-lookup"><span data-stu-id="03428-140">Optionally, in **Availability mode** drop list, select **Synchronous commit**.</span></span> <span data-ttu-id="03428-141">此步骤不是必需的，但设置它可以确保主副本与辅助副本之间存在数据奇偶校验。</span><span class="sxs-lookup"><span data-stu-id="03428-141">This step is not required, but setting it ensures that there is data parity between the primary and secondary replica.</span></span>  
  
         <span data-ttu-id="03428-142">计划的故障转移也需要该属性。</span><span class="sxs-lookup"><span data-stu-id="03428-142">This property is also a requirement for planned failover.</span></span> <span data-ttu-id="03428-143">如果出于测试目的要执行计划的手动故障转移，请将主副本和辅助副本的 **“可用性模式”** 同时设置为 **“同步提交”** 。</span><span class="sxs-lookup"><span data-stu-id="03428-143">If you want to perform a planned manual failover for testing purposes, set **Availability mode** to **Synchronous commit** for both the primary and secondary replica.</span></span>  
  
#### <a name="step-2-configure-read-only-routing"></a><span data-ttu-id="03428-144">第 2 步：配置只读路由</span><span class="sxs-lookup"><span data-stu-id="03428-144">Step 2: Configure read-only routing</span></span>  
  
1.  <span data-ttu-id="03428-145">连接到主副本。</span><span class="sxs-lookup"><span data-stu-id="03428-145">Connect to the primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03428-146">这些步骤来自 [为可用性组配置只读路由 (SQL Server)](configure-read-only-routing-for-an-availability-group-sql-server.md)，为执行此任务提供了其他信息和说明。</span><span class="sxs-lookup"><span data-stu-id="03428-146">These steps are taken from [Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md), which provides additional information and alternative instructions for performing this task.</span></span>  
  
2.  <span data-ttu-id="03428-147">打开一个查询窗口，在其中粘贴以下脚本。</span><span class="sxs-lookup"><span data-stu-id="03428-147">Open a query window and paste in the following script.</span></span> <span data-ttu-id="03428-148">此脚本执行三项操作：启用对辅助副本的可读连接（默认禁用该连接）、设置只读路由 URL，以及创建确定连接请求的定向先后顺序的路由列表。</span><span class="sxs-lookup"><span data-stu-id="03428-148">This script does three things: enables readable connections to a secondary replica (which is off by default), sets the read-only routing URL, and creates the routing list that prioritizes how connection requests are directed.</span></span>  <span data-ttu-id="03428-149">如果已经在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中设置了属性，则第一个语句（用于允许可读连接）是多余的，但为完整起见仍包括在该脚本中。</span><span class="sxs-lookup"><span data-stu-id="03428-149">The first statement, allowing readable connections, is redundant if you already set the properties in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], but are included for completeness.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER01' WITH   
    (SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER01' WITH   
    (SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER02' WITH   
    (SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER02' WITH   
    (SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
    ALTER AVAILABILITY GROUP [AG1]   
    MODIFY REPLICA ON  
    N'COMPUTER01' WITH   
    (PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
    ALTER AVAILABILITY GROUP [AG1]   
    MODIFY REPLICA ON  
    N'COMPUTER02' WITH   
    (PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
    GO  
    ```  
  
3.  <span data-ttu-id="03428-150">修改该脚本，用对您的部署有效的值取代占位符：</span><span class="sxs-lookup"><span data-stu-id="03428-150">Modify the script, replacing placeholders with values that are valid for your deployment:</span></span>  
  
    -   <span data-ttu-id="03428-151">用承载主副本的服务器实例的名称取代“Computer01”。</span><span class="sxs-lookup"><span data-stu-id="03428-151">Replace 'Computer01' with the name of the server instance that hosts the primary replica.</span></span>  
  
    -   <span data-ttu-id="03428-152">用承载辅助副本的服务器实例的名称取代“Computer02”。</span><span class="sxs-lookup"><span data-stu-id="03428-152">Replace 'Computer02' with the name of the server instance that hosts the secondary replica.</span></span>  
  
    -   <span data-ttu-id="03428-153">用所在域的名称取代“contoso.com”；如果所有计算机都位于相同的域中，则可在该脚本中省略该域。</span><span class="sxs-lookup"><span data-stu-id="03428-153">Replace 'contoso.com' with the name of your domain, or omit it from the script if all computers are in the same domain.</span></span> <span data-ttu-id="03428-154">如果侦听器使用的是默认端口，可保留该端口号。</span><span class="sxs-lookup"><span data-stu-id="03428-154">Keep the port number if the listener is using the default port.</span></span> <span data-ttu-id="03428-155">侦听器实际使用的端口列在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]的属性页中。</span><span class="sxs-lookup"><span data-stu-id="03428-155">The port that is actually used by the listener is listed in the properties page in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="03428-156">执行脚本。</span><span class="sxs-lookup"><span data-stu-id="03428-156">Execute the script.</span></span>  
  
     <span data-ttu-id="03428-157">下一步，在使用您刚配置的组中的数据库的 Analysis Services 模型中创建数据源。</span><span class="sxs-lookup"><span data-stu-id="03428-157">Next, create a data source in an Analysis Services model that uses a database from the group you just configured.</span></span>  
  
##  <a name="create-an-analysis-services-data-source-using-an-alwayson-availability-database"></a><a name="bkmk_ssasAODB"></a><span data-ttu-id="03428-158">使用 AlwaysOn 可用性数据库创建 Analysis Services 数据源</span><span class="sxs-lookup"><span data-stu-id="03428-158">Create an Analysis Services data source using an AlwaysOn availability database</span></span>  
 <span data-ttu-id="03428-159">本节说明如何创建连接到可用性组中的数据库的 Analysis Services 数据源。</span><span class="sxs-lookup"><span data-stu-id="03428-159">This section explains how to create an Analysis Services data source that connects to a database in an availability group.</span></span> <span data-ttu-id="03428-160">您可以使用这些说明来配置与主副本（默认）的连接，或配置与基于上一节中的步骤配置的可读辅助副本的连接。</span><span class="sxs-lookup"><span data-stu-id="03428-160">You can use these instructions to configure a connection to either a primary replica (default) or a readable secondary replica that you configured based on steps in a previous section.</span></span> <span data-ttu-id="03428-161">AlwaysOn 配置设置连同在客户端中设置的连接属性将共同决定是使用主副本还是辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-161">AlwaysOn configuration settings, plus the connection properties set in the client, will determine whether a primary or secondary replica is used.</span></span>  
  
1.  <span data-ttu-id="03428-162">在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 的 Analysis Services 多维和数据挖掘模型项目中，右键单击“数据源”\*\*\*\* 并选择“新建数据源”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-162">In [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], in an Analysis Services Multidimensional and Data Mining Model project, right-click **Data Sources** and select **New Data Source**.</span></span> <span data-ttu-id="03428-163">单击 **“新建”** 创建新的数据源。</span><span class="sxs-lookup"><span data-stu-id="03428-163">Click **New** to create a new data source.</span></span>  
  
     <span data-ttu-id="03428-164">或者，对于表格模型项目，单击“模型”菜单，然后单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="03428-164">Alternatively, for a tabular model project, click the Model menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="03428-165">在连接管理器的“访问接口”中，选择支持表格格式数据流 (TDS) 协议的访问接口。</span><span class="sxs-lookup"><span data-stu-id="03428-165">In Connection Manager, in Provider, choose a provider that supports the Tabular Data Stream (TDS) protocol.</span></span> <span data-ttu-id="03428-166">SQL Server Native Client 11.0 支持此协议。</span><span class="sxs-lookup"><span data-stu-id="03428-166">The SQL Server Native Client 11.0 supports this protocol.</span></span>  
  
3.  <span data-ttu-id="03428-167">在连接管理器的“服务器名称”中，输入“可用性组侦听器” \*\* 的名称，然后选择该组中可用的数据库。</span><span class="sxs-lookup"><span data-stu-id="03428-167">In Connection Manager, in Server Name, enter the name of the *availability group listener*, and then choose a database that is available in the group.</span></span>  
  
     <span data-ttu-id="03428-168">可用性组侦听器将客户端连接重定向到主副本以处理读写请求，或重定向到辅助副本（如果在连接字符串中指定了读意向）。</span><span class="sxs-lookup"><span data-stu-id="03428-168">The availability group listener redirects a client connection to a primary replica for read-write requests or to a secondary replica if you specify read-intent in the connection string.</span></span> <span data-ttu-id="03428-169">由于副本角色将在故障转移期间改变（此时主副本将变为辅助副本，辅助副本将变为主副本），所以您应该始终指定该侦听器，这样才能相应地重定向客户端连接。</span><span class="sxs-lookup"><span data-stu-id="03428-169">Because replica roles will change during a failover (where the primary becomes the secondary and a secondary becomes a primary), you should always specify the listener so that the client connection is redirected accordingly.</span></span>  
  
     <span data-ttu-id="03428-170">要确定可用性组侦听器的名称，您可以询问数据库管理员，或连接到可用性组中的某个实例并查看其 AlwaysOn 可用性配置。</span><span class="sxs-lookup"><span data-stu-id="03428-170">To determine the name of the availability group listener, you can either ask a database administrator or connect to an instance in the availability group and view its AlwaysOn availability configuration.</span></span> <span data-ttu-id="03428-171">在下面的屏幕截图中，可用性组侦听器为 **AdventureWorks2**。</span><span class="sxs-lookup"><span data-stu-id="03428-171">In the screenshot below, the availability group listener is **AdventureWorks2**.</span></span>  
  
     <span data-ttu-id="03428-172">![Management Studio 中的 AlwaysOn 可用性文件夹](../../media/ssas-alwaysoninfoinssms.png "Management Studio 中的 AlwaysOn 可用性文件夹")</span><span class="sxs-lookup"><span data-stu-id="03428-172">![AlwaysOn Availability folder in Management Studio](../../media/ssas-alwaysoninfoinssms.png "AlwaysOn Availability folder in Management Studio")</span></span>  
  
4.  <span data-ttu-id="03428-173">还是在连接管理器中，单击左侧导航窗格中的 **“全部”** ，查看数据访问接口的属性网格。</span><span class="sxs-lookup"><span data-stu-id="03428-173">Still in Connection Manager, click **All** in the left navigation pane to view the property grid of data provider.</span></span>  
  
     <span data-ttu-id="03428-174">若要配置与次要副本的只读客户端连接，请将“应用程序意向”\*\*\*\* 设置为“READONLY”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-174">Set **Application Intent** to **READONLY** if you are configuring a read-only client connection to a secondary replica.</span></span> <span data-ttu-id="03428-175">否则，保持默认设置 **READWRITE** ，将连接重定向到主副本。</span><span class="sxs-lookup"><span data-stu-id="03428-175">Otherwise, keep the **READWRITE** default to redirect the connection to the primary replica.</span></span>  
  
5.  <span data-ttu-id="03428-176">在“模拟信息”中，选择“使用特定 Windows 用户名和密码”\*\*\*\*，然后输入对数据库至少具有 **db_datareader** 权限的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="03428-176">In Impersonation Information, select **Use a specific Windows user name and password**, and then enter a Windows domain user account that has a minimum of **db_datareader** permissions on the database.</span></span>  
  
     <span data-ttu-id="03428-177">不要选择 **“使用当前用户的凭据”** 或 **“继承”**。</span><span class="sxs-lookup"><span data-stu-id="03428-177">Do not choose **Use the credentials of the current user** or **Inherit**.</span></span> <span data-ttu-id="03428-178">您可以选择 **“使用服务帐户”**，但前提是该帐户对数据库具有读权限。</span><span class="sxs-lookup"><span data-stu-id="03428-178">You can choose **Use the service account**, but only if that account has read permissions on the database.</span></span>  
  
     <span data-ttu-id="03428-179">完成数据源设置并关闭数据源向导。</span><span class="sxs-lookup"><span data-stu-id="03428-179">Finish the data source and close the Data Source Wizard.</span></span>  
  
6.  <span data-ttu-id="03428-180">向连接字符串添加 **MultiSubnetFailover=Yes** ，以便更快地检测和连接到活动服务器。</span><span class="sxs-lookup"><span data-stu-id="03428-180">Add **MultiSubnetFailover=Yes** to the connection string to provide faster detection and connection to the active server.</span></span> <span data-ttu-id="03428-181">有关此属性的详细信息，请参阅[高可用性和灾难恢复的 SQL Server Native Client Support](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="03428-181">For more information about this property, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
     <span data-ttu-id="03428-182">此属性不显示在属性网格中。</span><span class="sxs-lookup"><span data-stu-id="03428-182">This property is not visible in the property grid.</span></span> <span data-ttu-id="03428-183">要添加该属性，请右键单击数据源并选择“查看代码”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-183">To add the property, right-click the data source and choose **View Code**.</span></span> <span data-ttu-id="03428-184">将 `MultiSubnetFailover=Yes` 添加到连接字符串。</span><span class="sxs-lookup"><span data-stu-id="03428-184">Add `MultiSubnetFailover=Yes` to the connection string.</span></span>  
  
 <span data-ttu-id="03428-185">现在已经定义了数据源。</span><span class="sxs-lookup"><span data-stu-id="03428-185">The data source is now defined.</span></span> <span data-ttu-id="03428-186">接下来可以构建模型，可以从数据源视图入手；如果是表格模型，则可以创建关系。</span><span class="sxs-lookup"><span data-stu-id="03428-186">You can now proceed to build a model, starting with the data source view, or in the case of tabular models, creating relationships.</span></span> <span data-ttu-id="03428-187">在您需要从可用性数据库中检索数据时（例如在您准备处理或部署解决方案时），您可以测试配置以验证是否从辅助副本检索数据。</span><span class="sxs-lookup"><span data-stu-id="03428-187">When you are at a point where data must be retrieved from the availability database (for example when you are ready to process or deploy the solution), you can test the configuration to verify data is accessed from the secondary replica.</span></span>  
  
##  <a name="test-the-configuration"></a><a name="bkmk_test"></a><span data-ttu-id="03428-188">测试配置</span><span class="sxs-lookup"><span data-stu-id="03428-188">Test the configuration</span></span>  
 <span data-ttu-id="03428-189">在 Analysis Services 中配置了辅助副本并创建了数据源连接后，您可以确认处理和查询命令是否重定向到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-189">After you configure the secondary replica and create a data source connection in Analysis Services, you can confirm that processing and query commands are redirected to the secondary replica.</span></span> <span data-ttu-id="03428-190">还可以执行计划的手动故障转移，以验证适用于此应用场景的恢复计划。</span><span class="sxs-lookup"><span data-stu-id="03428-190">You can also perform a planned manual failover to verify your recovery plan for this scenario.</span></span>  
  
#### <a name="step-1-confirm-the-data-source-connection-is-redirected-to-the-secondary-replica"></a><span data-ttu-id="03428-191">第 1 步：确认数据源连接重定向到辅助副本</span><span class="sxs-lookup"><span data-stu-id="03428-191">Step 1: Confirm the data source connection is redirected to the secondary replica</span></span>  
  
1.  <span data-ttu-id="03428-192">启动 SQL Server Profiler 并连接到承载辅助副本的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="03428-192">Start SQL Server Profiler and connect to the SQL Server instance hosting the secondary replica.</span></span>  
  
     <span data-ttu-id="03428-193">当跟踪运行时，`SQL:BatchStarting` 和 `SQL:BatchCompleting` 事件将显示从数据库引擎实例上执行的 Analysis Services 中发出的查询。</span><span class="sxs-lookup"><span data-stu-id="03428-193">As the trace runs, the `SQL:BatchStarting` and `SQL:BatchCompleting` events will show the queries issued from Analysis Services that are executing on the database engine instance.</span></span> <span data-ttu-id="03428-194">这些事件已默认选定，您只需启动跟踪即可。</span><span class="sxs-lookup"><span data-stu-id="03428-194">These events are selected by default so all you need to do is start the trace.</span></span>  
  
2.  <span data-ttu-id="03428-195">在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]中，打开 Analysis Services 项目或包含要测试的数据源连接的解决方案。</span><span class="sxs-lookup"><span data-stu-id="03428-195">In [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], open the Analysis Services project or solution containing a data source connection you want to test.</span></span> <span data-ttu-id="03428-196">确保数据源指定的是可用性组侦听器而不是组中的实例。</span><span class="sxs-lookup"><span data-stu-id="03428-196">Be sure that the data source specifies the availability group listener and not an instance in the group.</span></span>  
  
     <span data-ttu-id="03428-197">此步骤非常重要，</span><span class="sxs-lookup"><span data-stu-id="03428-197">This step is important.</span></span> <span data-ttu-id="03428-198">如果指定服务器实例名称，则不会路由到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-198">Routing to the secondary replica will not occur if you specify a server instance name.</span></span>  
  
3.  <span data-ttu-id="03428-199">排列应用程序窗口，使 SQL Server Profiler 和 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 并排显示。</span><span class="sxs-lookup"><span data-stu-id="03428-199">Arrange the application windows so that you can view SQL Server Profiler and [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] side by side.</span></span>  
  
4.  <span data-ttu-id="03428-200">部署该解决方案，并在部署完成后停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="03428-200">Deploy the solution, and when it completes, stop the trace.</span></span>  
  
     <span data-ttu-id="03428-201">在跟踪窗口中，您应能看到来自应用程序 **Microsoft SQL Server Analysis Services**的事件。</span><span class="sxs-lookup"><span data-stu-id="03428-201">In the trace window, you should see events from the application **Microsoft SQL Server Analysis Services**.</span></span> <span data-ttu-id="03428-202">应能看到从承载辅助副本的服务器实例上的数据库中检索数据的 `SELECT` 语句，证明是通过该侦听器连接到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-202">You should see `SELECT` statements that retrieve data from a database on the server instance that hosts the secondary replica, proving that the connection was made via the listener to the secondary replica.</span></span>  
  
#### <a name="step-2-perform-a-planned-failover-to-test-the-configuration"></a><span data-ttu-id="03428-203">第 2 步：执行计划的故障转移以测试配置</span><span class="sxs-lookup"><span data-stu-id="03428-203">Step 2: Perform a planned failover to test the configuration</span></span>  
  
1.  <span data-ttu-id="03428-204">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中，检查主副本和辅助副本，确保两个副本均配置为同步提交模式并且当前保持同步。</span><span class="sxs-lookup"><span data-stu-id="03428-204">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] check the primary and secondary replicas to ensure that both are configured for synchronous-commit mode and are currently synchronized.</span></span>  
  
     <span data-ttu-id="03428-205">以下步骤假定将辅助副本配置为同步提交。</span><span class="sxs-lookup"><span data-stu-id="03428-205">The following steps assume a secondary replica is configured for synchronous commit.</span></span>  
  
     <span data-ttu-id="03428-206">要验证同步，请打开与托管主要副本和次要副本的每个实例的连接，展开“数据库”文件夹，确保每个副本中的数据库名称旁边均附有“(已同步)”\*\*\*\* 和“(正在同步)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-206">To verify synchronization, open a connection to each instance that hosts the primary and secondary replicas, expand the Databases folder, and ensure that the database has **(Synchronized)** and **(Synchronizing)** appended to its name in each replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03428-207">这些步骤来自 [执行可用性组的计划手动故障转移 (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)，为执行此任务提供了其他信息和说明。</span><span class="sxs-lookup"><span data-stu-id="03428-207">These steps are taken from [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md), which provides additional information and alternative instructions for performing this task.</span></span>  
  
2.  <span data-ttu-id="03428-208">在 SQL Server Profiler 中，启动每个副本的跟踪并且并排查看跟踪。</span><span class="sxs-lookup"><span data-stu-id="03428-208">In SQL Server Profiler, start traces for each replica and view the traces side-by-side.</span></span> <span data-ttu-id="03428-209">在以下步骤中，您需要比较各个跟踪，确认用于从 Analysis Services 执行处理或查询的 SQL 查询从一个副本切换到另一个副本。</span><span class="sxs-lookup"><span data-stu-id="03428-209">In the following steps, you will compare traces, confirming that the SQL queries used for processing or querying from Analysis Services switch from one replica to the other.</span></span>  
  
3.  <span data-ttu-id="03428-210">从 Analysis Services 内部执行处理或查询命令。</span><span class="sxs-lookup"><span data-stu-id="03428-210">Execute a processing or query command from within Analysis Services.</span></span> <span data-ttu-id="03428-211">由于您已将数据源配置为只读连接，所以应能看到在辅助副本上执行该命令。</span><span class="sxs-lookup"><span data-stu-id="03428-211">Because you configured the data source for a read-only connection, you should see the command execute on the secondary replica.</span></span>  
  
4.  <span data-ttu-id="03428-212">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中，连接到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-212">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], connect to the secondary replica.</span></span>  
  
5.  <span data-ttu-id="03428-213">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="03428-213">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
6.  <span data-ttu-id="03428-214">右键单击要进行故障转移的可用性组，然后选择“故障转移”  命令。</span><span class="sxs-lookup"><span data-stu-id="03428-214">Right-click the availability group to be failed over, and select the **Failover** command.</span></span> <span data-ttu-id="03428-215">这将启动故障转移可用性组向导。</span><span class="sxs-lookup"><span data-stu-id="03428-215">This starts the Fail Over Availability Group Wizard.</span></span> <span data-ttu-id="03428-216">使用该向导选择要将哪一副本用作新的主副本。</span><span class="sxs-lookup"><span data-stu-id="03428-216">Use the wizard to choose which replica to make the new primary replica.</span></span>  
  
7.  <span data-ttu-id="03428-217">确认故障转移已成功：</span><span class="sxs-lookup"><span data-stu-id="03428-217">Confirm that failover succeeded:</span></span>  
  
    -   <span data-ttu-id="03428-218">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中，展开可用性组以查看所指定的主副本和辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-218">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], expand the availability groups to view the (primary) and (secondary) designations.</span></span> <span data-ttu-id="03428-219">以前充当主副本的实例现在应该变为辅助副本。</span><span class="sxs-lookup"><span data-stu-id="03428-219">The instance that was previously a primary replica should now be a secondary replica.</span></span>  
  
    -   <span data-ttu-id="03428-220">查看面板，确定是否检测到任何运行状况问题。</span><span class="sxs-lookup"><span data-stu-id="03428-220">View the dashboard to determine if any health issues were detected.</span></span> <span data-ttu-id="03428-221">右键单击该可用性组，然后选择 "**显示仪表板**"。</span><span class="sxs-lookup"><span data-stu-id="03428-221">Right-click the availability group and select **Show Dashboard**.</span></span>  
  
8.  <span data-ttu-id="03428-222">花一两分钟的时间等待故障转移在后端完成。</span><span class="sxs-lookup"><span data-stu-id="03428-222">Wait one or two minutes for the failover to complete on the backend.</span></span>  
  
9. <span data-ttu-id="03428-223">在 Analysis Services 解决方案中重复处理或查询命令，然后在 SQL Server Profiler 中并排观察跟踪状况。</span><span class="sxs-lookup"><span data-stu-id="03428-223">Repeat the processing or query command in the Analysis Services solution, and then watch the traces side by side in SQL Server Profiler.</span></span> <span data-ttu-id="03428-224">您应能发现在另一个实例（即现在的新辅助副本）上执行处理的证据。</span><span class="sxs-lookup"><span data-stu-id="03428-224">You should see evidence of processing on the other instance, which is now the new secondary replica.</span></span>  
  
##  <a name="what-happens-after-a-failover-occurs"></a><a name="bkmk_whathappens"></a><span data-ttu-id="03428-225">发生故障转移后的情况</span><span class="sxs-lookup"><span data-stu-id="03428-225">What happens after a failover occurs</span></span>  
 <span data-ttu-id="03428-226">在故障转移期间，辅助副本转换为主角色，以前的主副本转换为辅助角色。</span><span class="sxs-lookup"><span data-stu-id="03428-226">During a failover, a secondary replica transitions to the primary role and the former primary replica transitions to the secondary role.</span></span> <span data-ttu-id="03428-227">所有客户端连接都已终止，可用性组侦听器的所有权随主副本角色移至新的 SQL Server 实例，并且该侦听器终结点绑定到新实例的虚拟 IP 地址和 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="03428-227">All client connections are terminated, ownership of the availability group listener moves with the primary replica role to a new SQL Server instance, and the listener endpoint is bound to the new instance's virtual IP addresses and TCP ports.</span></span> <span data-ttu-id="03428-228">有关详细信息，请参阅本主题后面的 [关于对可用性副本的客户端连接访问 (SQL Server)](about-client-connection-access-to-availability-replicas-sql-server.md)之类的系统数据库。</span><span class="sxs-lookup"><span data-stu-id="03428-228">For more information, see [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md).</span></span>  
  
 <span data-ttu-id="03428-229">如果执行过程中出现故障转移，Analysis Services 中会出现以下错误并显示在日志文件或输出窗口中：“OLE DB 错误: OLE DB 或 ODBC 错误通讯链接失败; 08S01; TPC 提供程序: 现有连接已被远程主机强行关闭。</span><span class="sxs-lookup"><span data-stu-id="03428-229">If failover occurs during processing, the following error occurs in Analysis Services in the log file or output window: "OLE DB error: OLE DB or ODBC error: Communication link failure; 08S01; TPC Provider: An existing connection was forcibly closed by the remote host.</span></span> <span data-ttu-id="03428-230">; 08S01。”</span><span class="sxs-lookup"><span data-stu-id="03428-230">; 08S01."</span></span>  
  
 <span data-ttu-id="03428-231">稍等片刻然后重试，该错误应自行解决。</span><span class="sxs-lookup"><span data-stu-id="03428-231">This error should resolve if you wait a minute and try again.</span></span> <span data-ttu-id="03428-232">如果为可读辅助副本正确配置了可用性组，那么在您重试处理后，处理将在新的辅助副本上继续执行。</span><span class="sxs-lookup"><span data-stu-id="03428-232">If the availability group is configured correctly for readable secondary replica, processing will resume on the new secondary replica when you retry processing.</span></span>  
  
 <span data-ttu-id="03428-233">若错误反复出现，则很可能是因为配置有误。</span><span class="sxs-lookup"><span data-stu-id="03428-233">Persistent errors are most likely due to a configuration problem.</span></span> <span data-ttu-id="03428-234">您可以尝试重新运行 T-SQL 脚本，以解决辅助副本上可能存在的路由列表、只读路由 URL 和读意向问题。</span><span class="sxs-lookup"><span data-stu-id="03428-234">You can try re-running the T-SQL script to resolve problems with the routing list, read-only routing URLs, and read-intent on the secondary replica.</span></span> <span data-ttu-id="03428-235">还应该确认主副本允许所有连接。</span><span class="sxs-lookup"><span data-stu-id="03428-235">You should also verify that the primary replica allows all connections.</span></span>  
  
##  <a name="writeback-when-using-an-alwayson-availability-database"></a><a name="bkmk_writeback"></a><span data-ttu-id="03428-236">使用 AlwaysOn 可用性数据库时的写回</span><span class="sxs-lookup"><span data-stu-id="03428-236">Writeback when using an AlwaysOn availability database</span></span>  
 <span data-ttu-id="03428-237">写回是 Analysis Services 中用来支持 Excel 中的假设分析的一项功能。</span><span class="sxs-lookup"><span data-stu-id="03428-237">Writeback is an Analysis Services feature that supports What If analysis in Excel.</span></span> <span data-ttu-id="03428-238">该功能还常用于自定义应用程序中的预算和预测任务。</span><span class="sxs-lookup"><span data-stu-id="03428-238">It is also commonly used for budgeting and forecasting tasks in custom applications.</span></span>  
  
 <span data-ttu-id="03428-239">要支持写回功能，需要 READWRITE 客户端连接。</span><span class="sxs-lookup"><span data-stu-id="03428-239">Support for writeback requires a READWRITE client connection.</span></span> <span data-ttu-id="03428-240">在 Excel 中，如果在只读连接上尝试写回，将出现以下错误：“无法从外部数据源检索数据。”</span><span class="sxs-lookup"><span data-stu-id="03428-240">In Excel, if you attempt to write back on a read-only connection, the following error will occur: "Data could not be retrieved from the external data source."</span></span> <span data-ttu-id="03428-241">“无法从外部数据源检索数据。”</span><span class="sxs-lookup"><span data-stu-id="03428-241">"Data could not be retrieved from the external data source."</span></span>  
  
 <span data-ttu-id="03428-242">如果配置某个连接始终访问只读辅助副本，您现在必须配置一个使用 READWRITE 连接访问主副本的新连接。</span><span class="sxs-lookup"><span data-stu-id="03428-242">If you configured a connection to always access a readable secondary replica, you must now configure a new connection that uses a READWRITE connection to the primary replica.</span></span>  
  
 <span data-ttu-id="03428-243">为此，应该在 Analysis Services 模型中另外创建一个数据源，以便支持读写连接。</span><span class="sxs-lookup"><span data-stu-id="03428-243">To do this, create an additional data source in an Analysis Services model to support the read-write connection.</span></span> <span data-ttu-id="03428-244">创建另一个数据源时，请使用你在只读连接中指定的相同的侦听器名称和数据库，但应保留支持 READWRITE 连接的默认设置，而不要修改“应用程序意向”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03428-244">When creating the additional data source, use the same listener name and database that you specified in the read-only connection, but instead of modifying **Application Intent**, keep the default that supports READWRITE connections.</span></span> <span data-ttu-id="03428-245">您现在可以向基于读写数据源的数据源视图添加新的事实表或维度表，然后针对新表启用写回功能。</span><span class="sxs-lookup"><span data-stu-id="03428-245">You can now add new fact or dimension tables to your data source view that are based on the read-write data source, and then enable writeback on the new tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03428-246">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03428-246">See Also</span></span>  
 <span data-ttu-id="03428-247">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="03428-247">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="03428-248">[活动辅助副本：可读辅助副本 &#40;AlwaysOn 可用性组&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="03428-248">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="03428-249">[AlwaysOn 可用性组 &#40;SQL Server 的操作问题的 AlwaysOn 策略&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="03428-249">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="03428-250">[&#40;SSAS 多维&#41;创建数据源](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="03428-250">[Create a Data Source &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span></span>  
 [<span data-ttu-id="03428-251">“启用维度写回”</span><span class="sxs-lookup"><span data-stu-id="03428-251">Enable Dimension Writeback</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/bi-wizard-enable-dimension-writeback)  
  
  
