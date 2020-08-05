---
title: 分离和附加 DQS 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bcac9d1f53b10cf6356b878ce4006f66c198d99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579056"
---
# <a name="detaching-and-attaching-dqs-databases"></a><span data-ttu-id="c5359-102">分离数据库和附加 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="c5359-102">Detaching and Attaching DQS Databases</span></span>
  <span data-ttu-id="c5359-103">本主题介绍如何分离和附加 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-103">This topic describes how to detach and attach the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c5359-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="c5359-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="c5359-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c5359-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c5359-106">有关限制和局限的列表，请参阅 [数据库分离和附加 (SQL Server)](../relational-databases/databases/database-detach-and-attach-sql-server.md)中分离数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-106">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="c5359-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="c5359-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="c5359-108">确保 DQS 中没有正在运行的活动或过程。</span><span class="sxs-lookup"><span data-stu-id="c5359-108">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="c5359-109">这可以使用 **“活动监视”** 屏幕进行验证。</span><span class="sxs-lookup"><span data-stu-id="c5359-109">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="c5359-110">有关使用该屏幕的详细信息，请参阅 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="c5359-110">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="c5359-111">确保没有用户已登录 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5359-111">Ensure that there are no users logged on the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c5359-112">Security</span><span class="sxs-lookup"><span data-stu-id="c5359-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c5359-113">权限</span><span class="sxs-lookup"><span data-stu-id="c5359-113">Permissions</span></span>  
  
-   <span data-ttu-id="c5359-114">您的 Windows 用户帐户必须是 SQL Server 实例中 db_owner 固定服务器角色的成员，才能分离 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-114">Your Windows user account must be a member of the db_owner fixed server role in the SQL Server instance to detach DQS databases.</span></span>  
  
-   <span data-ttu-id="c5359-115">您的 Windows 用户帐户必须具有 CREATE DATABASE、CREATE ANY DATABASE 或 ALTER ANY DATABASE 权限，才能附加数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-115">Your Windows user account must have CREATE DATABASE, CREATE ANY DATABASE, or ALTER ANY DATABASE permission to attach a database.</span></span>  
  
-   <span data-ttu-id="c5359-116">您必须具有 DQS_MAIN 数据库的 dqs_administrator 角色，才能终止 DQS 中任何正在运行的活动或停止任何正在运行的过程。</span><span class="sxs-lookup"><span data-stu-id="c5359-116">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="detach-dqs-databases"></a><a name="Detach"></a> <span data-ttu-id="c5359-117">分离 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="c5359-117">Detach DQS Databases</span></span>  
 <span data-ttu-id="c5359-118">在您使用 SQL Server Management Studio 分离 DQS 数据库时，分离后的文件将保留在您的计算机上，并且可以重新附加到同一个 SQL Server 实例上，也可以移到其他服务器上并附加其上。</span><span class="sxs-lookup"><span data-stu-id="c5359-118">When you detach a DQS database using SQL Server Management Studio, the detached files remain on your computer, and can be reattached to the same SQL Server instance or can be can be moved to another server and attached there.</span></span> <span data-ttu-id="c5359-119">DQS 数据库文件通常位于 Data Quality Services 计算机上的以下位置： C:\Program Files\Microsoft SQL Server\MSSQL12。*<Instance_Name>* \mssql\data。</span><span class="sxs-lookup"><span data-stu-id="c5359-119">The DQS database files are typically available at the following location on your Data Quality Services computer: C:\Program Files\Microsoft SQL Server\MSSQL12.*<Instance_Name>* \MSSQL\DATA.</span></span>  
  
1.  <span data-ttu-id="c5359-120">启动 Microsoft SQL Server Management Studio 并连接到适当的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="c5359-120">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="c5359-121">在“对象资源管理器”中，展开 **“数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="c5359-121">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="c5359-122">右键单击 **DQS_MAIN** 数据库，指向 **“任务”**，再单击 **“分离”**。</span><span class="sxs-lookup"><span data-stu-id="c5359-122">Right-click the **DQS_MAIN** database, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="c5359-123">将出现 **“分离数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c5359-123">The **Detach Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="c5359-124">选中 **“删除”** 列下的复选框，然后单击 **“确定”** 以便分离 DQS_MAIN 数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-124">Select the check box under the **Drop** column, and click **OK** to detach the DQS_MAIN database.</span></span>  
  
5.  <span data-ttu-id="c5359-125">对 DQS_PROJECTS 和 DQS_STAGING_DATA 数据库重复执行步骤 3 和步骤 4，以便分离它们。</span><span class="sxs-lookup"><span data-stu-id="c5359-125">Repeat steps 3 and 4 with the DQS_PROJECTS and DQS_STAGING_DATA databases to detach them.</span></span>  
  
 <span data-ttu-id="c5359-126">您还可以使用 sp_detach_db 存储过程通过 Transact-SQL 语句分离 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-126">You can also detach DQS databases using the Transact-SQL statements by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="c5359-127">有关使用 Transact-SQL 语句分离数据库的详细信息，请参阅 [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) 中的 [Detach a Database](../relational-databases/databases/detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c5359-127">For more information about detaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) in [Detach a Database](../relational-databases/databases/detach-a-database.md).</span></span>  
  
##  <a name="attach-dqs-databases"></a><a name="Attach"></a> <span data-ttu-id="c5359-128">附加 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="c5359-128">Attach DQS Databases</span></span>  
 <span data-ttu-id="c5359-129">使用以下说明可以将 DQS 数据库附加到原来从其上分离出来的 SQL Server 实例，或是其他安装了 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="c5359-129">Use the following instructions to attach a DQS database to the same SQL Server instance (from where you detached) or a different SQL Server instance where [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
1.  <span data-ttu-id="c5359-130">启动 Microsoft SQL Server Management Studio 并连接到适当的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="c5359-130">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="c5359-131">在对象资源管理器中，右键单击 **“数据库”**，然后单击 **“附加”**。</span><span class="sxs-lookup"><span data-stu-id="c5359-131">In Object Explorer, right-click **Databases**, and then click **Attach**.</span></span> <span data-ttu-id="c5359-132">将出现 **“附加数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c5359-132">The **Attach Databases** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="c5359-133">若要指定要附加的数据库，请单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="c5359-133">To specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="c5359-134">**“定位数据库文件”** 对话框将出现。</span><span class="sxs-lookup"><span data-stu-id="c5359-134">The **Locate Database Files** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="c5359-135">选择数据库驻留的磁盘驱动器，然后展开目录树以便找到并选择该数据库的 .mdf 文件。</span><span class="sxs-lookup"><span data-stu-id="c5359-135">Select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database.</span></span> <span data-ttu-id="c5359-136">例如，对于 DQS_MAIN 数据库：</span><span class="sxs-lookup"><span data-stu-id="c5359-136">For example, for the DQS_MAIN database:</span></span>  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  <span data-ttu-id="c5359-137">**“数据库详细信息”** （下部）窗格将显示要附加的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c5359-137">The **database details** (lower) pane displays the names of the files to be attached.</span></span> <span data-ttu-id="c5359-138">若要验证或更改文件的路径名，请单击 "**浏览**" 按钮 ( ... ") 。</span><span class="sxs-lookup"><span data-stu-id="c5359-138">To verify or change the pathname of a file, click the **Browse** button (...).</span></span>  
  
6.  <span data-ttu-id="c5359-139">单击 **“确定”** 将附加该 DQS_MAIN 数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-139">Click **OK** to attach the DQS_MAIN database.</span></span>  
  
7.  <span data-ttu-id="c5359-140">对 DQS_PROJECTS 和 DQS_STAGING_DATA 数据库重复执行步骤 2-6，以便附加它们。</span><span class="sxs-lookup"><span data-stu-id="c5359-140">Repeat steps 2-6 for the DQS_PROJECTS and DQS_STAGING_DATA databases to attach them.</span></span>  
  
8.  <span data-ttu-id="c5359-141">在还原 DQS_MAIN 数据库后您还必须在接下来的步骤中运行 Transact-SQL 语句，否则，在您尝试通过使用数据质量客户端应用程序连接到数据质量服务器时系统将会显示错误消息，并且您将无法连接。</span><span class="sxs-lookup"><span data-stu-id="c5359-141">You must also run the Transact-SQL statements in the next step after restoring the DQS_MAIN database otherwise an error message is displayed when you try to connect to Data Quality Server by using the Data Quality Client application, and you cannot connect.</span></span> <span data-ttu-id="c5359-142">但是，如果您只是附加 DQS_PROJECTS 或 DQS_STAGING_DATA 数据库，而不是 DQS_MAIN，则不需要执行步骤 9 和 10。</span><span class="sxs-lookup"><span data-stu-id="c5359-142">However, you do not need to perform steps 9 and 10 if you have just attached the DQS_PROJECTS or DQS_STAGING_DATA database, and not DQS_MAIN.</span></span>  
  
     <span data-ttu-id="c5359-143">若要运行 Transact-SQL 语句，请在对象资源管理器中，右键单击服务器，然后单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="c5359-143">To run the Transact-SQL statements, in Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
9. <span data-ttu-id="c5359-144">在“查询编辑器”窗口中，复制以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="c5359-144">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
    ```  
  
10. <span data-ttu-id="c5359-145">按 F5 执行这些语句。</span><span class="sxs-lookup"><span data-stu-id="c5359-145">Press F5 to execute the statements.</span></span> <span data-ttu-id="c5359-146">查看“结果”窗格以便验证这些语句已成功执行。</span><span class="sxs-lookup"><span data-stu-id="c5359-146">Check the Results pane to verify that the statements have executed successfully.</span></span> <span data-ttu-id="c5359-147">您将看到下列消息： `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span><span class="sxs-lookup"><span data-stu-id="c5359-147">You will see the following message: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span></span>  
  
11. <span data-ttu-id="c5359-148">使用数据质量客户端连接到数据质量服务器以便验证您是否可以成功连接。</span><span class="sxs-lookup"><span data-stu-id="c5359-148">Connect to the Data Quality Server using the Data Quality Client to verify if you can connect successfully.</span></span>  
  
 <span data-ttu-id="c5359-149">您还可以使用 Transact-SQL 语句附加 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="c5359-149">You can also attach DQS databases using the Transact-SQL statements.</span></span> <span data-ttu-id="c5359-150">有关使用 Transact-SQL 语句附加数据库的详细信息，请参阅 [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) 中的 [Attach a Database](../relational-databases/databases/attach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c5359-150">For more information about attaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) in [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5359-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5359-151">See Also</span></span>  
 [<span data-ttu-id="c5359-152">管理 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="c5359-152">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
