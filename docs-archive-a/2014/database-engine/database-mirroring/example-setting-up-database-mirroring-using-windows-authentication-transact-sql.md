---
title: 示例：使用 Windows 身份验证设置数据库镜像 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: 35800769-aede-4aac-b077-0e0e487e302f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95df855e8e41c5937aae02884c71792537eb2bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578391"
---
# <a name="example-setting-up-database-mirroring-using-windows-authentication-transact-sql"></a><span data-ttu-id="e7e24-102">示例：使用 Windows 身份验证设置数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7e24-102">Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="e7e24-103">此示例说明使用 Windows 身份验证来创建带有见证服务器的数据库镜像会话所需的所有阶段。</span><span class="sxs-lookup"><span data-stu-id="e7e24-103">This example shows all the stages required to create a database mirroring session with a witness using Windows Authentication.</span></span> <span data-ttu-id="e7e24-104">本主题中的示例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e7e24-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e7e24-105">注意，可以不使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步骤，而使用配置数据库镜像安全向导来设置数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="e7e24-105">Note that as an alternative to using [!INCLUDE[tsql](../../includes/tsql-md.md)] steps, you can use the Configure Database Mirroring Security Wizard for database mirroring setup.</span></span> <span data-ttu-id="e7e24-106">有关详细信息，请参阅本主题后面的 [使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="e7e24-106">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="e7e24-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="e7e24-107">Prerequisite</span></span>  
 <span data-ttu-id="e7e24-108">该示例使用了 **AdventureWorks** 示例数据库，在默认情况下该数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="e7e24-108">The example uses the **AdventureWorks** sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="e7e24-109">若要对此数据库进行数据库镜像，必须将它更改为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="e7e24-109">To use database mirroring with this database, you must alter it to use the full recovery model.</span></span> <span data-ttu-id="e7e24-110">若要用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 实现此目的，请使用 ALTER DATABASE 语句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e7e24-110">To do this in [!INCLUDE[tsql](../../includes/tsql-md.md)], use the ALTER DATABASE statement, as follows:</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks   
SET RECOVERY FULL;  
GO  
```  
  
 <span data-ttu-id="e7e24-111">有关更改 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中恢复模式的信息，请参阅[查看或更改数据库的恢复模式 (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7e24-111">For information on changing the recovery model in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="e7e24-112">权限</span><span class="sxs-lookup"><span data-stu-id="e7e24-112">Permissions</span></span>  
 <span data-ttu-id="e7e24-113">需要对数据库的 ALTER 权限和 CREATE ENDPOINT 权限，或者需要 **sysadmin** 固定服务器角色的成员资格。</span><span class="sxs-lookup"><span data-stu-id="e7e24-113">Requires ALTER permission on the database and CREATE ENDPOINT permission, or membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7e24-114">示例</span><span class="sxs-lookup"><span data-stu-id="e7e24-114">Example</span></span>  
 <span data-ttu-id="e7e24-115">在此示例中，两个伙伴服务器和见证服务器分别是三台计算机系统上的默认服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e7e24-115">In this example, the two partners and the witness are the default server instances on three computer systems.</span></span> <span data-ttu-id="e7e24-116">这三个服务器实例运行同一个 Windows 域，但本示例的见证服务器实例的用户帐户（用作启动服务帐户）有所不同。</span><span class="sxs-lookup"><span data-stu-id="e7e24-116">The three server instances run the same Windows domain, but the user account (used as the startup service account) is different for the example's witness server instance.</span></span>  
  
 <span data-ttu-id="e7e24-117">下表总结了此示例中使用的值。</span><span class="sxs-lookup"><span data-stu-id="e7e24-117">The following table summarizes the values used in this example.</span></span>  
  
|<span data-ttu-id="e7e24-118">初始镜像角色</span><span class="sxs-lookup"><span data-stu-id="e7e24-118">Initial mirroring role</span></span>|<span data-ttu-id="e7e24-119">宿主系统</span><span class="sxs-lookup"><span data-stu-id="e7e24-119">Host system</span></span>|<span data-ttu-id="e7e24-120">域用户帐户</span><span class="sxs-lookup"><span data-stu-id="e7e24-120">Domain user account</span></span>|  
|----------------------------|-----------------|-------------------------|  
|<span data-ttu-id="e7e24-121">主体</span><span class="sxs-lookup"><span data-stu-id="e7e24-121">Principal</span></span>|<span data-ttu-id="e7e24-122">PARTNERHOST1</span><span class="sxs-lookup"><span data-stu-id="e7e24-122">PARTNERHOST1</span></span>|<span data-ttu-id="e7e24-123">\<Mydomain>\\<dbousername\></span><span class="sxs-lookup"><span data-stu-id="e7e24-123">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="e7e24-124">镜像</span><span class="sxs-lookup"><span data-stu-id="e7e24-124">Mirror</span></span>|<span data-ttu-id="e7e24-125">PARTNERHOST5</span><span class="sxs-lookup"><span data-stu-id="e7e24-125">PARTNERHOST5</span></span>|<span data-ttu-id="e7e24-126">\<Mydomain>\\<dbousername\></span><span class="sxs-lookup"><span data-stu-id="e7e24-126">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="e7e24-127">见证</span><span class="sxs-lookup"><span data-stu-id="e7e24-127">Witness</span></span>|<span data-ttu-id="e7e24-128">WITNESSHOST4</span><span class="sxs-lookup"><span data-stu-id="e7e24-128">WITNESSHOST4</span></span>|<span data-ttu-id="e7e24-129">\<Somedomain>\\<witnessuser\></span><span class="sxs-lookup"><span data-stu-id="e7e24-129">*\<Somedomain>\\<witnessuser\>*</span></span>|  
  
1.  <span data-ttu-id="e7e24-130">在主体服务器实例（PARTNERHOST1 中的默认实例）上创建端点。</span><span class="sxs-lookup"><span data-stu-id="e7e24-130">Create an endpoint on the principal server instance (default instance on PARTNERHOST1).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=PARTNER)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    -- Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
2.  <span data-ttu-id="e7e24-131">在镜像服务器实例（PARTNERHOST5 中的默认实例）上创建端点。</span><span class="sxs-lookup"><span data-stu-id="e7e24-131">Create an endpoint on the mirror server instance (default instance on PARTNERHOST5).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="e7e24-132">在见证服务器实例（WITNESSHOST4 中的默认实例）上创建端点。</span><span class="sxs-lookup"><span data-stu-id="e7e24-132">Create an endpoint on the witness server instance (default instance on WITNESSHOST4).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    --Create a login for the partner server instances,  
    --which are both running as Mydomain\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [Mydomain\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
4.  <span data-ttu-id="e7e24-133">创建镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="e7e24-133">Create the mirror database.</span></span> <span data-ttu-id="e7e24-134">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e7e24-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="e7e24-135">在 PARTNERHOST5 中的镜像服务器实例上，将 PARTNERHOST1 中的服务器实例设置为伙伴（使它成为初始的主体服务器实例）。</span><span class="sxs-lookup"><span data-stu-id="e7e24-135">On the mirror server instance on PARTNERHOST5, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1.COM:7022'  
    GO  
    ```  
  
6.  <span data-ttu-id="e7e24-136">在 PARTNERHOST1 中的主体服务器实例上，将 PARTNERHOST5 中的服务器实例设置为伙伴（使它成为初始的镜像服务器实例）。</span><span class="sxs-lookup"><span data-stu-id="e7e24-136">On the principal server instance on PARTNERHOST1, set the server instance on PARTNERHOST5 as the partner (making it the initial mirror server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5.COM:7022'  
    GO  
    ```  
  
7.  <span data-ttu-id="e7e24-137">在主体服务器中，设置见证服务器（位于 WITNESSHOST4 中）。</span><span class="sxs-lookup"><span data-stu-id="e7e24-137">On the principal server, set the witness (which is on WITNESSHOST4).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4.COM:7022'  
    GO  
    ```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e7e24-138">相关任务</span><span class="sxs-lookup"><span data-stu-id="e7e24-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e7e24-139">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e7e24-139">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="e7e24-140">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e7e24-140">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="e7e24-141">将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7e24-141">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
-   [<span data-ttu-id="e7e24-142">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7e24-142">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="e7e24-143">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7e24-143">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="e7e24-144">示例：使用证书设置数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7e24-144">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7e24-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7e24-145">See Also</span></span>  
 <span data-ttu-id="e7e24-146">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e7e24-146">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="e7e24-147">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7e24-147">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="e7e24-148">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e7e24-148">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="e7e24-149">[当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7e24-149">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 [<span data-ttu-id="e7e24-150">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="e7e24-150">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
