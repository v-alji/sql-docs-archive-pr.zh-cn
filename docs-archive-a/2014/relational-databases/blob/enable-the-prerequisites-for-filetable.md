---
title: 启用 FileTable 的先决条件 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d5d2c5dab7909ec5403911d482823f488cdd809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576839"
---
# <a name="enable-the-prerequisites-for-filetable"></a><span data-ttu-id="9184a-102">启用 FileTable 的先决条件</span><span class="sxs-lookup"><span data-stu-id="9184a-102">Enable the Prerequisites for FileTable</span></span>
  <span data-ttu-id="9184a-103">介绍如何启用创建和使用 FileTable 的先决条件。</span><span class="sxs-lookup"><span data-stu-id="9184a-103">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
##  <a name="enabling-the-prerequisites-for-filetable"></a><a name="EnablePrereq"></a> <span data-ttu-id="9184a-104">启用 FileTable 的先决条件</span><span class="sxs-lookup"><span data-stu-id="9184a-104">Enabling the Prerequisites for FileTable</span></span>  
 <span data-ttu-id="9184a-105">若要启用创建和使用 FileTable 的先决条件，请启用下列项目：</span><span class="sxs-lookup"><span data-stu-id="9184a-105">To enable the prerequisites for creating and using FileTables, enable the following items:</span></span>  
  
-   <span data-ttu-id="9184a-106">**在实例级别：**</span><span class="sxs-lookup"><span data-stu-id="9184a-106">**At the instance level:**</span></span>  
  
    -   [<span data-ttu-id="9184a-107">在实例级别启用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9184a-107">Enabling FILESTREAM at the Instance Level</span></span>](#BasicsFilestream)  
  
-   <span data-ttu-id="9184a-108">**在数据库级别：**</span><span class="sxs-lookup"><span data-stu-id="9184a-108">**At the database level:**</span></span>  
  
    -   [<span data-ttu-id="9184a-109">在数据库级别提供 FILESTREAM 文件组</span><span class="sxs-lookup"><span data-stu-id="9184a-109">Providing a FILESTREAM Filegroup at the Database Level</span></span>](#filegroup)  
  
    -   [<span data-ttu-id="9184a-110">在数据库级别启用非事务性访问</span><span class="sxs-lookup"><span data-stu-id="9184a-110">Enabling Non-Transactional Access at the Database Level</span></span>](#BasicsNTAccess)  
  
    -   [<span data-ttu-id="9184a-111">在数据库级别指定 FileTable 的目录</span><span class="sxs-lookup"><span data-stu-id="9184a-111">Specifying a Directory for FileTables at the Database Level</span></span>](#BasicsDirectory)  
  
##  <a name="enabling-filestream-at-the-instance-level"></a><a name="BasicsFilestream"></a> <span data-ttu-id="9184a-112">在实例级别启用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9184a-112">Enabling FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="9184a-113">FileTable 扩展了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="9184a-113">FileTables extend the capabilities of the FILESTREAM feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9184a-114">因此，在创建和使用 FileTable 前，必须在 Windows 级别和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上启用 FILESTREAM 用于文件 I/O 访问。</span><span class="sxs-lookup"><span data-stu-id="9184a-114">Therefore you have to enable FILESTREAM for file I/O access at the Windows level and on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you can create and use FileTables.</span></span>  
  
###  <a name="how-to-enable-filestream-at-the-instance-level"></a><a name="HowToFilestream"></a> <span data-ttu-id="9184a-115">如何：在实例级别启用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9184a-115">How To: Enable FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="9184a-116">有关如何启用 FILESTREAM 的信息，请参阅 [启用和配置 FILESTREAM](enable-and-configure-filestream.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-116">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
 <span data-ttu-id="9184a-117">当您调用 `sp_configure` 在实例级别启用 FILESTREAM 时，必须将 filestream_access_level 选项设置为 2。</span><span class="sxs-lookup"><span data-stu-id="9184a-117">When you call `sp_configure` to enable FILESTREAM at the instance level, you have to set the filestream_access_level option to 2.</span></span> <span data-ttu-id="9184a-118">有关详细信息，请参阅 [文件流访问级别服务器配置选项](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-118">For more information, see [filestream access level Server Configuration Option](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).</span></span>  
  
###  <a name="how-to-allow-filestream-through-the-firewall"></a><a name="firewall"></a> <span data-ttu-id="9184a-119">如何：允许 FILESTREAM 通过防火墙</span><span class="sxs-lookup"><span data-stu-id="9184a-119">How To: Allow FILESTREAM through the Firewall</span></span>  
 <span data-ttu-id="9184a-120">有关如何允许 FILESTREAM 通过防火墙的信息，请参阅 [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-120">For information about how to allow FILESTREAM through the firewall, see [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md).</span></span>  
  
##  <a name="providing-a-filestream-filegroup-at-the-database-level"></a><a name="filegroup"></a> <span data-ttu-id="9184a-121">在数据库级别提供 FILESTREAM 文件组</span><span class="sxs-lookup"><span data-stu-id="9184a-121">Providing a FILESTREAM Filegroup at the Database Level</span></span>  
 <span data-ttu-id="9184a-122">数据库必须首先具有 FILESTREAM 文件组，然后您才能在该数据库中创建 FileTable。</span><span class="sxs-lookup"><span data-stu-id="9184a-122">Before you can create FileTables in a database, the database must have a FILESTREAM filegroup.</span></span> <span data-ttu-id="9184a-123">有关此先决条件的详细信息，请参阅 [创建启用了 FILESTREAM 的数据库](create-a-filestream-enabled-database.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-123">For more information about this prerequisite, see [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
##  <a name="enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsNTAccess"></a> <span data-ttu-id="9184a-124">在数据库级别启用非事务性访问</span><span class="sxs-lookup"><span data-stu-id="9184a-124">Enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="9184a-125">FileTable 使 Windows 应用程序可以获取 FILESTREAM 数据的 Windows 文件句柄而不需要事务。</span><span class="sxs-lookup"><span data-stu-id="9184a-125">FileTables let Windows applications obtain a Windows file handle to FILESTREAM data without requiring a transaction.</span></span> <span data-ttu-id="9184a-126">为了允许对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中存储的文件进行此非事务性访问，您必须为要包含 FileTable 的每个数据库在数据库级别上指定所需的非事务性访问级别。</span><span class="sxs-lookup"><span data-stu-id="9184a-126">To allow this non-transactional access to files stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you have to specify the desired level of non-transactional access at the database level for each database that will contain FileTables.</span></span>  
  
###  <a name="how-to-check-whether-non-transactional-access-is-enabled-on-databases"></a><a name="HowToCheckAccess"></a> <span data-ttu-id="9184a-127">如何：检查是否在数据库上启用了非事务性访问</span><span class="sxs-lookup"><span data-stu-id="9184a-127">How To: Check Whether Non-Transactional Access Is Enabled on Databases</span></span>  
 <span data-ttu-id="9184a-128">查询目录视图 [sys.database_filestream_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) 并检查 **non_transacted_access** 和 **non_transacted_access_desc** 列。</span><span class="sxs-lookup"><span data-stu-id="9184a-128">Query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **non_transacted_access** and **non_transacted_access_desc** columns.</span></span>  
  
```sql  
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="how-to-enable-non-transactional-access-at-the-database-level"></a><a name="HowToNTAccess"></a> <span data-ttu-id="9184a-129">如何：在数据库级别启用非事务性访问</span><span class="sxs-lookup"><span data-stu-id="9184a-129">How To: Enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="9184a-130">非事务性访问的可用级别为 FULL、READ_ONLY 和 OFF。</span><span class="sxs-lookup"><span data-stu-id="9184a-130">The available levels of non-transactional access are FULL, READ_ONLY, and OFF.</span></span>  
  
 <span data-ttu-id="9184a-131">**使用 Transact-SQL 指定非事务性访问的级别**</span><span class="sxs-lookup"><span data-stu-id="9184a-131">**Specify the level of non-transactional access by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="9184a-132">**创建新数据库**时，调用带 **NON_TRANSACTED_ACCESS** FILESTREAM 选项的 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="9184a-132">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
-   <span data-ttu-id="9184a-133">**更改现有数据库**时，调用带 **NON_TRANSACTED_ACCESS** FILESTREAM 选项的 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="9184a-133">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
 <span data-ttu-id="9184a-134">**使用 SQL Server Management Studio 指定非事务性访问的级别**</span><span class="sxs-lookup"><span data-stu-id="9184a-134">**Specify the level of non-transactional access by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="9184a-135">可以在“数据库属性”  对话框的“选项”  页的“FILESTREAM 非事务性访问”  字段中指定非事务性访问的级别。</span><span class="sxs-lookup"><span data-stu-id="9184a-135">You can specify the level of non-transactional access in the **FILESTREAM Non-transacted Access** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="9184a-136">有关此对话框的详细信息，请参阅[数据库属性（选项页）](../databases/database-properties-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-136">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
##  <a name="specifying-a-directory-for-filetables-at-the-database-level"></a><a name="BasicsDirectory"></a> <span data-ttu-id="9184a-137">在数据库级别指定 FileTable 的目录</span><span class="sxs-lookup"><span data-stu-id="9184a-137">Specifying a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="9184a-138">在数据库级别启用对文件的非事务性访问时，可以选择使用 **DIRECTORY_NAME** 选项同时提供一个目录名称。</span><span class="sxs-lookup"><span data-stu-id="9184a-138">When you enable non-transactional access to files at the database level, you can optionally provide a directory name at the same time by using the **DIRECTORY_NAME** option.</span></span> <span data-ttu-id="9184a-139">如果启用非事务性访问时没有提供目录名称，则在以后必须提供它，这样才能在数据库中创建 FileTable。</span><span class="sxs-lookup"><span data-stu-id="9184a-139">If you do not provide a directory name when you enable non-transactional access, then you have to provide it later before you can create FileTables in the database.</span></span>  
  
 <span data-ttu-id="9184a-140">在 FileTable 文件夹层次结构中，此数据库级目录将成为在实例级别为 FILESTREAM 指定的共享名称的子级以及在数据库中创建的 FileTable 的父级。</span><span class="sxs-lookup"><span data-stu-id="9184a-140">In the FileTable folder hierarchy, this database-level directory becomes the child of the share name specified for FILESTREAM at the instance level, and the parent of the FileTables created in the database.</span></span> <span data-ttu-id="9184a-141">有关详细信息，请参阅 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-141">For more information, see [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).</span></span>  
  
###  <a name="how-to-specify-a-directory-for-filetables-at-the-database-level"></a><a name="HowToDirectory"></a> <span data-ttu-id="9184a-142">如何：在数据库级别指定 FileTable 的目录</span><span class="sxs-lookup"><span data-stu-id="9184a-142">How To: Specify a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="9184a-143">您指定的名称必须在跨数据库级目录的实例中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9184a-143">The name that you specify must be unique across the instance for database-level directories.</span></span>  
  
 <span data-ttu-id="9184a-144">**使用 Transact-SQL 指定 FileTable 的目录**</span><span class="sxs-lookup"><span data-stu-id="9184a-144">**Specify a directory for FileTables by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="9184a-145">**创建新数据库**时，调用带 **DIRECTORY_NAME** FILESTREAM 选项的 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="9184a-145">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="9184a-146">**更改现有数据库**时，调用带 **DIRECTORY_NAME** FILESTREAM 选项的 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="9184a-146">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span> <span data-ttu-id="9184a-147">使用这些选项更改目录名称时，数据库必须以独占方式锁定，没有打开的文件句柄。</span><span class="sxs-lookup"><span data-stu-id="9184a-147">When you use these options to change the directory name, the database must be exclusively locked, with no open file handles.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="9184a-148">**附加数据库**时，调用带 **FOR ATTACH** 选项和 **DIRECTORY_NAME** FILESTREAM 选项的 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="9184a-148">When you **attach a database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **FOR ATTACH** option and with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="9184a-149">**还原数据库**时，调用带 **DIRECTORY_NAME** FILESTREAM 选项的 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="9184a-149">When you **restore a database**, call the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 <span data-ttu-id="9184a-150">**使用 SQL Server Management Studio 指定 FileTable 的目录**</span><span class="sxs-lookup"><span data-stu-id="9184a-150">**Specify a directory for FileTables by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="9184a-151">可以在“数据库属性”  对话框的“选项”  页的“FILESTREAM 目录名称”  字段中指定目录名称。</span><span class="sxs-lookup"><span data-stu-id="9184a-151">You can specify a directory name in the **FILESTREAM Directory Name** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="9184a-152">有关此对话框的详细信息，请参阅[数据库属性（选项页）](../databases/database-properties-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="9184a-152">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
###  <a name="how-to-view-existing-directory-names-for-the-instance"></a><a name="viewnames"></a> <span data-ttu-id="9184a-153">如何：查看实例的现有目录名</span><span class="sxs-lookup"><span data-stu-id="9184a-153">How to: View Existing Directory Names for the Instance</span></span>  
 <span data-ttu-id="9184a-154">若要查看该实例的现有目录名称的列表，可查询目录视图 [sys.database_filestream_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) 并查看 **filestream_database_directory_name** 列。</span><span class="sxs-lookup"><span data-stu-id="9184a-154">To view the list of existing directory names for the instance, query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **filestream_database_directory_name** column.</span></span>  
  
```sql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="requirements-and-restrictions-for-the-database-level-directory"></a><a name="ReqDirectory"></a> <span data-ttu-id="9184a-155">数据库级别目录的要求和限制</span><span class="sxs-lookup"><span data-stu-id="9184a-155">Requirements and Restrictions for the Database-Level Directory</span></span>  
  
-   <span data-ttu-id="9184a-156">在调用 **CREATE DATABASE** 或 **ALTER DATABASE** 时，设置 **DIRECTORY_NAME**是可选的。</span><span class="sxs-lookup"><span data-stu-id="9184a-156">Setting the **DIRECTORY_NAME** is optional when you call **CREATE DATABASE** or **ALTER DATABASE**.</span></span> <span data-ttu-id="9184a-157">如果未指定 **DIRECTORY_NAME**的值，则目录名称仍是 Null。</span><span class="sxs-lookup"><span data-stu-id="9184a-157">If you do not specify a value for **DIRECTORY_NAME**, then the directory name remains null.</span></span> <span data-ttu-id="9184a-158">但不能在数据库中创建 FileTable，直到在数据库级别指定了 **DIRECTORY_NAME** 的值。</span><span class="sxs-lookup"><span data-stu-id="9184a-158">However you cannot create FileTables in the database until you specify a value for **DIRECTORY_NAME** at the database level.</span></span>  
  
-   <span data-ttu-id="9184a-159">您提供的目录名称必须符合文件系统对有效目录名称的要求。</span><span class="sxs-lookup"><span data-stu-id="9184a-159">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
-   <span data-ttu-id="9184a-160">当数据库包含 FileTable 时，不能将 **DIRECTORY_NAME** 设置回为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="9184a-160">When the database contains FileTables, you cannot set the **DIRECTORY_NAME** back to a null value.</span></span>  
  
-   <span data-ttu-id="9184a-161">附加或还原数据库时，如果新数据库的 **DIRECTORY_NAME** 值在目标实例中已存在，则该操作失败。</span><span class="sxs-lookup"><span data-stu-id="9184a-161">When you attach or restore a database, the operation fails if the new database has a value for **DIRECTORY_NAME** that already exists in the target instance.</span></span> <span data-ttu-id="9184a-162">调用 **CREATE DATABASE FOR ATTACH** 或 **RESTORE DATABASE** 时，指定 **DIRECTORY_NAME**的唯一值。</span><span class="sxs-lookup"><span data-stu-id="9184a-162">Specify a unique value for **DIRECTORY_NAME** when you call **CREATE DATABASE FOR ATTACH** or **RESTORE DATABASE**.</span></span>  
  
-   <span data-ttu-id="9184a-163">当将现有数据库升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时， **DIRECTORY_NAME** 的值为 Null。</span><span class="sxs-lookup"><span data-stu-id="9184a-163">When you upgrade an existing database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the value of **DIRECTORY_NAME** is null.</span></span>  
  
-   <span data-ttu-id="9184a-164">在数据库级别启用或禁用非事务性访问时，该操作不检查是否已指定目录名称或该名称是否唯一。</span><span class="sxs-lookup"><span data-stu-id="9184a-164">When you enable or disable non-transactional access at the database level, the operation does not check whether the directory name has been specified or whether it is unique.</span></span>  
  
-   <span data-ttu-id="9184a-165">删除已为 FileTable 启用的数据库时，将删除数据库级目录和其下的所有 FileTable 的所有目录结构。</span><span class="sxs-lookup"><span data-stu-id="9184a-165">When you drop a database that was enabled for FileTables, the database-level directory and all the directory stuctures of all the FileTables under it are removed.</span></span>  
  
  
