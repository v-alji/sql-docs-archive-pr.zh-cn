---
title: 第4课：从完整数据库备份执行还原 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9906ea14c2f76a49644a8f76fbd894adf8b9d500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581065"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a><span data-ttu-id="b7a64-102">第 4 课：从完整数据库备份执行还原</span><span class="sxs-lookup"><span data-stu-id="b7a64-102">Lesson 4: Perform a Restore From a Full Database Backup</span></span>
  <span data-ttu-id="b7a64-103">本课演示如何使用 tsql 语句从上一课所创建的完整数据库备份中执行还原。</span><span class="sxs-lookup"><span data-stu-id="b7a64-103">This lesson demonstrates the use of a tsql statement to perform a restore from a full database backup created in the previous lesson.</span></span>  
  
## <a name="perform-a-restore-of-a-database-backup"></a><span data-ttu-id="b7a64-104">执行数据库备份的还原</span><span class="sxs-lookup"><span data-stu-id="b7a64-104">Perform a Restore of a Database Backup</span></span>  
 <span data-ttu-id="b7a64-105">若要还原完整数据库备份，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="b7a64-105">To restore a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="b7a64-106">连接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b7a64-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b7a64-107">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b7a64-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="b7a64-108">在标准菜单栏上，单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="b7a64-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="b7a64-109">将以下示例复制并粘贴到查询窗口中，并根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="b7a64-109">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  <span data-ttu-id="b7a64-110">验证 T-sql 语句，然后单击 "**执行**"</span><span class="sxs-lookup"><span data-stu-id="b7a64-110">Verify the T-SQL statement and click **Execute**</span></span>  
  
### <a name="return-to-tutorials-portal"></a><span data-ttu-id="b7a64-111">返回到教程入门</span><span class="sxs-lookup"><span data-stu-id="b7a64-111">Return to Tutorials Portal</span></span>  
 <span data-ttu-id="b7a64-112">[教程： SQL Server 备份和还原到 Azure Blob 存储服务](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a64-112">[Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).</span></span>  
  
  
