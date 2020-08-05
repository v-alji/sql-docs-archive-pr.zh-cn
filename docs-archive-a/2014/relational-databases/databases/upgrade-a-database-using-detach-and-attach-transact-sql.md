---
title: 使用分离和附加升级数据库 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- upgrading databases
- database upgrades [SQL Server]
- database detaching [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 99f66ed9-3a75-4e38-ad7d-6c27cc3529a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d430825fd862ff49b867790f366200a524df3c1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580292"
---
# <a name="upgrade-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="3a8c1-102">使用分离和附加来升级数据库 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3a8c1-102">Upgrade a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="3a8c1-103">本主题说明如何使用分离和附加操作在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中升级数据库。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-103">This topic describes how to use detach and attach operations to upgrade a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3a8c1-104">在附加到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]后，数据库将立即变为可用，然后会自动进行升级。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-104">After being attached to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is available immediately and is automatically upgraded.</span></span>  
  
 <span data-ttu-id="3a8c1-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3a8c1-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3a8c1-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3a8c1-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3a8c1-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3a8c1-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3a8c1-108">建议</span><span class="sxs-lookup"><span data-stu-id="3a8c1-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="3a8c1-109">**升级 SQL Server 数据库：**</span><span class="sxs-lookup"><span data-stu-id="3a8c1-109">**To Upgrade a SQL Server Database:**</span></span>  
  
     [<span data-ttu-id="3a8c1-110">使用分离和附加操作</span><span class="sxs-lookup"><span data-stu-id="3a8c1-110">Using detach and attach operations</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="3a8c1-111">**跟进：**  [在升级 SQL Server 数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="3a8c1-111">**Follow Up:**  [After Upgrading a SQL Server Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3a8c1-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="3a8c1-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3a8c1-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3a8c1-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3a8c1-114">不能附加系统数据库。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-114">The system databases cannot be attached.</span></span>  
  
-   <span data-ttu-id="3a8c1-115">附加和分离操作可以通过将数据库的 **cross db ownership chaining** 选项设置为 0 来禁用数据库的跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-115">Attach and detach disable cross-database ownership chaining for the database by setting its **cross db ownership chaining** option to 0.</span></span> <span data-ttu-id="3a8c1-116">有关启用链接的详细信息，请参阅 [cross db ownership chaining 服务器配置选项](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-116">For information about enabling chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="3a8c1-117">附加复制的而不是分离的复制数据库时：</span><span class="sxs-lookup"><span data-stu-id="3a8c1-117">When attaching a replicated database that was copied instead of detached:</span></span>  
  
    -   <span data-ttu-id="3a8c1-118">如果将该数据库附加到同一服务器实例的升级版本中，则必须在附加操作完成后执行 **sp_vupgrade_replication** 来升级复制数据库。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-118">If you attach the database to an upgraded version of the same server instance, you must execute **sp_vupgrade_replication** to upgrade replication after the attach operation finishes.</span></span> <span data-ttu-id="3a8c1-119">有关详细信息，请参阅 [sp_vupgrade_replication (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-119">For more information, see [sp_vupgrade_replication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="3a8c1-120">如果将该数据库附加到不同的服务器实例中（不考虑版本），则必须在附加操作完成后执行 **sp_removedbreplication** 来删除复制数据库。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-120">If you attach the database to a different server instance (regardless of version), you must execute **sp_removedbreplication** to remove replication after the attach operation finishes.</span></span> <span data-ttu-id="3a8c1-121">有关详细信息，请参阅 [sp_removedbreplication (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-121">For more information, see [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3a8c1-122">建议</span><span class="sxs-lookup"><span data-stu-id="3a8c1-122">Recommendations</span></span>  
 <span data-ttu-id="3a8c1-123">建议您不要附加或还原来自未知或不可信源的数据库。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-123">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="3a8c1-124">此类数据库可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-124">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="3a8c1-125">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-125">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="to-upgrade-a-database-by-using-detach-and-attach"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3a8c1-126">使用分离和附加功能来升级数据库</span><span class="sxs-lookup"><span data-stu-id="3a8c1-126">To Upgrade a Database by Using Detach and Attach</span></span>  
  
1.  <span data-ttu-id="3a8c1-127">分离数据库。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-127">Detach the database.</span></span> <span data-ttu-id="3a8c1-128">有关详细信息，请参阅 [分离数据库](detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-128">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="3a8c1-129">（可选）移动所分离的数据库文件和日志文件。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-129">Optionally, move the detached database file or files and the log file or files.</span></span>  
  
     <span data-ttu-id="3a8c1-130">即使希望创建新的日志文件，也应该将日志文件与数据文件一起移动。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-130">You should move the log files along with the data files, even if you intend to create new log files.</span></span> <span data-ttu-id="3a8c1-131">在某些情况下，重新附加数据库需要使用其现有的日志文件。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-131">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="3a8c1-132">因此，除非在不使用分离日志文件的情况下可以成功附加数据库，否则，请始终保留所有分离的日志文件。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-132">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a8c1-133">如果尝试在不指定日志文件的情况下附加数据库，则附加操作将会在日志文件的原始位置中查找文件。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-133">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="3a8c1-134">如果该位置仍存在日志文件的原始副本，则附加该副本。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-134">If the original copy of the log still exists in that location, that copy is attached.</span></span> <span data-ttu-id="3a8c1-135">若要避免使用原始日志文件，请指定新日志文件的路径，或在日志文件复制到新位置之后，删除其原始副本。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-135">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="3a8c1-136">将复制的文件附加到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-136">Attach the copied files to the instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3a8c1-137">有关详细信息，请参阅 [Attach a Database](attach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-137">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a8c1-138">示例</span><span class="sxs-lookup"><span data-stu-id="3a8c1-138">Example</span></span>  
 <span data-ttu-id="3a8c1-139">以下实例升级以前版本的 SQL Server 的数据库副本。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-139">The following example upgrades a copy of a database from an earlier version of SQL Server.</span></span> <span data-ttu-id="3a8c1-140">[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在与该服务器实例（附加该数据库副本）连接的查询编辑器窗口中执行。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-140">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="3a8c1-141">执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以分离数据库：</span><span class="sxs-lookup"><span data-stu-id="3a8c1-141">Detach the database by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'MyDatabase';  
    GO  
    ```  
  
2.  <span data-ttu-id="3a8c1-142">使用您选择的方法，将数据文件和日志文件复制到新位置。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-142">Using the method of your choice, copy the data and log files to the new location.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3a8c1-143">对于生产数据库，请将数据库和事务日志存放在不同的磁盘上。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-143">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="3a8c1-144">若要通过网络将文件复制到远程计算机的磁盘上，请使用远程位置的通用命名约定 (UNC) 名称。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-144">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="3a8c1-145">UNC 名称采用的格式为 **\\\\** _Servername_ **\\** _共享_名 **\\** _路径_ **\\** _Filename_。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-145">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="3a8c1-146">将文件写入本地硬盘时，必须对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例使用的用户帐户授予读写远程磁盘文件所需的相应权限。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-146">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="3a8c1-147">通过执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句来附加移动的数据库及其日志（日志为可选项）：</span><span class="sxs-lookup"><span data-stu-id="3a8c1-147">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyDatabase   
        ON (FILENAME = 'C:\MySQLServer\MyDatabase.mdf'),  
        (FILENAME = 'C:\MySQLServer\Database.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="3a8c1-148">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，新附加的数据库在对象资源管理器中不是立即可见的。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="3a8c1-149">若要查看数据库，请在对象资源管理器中，单击 **“查看”** ，再单击 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-149">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="3a8c1-150">在对象资源管理器中展开 **“数据库”** 节点后，新附加的数据库即显示在数据库列表中。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-150">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="3a8c1-151">跟进：在升级 SQL Server 数据库之后</span><span class="sxs-lookup"><span data-stu-id="3a8c1-151">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="3a8c1-152">如果数据库具有全文检索，则升级过程将导入、重置或重新生成它们，具体取决于 **upgrade_option** 服务器属性的设置。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-152">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **upgrade_option** server property.</span></span> <span data-ttu-id="3a8c1-153">如果将升级选项设置为“导入”(**upgrade_option** = 2) 或“重新生成”(**upgrade_option** = 0)，在升级过程中将无法使用全文检索。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-153">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="3a8c1-154">导入可能需要数小时，而重新生成所需的时间最多时可能十倍于此，具体取决于要编制索引的数据量。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-154">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="3a8c1-155">另请注意，如果将升级选项设置为“导入”，并且全文目录不可用，则会重新生成关联的全文索引。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-155">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="3a8c1-156">若要更改 **upgrade_option** 服务器属性的设置，请使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-156">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
### <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="3a8c1-157">升级后的数据库兼容级别</span><span class="sxs-lookup"><span data-stu-id="3a8c1-157">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="3a8c1-158">如果升级前用户数据库的兼容级别为 100 或更高，升级后将保持相应级别。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-158">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="3a8c1-159">如果升级前兼容级别为 90，则在升级后的数据库中，兼容级别将设置为 100，该级别为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]支持的最低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-159">If the compatibility level is 90 before upgrade in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3a8c1-160">有关详细信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-160">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
### <a name="managing-metadata-on-the-upgraded-server-instance"></a><span data-ttu-id="3a8c1-161">管理已升级服务器实例上的元数据</span><span class="sxs-lookup"><span data-stu-id="3a8c1-161">Managing Metadata on the Upgraded Server Instance</span></span>  
 <span data-ttu-id="3a8c1-162">将数据库附加到其他服务器实例时，为了给用户和应用程序提供一致的体验，您可能需要在其他服务器实例上为数据库重新创建部分或全部元数据（例如登录名、作业和权限）。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-162">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins, jobs, and permissions, on the other server instance.</span></span> <span data-ttu-id="3a8c1-163">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-163">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
### <a name="service-master-key-and-database-master-key-encryption-changes-from-3des-to-aes"></a><span data-ttu-id="3a8c1-164">服务主密钥和数据库主密钥加密从 3DES 更改为 AES</span><span class="sxs-lookup"><span data-stu-id="3a8c1-164">Service Master Key and Database Master Key Encryption changes from 3DES to AES</span></span>  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="3a8c1-165">以及更高版本使用 AES 加密算法来保护服务主密钥 (SMK) 和数据库主密钥 (DMK)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-165">and higher versions uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="3a8c1-166">AES 是一种比早期版本中使用的 3DES 更新的加密算法。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-166">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="3a8c1-167">当数据库第一次附加或还原到新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例时，数据库主密钥（由服务主密钥加密）的副本尚未存储在服务器中。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-167">When a database is first attached or restored to a new instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a copy of the database master key (encrypted by the service master key) is not yet stored in the server.</span></span> <span data-ttu-id="3a8c1-168">必须使用 `OPEN MASTER KEY` 语句解密数据库主密钥 (DMK)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-168">You must use the `OPEN MASTER KEY` statement to decrypt the database master key (DMK).</span></span> <span data-ttu-id="3a8c1-169">一旦 DMK 解密后，通过使用 `ALTER MASTER KEY REGENERATE` 语句向服务器提供 DMK（使用服务主密钥 (SMK) 加密）的副本，即可拥有将来启用自动解密的选项。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-169">Once the DMK has been decrypted, you have the option of enabling automatic decryption in the future by using the `ALTER MASTER KEY REGENERATE` statement to provision the server with a copy of the DMK, encrypted with the service master key (SMK).</span></span> <span data-ttu-id="3a8c1-170">当数据库已从较早版本升级后，应重新生成 DMK 以使用更新的 AES 算法。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-170">When a database has been upgraded from an earlier version, the DMK should be regenerated to use the newer AES algorithm.</span></span> <span data-ttu-id="3a8c1-171">有关重新生成 DMK 的详细信息，请参阅 [ALTER MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-171">For more information about regenerating the DMK, see [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span> <span data-ttu-id="3a8c1-172">重新生成 DMK 密钥以升级到 AES 所需的时间取决于 DMK 保护的对象数。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-172">The time required to regenerate the DMK key to upgrade to AES depends upon the number of objects protected by the DMK.</span></span> <span data-ttu-id="3a8c1-173">重新生成 DMK 密钥以升级到 AES 只在必需时执行一次，不影响将来作为密钥循环策略的一部分而重新生成的过程。</span><span class="sxs-lookup"><span data-stu-id="3a8c1-173">Regenerating the DMK key to upgrade to AES is only necessary once, and has no impact on future regenerations as part of a key rotation strategy.</span></span>  
  
  
