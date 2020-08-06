---
title: 使用 EKM 启用 TDE |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], TDE using an EKM
- TDE, EKM how to
- EKM, TDE how to
- Transparent Data Encryption, using EKM
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: e659c5ff0245fdb17192b845eafc60badf5e295e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693693"
---
# <a name="enable-tde-using-ekm"></a><span data-ttu-id="6720b-102">使用 EKM 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="6720b-102">Enable TDE Using EKM</span></span>
  <span data-ttu-id="6720b-103">本主题介绍如何在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中启用透明数据加密 (TDE)，以便通过结合使用存储在可扩展密钥管理 (EKM) 模块中的非对称密钥和 [!INCLUDE[tsql](../../../includes/tsql-md.md)]来保护数据库加密密钥。</span><span class="sxs-lookup"><span data-stu-id="6720b-103">This topic describes how to enable transparent data encryption (TDE) in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to protect a database encryption key by using an asymmetric key stored in an extensible key management (EKM) module with [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6720b-104">TDE 使用称为数据库加密密钥的对称密钥来加密整个数据库的存储。</span><span class="sxs-lookup"><span data-stu-id="6720b-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="6720b-105">还可以使用受 master 数据库的数据库主密钥保护的证书来保护数据库加密密钥。</span><span class="sxs-lookup"><span data-stu-id="6720b-105">The database encryption key can also be protected using a certificate which is protected by the database master key of the master database.</span></span> <span data-ttu-id="6720b-106">有关使用数据库主密钥保护数据库加密密钥的详细信息，请参阅[透明数据加密 (TDE)](transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="6720b-106">For more information about protecting the database encryption key by using the database master key, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span> <span data-ttu-id="6720b-107">有关当 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在 Azure VM 上运行时配置 TDE 的信息，请参阅[使用 Azure Key Vault 的可扩展密钥管理 (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6720b-107">For information about configuring TDE when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running on an Azure VM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
 <span data-ttu-id="6720b-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="6720b-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6720b-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6720b-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6720b-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6720b-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6720b-111">安全性</span><span class="sxs-lookup"><span data-stu-id="6720b-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="6720b-112">使用 EKM 和 Transact-SQL 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="6720b-112">To enable TDE using EKM, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6720b-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="6720b-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6720b-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6720b-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6720b-115">必须是高特权用户（如系统管理员）才能创建数据库加密密钥以及加密数据库。</span><span class="sxs-lookup"><span data-stu-id="6720b-115">You must be a high privileged user (such as a system administrator) to create a database encryption key and encrypt a database.</span></span> <span data-ttu-id="6720b-116">该用户必须能够通过 EKM 模块进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6720b-116">That user must be able to be authenticated by the EKM module.</span></span>  
  
-   <span data-ttu-id="6720b-117">启动时， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 必须打开数据库。</span><span class="sxs-lookup"><span data-stu-id="6720b-117">Upon start up the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must open the database.</span></span> <span data-ttu-id="6720b-118">为此，您应创建一个将通过 EKM 进行身份验证的凭据，并将该凭据添加到一个基于非对称密钥的登录名。</span><span class="sxs-lookup"><span data-stu-id="6720b-118">To do this, you should create a credential that will be authenticated by the EKM, and add it to a login that is based on an asymmetric key.</span></span> <span data-ttu-id="6720b-119">用户无法使用该登录名进行登录，但 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 将能够通过 EKM 设备对其自身进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6720b-119">Users cannot login using that login, but the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] will be able to authenticate itself with the EKM device.</span></span>  
  
-   <span data-ttu-id="6720b-120">如果存储在 EKM 模块中的非对称密钥丢失， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]将无法打开数据库。</span><span class="sxs-lookup"><span data-stu-id="6720b-120">If the asymmetric key stored in the EKM module is lost, the database will not be able to be opened by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6720b-121">如果 EKM 提供程序允许您备份非对称密钥，则应该创建备份并将该备份存储到安全的位置。</span><span class="sxs-lookup"><span data-stu-id="6720b-121">If the EKM provider lets you back up the asymmetric key, you should create a back up and store it in a secure location.</span></span>  
  
-   <span data-ttu-id="6720b-122">您的 EKM 提供程序所需的选项和参数可能与下面的代码示例中所提供的选项和参数不同。</span><span class="sxs-lookup"><span data-stu-id="6720b-122">The options and parameters required by your EKM provider can differ from what is provided in the code example below.</span></span> <span data-ttu-id="6720b-123">有关详细信息，请参阅 EKM 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6720b-123">For more information, see your EKM provider.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6720b-124">Security</span><span class="sxs-lookup"><span data-stu-id="6720b-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6720b-125">权限</span><span class="sxs-lookup"><span data-stu-id="6720b-125">Permissions</span></span>  
 <span data-ttu-id="6720b-126">本主题使用了以下权限：</span><span class="sxs-lookup"><span data-stu-id="6720b-126">This topic uses the following permissions:</span></span>  
  
-   <span data-ttu-id="6720b-127">若要更改配置选项以及运行 RECONFIGURE 语句，您必须具有 ALTER SETTINGS 服务器级别权限。</span><span class="sxs-lookup"><span data-stu-id="6720b-127">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="6720b-128">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="6720b-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
-   <span data-ttu-id="6720b-129">需要 ALTER ANY CREDENTIAL 权限。</span><span class="sxs-lookup"><span data-stu-id="6720b-129">Requires ALTER ANY CREDENTIAL permission.</span></span>  
  
-   <span data-ttu-id="6720b-130">需要 ALTER ANY LOGIN 权限。</span><span class="sxs-lookup"><span data-stu-id="6720b-130">Requires ALTER ANY LOGIN permission.</span></span>  
  
-   <span data-ttu-id="6720b-131">需要 CREATE ASYMMETRIC KEY 权限。</span><span class="sxs-lookup"><span data-stu-id="6720b-131">Requires CREATE ASYMMETRIC KEY permission.</span></span>  
  
-   <span data-ttu-id="6720b-132">需要拥有对数据库的 CONTROL 权限才能加密该数据库。</span><span class="sxs-lookup"><span data-stu-id="6720b-132">Requires CONTROL permission on the database to encrypt the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6720b-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6720b-133">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-tde-using-ekm"></a><span data-ttu-id="6720b-134">使用 EKM 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="6720b-134">To enable TDE using EKM</span></span>  
  
1.  <span data-ttu-id="6720b-135">将由 EKM 提供程序提供的文件复制到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 计算机上的相应位置。</span><span class="sxs-lookup"><span data-stu-id="6720b-135">Copy the files supplied by the EKM provider to an appropriate location on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="6720b-136">在本示例中，我们使用 **C:\EKM** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="6720b-136">In this example, we use the **C:\EKM** folder.</span></span>  
  
2.  <span data-ttu-id="6720b-137">根据 EKM 提供程序的要求，将证书安装到计算机上。</span><span class="sxs-lookup"><span data-stu-id="6720b-137">Install certificates to the computer as required by your EKM provider.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6720b-138">不提供 EKM 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6720b-138">does not supply an EKM provider.</span></span> <span data-ttu-id="6720b-139">每个 EKM 提供程序可以有不同的安装、配置和授权用户的过程。</span><span class="sxs-lookup"><span data-stu-id="6720b-139">Each EKM provider can have different procedures for installing, configuring and authorizing users.</span></span>  <span data-ttu-id="6720b-140">请查阅 EKM 提供程序文档，完成此步骤。</span><span class="sxs-lookup"><span data-stu-id="6720b-140">Consult your EKM provider documentation to complete this step.</span></span>  
  
3.  <span data-ttu-id="6720b-141">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6720b-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
4.  <span data-ttu-id="6720b-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6720b-142">On the Standard bar, click **New Query**.</span></span>  
  
5.  <span data-ttu-id="6720b-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="6720b-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 <span data-ttu-id="6720b-144">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="6720b-144">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="6720b-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6720b-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [<span data-ttu-id="6720b-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6720b-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [<span data-ttu-id="6720b-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6720b-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="6720b-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6720b-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [<span data-ttu-id="6720b-149">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6720b-149">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [<span data-ttu-id="6720b-150">CREATE DATABASE ENCRYPTION KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6720b-150">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="6720b-151">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6720b-151">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
-   [<span data-ttu-id="6720b-152">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6720b-152">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [<span data-ttu-id="6720b-153">使用 Azure 密钥保管库的可扩展密钥管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6720b-153">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
-   [<span data-ttu-id="6720b-154">借助 Azure SQL 数据库实现透明数据加密</span><span class="sxs-lookup"><span data-stu-id="6720b-154">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)  
  
  
