---
title: 第6课：将数据库从本地源计算机迁移到 Azure 中的目标计算机 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9af8a260493561f9728d1677b7667bd3f36cb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589068"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-azure"></a><span data-ttu-id="ebf8e-102">第 6 课：将数据库从本地源计算机迁移至 Azure 中的目标计算机</span><span class="sxs-lookup"><span data-stu-id="ebf8e-102">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>
  <span data-ttu-id="ebf8e-103">本课程假定你已有另一个 SQL Server，该可能驻留在其他本地计算机或 Azure 中的虚拟机中。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-103">This lesson assumes that you already have another SQL Server, which might reside in another on-premises computer or in a virtual machine in Azure.</span></span> <span data-ttu-id="ebf8e-104">有关如何在 Azure 中创建 SQL Server 虚拟机的信息，请参阅在[azure 上预配 SQL Server 虚拟机](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/)。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-104">For information on how to create a SQL Server virtual machine in Azure, see [Provisioning a SQL Server Virtual Machine on Azure](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/).</span></span> <span data-ttu-id="ebf8e-105">在 Azure 中预配 SQL Server 虚拟机后，请确保可以通过其他计算机中的 SQL Server Management Studio 连接到此虚拟机中 SQL Server 的实例。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-105">After provisioning a SQL Server virtual machine in Azure, make sure that you can connect to an instance of SQL Server in this virtual machine via SQL Server Management Studio in another computer.</span></span>  
  
 <span data-ttu-id="ebf8e-106">本课还假定您已完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-106">This lesson also assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="ebf8e-107">你有 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="ebf8e-108">在 Azure 存储帐户下创建了容器。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="ebf8e-109">已在容器上创建了具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="ebf8e-110">还生成了 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="ebf8e-111">已在源计算机上创建了 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-111">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="ebf8e-112">你已在 Azure 中创建了目标 SQL Server 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-112">You already have created a destination SQL Server virtual machine in Azure.</span></span> <span data-ttu-id="ebf8e-113">建议通过选择包含 SQL Server 2014 的平台映像创建该虚拟机。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-113">We recommend that you create it by selecting a platform image that includes SQL Server 2014.</span></span>  
  
 <span data-ttu-id="ebf8e-114">若要将数据库从本地 SQL Server 迁移到 Azure 中的其他虚拟机，可以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-114">To migrate a database from SQL Server on-premises to another virtual machine in Azure, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="ebf8e-115">在源计算机（本教程中为本地计算机）中，在 SQL Server Management Studio 中打开查询窗口。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-115">In the source machine (which is an on-premises computer in this tutorial), open a query window in SQL Server Management Studio.</span></span> <span data-ttu-id="ebf8e-116">通过执行以下语句，分离数据库以将其移至另一个计算机：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-116">Detach your database to move it to another machine by executing these statements:</span></span>  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  <span data-ttu-id="ebf8e-117">如果需要将数据库传输到目标计算机，则首先必须准备该数据库。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-117">If you need to transfer a database to a destination machine, first you must prepare it.</span></span> <span data-ttu-id="ebf8e-118">若要准备目标计算机，首先需要在目标计算机中创建一个 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-118">To prepare your destination machine, first you need to create a SQL Server credential in the destination machine.</span></span> <span data-ttu-id="ebf8e-119">如果这是加密数据库，则还需要将源计算机中的证书导入到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-119">If it is an encrypted database, you need to import the certificate from the source machine to the destination machine as well.</span></span>  
  
    1.  <span data-ttu-id="ebf8e-120">若要在目标计算机中创建 SQL Server 凭据，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-120">To create a SQL Server Credential in the destination machine, follow these steps:</span></span>  
  
        1.  <span data-ttu-id="ebf8e-121">在源计算机中通过 SQL Server Management Studio 连接到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-121">Connect to the destination machine via SQL Server Management Studio in your source computer.</span></span>  <span data-ttu-id="ebf8e-122">或者，直接在目标计算机中启动 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-122">Or, start SQL Server Management Studio in your destination computer directly.</span></span>  
  
        2.  <span data-ttu-id="ebf8e-123">在 “标准” 工具栏上，单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-123">On the Standard tool bar, click **New Query**.</span></span>  
  
        3.  <span data-ttu-id="ebf8e-124">将以下示例复制并粘贴到查询窗口中，并根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-124">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="ebf8e-125">以下语句将创建一个 SQL Server 凭据来存储存储容器的共享访问证书。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-125">The following statement creates a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
            ```sql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  <span data-ttu-id="ebf8e-126">若要查看所有可用的凭据，可在查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-126">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
            ```sql  
            SELECT * from sys.credentials   
            ```  
  
        5.  <span data-ttu-id="ebf8e-127">连接到目标服务器后，打开查询窗口并运行：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-127">When connected to the destination server, open query window, and run:</span></span>  
  
            ```sql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             <span data-ttu-id="ebf8e-128">此步骤结束时，目标计算机已导入从源计算机备份的加密证书。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-128">At the end of this step, the destination machine has imported the encryption certificate that was backed up from the source machine.</span></span> <span data-ttu-id="ebf8e-129">接下来，可将数据文件附加到目标计算机中。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-129">Next, you can attach the data files in the destination machine.</span></span>  
  
    2.  <span data-ttu-id="ebf8e-130">然后，使用 FOR ATTACH 选项创建一个数据库，其中包含指向 Azure 存储中现有文件的数据和日志文件。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-130">Then, create a database with data and log files pointing to the existing files in Azure Storage by using FOR ATTACH option.</span></span> <span data-ttu-id="ebf8e-131">在查询窗口中，运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-131">In the query window, run the following statement:</span></span>  
  
        ```sql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  <span data-ttu-id="ebf8e-132">在对象资源管理器中，单击“数据库”，右键单击“刷新”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-132">On the Object Explorer, click Databases, right-click Refresh.</span></span> <span data-ttu-id="ebf8e-133">应可看到列出新创建的数据库 TestDB1onDest。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-133">You should be able to see the newly created database TestDB1onDest listed.</span></span>  
  
    4.  <span data-ttu-id="ebf8e-134">接下来，在查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-134">Next, run the following statement in the query window:</span></span>  
  
        ```sql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         <span data-ttu-id="ebf8e-135">随后应列出在第 4 课中输入的所有数据。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-135">This should list all the data you entered in Lesson 4.</span></span>  
  
 <span data-ttu-id="ebf8e-136">注意，加密的数据库传输到另一个计算实例，但未移动数据。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-136">Note that the encrypted database was transferred to another compute instance with no data movement.</span></span>  
  
 <span data-ttu-id="ebf8e-137">若要使用 SQL Server Management Studio 用户界面创建包含指向 Azure 存储中现有文件的数据和日志文件的数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-137">To create a database with data and log files pointing to the existing files in Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="ebf8e-138">在“对象资源管理器”中，连接到一个 SQL Server 数据库引擎实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-138">In **Object Explorer**, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ebf8e-139">右键单击“数据库”，然后单击“新建数据库”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-139">Right-click **Databases**, and then click **New Database**.</span></span> <span data-ttu-id="ebf8e-140">然后，右键单击“TestDB1”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-140">Then, right-click TestDB1.</span></span> <span data-ttu-id="ebf8e-141">单击“任务”，然后单击“分离”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-141">Click Tasks, and then click Detach.</span></span> <span data-ttu-id="ebf8e-142">在“分离”对话框窗口中，选中“删除连接”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-142">In the Detach dialog window, check Drop Connections.</span></span> <span data-ttu-id="ebf8e-143">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="ebf8e-144">连接到目标计算机，该计算机具有 SQL Server 2014 CTP2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-144">Connect to the destination machine, which has SQL Server 2014 CTP2 or later.</span></span> <span data-ttu-id="ebf8e-145">若要准备目标计算机，需要在目标计算机中创建一个 SQL Server 凭据，使其指向将 TestDB1 放入的同一容器。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-145">To prepare your destination machine, you need to create a SQL Server credential in the destination machine to point to the same container that you put TestDB1 in.</span></span> <span data-ttu-id="ebf8e-146">如果要在同一个计算机上重新附加，则不需要创建另一个凭据。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-146">If you are going to re-attach in the same computer, you do not need to create another credential.</span></span>  
  
4.  <span data-ttu-id="ebf8e-147">在**对象资源管理器**中，右键单击 "**数据库**"，然后单击 "**附加**"。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-147">In **Object Explorer**, right-click **Databases** and click **Attach**.</span></span>  
  
5.  <span data-ttu-id="ebf8e-148">在 "**附加数据库**" 对话框中，若要指定要附加的数据库，请单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-148">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="ebf8e-149">在 "**定位数据库文件**" 对话框窗口中：</span><span class="sxs-lookup"><span data-stu-id="ebf8e-149">In the **Locate Database Files** dialog window:</span></span>  
  
     <span data-ttu-id="ebf8e-150">对于 "数据库数据文件位置"，键入： `https://teststorageaccnt.blob.core.windows.net/testcontainer/` 。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-150">For Database Data File Location, type: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span>  
  
     <span data-ttu-id="ebf8e-151">对于 "文件名"，请键入： `TestDB1Data.mdf` 。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-151">For File name, type: `TestDB1Data.mdf`.</span></span>  
  
6.  <span data-ttu-id="ebf8e-152">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ebf8e-152">Click **OK**.</span></span>  
  
     <span data-ttu-id="ebf8e-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="ebf8e-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="ebf8e-154">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="ebf8e-154">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="ebf8e-155">第 7 课：将数据文件移动到 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="ebf8e-155">Lesson 7: Move your data files to Azure Storage</span></span>](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
