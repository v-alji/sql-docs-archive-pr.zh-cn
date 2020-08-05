---
title: 数据库文件和文件组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91e22e536a91878609feedf2977ffa7d78a54d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581309"
---
# <a name="database-files-and-filegroups"></a><span data-ttu-id="31931-102">数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="31931-102">Database Files and Filegroups</span></span>
  <span data-ttu-id="31931-103">每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库至少具有两个操作系统文件：一个数据文件和一个日志文件。</span><span class="sxs-lookup"><span data-stu-id="31931-103">At a minimum, every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database has two operating system files: a data file and a log file.</span></span> <span data-ttu-id="31931-104">数据文件包含数据和对象，例如表、索引、存储过程和视图。</span><span class="sxs-lookup"><span data-stu-id="31931-104">Data files contain data and objects such as tables, indexes, stored procedures, and views.</span></span> <span data-ttu-id="31931-105">日志文件包含恢复数据库中的所有事务所需的信息。</span><span class="sxs-lookup"><span data-stu-id="31931-105">Log files contain the information that is required to recover all transactions in the database.</span></span> <span data-ttu-id="31931-106">为了便于分配和管理，可以将数据文件集合起来，放到文件组中。</span><span class="sxs-lookup"><span data-stu-id="31931-106">Data files can be grouped together in filegroups for allocation and administration purposes.</span></span>  
  
## <a name="database-files"></a><span data-ttu-id="31931-107">数据库文件</span><span class="sxs-lookup"><span data-stu-id="31931-107">Database Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="31931-108">数据库具有三种类型的文件，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="31931-108">databases have three types of files, as shown in the following table.</span></span>  
  
|<span data-ttu-id="31931-109">文件</span><span class="sxs-lookup"><span data-stu-id="31931-109">File</span></span>|<span data-ttu-id="31931-110">说明</span><span class="sxs-lookup"><span data-stu-id="31931-110">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="31931-111">主</span><span class="sxs-lookup"><span data-stu-id="31931-111">Primary</span></span>|<span data-ttu-id="31931-112">主要数据文件包含数据库的启动信息，并指向数据库中的其他文件。</span><span class="sxs-lookup"><span data-stu-id="31931-112">The primary data file contains the startup information for the database and points to the other files in the database.</span></span> <span data-ttu-id="31931-113">用户数据和对象可存储在此文件中，也可以存储在次要数据文件中。</span><span class="sxs-lookup"><span data-stu-id="31931-113">User data and objects can be stored in this file or in secondary data files.</span></span> <span data-ttu-id="31931-114">每个数据库有一个主要数据文件。</span><span class="sxs-lookup"><span data-stu-id="31931-114">Every database has one primary data file.</span></span> <span data-ttu-id="31931-115">主要数据文件的建议文件扩展名是 .mdf。</span><span class="sxs-lookup"><span data-stu-id="31931-115">The recommended file name extension for primary data files is .mdf.</span></span>|  
|<span data-ttu-id="31931-116">辅助副本</span><span class="sxs-lookup"><span data-stu-id="31931-116">Secondary</span></span>|<span data-ttu-id="31931-117">次要数据文件是可选的，由用户定义并存储用户数据。</span><span class="sxs-lookup"><span data-stu-id="31931-117">Secondary data files are optional, are user-defined, and store user data.</span></span> <span data-ttu-id="31931-118">通过将每个文件放在不同的磁盘驱动器上，次要文件可用于将数据分散到多个磁盘上。</span><span class="sxs-lookup"><span data-stu-id="31931-118">Secondary files can be used to spread data across multiple disks by putting each file on a different disk drive.</span></span> <span data-ttu-id="31931-119">另外，如果数据库超过了单个 Windows 文件的最大大小，可以使用次要数据文件，这样数据库就能继续增长。</span><span class="sxs-lookup"><span data-stu-id="31931-119">Additionally, if a database exceeds the maximum size for a single Windows file, you can use secondary data files so the database can continue to grow.</span></span><br /><br /> <span data-ttu-id="31931-120">次要数据文件的建议文件扩展名是 .ndf。</span><span class="sxs-lookup"><span data-stu-id="31931-120">The recommended file name extension for secondary data files is .ndf.</span></span>|  
|<span data-ttu-id="31931-121">事务日志</span><span class="sxs-lookup"><span data-stu-id="31931-121">Transaction Log</span></span>|<span data-ttu-id="31931-122">事务日志文件保存用于恢复数据库的日志信息。</span><span class="sxs-lookup"><span data-stu-id="31931-122">The transaction log files hold the log information that is used to recover the database.</span></span> <span data-ttu-id="31931-123">每个数据库必须至少有一个日志文件。</span><span class="sxs-lookup"><span data-stu-id="31931-123">There must be at least one log file for each database.</span></span> <span data-ttu-id="31931-124">事务日志的建议文件扩展名是 .ldf。</span><span class="sxs-lookup"><span data-stu-id="31931-124">The recommended file name extension for transaction logs is .ldf.</span></span>|  
  
 <span data-ttu-id="31931-125">例如，可以创建一个简单的数据库 **Sales** ，其中包括一个包含所有数据和对象的主要文件和一个包含事务日志信息的日志文件。</span><span class="sxs-lookup"><span data-stu-id="31931-125">For example, a simple database named **Sales** can be created that includes one primary file that contains all data and objects and a log file that contains the transaction log information.</span></span> <span data-ttu-id="31931-126">也可以创建一个更复杂的数据库 **Orders** ，其中包括一个主要文件和五个次要文件。</span><span class="sxs-lookup"><span data-stu-id="31931-126">Alternatively, a more complex database named **Orders** can be created that includes one primary file and five secondary files.</span></span> <span data-ttu-id="31931-127">数据库中的数据和对象分散在所有六个文件中，而四个日志文件包含事务日志信息。</span><span class="sxs-lookup"><span data-stu-id="31931-127">The data and objects within the database spread across all six files, and the four log files contain the transaction log information.</span></span>  
  
 <span data-ttu-id="31931-128">默认情况下，数据和事务日志被放在同一个驱动器上的同一个路径下。</span><span class="sxs-lookup"><span data-stu-id="31931-128">By default, the data and transaction logs are put on the same drive and path.</span></span> <span data-ttu-id="31931-129">这是为处理单磁盘系统而采用的方法。</span><span class="sxs-lookup"><span data-stu-id="31931-129">This is done to handle single-disk systems.</span></span> <span data-ttu-id="31931-130">但是，在生产环境中，这可能不是最佳的方法。</span><span class="sxs-lookup"><span data-stu-id="31931-130">However, this may not be optimal for production environments.</span></span> <span data-ttu-id="31931-131">建议将数据和日志文件放在不同的磁盘上。</span><span class="sxs-lookup"><span data-stu-id="31931-131">We recommend that you put data and log files on separate disks.</span></span>  
  
## <a name="filegroups"></a><span data-ttu-id="31931-132">文件组</span><span class="sxs-lookup"><span data-stu-id="31931-132">Filegroups</span></span>  
 <span data-ttu-id="31931-133">每个数据库有一个主要文件组。</span><span class="sxs-lookup"><span data-stu-id="31931-133">Every database has a primary filegroup.</span></span> <span data-ttu-id="31931-134">此文件组包含主要数据文件和未放入其他文件组的所有次要文件。</span><span class="sxs-lookup"><span data-stu-id="31931-134">This filegroup contains the primary data file and any secondary files that are not put into other filegroups.</span></span> <span data-ttu-id="31931-135">可以创建用户定义的文件组，用于将数据文件集合起来，以便于管理、数据分配和放置。</span><span class="sxs-lookup"><span data-stu-id="31931-135">User-defined filegroups can be created to group data files together for administrative, data allocation, and placement purposes.</span></span>  
  
 <span data-ttu-id="31931-136">例如，可以分别在三个磁盘驱动器上创建三个文件 Data1.ndf、Data2.ndf 和 Data3.ndf，然后将它们分配给文件组 **fgroup1**。</span><span class="sxs-lookup"><span data-stu-id="31931-136">For example, three files, Data1.ndf, Data2.ndf, and Data3.ndf, can be created on three disk drives, respectively, and assigned to the filegroup **fgroup1**.</span></span> <span data-ttu-id="31931-137">然后，可以明确地在文件组 **fgroup1**上创建一个表。</span><span class="sxs-lookup"><span data-stu-id="31931-137">A table can then be created specifically on the filegroup **fgroup1**.</span></span> <span data-ttu-id="31931-138">对表中数据的查询将分散到三个磁盘上，从而提高了性能。</span><span class="sxs-lookup"><span data-stu-id="31931-138">Queries for data from the table will be spread across the three disks; this will improve performance.</span></span> <span data-ttu-id="31931-139">通过使用在 RAID（独立磁盘冗余阵列）条带集上创建的单个文件也能获得同样的性能提高。</span><span class="sxs-lookup"><span data-stu-id="31931-139">The same performance improvement can be accomplished by using a single file created on a RAID (redundant array of independent disks) stripe set.</span></span> <span data-ttu-id="31931-140">但是，文件和文件组使您能够轻松地在新磁盘上添加新文件。</span><span class="sxs-lookup"><span data-stu-id="31931-140">However, files and filegroups let you easily add new files to new disks.</span></span>  
  
 <span data-ttu-id="31931-141">下表列出了存储在文件组中的所有数据文件。</span><span class="sxs-lookup"><span data-stu-id="31931-141">All data files are stored in the filegroups listed in the following table.</span></span>  
  
|<span data-ttu-id="31931-142">文件组</span><span class="sxs-lookup"><span data-stu-id="31931-142">Filegroup</span></span>|<span data-ttu-id="31931-143">说明</span><span class="sxs-lookup"><span data-stu-id="31931-143">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31931-144">主</span><span class="sxs-lookup"><span data-stu-id="31931-144">Primary</span></span>|<span data-ttu-id="31931-145">包含主要文件的文件组。</span><span class="sxs-lookup"><span data-stu-id="31931-145">The filegroup that contains the primary file.</span></span> <span data-ttu-id="31931-146">所有系统表都被分配到主要文件组中。</span><span class="sxs-lookup"><span data-stu-id="31931-146">All system tables are allocated to the primary filegroup.</span></span>|  
|<span data-ttu-id="31931-147">用户定义</span><span class="sxs-lookup"><span data-stu-id="31931-147">User-defined</span></span>|<span data-ttu-id="31931-148">用户首次创建数据库或以后修改数据库时明确创建的任何文件组。</span><span class="sxs-lookup"><span data-stu-id="31931-148">Any filegroup that is specifically created by the user when the user first creates or later modifies the database.</span></span>|  
  
### <a name="default-filegroup"></a><span data-ttu-id="31931-149">默认文件组</span><span class="sxs-lookup"><span data-stu-id="31931-149">Default Filegroup</span></span>  
 <span data-ttu-id="31931-150">如果在数据库中创建对象时没有指定对象所属的文件组，对象将被分配给默认文件组。</span><span class="sxs-lookup"><span data-stu-id="31931-150">When objects are created in the database without specifying which filegroup they belong to, they are assigned to the default filegroup.</span></span> <span data-ttu-id="31931-151">不管何时，只能将一个文件组指定为默认文件组。</span><span class="sxs-lookup"><span data-stu-id="31931-151">At any time, exactly one filegroup is designated as the default filegroup.</span></span> <span data-ttu-id="31931-152">默认文件组中的文件必须足够大，能够容纳未分配给其他文件组的所有新对象。</span><span class="sxs-lookup"><span data-stu-id="31931-152">The files in the default filegroup must be large enough to hold any new objects not allocated to other filegroups.</span></span>  
  
 <span data-ttu-id="31931-153">PRIMARY 文件组是默认文件组，除非使用 ALTER DATABASE 语句进行了更改。</span><span class="sxs-lookup"><span data-stu-id="31931-153">The PRIMARY filegroup is the default filegroup unless it is changed by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="31931-154">但系统对象和表仍然分配给 PRIMARY 文件组，而不是新的默认文件组。</span><span class="sxs-lookup"><span data-stu-id="31931-154">Allocation for the system objects and tables remains within the PRIMARY filegroup, not the new default filegroup.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="31931-155">相关内容</span><span class="sxs-lookup"><span data-stu-id="31931-155">Related Content</span></span>  
 [<span data-ttu-id="31931-156">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="31931-156">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
 [<span data-ttu-id="31931-157">ALTER DATABASE 文件和文件组选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="31931-157">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
 [<span data-ttu-id="31931-158">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="31931-158">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
