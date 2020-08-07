---
title: 第 5 课。  (可选) 使用 TDE 加密数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 613b66c04a69364f3c9be1059f95021dd3eff595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587815"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a><span data-ttu-id="a0dee-103">第 5 课。</span><span class="sxs-lookup"><span data-stu-id="a0dee-103">Lesson 5.</span></span> <span data-ttu-id="a0dee-104">（可选）使用 TDE 加密数据库</span><span class="sxs-lookup"><span data-stu-id="a0dee-104">(Optional) Encrypt your database using TDE</span></span>
  <span data-ttu-id="a0dee-105">作为一个可选步骤，可加密新创建的数据库。</span><span class="sxs-lookup"><span data-stu-id="a0dee-105">As an optional step, you can encrypt the newly created database.</span></span> <span data-ttu-id="a0dee-106">“透明数据加密”(TDE) 可对数据和日志文件执行实时 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="a0dee-106">Transparent data encryption (TDE) performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="a0dee-107">这种加密使用数据库加密密钥 (DEK)，该密钥存储在数据库引导记录中以供恢复时使用。</span><span class="sxs-lookup"><span data-stu-id="a0dee-107">This kind of encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="a0dee-108">有关详细信息，请参阅[透明数据加密 &#40;TDE&#41;](security/encryption/transparent-data-encryption.md) ，并[将受 TDE 保护的数据库移到另一个 SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a0dee-108">For more information, see [Transparent Data Encryption &#40;TDE&#41;](security/encryption/transparent-data-encryption.md) and [Move a TDE Protected Database to Another SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).</span></span>  
  
 <span data-ttu-id="a0dee-109">本课假定您已完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a0dee-109">This lesson assumes you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="a0dee-110">你有 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="a0dee-110">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="a0dee-111">在 Azure 存储帐户下创建了容器。</span><span class="sxs-lookup"><span data-stu-id="a0dee-111">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="a0dee-112">已在容器上创建了具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="a0dee-112">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="a0dee-113">还生成了 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="a0dee-113">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="a0dee-114">已在源计算机上创建了 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="a0dee-114">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="a0dee-115">已按第 4 课中所述的步骤创建了数据库。</span><span class="sxs-lookup"><span data-stu-id="a0dee-115">You have created a database by following the steps that are described in Lesson 4.</span></span>  
  
 <span data-ttu-id="a0dee-116">如果要加密数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a0dee-116">If you want to encrypt a database, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a0dee-117">在源计算机上，在查询窗口中修改并运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="a0dee-117">In the source machine, modify and run the following statements in a query window:</span></span>  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  <span data-ttu-id="a0dee-118">然后，通过执行以下步骤，在源计算机中加密新数据库：</span><span class="sxs-lookup"><span data-stu-id="a0dee-118">Then, encrypt your new database in the source machine by following these steps:</span></span>  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 <span data-ttu-id="a0dee-119">如果要了解数据库的加密状态及其关联的数据库加密密钥，请运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="a0dee-119">If you want to learn the encryption state of a database and its associated database encryption keys, run the following statement:</span></span>  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 <span data-ttu-id="a0dee-120">有关在本课中使用的 Transact-sql 语句的详细信息，请参阅[CREATE database &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)， [ALTER database &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)， [create MASTER KEY &#40;transact-sql&#41;](/sql/t-sql/statements/create-master-key-transact-sql)， [create CERTIFICATE &#40;transact-sql ](/sql/t-sql/statements/create-certificate-transact-sql)&#41;，dm_database_encryption_keys [&#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a0dee-120">For detailed information the Transact-SQL statements that have been used in this lesson, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), and [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).</span></span>  
  
 <span data-ttu-id="a0dee-121">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="a0dee-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="a0dee-122">第 6 课：将数据库从本地源计算机迁移至 Azure 中的目标计算机</span><span class="sxs-lookup"><span data-stu-id="a0dee-122">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
