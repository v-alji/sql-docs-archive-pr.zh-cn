---
title: 创建、更改和删除 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], altering
- FileTables [SQL Server], dropping
- FileTables [SQL Server], creating
ms.assetid: 47d69e37-8778-4630-809b-2261b5c41c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a10e6333f6dd38a850a832b82a7cb7a0e0bf698
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578262"
---
# <a name="create-alter-and-drop-filetables"></a><span data-ttu-id="e635e-102">创建、更改和删除 FileTable</span><span class="sxs-lookup"><span data-stu-id="e635e-102">Create, Alter, and Drop FileTables</span></span>
  <span data-ttu-id="e635e-103">说明如何创建新的 FileTable 或者更改或删除现有的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-103">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
##  <a name="creating-a-filetable"></a><a name="BasicsCreate"></a> <span data-ttu-id="e635e-104">创建 FileTable</span><span class="sxs-lookup"><span data-stu-id="e635e-104">Creating a FileTable</span></span>  
 <span data-ttu-id="e635e-105">FileTable 是专用的用户表，它具有预定义的固定架构。</span><span class="sxs-lookup"><span data-stu-id="e635e-105">A FileTable is a specialized user table that has a pre-defined and fixed schema.</span></span> <span data-ttu-id="e635e-106">此架构存储 FILESTREAM 数据、文件和目录信息以及文件属性。</span><span class="sxs-lookup"><span data-stu-id="e635e-106">This schema stores FILESTREAM data, file and directory information, and file attributes.</span></span> <span data-ttu-id="e635e-107">有关 FileTable 架构的信息，请参阅 [FileTable Schema](filetable-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="e635e-107">For information about the FileTable schema, see [FileTable Schema](filetable-schema.md).</span></span>  
  
 <span data-ttu-id="e635e-108">可以使用 Transact-SQL 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]创建新的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-108">You can create a new FileTable by using Transact-SQL or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e635e-109">由于 FileTable 有固定架构，您不必指定列的列表。</span><span class="sxs-lookup"><span data-stu-id="e635e-109">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="e635e-110">创建 FileTable 的简单语法允许您指定：</span><span class="sxs-lookup"><span data-stu-id="e635e-110">The simple syntax for creating a FileTable lets you specify:</span></span>  
  
-   <span data-ttu-id="e635e-111">目录名称。</span><span class="sxs-lookup"><span data-stu-id="e635e-111">A directory name.</span></span> <span data-ttu-id="e635e-112">在 FileTable 文件夹层次结构中，此表级目录将成为在数据库级别指定的数据库目录的子级以及在表中存储的文件或目录的父级。</span><span class="sxs-lookup"><span data-stu-id="e635e-112">In the FileTable folder hierarchy, this table-level directory becomes the child of the database directory specified at the database level, and the parent of the files or directories stored in the table.</span></span>  
  
-   <span data-ttu-id="e635e-113">要用于 FileTable 的“名称”  列中文件名的排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="e635e-113">The name of the collation to be used for file names in the **Name** column of the FileTable.</span></span>  
  
-   <span data-ttu-id="e635e-114">要用于 3 个主键的名称和自动创建的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="e635e-114">The names to be used for the 3 primary key and unique constraints that are automatically created.</span></span>  
  
###  <a name="how-to-create-a-filetable"></a><a name="HowToCreate"></a> <span data-ttu-id="e635e-115">如何：创建 FileTable</span><span class="sxs-lookup"><span data-stu-id="e635e-115">How To: Create a FileTable</span></span>  
 <span data-ttu-id="e635e-116">**使用 Transact-SQL 创建 FileTable**</span><span class="sxs-lookup"><span data-stu-id="e635e-116">**Create a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="e635e-117">通过调用带 **AS FileTable** 选项的 [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) 语句创建 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-117">Create a FileTable by calling the [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) statement with the **AS FileTable** option.</span></span> <span data-ttu-id="e635e-118">由于 FileTable 有固定架构，您不必指定列的列表。</span><span class="sxs-lookup"><span data-stu-id="e635e-118">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="e635e-119">您可以为新的 FileTable 指定以下设置：</span><span class="sxs-lookup"><span data-stu-id="e635e-119">You can specify the following settings for the new FileTable:</span></span>  
  
1.  <span data-ttu-id="e635e-120">**FILETABLE_DIRECTORY**。</span><span class="sxs-lookup"><span data-stu-id="e635e-120">**FILETABLE_DIRECTORY**.</span></span> <span data-ttu-id="e635e-121">指定充当存储在 FileTable 中的所有文件和目录的根目录的目录。</span><span class="sxs-lookup"><span data-stu-id="e635e-121">Specifies the directory that serves as the root directory for all the files and directories stored in the FileTable.</span></span> <span data-ttu-id="e635e-122">此名称应在数据库的所有 FileTable 目录名称中唯一。</span><span class="sxs-lookup"><span data-stu-id="e635e-122">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="e635e-123">无论当前排序规则设置如何，唯一性比较都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e635e-123">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="e635e-124">此值的数据类型为 **nvarchar(255)** ，并且使用 **Latin1_General_CI_AS_KS_WS**的固定排序规则。</span><span class="sxs-lookup"><span data-stu-id="e635e-124">This value has a data type of **nvarchar(255)** and uses a fixed collation of **Latin1_General_CI_AS_KS_WS**.</span></span>  
  
    -   <span data-ttu-id="e635e-125">您提供的目录名称必须符合文件系统对有效目录名称的要求。</span><span class="sxs-lookup"><span data-stu-id="e635e-125">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
    -   <span data-ttu-id="e635e-126">此名称应在数据库的所有 FileTable 目录名称中唯一。</span><span class="sxs-lookup"><span data-stu-id="e635e-126">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="e635e-127">无论当前排序规则设置如何，唯一性比较都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e635e-127">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="e635e-128">如果您创建 FileTable 时没有提供目录名称，则 FileTable 自身的名称将用作目录名称。</span><span class="sxs-lookup"><span data-stu-id="e635e-128">If you do not provide a directory name when you create the FileTable, then the name of the FileTable itself is used as the directory name.</span></span>  
  
2.  <span data-ttu-id="e635e-129">**FILETABLE_COLLATE_FILENAME**。</span><span class="sxs-lookup"><span data-stu-id="e635e-129">**FILETABLE_COLLATE_FILENAME**.</span></span> <span data-ttu-id="e635e-130">指定要应用于 FileTable 的“名称”  列的排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="e635e-130">Specifies the name of the collation to be applied to the **Name** column in the FileTable.</span></span>  
  
    1.  <span data-ttu-id="e635e-131">指定的排序规则必须 **不区分大小写** ，以符合 Windows 文件命名语义。</span><span class="sxs-lookup"><span data-stu-id="e635e-131">The specified collation must be **case-insensitive** to comply with Windows file naming semantics.</span></span>  
  
    2.  <span data-ttu-id="e635e-132">如果未提供 **FILETABLE_COLLATE_FILENAME**的值，或指定了 **database_default**，则该列继承当前数据库的排序规则。</span><span class="sxs-lookup"><span data-stu-id="e635e-132">If you do not provide a value for **FILETABLE_COLLATE_FILENAME**, or you specify **database_default**, the column inherits the collation of the current database.</span></span> <span data-ttu-id="e635e-133">如果当前数据库排序规则区分大小写，将引发错误， **CREATE TABLE** 操作将失败。</span><span class="sxs-lookup"><span data-stu-id="e635e-133">If the current database collation is case-sensitive, an error is raised and the **CREATE TABLE** operation fails.</span></span>  
  
3.  <span data-ttu-id="e635e-134">您还可以指定要用于 3 个主键的名称和自动创建的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="e635e-134">You can also specify the names to be used for the 3 primary key and unique constraints that are automatically created.</span></span> <span data-ttu-id="e635e-135">如果您不提供名称，则系统会生成名称，如本主题后面所述。</span><span class="sxs-lookup"><span data-stu-id="e635e-135">If you do not provide names, then the system generates names as described later in this topic.</span></span>  
  
    -   <span data-ttu-id="e635e-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="e635e-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="e635e-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="e635e-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="e635e-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="e635e-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
 <span data-ttu-id="e635e-139">**示例**</span><span class="sxs-lookup"><span data-stu-id="e635e-139">**Examples**</span></span>  
  
 <span data-ttu-id="e635e-140">以下示例将创建一个新的 FileTable，并为 **FILETABLE_DIRECTORY** 和 **FILETABLE_COLLATE_FILENAME**指定用户定义的值。</span><span class="sxs-lookup"><span data-stu-id="e635e-140">The following example creates a new FileTable and specifies user-defined values for both **FILETABLE_DIRECTORY** and **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable  
    WITH (   
          FileTable_Directory = 'DocumentTable',  
          FileTable_Collate_Filename = database_default  
         );  
GO  
```  
  
 <span data-ttu-id="e635e-141">下面的示例也创建一个新的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-141">The following example also creates a new FileTable.</span></span> <span data-ttu-id="e635e-142">由于没有指定用户定义的值，因此 **FILETABLE_DIRECTORY** 的值将成为 FileTable 的名称， **FILETABLE_COLLATE_FILENAME** 的值将成为 database_default，主键和唯一约束将收到系统生成的名称。</span><span class="sxs-lookup"><span data-stu-id="e635e-142">Since user-defined values are not specified, the value of **FILETABLE_DIRECTORY** becomes the name of the FileTable, the value of **FILETABLE_COLLATE_FILENAME** becomes database_default, and the primary key and unique contraints receive system-generated names.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable;  
GO  
```  
  
 <span data-ttu-id="e635e-143">**使用 SQL Server Management Studio 创建 FileTable**</span><span class="sxs-lookup"><span data-stu-id="e635e-143">**Create a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="e635e-144">在对象资源管理器中，展开所选数据库下的对象，然后右键单击“Tables”文件夹，选择“新建 FileTable”。</span><span class="sxs-lookup"><span data-stu-id="e635e-144">In Object Explorer, expand the objects under the selected database, then right-click on the **Tables** folder, and then select **New FileTable**.</span></span>  
  
 <span data-ttu-id="e635e-145">此选项将打开一个新的脚本窗口，其中包含一个 Transact-SQL 脚本模板，您可以自定义和运行此模板以创建 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-145">This option opens a new script window which contains a Transact-SQL script template that you can customize and run to create a FileTable.</span></span> <span data-ttu-id="e635e-146">使用 **“查询”** 菜单上的 **“指定模板参数的值”** 选择可轻松指定脚本。</span><span class="sxs-lookup"><span data-stu-id="e635e-146">Use the **Specify Values for Template Parameters** option on the **Query** menu to customize the script easily.</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-filetable"></a><a name="ReqCreate"></a> <span data-ttu-id="e635e-147">创建 FileTable 的要求和限制</span><span class="sxs-lookup"><span data-stu-id="e635e-147">Requirements and Restrictions for Creating a FileTable</span></span>  
  
-   <span data-ttu-id="e635e-148">不能更改现有表以将其转换为 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-148">You cannot alter an existing table to convert it into a FileTable.</span></span>  
  
-   <span data-ttu-id="e635e-149">先前在数据库级别指定的父目录还必须具有非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e635e-149">The parent directory previously specified at the database level must have a non-null value.</span></span> <span data-ttu-id="e635e-150">有关指定数据库级目录的信息，请参阅 [启用 FileTable 的先决条件](enable-the-prerequisites-for-filetable.md)。</span><span class="sxs-lookup"><span data-stu-id="e635e-150">For information about specifying the database-level directory, see [Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md).</span></span>  
  
-   <span data-ttu-id="e635e-151">由于一个 FileTable 包含一个 FILESTREAM 列，因此，FileTable 需要有效的 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="e635e-151">A FileTable requires a valid FILESTREAM filegroup, since a FileTable contains a FILESTREAM column.</span></span> <span data-ttu-id="e635e-152">可以指定有效的 FILESTREAM 文件组作为 **CREATE TABLE** 命令的一部分以创建 FileTable（可选）。</span><span class="sxs-lookup"><span data-stu-id="e635e-152">You can optionally specify a valid FILESTREAM filegroup as part of the **CREATE TABLE** command for creating a FileTable.</span></span> <span data-ttu-id="e635e-153">如果未指定文件组，则 FileTable 使用数据库的默认 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="e635e-153">If you do not specify a filegroup, then the FileTable uses the default FILESTREAM filegroup for the database.</span></span> <span data-ttu-id="e635e-154">如果数据库没有 FILESTREAM 文件组，将引发错误。</span><span class="sxs-lookup"><span data-stu-id="e635e-154">If the database does not have a FILESTREAM filegroup, then an error is raised.</span></span>  
  
-   <span data-ttu-id="e635e-155">不能将表约束作为 CREATE TABLE…AS FILETABLE 语句的一部分创建。</span><span class="sxs-lookup"><span data-stu-id="e635e-155">You cannot create a table constraint as part of a **CREATE TABLE...AS FILETABLE** statement.</span></span> <span data-ttu-id="e635e-156">但是，您以后可以使用 **ALTER TABLE** 语句添加该约束。</span><span class="sxs-lookup"><span data-stu-id="e635e-156">However you can add the constraint later by using an **ALTER TABLE** statement.</span></span>  
  
-   <span data-ttu-id="e635e-157">不能在 **tempdb** 数据库或任何其他系统数据库中创建 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-157">You cannot create a FileTable in the **tempdb** database or in any of the other system databases.</span></span>  
  
-   <span data-ttu-id="e635e-158">不能将 FileTable 作为临时表创建。</span><span class="sxs-lookup"><span data-stu-id="e635e-158">You cannot create a FileTable as a temporary table.</span></span>  
  
##  <a name="altering-a-filetable"></a><a name="BasicsAlter"></a> <span data-ttu-id="e635e-159">更改 FileTable</span><span class="sxs-lookup"><span data-stu-id="e635e-159">Altering a FileTable</span></span>  
 <span data-ttu-id="e635e-160">由于 FileTable 具有预定义的固定架构，您不能添加或更改它的列。</span><span class="sxs-lookup"><span data-stu-id="e635e-160">Since a FileTable has a pre-defined and fixed schema, you cannot add or change its columns.</span></span> <span data-ttu-id="e635e-161">但是，可以将自定义索引、触发器、约束和其他选项添加到 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-161">However, you can add custom indexes, triggers, constraints, and other options to a FileTable.</span></span>  
  
 <span data-ttu-id="e635e-162">有关使用 ALTER TABLE 语句启用或禁用 FileTable 命名空间（包括系统定义的约束）的信息，请参阅 [管理 FileTables](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="e635e-162">For information about using the ALTER TABLE statement to enable or disable the FileTable namespace, including the system-defined constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-change-the-directory-for-a-filetable"></a><a name="HowToChange"></a> <span data-ttu-id="e635e-163">如何：更改 FileTable 的目录</span><span class="sxs-lookup"><span data-stu-id="e635e-163">How To: Change the Directory for a FileTable</span></span>  
 <span data-ttu-id="e635e-164">**使用 Transact-SQL 更改 FileTable 的目录**</span><span class="sxs-lookup"><span data-stu-id="e635e-164">**Change the Directory for a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="e635e-165">调用 ALTER TABLE 语句并为 **FILETABLE_DIRECTORY** SET 选项提供一个有效的新值。</span><span class="sxs-lookup"><span data-stu-id="e635e-165">Call the ALTER TABLE statement and provide a valid new value for the **FILETABLE_DIRECTORY** SET option.</span></span>  
  
 <span data-ttu-id="e635e-166">**示例**</span><span class="sxs-lookup"><span data-stu-id="e635e-166">**Example**</span></span>  
  
```sql  
ALTER TABLE filetable_name  
    SET ( FILETABLE_DIRECTORY = N'directory_name' );  
GO  
```  
  
 <span data-ttu-id="e635e-167">**使用 SQL Server Management Studio 更改 FileTable 的目录**</span><span class="sxs-lookup"><span data-stu-id="e635e-167">**Change the Directory for a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="e635e-168">在对象资源管理器中，右键单击 FileTable，然后选择“属性”以打开“表属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="e635e-168">In Object Explorer, right-click on the FileTable and select **Properties** to open the **Table Properties** dialog box.</span></span> <span data-ttu-id="e635e-169">在 **FileTable** 页上，为 **“FileTable 目录名称”** 输入新值。</span><span class="sxs-lookup"><span data-stu-id="e635e-169">On the **FileTable** page, enter a new value for **FileTable directory name**.</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-a-filetable"></a><a name="ReqAlter"></a> <span data-ttu-id="e635e-170">更改 FileTable 的要求和限制</span><span class="sxs-lookup"><span data-stu-id="e635e-170">Requirements and Restrictions for Altering a FileTable</span></span>  
  
-   <span data-ttu-id="e635e-171">你不能更改 **FILETABLE_COLLATE_FILENAME**的值。</span><span class="sxs-lookup"><span data-stu-id="e635e-171">You cannot alter the value of **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
-   <span data-ttu-id="e635e-172">不能更改、删除或禁用 FileTable 的系统定义的列。</span><span class="sxs-lookup"><span data-stu-id="e635e-172">You cannot change, drop, or disable the system-defined columns of a FileTable.</span></span>  
  
-   <span data-ttu-id="e635e-173">不能将新的用户列、计算列或持久化计算列添加到 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-173">You cannot add new user columns, computed columns, or persisted computed columns to a FileTable.</span></span>  
  
##  <a name="dropping-a-filetable"></a><a name="BasicsDrop"></a> <span data-ttu-id="e635e-174">删除 FileTable</span><span class="sxs-lookup"><span data-stu-id="e635e-174">Dropping a FileTable</span></span>  
 <span data-ttu-id="e635e-175">可以使用 [DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql) 语句的普通语法删除 FileTable。</span><span class="sxs-lookup"><span data-stu-id="e635e-175">You can drop a FileTable by using the ordinary syntax for the [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="e635e-176">当您删除 FileTable 时，同时也会删除下列对象：</span><span class="sxs-lookup"><span data-stu-id="e635e-176">When you drop a FileTable, the following objects are also dropped:</span></span>  
  
-   <span data-ttu-id="e635e-177">此时还将删除 FileTable 的所有列以及与该表关联的所有对象，如索引、约束和触发器。</span><span class="sxs-lookup"><span data-stu-id="e635e-177">All the columns of the FileTable and all the objects associated with the table, such as indexes, constraints, and triggers, are also dropped.</span></span>  
  
-   <span data-ttu-id="e635e-178">FileTable 目录及其包含的子目录将从数据库的 FILESTREAM 文件和目录层次结构中消失。</span><span class="sxs-lookup"><span data-stu-id="e635e-178">The FileTable directory and the sub-directories that it contained disappear from the FILESTREAM file and directory hierarchy of the database.</span></span>  
  
 <span data-ttu-id="e635e-179">如果 FileTable 的文件命名空间中有打开的文件句柄，DROP TABLE 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="e635e-179">The DROP TABLE command fails if there are open file handles in the FileTable's file namespace.</span></span> <span data-ttu-id="e635e-180">有关关闭打开的句柄的信息，请参阅 [管理 FileTable](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="e635e-180">For information about closing open handles, see [Manage FileTables](manage-filetables.md).</span></span>  
  
##  <a name="other-database-objects-are-created-when-you-create-a-filetable"></a><a name="BasicsOtherObjects"></a> <span data-ttu-id="e635e-181">创建 FileTable 时创建其他数据库对象</span><span class="sxs-lookup"><span data-stu-id="e635e-181">Other Database Objects Are Created When You Create a FileTable</span></span>  
 <span data-ttu-id="e635e-182">创建新的 FileTable 时，还会创建一些系统定义的索引和约束。</span><span class="sxs-lookup"><span data-stu-id="e635e-182">When you create a new FileTable, some system-defined indexes and constraints are also created.</span></span> <span data-ttu-id="e635e-183">您不能更改或删除这些对象；仅当删除 FileTable 本身时，它们才消失。</span><span class="sxs-lookup"><span data-stu-id="e635e-183">You cannot alter or drop these objects; they disappear only when the FileTable itself is dropped.</span></span> <span data-ttu-id="e635e-184">若要查看这些对象的列表，请查询目录视图 [sys.filetable_system_defined_objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e635e-184">To see the list of these objects, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
--View all objects for all filetables, unsorted  
SELECT * FROM sys.filetable_system_defined_objects;  
GO  
  
--View sorted list with friendly names  
SELECT OBJECT_NAME(parent_object_id) AS 'FileTable', OBJECT_NAME(object_id) AS 'System-defined Object'  
    FROM sys.filetable_system_defined_objects  
    ORDER BY FileTable, 'System-defined Object';  
GO  
```  
  
 <span data-ttu-id="e635e-185">**创建新的 FileTable 时创建的索引**</span><span class="sxs-lookup"><span data-stu-id="e635e-185">**Indexes that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="e635e-186">创建新的 FileTable 时，还会创建以下系统定义的索引：</span><span class="sxs-lookup"><span data-stu-id="e635e-186">When you create a new FileTable, the following system-defined indexes are also created:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e635e-187">**“列”**</span><span class="sxs-lookup"><span data-stu-id="e635e-187">**Columns**</span></span>|<span data-ttu-id="e635e-188">**索引类型**</span><span class="sxs-lookup"><span data-stu-id="e635e-188">**Index type**</span></span>|  
|<span data-ttu-id="e635e-189">[path_locator] ASC</span><span class="sxs-lookup"><span data-stu-id="e635e-189">[path_locator] ASC</span></span>|<span data-ttu-id="e635e-190">主键，非聚集</span><span class="sxs-lookup"><span data-stu-id="e635e-190">Primary Key, nonclustered</span></span>|  
|<span data-ttu-id="e635e-191">[parent_path_locator] ASC，</span><span class="sxs-lookup"><span data-stu-id="e635e-191">[parent_path_locator] ASC,</span></span><br /><br /> <span data-ttu-id="e635e-192">[name] ASC</span><span class="sxs-lookup"><span data-stu-id="e635e-192">[name] ASC</span></span>|<span data-ttu-id="e635e-193">唯一，非聚集</span><span class="sxs-lookup"><span data-stu-id="e635e-193">Unique, nonclustered</span></span>|  
|<span data-ttu-id="e635e-194">[stream_id] ASC</span><span class="sxs-lookup"><span data-stu-id="e635e-194">[stream_id] ASC</span></span>|<span data-ttu-id="e635e-195">唯一，非聚集</span><span class="sxs-lookup"><span data-stu-id="e635e-195">Unique, nonclustered</span></span>|  
  
 <span data-ttu-id="e635e-196">**创建新的 FileTable 时创建的约束**</span><span class="sxs-lookup"><span data-stu-id="e635e-196">**Constraints that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="e635e-197">创建新的 FileTable 时，还会创建以下系统定义的约束：</span><span class="sxs-lookup"><span data-stu-id="e635e-197">When you create a new FileTable, the following system-defined constraints are also created:</span></span>  
  
|<span data-ttu-id="e635e-198">约束</span><span class="sxs-lookup"><span data-stu-id="e635e-198">Constraints</span></span>|<span data-ttu-id="e635e-199">强制执行</span><span class="sxs-lookup"><span data-stu-id="e635e-199">Enforces</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="e635e-200">以下列的默认约束：</span><span class="sxs-lookup"><span data-stu-id="e635e-200">Default constraints on the following columns:</span></span><br /><br /> <span data-ttu-id="e635e-201">**creation_time**</span><span class="sxs-lookup"><span data-stu-id="e635e-201">**creation_time**</span></span> <br /> <span data-ttu-id="e635e-202">**is_archive**</span><span class="sxs-lookup"><span data-stu-id="e635e-202">**is_archive**</span></span> <br /> <span data-ttu-id="e635e-203">**is_directory**</span><span class="sxs-lookup"><span data-stu-id="e635e-203">**is_directory**</span></span> <br /> <span data-ttu-id="e635e-204">**is_hidden**</span><span class="sxs-lookup"><span data-stu-id="e635e-204">**is_hidden**</span></span> <br /> <span data-ttu-id="e635e-205">**is_offline**</span><span class="sxs-lookup"><span data-stu-id="e635e-205">**is_offline**</span></span> <br /> <span data-ttu-id="e635e-206">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="e635e-206">**is_readonly**</span></span> <br /> <span data-ttu-id="e635e-207">**is_system**</span><span class="sxs-lookup"><span data-stu-id="e635e-207">**is_system**</span></span> <br /> <span data-ttu-id="e635e-208">**is_temporary**</span><span class="sxs-lookup"><span data-stu-id="e635e-208">**is_temporary**</span></span> <br /> <span data-ttu-id="e635e-209">**last_access_time**</span><span class="sxs-lookup"><span data-stu-id="e635e-209">**last_access_time**</span></span> <br /> <span data-ttu-id="e635e-210">**last_write_time**</span><span class="sxs-lookup"><span data-stu-id="e635e-210">**last_write_time**</span></span> <br /> <span data-ttu-id="e635e-211">**path_locator**</span><span class="sxs-lookup"><span data-stu-id="e635e-211">**path_locator**</span></span> <br /> <span data-ttu-id="e635e-212">**stream_id**</span><span class="sxs-lookup"><span data-stu-id="e635e-212">**stream_id**</span></span>|<span data-ttu-id="e635e-213">系统定义的默认约束强制采用指定列的默认值。</span><span class="sxs-lookup"><span data-stu-id="e635e-213">The system-defined default constraints enforce default values for the specified columns.</span></span>|  
|<span data-ttu-id="e635e-214">检查约束</span><span class="sxs-lookup"><span data-stu-id="e635e-214">Check constraints</span></span>|<span data-ttu-id="e635e-215">系统定义的检查约束强制执行下列要求：</span><span class="sxs-lookup"><span data-stu-id="e635e-215">The system-defined check constraints enforce the following requirements:</span></span><br /><br /> <span data-ttu-id="e635e-216">有效的文件名。</span><span class="sxs-lookup"><span data-stu-id="e635e-216">Valid filenames.</span></span><br /><br /> <span data-ttu-id="e635e-217">有效的文件属性。</span><span class="sxs-lookup"><span data-stu-id="e635e-217">Valid file attributes.</span></span><br /><br /> <span data-ttu-id="e635e-218">父对象必须是目录。</span><span class="sxs-lookup"><span data-stu-id="e635e-218">Parent object must be a directory.</span></span><br /><br /> <span data-ttu-id="e635e-219">命名空间层次结构在文件操作过程中锁定。</span><span class="sxs-lookup"><span data-stu-id="e635e-219">Namespace hierarchy is locked during file manipulation.</span></span>|  
  
 <span data-ttu-id="e635e-220">**系统定义的约束的命名约定**</span><span class="sxs-lookup"><span data-stu-id="e635e-220">**Naming convention for the system-defined constraints**</span></span>  
 <span data-ttu-id="e635e-221">上述系统定义的约束采用 \<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier> 格式命名，其中：</span><span class="sxs-lookup"><span data-stu-id="e635e-221">The system-defined constraints described above are named in the format **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** where:</span></span>  
  
-   <span data-ttu-id="e635e-222">*<constraint_type>* 为 CK（检查约束）、DF（默认约束）、FK（外键）、PK（主键）或 UQ（唯一约束）。</span><span class="sxs-lookup"><span data-stu-id="e635e-222">*<constraint_type>* is CK (check constraint), DF (default constraint), FK (foreign key), PK (primary key), or UQ (unique constraint).</span></span>  
  
-   <span data-ttu-id="e635e-223">\<uniquifier> 是系统生成的字符串以使名称唯一。</span><span class="sxs-lookup"><span data-stu-id="e635e-223">*\<uniquifier>* is a system-generated string to make the name unique.</span></span> <span data-ttu-id="e635e-224">此字符串中可能包含 FileTable 的名称和唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="e635e-224">This string may contain the FileTable name and a unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e635e-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e635e-225">See Also</span></span>  
 [<span data-ttu-id="e635e-226">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="e635e-226">Manage FileTables</span></span>](manage-filetables.md)  
  
  
