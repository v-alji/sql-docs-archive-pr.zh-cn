---
title: 第 9 课。 从 Azure 存储还原数据库 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5e7c2350bb2a9b1f8c31da8e094459b5bc8ccd90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590779"
---
# <a name="lesson-9-restore-a-database-from-azure-storage"></a><span data-ttu-id="2bc22-103">第 9 课。</span><span class="sxs-lookup"><span data-stu-id="2bc22-103">Lesson 9.</span></span> <span data-ttu-id="2bc22-104">从 Azure 存储还原数据库</span><span class="sxs-lookup"><span data-stu-id="2bc22-104">Restore a database from Azure Storage</span></span>
  <span data-ttu-id="2bc22-105">在本课中，您将学习如何将数据库备份文件从 Azure 存储还原到数据库（驻留在本地或 Azure 中的虚拟机上）。</span><span class="sxs-lookup"><span data-stu-id="2bc22-105">In this lesson, you will learn how to restore a database backup file from Azure Storage to a database, which either resides on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="2bc22-106">不需要学完第 4、5、6、7 和 8 课即可听懂本课。</span><span class="sxs-lookup"><span data-stu-id="2bc22-106">To follow this lesson, you do not need to complete Lesson 4, 5, 6, 7, and 8.</span></span>  
  
 <span data-ttu-id="2bc22-107">本课假定您已完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="2bc22-107">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="2bc22-108">已在源计算机中创建了数据库。</span><span class="sxs-lookup"><span data-stu-id="2bc22-108">You have created a database in the source machine.</span></span>  
  
-   <span data-ttu-id="2bc22-109">已通过使用 "[使用 Azure Blob 存储服务进行备份和还原 SQL Server](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) " 功能在 azure 存储中创建数据库 ( .bak) 的备份。</span><span class="sxs-lookup"><span data-stu-id="2bc22-109">You have created a backup of your database (.bak) in Azure Storage by using the [SQL Server Backup and Restore with Azure Blob Storage Service](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) feature.</span></span> <span data-ttu-id="2bc22-110">注意，需要在此步骤中创建另一个 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="2bc22-110">Note that you will need to create another SQL Server Credential in this step.</span></span> <span data-ttu-id="2bc22-111">此凭据使用存储帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="2bc22-111">This credential uses storage account keys.</span></span>  
  
-   <span data-ttu-id="2bc22-112">你有 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="2bc22-112">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="2bc22-113">在 Azure 存储帐户下创建了容器。</span><span class="sxs-lookup"><span data-stu-id="2bc22-113">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="2bc22-114">已在容器上创建了具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="2bc22-114">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="2bc22-115">还生成了 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="2bc22-115">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="2bc22-116">已在计算机上为 Azure 存储集成功能创建了 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="2bc22-116">You have created a SQL Server credential on your machine for Azure Storage Integration feature.</span></span> <span data-ttu-id="2bc22-117">注意，此凭据需要共享访问签名 (SAS) 密钥。</span><span class="sxs-lookup"><span data-stu-id="2bc22-117">Note that this credential requires a Shared Access Signature (SAS) key.</span></span>  
  
 <span data-ttu-id="2bc22-118">若要从 Azure 存储还原数据库，可以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="2bc22-118">To restore a database from Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="2bc22-119">启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="2bc22-119">Start SQL Server Management Studio.</span></span> <span data-ttu-id="2bc22-120">连接到默认实例。</span><span class="sxs-lookup"><span data-stu-id="2bc22-120">Connect to the default instance.</span></span>  
  
2.  <span data-ttu-id="2bc22-121">单击 "标准" 工具栏上的 "**新建查询**"。</span><span class="sxs-lookup"><span data-stu-id="2bc22-121">Click **New Query** on the Standard Toolbar.</span></span>  
  
3.  <span data-ttu-id="2bc22-122">复制以下完整脚本并将其粘贴到查询窗口。</span><span class="sxs-lookup"><span data-stu-id="2bc22-122">Copy and paste the following complete script to the query window.</span></span> <span data-ttu-id="2bc22-123">根据需要修改脚本。</span><span class="sxs-lookup"><span data-stu-id="2bc22-123">Modify the script as needed.</span></span>  
  
     <span data-ttu-id="2bc22-124">**注意：** 运行 `RESTORE` 语句，将 Azure 存储中的数据库备份 ( .bak) 还原到另一台计算机中的数据库实例。</span><span class="sxs-lookup"><span data-stu-id="2bc22-124">**Note:** You run the `RESTORE` statement to restore the database backup (.bak) in Azure Storage to a database instance in another machine.</span></span>  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 <span data-ttu-id="2bc22-125">**教程结束：在 Azure 存储服务中 SQL Server 数据文件**</span><span class="sxs-lookup"><span data-stu-id="2bc22-125">**End of Tutorial: SQL Server Data Files in Azure Storage service**</span></span>  
  
  
