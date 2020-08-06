---
title: 第2课：创建 SQL Server 凭据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e8b13c8d4d9e5937064cef5503ec64bfd6e4a2d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694190"
---
# <a name="lesson-2-create-a-sql-server-credential"></a><span data-ttu-id="93bfd-102">第 2 课：创建 SQL Server 凭据</span><span class="sxs-lookup"><span data-stu-id="93bfd-102">Lesson 2: Create a SQL Server Credential</span></span>
  <span data-ttu-id="93bfd-103">**凭据：** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 凭据是用于存储连接到 SQL Server 外部资源所需的身份验证信息的对象。</span><span class="sxs-lookup"><span data-stu-id="93bfd-103">**Credential:** A [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="93bfd-104">在这里， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 备份和还原进程使用凭据对 Azure Blob 存储服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="93bfd-104">Here, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="93bfd-105">凭据存储着存储帐户的名称和存储帐户的 **access key** 值。</span><span class="sxs-lookup"><span data-stu-id="93bfd-105">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="93bfd-106">创建凭据后，在发出 BACKUP/RESTORE 命令时必须在 WITH CREDENTIAL 选项中指定它。</span><span class="sxs-lookup"><span data-stu-id="93bfd-106">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="93bfd-107">有关如何查看、复制或重新生成存储帐户**访问密钥**的详细信息，请参阅[存储帐户访问密钥](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)。</span><span class="sxs-lookup"><span data-stu-id="93bfd-107">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="93bfd-108">有关凭据的一般信息，请参阅[凭据](../relational-databases/security/authentication-access/credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="93bfd-108">For general information about credentials, see [Credentials](../relational-databases/security/authentication-access/credentials-database-engine.md).</span></span>  
  
 <span data-ttu-id="93bfd-109">有关使用凭据的其他示例的信息，请参阅[创建 SQL Server 代理代理](../ssms/agent/create-a-sql-server-agent-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="93bfd-109">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93bfd-110">创建如下所述的 SQL Server 凭据的要求特定于 SQL Server 备份过程 ([SQL Server 备份到 URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)，以及[SQL Server 托管备份到 Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)) 。</span><span class="sxs-lookup"><span data-stu-id="93bfd-110">The requirements for creating a SQL Server credential described below are specific to SQL Server backup processes ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), and [SQL Server Managed  Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)).</span></span> <span data-ttu-id="93bfd-111">在访问 Azure 存储来读写备份时，SQL Server 使用存储账户名称和访问密钥信息。</span><span class="sxs-lookup"><span data-stu-id="93bfd-111">SQL Server, when accessing Azure storage to write or read backups uses the storage account name and access key information.</span></span>  <span data-ttu-id="93bfd-112">有关为 Azure 存储中的存储数据库文件创建凭据的详细信息，请参阅 [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)</span><span class="sxs-lookup"><span data-stu-id="93bfd-112">For more information on creating credentials for storing database files in Azure storage, see [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)</span></span>  
  
## <a name="create-a-sql-server-credential"></a><span data-ttu-id="93bfd-113">创建 SQL Server 凭据</span><span class="sxs-lookup"><span data-stu-id="93bfd-113">Create a SQL Server Credential</span></span>  
 <span data-ttu-id="93bfd-114">若要创建 SQL Server 凭据，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="93bfd-114">To create a SQL Server Credential, use the following steps:</span></span>  
  
1.  <span data-ttu-id="93bfd-115">连接到 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="93bfd-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="93bfd-116">在对象资源管理器中，连接到已安装 AdventureWorks2012 数据库的数据库引擎实例，或使用计划用于本教程的自己的数据库。</span><span class="sxs-lookup"><span data-stu-id="93bfd-116">In Object Explorer, connect to the instance of Database Engine that has AdventureWorks2012 database installed, or use your own database you plan to use for this tutorial.</span></span>  
  
3.  <span data-ttu-id="93bfd-117">在 **“标准”** 工具栏上，单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="93bfd-117">On the **Standard** tool bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="93bfd-118">将以下示例复制并粘贴到查询窗口中，并根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="93bfd-118">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     <span data-ttu-id="93bfd-119">![将存储帐户映射到 sql 凭据](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "将存储帐户映射到 sql 凭据")</span><span class="sxs-lookup"><span data-stu-id="93bfd-119">![mapping storage account to sql credentials](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
5.  <span data-ttu-id="93bfd-120">验证 T-SQL 语句，然后单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="93bfd-120">Verify the T-SQL statement and click **Execute**.</span></span>  
  
 <span data-ttu-id="93bfd-121">有关备份概念和要求的 Azure Blob 存储服务的详细信息，请参阅[SQL Server Azure Blob 存储服务的备份和还原](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="93bfd-121">For more information about the Azure Blob storage service for backup concepts and requirements, see [SQL Server Backup and Restore with Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="93bfd-122">下一课</span><span class="sxs-lookup"><span data-stu-id="93bfd-122">Next Lesson</span></span>  
 <span data-ttu-id="93bfd-123">[第3课：将完整数据库备份写入到 Azure Blob 存储服务](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="93bfd-123">[Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).</span></span>  
  
  
