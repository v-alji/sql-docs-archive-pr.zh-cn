---
title: 使用 Transact-SQL 访问 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c47751ef34747e1b3742accf5040846ecde074f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691748"
---
# <a name="access-filetables-with-transact-sql"></a><span data-ttu-id="6448c-102">使用 Transact-SQL 访问 FileTable</span><span class="sxs-lookup"><span data-stu-id="6448c-102">Access FileTables with Transact-SQL</span></span>
  <span data-ttu-id="6448c-103">说明 [!INCLUDE[tsql](../../includes/tsql-md.md)] 数据操作语言 (DML) 命令如何与 FileTable 一起使用。</span><span class="sxs-lookup"><span data-stu-id="6448c-103">Describes how [!INCLUDE[tsql](../../includes/tsql-md.md)] data manipulation language (DML) commands work with FileTables.</span></span>  
  
##  <a name="insert-operations-on-filetables"></a><a name="BasicsInsert"></a> <span data-ttu-id="6448c-104">FileTable 上的 INSERT 操作</span><span class="sxs-lookup"><span data-stu-id="6448c-104">INSERT Operations on FileTables</span></span>  
 <span data-ttu-id="6448c-105">下列注意事项适用于 FileTable 上的 **INSERT** 操作：</span><span class="sxs-lookup"><span data-stu-id="6448c-105">The following considerations apply to **INSERT** Operations on FileTables:</span></span>  
  
-   <span data-ttu-id="6448c-106">所有文件属性列具有 NOT NULL 约束。</span><span class="sxs-lookup"><span data-stu-id="6448c-106">All the file attribute columns have NOT NULL constraints.</span></span> <span data-ttu-id="6448c-107">如果没有显式设置值，则提供适当的默认值。</span><span class="sxs-lookup"><span data-stu-id="6448c-107">If values are not explicitly set, then appropriate default values are supplied.</span></span>  
  
-   <span data-ttu-id="6448c-108">如果 INSERT 语句设置了 **name**、 **path_locator**、 **parent_path_locator**或文件属性，则强制执行系统定义的约束。</span><span class="sxs-lookup"><span data-stu-id="6448c-108">System-defined constraints are enforced if the INSERT statement sets the **name**, **path_locator**, **parent_path_locator**, or file attributes.</span></span>  
  
-   <span data-ttu-id="6448c-109">该应用程序可以通过提供指向 [GetPathLocator (Transact-SQL)](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 函数的文件系统路径，来获取文件或目录的 **path_locator**。</span><span class="sxs-lookup"><span data-stu-id="6448c-109">The application can obtain the **path_locator** for a file or directory by providing the file system path to the [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function.</span></span>  
  
##  <a name="update-operations-on-filetables"></a><a name="BasicsUpdate"></a> <span data-ttu-id="6448c-110">FileTable 上的 UPDATE 操作</span><span class="sxs-lookup"><span data-stu-id="6448c-110">UPDATE Operations on FileTables</span></span>  
 <span data-ttu-id="6448c-111">下列注意事项适用于 FileTable 上的 **UPDATE** 操作：</span><span class="sxs-lookup"><span data-stu-id="6448c-111">The following considerations apply to **UPDATE** operations on FileTables:</span></span>  
  
-   <span data-ttu-id="6448c-112">允许更新任何用户定义的数据。</span><span class="sxs-lookup"><span data-stu-id="6448c-112">Updates to any user-defined data are allowed.</span></span>  
  
-   <span data-ttu-id="6448c-113">如果 INSERT 语句设置了 **name**、 **path_locator**、 **parent_path_locator**或文件属性，则强制执行系统定义的约束。</span><span class="sxs-lookup"><span data-stu-id="6448c-113">System-defined constraints are enforced if the INSERT statement sets the **name**, **path_locator**, **parent_path_locator**, or file attributes.</span></span>  
  
-   <span data-ttu-id="6448c-114">可以对 **file_stream** 列中的 FILESTREAM 数据进行更新，且不会影响任何其他列（包括时间戳）。</span><span class="sxs-lookup"><span data-stu-id="6448c-114">Updates can be made to the FILESTREAM data in the **file_stream** column without affecting any of the other columns, including the timestamps.</span></span>  
  
##  <a name="delete-operations-on-filetables"></a><a name="BasicsDelete"></a> <span data-ttu-id="6448c-115">FileTable 上的 DELETE 操作</span><span class="sxs-lookup"><span data-stu-id="6448c-115">DELETE Operations on FileTables</span></span>  
 <span data-ttu-id="6448c-116">下列注意事项适用于 FileTable 上的 **DELETE** 操作：</span><span class="sxs-lookup"><span data-stu-id="6448c-116">The following considerations apply to **DELETE** operations on FileTables:</span></span>  
  
-   <span data-ttu-id="6448c-117">删除行还将从文件系统中删除相应的文件或目录。</span><span class="sxs-lookup"><span data-stu-id="6448c-117">Deleting a row also removes the corresponding file or directory from the file system.</span></span>  
  
-   <span data-ttu-id="6448c-118">如果该行与包含其他文件或目录的目录相对应，则删除行操作将失败。</span><span class="sxs-lookup"><span data-stu-id="6448c-118">Deleting a row fails if the row corresponds to a directory that contains other files or directories.</span></span>  
  
##  <a name="constraints-that-are-enforced-for-dml-operations-on-filetables"></a><a name="BasicsConstraints"></a> <span data-ttu-id="6448c-119">针对 FileTable 的 DML 操作强制执行的约束</span><span class="sxs-lookup"><span data-stu-id="6448c-119">Constraints That Are Enforced for DML Operations on FileTables</span></span>  
 <span data-ttu-id="6448c-120">系统定义的约束确保 DML 操作不破坏文件命名空间层次结构的完整性。</span><span class="sxs-lookup"><span data-stu-id="6448c-120">System-defined constraints ensure that DML actions do not compromise the integrity of the file namespace hierarchy.</span></span> <span data-ttu-id="6448c-121">强制执行的约束包括：</span><span class="sxs-lookup"><span data-stu-id="6448c-121">The constraints that are enforced include the following:</span></span>  
  
-   <span data-ttu-id="6448c-122">当您设置或更改文件或目录的 **名称** 时：</span><span class="sxs-lookup"><span data-stu-id="6448c-122">When you set or change the **name** of the file or directory:</span></span>  
  
    -   <span data-ttu-id="6448c-123">将强制执行 Windows 文件或目录命名约定。</span><span class="sxs-lookup"><span data-stu-id="6448c-123">Windows file and directory naming conventions are enforced.</span></span>  
  
    -   <span data-ttu-id="6448c-124">将强制实施父目录中名称的唯一性。</span><span class="sxs-lookup"><span data-stu-id="6448c-124">The uniqueness of the name in the parent directory is enforced.</span></span>  
  
-   <span data-ttu-id="6448c-125">当通过设置或更改 **path_locator** 或 **parent_path_locator**来设置或更改文件或目录的位置时：</span><span class="sxs-lookup"><span data-stu-id="6448c-125">When you set or change the location of a file or directory by setting or changing the **path_locator** or **parent_path_locator**:</span></span>  
  
    -   <span data-ttu-id="6448c-126">强制执行唯一性。</span><span class="sxs-lookup"><span data-stu-id="6448c-126">Uniqueness is enforced.</span></span>  
  
    -   <span data-ttu-id="6448c-127">将强制执行目录和文件的层次结构树的一致性，包括 **path_locator** 和 **parent_path_locator** 值的一致性。</span><span class="sxs-lookup"><span data-stu-id="6448c-127">The consistency of the hierarchical tree of directories and files is enforced, including the consistency of **path_locator** and **parent_path_locator** values.</span></span>  
  
-   <span data-ttu-id="6448c-128">当 **file_stream** 列为非 Null 时，不能将 **is_directory** 的值设置为 True。</span><span class="sxs-lookup"><span data-stu-id="6448c-128">The value of **is_directory** cannot be set to true when the **file_stream** column is not null.</span></span> <span data-ttu-id="6448c-129">**file_stream** 列中的数据指示该行表示一个文件，而不是一个目录。</span><span class="sxs-lookup"><span data-stu-id="6448c-129">Data in the **file_stream** column indicates that the row represents a file and not a directory.</span></span>  
  
-   <span data-ttu-id="6448c-130">文件属性列不能为 Null。</span><span class="sxs-lookup"><span data-stu-id="6448c-130">File attribute columns cannot be null.</span></span> <span data-ttu-id="6448c-131">将使用默认值强制执行 NOT NULL 约束。</span><span class="sxs-lookup"><span data-stu-id="6448c-131">NOT NULL constraints are enforced with default values.</span></span>  
  
-   <span data-ttu-id="6448c-132">**last_access_time** 的值不能早于 **last_write_time** 和 **creation_time**。</span><span class="sxs-lookup"><span data-stu-id="6448c-132">The value of **last_access_time** cannot be earlier than **last_write_time** and **creation_time**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6448c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6448c-133">See Also</span></span>  
 <span data-ttu-id="6448c-134">[将文件加载到 FileTable 中](load-files-into-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="6448c-134">[Load Files into FileTables](load-files-into-filetables.md) </span></span>  
 <span data-ttu-id="6448c-135">[Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="6448c-135">[Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md) </span></span>  
 <span data-ttu-id="6448c-136">[使用文件输入输出 API 访问 FileTable](access-filetables-with-file-input-output-apis.md) </span><span class="sxs-lookup"><span data-stu-id="6448c-136">[Access FileTables with File Input-Output APIs](access-filetables-with-file-input-output-apis.md) </span></span>  
 [<span data-ttu-id="6448c-137">FileTable DDL、函数、存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="6448c-137">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
