---
title: 示例：使用证书设置数据库镜像 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: df489ecd-deee-465c-a26a-6d1bef6d7b66
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea87e2de984107c5a0fda6eb2629ee5cfd197841
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694123"
---
# <a name="example-setting-up-database-mirroring-using-certificates-transact-sql"></a><span data-ttu-id="c4387-102">示例：使用证书设置数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c4387-102">Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)</span></span>
  <span data-ttu-id="c4387-103">此示例演示了使用基于证书的身份验证创建数据库镜像会话所需的所有阶段。</span><span class="sxs-lookup"><span data-stu-id="c4387-103">This example shows all the stages required to create a database mirroring session using certificate-based authentication.</span></span> <span data-ttu-id="c4387-104">本主题中的示例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4387-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c4387-105">建议您对数据库镜像连接进行加密，除非您能够保证网络的安全。</span><span class="sxs-lookup"><span data-stu-id="c4387-105">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="c4387-106">将证书复制到其他系统时，请使用安全的复制方法。</span><span class="sxs-lookup"><span data-stu-id="c4387-106">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="c4387-107">必须格外小心地保证所有证书的安全。</span><span class="sxs-lookup"><span data-stu-id="c4387-107">Be extremely careful to keep all of your certificates secure.</span></span>  
  
##  <a name="example"></a><a name="ExampleH2"></a> <span data-ttu-id="c4387-108">示例</span><span class="sxs-lookup"><span data-stu-id="c4387-108">Example</span></span>  
 <span data-ttu-id="c4387-109">下面的示例演示必须对驻留在 HOST_A 上的一个伙伴执行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="c4387-109">The following example demonstrates what must be done on one partner that resides on HOST_A.</span></span> <span data-ttu-id="c4387-110">在此示例中，两个伙伴是三个计算机系统上的默认服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c4387-110">In this example, the two partners are the default server instances on three computer systems.</span></span> <span data-ttu-id="c4387-111">两个服务器实例在非信任的 Windows 域中运行，因此需要基于证书的身份验证。</span><span class="sxs-lookup"><span data-stu-id="c4387-111">The two server instances run in nontrusted Windows domains, so certificate-based authentication is required.</span></span>  
  
 <span data-ttu-id="c4387-112">HOST_A 担当初始主体角色，HOST_B 担当镜像角色。</span><span class="sxs-lookup"><span data-stu-id="c4387-112">The initial principal role is taken by HOST_A, and the mirror role is taken by HOST_B.</span></span>  
  
 <span data-ttu-id="c4387-113">使用证书设置数据库镜像涉及四个常规阶段，本示例演示其中的三个阶段：1、2、4。</span><span class="sxs-lookup"><span data-stu-id="c4387-113">Setting up database mirroring using certificates involves four general stages, of which three stages-1, 2, and 4-are demonstrated by this example.</span></span> <span data-ttu-id="c4387-114">这些阶段如下：</span><span class="sxs-lookup"><span data-stu-id="c4387-114">These stages are as follows:</span></span>  
  
1.  [<span data-ttu-id="c4387-115">配置出站连接</span><span class="sxs-lookup"><span data-stu-id="c4387-115">Configuring Outbound Connections</span></span>](#ConfiguringOutboundConnections)  
  
     <span data-ttu-id="c4387-116">本示例显示了下列操作的步骤：</span><span class="sxs-lookup"><span data-stu-id="c4387-116">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="c4387-117">为出站连接配置 Host_A。</span><span class="sxs-lookup"><span data-stu-id="c4387-117">Configuring Host_A for outbound connections.</span></span>  
  
    2.  <span data-ttu-id="c4387-118">为出站连接配置 Host_B。</span><span class="sxs-lookup"><span data-stu-id="c4387-118">Configuring Host_B for outbound connections.</span></span>  
  
     <span data-ttu-id="c4387-119">有关设置数据库镜像的本阶段信息，请参阅 [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-119">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
2.  [<span data-ttu-id="c4387-120">配置入站连接</span><span class="sxs-lookup"><span data-stu-id="c4387-120">Configuring Inbound Connections</span></span>](#ConfigureInboundConnections)  
  
     <span data-ttu-id="c4387-121">本示例显示了下列操作的步骤：</span><span class="sxs-lookup"><span data-stu-id="c4387-121">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="c4387-122">为入站连接配置 Host_A。</span><span class="sxs-lookup"><span data-stu-id="c4387-122">Configuring Host_A for inbound connections.</span></span>  
  
    2.  <span data-ttu-id="c4387-123">为入站连接配置 Host_B。</span><span class="sxs-lookup"><span data-stu-id="c4387-123">Configuring Host_B for inbound connections.</span></span>  
  
     <span data-ttu-id="c4387-124">有关设置数据库镜像的本阶段信息，请参阅 [允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-124">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
3.  <span data-ttu-id="c4387-125">创建镜像数据库</span><span class="sxs-lookup"><span data-stu-id="c4387-125">Creating the Mirror Database</span></span>  
  
     <span data-ttu-id="c4387-126">有关如何创建镜像数据库的信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-126">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
4.  [<span data-ttu-id="c4387-127">配置镜像伙伴</span><span class="sxs-lookup"><span data-stu-id="c4387-127">Configuring the Mirroring Partners</span></span>](#ConfigureMirroringPartners)  
  
###  <a name="configuring-outbound-connections"></a><a name="ConfiguringOutboundConnections"></a> <span data-ttu-id="c4387-128">配置出站连接</span><span class="sxs-lookup"><span data-stu-id="c4387-128">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="c4387-129">**为出站连接配置 Host_A**</span><span class="sxs-lookup"><span data-stu-id="c4387-129">**To configure Host_A for outbound connections**</span></span>  
  
1.  <span data-ttu-id="c4387-130">在 master 数据库中，创建数据库主密钥（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="c4387-130">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
2.  <span data-ttu-id="c4387-131">为此服务器实例制作一个证书。</span><span class="sxs-lookup"><span data-stu-id="c4387-131">Make a certificate for this server instance.</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate';  
    GO  
    ```  
  
3.  <span data-ttu-id="c4387-132">使用该证书为服务器实例创建一个镜像端点。</span><span class="sxs-lookup"><span data-stu-id="c4387-132">Create a mirroring endpoint for server instance using the certificate.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  <span data-ttu-id="c4387-133">备份 HOST_A 证书，并将其复制到其他系统，即 HOST_B。</span><span class="sxs-lookup"><span data-stu-id="c4387-133">Back up the HOST_A certificate, and copy it to other system, HOST_B.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
5.  <span data-ttu-id="c4387-134">使用任一安全的复制方法，将 C:\HOST_A_cert.cer 复制到 HOST_B。</span><span class="sxs-lookup"><span data-stu-id="c4387-134">Using any secure copy method, copy C:\HOST_A_cert.cer to HOST_B.</span></span>  
  
 <span data-ttu-id="c4387-135">**为出站连接配置 Host_B**</span><span class="sxs-lookup"><span data-stu-id="c4387-135">**To configure Host_B for outbound connections**</span></span>  
  
1.  <span data-ttu-id="c4387-136">在 master 数据库中，创建数据库主密钥（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="c4387-136">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
    GO  
    ```  
  
2.  <span data-ttu-id="c4387-137">为 HOST_B 服务器实例制作一个证书。</span><span class="sxs-lookup"><span data-stu-id="c4387-137">Make a certificate on the HOST_B server instance.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert   
       WITH SUBJECT = 'HOST_B certificate for database mirroring';  
    GO  
    ```  
  
3.  <span data-ttu-id="c4387-138">在 HOST_B 中为服务器实例创建一个镜像端点。</span><span class="sxs-lookup"><span data-stu-id="c4387-138">Create a mirroring endpoint for the server instance on HOST_B.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_B_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  <span data-ttu-id="c4387-139">备份 HOST_B 证书。</span><span class="sxs-lookup"><span data-stu-id="c4387-139">Back up HOST_B certificate.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
    GO   
    ```  
  
5.  <span data-ttu-id="c4387-140">使用任一安全的复制方法，将 C:\HOST_B_cert.cer 复制到 HOST_A。</span><span class="sxs-lookup"><span data-stu-id="c4387-140">Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.</span></span>  
  
 <span data-ttu-id="c4387-141">有关详细信息，请参阅 [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-141">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
###  <a name="configuring-inbound-connections"></a><a name="ConfigureInboundConnections"></a> <span data-ttu-id="c4387-142">配置入站连接</span><span class="sxs-lookup"><span data-stu-id="c4387-142">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="c4387-143">**为入站连接配置 Host_A**</span><span class="sxs-lookup"><span data-stu-id="c4387-143">**To configure Host_A for inbound connections**</span></span>  
  
1.  <span data-ttu-id="c4387-144">在 HOST_A 上为 HOST_B 创建一个登录名。</span><span class="sxs-lookup"><span data-stu-id="c4387-144">Create a login on HOST_A for HOST_B.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_B_login WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
2.  <span data-ttu-id="c4387-145">创建一个使用该登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="c4387-145">--Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="c4387-146">使证书与该用户关联。</span><span class="sxs-lookup"><span data-stu-id="c4387-146">--Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="c4387-147">授予对远程镜像端点的登录名的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="c4387-147">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
 <span data-ttu-id="c4387-148">**为入站连接配置 Host_B**</span><span class="sxs-lookup"><span data-stu-id="c4387-148">**To configure Host_B for inbound connections**</span></span>  
  
1.  <span data-ttu-id="c4387-149">在 HOST_B 上为 HOST_A 创建一个登录名。</span><span class="sxs-lookup"><span data-stu-id="c4387-149">Create a login on HOST_B for HOST_A.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_A_login WITH PASSWORD = '=Sample#2_Strong_Password2';  
    GO  
    ```  
  
2.  <span data-ttu-id="c4387-150">创建一个使用该登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="c4387-150">Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="c4387-151">使证书与该用户关联。</span><span class="sxs-lookup"><span data-stu-id="c4387-151">Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_A_cert  
       AUTHORIZATION HOST_A_user  
       FROM FILE = 'C:\HOST_A_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="c4387-152">授予对远程镜像端点的登录名的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="c4387-152">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_A_login];  
    GO  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c4387-153">如果打算在具有自动故障转移功能的高安全性模式下运行，则必须重复相同的设置步骤为出站连接和入站连接配置见证服务器。</span><span class="sxs-lookup"><span data-stu-id="c4387-153">If you intend to run in high-safety mode with automatic failover, you must repeat the same setup steps to configure the witness for outbound and inbound connections.</span></span> <span data-ttu-id="c4387-154">设置入站连接时，如果涉及到见证服务器，则需要为两个伙伴的见证服务器和见证服务器的两个伙伴设置登录名和用户。</span><span class="sxs-lookup"><span data-stu-id="c4387-154">Setting up the inbound connections when a witness is involved requires that you set up logins and users for the witness on both of the partners and for both partners on the witness.</span></span>  
  
 <span data-ttu-id="c4387-155">有关详细信息，请参阅 [允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-155">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="c4387-156">创建镜像数据库</span><span class="sxs-lookup"><span data-stu-id="c4387-156">Creating the Mirror Database</span></span>  
 <span data-ttu-id="c4387-157">有关如何创建镜像数据库的信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-157">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
###  <a name="configuring-the-mirroring-partners"></a><a name="ConfigureMirroringPartners"></a> <span data-ttu-id="c4387-158">配置镜像伙伴</span><span class="sxs-lookup"><span data-stu-id="c4387-158">Configuring the Mirroring Partners</span></span>  
  
1.  <span data-ttu-id="c4387-159">在 HOST_B 的镜像服务器实例上，将 HOST_A 上的服务器实例设置为伙伴（使其成为初始主体服务器实例）。</span><span class="sxs-lookup"><span data-stu-id="c4387-159">On the mirror server instance on HOST_B, set the server instance on HOST_A as the partner (making it the initial principal server instance).</span></span> <span data-ttu-id="c4387-160">将 `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`替换为有效的网络地址。</span><span class="sxs-lookup"><span data-stu-id="c4387-160">Substitute a valid network address for `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`.</span></span> <span data-ttu-id="c4387-161">有关详细信息，请参阅 [指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="c4387-161">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
    ```  
    --At HOST_B, set server instance on HOST_A as partner (principal server):  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_A.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
2.  <span data-ttu-id="c4387-162">在 HOST_A 的主体服务器实例上，将 HOST_B 上的服务器实例设置为伙伴（使其成为初始镜像服务器实例）。</span><span class="sxs-lookup"><span data-stu-id="c4387-162">On the principal server instance on HOST_A, set the server instance on HOST_B as the partner (making it the initial mirror server instance).</span></span> <span data-ttu-id="c4387-163">将 `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`替换为有效的网络地址。</span><span class="sxs-lookup"><span data-stu-id="c4387-163">Substitute a valid network address for `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`.</span></span>  
  
    ```  
    --At HOST_A, set server instance on HOST_B as partner (mirror server).  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
3.  <span data-ttu-id="c4387-164">此示例假设会话将在高性能模式下运行。</span><span class="sxs-lookup"><span data-stu-id="c4387-164">This example assumes that the session will be running in high-performance mode.</span></span> <span data-ttu-id="c4387-165">若要在高性能模式下配置此会话，在主体服务器实例上（位于 HOST_A 上），将事务安全性设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="c4387-165">To configure this session for high-performance mode, on the principal server instance (on HOST_A), set transaction safety to OFF.</span></span>  
  
    ```  
    --Change to high-performance mode by turning off transacton safety.  
    ALTER DATABASE AdventureWorks   
        SET PARTNER SAFETY OFF  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4387-166">如果打算在具有自动故障转移功能的高安全性模式下运行，请将 "事务安全" 设置为 "完整" (默认设置) 并在执行第二个 set 伙伴 **" *`partner_server`* "** 语句后尽快添加见证服务器。</span><span class="sxs-lookup"><span data-stu-id="c4387-166">If you intend to run in high-safety mode with automatic failover, leave transaction safety set to FULL (the default setting) and add the witness as soon as possible after executing the second SET PARTNER **'*`partner_server`*'** statement.</span></span> <span data-ttu-id="c4387-167">注意，必须首先为出站连接和入站连接配置见证服务器。</span><span class="sxs-lookup"><span data-stu-id="c4387-167">Note that the witness must first be configured for outbound and inbound connections.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c4387-168">相关任务</span><span class="sxs-lookup"><span data-stu-id="c4387-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c4387-169">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c4387-169">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="c4387-170">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c4387-170">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="c4387-171">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c4387-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="c4387-172">角色切换后登录名和作业的管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c4387-172">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
-   <span data-ttu-id="c4387-173">[当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c4387-173">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span></span>  
  
-   [<span data-ttu-id="c4387-174">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c4387-174">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4387-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4387-175">See Also</span></span>  
 <span data-ttu-id="c4387-176">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="c4387-176">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="c4387-177">[指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="c4387-177">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="c4387-178">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4387-178">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="c4387-179">[使用数据库镜像终结点证书 (Transact-SQL)](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="c4387-179">[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span></span>  
 <span data-ttu-id="c4387-180">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4387-180">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="c4387-181">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="c4387-181">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
