---
title: 第3课：创建 SQL Server 凭据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 808438e544e3beb18b2e2afa9c399b5666277483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692919"
---
# <a name="lesson-3-create-a-sql-server-credential"></a><span data-ttu-id="76c80-102">第 3 课：创建 SQL Server 凭据</span><span class="sxs-lookup"><span data-stu-id="76c80-102">Lesson 3: Create a SQL Server Credential</span></span>
  <span data-ttu-id="76c80-103">在本课中，您将创建凭据以存储用于访问 Azure 存储帐户的安全信息。</span><span class="sxs-lookup"><span data-stu-id="76c80-103">In this lesson, you will create a credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="76c80-104">SQL Server 凭据是一个对象，用于存储连接到 SQL Server 以外资源所需的身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="76c80-104">A SQL Server credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span> <span data-ttu-id="76c80-105">凭据中存储了存储容器的 URI 路径以及共享的访问签名密钥值。</span><span class="sxs-lookup"><span data-stu-id="76c80-105">The credential stores the URI path of the storage container and the shared access signature key values.</span></span> <span data-ttu-id="76c80-106">对于数据或日志文件使用的每个存储容器，都必须创建一个 SQL Server 凭据，其名称与容器路径相同。</span><span class="sxs-lookup"><span data-stu-id="76c80-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span>  
  
 <span data-ttu-id="76c80-107">有关凭据的一般信息，请参阅[凭据 &#40;数据库引擎&#41;](security/authentication-access/credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="76c80-107">For general information about credentials, see [Credentials &#40;Database Engine&#41;](security/authentication-access/credentials-database-engine.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="76c80-108">创建下述 SQL Server 凭据的要求特定于[Azure 功能中的 SQL Server 数据文件](databases/sql-server-data-files-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="76c80-108">The requirements for creating a SQL Server credential described below are specific to the [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md) feature.</span></span> <span data-ttu-id="76c80-109">有关在 Azure 存储中创建备份过程的凭据的信息，请参阅 [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md)。</span><span class="sxs-lookup"><span data-stu-id="76c80-109">For information on creating credentials for backup processes in Azure storage, see [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
 <span data-ttu-id="76c80-110">若要创建 SQL Server 凭据，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="76c80-110">To create a SQL Server Credential, follow these steps:</span></span>  
  
1.  <span data-ttu-id="76c80-111">连接到 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="76c80-111">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="76c80-112">在对象资源管理器中，连接到所安装的数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="76c80-112">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="76c80-113">在“标准”工具栏上，单击“新建查询”。</span><span class="sxs-lookup"><span data-stu-id="76c80-113">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="76c80-114">将以下示例复制并粘贴到查询窗口中，并根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="76c80-114">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="76c80-115">以下语句将创建一个 SQL Server 凭据来存储存储容器的共享访问证书。</span><span class="sxs-lookup"><span data-stu-id="76c80-115">The following statement will create a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     <span data-ttu-id="76c80-116">有关详细信息，请参阅 SQL Server 联机丛书中的[CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="76c80-116">For detailed information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) in SQL Server Books Online.</span></span>  
  
5.  <span data-ttu-id="76c80-117">若要查看所有可用的凭据，可在查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="76c80-117">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     <span data-ttu-id="76c80-118">有关 sys.databases 的详细信息，请参阅 SQL Server 联机丛书中的[sys.databases &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="76c80-118">For more information on sys.credentials, see [sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="76c80-119">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="76c80-119">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="76c80-120">第 4 课：在 Azure 存储中创建数据库</span><span class="sxs-lookup"><span data-stu-id="76c80-120">Lesson 4: Create a database in Azure Storage</span></span>](lesson-3-database-backup-to-url.md)  
  
  
