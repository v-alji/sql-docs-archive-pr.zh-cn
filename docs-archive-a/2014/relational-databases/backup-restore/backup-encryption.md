---
title: 备份加密 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6a78ae4969982fbfe5295ee4219855f48ac60793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694507"
---
# <a name="backup-encryption"></a><span data-ttu-id="d1a5a-102">备份加密</span><span class="sxs-lookup"><span data-stu-id="d1a5a-102">Backup Encryption</span></span>
  <span data-ttu-id="d1a5a-103">本主题概述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份的加密选项。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-103">This topic provides an overview of the encryption options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="d1a5a-104">其中详细介绍备份期间加密的用法、优点和推荐做法。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-104">It includes details of the usage, benefits, and recommended practices for encrypting during backup.</span></span>  
  
  
##  <a name="overview"></a><a name="Overview"></a> <span data-ttu-id="d1a5a-105">概述</span><span class="sxs-lookup"><span data-stu-id="d1a5a-105">Overview</span></span>  
 <span data-ttu-id="d1a5a-106">从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]开始，SQL Server 可在创建备份时加密数据。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-106">Starting in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SQL Server has the ability to encrypt the data while creating a backup.</span></span> <span data-ttu-id="d1a5a-107">通过在创建备份时指定加密算法和加密程序（证书或非对称密钥），可创建加密的备份文件。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-107">By specifying the encryption algorithm and the encryptor (a Certificate or Asymmetric Key) when creating a backup, you can create an encrypted backup file.</span></span> <span data-ttu-id="d1a5a-108">所有存储目标：支持本地和 Windows Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-108">All storage destinations: on-premises and Window Azure storage are supported.</span></span> <span data-ttu-id="d1a5a-109">此外，可为 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 操作配置加密选项，这是 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]中引入的一项新功能。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-109">In addition, encryption options can be configured for [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] operations, a new feature introduced in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="d1a5a-110">若要在备份期间加密，必须指定加密算法以及用于保护加密密钥的加密程序。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-110">To encrypt during backup, you must specify an encryption algorithm, and an encryptor to secure the encryption key.</span></span> <span data-ttu-id="d1a5a-111">支持以下加密选项：</span><span class="sxs-lookup"><span data-stu-id="d1a5a-111">The following are the supported encryption options:</span></span>  
  
-   <span data-ttu-id="d1a5a-112">**加密算法：** 支持的加密算法包括：AES 128、AES 192、AES 256 和 Triple DES</span><span class="sxs-lookup"><span data-stu-id="d1a5a-112">**Encryption Algorithm:** The supported encryption algorithms are: AES 128, AES 192, AES 256, and Triple DES</span></span>  
  
-   <span data-ttu-id="d1a5a-113">**加密程序：** 证书或非对称密钥</span><span class="sxs-lookup"><span data-stu-id="d1a5a-113">**Encryptor:** A certificate or asymmetric Key</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d1a5a-114">备份证书或非对称密钥很重要，并且最好备份到与用于加密的备份文件不同的位置。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-114">It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt.</span></span> <span data-ttu-id="d1a5a-115">没有证书或非对称密钥，你将无法还原备份，从而使备份文件无法使用。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-115">Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable.</span></span>  
  
 <span data-ttu-id="d1a5a-116">**还原加密的备份：** SQL Server 还原不需要在还原期间指定任何加密参数。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-116">**Restoring the encrypted backup:** SQL Server restore does not require any encryption parameters to be specified during restores.</span></span> <span data-ttu-id="d1a5a-117">但要求在要还原到的实例上有用于加密备份文件的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-117">It does require that the certificate or the asymmetric key used to encrypt the backup file be available on the instance that you are restoring to.</span></span> <span data-ttu-id="d1a5a-118">执行还原的用户帐户必须对证书或密钥具有 `VIEW DEFINITION` 权限。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-118">The user account performing the restore must have `VIEW DEFINITION` permissions on the certificate or key.</span></span> <span data-ttu-id="d1a5a-119">如果将加密的备份还原到其他实例，则必须确保该实例上有证书。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-119">If you are restoring the encrypted backup to a different instance, you must make sure that the certificate is available on that instance.</span></span>  
  
 <span data-ttu-id="d1a5a-120">如果从经过 TDE 加密的数据库还原备份，则要还原到的实例上应有 TDE 证书。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-120">If you are restoring a backup from a TDE encrypted database, the TDE certificate should be available on the instance you are restoring to.</span></span>  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="d1a5a-121">优势</span><span class="sxs-lookup"><span data-stu-id="d1a5a-121">Benefits</span></span>  
  
1.  <span data-ttu-id="d1a5a-122">加密数据库备份有助于保证数据安全：SQL Server 提供用于在创建备份时加密备份数据的选项。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-122">Encrypting the database backups helps secure the data: SQL Server provides the option to encrypt the backup data while creating a backup.</span></span>  
  
2.  <span data-ttu-id="d1a5a-123">加密还可用于使用 TDE 加密的数据库。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-123">Encryption can also be used for databases that are encrypted using TDE.</span></span>  
  
3.  <span data-ttu-id="d1a5a-124">由 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]进行的备份支持加密，这样可提高站点外备份的安全性。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-124">Encryption is supported for backups done by [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], which provides additional security for off-site backups.</span></span>  
  
4.  <span data-ttu-id="d1a5a-125">此功能支持多个最高 AES 256 位的加密算法。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-125">This feature supports multiple encryption algorithms up to AES 256 bit.</span></span> <span data-ttu-id="d1a5a-126">这样可选择符合要求的算法。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-126">This gives you the option to select an algorithm that aligns with your requirements.</span></span>  
  
5.  <span data-ttu-id="d1a5a-127">可将加密密钥与扩展密钥管理 (EKM) 提供程序集成。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-127">You can integrate encryption keys with Extended Key Management (EKM) providers.</span></span>  
  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="d1a5a-128">先决条件</span><span class="sxs-lookup"><span data-stu-id="d1a5a-128">Prerequisites</span></span>  
 <span data-ttu-id="d1a5a-129">以下是有关加密备份的先决条件：</span><span class="sxs-lookup"><span data-stu-id="d1a5a-129">The following are prerequisites for encrypting a backup:</span></span>  
  
1.  <span data-ttu-id="d1a5a-130">**创建 master 数据库的数据库主密钥：** 数据库主密钥是一种用于保护数据库中存在的证书私钥和非对称密钥的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-130">**Create a Database Master Key for the master database:** The database master key is a symmetric key that is used to protect the private keys of certificates and asymmetric keys that are present in the database.</span></span> <span data-ttu-id="d1a5a-131">有关详细信息，请参阅 [SQL Server 和数据库加密密钥（数据库引擎）](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-131">For more information, see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md).</span></span>  
  
2.  <span data-ttu-id="d1a5a-132">创建用于备份加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-132">Create a certificate or asymmetric Key to use for backup encryption.</span></span> <span data-ttu-id="d1a5a-133">有关创建证书的详细信息，请参阅 [CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-133">For more information on creating a certificate, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span> <span data-ttu-id="d1a5a-134">有关创建非对称密钥的详细信息，请参阅[创建非对称密钥 (Transact-SQL)](/sql/t-sql/statements/create-asymmetric-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-134">For more information on creating an asymmetric key, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d1a5a-135">仅支持位于扩展密钥管理 (EKM) 中的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-135">Only asymmetric keys residing in an Extended Key Management (EKM) are supported.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d1a5a-136">限制</span><span class="sxs-lookup"><span data-stu-id="d1a5a-136">Restrictions</span></span>  
 <span data-ttu-id="d1a5a-137">以下限制适用于加密选项：</span><span class="sxs-lookup"><span data-stu-id="d1a5a-137">The following are restrictions that apply to the encryption options:</span></span>  
  
-   <span data-ttu-id="d1a5a-138">如果使用非对称密钥加密备份数据，则仅支持位于 EKM 提供程序中的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-138">If you are using asymmetric key to encrypt the backup data, only asymmetric keys residing in the EKM provider are supported.</span></span>  
  
-   <span data-ttu-id="d1a5a-139">SQL Server Express 和 SQL Server Web 不支持在备份期间进行加密。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-139">SQL Server Express and SQL Server Web do not support encryption during backup.</span></span> <span data-ttu-id="d1a5a-140">但是，支持从加密的备份还原到 SQL Server Express 或 SQL Server Web 的实例。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-140">However restoring from an encrypted backup to an instance of SQL Server Express or SQL Server Web is supported.</span></span>  
  
-   <span data-ttu-id="d1a5a-141">旧版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法读取加密的备份。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-141">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read encrypted backups.</span></span>  
  
-   <span data-ttu-id="d1a5a-142">加密的备份不支持追加到现有的备份集选项。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-142">Appending to an existing backup set option is not supported for encrypted backups.</span></span>  
  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d1a5a-143">权限</span><span class="sxs-lookup"><span data-stu-id="d1a5a-143">Permissions</span></span>  
 <span data-ttu-id="d1a5a-144">**若要加密备份或从加密的备份还原：**</span><span class="sxs-lookup"><span data-stu-id="d1a5a-144">**To encrypt a backup or to restore from an encrypted backup:**</span></span>  
  
 <span data-ttu-id="d1a5a-145">需要对用于加密数据库备份的证书或非对称密钥具有 `VIEW DEFINITION` 权限。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-145">`VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database backup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1a5a-146">不需要访问 TDE 证书即可备份或还原受 TDE 保护的数据库。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-146">Access to the TDE certificate is not required to back up or restore a TDE protected database.</span></span>  
  
##  <a name="backup-encryption-methods"></a><a name="Methods"></a> <span data-ttu-id="d1a5a-147">备份加密方法</span><span class="sxs-lookup"><span data-stu-id="d1a5a-147">Backup Encryption Methods</span></span>  
 <span data-ttu-id="d1a5a-148">以下各节简要介绍在备份期间加密数据的步骤。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-148">The sections below provide a brief introduction to the steps to encrypting the data during backup.</span></span> <span data-ttu-id="d1a5a-149">有关使用 Transact-SQL 加密备份的不同步骤的完整演练，请参阅 [创建加密的备份](create-an-encrypted-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-149">For a complete walkthrough of the different steps of encrypting your backup using Transact-SQL, see [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
### <a name="using-sql-server-management-studio"></a><span data-ttu-id="d1a5a-150">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d1a5a-150">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d1a5a-151">在以下任何对话框中，可在创建数据库的备份时加密备份。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-151">You can encrypt a backup when creating the backup of a database in any of the following dialog boxes:</span></span>  
  
1.  <span data-ttu-id="d1a5a-152">[备份数据库（“备份选项”页）](back-up-database-backup-options-page.md)在“备份选项”页上，可以选择“加密”，并指定加密算法和证书或非对称密钥以用于加密。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-152">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) On the **Backup Options** page, you can select **Encryption**, and specify the encryption algorithm and the certificate or asymmetric key to use for the encryption.</span></span>  
  
2.  <span data-ttu-id="d1a5a-153">[使用维护计划向导](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)选择某个备份任务后，可以在“定义备份()任务”页的“选项”选项卡上，选择“备份加密”，并指定加密算法和证书或密钥以用于加密。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-153">[Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) When you select a backup task, on the **Options** tab of the **Define Backup ()Task** page, you can select **Backup Encryption**, and specify the encryption algorithm and the certificate or key to use for the encryption.</span></span>  
  
### <a name="using-transact-sql"></a><span data-ttu-id="d1a5a-154">使用 Transact SQL</span><span class="sxs-lookup"><span data-stu-id="d1a5a-154">Using Transact SQL</span></span>  
 <span data-ttu-id="d1a5a-155">以下是示例 Transact-SQL 语句以加密备份文件：</span><span class="sxs-lookup"><span data-stu-id="d1a5a-155">Following is a sample Transact-SQL statement to encrypt the backup file:</span></span>  
  
```sql
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO
```  
  
 <span data-ttu-id="d1a5a-156">有关完整 Transact-SQL 语法，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-156">For the full Transact-SQL statement syntax, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="using-powershell"></a><span data-ttu-id="d1a5a-157">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1a5a-157">Using PowerShell</span></span>  
 <span data-ttu-id="d1a5a-158">此示例创建加密选项并在 **Backup-SqlDatabase** cmdlet 中将它作为参数值以创建加密的备份。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-158">This example creates the encryption options and uses it as a parameter value in **Backup-SqlDatabase** cmdlet to create an encrypted backup.</span></span>  
  
```powershell
$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  
Backup-SqlDatabase -ServerInstance . -Database "MyTestDB" -BackupFile "MyTestDB.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="recommended-practices"></a><a name="RecommendedPractices"></a> <span data-ttu-id="d1a5a-159">推荐做法</span><span class="sxs-lookup"><span data-stu-id="d1a5a-159">Recommended Practices</span></span>  
 <span data-ttu-id="d1a5a-160">将加密证书和密钥备份到安装实例的本地计算机以外的位置。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-160">Create a backup of the encryption certificate and keys to a location other than your local machine where the instance is installed.</span></span> <span data-ttu-id="d1a5a-161">若要考虑灾难恢复情况，请考虑将证书和密钥存储到站点外位置。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-161">To account for disaster recovery scenarios, consider storing a backup of the certificate or key to an off-site location.</span></span> <span data-ttu-id="d1a5a-162">没有用于加密备份的证书即无法还原加密的备份。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-162">You cannot restore an encrypted backup without the certificate used to encrypt the backup.</span></span>  
  
 <span data-ttu-id="d1a5a-163">若要还原加密的备份，要还原到的实例上应有进行备份时使用的原始证书及匹配的指纹。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-163">To restore an encrypted backup, the original certificate used when the backup was taken with the matching thumbprint should be available on the instance you are restoring to.</span></span> <span data-ttu-id="d1a5a-164">因此，不应在到期时续订或以任何方式更改证书。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-164">Therefore, the certificate should not be renewed on expiry or changed in any way.</span></span> <span data-ttu-id="d1a5a-165">续订可导致更改证书并触发指纹更改，从而使证书对于备份文件变为无效。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-165">Renewal can result in updating the certificate triggering the change of the thumbprint, therefore making the certificate invalid for the backup file.</span></span> <span data-ttu-id="d1a5a-166">执行还原的帐户应对备份期间用于加密的证书或非对称密钥具有 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-166">The account performing the restore should have VIEW DEFINITION permissions on the certificate or the asymmetric key used to encrypt during backup.</span></span>  
  
 <span data-ttu-id="d1a5a-167">可用性组数据库备份通常在首选备份副本上执行。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-167">Availability Group database backups are typically performed on the preferred backup replica.</span></span>  <span data-ttu-id="d1a5a-168">如果在不是备份来源的其他副本上还原备份，请确保用于备份的原始证书在还原到的副本上可用。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-168">If restoring a backup on a replica other than where the backup was taken from, ensure that the original certificate used for backup is available on the replica you are restoring to.</span></span>  
  
 <span data-ttu-id="d1a5a-169">如果数据库启用了 TDE，则选择其他证书或非对称密钥用于加密数据库和备份以提高安全性。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-169">If the database is TDE enabled, choose different certificates or asymmetric keys for encrypting the database and the backup to increase security.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d1a5a-170">相关任务</span><span class="sxs-lookup"><span data-stu-id="d1a5a-170">Related Tasks</span></span>  
  
|<span data-ttu-id="d1a5a-171">主题/任务</span><span class="sxs-lookup"><span data-stu-id="d1a5a-171">Topic/Task</span></span>|<span data-ttu-id="d1a5a-172">说明</span><span class="sxs-lookup"><span data-stu-id="d1a5a-172">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="d1a5a-173">创建加密的备份</span><span class="sxs-lookup"><span data-stu-id="d1a5a-173">Create an Encrypted Backup</span></span>](create-an-encrypted-backup.md)|<span data-ttu-id="d1a5a-174">介绍创建加密的备份所需的基本步骤</span><span class="sxs-lookup"><span data-stu-id="d1a5a-174">Describes the basic steps required to create an encrypted backup</span></span>|  
|[<span data-ttu-id="d1a5a-175">针对 Azure 的 SQL Server 托管备份 - 保留和存储设置</span><span class="sxs-lookup"><span data-stu-id="d1a5a-175">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|<span data-ttu-id="d1a5a-176">介绍在指定了加密选项的情况下配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-176">Describes the basic steps required to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with the encryption options specified.</span></span>|  
|[<span data-ttu-id="d1a5a-177">使用 Azure 密钥保管库的可扩展密钥管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d1a5a-177">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|<span data-ttu-id="d1a5a-178">提供了创建受 Azure 密钥保管库中的密钥保护的加密备份的示例。</span><span class="sxs-lookup"><span data-stu-id="d1a5a-178">Provides an example of creating an encrypted backup protected by keys in the Azure Key Vault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1a5a-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1a5a-179">See Also</span></span>  
 [<span data-ttu-id="d1a5a-180">备份概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d1a5a-180">Backup Overview &#40;SQL Server&#41;</span></span>](backup-overview-sql-server.md)  
  
  
