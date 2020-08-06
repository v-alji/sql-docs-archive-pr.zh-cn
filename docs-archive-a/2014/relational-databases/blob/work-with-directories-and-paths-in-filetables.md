---
title: 在 FileTable 中使用目录和路径 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], directories
ms.assetid: f1e45900-bea0-4f6f-924e-c11e1f98ab62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4641159e894b764cbee4d7f02085f3ceb8e6d87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682885"
---
# <a name="work-with-directories-and-paths-in-filetables"></a><span data-ttu-id="79ade-102">在 FileTable 中使用目录和路径</span><span class="sxs-lookup"><span data-stu-id="79ade-102">Work with Directories and Paths in FileTables</span></span>
  <span data-ttu-id="79ade-103">说明 FileTable 中用于存储文件的目录结构。</span><span class="sxs-lookup"><span data-stu-id="79ade-103">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
##  <a name="how-to-work-with-directories-and-paths-in-filetables"></a><a name="HowToDirectories"></a> <span data-ttu-id="79ade-104">如何：在 FileTable 中使用目录和路径</span><span class="sxs-lookup"><span data-stu-id="79ade-104">How To: Work with Directories and Paths in FileTables</span></span>  
 <span data-ttu-id="79ade-105">您可以使用以下 3 个函数以便在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中使用 FileTable 目录：</span><span class="sxs-lookup"><span data-stu-id="79ade-105">You can use the following 3 functions to work with FileTable directories in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
|<span data-ttu-id="79ade-106">为得到这一结果</span><span class="sxs-lookup"><span data-stu-id="79ade-106">To get this result</span></span>|<span data-ttu-id="79ade-107">使用此函数</span><span class="sxs-lookup"><span data-stu-id="79ade-107">Use this function</span></span>|  
|------------------------|-----------------------|  
|<span data-ttu-id="79ade-108">获取特定 FileTable 或当前数据库的根级 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="79ade-108">Get the root-level UNC path for a specific FileTable or for the current database.</span></span>|[<span data-ttu-id="79ade-109">FileTableRootPath (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="79ade-109">FileTableRootPath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|  
|<span data-ttu-id="79ade-110">获取 FileTable 中文件或目录的绝对或相对 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="79ade-110">Get an absolute or relative UNC path for a file or directory in a FileTable.</span></span>|[<span data-ttu-id="79ade-111">GetFileNamespacePath (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="79ade-111">GetFileNamespacePath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|  
|<span data-ttu-id="79ade-112">通过提供路径，获取 FileTable 中指定文件或目录的路径定位器 ID 值。</span><span class="sxs-lookup"><span data-stu-id="79ade-112">Get the path locator ID value for the specified file or directory in a FileTable, by providing the path.</span></span>|[<span data-ttu-id="79ade-113">GetPathLocator (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="79ade-113">GetPathLocator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|  
  
##  <a name="how-to-use-relative-paths-for-portable-code"></a><a name="BestPracticeRelativePaths"></a> <span data-ttu-id="79ade-114">如何：使用相对路径编写可移植代码</span><span class="sxs-lookup"><span data-stu-id="79ade-114">How to: Use Relative Paths for Portable Code</span></span>  
 <span data-ttu-id="79ade-115">若要使代码和应用程序独立于当前的计算机和数据库，应避免编写依赖于绝对文件路径的代码。</span><span class="sxs-lookup"><span data-stu-id="79ade-115">To keep code and applications independent of the current computer and database, avoid writing code that relies on absolute file paths.</span></span> <span data-ttu-id="79ade-116">可通过使用 [FileTableRootPath (Transact-SQL)](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) 和 [GetFileNamespacePath (Transact-SQL)](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)函数组合在运行时获取文件的完整路径，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="79ade-116">Instead, get the complete path for a file at run time by using the [FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) and [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)) functions together, as shown in the following example.</span></span> <span data-ttu-id="79ade-117">默认情况下，`GetFileNamespacePath` 函数返回数据库根路径下的文件的相对路径。</span><span class="sxs-lookup"><span data-stu-id="79ade-117">By default, the `GetFileNamespacePath` function returns the relative path of the file under the root path for the database.</span></span>  
  
```sql  
USE database_name;  
DECLARE @root nvarchar(100);  
DECLARE @fullpath nvarchar(1000);  
  
SELECT @root = FileTableRootPath();  
SELECT @fullpath = @root + file_stream.GetFileNamespacePath()  
    FROM filetable_name  
    WHERE name = N'document_name';  
  
PRINT @fullpath;  
GO  
```  
  
##  <a name="important-restrictions"></a><a name="restrictions"></a> <span data-ttu-id="79ade-118">重要限制</span><span class="sxs-lookup"><span data-stu-id="79ade-118">Important restrictions</span></span>  
  
###  <a name="nesting-level"></a><a name="nesting"></a> <span data-ttu-id="79ade-119">嵌套级别</span><span class="sxs-lookup"><span data-stu-id="79ade-119">Nesting level</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79ade-120">您不能在 FileTable 目录中存储超过 15 个级别的子目录。</span><span class="sxs-lookup"><span data-stu-id="79ade-120">You cannot store more than 15 levels of subdirectories in the FileTable directory.</span></span> <span data-ttu-id="79ade-121">在您存储 15 个级别的子目录时，最下面的一级不能包含文件，因为这些文件将代表另外一个级别。</span><span class="sxs-lookup"><span data-stu-id="79ade-121">When you store 15 levels of subdirectories, then the lowest level cannot contain files, since these files would represent an additional level.</span></span>  
  
###  <a name="length-of-full-path-name"></a><a name="fqnlength"></a> <span data-ttu-id="79ade-122">完整路径名的长度</span><span class="sxs-lookup"><span data-stu-id="79ade-122">Length of full path name</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79ade-123">NTFS 文件系统支持远远超过 Windows 外壳程序和大多数 Windows API 的 260 个字符限制的路径名。</span><span class="sxs-lookup"><span data-stu-id="79ade-123">The NTFS file system supports path names that are much longer than the 260-character limit of the Windows shell and most Windows APIs.</span></span> <span data-ttu-id="79ade-124">因此，使用 Transact-SQL 在 FileTable 的文件层次结构中创建的文件有可能无法使用 Windows 资源管理器或很多其他 Windows 应用程序查看或打开，原因是这些文件的完整路径名称超过了 260 个字符。</span><span class="sxs-lookup"><span data-stu-id="79ade-124">Therefore it is possible to create files in the file hierarchy of a FileTable by using Transact-SQL that you cannot view or open with Windows Explorer or many other Windows applications, because the full path name exceeds 260 characters.</span></span> <span data-ttu-id="79ade-125">但是，您可使用 Transact-SQL 继续访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="79ade-125">However you can continue to access these files by using Transact-SQL.</span></span>  
  
##  <a name="the-full-path-to-an-item-stored-in-a-filetable"></a><a name="fullpath"></a> <span data-ttu-id="79ade-126">FileTable 中存储的项的完整路径</span><span class="sxs-lookup"><span data-stu-id="79ade-126">The full path to an item stored in a FileTable</span></span>  
 <span data-ttu-id="79ade-127">FileTable 中存储的文件或目录的完整路径用以下元素开头：</span><span class="sxs-lookup"><span data-stu-id="79ade-127">The full path to a file or directory stored in a FileTable begins with the following elements:</span></span>  
  
1.  <span data-ttu-id="79ade-128">为在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例级别进行 FILESTREAM 文件 I/O 访问启用的共享区。</span><span class="sxs-lookup"><span data-stu-id="79ade-128">The share enabled for FILESTREAM file I/O access at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level.</span></span>  
  
2.  <span data-ttu-id="79ade-129">在数据库级别指定的 **DIRECTORY_NAME** 。</span><span class="sxs-lookup"><span data-stu-id="79ade-129">The **DIRECTORY_NAME** specified at the database level.</span></span>  
  
3.  <span data-ttu-id="79ade-130">在 FileTable 级别指定的 **FILETABLE_DIRECTORY** 。</span><span class="sxs-lookup"><span data-stu-id="79ade-130">The **FILETABLE_DIRECTORY** specified at the FileTable level.</span></span>  
  
 <span data-ttu-id="79ade-131">生成的层次结构如下所示：</span><span class="sxs-lookup"><span data-stu-id="79ade-131">The resulting hierarchy looks like this:</span></span>  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\`  
  
 <span data-ttu-id="79ade-132">此目录层次结构构成了 FileTable 的文件命名空间的根。</span><span class="sxs-lookup"><span data-stu-id="79ade-132">This directory hierarchy forms the root of the FileTable's file namespace.</span></span> <span data-ttu-id="79ade-133">在此目录层次结构下，FileTable 的 FILESTREAM 数据作为文件存储，并且存储为也包含文件和子目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="79ade-133">Under this directory hierarchy, the FILESTREAM data for the FileTable is stored as files, and as subdirectories which can also contain files and subdirectories.</span></span>  
  
 <span data-ttu-id="79ade-134">请务必记住，在此实例级别 FILESTREAM 共享区下创建的目录层次结构是虚拟目录层次结构。</span><span class="sxs-lookup"><span data-stu-id="79ade-134">It is important to keep in mind that the directory hierarchy created under the instance-level FILESTREAM share is a virtual directory hierarchy.</span></span> <span data-ttu-id="79ade-135">该层次结构存储于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中，并且在物理上不在 NTFS 文件系统中表示。</span><span class="sxs-lookup"><span data-stu-id="79ade-135">This hierarchy is stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and is not represented physically in the NTFS file system.</span></span> <span data-ttu-id="79ade-136">访问 FILESTREAM 共享区之下和其包含的 FileTable 中的文件和目录的所有操作都将被文件系统中嵌入的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件拦截和处理。</span><span class="sxs-lookup"><span data-stu-id="79ade-136">All operations that access files and directories under the FILESTREAM share and in the FileTables that it contains are intercepted and handled by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component embedded in the file system.</span></span>  
  
##  <a name="the-semantics-of-the-root-directories-at-the-instance-database-and-filetable-levels"></a><a name="roots"></a> <span data-ttu-id="79ade-137">实例级、数据库级和 FileTable 级根目录的语义</span><span class="sxs-lookup"><span data-stu-id="79ade-137">The semantics of the root directories at the instance, database, and FileTable levels</span></span>  
 <span data-ttu-id="79ade-138">此目录层次结构遵循下面的语义：</span><span class="sxs-lookup"><span data-stu-id="79ade-138">This directory hierarchy observes the following semantics:</span></span>  
  
-   <span data-ttu-id="79ade-139">实例级别 FILESTREAM 共享区由管理员配置并且存储为服务器的属性。</span><span class="sxs-lookup"><span data-stu-id="79ade-139">The instance-level FILESTREAM share is configured by an administrator and stored as a property of the server.</span></span> <span data-ttu-id="79ade-140">您可以通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器，重命名该存储区。</span><span class="sxs-lookup"><span data-stu-id="79ade-140">You can rename this share by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="79ade-141">在重新启动服务器之前，重命名操作将不会生效。</span><span class="sxs-lookup"><span data-stu-id="79ade-141">A renaming operation does not take effect until the server is restarted.</span></span>  
  
-   <span data-ttu-id="79ade-142">在创建新的数据库时，数据库级别 **DIRECTORY_NAME** 默认为 Null。</span><span class="sxs-lookup"><span data-stu-id="79ade-142">The database-level **DIRECTORY_NAME** is null by default when you create a new database.</span></span> <span data-ttu-id="79ade-143">管理员可以通过使用 **ALTER DATABASE** 语句设置或更改此名称。</span><span class="sxs-lookup"><span data-stu-id="79ade-143">An administrator can set or change this name by using the **ALTER DATABASE** statement.</span></span> <span data-ttu-id="79ade-144">此名称在该实例中必须唯一（不区分大小写比较时）。</span><span class="sxs-lookup"><span data-stu-id="79ade-144">The name must be unique (in a case-insensitive comparison) in that instance.</span></span>  
  
-   <span data-ttu-id="79ade-145">在创建 FileTable 时，通常提供 **FILETABLE_DIRECTORY** 名称作为 **CREATE TABLE** 语句的一部分。</span><span class="sxs-lookup"><span data-stu-id="79ade-145">You typically provide the **FILETABLE_DIRECTORY** name as part of the **CREATE TABLE** statement when you create a FileTable.</span></span> <span data-ttu-id="79ade-146">您可以通过使用 **ALTER TABLE** 命令来更改此名称。</span><span class="sxs-lookup"><span data-stu-id="79ade-146">You can change this name by using the **ALTER TABLE** command.</span></span>  
  
-   <span data-ttu-id="79ade-147">不能通过文件 I/O 操作来重命名这些根目录。</span><span class="sxs-lookup"><span data-stu-id="79ade-147">You cannot rename these root directories through file I/O operations.</span></span>  
  
-   <span data-ttu-id="79ade-148">不能使用独占式文件句柄打开这些根目录。</span><span class="sxs-lookup"><span data-stu-id="79ade-148">You cannot open these root directories with exclusive file handles.</span></span>  
  
##  <a name="the-is_directory-column-in-the-filetable-schema"></a><a name="is_directory"></a> <span data-ttu-id="79ade-149">FileTable 架构中的 is_directory 列</span><span class="sxs-lookup"><span data-stu-id="79ade-149">The is_directory column in the FileTable schema</span></span>  
 <span data-ttu-id="79ade-150">下表说明 **is_directory** 列与包含 FileTable 中 FILESTREAM 数据的 **file_stream** 列之间的相互影响：</span><span class="sxs-lookup"><span data-stu-id="79ade-150">The following table describes the interaction between the **is_directory** column and the **file_stream** column that contains the FILESTREAM data in a FileTable.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="79ade-151">*is_directory* **value**</span><span class="sxs-lookup"><span data-stu-id="79ade-151">*is_directory* **value**</span></span>|<span data-ttu-id="79ade-152">*file_stream* **value**</span><span class="sxs-lookup"><span data-stu-id="79ade-152">*file_stream* **value**</span></span>|<span data-ttu-id="79ade-153">**行为**</span><span class="sxs-lookup"><span data-stu-id="79ade-153">**Behavior**</span></span>|  
|<span data-ttu-id="79ade-154">FALSE</span><span class="sxs-lookup"><span data-stu-id="79ade-154">FALSE</span></span>|<span data-ttu-id="79ade-155">Null</span><span class="sxs-lookup"><span data-stu-id="79ade-155">NULL</span></span>|<span data-ttu-id="79ade-156">这是将被系统定义的约束捕获的无效组合。</span><span class="sxs-lookup"><span data-stu-id="79ade-156">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
|<span data-ttu-id="79ade-157">FALSE</span><span class="sxs-lookup"><span data-stu-id="79ade-157">FALSE</span></span>|\<value>|<span data-ttu-id="79ade-158">该项表示一个文件。</span><span class="sxs-lookup"><span data-stu-id="79ade-158">The item represents a file.</span></span>|  
|<span data-ttu-id="79ade-159">TRUE</span><span class="sxs-lookup"><span data-stu-id="79ade-159">TRUE</span></span>|<span data-ttu-id="79ade-160">Null</span><span class="sxs-lookup"><span data-stu-id="79ade-160">NULL</span></span>|<span data-ttu-id="79ade-161">该项表示一个目录。</span><span class="sxs-lookup"><span data-stu-id="79ade-161">The item represents a directory.</span></span>|  
|<span data-ttu-id="79ade-162">TRUE</span><span class="sxs-lookup"><span data-stu-id="79ade-162">TRUE</span></span>|\<value>|<span data-ttu-id="79ade-163">这是将被系统定义的约束捕获的无效组合。</span><span class="sxs-lookup"><span data-stu-id="79ade-163">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
  
##  <a name="using-virtual-network-names-vnns-with-alwayson-availability-groups"></a><a name="alwayson"></a> <span data-ttu-id="79ade-164">将虚拟网络名称 (VNN) 用于 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="79ade-164">Using Virtual Network Names (VNNs) with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="79ade-165">在包含 FILESTREAM 或 FileTable 数据的数据库属于某一 AlwaysOn 可用性组时：</span><span class="sxs-lookup"><span data-stu-id="79ade-165">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="79ade-166">FILESTREAM 和 FileTable 函数接受或返回虚拟网络名称 (VNN)，而非计算机名称。</span><span class="sxs-lookup"><span data-stu-id="79ade-166">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="79ade-167">有关这些函数的详细信息，请参阅 [Filestream 和 FileTable 函数 (Transact-SQL)](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="79ade-167">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="79ade-168">通过文件系统 API 对 FILESTREAM 或 FileTable 数据进行的所有访问都应该使用 VNN，而非计算机名称。</span><span class="sxs-lookup"><span data-stu-id="79ade-168">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="79ade-169">有关详细信息，请参阅 [FILESTREAM 和 FileTable 与 AlwaysOn 可用性组 (SQL Server)](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="79ade-169">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ade-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79ade-170">See Also</span></span>  
 <span data-ttu-id="79ade-171">[启用 FileTable 的先决条件](enable-the-prerequisites-for-filetable.md) </span><span class="sxs-lookup"><span data-stu-id="79ade-171">[Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md) </span></span>  
 <span data-ttu-id="79ade-172">[创建、更改和删除 FileTable](create-alter-and-drop-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="79ade-172">[Create, Alter, and Drop FileTables](create-alter-and-drop-filetables.md) </span></span>  
 <span data-ttu-id="79ade-173">[使用 Transact-SQL 访问 FileTable](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="79ade-173">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="79ade-174">使用文件输入输出 API 访问 FileTable</span><span class="sxs-lookup"><span data-stu-id="79ade-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
