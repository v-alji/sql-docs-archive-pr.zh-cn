---
title: 查看数据库快照的稀疏文件大小 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: 424399b9915c8e7e26e1076fd2e553aafe06fcf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691229"
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a><span data-ttu-id="94066-102">查看数据库快照的稀疏文件大小 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="94066-102">View the Size of the Sparse File of a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="94066-103">本主题说明如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 来验证 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库文件是稀疏文件以及查看其实际大小和最大大小。</span><span class="sxs-lookup"><span data-stu-id="94066-103">This topic describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to verify that a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database file is a sparse file and to find out its actual and maximum sizes.</span></span> <span data-ttu-id="94066-104">稀疏文件是 NTFS 文件系统的功能，由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库快照使用。</span><span class="sxs-lookup"><span data-stu-id="94066-104">Sparse files, which are a feature of the NTFS file system, are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshots.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94066-105">创建数据库快照期间，可以使用 CREATE DATABASE 语句中的文件名来创建稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="94066-105">During database snapshot creation, sparse files are created by using the file names in the CREATE DATABASE statement.</span></span> <span data-ttu-id="94066-106">这些文件名存储在 **sys.master_files** 中的 **physical_name** 列中。</span><span class="sxs-lookup"><span data-stu-id="94066-106">These file names are stored in **sys.master_files** in the **physical_name** column.</span></span> <span data-ttu-id="94066-107">在 **sys.database_files** 中（无论是在源数据库中还是在快照中）， **physical_name** 列中始终包含源数据库文件的名称。</span><span class="sxs-lookup"><span data-stu-id="94066-107">In **sys.database_files** (whether in the source database or in a snapshot), the **physical_name** column always contains the names of the source database files.</span></span>  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a><span data-ttu-id="94066-108">验证数据库文件是稀疏文件</span><span class="sxs-lookup"><span data-stu-id="94066-108">Verify that a Database File is a Sparse File</span></span>  
  
1.  <span data-ttu-id="94066-109">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上：</span><span class="sxs-lookup"><span data-stu-id="94066-109">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="94066-110">从数据库快照的 **sys.database_files** 中或从 **sys.master_files** 中选择 **is_sparse**列。</span><span class="sxs-lookup"><span data-stu-id="94066-110">Select the **is_sparse** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="94066-111">该值指示文件是否是稀疏文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="94066-111">The value indicates whether the file is a sparse file, as follows:</span></span>  
  
     <span data-ttu-id="94066-112">1 = 文件是稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="94066-112">1 = File is a sparse file.</span></span>  
  
     <span data-ttu-id="94066-113">0 = 文件不是稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="94066-113">0 = File is not a sparse file.</span></span>  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a><span data-ttu-id="94066-114">查看稀疏文件的实际大小</span><span class="sxs-lookup"><span data-stu-id="94066-114">Find Out the Actual Size of a Sparse File</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94066-115">稀疏文件按 64 KB 的增量增长；因此，磁盘上稀疏文件的大小始终是 64 KB 的倍数。</span><span class="sxs-lookup"><span data-stu-id="94066-115">Sparse files grow in 64-kilobyte (KB) increments; thus, the size of a sparse file on disk is always a multiple of 64 KB.</span></span>  
  
 <span data-ttu-id="94066-116">若要查看快照的每个稀疏文件当前正在磁盘上使用的字节数，请查询**size_on_disk_bytes** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [sys.databases dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql)动态管理视图的 size_on_disk_bytes 列。</span><span class="sxs-lookup"><span data-stu-id="94066-116">To view the number of bytes that each sparse file of a snapshot is currently using on disk, query the **size_on_disk_bytes** column of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][sys.dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) dynamic management view.</span></span>  
  
 <span data-ttu-id="94066-117">若要查看稀疏文件占用的磁盘空间，在 Microsoft Windows 中右键单击文件，再单击“属性”，然后查看“占用空间”值。</span><span class="sxs-lookup"><span data-stu-id="94066-117">To view the disk space used by a sparse file, right-click the file in Microsoft Windows, click **Properties**, and look at the **Size on disk** value.</span></span>  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a><span data-ttu-id="94066-118">查看稀疏文件的最大大小</span><span class="sxs-lookup"><span data-stu-id="94066-118">Find Out the Maximum Size of a Sparse File</span></span>  
 <span data-ttu-id="94066-119">稀疏文件最大只能增长到创建快照时相应的源数据库文件的大小。</span><span class="sxs-lookup"><span data-stu-id="94066-119">The maximum size to which a sparse can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span> <span data-ttu-id="94066-120">若要了解此大小，可以使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="94066-120">To learn this size, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="94066-121">使用 Windows 命令提示符：</span><span class="sxs-lookup"><span data-stu-id="94066-121">Using Windows Command Prompt:</span></span>  
  
    1.  <span data-ttu-id="94066-122">使用 Windows **dir** 命令。</span><span class="sxs-lookup"><span data-stu-id="94066-122">Use Windows **dir** commands.</span></span>  
  
    2.  <span data-ttu-id="94066-123">在 Windows 中，选择稀疏文件，打开文件 **“属性”** 对话框，然后查看 **“大小”** 值。</span><span class="sxs-lookup"><span data-stu-id="94066-123">Select the sparse file, open the file **Properties** dialog box in Windows, and look at the **Size** value.</span></span>  
  
-   <span data-ttu-id="94066-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上：</span><span class="sxs-lookup"><span data-stu-id="94066-124">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="94066-125">从数据库快照的 **sys.database_files** 中或从 **sys.master_files** 中选择 **size**列。</span><span class="sxs-lookup"><span data-stu-id="94066-125">Select the **size** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="94066-126">**“大小”** 列的值反映快照可以使用的最大空间（SQL 页数）；此值相当于 Windows 的 **“大小”** 字段，不同的是此值以文件中包含的 SQL 页数表示；大小（以字节为单位）为：</span><span class="sxs-lookup"><span data-stu-id="94066-126">The value of **size** column reflects the maximum space, in SQL pages, that the snapshot can ever use; this value is equivalent to the Windows **Size** field, except that it is represented in terms of the number of SQL pages in the file; the size in bytes is:</span></span>  
  
     <span data-ttu-id="94066-127">( *number_of_pages* \* 8192)</span><span class="sxs-lookup"><span data-stu-id="94066-127">( *number_of_pages* \* 8192)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94066-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94066-128">See Also</span></span>  
 <span data-ttu-id="94066-129">[数据库快照 (SQL Server)](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="94066-129">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="94066-130">[sys.fn_virtualfilestats (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="94066-130">[sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span></span>  
 <span data-ttu-id="94066-131">[sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="94066-131">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 [<span data-ttu-id="94066-132">sys.master_files (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="94066-132">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
  
