---
title: 通过分离和附加来移动数据库 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- moving databases [SQL Server]
- database detaching [SQL Server]
- relocating databases [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 6732a431-cdef-4f1e-9262-4ac3b77c275e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 768a70dfe94af6f8d65f7c76fa08d3dff650fe7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591363"
---
# <a name="move-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="078af-102">通过分离和附加来移动数据库 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="078af-102">Move a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="078af-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中将分离的数据库移至其他位置，并将其重新附加到相同或不同的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="078af-103">This topic describes how to move a detached database to another location and re-attach it to the same or a different server instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="078af-104">但是，我们建议您使用 ALTER DATABASE 计划重定位过程（而不使用分离和附加操作）移动数据库。</span><span class="sxs-lookup"><span data-stu-id="078af-104">However, we recommend that you move databases by using the ALTER DATABASE planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="078af-105">有关详细信息，请参阅 [Move User Databases](move-user-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="078af-105">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="078af-106">建议您不要附加或还原来自未知或不可信源的数据库。</span><span class="sxs-lookup"><span data-stu-id="078af-106">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="078af-107">此类数据库可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="078af-107">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="078af-108">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="078af-108">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="078af-109">过程</span><span class="sxs-lookup"><span data-stu-id="078af-109">Procedure</span></span>  
  
#### <a name="to-move-a-database-by-using-detach-and-attach"></a><span data-ttu-id="078af-110">使用分离和附加操作移动数据库</span><span class="sxs-lookup"><span data-stu-id="078af-110">To move a database by using detach and attach</span></span>  
  
1.  <span data-ttu-id="078af-111">分离数据库。</span><span class="sxs-lookup"><span data-stu-id="078af-111">Detach the database.</span></span> <span data-ttu-id="078af-112">有关详细信息，请参阅 [分离数据库](detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="078af-112">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="078af-113">在 Windows 资源管理器或 Windows“命令提示符”窗口中，将分离的数据库文件和日志文件移至新位置。</span><span class="sxs-lookup"><span data-stu-id="078af-113">In a Windows Explorer or Windows Command Prompt window, move the detached database file or files and log file or files to the new location.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="078af-114">移动单文件数据库时，如果文件小到可以通过电子邮件发送，则可以通过电子邮件来移动该数据库。</span><span class="sxs-lookup"><span data-stu-id="078af-114">To move a single-file database, you can use email if the file size is small enough for email to accommodate.</span></span>  
  
     <span data-ttu-id="078af-115">即使打算创建新的日志文件，也应该移动日志文件。</span><span class="sxs-lookup"><span data-stu-id="078af-115">You should move the log files even if you intend to create new log files.</span></span> <span data-ttu-id="078af-116">在某些情况下，重新附加数据库需要使用其现有的日志文件。</span><span class="sxs-lookup"><span data-stu-id="078af-116">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="078af-117">因此，除非在不使用分离日志文件的情况下可以成功附加数据库，否则，请始终保留所有分离的日志文件。</span><span class="sxs-lookup"><span data-stu-id="078af-117">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="078af-118">如果尝试在不指定日志文件的情况下附加数据库，则附加操作将会在日志文件的原始位置中查找文件。</span><span class="sxs-lookup"><span data-stu-id="078af-118">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="078af-119">如果原始位置还有一份日志，则附加该日志。</span><span class="sxs-lookup"><span data-stu-id="078af-119">If a copy of the log still exists in the original location, that copy is attached.</span></span> <span data-ttu-id="078af-120">若要避免使用原始日志文件，请指定新日志文件的路径，或在日志文件复制到新位置之后，删除其原始副本。</span><span class="sxs-lookup"><span data-stu-id="078af-120">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="078af-121">附加复制的文件。</span><span class="sxs-lookup"><span data-stu-id="078af-121">Attach the copied files.</span></span> <span data-ttu-id="078af-122">有关详细信息，请参阅 [Attach a Database](attach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="078af-122">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="078af-123">示例</span><span class="sxs-lookup"><span data-stu-id="078af-123">Example</span></span>  
 <span data-ttu-id="078af-124">下面的示例创建了语句的副本，这些 [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] 语句在连接到附加到的服务器实例的查询编辑器窗口中执行。</span><span class="sxs-lookup"><span data-stu-id="078af-124">The following example creates a copy of the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="078af-125">分离 [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="078af-125">Detach the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'AdventureWorks2012';  
    GO  
    ```  
  
2.  <span data-ttu-id="078af-126">使用您选择的方法，将数据库文件（AdventureWorks208R2_Data.mdf 和 AdventureWorks208R2_log）分别复制到：C:\MySQLServer\AdventureWorks208R2_Data.mdf 和 C:\MySQLServer\AdventureWorks208R2_Log.ldf。</span><span class="sxs-lookup"><span data-stu-id="078af-126">Using the method of your choice, copy the database files (AdventureWorks208R2_Data.mdf and AdventureWorks208R2_log) to: C:\MySQLServer\AdventureWorks208R2_Data.mdf and C:\MySQLServer\AdventureWorks208R2_Log.ldf, respectively.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="078af-127">对于生产数据库，请将数据库和事务日志存放在不同的磁盘上。</span><span class="sxs-lookup"><span data-stu-id="078af-127">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="078af-128">若要通过网络将文件复制到远程计算机的磁盘上，请使用远程位置的通用命名约定 (UNC) 名称。</span><span class="sxs-lookup"><span data-stu-id="078af-128">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="078af-129">UNC 名称采用以下格式： **\\\\** _服务器名称_ **\\** _共享名_ **\\** _路径_ **\\** _文件名_。</span><span class="sxs-lookup"><span data-stu-id="078af-129">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="078af-130">将文件写入本地硬盘时，必须对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例使用的用户帐户授予读写远程磁盘文件所需的相应权限。</span><span class="sxs-lookup"><span data-stu-id="078af-130">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="078af-131">通过执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句来附加移动的数据库及其日志（可选）：</span><span class="sxs-lookup"><span data-stu-id="078af-131">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Data.mdf'),  
        (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Log.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="078af-132">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，新附加的数据库在对象资源管理器中不是立即可见的。</span><span class="sxs-lookup"><span data-stu-id="078af-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="078af-133">若要查看数据库，请在对象资源管理器中，单击 **“查看”** ，再单击 **“刷新”** 。</span><span class="sxs-lookup"><span data-stu-id="078af-133">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="078af-134">在对象资源管理器中展开 **“数据库”** 节点后，新附加的数据库即显示在数据库列表中。</span><span class="sxs-lookup"><span data-stu-id="078af-134">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078af-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="078af-135">See Also</span></span>  
 [<span data-ttu-id="078af-136">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="078af-136">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
