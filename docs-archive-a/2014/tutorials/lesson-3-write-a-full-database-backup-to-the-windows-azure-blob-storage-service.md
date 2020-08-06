---
title: 第3课：将完整数据库备份写入到 Azure Blob 存储服务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 17e7e6b608d248a48cde52f1107bb910f06d64ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682470"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="1824f-102">第 3 课：将完整数据库备份写入到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="1824f-102">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>
  <span data-ttu-id="1824f-103">本课演示如何使用 tsql 语句执行到 Azure Blob 存储服务的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="1824f-103">This lesson demonstrates the use of tsql statement to perform a full database backup to Azure Blob storage service.</span></span>  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="1824f-104">对 Azure Blob 存储服务执行完整的数据库备份</span><span class="sxs-lookup"><span data-stu-id="1824f-104">Perform a Full Database Backup to the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="1824f-105">若要创建完整数据库备份，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1824f-105">To create a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="1824f-106">连接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1824f-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="1824f-107">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1824f-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="1824f-108">在标准菜单栏上，单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="1824f-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="1824f-109">将以下示例复制并粘贴到查询窗口中，根据需要进行修改，然后单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="1824f-109">Copy and paste the following example into the query window, modify as needed, and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  <span data-ttu-id="1824f-110">在对象资源管理器中，连接到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="1824f-110">In the object explorer, connect to Azure Storage.</span></span> <span data-ttu-id="1824f-111">通过浏览找到容器和新创建的备份文件。</span><span class="sxs-lookup"><span data-stu-id="1824f-111">Browse to find the container and the newly created backup files.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="1824f-112">下一课</span><span class="sxs-lookup"><span data-stu-id="1824f-112">Next Lesson</span></span>  
 <span data-ttu-id="1824f-113">[第4课：从完整数据库备份执行还原](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="1824f-113">[Lesson 4: Perform a Restore From a Full Database Backup](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).</span></span>  
  
  
