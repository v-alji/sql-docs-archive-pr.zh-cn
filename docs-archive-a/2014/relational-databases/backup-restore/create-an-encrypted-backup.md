---
title: 创建加密的备份 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d46cc686684d87fe393a5db7cfe01194ae917836
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692975"
---
# <a name="create-an-encrypted-backup"></a><span data-ttu-id="b4548-102">创建加密的备份</span><span class="sxs-lookup"><span data-stu-id="b4548-102">Create an Encrypted Backup</span></span>
  <span data-ttu-id="b4548-103">本主题介绍使用 Transact-SQL 创建加密备份所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="b4548-103">This topic describes the steps necessary to create an encrypted backup using Transact-SQL.</span></span>  
  
## <a name="backup-to-disk-with-encryption"></a><span data-ttu-id="b4548-104">备份到磁盘并加密</span><span class="sxs-lookup"><span data-stu-id="b4548-104">Backup to Disk with Encryption</span></span>  
 <span data-ttu-id="b4548-105">**先决条件：**</span><span class="sxs-lookup"><span data-stu-id="b4548-105">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="b4548-106">有权访问本地磁盘或空间充足的存储以创建数据库备份。</span><span class="sxs-lookup"><span data-stu-id="b4548-106">Access to a local disk or to storage with adequate space to create a backup of the database.</span></span>  
  
-   <span data-ttu-id="b4548-107">master 数据库的数据库主密钥以及 SQL Server 实例上提供的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="b4548-107">A Database Master Key for the master database, and a certificate or asymmetric key available on the instance of SQL Server.</span></span> <span data-ttu-id="b4548-108">有关加密要求和权限，请参阅 [Backup Encryption](backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="b4548-108">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
 <span data-ttu-id="b4548-109">按照以下步骤向本地磁盘创建数据库的加密备份。</span><span class="sxs-lookup"><span data-stu-id="b4548-109">Use the following steps to create an encrypted backup of a database to a local disk.</span></span> <span data-ttu-id="b4548-110">本例使用一个名为 MyTestDB 的用户数据库。</span><span class="sxs-lookup"><span data-stu-id="b4548-110">This example uses a user database called MyTestDB.</span></span>  
  
1.  <span data-ttu-id="b4548-111">**创建 master 数据库的数据库主密钥：** 选择密码来对存储于该数据库中的主密钥副本进行加密。</span><span class="sxs-lookup"><span data-stu-id="b4548-111">**Create a Database Master Key of the master database:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="b4548-112">连接到数据库引擎，启动新查询窗口并复制和粘贴下例，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b4548-112">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  <span data-ttu-id="b4548-113">**创建备份证书：** 在 master 数据库中创建备份证书。</span><span class="sxs-lookup"><span data-stu-id="b4548-113">**Create a Backup Certificate:** Create a backup certificate in the master database.</span></span> <span data-ttu-id="b4548-114">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b4548-114">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="b4548-115">**备份数据库：** 指定要使用的加密算法和证书。</span><span class="sxs-lookup"><span data-stu-id="b4548-115">**Backup the database:** Specify the encryption algorithm and certificate to use.</span></span> <span data-ttu-id="b4548-116">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="b4548-116">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 <span data-ttu-id="b4548-117">有关加密受 EKM 保护的备份的示例，请参阅[使用 Azure 密钥保管库的可扩展密钥管理 (SQL Server)](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b4548-117">For an example of encrypting a backup protected by an EKM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
### <a name="backup-to-azure-storage-with-encryption"></a><span data-ttu-id="b4548-118">备份到 Azure 存储并加密</span><span class="sxs-lookup"><span data-stu-id="b4548-118">Backup to Azure Storage with Encryption</span></span>  
 <span data-ttu-id="b4548-119">如果使用“SQL Server 备份到 URL”  选项向 Azure 存储创建备份，则加密步骤相同，但必须使用 URL 作为目标，并使用 SQL 凭据向 Azure 存储进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b4548-119">If you are creating a backup to Azure storage using the **SQL Server Backup to URL** option, the encryption steps are the same, but you must use URL as the destination and a SQL Credential to authenticate to the Azure storage.</span></span> <span data-ttu-id="b4548-120">如果要配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 加密选项，请参阅[设置 SQL Server 托管备份到 azure](enable-sql-server-managed-backup-to-microsoft-azure.md) ，并为[可用性组设置 SQL Server 托管备份到 azure](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="b4548-120">If you want to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with encryption options, see [Setting up SQL Server Managed Backup to Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 <span data-ttu-id="b4548-121">**先决条件：**</span><span class="sxs-lookup"><span data-stu-id="b4548-121">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="b4548-122">Windows 存储帐户和容器。</span><span class="sxs-lookup"><span data-stu-id="b4548-122">A windows storage account and a container.</span></span> <span data-ttu-id="b4548-123">有关详细信息，请参阅</span><span class="sxs-lookup"><span data-stu-id="b4548-123">For more information, see.</span></span> <span data-ttu-id="b4548-124">[第 1 课：创建 Azure 存储对象](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="b4548-124">[Lesson 1: Create Azure Storage Objects](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).</span></span>  
  
-   <span data-ttu-id="b4548-125">master 数据库的数据库主密钥以及 SQL Server 实例上的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="b4548-125">A Database Master Key for the master database, and a certificate or asymmetric key  on the instance of SQL Server.</span></span> <span data-ttu-id="b4548-126">有关加密要求和权限，请参阅 [Backup Encryption](backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="b4548-126">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
1.  <span data-ttu-id="b4548-127">**创建 SQL Server 凭据：** 若要创建 SQL Server 凭据，请连接到数据库引擎、打开新查询窗口并复制和粘贴到下例，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="b4548-127">**Create SQL Server Credential:** To create a SQL Server credential, connect to the Database Engine, open a new query window, and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  <span data-ttu-id="b4548-128">**创建数据库主密钥：** 选择密码来对存储于该数据库中的主密钥副本进行加密。</span><span class="sxs-lookup"><span data-stu-id="b4548-128">**Create a Database Master Key:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="b4548-129">连接到数据库引擎，启动新查询窗口并复制和粘贴下例，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b4548-129">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="b4548-130">**创建备份证书：** 在 master 数据库中创建备份证书。</span><span class="sxs-lookup"><span data-stu-id="b4548-130">**Create a Backup Certificate:** Create a Backup Certificate in the master database.</span></span> <span data-ttu-id="b4548-131">将下例复制并粘贴到查询窗口中，然后单击 **“执行”**</span><span class="sxs-lookup"><span data-stu-id="b4548-131">Copy and paste the following example in the query window and click **Execute**</span></span>  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  <span data-ttu-id="b4548-132">**备份数据库：** 指定要使用的加密算法和证书。</span><span class="sxs-lookup"><span data-stu-id="b4548-132">**Backup the database:** Specify the encryption algorithm and the certificate to use.</span></span> <span data-ttu-id="b4548-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="b4548-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
