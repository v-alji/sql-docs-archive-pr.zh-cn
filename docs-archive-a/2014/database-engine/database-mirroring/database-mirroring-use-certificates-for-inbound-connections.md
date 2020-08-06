---
title: 允许数据库镜像终结点将证书用于入站连接 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- inbound connections
- database mirroring [SQL Server], security
ms.assetid: 5d48bb98-61f0-4b99-8f1a-b53f831d63d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c05397dfbd1740293c4b154ace1ed5704cec11a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578409"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-inbound-connections-transact-sql"></a><span data-ttu-id="2ac4c-102">允许数据库镜像端点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2ac4c-102">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="2ac4c-103">本主题说明配置服务器实例以使用证书对数据库镜像的入站连接进行身份验证的步骤。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-103">This topic describes the steps for configuring server instances to use certificates to authenticate inbound connections for database mirroring.</span></span> <span data-ttu-id="2ac4c-104">在可以建立入站连接之前，必须在每个服务器实例上配置出站连接。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-104">Before you can set up inbound connections, you must configure outbound connections on each server instance.</span></span> <span data-ttu-id="2ac4c-105">有关详细信息，请参阅 [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-105">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
 <span data-ttu-id="2ac4c-106">配置入站连接的过程通常有以下几个步骤：</span><span class="sxs-lookup"><span data-stu-id="2ac4c-106">The process of configuring inbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="2ac4c-107">为其他系统创建登录名。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-107">Create a login for other system.</span></span>  
  
2.  <span data-ttu-id="2ac4c-108">创建一个使用该登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-108">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="2ac4c-109">获取其他服务器实例的镜像端点的证书。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-109">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="2ac4c-110">将该证书与在步骤 2 中创建的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-110">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="2ac4c-111">授予对该镜像端点的登录名的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-111">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="2ac4c-112">如果存在见证服务器，还必须为见证服务器设置进站连接。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-112">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="2ac4c-113">这需要在两个伙伴上为见证服务器设置登录名、用户和证书，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-113">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="2ac4c-114">下面的过程详细说明了这些步骤。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-114">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="2ac4c-115">对于每个步骤，该过程都提供了一个在名为 HOST_A 的系统上配置服务器实例的示例。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-115">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="2ac4c-116">伴随的示例部分说明了在名为 HOST_B 的系统上配置另一服务器实例的步骤（步骤相同）。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-116">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
### <a name="to-configure-server-instances-for-inbound-mirroring-connections-on-host_a"></a><span data-ttu-id="2ac4c-117">为入站镜像连接配置服务器实例（在 HOST_A 上）</span><span class="sxs-lookup"><span data-stu-id="2ac4c-117">To configure server instances for inbound mirroring connections (on HOST_A)</span></span>  
  
1.  <span data-ttu-id="2ac4c-118">为其他系统创建登录名。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-118">Create a login for the other system.</span></span>  
  
     <span data-ttu-id="2ac4c-119">下面的示例在 HOST_A 上的服务器实例的 **master** 数据库中为系统 HOST_B 创建登录名；在此示例中，登录名为 `HOST_B_login`。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-119">The following example creates a login for the system, HOST_B, in the **master** database of the server instance on HOST_A; in this example, the login is named `HOST_B_login`.</span></span> <span data-ttu-id="2ac4c-120">请用自己的密码替换示例密码。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-120">Substitute a password of your own for the sample password.</span></span>  
  
    ```sql  
    USE master;  
    CREATE LOGIN HOST_B_login   
       WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
     <span data-ttu-id="2ac4c-121">有关详细信息，请参阅 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-121">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
     <span data-ttu-id="2ac4c-122">若要查看此服务器实例上的登录名，可以使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="2ac4c-122">To view the logins on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.server_principals;  
    ```  
  
     <span data-ttu-id="2ac4c-123">有关详细信息，请参阅 [ys.server_principals (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-123">For more information, see [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql).</span></span>  
  
2.  <span data-ttu-id="2ac4c-124">创建一个使用该登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-124">Create a user for that login.</span></span>  
  
     <span data-ttu-id="2ac4c-125">下面的示例为上述步骤中创建的登录名创建了一个用户 `HOST_B_user`。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-125">The following example creates a user, `HOST_B_user`, for the login created in the preceding step.</span></span>  
  
    ```sql  
    USE master;  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
     <span data-ttu-id="2ac4c-126">有关详细信息，请参阅 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-126">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
     <span data-ttu-id="2ac4c-127">若要查看此服务器实例上的用户，可以使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="2ac4c-127">To view the users on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.sysusers;  
    ```  
  
     <span data-ttu-id="2ac4c-128">有关详细信息，请参阅 [sys.sysusers (Transact-SQL)](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-128">For more information, see [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql).</span></span>  
  
3.  <span data-ttu-id="2ac4c-129">获取其他服务器实例的镜像端点的证书。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-129">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
     <span data-ttu-id="2ac4c-130">如果配置出站连接时还没有获取远程服务器实例的镜像端点的证书副本，请执行此操作。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-130">If you have not already done so when configuring outbound connections, obtain a copy of the certificate for the mirroring endpoint of the remote server instance.</span></span> <span data-ttu-id="2ac4c-131">若要执行此操作，请按照 [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](database-mirroring-use-certificates-for-outbound-connections.md) 在该服务器实例上对证书进行备份。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-131">To do this, back up the certificate on that server instance as described in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span> <span data-ttu-id="2ac4c-132">将证书复制到其他系统时，请使用安全的复制方法。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-132">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="2ac4c-133">必须格外小心地保证所有证书的安全。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-133">Be extremely careful to keep all of your certificates secure.</span></span>  
  
     <span data-ttu-id="2ac4c-134">有关详细信息，请参阅 [BACKUP CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/backup-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-134">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
4.  <span data-ttu-id="2ac4c-135">将该证书与在步骤 2 中创建的用户相关联。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-135">Associate the certificate with the user created in step 2.</span></span>  
  
     <span data-ttu-id="2ac4c-136">下面的示例将 HOST_B 的证书与它在 HOST_A 上的用户关联。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-136">The following example, associates the certificate of HOST_B with its user on HOST_A.</span></span>  
  
    ```sql  
    USE master;  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
     <span data-ttu-id="2ac4c-137">有关详细信息，请参阅 [CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-137">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="2ac4c-138">若要查看此服务器实例上的证书，请使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="2ac4c-138">To view the certificates on this server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="2ac4c-139">有关详细信息，请参阅 [sys.certificates (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-139">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
5.  <span data-ttu-id="2ac4c-140">授予对远程镜像端点的登录名的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-140">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
     <span data-ttu-id="2ac4c-141">例如，若要将对 HOST_A 的权限授予 HOST_B 上的远程服务器实例，以连接到其本地登录名，即连接到 `HOST_B_login`，请使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="2ac4c-141">For example, to grant permission on HOST_A to the remote server instance on HOST_B to connect to its local login-that is, to connect to `HOST_B_login`-use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```sql  
    USE master;  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
     <span data-ttu-id="2ac4c-142">有关详细信息，请参阅 [GRANT 终结点权限 (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-142">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="2ac4c-143">这将完成对 HOST_B 登录到 HOST_A 所需的证书身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-143">This completes setting up certificate authentication for HOST_B to log in to HOST_A.</span></span>  
  
 <span data-ttu-id="2ac4c-144">您现在需要在 HOST_B 上为 HOST_A 执行相同的入站步骤，</span><span class="sxs-lookup"><span data-stu-id="2ac4c-144">You now need to perform the equivalent inbound steps for HOST_A on HOST_B.</span></span> <span data-ttu-id="2ac4c-145">下面的示例部分中示例的入站部分说明了这些步骤。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-145">These steps are illustrated in the inbound portion of the example in the Example section, below.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ac4c-146">示例</span><span class="sxs-lookup"><span data-stu-id="2ac4c-146">Example</span></span>  
 <span data-ttu-id="2ac4c-147">下面的示例说明了配置入站连接的 HOST_B。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-147">The following example demonstrates configuring HOST_B for inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ac4c-148">此示例使用一个包含 HOST_A 证书的证书文件，该证书由[允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](database-mirroring-use-certificates-for-outbound-connections.md) 中的代码片段创建。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-148">This example uses a certificate file containing the HOST_A certificate that is created by a code snippet in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
```sql  
USE master;  
--On HOST_B, create a login for HOST_A.  
CREATE LOGIN HOST_A_login WITH PASSWORD = 'AStrongPassword!@#';  
GO  
--Create a user, HOST_A_user, for that login.  
CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
GO  
--Obtain HOST_A certificate. (See the note   
--   preceding this example.)  
--Asscociate this certificate with the user, HOST_A_user.  
CREATE CERTIFICATE HOST_A_cert  
   AUTHORIZATION HOST_A_user  
   FROM FILE = 'C:\HOST_A_cert.cer';  
GO  
--Grant CONNECT permission for the server instance on HOST_A.  
GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO HOST_A_login;  
GO  
```  
  
 <span data-ttu-id="2ac4c-149">如果打算在具有自动故障转移功能的高安全性模式下运行，则必须重复相同的设置步骤为出站连接和入站连接配置见证服务器。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-149">If you intend to run in high-safety mode with automatic failover, you must repeat the same set up steps to configure the witness for outbound and inbound connections.</span></span>  
  
 <span data-ttu-id="2ac4c-150">有关创建镜像数据库（包括 Transact-SQL 示例）的详细信息，请参阅[为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-150">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="2ac4c-151">有关建立高性能模式会话的 Transact-SQL 示例，请参阅[示例：使用证书设置数据库镜像 (Transact-SQL)](example-setting-up-database-mirroring-using-certificates-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-151">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2ac4c-152">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="2ac4c-152">.NET Framework Security</span></span>  
 <span data-ttu-id="2ac4c-153">将证书复制到其他系统时，请使用安全的复制方法。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-153">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="2ac4c-154">必须格外小心地保证所有证书的安全。</span><span class="sxs-lookup"><span data-stu-id="2ac4c-154">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac4c-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ac4c-155">See Also</span></span>  
 <span data-ttu-id="2ac4c-156">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="2ac4c-156">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="2ac4c-157">[GRANT 终结点权限 (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2ac4c-157">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 <span data-ttu-id="2ac4c-158">[设置加密的镜像数据库](set-up-an-encrypted-mirror-database.md) </span><span class="sxs-lookup"><span data-stu-id="2ac4c-158">[Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md) </span></span>  
 <span data-ttu-id="2ac4c-159">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2ac4c-159">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 [<span data-ttu-id="2ac4c-160">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2ac4c-160">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
