---
title: 使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- Windows authentication [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: bf5e87df-91a4-49f9-ae88-2a6dcf644510
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 88684c3a1ca12ea579859759ed804ca281647fa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579782"
---
# <a name="add-a-database-mirroring-witness-using-windows-authentication-transact-sql"></a><span data-ttu-id="17117-102">使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="17117-102">Add a Database Mirroring Witness Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="17117-103">为了给数据库设置见证服务器，数据库所有者为见证服务器的角色分配数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="17117-103">To set up a witness for a database, the database owner assigns a Database Engine instance to the role of witness server.</span></span> <span data-ttu-id="17117-104">见证服务器实例可以与主体服务器实例或镜像服务器实例运行于同一台计算机上，但这样会明显降低自动故障转移的可靠性。</span><span class="sxs-lookup"><span data-stu-id="17117-104">The witness server instance can run on the same computer as the principal or mirror server instance, but this substantially reduces the robustness of automatic failover.</span></span>  
  
 <span data-ttu-id="17117-105">极力建议见证服务器应位于另外一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="17117-105">We strongly recommend that the witness reside on a separate computer.</span></span> <span data-ttu-id="17117-106">给定的服务器可以参与到多个具有相同或不同伙伴的并发数据库镜像会话中。</span><span class="sxs-lookup"><span data-stu-id="17117-106">A given server can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="17117-107">给定的服务器在某些会话中可能是伙伴，而在其他会话中则是见证服务器。</span><span class="sxs-lookup"><span data-stu-id="17117-107">A given server can be a partner in some sessions and a witness in other sessions.</span></span>  
  
 <span data-ttu-id="17117-108">见证服务器专用于具有自动故障转移功能的高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="17117-108">The witness is intended exclusively for high-safety mode with automatic failover.</span></span> <span data-ttu-id="17117-109">在设置见证服务器之前，极力建议确保 SAFETY 属性当前设置为 FULL。</span><span class="sxs-lookup"><span data-stu-id="17117-109">Before you set a witness, we strongly recommend that you ensure that the SAFETY property is currently set to FULL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17117-110">我们建议您在非高峰时段配置数据库镜像，因为配置会影响性能。</span><span class="sxs-lookup"><span data-stu-id="17117-110">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
### <a name="to-establish-a-witness"></a><span data-ttu-id="17117-111">建立见证服务器</span><span class="sxs-lookup"><span data-stu-id="17117-111">To establish a witness</span></span>  
  
1.  <span data-ttu-id="17117-112">在见证服务器实例上，请确保存在用于数据库镜像的端点。</span><span class="sxs-lookup"><span data-stu-id="17117-112">On the witness server instance, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="17117-113">无论支持的镜像会话数是多少，服务器实例都只能有一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="17117-113">Regardless of the number of mirroring session to be supported, the server instance must have only one database mirroring endpoint.</span></span> <span data-ttu-id="17117-114">如果打算在数据库镜像会话中以独占方式将此服务器实例用作见证服务器，请将见证服务器的角色分配到 (角色见证) 的终结点 **=** 。</span><span class="sxs-lookup"><span data-stu-id="17117-114">If you intend to use this server instance exclusively as a witness in database mirroring sessions, assign the role of witness to the endpoint (ROLE **=** WITNESS).</span></span> <span data-ttu-id="17117-115">如果要将该服务器实例用于其他数据库镜像会话中的伙伴，请将端点的角色分配为 ALL。</span><span class="sxs-lookup"><span data-stu-id="17117-115">If you intend to use this server instance as a partner in one or more other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="17117-116">若要执行 SET WITNESS 语句，数据库镜像会话必须已启动（在伙伴之间），并且见证服务器端点的 STATE 必须设置为 STARTED。</span><span class="sxs-lookup"><span data-stu-id="17117-116">To execute a SET WITNESS statement, the database mirroring session must already be started (between the partners), and the STATE of the endpoint of the witness must be set to STARTED.</span></span>  
  
     <span data-ttu-id="17117-117">若要了解见证服务器实例是否具有其数据库镜像端点并了解其角色和状态，请针对该实例使用以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="17117-117">To learn whether the witness server instance has its database mirroring endpoint and to learn its role and state, on that instance, use the following Transact-SQL statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="17117-118">如果数据库镜像端点已存在并处于使用状态，则我们建议您将此端点用于服务器实例中的每一个会话。</span><span class="sxs-lookup"><span data-stu-id="17117-118">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="17117-119">删除正在使用的端点会中断现有会话的连接。</span><span class="sxs-lookup"><span data-stu-id="17117-119">Dropping an in-use endpoint disrupts the connections of the existing sessions.</span></span> <span data-ttu-id="17117-120">如果已经为会话设置了见证服务器，则删除数据库镜像端点会造成该会话的主体服务器失去仲裁；如果发生这种情况，数据库会进入脱机状态，其用户也会断开连接。</span><span class="sxs-lookup"><span data-stu-id="17117-120">If a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="17117-121">有关详细信息，请参阅[仲裁：见证服务器如何影响数据库可用性（数据库镜像）](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="17117-121">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="17117-122">如果见证服务器缺少终结点，请参阅[为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="17117-122">If the witness lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="17117-123">如果使用不同的域用户帐户运行伙伴实例，请在每个实例的 master 数据库中为不同帐户创建登录名。</span><span class="sxs-lookup"><span data-stu-id="17117-123">If the partner instances are running under different domain user accounts, create a login for the different accounts in the master database of each instance.</span></span> <span data-ttu-id="17117-124">有关详细信息，请参阅 [允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="17117-124">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="17117-125">连接到主体服务器并执行下面的语句：</span><span class="sxs-lookup"><span data-stu-id="17117-125">Connect to the principal server and issue the following statement:</span></span>  
  
     <span data-ttu-id="17117-126">更改数据库 *<database_name>* 集见证 **=** _<server_network_address_></span><span class="sxs-lookup"><span data-stu-id="17117-126">ALTER DATABASE *<database_name>* SET WITNESS **=** _<server_network_address>_</span></span>  
  
     <span data-ttu-id="17117-127">其中，<database_name> 是要镜像的数据库的名称（此名称在两个伙伴上相同），<server_network_address> 是见证服务器实例的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="17117-127">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the witness server instance.</span></span>  
  
     <span data-ttu-id="17117-128">服务器网络地址的语法如下：</span><span class="sxs-lookup"><span data-stu-id="17117-128">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="17117-129">TCP：**//** \<_system-address> _**：**\<*port>\*</span><span class="sxs-lookup"><span data-stu-id="17117-129">TCP **://**\<_system-address>_**:**\<*port>\*</span></span>  
  
     <span data-ttu-id="17117-130">其中，\<*system-address>\* 是明确标识目标计算机系统的字符串，\<*port>\* 是合作服务器实例的镜像终结点使用的端口号。</span><span class="sxs-lookup"><span data-stu-id="17117-130">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="17117-131">有关详细信息，请参阅 [指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="17117-131">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="17117-132">例如，在主体服务器实例上，下面的 ALTER DATABASE 语句设置见证服务器。</span><span class="sxs-lookup"><span data-stu-id="17117-132">For example, on the principal server instance, the following ALTER DATABASE statement sets the witness.</span></span> <span data-ttu-id="17117-133">数据库名称为“AdventureWorks”，系统地址为 DBSERVER3（见证服务器系统的名称），见证服务器的数据库镜像终结点使用的端口为 `7022`：</span><span class="sxs-lookup"><span data-stu-id="17117-133">The database name is **AdventureWorks**, the system address is DBSERVER3-the name of the witness system, and the port used by the database mirroring endpoint of the witness is `7022`:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
      SET WITNESS = 'TCP://DBSERVER3:7022'  
    ```  
  
## <a name="example"></a><span data-ttu-id="17117-134">示例</span><span class="sxs-lookup"><span data-stu-id="17117-134">Example</span></span>  
 <span data-ttu-id="17117-135">下面的示例将建立一个数据镜像见证服务器。</span><span class="sxs-lookup"><span data-stu-id="17117-135">The following example establishes a data mirroring witness.</span></span> <span data-ttu-id="17117-136">在见证服务器实例（ `WITNESSHOST4`上的默认实例）上：</span><span class="sxs-lookup"><span data-stu-id="17117-136">On the witness server instance (default instance on `WITNESSHOST4`):</span></span>  
  
1.  <span data-ttu-id="17117-137">为仅使用端口 `7022`的 WITNESS 角色创建此服务器实例的一个端点。</span><span class="sxs-lookup"><span data-stu-id="17117-137">Create an endpoint for this server instance for the WITNESS role only using port `7022`.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    ```  
  
2.  <span data-ttu-id="17117-138">如果伙伴实例与见证服务器实例的域用户帐户不同，则为伙伴实例的域用户帐户创建一个登录名；例如，假定见证服务器作为 `SOMEDOMAIN\witnessuser`运行，而伙伴作为 `MYDOMAIN\dbousername`运行。</span><span class="sxs-lookup"><span data-stu-id="17117-138">Create a login for domain user account of partner instances, if different; for example, assume that the witness is running as `SOMEDOMAIN\witnessuser`, but the partners are running as `MYDOMAIN\dbousername`.</span></span> <span data-ttu-id="17117-139">为伙伴创建登录名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="17117-139">Create a login for the partners, as follows:</span></span>  
  
    ```  
    --Create a login for the partner server instances,  
    --which are both running as MYDOMAIN\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [MYDOMAIN\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [MYDOMAIN\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="17117-140">在每个伙伴服务器实例上，为见证服务器实例创建登录名：</span><span class="sxs-lookup"><span data-stu-id="17117-140">On each of the partner server instances, create a login for the witness server instance:</span></span>  
  
    ```  
    --Create a login for the witness server instance,  
    --which is running as SOMEDOMAIN\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [SOMEDOMAIN\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [SOMEDOMAIN\witnessuser];  
    GO  
    ```  
  
4.  <span data-ttu-id="17117-141">在主体服务器上，设置见证服务器（位于 `WITNESSHOST4`上）：</span><span class="sxs-lookup"><span data-stu-id="17117-141">On the principal server, set the witness (which is on `WITNESSHOST4`):</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4:7022'  
    GO  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="17117-142">服务器网络地址通过端口号来指示目标服务器实例，端口号映射到该实例的镜像端点。</span><span class="sxs-lookup"><span data-stu-id="17117-142">The server network address indicates the target server instance by the port number, which maps to the mirroring endpoint of the instance.</span></span>  
  
 <span data-ttu-id="17117-143">有关显示安全设置、准备镜像数据库、设置伙伴以及添加见证服务器的完整示例的信息，请参阅[设置数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="17117-143">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17117-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17117-144">See Also</span></span>  
 <span data-ttu-id="17117-145">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="17117-145">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="17117-146">[允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="17117-146">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="17117-147">[为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="17117-147">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="17117-148">[使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="17117-148">[Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span></span>  
 <span data-ttu-id="17117-149">[从数据库镜像会话删除见证服务器 (SQL Server)](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="17117-149">[Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="17117-150">数据库镜像见证服务器</span><span class="sxs-lookup"><span data-stu-id="17117-150">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
