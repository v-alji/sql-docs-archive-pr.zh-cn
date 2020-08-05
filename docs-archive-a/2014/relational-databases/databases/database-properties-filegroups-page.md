---
title: 数据库属性（“文件组”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0546a17491ed5d3b36890a605c5faa922c24fe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581294"
---
# <a name="database-properties-filegroups-page"></a><span data-ttu-id="bd320-102">数据库属性（“文件组”页）</span><span class="sxs-lookup"><span data-stu-id="bd320-102">Database Properties (Filegroups Page)</span></span>
  <span data-ttu-id="bd320-103">使用此页可以查看文件组，或为所选数据库添加新的文件组。</span><span class="sxs-lookup"><span data-stu-id="bd320-103">Use this page to view the filegroups or add a new filegroup to the selected database.</span></span> <span data-ttu-id="bd320-104">文件组类型分为行 文件组、FILESTREAM 数据和内存优化文件组。</span><span class="sxs-lookup"><span data-stu-id="bd320-104">Filegroup types are separated into *row* filegroups, FILESTREAM data, and memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="bd320-105">行文件组包含常规数据和日志文件。</span><span class="sxs-lookup"><span data-stu-id="bd320-105">Row filegroups contain regular data and log files.</span></span> <span data-ttu-id="bd320-106">FILESTREAM 数据文件组包含 FILESTREAM 数据文件。</span><span class="sxs-lookup"><span data-stu-id="bd320-106">FILESTREAM data filegroups contain FILESTREAM data files.</span></span> <span data-ttu-id="bd320-107">这些数据文件存储有关在使用 FILESTREAM 存储时二进制大型对象 (BLOB) 数据在文件系统中的存储方式的信息。</span><span class="sxs-lookup"><span data-stu-id="bd320-107">These data files store information about how binary large object (BLOB) data is stored on the file system when you are using FILESTREAM storage.</span></span> <span data-ttu-id="bd320-108">两种类型的文件组具有相同的选项。</span><span class="sxs-lookup"><span data-stu-id="bd320-108">The options are the same for both types of filegroups.</span></span>  
  
 <span data-ttu-id="bd320-109">如果未启用 FILESTREAM，则不能使用 **Filestream** 部分。</span><span class="sxs-lookup"><span data-stu-id="bd320-109">If FILESTREAM is not enabled, the **Filestream** section will not be available.</span></span> <span data-ttu-id="bd320-110">可以通过 [服务器属性（“高级”页）](../../database-engine/configure-windows/server-properties-advanced-page.md)启用 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="bd320-110">You can enable FILESTREAM storage by using [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md).</span></span>  
  
 <span data-ttu-id="bd320-111">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户如何使用行文件组的信息，请参阅 [数据库文件和文件组](database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="bd320-111">For information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses row filegroups, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span> <span data-ttu-id="bd320-112">有关 FILESTREAM 数据和文件组的详细信息，请参阅 [FILESTREAM (SQL Server)](../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bd320-112">For more information about FILESTREAM data and filegroups, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="bd320-113">数据库必须有内存优化文件组才能包含一个或多个内存优化表。</span><span class="sxs-lookup"><span data-stu-id="bd320-113">Memory-optimized file groups are required for a database to contain one or more memory-optimized tables.</span></span>  
  
## <a name="row-and-filestream-data-filegroup-options"></a><span data-ttu-id="bd320-114">行和 FILESTREAM 数据文件组选项</span><span class="sxs-lookup"><span data-stu-id="bd320-114">Row and FILESTREAM Data Filegroup Options</span></span>  
 <span data-ttu-id="bd320-115">**名称**</span><span class="sxs-lookup"><span data-stu-id="bd320-115">**Name**</span></span>  
 <span data-ttu-id="bd320-116">输入文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="bd320-116">Enter the name of the filegroup.</span></span>  
  
 <span data-ttu-id="bd320-117">**文件**</span><span class="sxs-lookup"><span data-stu-id="bd320-117">**Files**</span></span>  
 <span data-ttu-id="bd320-118">显示文件组中的文件数量。</span><span class="sxs-lookup"><span data-stu-id="bd320-118">Displays the count of files in the filegroup.</span></span>  
  
 <span data-ttu-id="bd320-119">**只读**</span><span class="sxs-lookup"><span data-stu-id="bd320-119">**Read-only**</span></span>  
 <span data-ttu-id="bd320-120">选中此项可以将文件组设为只读状态。</span><span class="sxs-lookup"><span data-stu-id="bd320-120">Select to set the filegroup to a read-only status.</span></span>  
  
 <span data-ttu-id="bd320-121">**Default**</span><span class="sxs-lookup"><span data-stu-id="bd320-121">**Default**</span></span>  
 <span data-ttu-id="bd320-122">选中此项可以将此文件组设为默认文件组。</span><span class="sxs-lookup"><span data-stu-id="bd320-122">Select to make this filegroup the default filegroup.</span></span> <span data-ttu-id="bd320-123">您可以有一个用于行的默认文件组和一个用于 FILESTREAM 数据的默认文件组。</span><span class="sxs-lookup"><span data-stu-id="bd320-123">You can have one default filegroup for rows and one default filegroup for FILESTREAM data.</span></span>  
  
 <span data-ttu-id="bd320-124">**添加**</span><span class="sxs-lookup"><span data-stu-id="bd320-124">**Add**</span></span>  
 <span data-ttu-id="bd320-125">向列出数据库文件组的网格中添加新的空白行。</span><span class="sxs-lookup"><span data-stu-id="bd320-125">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="bd320-126">**删除**</span><span class="sxs-lookup"><span data-stu-id="bd320-126">**Remove**</span></span>  
 <span data-ttu-id="bd320-127">从网格中删除所选文件组行。</span><span class="sxs-lookup"><span data-stu-id="bd320-127">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="memory-optimized-data-filegroup-options"></a><span data-ttu-id="bd320-128">内存优化数据文件组选项</span><span class="sxs-lookup"><span data-stu-id="bd320-128">Memory-Optimized Data Filegroup Options</span></span>  
 <span data-ttu-id="bd320-129">**名称**</span><span class="sxs-lookup"><span data-stu-id="bd320-129">**Name**</span></span>  
 <span data-ttu-id="bd320-130">输入内存优化文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="bd320-130">Enter the name of the memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="bd320-131">**Filestream 文件**</span><span class="sxs-lookup"><span data-stu-id="bd320-131">**Filestream Files**</span></span>  
 <span data-ttu-id="bd320-132">显示内存优化数据文件组中文件（容器）的数量。</span><span class="sxs-lookup"><span data-stu-id="bd320-132">Displays the number of files (containers) in the memory-optimized data filegroup.</span></span> <span data-ttu-id="bd320-133">可以在 **“文件”** 页面添加容器。</span><span class="sxs-lookup"><span data-stu-id="bd320-133">You can add containers in the **Files** page.</span></span>  
  
 <span data-ttu-id="bd320-134">**添加**</span><span class="sxs-lookup"><span data-stu-id="bd320-134">**Add**</span></span>  
 <span data-ttu-id="bd320-135">向列出数据库文件组的网格中添加新的空白行。</span><span class="sxs-lookup"><span data-stu-id="bd320-135">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="bd320-136">**删除**</span><span class="sxs-lookup"><span data-stu-id="bd320-136">**Remove**</span></span>  
 <span data-ttu-id="bd320-137">从网格中删除所选文件组行。</span><span class="sxs-lookup"><span data-stu-id="bd320-137">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd320-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd320-138">See Also</span></span>  
 <span data-ttu-id="bd320-139">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd320-139">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="bd320-140">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bd320-140">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
