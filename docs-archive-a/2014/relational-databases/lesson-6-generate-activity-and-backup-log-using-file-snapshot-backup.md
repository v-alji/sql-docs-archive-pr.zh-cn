---
title: 第7课：将数据文件移到 Azure 存储 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 753863d7b8b8d8fa554f1579bee6837c525efd9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589067"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a><span data-ttu-id="5b379-102">第 7 课：将数据文件移动到 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="5b379-102">Lesson 7: Move your data files to Azure Storage</span></span>
  <span data-ttu-id="5b379-103">在本课程中，您将学习如何将数据文件移到 Azure 存储 (，而不是) SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="5b379-103">In this lesson, you will learn how to move your data files to Azure Storage (but not your SQL Server instance).</span></span> <span data-ttu-id="5b379-104">不需要学完第 4、5 和 6 课即可听懂本课。</span><span class="sxs-lookup"><span data-stu-id="5b379-104">To follow this lesson, you do not need to complete Lesson 4, 5, and 6.</span></span>  
  
 <span data-ttu-id="5b379-105">若要将数据文件移到 Azure 存储，可以使用 `ALTER DATABASE` 语句，因为它可帮助更改数据文件的位置。</span><span class="sxs-lookup"><span data-stu-id="5b379-105">To move your data files to Azure Storage, you can use the `ALTER DATABASE` statement as it helps to change the location of the data files.</span></span>  
  
 <span data-ttu-id="5b379-106">本课假定您已完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="5b379-106">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="5b379-107">你有 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="5b379-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="5b379-108">在 Azure 存储帐户下创建了容器。</span><span class="sxs-lookup"><span data-stu-id="5b379-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="5b379-109">已在容器上创建了具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="5b379-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="5b379-110">还生成了 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="5b379-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="5b379-111">已在源计算机上创建了 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="5b379-111">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="5b379-112">接下来，使用以下步骤将数据文件移到 Azure 存储：</span><span class="sxs-lookup"><span data-stu-id="5b379-112">Next, use the following steps to move your data files to Azure Storage:</span></span>  
  
1.  <span data-ttu-id="5b379-113">首先，在源计算机中创建测试数据库，然后向其添加一些数据。</span><span class="sxs-lookup"><span data-stu-id="5b379-113">First, create a test database in the source machine and add some data to it.</span></span>  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  <span data-ttu-id="5b379-114">运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="5b379-114">Run the following code:</span></span>  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  <span data-ttu-id="5b379-115">当你运行此操作时，你将看到以下消息： "文件" Testdb1alter ' "已在系统目录中修改。</span><span class="sxs-lookup"><span data-stu-id="5b379-115">When you run this, you will see this message: "The file "TestDB1Alter" has been modified in the system catalog.</span></span> <span data-ttu-id="5b379-116">新路径将在数据库下次启动时使用。 "</span><span class="sxs-lookup"><span data-stu-id="5b379-116">The new path will be used the next time the database is started."</span></span>  
  
4.  <span data-ttu-id="5b379-117">然后，将数据库设为脱机状态。</span><span class="sxs-lookup"><span data-stu-id="5b379-117">Then, set the database offline.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  <span data-ttu-id="5b379-118">现在，需要使用以下方法之一将数据文件复制到 Azure 存储： [AzCopy 工具](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs)、 [Put 页面](https://msdn.microsoft.com/library/azure/ee691975.aspx)、[存储客户端库参考](https://msdn.microsoft.com/library/azure/dn261237.aspx)或第三方存储资源管理器工具。</span><span class="sxs-lookup"><span data-stu-id="5b379-118">Now, you need to copy the data files to Azure Storage by using one of the following methods: [AzCopy Tool](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx), or a third-party storage explorer tool.</span></span>  
  
     <span data-ttu-id="5b379-119">**重要提示：** 使用此新增强功能时，请始终确保创建的是页 Blob 而非块 Blob。</span><span class="sxs-lookup"><span data-stu-id="5b379-119">**Important:** When using this new enhancement, always make sure that you create a page blob not a block blob.</span></span>  
  
6.  <span data-ttu-id="5b379-120">然后，将数据库设为联机状态。</span><span class="sxs-lookup"><span data-stu-id="5b379-120">Then, set the database online.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 <span data-ttu-id="5b379-121">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="5b379-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="5b379-122">第8课。将数据库还原到 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="5b379-122">Lesson 8. Restore a database to Azure Storage</span></span>](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
