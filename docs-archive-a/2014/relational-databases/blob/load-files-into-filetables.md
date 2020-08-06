---
title: 将文件加载到 FileTable 中 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 43ea31523da2dfa8b387f68ce4f7c7f07868dd6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692965"
---
# <a name="load-files-into-filetables"></a><span data-ttu-id="69328-102">将文件加载到 FileTable 中</span><span class="sxs-lookup"><span data-stu-id="69328-102">Load Files into FileTables</span></span>
  <span data-ttu-id="69328-103">说明如何将文件加载或迁移到 FileTable 中。</span><span class="sxs-lookup"><span data-stu-id="69328-103">Describes how to load or migrate files into FileTables.</span></span>  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> <span data-ttu-id="69328-104">将文件加载或迁移到 FileTable</span><span class="sxs-lookup"><span data-stu-id="69328-104">Loading or Migrating Files into a FileTable</span></span>  
 <span data-ttu-id="69328-105">您选择用于将文件加载或迁移到 FileTable 的方法取决于当前存储文件的位置。</span><span class="sxs-lookup"><span data-stu-id="69328-105">The method that you choose for loading or migrating files into a FileTable depends on where the files are currently stored.</span></span>  
  
|<span data-ttu-id="69328-106">文件的当前位置</span><span class="sxs-lookup"><span data-stu-id="69328-106">Current location of files</span></span>|<span data-ttu-id="69328-107">用于迁移的选项</span><span class="sxs-lookup"><span data-stu-id="69328-107">Options for migration</span></span>|  
|-------------------------------|---------------------------|  
|<span data-ttu-id="69328-108">文件当前存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="69328-108">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69328-109">不识别文件。</span><span class="sxs-lookup"><span data-stu-id="69328-109">has no knowledge of the files.</span></span>|<span data-ttu-id="69328-110">由于 FileTable 显示为 Windows 文件系统中的文件夹，您可以使用移动或复制文件的任何方法轻松地将文件加载到新的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="69328-110">Since a FileTable appears as a folder in the Windows file system, you can easily load files into a new FileTable by using any of the available methods for moving or copying files.</span></span> <span data-ttu-id="69328-111">这些方法包括 Windows 资源管理器、包括 xcopy 和 robocopy 在内的命令行选项，以及自定义脚本或应用程序。</span><span class="sxs-lookup"><span data-stu-id="69328-111">These methods include Windows Explorer, command line options including xcopy and robocopy, and custom scripts or applications.</span></span><br /><br /> <span data-ttu-id="69328-112">不能将现有文件夹转换为 FileTable。</span><span class="sxs-lookup"><span data-stu-id="69328-112">You cannot convert an existing folder to a FileTable.</span></span>|  
|<span data-ttu-id="69328-113">文件当前存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="69328-113">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69328-114">包含一个元数据表，该表中包含指向文件的指针。</span><span class="sxs-lookup"><span data-stu-id="69328-114">contains a table of metadata that contains pointers to the files.</span></span>|<span data-ttu-id="69328-115">第一步是使用上文所述的方法之一移动或复制文件。</span><span class="sxs-lookup"><span data-stu-id="69328-115">The first step is to move or copy the files by using one of the methods mentioned above.</span></span><br /><br /> <span data-ttu-id="69328-116">第二步是更新现有元数据的表以指向该文件的新位置。</span><span class="sxs-lookup"><span data-stu-id="69328-116">The second step is to update the existing table of metadata to point to the new location of the files.</span></span><br /><br /> <span data-ttu-id="69328-117">有关详细信息，请参阅本主题中的 [示例：将文件从文件系统迁移到 FileTable](#HowToMigrateFiles) 。</span><span class="sxs-lookup"><span data-stu-id="69328-117">For more information, see [Example: Migrating Files from the File System into a FileTable](#HowToMigrateFiles) in this topic.</span></span>|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> <span data-ttu-id="69328-118">如何：将文件加载到 FileTable 中</span><span class="sxs-lookup"><span data-stu-id="69328-118">How To: Load Files into a FileTable</span></span>  
 <span data-ttu-id="69328-119">可用于将文件加载到 FileTable 的方法包括：</span><span class="sxs-lookup"><span data-stu-id="69328-119">The methods that you can use to load files into a FileTable include the following:</span></span>  
  
-   <span data-ttu-id="69328-120">在 Windows 资源管理器中将文件从源文件夹拖放到新的 FileTable 文件夹。</span><span class="sxs-lookup"><span data-stu-id="69328-120">Drag and drop files from the source folders to the new FileTable folder in Windows Explorer.</span></span>  
  
-   <span data-ttu-id="69328-121">从命令提示符下、批处理文件或脚本中使用命令行选项（如 MOVE、COPY、XCOPY 或 ROBOCOPY）。</span><span class="sxs-lookup"><span data-stu-id="69328-121">Use command line options such as MOVE, COPY, XCOPY, or ROBOCOPY from the command prompt or in a batch file or script.</span></span>  
  
-   <span data-ttu-id="69328-122">用 C# 或 Visual Basic.NET 编写一个自定义应用程序，该应用程序使用 **System.IO** 命名空间的方法来移动或复制文件。</span><span class="sxs-lookup"><span data-stu-id="69328-122">Write a custom application in C# or Visual Basic.NET that uses methods from the **System.IO** namespace to move or copy the files.</span></span>  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> <span data-ttu-id="69328-123">示例：将文件从文件系统迁移到 FileTable</span><span class="sxs-lookup"><span data-stu-id="69328-123">Example: Migrating Files from the File System into a FileTable</span></span>  
 <span data-ttu-id="69328-124">在这种情况下，您的文件存储在文件系统中，并且您具有包含指向这些文件的指针的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的元数据表。</span><span class="sxs-lookup"><span data-stu-id="69328-124">In this scenario, your files are stored in the file system, and you have a table of metadata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains pointers to the files.</span></span> <span data-ttu-id="69328-125">您要将文件移入 FileTable，然后用 FileTable UNC 路径替换元数据中每个文件的原始 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="69328-125">You want to move the files into a FileTable, and then replace the original UNC path for each file in the metadata with the FileTable UNC path.</span></span> <span data-ttu-id="69328-126">[GetPathLocator (Transact-SQL)](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 函数帮助你实现这一目标。</span><span class="sxs-lookup"><span data-stu-id="69328-126">The [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function helps you to achieve this goal.</span></span>  
  
 <span data-ttu-id="69328-127">在此示例中，假设存在一个 `PhotoMetadata` 包含有关照片的数据的现有数据库表。</span><span class="sxs-lookup"><span data-stu-id="69328-127">For this example, assume that there is an existing database table, `PhotoMetadata`, which contains data about photographs.</span></span> <span data-ttu-id="69328-128">该表具有 `varchar`(512) 类型的 `UNCPath` 列，其中包含指向 .jpg 文件的实际 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="69328-128">This table has a column `UNCPath` of type `varchar`(512) which contains the actual UNC path to a .jpg file.</span></span>  
  
 <span data-ttu-id="69328-129">要将图像文件从文件系统迁移到 FileTable，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="69328-129">To migrate the image files from the file system into a FileTable, you have to do the following:</span></span>  
  
1.  <span data-ttu-id="69328-130">创建新的 FileTable 来保存文件。</span><span class="sxs-lookup"><span data-stu-id="69328-130">Create a new FileTable to hold the files.</span></span> <span data-ttu-id="69328-131">此示例将使用表名 `dbo.PhotoTable`，但不显示用来创建该表的代码。</span><span class="sxs-lookup"><span data-stu-id="69328-131">This example uses the table name, `dbo.PhotoTable`, but does not show the code to create the table.</span></span>  
  
2.  <span data-ttu-id="69328-132">使用 xcopy 或类似的工具将 .jpg 文件连同目录结构一起复制到 FileTable 的根目录下。</span><span class="sxs-lookup"><span data-stu-id="69328-132">Use xcopy or a similar tool to copy the .jpg files, with their directory structure, into the root directory of the FileTable.</span></span>  
  
3.  <span data-ttu-id="69328-133">通过使用类似于以下内容的代码修复 `PhotoMetadata` 表中的元数据：</span><span class="sxs-lookup"><span data-stu-id="69328-133">Fix the metadata in the `PhotoMetadata` table, by using code similar to the following:</span></span>  
  
```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> <span data-ttu-id="69328-134">大容量加载文件到 FileTable</span><span class="sxs-lookup"><span data-stu-id="69328-134">Bulk Loading Files into a FileTable</span></span>  
 <span data-ttu-id="69328-135">对于大容量操作，FileTable 在行为上与普通表相似，但具有以下限制。</span><span class="sxs-lookup"><span data-stu-id="69328-135">A FileTable behaves like a normal table for bulk operations, with the following qualifications.</span></span>  
  
 <span data-ttu-id="69328-136">FileTable 具有系统定义的约束，这些约束确保维护文件和目录命名空间的完整性。</span><span class="sxs-lookup"><span data-stu-id="69328-136">A FileTable has system-defined constraints which ensure that the integrity of the file and directory namespace is maintained.</span></span> <span data-ttu-id="69328-137">必须针对大容量加载到 FileTable 上的数据验证这些约束。</span><span class="sxs-lookup"><span data-stu-id="69328-137">These constraints have to be verified on the data bulk loaded into the FileTable.</span></span> <span data-ttu-id="69328-138">因为一些大容量插入操作允许忽略表约束，所以将强制以下要求。</span><span class="sxs-lookup"><span data-stu-id="69328-138">Since some bulk insert operations allow table constraints to be ignored, the following requirements are enforced.</span></span>  
  
-   <span data-ttu-id="69328-139">强制执行约束的大容量加载操作可以像对任何其他表一样对 FileTable 运行。</span><span class="sxs-lookup"><span data-stu-id="69328-139">Bulk loading operations that enforce constraints can be run against a FileTable as against any other table.</span></span> <span data-ttu-id="69328-140">此类别包括下列操作：</span><span class="sxs-lookup"><span data-stu-id="69328-140">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="69328-141">带 CHECK_CONSTRAINTS 子句的 bcp。</span><span class="sxs-lookup"><span data-stu-id="69328-141">bcp with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="69328-142">带 CHECK_CONSTRAINTS 子句的 BULK INSERT。</span><span class="sxs-lookup"><span data-stu-id="69328-142">BULK INSERT with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="69328-143">INSERT INTO... 不带 IGNORE_CONSTRAINTS 子句的 SELECT \* FROM OPENROWSET(BULK …)。</span><span class="sxs-lookup"><span data-stu-id="69328-143">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) without IGNORE_CONSTRAINTS clause.</span></span>  
  
-   <span data-ttu-id="69328-144">不强制执行约束的大容量加载操作将失败，除非 FileTable 系统定义的约束已禁用。</span><span class="sxs-lookup"><span data-stu-id="69328-144">Bulk loading operations that do not enforce constraints fail unless the FileTable system-defined constraints have been disabled.</span></span> <span data-ttu-id="69328-145">此类别包括下列操作：</span><span class="sxs-lookup"><span data-stu-id="69328-145">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="69328-146">不带 CHECK_CONSTRAINTS 子句的 bcp。</span><span class="sxs-lookup"><span data-stu-id="69328-146">bcp without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="69328-147">不带 CHECK_CONSTRAINTS 子句的 BULK INSERT。</span><span class="sxs-lookup"><span data-stu-id="69328-147">BULK INSERT without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="69328-148">INSERT INTO... 带 IGNORE_CONSTRAINTS 子句的 SELECT \* FROM OPENROWSET(BULK …)。</span><span class="sxs-lookup"><span data-stu-id="69328-148">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) with IGNORE_CONSTRAINTS clause.</span></span>  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> <span data-ttu-id="69328-149">如何：将文件批量到 FileTable</span><span class="sxs-lookup"><span data-stu-id="69328-149">How To: Bulk Load Files into a FileTable</span></span>  
 <span data-ttu-id="69328-150">您可以使用各种方法来大容量加载文件到 FileTable：</span><span class="sxs-lookup"><span data-stu-id="69328-150">You can use various methods to bulk load files into a FileTable:</span></span>  
  
-   <span data-ttu-id="69328-151">**bcp**</span><span class="sxs-lookup"><span data-stu-id="69328-151">**bcp**</span></span>  
  
    -   <span data-ttu-id="69328-152">使用 **CHECK_CONSTRAINTS** 子句调用。</span><span class="sxs-lookup"><span data-stu-id="69328-152">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="69328-153">禁用 FileTable 命名空间并不使用 **CHECK_CONSTRAINTS** 子句调用。</span><span class="sxs-lookup"><span data-stu-id="69328-153">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="69328-154">然后重新启用 FileTable 命名空间。</span><span class="sxs-lookup"><span data-stu-id="69328-154">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="69328-155">**BULK INSERT**</span><span class="sxs-lookup"><span data-stu-id="69328-155">**BULK INSERT**</span></span>  
  
    -   <span data-ttu-id="69328-156">使用 **CHECK_CONSTRAINTS** 子句调用。</span><span class="sxs-lookup"><span data-stu-id="69328-156">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="69328-157">禁用 FileTable 命名空间并不使用 **CHECK_CONSTRAINTS** 子句调用。</span><span class="sxs-lookup"><span data-stu-id="69328-157">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="69328-158">然后重新启用 FileTable 命名空间。</span><span class="sxs-lookup"><span data-stu-id="69328-158">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="69328-159">**INSERT INTO ...SELECT \* FROM OPENROWSET(BULK ...)**</span><span class="sxs-lookup"><span data-stu-id="69328-159">**INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...)**</span></span>  
  
    -   <span data-ttu-id="69328-160">使用 **IGNORE_CONSTRAINTS** 子句调用。</span><span class="sxs-lookup"><span data-stu-id="69328-160">Call with the **IGNORE_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="69328-161">禁用 FileTable 命名空间并不使用 **IGNORE_CONSTRAINTS** 子句调用。</span><span class="sxs-lookup"><span data-stu-id="69328-161">Disable the FileTable namespace and call without the **IGNORE_CONSTRAINTS** clause.</span></span> <span data-ttu-id="69328-162">然后重新启用 FileTable 命名空间。</span><span class="sxs-lookup"><span data-stu-id="69328-162">Then re-enable the FileTable namespace.</span></span>  
  
 <span data-ttu-id="69328-163">有关禁用 FileTable 约束的信息，请参阅 [管理 FileTables](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="69328-163">For information about disabling the FileTable constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> <span data-ttu-id="69328-164">如何：禁用针对批量加载的 FileTable 约束</span><span class="sxs-lookup"><span data-stu-id="69328-164">How To: Disable FileTable Constraints for Bulk Loading</span></span>  
 <span data-ttu-id="69328-165">若要在没有强制系统定义约束的开销的情况下将文件大容量加载到 FileTable 中，可以暂时禁用约束。</span><span class="sxs-lookup"><span data-stu-id="69328-165">To bulk load files into a FileTable without the overhead of enforcing the system-defined constraints, you can temporarily disable the constraints.</span></span> <span data-ttu-id="69328-166">有关详细信息，请参阅 [管理 FileTables](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="69328-166">For more information, see [Manage FileTables](manage-filetables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69328-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69328-167">See Also</span></span>  
 <span data-ttu-id="69328-168">[使用 Transact-SQL 访问 FileTable](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="69328-168">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="69328-169">使用文件输入输出 API 访问 FileTable</span><span class="sxs-lookup"><span data-stu-id="69328-169">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
