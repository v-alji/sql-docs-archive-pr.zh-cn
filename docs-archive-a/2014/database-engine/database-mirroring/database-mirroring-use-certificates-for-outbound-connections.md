---
title: 允许数据库镜像终结点使用证书进行出站连接 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- outbound connections [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 464c9096-10d6-4c5e-8bb1-19acba27ad9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f380f268f8d0f8d033db9c28f83d066d3f134571
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578408"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-outbound-connections-transact-sql"></a><span data-ttu-id="945d1-102">允许数据库镜像端点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="945d1-102">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="945d1-103">本主题说明配置服务器实例以使用证书对数据库镜像的出站连接进行身份验证的步骤。</span><span class="sxs-lookup"><span data-stu-id="945d1-103">This topic describes the steps for configuring server instances to use certificates to authenticate outbound connections for database mirroring.</span></span> <span data-ttu-id="945d1-104">必须配置出站连接，才可以设置入站连接。</span><span class="sxs-lookup"><span data-stu-id="945d1-104">Outbound connection configuration must be done before you can set up inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="945d1-105">服务器实例上的所有镜像连接都使用单个数据库镜像端点，必须在创建端点时指定服务器实例的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="945d1-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span>  
  
 <span data-ttu-id="945d1-106">配置出站连接的进程分为以下基本步骤：</span><span class="sxs-lookup"><span data-stu-id="945d1-106">The process of configuring outbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="945d1-107">在 **master** 数据库中，创建数据库主密钥。</span><span class="sxs-lookup"><span data-stu-id="945d1-107">In the **master** database, create a database Master Key.</span></span>  
  
2.  <span data-ttu-id="945d1-108">在 **master** 数据库中，为服务器实例创建加密证书。</span><span class="sxs-lookup"><span data-stu-id="945d1-108">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="945d1-109">使用服务器实例的证书为该服务器实例创建端点。</span><span class="sxs-lookup"><span data-stu-id="945d1-109">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="945d1-110">将证书备份到文件，并将其安全地复制到其他系统。</span><span class="sxs-lookup"><span data-stu-id="945d1-110">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="945d1-111">必须对每一个伙伴和见证服务器（如果存在）完成以上步骤。</span><span class="sxs-lookup"><span data-stu-id="945d1-111">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="945d1-112">下面的过程详细说明了这些步骤。</span><span class="sxs-lookup"><span data-stu-id="945d1-112">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="945d1-113">对于每个步骤，该过程都提供了一个在名为 HOST_A 的系统上配置服务器实例的示例。</span><span class="sxs-lookup"><span data-stu-id="945d1-113">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="945d1-114">伴随的示例部分说明了在名为 HOST_B 的系统上配置另一服务器实例的步骤（步骤相同）。</span><span class="sxs-lookup"><span data-stu-id="945d1-114">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="945d1-115">过程</span><span class="sxs-lookup"><span data-stu-id="945d1-115">Procedure</span></span>  
  
#### <a name="to-configure-server-instances-for-outbound-mirroring-connections-on-host_a"></a><span data-ttu-id="945d1-116">配置用于出站镜像连接的服务器实例（在 HOST_A 上）</span><span class="sxs-lookup"><span data-stu-id="945d1-116">To configure server instances for outbound mirroring connections (On HOST_A)</span></span>  
  
1.  <span data-ttu-id="945d1-117">在 **master** 数据库上，创建数据库主密钥（如果不存在）。</span><span class="sxs-lookup"><span data-stu-id="945d1-117">On the **master** database, create the database Master Key, if none exists.</span></span> <span data-ttu-id="945d1-118">若要查看数据库的现有密钥，请使用 [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="945d1-118">To view the existing keys for a database, use the [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) catalog view.</span></span>  
  
     <span data-ttu-id="945d1-119">若要创建数据库主密钥，请使用下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="945d1-119">To create the database Master Key, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command:</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
     <span data-ttu-id="945d1-120">使用唯一的强密码，并将其记录到一个安全的位置。</span><span class="sxs-lookup"><span data-stu-id="945d1-120">Use a unique, strong password, and record it in a safe place.</span></span>  
  
     <span data-ttu-id="945d1-121">有关详细信息，请参阅 [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql) 和[创建数据库主密钥](../../relational-databases/security/encryption/create-a-database-master-key.md)。</span><span class="sxs-lookup"><span data-stu-id="945d1-121">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md).</span></span>  
  
2.  <span data-ttu-id="945d1-122">在 **master** 数据库中，对服务器实例创建一个用于其数据库镜像出站连接的加密证书。</span><span class="sxs-lookup"><span data-stu-id="945d1-122">In the **master** database, create an encrypted certificate on the server instance to use for its outbound connections for database mirroring.</span></span>  
  
     <span data-ttu-id="945d1-123">例如，为 HOST_A 系统创建一个证书。</span><span class="sxs-lookup"><span data-stu-id="945d1-123">For example, to create a certificate for the HOST_A system.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="945d1-124">如果您想要使用超过一年的证书，则通过在 CREATE CERTIFICATE 语句中使用 EXPIRY_DATE 选项，按 UTC 时间指定到期日期。</span><span class="sxs-lookup"><span data-stu-id="945d1-124">If you intend to use the certificate for more than one year, specify the expiry date in UTC time by using the EXPIRY_DATE option in your CREATE CERTIFICATE statement.</span></span> <span data-ttu-id="945d1-125">此外，我们建议您使用 SQL Server Management Studio 来创建基于策略的管理规则，以便在证书到期时提醒您。</span><span class="sxs-lookup"><span data-stu-id="945d1-125">Also, we recommend that you use SQL Server Management Studio to create a Policy-Based Management rule to alert you when your certificates are expiring.</span></span> <span data-ttu-id="945d1-126">使用策略管理的 **“创建新条件”** 对话框，在 **@ExpirationDate** 方面的 **“到期日期”** 字段中创建此规则。</span><span class="sxs-lookup"><span data-stu-id="945d1-126">Using the Policy Management **Create New Condition** dialog box, create this rule on the **@ExpirationDate** field of the **Certificate** facet.</span></span> <span data-ttu-id="945d1-127">有关详细信息，请参阅 [使用基于策略的管理来管理服务器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) 和 [保护 SQL Server](../../relational-databases/security/securing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="945d1-127">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Securing SQL Server](../../relational-databases/security/securing-sql-server.md).</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate for database mirroring',   
       EXPIRY_DATE = '11/30/2013';  
    GO  
    ```  
  
     <span data-ttu-id="945d1-128">有关详细信息，请参阅 [CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="945d1-128">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="945d1-129">若要查看 **master** 数据库中的证书，可以使用下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="945d1-129">To view the certificates in the **master** database, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="945d1-130">有关详细信息，请参阅 [sys.certificates (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="945d1-130">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
3.  <span data-ttu-id="945d1-131">确保每个服务器实例上都存在数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="945d1-131">Ensure that the database mirroring endpoint exist on each of the server instances.</span></span>  
  
     <span data-ttu-id="945d1-132">如果服务器实例上已存在数据库镜像端点，则您应将该端点重新用于在服务器实例上建立的任何其他会话。</span><span class="sxs-lookup"><span data-stu-id="945d1-132">If a database mirroring endpoint already exists for the server instance, you should reuse that endpoint for any other sessions you establish on the server instance.</span></span> <span data-ttu-id="945d1-133">若要确定服务器实例上是否存在数据库镜像端点并查看其配置，请使用下面的语句：</span><span class="sxs-lookup"><span data-stu-id="945d1-133">To determine whether a database mirroring endpoint exists on a server instance and to view its configuration, use the following statement:</span></span>  
  
    ```  
    SELECT name, role_desc, state_desc, connection_auth_desc, encryption_algorithm_desc   
       FROM sys.database_mirroring_endpoints;  
    ```  
  
     <span data-ttu-id="945d1-134">如果端点不存在，请创建一个端点，该端点使用此证书进行出站连接，并使用此证书的凭据通过其他系统的验证。</span><span class="sxs-lookup"><span data-stu-id="945d1-134">If no endpoint exists, create an endpoint that uses this certificate for outbound connections and that uses the certificate's credentials for verification on the other system.</span></span> <span data-ttu-id="945d1-135">这是一个服务器范围内的端点，供服务器实例参与的所有镜像会话使用。</span><span class="sxs-lookup"><span data-stu-id="945d1-135">This is a server-wide endpoint that is used by all mirroring sessions in which the server instance participates.</span></span>  
  
     <span data-ttu-id="945d1-136">例如，为 HOST_A 上的示例服务器实例创建镜像端点。</span><span class="sxs-lookup"><span data-stu-id="945d1-136">For example, to create a mirroring endpoint for the example server instance on HOST_A.</span></span>  
  
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
  
     <span data-ttu-id="945d1-137">有关详细信息，请参阅 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="945d1-137">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
4.  <span data-ttu-id="945d1-138">备份证书并将其复制到其他系统。</span><span class="sxs-lookup"><span data-stu-id="945d1-138">Back up the certificate and copy it to the other system or systems.</span></span> <span data-ttu-id="945d1-139">若要在其他系统上配置入站连接，此步骤是必需的。</span><span class="sxs-lookup"><span data-stu-id="945d1-139">This is necessary in order to configure inbound connections on the other system.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
     <span data-ttu-id="945d1-140">有关详细信息，请参阅 [BACKUP CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/backup-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="945d1-140">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="945d1-141">使用您选择的任何安全方法复制此证书。</span><span class="sxs-lookup"><span data-stu-id="945d1-141">Copy this certificate using any secure method you choose.</span></span> <span data-ttu-id="945d1-142">必须格外小心地保证所有证书的安全。</span><span class="sxs-lookup"><span data-stu-id="945d1-142">Be extremely careful to keep all of your certificates secure.</span></span>  
  
 <span data-ttu-id="945d1-143">前面步骤中的示例代码将在 HOST_A 上配置出站连接。</span><span class="sxs-lookup"><span data-stu-id="945d1-143">The example code in the preceding steps configure outbound connections on HOST_A.</span></span>  
  
 <span data-ttu-id="945d1-144">您现在需要对 HOST_B 执行相同的出站步骤，</span><span class="sxs-lookup"><span data-stu-id="945d1-144">You now need to perform the equivalent outbound steps for HOST_B.</span></span> <span data-ttu-id="945d1-145">下面的示例部分说明了这些步骤。</span><span class="sxs-lookup"><span data-stu-id="945d1-145">These steps are illustrated in the following Example section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="945d1-146">示例</span><span class="sxs-lookup"><span data-stu-id="945d1-146">Example</span></span>  
 <span data-ttu-id="945d1-147">下面的示例说明了如何配置 HOST_B 以进行出站连接。</span><span class="sxs-lookup"><span data-stu-id="945d1-147">The following example demonstrates configuring HOST_B for outbound connections.</span></span>  
  
```  
USE master;  
--Create the database Master Key, if needed.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
GO  
-- Make a certifcate on HOST_B server instance.  
CREATE CERTIFICATE HOST_B_cert   
   WITH SUBJECT = 'HOST_B certificate for database mirroring',   
   EXPIRY_DATE = '11/30/2013';  
GO  
--Create a mirroring endpoint for the server instance on HOST_B.  
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
--Backup HOST_B certificate.  
BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
GO   
--Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.  
```  
  
 <span data-ttu-id="945d1-148">使用您选择的任何安全方法将证书复制到其他系统。</span><span class="sxs-lookup"><span data-stu-id="945d1-148">Copy the certificate to the other system using any secure method you choose.</span></span> <span data-ttu-id="945d1-149">必须格外小心地保证所有证书的安全。</span><span class="sxs-lookup"><span data-stu-id="945d1-149">Be extremely careful to keep all of your certificates secure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="945d1-150">在建立出站连接之后，必须在每个服务器实例上为其他服务器实例配置入站连接。</span><span class="sxs-lookup"><span data-stu-id="945d1-150">After you set up outbound connections, you must configure inbound connections on each server instance for the other server instance or instances.</span></span> <span data-ttu-id="945d1-151">有关详细信息，请参阅 [允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="945d1-151">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
 <span data-ttu-id="945d1-152">有关创建镜像数据库（包括 Transact-SQL 示例）的详细信息，请参阅[为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="945d1-152">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="945d1-153">有关建立高性能模式会话的 Transact-SQL 示例，请参阅[示例：使用证书设置数据库镜像 (Transact-SQL)](example-setting-up-database-mirroring-using-certificates-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="945d1-153">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="945d1-154">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="945d1-154">.NET Framework Security</span></span>  
 <span data-ttu-id="945d1-155">建议您对数据库镜像连接进行加密，除非您能够保证网络的安全。</span><span class="sxs-lookup"><span data-stu-id="945d1-155">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="945d1-156">将证书复制到其他系统时，请使用安全的复制方法。</span><span class="sxs-lookup"><span data-stu-id="945d1-156">When copying a certificate to another system, use a secure copy method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945d1-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="945d1-157">See Also</span></span>  
 <span data-ttu-id="945d1-158">[选择加密算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="945d1-158">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="945d1-159">[为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="945d1-159">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="945d1-160">[ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="945d1-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="945d1-161">[示例：使用证书设置数据库镜像 (Transact-SQL)](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="945d1-161">[Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span></span>  
 <span data-ttu-id="945d1-162">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="945d1-162">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="945d1-163">[数据库镜像配置故障排除 (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="945d1-163">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="945d1-164">设置加密的镜像数据库</span><span class="sxs-lookup"><span data-stu-id="945d1-164">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
