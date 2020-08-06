---
title: 使用 Windows 身份验证建立数据库镜像会话 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 143c68a5-589f-4e7f-be59-02707e1a430a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3088333fbfd4babd209df07f8880c838ce626d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578422"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-transact-sql"></a><span data-ttu-id="f653a-102">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f653a-102">Establish a Database Mirroring Session Using Windows Authentication (Transact-SQL)</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="f653a-103">改为使用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f653a-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="f653a-104">准备好镜像数据库后（请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)），便可以建立数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="f653a-104">After the mirror database is prepared (see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)), you can establish a database mirroring session.</span></span> <span data-ttu-id="f653a-105">主体服务器实例、镜像服务器实例和见证服务器实例都必须是单独的服务器实例，并位于单独的主机系统中。</span><span class="sxs-lookup"><span data-stu-id="f653a-105">The principal, mirror, and witness server instances must be separate server instances, which should be on separate host systems.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f653a-106">我们建议您在非高峰时段配置数据库镜像，因为配置镜像会影响性能。</span><span class="sxs-lookup"><span data-stu-id="f653a-106">We recommend that you configure database mirroring during off-peak hours because configuring mirroring can impact performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f653a-107">给定的服务器实例可以参与到多个具有相同或不同伙伴的并发数据库镜像会话中。</span><span class="sxs-lookup"><span data-stu-id="f653a-107">A given server instance can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="f653a-108">某个服务器实例可能在某些会话中是伙伴，而在其他会话中则是见证服务器。</span><span class="sxs-lookup"><span data-stu-id="f653a-108">A server instance can be a partner in some sessions and a witness in other sessions.</span></span> <span data-ttu-id="f653a-109">镜像服务器实例必须与主体服务器实例运行相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f653a-109">The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the principal server instance.</span></span> <span data-ttu-id="f653a-110">并非 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].的每个版本都提供数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="f653a-110">Database mirroring is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f653a-111">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="f653a-112">此外，极力建议这些服务器实例在可以处理相同工作负荷的类似系统上运行。</span><span class="sxs-lookup"><span data-stu-id="f653a-112">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
### <a name="to-establish-a-database-mirroring-session"></a><span data-ttu-id="f653a-113">建立数据库镜像会话</span><span class="sxs-lookup"><span data-stu-id="f653a-113">To establish a database mirroring session</span></span>  
  
1.  <span data-ttu-id="f653a-114">创建镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="f653a-114">Create the mirror database.</span></span> <span data-ttu-id="f653a-115">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f653a-115">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="f653a-116">在每个服务器实例上设置安全性。</span><span class="sxs-lookup"><span data-stu-id="f653a-116">Set up security on each server instance.</span></span>  
  
     <span data-ttu-id="f653a-117">数据库镜像会话中的每个服务器实例都需要一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f653a-117">Each server instance in a database mirroring session requires a database mirroring endpoint.</span></span> <span data-ttu-id="f653a-118">如果端点不存在，则必须先创建。</span><span class="sxs-lookup"><span data-stu-id="f653a-118">If the endpoint does not exist, you must create it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f653a-119">服务器实例对数据库镜像使用的验证形式是其数据库镜像端点的一种属性。</span><span class="sxs-lookup"><span data-stu-id="f653a-119">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="f653a-120">两种类型的传输安全性可用于数据库镜像：Windows 身份验证或基于证书的身份验证。</span><span class="sxs-lookup"><span data-stu-id="f653a-120">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="f653a-121">有关详细信息，请参阅[数据库镜像的传输安全性和 AlwaysOn 可用性组 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-121">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="f653a-122">在每台主体服务器和镜像服务器上，请确保存在用于数据库镜像的端点。</span><span class="sxs-lookup"><span data-stu-id="f653a-122">On each partner server, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="f653a-123">无论支持的镜像会话数是多少，服务器实例都只能有一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f653a-123">Regardless of the number of mirroring sessions to be supported, the server instance can have only one database mirroring endpoint.</span></span> <span data-ttu-id="f653a-124">如果只将该服务器实例用于数据库镜像会话中的伙伴，你可以为终结点分配伙伴角色 (ROLE **=** PARTNER)。</span><span class="sxs-lookup"><span data-stu-id="f653a-124">If you intend to use this server instance exclusively for partners in database mirroring sessions, you can assign the role of partner to the endpoint (ROLE**=** PARTNER).</span></span> <span data-ttu-id="f653a-125">如果还要将该服务器用于其他数据库镜像会话中的见证服务器，则请将端点的角色分配为 ALL。</span><span class="sxs-lookup"><span data-stu-id="f653a-125">If you intend also to use this server for the witness in other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="f653a-126">若要执行 SET PARTNER 语句，必须将两个合作伙伴的端点的 STATE 都设置为 STARTED。</span><span class="sxs-lookup"><span data-stu-id="f653a-126">To execute a SET PARTNER statement, the STATE of the endpoints of both partners must be set to STARTED.</span></span>  
  
     <span data-ttu-id="f653a-127">若要了解服务器实例是否具有数据库镜像端点并了解其角色和状态，请对该实例使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="f653a-127">To learn whether a server instance has a database mirroring endpoint and to learn its role and state, on that instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f653a-128">请勿重新配置正在使用的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f653a-128">Do not reconfigure an in-use database mirroring endpoint.</span></span> <span data-ttu-id="f653a-129">如果数据库镜像端点已存在并处于使用状态，则我们建议您将此端点用于服务器实例中的每一个会话。</span><span class="sxs-lookup"><span data-stu-id="f653a-129">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="f653a-130">删除正在使用的端点可导致端点重新启动，中断现有会话的连接，从而导致其他服务器实例出现错误。</span><span class="sxs-lookup"><span data-stu-id="f653a-130">Dropping an in-use endpoint can cause the endpoint to restart, disrupting the connections of the existing sessions, which can appear to be an error to the other server instances.</span></span> <span data-ttu-id="f653a-131">这在具有自动故障转移功能的高安全性模式下尤为重要，在此模式下，在伙伴上重新配置端点可能会导致故障转移。</span><span class="sxs-lookup"><span data-stu-id="f653a-131">This is particularly important in high-safety mode with automatic failover, in which reconfiguring the endpoint on a partner could cause a failover to occur.</span></span> <span data-ttu-id="f653a-132">此外，如果已经为会话设置了见证服务器，则删除数据库镜像端点会造成该会话的主体服务器失去仲裁；如果发生这种情况，数据库会进入脱机状态，其用户也会断开连接。</span><span class="sxs-lookup"><span data-stu-id="f653a-132">Also, if a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="f653a-133">有关详细信息，请参阅[仲裁：见证服务器如何影响数据库可用性（数据库镜像）](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-133">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="f653a-134">如果任一伙伴缺少终结点，请参阅[为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-134">If either partner lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
3.  <span data-ttu-id="f653a-135">如果服务器实例使用不同的域用户帐户运行，则每个实例还需要在其他实例的 **master** 数据库中具有登录名。</span><span class="sxs-lookup"><span data-stu-id="f653a-135">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="f653a-136">如果登录名不存在，则必须先创建。</span><span class="sxs-lookup"><span data-stu-id="f653a-136">If the login does not exist, you must create it.</span></span> <span data-ttu-id="f653a-137">有关详细信息，请参阅 [允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-137">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
4.  <span data-ttu-id="f653a-138">若要将主体服务器设置为镜像数据库中的伙伴，请连接到镜像服务器，然后执行下面的语句：</span><span class="sxs-lookup"><span data-stu-id="f653a-138">To set the principal server as partner on the mirror database, connect to the mirror server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="f653a-139">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="f653a-139">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="f653a-140">其中，*<database_name>* 是要镜像的数据库的名称（此名称在两个伙伴上相同），*<server_network_address>* 是主体服务器的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="f653a-140">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the principal server.</span></span>  
  
     <span data-ttu-id="f653a-141">服务器网络地址的语法如下：</span><span class="sxs-lookup"><span data-stu-id="f653a-141">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="f653a-142">TCP：<strong>//</strong> \<*system-address> \*<strong>：</strong> \<*port> \*</span><span class="sxs-lookup"><span data-stu-id="f653a-142">TCP<strong>://</strong>\<*system-address>*<strong>:</strong>\<*port>*</span></span>  
  
     <span data-ttu-id="f653a-143">其中，\<*system-address>\* 是明确标识目标计算机系统的字符串，\<*port>\* 是合作服务器实例的镜像终结点使用的端口号。</span><span class="sxs-lookup"><span data-stu-id="f653a-143">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="f653a-144">有关详细信息，请参阅 [指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-144">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="f653a-145">例如，在镜像服务器实例中，下面的 ALTER DATABASE 语句将伙伴设置为原始主体服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f653a-145">For example, on the mirror server instance, the following ALTER DATABASE statement sets the partner as the original principal server instance.</span></span> <span data-ttu-id="f653a-146">数据库名称为“AdventureWorks”，系统地址为 DBSERVER1（伙伴系统的名称），伙伴数据库镜像终结点使用的端口为 7022：</span><span class="sxs-lookup"><span data-stu-id="f653a-146">The database name is **AdventureWorks**, the system address is DBSERVER1-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7022:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
       SET PARTNER = 'TCP://DBSERVER1:7022'  
    ```  
  
     <span data-ttu-id="f653a-147">与主体服务器连接时，此语句将准备镜像服务器来形成会话。</span><span class="sxs-lookup"><span data-stu-id="f653a-147">This statement prepares the mirror server to form a session when it is contacted by the principal server.</span></span>  
  
5.  <span data-ttu-id="f653a-148">若要将镜像服务器设置为主体数据库中的伙伴，请连接到主体服务器，然后执行下面的语句：</span><span class="sxs-lookup"><span data-stu-id="f653a-148">To set the mirror server as partner on the principal database, connect to the principal server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="f653a-149">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="f653a-149">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="f653a-150">有关详细信息，请参阅步骤 4。</span><span class="sxs-lookup"><span data-stu-id="f653a-150">For more information, see step 4.</span></span>  
  
     <span data-ttu-id="f653a-151">例如，在主体服务器实例中，下面的 ALTER DATABASE 语句将伙伴设置为原始镜像服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f653a-151">For example, on the principal server instance, the following ALTER DATABASE statement sets the partner as the original mirror server instance.</span></span> <span data-ttu-id="f653a-152">数据库名称为“AdventureWorks”，系统地址为 DBSERVER2（伙伴系统的名称），伙伴数据库镜像终结点使用的端口为 7025：</span><span class="sxs-lookup"><span data-stu-id="f653a-152">The database name is **AdventureWorks**, the system address is DBSERVER2-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7025:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks SET PARTNER = 'TCP://DBSERVER2:7022'  
    ```  
  
     <span data-ttu-id="f653a-153">在主体服务器上输入此语句将启动数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="f653a-153">Entering this statement on the principal server begins the database mirroring session.</span></span>  
  
6.  <span data-ttu-id="f653a-154">默认情况下，会话设置为完整事务安全（SAFETY 设置为 FULL），此设置会在同步、不带自动故障转移功能的高安全性模式下启动会话。</span><span class="sxs-lookup"><span data-stu-id="f653a-154">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="f653a-155">您可以将会话重新配置为在具有自动故障转移功能的高安全性模式下运行，或者在异步、高性能模式下运行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f653a-155">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="f653a-156">**具有自动故障转移的高安全性模式**</span><span class="sxs-lookup"><span data-stu-id="f653a-156">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="f653a-157">如果希望高安全性模式会话支持自动故障转移，则请添加见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f653a-157">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span> <span data-ttu-id="f653a-158">有关详细信息，请参阅[使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-158">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
    -   <span data-ttu-id="f653a-159">**高性能模式**</span><span class="sxs-lookup"><span data-stu-id="f653a-159">**High-performance mode**</span></span>  
  
         <span data-ttu-id="f653a-160">另外，如果您不想进行自动故障转移，并且您对性能的追求超过了可用性，则请关闭事务安全。</span><span class="sxs-lookup"><span data-stu-id="f653a-160">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="f653a-161">有关详细信息，请参阅[更改数据库镜像会话中的事务安全 (Transact-SQL)](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-161">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f653a-162">在高性能模式下，WITNESS 应设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="f653a-162">In high-performance mode, WITNESS should be set to OFF.</span></span> <span data-ttu-id="f653a-163">有关详细信息，请参阅[仲裁：见证服务器如何影响数据库可用性（数据库镜像）](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-163">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f653a-164">示例</span><span class="sxs-lookup"><span data-stu-id="f653a-164">Example</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f653a-165">下面的示例针对现有的镜像数据库在伙伴间建立了数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="f653a-165">The following example establishes a database mirroring session between partners for an existing mirror database.</span></span> <span data-ttu-id="f653a-166">有关创建镜像数据库的详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-166">For information on creating a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)=.</span></span>  
  
 <span data-ttu-id="f653a-167">该示例显示了创建没有见证服务器的数据库镜像会话的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="f653a-167">The example shows the basic steps for creating a database mirroring session without a witness.</span></span> <span data-ttu-id="f653a-168">这两个伙伴是两个计算机系统（PARTNERHOST1 和 PARTNERHOST5）中的默认服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f653a-168">The two partners are the default server instances on two computer systems (PARTNERHOST1 and PARTNERHOST5).</span></span> <span data-ttu-id="f653a-169">这两个伙伴实例运行相同的 Windows 域用户帐户 (MYDOMAIN\dbousername)。</span><span class="sxs-lookup"><span data-stu-id="f653a-169">The two partner instances run the same Windows domain user account (MYDOMAIN\dbousername).</span></span>  
  
1.  <span data-ttu-id="f653a-170">在主体服务器实例（PARTNERHOST1 中的默认实例）中，创建支持所有使用端口 7022 的角色的端点：</span><span class="sxs-lookup"><span data-stu-id="f653a-170">On the principal server instance (default instance on PARTNERHOST1), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="f653a-171">有关如何设置登录名的示例，请参阅 [允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md).的每个版本都提供数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="f653a-171">For an example of how to setup a login, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
2.  <span data-ttu-id="f653a-172">在镜像服务器实例（PARTNERHOST5 中的默认实例）中，创建支持所有使用端口 7022 的角色的端点：</span><span class="sxs-lookup"><span data-stu-id="f653a-172">On the mirror server instance (default instance on PARTNERHOST5), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
3.  <span data-ttu-id="f653a-173">在主体服务器实例（位于 PARTNERHOST1）中，备份数据库：</span><span class="sxs-lookup"><span data-stu-id="f653a-173">On the principal server instance (on PARTNERHOST1), back up the database:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdvWorks_dbmirror.bak'   
        WITH FORMAT  
    GO  
    ```  
  
4.  <span data-ttu-id="f653a-174">在镜像服务器实例（位于 `PARTNERHOST5`）中还原数据库：</span><span class="sxs-lookup"><span data-stu-id="f653a-174">On the mirror server instance (on `PARTNERHOST5`), restore the database:</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks   
        FROM DISK = 'Z:\AdvWorks_dbmirror.bak'   
        WITH NORECOVERY  
    GO  
    ```  
  
5.  <span data-ttu-id="f653a-175">创建数据库的完整备份之后，必须在主体数据库中创建日志备份。</span><span class="sxs-lookup"><span data-stu-id="f653a-175">After you create the full database backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="f653a-176">例如，下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将日志备份到先前数据库备份所使用的同一个文件中：</span><span class="sxs-lookup"><span data-stu-id="f653a-176">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding database backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="f653a-177">在开始镜像之前，必须应用必要的日志备份（以及所有后续日志备份）。</span><span class="sxs-lookup"><span data-stu-id="f653a-177">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="f653a-178">例如，以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句还原 C:\AdventureWorks.bak 中的第一个日志：</span><span class="sxs-lookup"><span data-stu-id="f653a-178">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from C:\AdventureWorks.bak:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\ AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="f653a-179">在镜像服务器实例中，将 PARTNERHOST1 中的服务器实例设置为伙伴（使它成为初始主体服务器）：</span><span class="sxs-lookup"><span data-stu-id="f653a-179">On the mirror server instance, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1:7022'  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f653a-180">默认情况下，数据库镜像会话在同步模式下运行，这是由于将会话设置为完整事务安全（SAFETY 设置为 FULL）。</span><span class="sxs-lookup"><span data-stu-id="f653a-180">default, a database mirroring session runs in synchronous mode, which depends on having full transaction safety (SAFETY is set to FULL).</span></span> <span data-ttu-id="f653a-181">若要使会话在异步、高性能模式下运行，请将 SAFETY 设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="f653a-181">To cause a session to run in asynchronous, high-performance mode, set SAFETY to OFF.</span></span> <span data-ttu-id="f653a-182">有关详细信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-182">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
8.  <span data-ttu-id="f653a-183">在主体服务器实例上，将 `PARTNERHOST5` 上的服务器实例设置为伙伴（使其成为初始镜像服务器）：</span><span class="sxs-lookup"><span data-stu-id="f653a-183">On the principal server instance, set the server instance on `PARTNERHOST5` as the partner (making it the initial mirror server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5:7022'  
    GO  
    ```  
  
9. <span data-ttu-id="f653a-184">或者，如果想使用具有自动故障转移功能的高安全性模式，则请设置见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f653a-184">Optionally, if you intend to use high-safety mode with automatic failover, set up the witness server instance.</span></span> <span data-ttu-id="f653a-185">有关详细信息，请参阅[使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-185">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f653a-186">有关显示安全设置、准备镜像数据库、设置伙伴以及添加见证服务器的完整示例的信息，请参阅[设置数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f653a-186">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f653a-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f653a-187">See Also</span></span>  
 <span data-ttu-id="f653a-188">[设置数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-188">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f653a-189">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f653a-189">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="f653a-190">[允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-190">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="f653a-191">[为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-191">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f653a-192">[为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-192">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="f653a-193">[数据库镜像和日志传送 (SQL Server)](database-mirroring-and-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-193">[Database Mirroring and Log Shipping &#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="f653a-194">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-194">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f653a-195">[数据库镜像和复制 (SQL Server)](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-195">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="f653a-196">[设置数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-196">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f653a-197">[指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="f653a-197">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 [<span data-ttu-id="f653a-198">数据库镜像运行模式</span><span class="sxs-lookup"><span data-stu-id="f653a-198">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
