---
title: 第4课：在 Azure 存储中创建数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50fca85111d5897b738e577e7735049e0b055a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590783"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a><span data-ttu-id="7d902-102">第 4 课：在 Azure 存储中创建数据库</span><span class="sxs-lookup"><span data-stu-id="7d902-102">Lesson 4: Create a database in Azure Storage</span></span>
  <span data-ttu-id="7d902-103">在本课中，您将学习如何使用 Azure 中的 SQL Server 数据文件功能创建数据库。</span><span class="sxs-lookup"><span data-stu-id="7d902-103">In this lesson, you will learn how to create a database using the SQL Server Data Files in Azure feature.</span></span> <span data-ttu-id="7d902-104">注意，开始学习本课之前，必须先学完第 1、2 和 3 课。</span><span class="sxs-lookup"><span data-stu-id="7d902-104">Note that before this lesson, you must complete the Lesson 1, 2, and 3.</span></span> <span data-ttu-id="7d902-105">第3课是一个非常重要的步骤，因为你需要在第4课之前将有关 Azure 存储容器及其关联的策略名称和 SAS 密钥的信息存储在 SQL Server 凭据存储中。</span><span class="sxs-lookup"><span data-stu-id="7d902-105">Lesson 3 is a very important step because you need to store the information about your Azure storage container and its associated policy name and SAS key in the SQL Server credential store before Lesson 4.</span></span>  
  
 <span data-ttu-id="7d902-106">对于数据或日志文件使用的每个存储容器，都必须创建一个 SQL Server 凭据，其名称与容器路径相同。</span><span class="sxs-lookup"><span data-stu-id="7d902-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span> <span data-ttu-id="7d902-107">然后，你可以在 Azure 存储中创建新的数据库</span><span class="sxs-lookup"><span data-stu-id="7d902-107">Then, you can create a new database in Azure Storage</span></span>  
  
 <span data-ttu-id="7d902-108">本课假定您已完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7d902-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="7d902-109">你有 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="7d902-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="7d902-110">在 Azure 存储帐户下创建了容器。</span><span class="sxs-lookup"><span data-stu-id="7d902-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="7d902-111">已在容器上创建了具有读取、写入和列表权限的策略。</span><span class="sxs-lookup"><span data-stu-id="7d902-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="7d902-112">还生成了 SAS 密钥。</span><span class="sxs-lookup"><span data-stu-id="7d902-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="7d902-113">已在源计算机上创建了 SQL Server 凭据。</span><span class="sxs-lookup"><span data-stu-id="7d902-113">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="7d902-114">若要使用 "Azure 存储中的 SQL Server 数据文件" 功能在 Azure 中创建数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7d902-114">To create a database in Azure using the SQL Server Data Files in Azure Storage feature, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7d902-115">连接到 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="7d902-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="7d902-116">在对象资源管理器中，连接到所安装的数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="7d902-116">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="7d902-117">在“标准”工具栏上，单击“新建查询”。</span><span class="sxs-lookup"><span data-stu-id="7d902-117">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="7d902-118">将以下示例复制并粘贴到查询窗口中，并根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="7d902-118">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="7d902-119">注意，FILENAME 字段指代存储容器中数据库文件的 URI 路径，它必须以 https 开头。</span><span class="sxs-lookup"><span data-stu-id="7d902-119">Note that the FILENAME field refers to the URI path of the database file in storage container and it must start with https.</span></span>  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     <span data-ttu-id="7d902-120">向数据库添加一些数据。</span><span class="sxs-lookup"><span data-stu-id="7d902-120">Add some data to your database.</span></span>  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  <span data-ttu-id="7d902-121">若要查看本地 SQL Server 上的新 TestDB1，请在对象资源管理器中刷新数据库。</span><span class="sxs-lookup"><span data-stu-id="7d902-121">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span>  
  
6.  <span data-ttu-id="7d902-122">同样，若要查看在存储帐户中新建的数据库，请通过 SQL Server Management Studio (SSMS) 连接到存储帐户。</span><span class="sxs-lookup"><span data-stu-id="7d902-122">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="7d902-123">有关如何使用 SQL Server Management Studio 连接到 Azure 存储的信息，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7d902-123">For information on how to connect to an Azure storage using SQL Server Management Studio, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="7d902-124">首先，获取存储帐户信息。</span><span class="sxs-lookup"><span data-stu-id="7d902-124">First, get the storage account information.</span></span> <span data-ttu-id="7d902-125">登录到管理门户。</span><span class="sxs-lookup"><span data-stu-id="7d902-125">Log in to the Management Portal.</span></span> <span data-ttu-id="7d902-126">然后，单击 **“存储”** 并选择您的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="7d902-126">Then, click **Storage** and choose your storage account.</span></span> <span data-ttu-id="7d902-127">选择存储帐户后，单击页面底部的 **“管理访问密钥”** 。</span><span class="sxs-lookup"><span data-stu-id="7d902-127">When a storage account is selected, click **Manage Access Keys** at the bottom of the page.</span></span> <span data-ttu-id="7d902-128">此操作将打开一个类似的对话框窗口：</span><span class="sxs-lookup"><span data-stu-id="7d902-128">This opens a similar dialog window:</span></span>  
  
         <span data-ttu-id="7d902-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="7d902-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span></span>  
  
    2.  <span data-ttu-id="7d902-130">将 "**存储帐户名称**" 和 "**主访问密钥**" 值复制到 SSMS 中的 "**连接到 Azure 存储**" 对话框窗口。</span><span class="sxs-lookup"><span data-stu-id="7d902-130">Copy the **Storage Account Name** and **Primary Access Key** values to the **Connect to Azure Storage** dialog window in SSMS.</span></span> <span data-ttu-id="7d902-131">然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="7d902-131">Then, click **Connect**.</span></span> <span data-ttu-id="7d902-132">此操作将有关存储帐户容器的信息提供给 SSMS，如下面的屏幕快照所示：</span><span class="sxs-lookup"><span data-stu-id="7d902-132">This brings the information about storage account containers to SSMS as shown in the following screenshot:</span></span>  
  
         <span data-ttu-id="7d902-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="7d902-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="7d902-134">以下屏幕截图演示了在本地和 Azure 存储环境中新建的数据库。</span><span class="sxs-lookup"><span data-stu-id="7d902-134">The following screenshot demonstrates the new created database both in on-premises and Azure Storage environment.</span></span>  
  
 <span data-ttu-id="7d902-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="7d902-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="7d902-136">**注意：** 如果当前引用了容器中的任何数据文件，则尝试删除关联的 SQL Server 凭据总是会失败。</span><span class="sxs-lookup"><span data-stu-id="7d902-136">**Note:** If there are any active references to data files in a container, any attempts to delete the associated SQL Server credential fails.</span></span> <span data-ttu-id="7d902-137">同样，如果在 blob 中的特定数据库文件上已有租约并且要删除它，则需要先中断 blob 上的租约。</span><span class="sxs-lookup"><span data-stu-id="7d902-137">Similarly, if there is already a lease on a specific database file in a blob and you want to delete it, first you need to break the lease on the blob.</span></span> <span data-ttu-id="7d902-138">若要中断租约，可以使用 [租约 Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7d902-138">To break the lease, you can use [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx).</span></span>  
  
 <span data-ttu-id="7d902-139">可使用此项新功能配置 SQL Server，以使任何 CREATE DATABASE 语句都默认使用支持云的数据库。</span><span class="sxs-lookup"><span data-stu-id="7d902-139">Using this new feature, you can configure SQL Server so that any CREATE DATABASE statement will default to a cloud enabled database.</span></span> <span data-ttu-id="7d902-140">换句话说，你可以在 SQL Server Management Studio 服务器实例属性中设置默认数据和日志位置，因此在创建数据库时，所有数据库文件 ( .mdf) 都作为页 blob 创建在 Azure 存储中。</span><span class="sxs-lookup"><span data-stu-id="7d902-140">In other words, you can set default data and log locations in SQL Server Management Studio Server instance properties so anytime you create a database, all database files (.mdf, .ldf) are created as page blobs in Azure Storage.</span></span>  
  
 <span data-ttu-id="7d902-141">若要使用 SQL Server Management Studio 用户界面在 Azure 存储中创建数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7d902-141">To create a database in Azure Storage by using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="7d902-142">在对象资源管理器中，连接到一个 SQL Server 数据库引擎实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="7d902-142">In Object Explorer, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="7d902-143">右键单击“数据库”，然后单击“新建数据库”。</span><span class="sxs-lookup"><span data-stu-id="7d902-143">Right-click Databases, and then click New Database.</span></span>  
  
3.  <span data-ttu-id="7d902-144">在“新建数据库”对话框窗口中，键入数据库名称。</span><span class="sxs-lookup"><span data-stu-id="7d902-144">In the New Database dialog window, type a database name.</span></span>  
  
4.  <span data-ttu-id="7d902-145">更改主数据文件和事务日志文件的默认值，在“数据库文件”网格中单击相应的单元格并输入新值。</span><span class="sxs-lookup"><span data-stu-id="7d902-145">Change the default values of the primary data and transaction log files, in the Database files grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="7d902-146">此外，指定文件位置的路径。</span><span class="sxs-lookup"><span data-stu-id="7d902-146">Also, specify the path for the file location.</span></span> <span data-ttu-id="7d902-147">在“路径”中，键入存储容器的 URL 路径，如 `https://teststorageaccnt.blob.core.windows.net/testcontainer/`。</span><span class="sxs-lookup"><span data-stu-id="7d902-147">For Path, type the URL path of the storage container, such as `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span> <span data-ttu-id="7d902-148">在“文件名”中，键入数据库文件的物理文件名（.mdf、.ldf）。</span><span class="sxs-lookup"><span data-stu-id="7d902-148">For FileName, type the physical file names of the database files (.mdf, .ldf).</span></span>  
  
     <span data-ttu-id="7d902-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="7d902-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span></span>  
  
     <span data-ttu-id="7d902-150">有关详细信息，请参阅 [向数据库中添加数据文件或日志文件](databases/add-data-or-log-files-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="7d902-150">For more information, see [Add Data or Log Files to a Database](databases/add-data-or-log-files-to-a-database.md).</span></span>  
  
5.  <span data-ttu-id="7d902-151">保留所有其他默认值。</span><span class="sxs-lookup"><span data-stu-id="7d902-151">Keep all other default values.</span></span>  
  
6.  <span data-ttu-id="7d902-152">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7d902-152">Click OK.</span></span>  
  
 <span data-ttu-id="7d902-153">若要查看本地 SQL Server 上的新 TestDB1，请在对象资源管理器中刷新数据库。</span><span class="sxs-lookup"><span data-stu-id="7d902-153">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span> <span data-ttu-id="7d902-154">同样，若要查看在存储帐户中新建的数据库，请通过 SQL Server Management Studio (SSMS) 连接到存储帐户，如本课程前面所述。</span><span class="sxs-lookup"><span data-stu-id="7d902-154">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS) as explained earlier in this lesson.</span></span>  
  
 <span data-ttu-id="7d902-155">**下一课：**</span><span class="sxs-lookup"><span data-stu-id="7d902-155">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="7d902-156">第5课。&#40;可选&#41; 使用 TDE 加密数据库</span><span class="sxs-lookup"><span data-stu-id="7d902-156">Lesson 5. &#40;Optional&#41; Encrypt your database using TDE</span></span>](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
