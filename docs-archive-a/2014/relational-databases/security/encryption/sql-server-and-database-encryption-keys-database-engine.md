---
title: SQL Server 和数据库加密密钥（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- keys [SQL Server], database encryption
ms.assetid: 15c0a5e8-9177-484c-ae75-8c552dc0dac0
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: f846e74e0afd89c6bb10a4aa9a23a6420b6a613a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694415"
---
# <a name="sql-server-and-database-encryption-keys-database-engine"></a><span data-ttu-id="6e584-102">SQL Server 和数据库加密密钥（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="6e584-102">SQL Server and Database Encryption Keys (Database Engine)</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6e584-103">使用加密密钥帮助保护存储在服务器数据库中的数据、凭据和连接信息。</span><span class="sxs-lookup"><span data-stu-id="6e584-103">uses encryption keys to help secure data, credentials, and connection information that is stored in a server database.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6e584-104">的密钥分为两种：“对称”和“非对称”。</span><span class="sxs-lookup"><span data-stu-id="6e584-104">has two kinds of keys: *symmetric* and *asymmetric*.</span></span> <span data-ttu-id="6e584-105">对称密钥使用相同的密码对数据进行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="6e584-105">Symmetric keys use the same password to encrypt and decrypt data.</span></span> <span data-ttu-id="6e584-106">非对称密钥使用一个密码来加密数据（称为公钥），使用另一个密码来解密数据（称为私钥）。</span><span class="sxs-lookup"><span data-stu-id="6e584-106">Asymmetric keys use one password to encrypt data (called the *public* key) and another to decrypt data (called the *private* key).</span></span>  
  
 <span data-ttu-id="6e584-107">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，加密密钥包括一组用来保护敏感数据的公钥、私钥和对称密钥。</span><span class="sxs-lookup"><span data-stu-id="6e584-107">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], encryption keys include a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="6e584-108">当第一次启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例时，将在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 初始化过程中创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="6e584-108">The symmetric key is created during [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] initialization when you first start the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="6e584-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用此密钥来加密存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="6e584-109">The key is used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to encrypt sensitive data that is stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6e584-110">公钥和私钥由操作系统创建，用于保护对称密钥。</span><span class="sxs-lookup"><span data-stu-id="6e584-110">Public and private keys are created by the operating system and they are used to protect the symmetric key.</span></span> <span data-ttu-id="6e584-111">对于在数据库中存储敏感数据的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，都要创建一个公钥私钥对。</span><span class="sxs-lookup"><span data-stu-id="6e584-111">A public and private key pair is created for each [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that stores sensitive data in a database.</span></span>  
  
## <a name="applications-for-sql-server-and-database-keys"></a><span data-ttu-id="6e584-112">SQL Server 和数据库密钥的应用</span><span class="sxs-lookup"><span data-stu-id="6e584-112">Applications for SQL Server and Database Keys</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6e584-113">在密钥中的应用主要有两个方面：作为某 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上为该实例生成的*服务主密钥* (SMK) 和作为用于数据库的*数据库主密钥* (DMK)。</span><span class="sxs-lookup"><span data-stu-id="6e584-113">has two primary applications for keys: a *service master key* (SMK) generated on and for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance, and a *database master key* (DMK) used for a database.</span></span>  
  
 <span data-ttu-id="6e584-114">当第一次启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例时，将自动生成 SMK 并用于对链接的服务器密码、凭据和数据库主密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="6e584-114">The SMK is automatically generated the first time the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance is started and is used to encrypt a linked server password, credentials, and the database master key.</span></span> <span data-ttu-id="6e584-115">SMK 是通过使用采用 Windows 数据保护 API (DPAPI) 的本地计算机密钥进行加密的。</span><span class="sxs-lookup"><span data-stu-id="6e584-115">The SMK is encrypted by using the local computer key using the Windows Data Protection API (DPAPI).</span></span> <span data-ttu-id="6e584-116">DPAPI 使用从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户的 Windows 凭据和计算机的凭据派生的密钥。</span><span class="sxs-lookup"><span data-stu-id="6e584-116">The DPAPI uses a key that is derived from the Windows credentials of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account and the computer's credentials.</span></span> <span data-ttu-id="6e584-117">服务主密钥只能由创建它时所用的服务帐户或可以访问该计算机凭据的主体进行解密。</span><span class="sxs-lookup"><span data-stu-id="6e584-117">The service master key can only be decrypted by the service account under which it was created or by a principal that has access to the machine's credentials.</span></span>  
  
 <span data-ttu-id="6e584-118">数据库主密钥是一种用于保护数据库中存在的证书私钥和非对称密钥的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="6e584-118">The database master key is a symmetric key that is used to protect the private keys of certificates and asymmetric keys that are present in the database.</span></span> <span data-ttu-id="6e584-119">它还可用于对数据进行加密，但由于它有长度限制，所以用于数据加密时实用性不如对称密钥。</span><span class="sxs-lookup"><span data-stu-id="6e584-119">It can also be used to encrypt data, but it has length limitations that make it less practical for data than using a symmetric key.</span></span>  
  
 <span data-ttu-id="6e584-120">当创建主密钥时，会使用 Triple DES 算法以及用户提供的密码对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="6e584-120">When it is created, the master key is encrypted by using the Triple DES algorithm and a user-supplied password.</span></span> <span data-ttu-id="6e584-121">若要启用数据库主密钥的自动解密，请使用 SMK 对此密钥的副本进行加密。</span><span class="sxs-lookup"><span data-stu-id="6e584-121">To enable the automatic decryption of the master key, a copy of the key is encrypted by using the SMK.</span></span> <span data-ttu-id="6e584-122">此密钥的副本存储在使用它的数据库和 `master` 系统数据库中。</span><span class="sxs-lookup"><span data-stu-id="6e584-122">It is stored in both the database where it is used and in the `master` system database.</span></span>  
  
 <span data-ttu-id="6e584-123">每当更改 DMK 时，存储在 `master` 系统数据库中的 DMK 副本都将在没有提示的情况下更新。</span><span class="sxs-lookup"><span data-stu-id="6e584-123">The copy of the DMK stored in the `master` system database is silently updated whenever the DMK is changed.</span></span> <span data-ttu-id="6e584-124">但是，使用 `DROP ENCRYPTION BY SERVICE MASTER KEY` 语句的 `ALTER MASTER KEY` 选项可以更改此默认设置。</span><span class="sxs-lookup"><span data-stu-id="6e584-124">However, this default can be changed by using the `DROP ENCRYPTION BY SERVICE MASTER KEY` option of the `ALTER MASTER KEY` statement.</span></span> <span data-ttu-id="6e584-125">必须使用 `OPEN MASTER KEY` 语句和密码打开未使用服务主密钥进行加密的 DMK。</span><span class="sxs-lookup"><span data-stu-id="6e584-125">A DMK that is not encrypted by the service master key must be opened by using the `OPEN MASTER KEY` statement and a password.</span></span>  
  
## <a name="managing-sql-server-and-database-keys"></a><span data-ttu-id="6e584-126">管理 SQL Server 和数据库密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-126">Managing SQL Server and Database Keys</span></span>  
 <span data-ttu-id="6e584-127">对加密密钥的管理包括创建新数据库密钥，创建服务器和数据库密钥的备份以及了解还原、删除或更改密钥的条件和方式。</span><span class="sxs-lookup"><span data-stu-id="6e584-127">Managing encryption keys consists of creating new database keys, creating a backup of the server and database keys, and knowing when and how to restore, delete, or change the keys.</span></span>  
  
 <span data-ttu-id="6e584-128">若要管理对称密钥，可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中包括的工具执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="6e584-128">To manage symmetric keys, you can use the tools included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to do the following:</span></span>  
  
-   <span data-ttu-id="6e584-129">备份服务器和数据库密钥的副本，以便可以使用这些密钥来恢复服务器安装，或作为计划迁移的一部分。</span><span class="sxs-lookup"><span data-stu-id="6e584-129">Back up a copy of the server and database keys so that you can use them to recover a server installation, or as part of a planned migration.</span></span>  
  
-   <span data-ttu-id="6e584-130">将以前保存的密钥还原到数据库。</span><span class="sxs-lookup"><span data-stu-id="6e584-130">Restore a previously saved key to a database.</span></span> <span data-ttu-id="6e584-131">这样，新服务器实例就可以访问最初不是由其加密的现有数据。</span><span class="sxs-lookup"><span data-stu-id="6e584-131">This enables a new server instance to access existing data that it did not originally encrypt.</span></span>  
  
-   <span data-ttu-id="6e584-132">当不能再访问加密数据时删除数据库中的加密数据，这种情况极少出现。</span><span class="sxs-lookup"><span data-stu-id="6e584-132">Delete the encrypted data in a database in the unlikely event that you can no longer access encrypted data.</span></span>  
  
-   <span data-ttu-id="6e584-133">当密钥的安全性受到威胁时，重新创建密钥并重新对数据进行加密，这种情况极少出现。</span><span class="sxs-lookup"><span data-stu-id="6e584-133">Re-create keys and re-encrypt data in the unlikely event that the key is compromised.</span></span> <span data-ttu-id="6e584-134">作为安全性方面的最佳做法，您应定期（例如，每隔几个月）重新创建密钥以保护服务器，使其能够抵御试图解开密钥的攻击。</span><span class="sxs-lookup"><span data-stu-id="6e584-134">As a security best practice, you should re-create the keys periodically (for example, every few months) to protect the server from attacks that try to decipher the keys.</span></span>  
  
-   <span data-ttu-id="6e584-135">在服务器扩展部署（多个服务器同时共享单个数据库以及为该数据库提供可逆加密的密钥）中添加或删除服务器实例。</span><span class="sxs-lookup"><span data-stu-id="6e584-135">Add or remove a server instance from a server scale-out deployment where multiple servers share both a single database and the key that provides reversible encryption for that database.</span></span>  
  
## <a name="important-security-information"></a><span data-ttu-id="6e584-136">重要的安全信息</span><span class="sxs-lookup"><span data-stu-id="6e584-136">Important Security Information</span></span>  
 <span data-ttu-id="6e584-137">访问由服务主密钥保护的对象需要使用用来创建该密钥的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户或计算机帐户。</span><span class="sxs-lookup"><span data-stu-id="6e584-137">Accessing objects secured by the service master key requires either the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service account that was used to create the key or the computer (machine) account.</span></span> <span data-ttu-id="6e584-138">即，计算机与创建密钥的系统绑定在一起。</span><span class="sxs-lookup"><span data-stu-id="6e584-138">That is, the computer is tied to the system where the key was created.</span></span> <span data-ttu-id="6e584-139">可以更改 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户或计算机帐户，而不会失去对密钥的访问权限。</span><span class="sxs-lookup"><span data-stu-id="6e584-139">You can change the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service account *or* the computer account without losing access to the key.</span></span> <span data-ttu-id="6e584-140">但是，如果同时更改两者，则将失去对服务主密钥的访问权限。</span><span class="sxs-lookup"><span data-stu-id="6e584-140">However, if you change both, you will lose access to the service master key.</span></span> <span data-ttu-id="6e584-141">如果在不具有这两个元素中的任何一个的情况下失去了服务主密钥的访问权限，则将无法对使用原始密钥加密的数据和对象进行解密。</span><span class="sxs-lookup"><span data-stu-id="6e584-141">If you lose access to the service master key without one of these two elements, you be unable to decrypt data and objects encrypted by using the original key.</span></span>  
  
 <span data-ttu-id="6e584-142">如果没有服务主密钥，则将无法还原受服务主密钥保护的连接。</span><span class="sxs-lookup"><span data-stu-id="6e584-142">Connections secured with the service master key cannot be restored without the service master key.</span></span>  
  
 <span data-ttu-id="6e584-143">访问受数据库主密钥保护的对象和数据只需要有用于帮助保护密钥的密码。</span><span class="sxs-lookup"><span data-stu-id="6e584-143">Access to objects and data secured with the database master key require only the password that is used to help secure the key.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6e584-144">如果失去了对前述密钥的所有访问权限，则将无法访问由这些密钥保护的对象、连接和数据。</span><span class="sxs-lookup"><span data-stu-id="6e584-144">If you lose all access to the keys described earlier, you will lose access to the objects, connections, and data secured by those keys.</span></span> <span data-ttu-id="6e584-145">可按照此处显示的链接中说明的方法还原服务主密钥，也可以返回原始加密系统来恢复访问权限。</span><span class="sxs-lookup"><span data-stu-id="6e584-145">You can restore the service master key, as described in the links that are shown here, or you can go back to the original encrypting system to recover the access.</span></span> <span data-ttu-id="6e584-146">没有用来恢复访问权限的“后门”。</span><span class="sxs-lookup"><span data-stu-id="6e584-146">There is no "back-door" to recover the access.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e584-147">本节内容</span><span class="sxs-lookup"><span data-stu-id="6e584-147">In This Section</span></span>  
 [<span data-ttu-id="6e584-148">服务主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-148">Service Master Key</span></span>](service-master-key.md)  
 <span data-ttu-id="6e584-149">简要介绍服务主密钥及其最佳用法。</span><span class="sxs-lookup"><span data-stu-id="6e584-149">Provides a brief explanation for the service master key and its best practices.</span></span>  
  
 [<span data-ttu-id="6e584-150">可扩展密钥管理 &#40;EKM&#41;</span><span class="sxs-lookup"><span data-stu-id="6e584-150">Extensible Key Management &#40;EKM&#41;</span></span>](extensible-key-management-ekm.md)  
 <span data-ttu-id="6e584-151">说明如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中使用第三方密钥管理系统。</span><span class="sxs-lookup"><span data-stu-id="6e584-151">Explains how to use third-party key management systems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6e584-152">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6e584-152">Related Tasks</span></span>  
 [<span data-ttu-id="6e584-153">备份服务主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-153">Back Up the Service Master Key</span></span>](back-up-the-service-master-key.md)  
  
 [<span data-ttu-id="6e584-154">还原服务主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-154">Restore the Service Master Key</span></span>](restore-the-service-master-key.md)  
  
 [<span data-ttu-id="6e584-155">创建数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-155">Create a Database Master Key</span></span>](create-a-database-master-key.md)  
  
 [<span data-ttu-id="6e584-156">备份数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-156">Back Up a Database Master Key</span></span>](back-up-a-database-master-key.md)  
  
 [<span data-ttu-id="6e584-157">还原数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-157">Restore a Database Master Key</span></span>](restore-a-database-master-key.md)  
  
 [<span data-ttu-id="6e584-158">在两个服务器上创建相同的对称密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-158">Create Identical Symmetric Keys on Two Servers</span></span>](create-identical-symmetric-keys-on-two-servers.md)  
  
 [<span data-ttu-id="6e584-159">使用 Azure 密钥保管库的可扩展密钥管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e584-159">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 [<span data-ttu-id="6e584-160">使用 EKM 启用 TDE</span><span class="sxs-lookup"><span data-stu-id="6e584-160">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="related-content"></a><span data-ttu-id="6e584-161">相关内容</span><span class="sxs-lookup"><span data-stu-id="6e584-161">Related Content</span></span>  
 [<span data-ttu-id="6e584-162">CREATE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6e584-162">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
 [<span data-ttu-id="6e584-163">ALTER SERVICE MASTER KEY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6e584-163">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
 [<span data-ttu-id="6e584-164">还原数据库主密钥</span><span class="sxs-lookup"><span data-stu-id="6e584-164">Restore a Database Master Key</span></span>](restore-a-database-master-key.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e584-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e584-165">See Also</span></span>  
 <span data-ttu-id="6e584-166">[备份和还原 Reporting Services 加密密钥](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="6e584-166">[Back Up and Restore Reporting Services Encryption Keys](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="6e584-167">[删除和重新创建加密密钥（SSRS 配置管理器）](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="6e584-167">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="6e584-168">[添加和删除扩展部署的加密密钥（SSRS 配置管理器）](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="6e584-168">[Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span></span>  
 [<span data-ttu-id="6e584-169">透明数据加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="6e584-169">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)  
  
  
