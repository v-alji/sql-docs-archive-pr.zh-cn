---
title: 第 8 课. 将数据库还原到 Azure 存储 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: adec725d1b519fb67560dc572823ba0a116aaa54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590780"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a><span data-ttu-id="8adb0-103">第 8 课.</span><span class="sxs-lookup"><span data-stu-id="8adb0-103">Lesson 8.</span></span> <span data-ttu-id="8adb0-104">将数据库还原到 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="8adb0-104">Restore a database to Azure Storage</span></span>
  <span data-ttu-id="8adb0-105">在本课中，您将学习如何在本地创建备份文件，然后将其还原到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="8adb0-105">In this lesson, you will learn how to create a backup file locally and then restore it to Azure Storage.</span></span> <span data-ttu-id="8adb0-106">请注意，你可以在本地或 Azure 中的虚拟机上使用数据库。</span><span class="sxs-lookup"><span data-stu-id="8adb0-106">Note that you can have your database either on either on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="8adb0-107">不需要学完第 4、5、6 和 7 课即可听懂本课。</span><span class="sxs-lookup"><span data-stu-id="8adb0-107">To follow this lesson, you do not need to complete Lesson 4, 5, 6, and 7.</span></span>  
  
 <span data-ttu-id="8adb0-108">本课假定您已完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="8adb0-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="8adb0-109">你有 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="8adb0-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="8adb0-110">在 Azure 存储帐户下创建了容器。</span><span class="sxs-lookup"><span data-stu-id="8adb0-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="8adb0-111">已在容器上创建了具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="8adb0-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="8adb0-112">还生成了 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="8adb0-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="8adb0-113">已根据共享访问签名在源计算机上创建了 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="8adb0-113">You have created a SQL Server credential on the source machine based on Shared Access Signature.</span></span>  
  
-   <span data-ttu-id="8adb0-114">已在源计算机中创建了数据库。</span><span class="sxs-lookup"><span data-stu-id="8adb0-114">You have created a database in the source machine.</span></span>  
  
 <span data-ttu-id="8adb0-115">若要将数据库还原到 Azure 存储，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="8adb0-115">To restore a database to Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="8adb0-116">在源计算机中，启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="8adb0-116">In the source machine, start SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="8adb0-117">连接到新创建的数据库时，打开查询窗口。</span><span class="sxs-lookup"><span data-stu-id="8adb0-117">When connected to the newly created database, open the query window.</span></span> <span data-ttu-id="8adb0-118">运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="8adb0-118">Run the following statement:</span></span>  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  <span data-ttu-id="8adb0-119">接下来，将以下语句复制到查询窗口中并运行这些语句。</span><span class="sxs-lookup"><span data-stu-id="8adb0-119">Next, copy and run the following statements in the Query window.</span></span>  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     <span data-ttu-id="8adb0-120">在此步骤结束时，您的容器应在管理门户上列出数据 (.mdf) 和 (.ldf) 文件。</span><span class="sxs-lookup"><span data-stu-id="8adb0-120">At the end of this step, your container should list data (.mdf) and (.ldf) files on the Management Portal.</span></span>  
  
 <span data-ttu-id="8adb0-121">若要使用 SQL Server Management Studio 用户界面还原包含指向 Azure 存储的数据文件和日志文件的数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="8adb0-121">To restore a database with data and log files pointing to Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="8adb0-122">在**对象资源管理器**中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="8adb0-122">In **Object Explorer**, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="8adb0-123">展开 "**数据库**"，然后选择数据库。</span><span class="sxs-lookup"><span data-stu-id="8adb0-123">Expand **Databases**, and, select your database.</span></span>  
  
3.  <span data-ttu-id="8adb0-124">右键单击数据库，指向“任务”  ，再单击“还原”  。</span><span class="sxs-lookup"><span data-stu-id="8adb0-124">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="8adb0-125">在 "**常规**" 页上的 "**还原**源" 部分中，单击 "**源**设备"。</span><span class="sxs-lookup"><span data-stu-id="8adb0-125">On the **General** page, in the **Restore** source section, click **Source** device.</span></span>  
  
5.  <span data-ttu-id="8adb0-126">单击 "**源**设备" 文本框的浏览按钮，这将打开 "**选择备份设备**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8adb0-126">Click the browse button for the **Source** device text box, which opens the **Select Backup Devices** dialog box.</span></span>  
  
6.  <span data-ttu-id="8adb0-127">在 "备份介质" 文本框中，选择 "**文件**"，然后单击 "**添加**" 按钮，以查找备份 ( .bak) 文件。</span><span class="sxs-lookup"><span data-stu-id="8adb0-127">In the Backup media text box, select **File**, and click the **Add** button to locate the backup (.bak) file.</span></span> <span data-ttu-id="8adb0-128">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="8adb0-128">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="8adb0-129">在第一页上单击 "**文件**"。</span><span class="sxs-lookup"><span data-stu-id="8adb0-129">Click **Files** on the first page.</span></span>  
  
8.  <span data-ttu-id="8adb0-130">在 "将**数据库文件还原**为" 部分中的 "**还原为**" 字段下，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="8adb0-130">In the **Restore Database Files** as section, under **Restore As** field, type the followings:</span></span>  
  
     <span data-ttu-id="8adb0-131">对于数据文件，键入： `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf` 。</span><span class="sxs-lookup"><span data-stu-id="8adb0-131">For data file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`.</span></span> <span data-ttu-id="8adb0-132">对于日志文件，键入： `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf` 。</span><span class="sxs-lookup"><span data-stu-id="8adb0-132">For log file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.</span></span>  
  
     <span data-ttu-id="8adb0-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="8adb0-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span></span>  
  
9. <span data-ttu-id="8adb0-134">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="8adb0-134">Click **OK**.</span></span>  
  
 <span data-ttu-id="8adb0-135">还原完后，登录到管理门户。</span><span class="sxs-lookup"><span data-stu-id="8adb0-135">When the restore is done, log in to the Management Portal.</span></span> <span data-ttu-id="8adb0-136">应该能在容器中看到 .mdf 和 .ldf 文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8adb0-136">You should be able to see the .mdf and .ldf files in the container as follows:</span></span>  
  
 <span data-ttu-id="8adb0-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="8adb0-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="8adb0-138">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="8adb0-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="8adb0-139">第9课：从 Azure 存储还原数据库</span><span class="sxs-lookup"><span data-stu-id="8adb0-139">Lesson 9. Restore a database from Azure Storage</span></span>](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
