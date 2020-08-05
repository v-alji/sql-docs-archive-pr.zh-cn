---
title: 大容量导入和导出数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b4e7611270135735cf3f7aada808a0a27ba927c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581192"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a><span data-ttu-id="2fde3-102">大容量导入和导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-102">Bulk Import and Export of Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2fde3-103">支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表大容量导出数据（“大容量数据”  ）以及将大容量数据导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或未分区的视图。</span><span class="sxs-lookup"><span data-stu-id="2fde3-103">supports exporting data in bulk (*bulk data*) from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and importing bulk data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="2fde3-104">大容量导入和大容量导出对在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和异类数据源之间有效传输数据是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="2fde3-104">Bulk importing and bulk exporting are essential to efficient transfer data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and heterogeneous data sources.</span></span> <span data-ttu-id="2fde3-105">“大容量导出”  是指将数据从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表复制到数据文件。</span><span class="sxs-lookup"><span data-stu-id="2fde3-105">*Bulk exporting* refers to copying data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file.</span></span> <span data-ttu-id="2fde3-106">“大容量导入”  是指将数据从数据文件加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="2fde3-106">*Bulk importing* refers to loading data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="2fde3-107">例如，您可以将数据从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 应用程序导出到数据文件，然后将这些数据大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="2fde3-107">For example, you can export data from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel application to a data file and then bulk import that data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="2fde3-108">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="2fde3-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="2fde3-109">大容量导入和大容量导出操作简介</span><span class="sxs-lookup"><span data-stu-id="2fde3-109">Introduction to Bulk Import and Bulk Export Operations</span></span>](#Intro)  
  
-   [<span data-ttu-id="2fde3-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="2fde3-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bulk-import-and-bulk-export-overview"></a><a name="Intro"></a><span data-ttu-id="2fde3-111">大容量导入和大容量导出概述</span><span class="sxs-lookup"><span data-stu-id="2fde3-111">Bulk Import and Bulk Export Overview</span></span>  
 <span data-ttu-id="2fde3-112">本节列出并简要比较了可用于大容量导入和导出数据的各种方法。</span><span class="sxs-lookup"><span data-stu-id="2fde3-112">This section lists and briefly compares the various methods that are available for bulk importing and exporting data.</span></span> <span data-ttu-id="2fde3-113">本节还介绍了格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2fde3-113">The section also introduces format files.</span></span>  
  
 <span data-ttu-id="2fde3-114">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="2fde3-114">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="2fde3-115">大容量导入和导出数据的方法</span><span class="sxs-lookup"><span data-stu-id="2fde3-115">Methods for Bulk Importing and Exporting Data</span></span>](#MethodsForBuliIE)  
  
-   [<span data-ttu-id="2fde3-116">格式化文件</span><span class="sxs-lookup"><span data-stu-id="2fde3-116">Format Files</span></span>](#FFs)  
  
###  <a name="methods-for-bulk-importing-and-exporting-data"></a><a name="MethodsForBuliIE"></a><span data-ttu-id="2fde3-117">大容量导入和导出数据的方法</span><span class="sxs-lookup"><span data-stu-id="2fde3-117">Methods for Bulk Importing and Exporting Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2fde3-118">支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表大容量导出数据以及将数据大容量导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或未分区的视图。</span><span class="sxs-lookup"><span data-stu-id="2fde3-118">supports bulk exporting data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="2fde3-119">可以使用下列基本方法：</span><span class="sxs-lookup"><span data-stu-id="2fde3-119">The following basic methods are available.</span></span>  
  
|<span data-ttu-id="2fde3-120">方法</span><span class="sxs-lookup"><span data-stu-id="2fde3-120">Method</span></span>|<span data-ttu-id="2fde3-121">说明</span><span class="sxs-lookup"><span data-stu-id="2fde3-121">Description</span></span>|<span data-ttu-id="2fde3-122">导入数据</span><span class="sxs-lookup"><span data-stu-id="2fde3-122">Imports data</span></span>|<span data-ttu-id="2fde3-123">导出数据</span><span class="sxs-lookup"><span data-stu-id="2fde3-123">Exports data</span></span>|  
|------------|-----------------|------------------|------------------|  
|[<span data-ttu-id="2fde3-124">bcp 实用工具</span><span class="sxs-lookup"><span data-stu-id="2fde3-124">bcp utility</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|<span data-ttu-id="2fde3-125">大容量导出数据和大容量导入数据并生成格式化文件的命令行实用工具 (Bcp.exe)。</span><span class="sxs-lookup"><span data-stu-id="2fde3-125">A command-line utility (Bcp.exe) that bulk exports and bulk imports data and generates format files.</span></span>|<span data-ttu-id="2fde3-126">是</span><span class="sxs-lookup"><span data-stu-id="2fde3-126">Yes</span></span>|<span data-ttu-id="2fde3-127">是</span><span class="sxs-lookup"><span data-stu-id="2fde3-127">Yes</span></span>|  
|[<span data-ttu-id="2fde3-128">BULK INSERT 语句</span><span class="sxs-lookup"><span data-stu-id="2fde3-128">BULK INSERT statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="2fde3-129">将数据直接从数据文件导入数据库表或未分区视图的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="2fde3-129">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that imports data directly from a data file into a database table or nonpartitioned view.</span></span>|<span data-ttu-id="2fde3-130">是</span><span class="sxs-lookup"><span data-stu-id="2fde3-130">Yes</span></span>|<span data-ttu-id="2fde3-131">否</span><span class="sxs-lookup"><span data-stu-id="2fde3-131">No</span></span>|  
|[<span data-ttu-id="2fde3-132">INSERT ...SELECT \* FROM OPENROWSET(BULK...) 语句</span><span class="sxs-lookup"><span data-stu-id="2fde3-132">INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="2fde3-133">通过在 INSERT 语句中指定 OPENROWSET(BULK…) 函数来选择数据，从而使用 OPENROWSET 大容量行集提供程序将数据大容量导入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="2fde3-133">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that uses the OPENROWSET bulk rowset provider to bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table by specifying the OPENROWSET(BULK...) function to select data in an INSERT statement.</span></span>|<span data-ttu-id="2fde3-134">是</span><span class="sxs-lookup"><span data-stu-id="2fde3-134">Yes</span></span>|<span data-ttu-id="2fde3-135">否</span><span class="sxs-lookup"><span data-stu-id="2fde3-135">No</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2fde3-136">SQL Server 大容量导入操作不支持逗号分隔值 (CSV) 文件。</span><span class="sxs-lookup"><span data-stu-id="2fde3-136">Comma-separated value (CSV) files are not supported by SQL Server bulk-import operations.</span></span> <span data-ttu-id="2fde3-137">但是，在某些情况下，CSV 文件可在将数据大容量导入 SQL Server 时用作数据文件。</span><span class="sxs-lookup"><span data-stu-id="2fde3-137">However, in some cases, a CSV file can be used as the data file for a bulk import of data into SQL Server.</span></span> <span data-ttu-id="2fde3-138">请注意，CSV 文件的字段终止符不一定是逗号。</span><span class="sxs-lookup"><span data-stu-id="2fde3-138">Note that the field terminator of a CSV file does not have to be a comma.</span></span> <span data-ttu-id="2fde3-139">有关详细信息，请参阅[准备用于批量导出或导入的数据 (SQL Server)](prepare-data-for-bulk-export-or-import-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2fde3-139">For more information, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
###  <a name="format-files"></a><a name="FFs"></a><span data-ttu-id="2fde3-140">格式化文件</span><span class="sxs-lookup"><span data-stu-id="2fde3-140">Format Files</span></span>  
 <span data-ttu-id="2fde3-141">**Bcp**实用工具、BULK INSERT 和 INSERT .。。选择 \* "从 OPENROWSET (BULK ..." ) 所有支持使用专用*格式化文件*，该文件存储数据文件中每个字段的格式信息。</span><span class="sxs-lookup"><span data-stu-id="2fde3-141">The **bcp** utility, BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) all support the use of a specialized *format file* that stores format information for each field in a data file.</span></span> <span data-ttu-id="2fde3-142">格式化文件还可以包含相应的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表的有关信息。</span><span class="sxs-lookup"><span data-stu-id="2fde3-142">A format file might also contain information about the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="2fde3-143">格式化文件可以用于提供从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例大容量导出数据和向其中大容量导入数据时所需的所有格式信息。</span><span class="sxs-lookup"><span data-stu-id="2fde3-143">The format file can be used to provide all the format information that is required to bulk export data from and bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2fde3-144">格式化文件提供了一种解释导入期间数据文件中数据的格式以及设置导出期间数据文件中数据格式的灵活方式。</span><span class="sxs-lookup"><span data-stu-id="2fde3-144">Format files provide a flexible way to interpret data as it is in the data file during import, and also to format data in the data file during export.</span></span> <span data-ttu-id="2fde3-145">这种灵活性使得解释数据时无需编写专用代码，也无需为满足 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或外部应用程序的特殊需要而重新设置数据的格式。</span><span class="sxs-lookup"><span data-stu-id="2fde3-145">This flexibility eliminates the need to write special-purpose code to interpret the data or reformat the data to the specific requirements of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the external application.</span></span> <span data-ttu-id="2fde3-146">例如，如果将要加载的数据大容量导出到某个需要逗号分隔值的应用程序，则可以使用格式化文件将逗号作为字段终止符插入导出的数据中。</span><span class="sxs-lookup"><span data-stu-id="2fde3-146">For example, if you are bulk exporting data to be loaded into an application that requires comma-separated values, you can use a format file to insert commas as field terminators in the exported data.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2fde3-147">支持两种格式化文件类型：XML 格式化文件和非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2fde3-147">supports two kinds of format files: XML format files and non-XML format files.</span></span>  
  
 <span data-ttu-id="2fde3-148">**Bcp**实用工具是唯一能够生成格式化文件的工具。</span><span class="sxs-lookup"><span data-stu-id="2fde3-148">The **bcp** utility is the only tool that can generate a format file.</span></span> <span data-ttu-id="2fde3-149">有关详细信息，请参阅 [创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2fde3-149">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="2fde3-150">有关格式化文件的详细信息，请参阅[导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2fde3-150">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fde3-151">如果在大容量导出或导入操作期间未提供格式化文件，您可以在命令行处覆盖默认格式。</span><span class="sxs-lookup"><span data-stu-id="2fde3-151">In cases when a format file is not supplied during a bulk export or import operations, you can override the default formatting at the command line.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2fde3-152">相关任务</span><span class="sxs-lookup"><span data-stu-id="2fde3-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2fde3-153">使用 bcp 实用工具导入和导出大容量数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-153">Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-154">使用 BULK INSERT 或 OPENROWSET (BULK...) 导入批量数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-154">Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-155">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-155">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-156">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-156">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-157">准备用于批量导出或导入的数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-157">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="2fde3-158">**使用格式化文件**</span><span class="sxs-lookup"><span data-stu-id="2fde3-158">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="2fde3-159">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-159">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-160">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-160">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-161">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-161">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-162">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-162">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-163">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-163">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="2fde3-164">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="2fde3-164">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="2fde3-165">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="2fde3-165">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-166">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-166">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-167">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-167">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-168">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-168">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="2fde3-169">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-169">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="2fde3-170">**在使用 bcp 时指定数据格式以获得兼容性**</span><span class="sxs-lookup"><span data-stu-id="2fde3-170">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="2fde3-171">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-171">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="2fde3-172">使用 bcp 指定数据文件中的前缀长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-172">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="2fde3-173">使用 bcp 指定文件存储类型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2fde3-173">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="2fde3-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fde3-174">See Also</span></span>  
 <span data-ttu-id="2fde3-175">[在大容量导入中按最小方式记录日志的前提条件](prerequisites-for-minimal-logging-in-bulk-import.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-175">[Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md) </span></span>  
 <span data-ttu-id="2fde3-176">[用于导入或导出数据的格式化文件 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-176">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 <span data-ttu-id="2fde3-177">[大容量导入和导出 XML 文档的示例 &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-177">[Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span></span>  
 <span data-ttu-id="2fde3-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span></span>  
 <span data-ttu-id="2fde3-179">[将数据库复制到其他服务器](../databases/copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-179">[Copy Databases to Other Servers](../databases/copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="2fde3-180">[&#40;SQLXML 4.0&#41;执行 XML 数据的大容量加载](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-180">[Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="2fde3-181">[执行大容量复制操作](../native-client/features/performing-bulk-copy-operations.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-181">[Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md) </span></span>  
 <span data-ttu-id="2fde3-182">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="2fde3-183">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2fde3-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="2fde3-184">[用于导入或导出数据的格式化文件 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2fde3-184">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 [<span data-ttu-id="2fde3-185">OPENROWSET (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2fde3-185">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
