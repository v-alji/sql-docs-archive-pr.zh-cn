---
title: 准备用于批量导出或导入的数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], planning
- bulk importing [SQL Server], from a CSV file
- data formats [SQL Server], planning operations
- CSV files [SQL Server]
- quoted fields in CSV files [SQL Server]
ms.assetid: 783fd581-2e5f-496b-b79c-d4de1e09ea30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f2780a4eadfc27ed2db15881d676965fca81e35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692424"
---
# <a name="prepare-data-for-bulk-export-or-import-sql-server"></a><span data-ttu-id="41bb7-102">准备用于大容量导出或导入的数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="41bb7-102">Prepare Data for Bulk Export or Import (SQL Server)</span></span>
  <span data-ttu-id="41bb7-103">本部分讨论计划大容量导出操作时的相关注意事项以及大容量导入操作的要求。</span><span class="sxs-lookup"><span data-stu-id="41bb7-103">This section discusses the considerations involved in planning for bulk-export operations and the requirements for bulk-import operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41bb7-104">如果您不确定应如何针对大容量导入设置数据文件的格式，则可以使用 **bcp** 实用工具将数据从表导出到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="41bb7-104">If you are uncertain about how to format a data file for bulk importing, you can use the **bcp** utility to export data from the table into a data file.</span></span> <span data-ttu-id="41bb7-105">此文件中每个数据字段的格式均显示了将数据大容量导入对应表列时所要求的格式。</span><span class="sxs-lookup"><span data-stu-id="41bb7-105">The formatting of each data field in this file shows the formatting required to bulk import data into the corresponding table column.</span></span> <span data-ttu-id="41bb7-106">对数据文件的各个字段使用相同的数据格式。</span><span class="sxs-lookup"><span data-stu-id="41bb7-106">Use the same data formatting for fields of your data file.</span></span>  
  
## <a name="data-file-format-considerations-for-bulk-export"></a><span data-ttu-id="41bb7-107">大容量导出的数据文件格式注意事项</span><span class="sxs-lookup"><span data-stu-id="41bb7-107">Data-File Format Considerations for Bulk Export</span></span>  
 <span data-ttu-id="41bb7-108">在使用 **bcp** 命令执行批量导出操作之前，请先考虑下列事项：</span><span class="sxs-lookup"><span data-stu-id="41bb7-108">Before you perform a bulk-export operation by using the **bcp** command, consider the following:</span></span>  
  
-   <span data-ttu-id="41bb7-109">将数据导出到文件时， **bcp** 命令使用指定的文件名自动创建数据文件。</span><span class="sxs-lookup"><span data-stu-id="41bb7-109">When data is exported to a file, the **bcp** command creates the data file automatically by using the specified file name.</span></span> <span data-ttu-id="41bb7-110">如果该文件名已经存在，正在大容量复制到数据文件的数据将覆盖文件中的现有内容。</span><span class="sxs-lookup"><span data-stu-id="41bb7-110">If that file name is already in use, the data that is being bulk copied to the data file overwrites the existing contents of the file.</span></span>  
  
-   <span data-ttu-id="41bb7-111">从表或视图大容量导出到数据文件要求对正在大容量复制的表或视图具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="41bb7-111">Bulk export from a table or view to a data file requires SELECT permission on the table or view that is being bulk copied.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="41bb7-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以使用并行扫描来检索数据。</span><span class="sxs-lookup"><span data-stu-id="41bb7-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use parallel scans to retrieve data.</span></span> <span data-ttu-id="41bb7-113">因此，通常不保证从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例大容量导出的表行在数据文件中按特定顺序排列。</span><span class="sxs-lookup"><span data-stu-id="41bb7-113">Therefore, the table rows that are bulk exported in from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are not ordinarily guaranteed to be in any specific order in the data file.</span></span> <span data-ttu-id="41bb7-114">为了确保大容量导出的表行在数据文件中按特定顺序排列，请使用 **queryout** 选项来通过查询进行大容量导出，并指定一个 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="41bb7-114">To make sure that bulk-exported table rows appear in a specific order in the data file, use the **queryout** option to bulk export from a query, and specify an ORDER BY clause.</span></span>  
  
## <a name="data-file-format-requirements-for-bulk-import"></a><span data-ttu-id="41bb7-115">大容量导入的数据文件格式要求</span><span class="sxs-lookup"><span data-stu-id="41bb7-115">Data-File Format Requirements for Bulk Import</span></span>  
 <span data-ttu-id="41bb7-116">为了导入数据文件中的数据，该文件必须满足以下基本要求：</span><span class="sxs-lookup"><span data-stu-id="41bb7-116">To import data from a data file, the file must meet the following basic requirements:</span></span>  
  
-   <span data-ttu-id="41bb7-117">数据必须以行和列的格式表示。</span><span class="sxs-lookup"><span data-stu-id="41bb7-117">The data must be in row and column format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41bb7-118">数据文件的结构不必与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表的结构一致，因为大容量导入过程中可以跳过列或对列重新排序。</span><span class="sxs-lookup"><span data-stu-id="41bb7-118">The structure of the data file does not need to be identical to the structure of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table because columns can be skipped or reordered during the bulk-import process.</span></span>  
  
-   <span data-ttu-id="41bb7-119">数据文件中的数据格式必须是支持的格式，例如字符格式或本机格式。</span><span class="sxs-lookup"><span data-stu-id="41bb7-119">The data in the data file must be in a supported format such as character or native format.</span></span>  
  
-   <span data-ttu-id="41bb7-120">数据可以是字符格式或本机二进制格式（包括 Unicode）。</span><span class="sxs-lookup"><span data-stu-id="41bb7-120">The data can be in character or native binary format including Unicode.</span></span>  
  
-   <span data-ttu-id="41bb7-121">若要使用 **bcp** 命令、BULK INSERT 语句或 INSERT...SELECT \* FROM OPENROWSET(BULK...) 语句导入数据，目标表必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="41bb7-121">To import data by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, the destination table must already exist.</span></span>  
  
-   <span data-ttu-id="41bb7-122">数据文件中的每个字段都必须与目标表中的对应列兼容。</span><span class="sxs-lookup"><span data-stu-id="41bb7-122">Each field in the data file must be compatible with the corresponding column in the target table.</span></span> <span data-ttu-id="41bb7-123">例如，不能将 `int` 字段加载到 `datetime` 列。</span><span class="sxs-lookup"><span data-stu-id="41bb7-123">For example, an `int` field cannot be loaded into a `datetime` column.</span></span> <span data-ttu-id="41bb7-124">有关详细信息，请参阅[用于批量导入或导出的数据格式 (SQL Server)](data-formats-for-bulk-import-or-bulk-export-sql-server.md)[在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="41bb7-124">For more information, see [Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) and [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41bb7-125">要指定从数据文件导入的行子集而并非整个文件，可以使用带有 -F first_row 开关和/或 -L last_row 开关的 bcp 命令 。</span><span class="sxs-lookup"><span data-stu-id="41bb7-125">To specify a subset of rows to import from a data file rather than the entire file, you can use a **bcp** command with the **-F** *first_row* switch and/or **-L** *last_row* switch.</span></span> <span data-ttu-id="41bb7-126">有关详细信息，请参阅 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="41bb7-126">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
-   <span data-ttu-id="41bb7-127">若要从包含固定长度或固定宽度字段的数据文件导入数据，则必须使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="41bb7-127">To import data from data files with fixed-length or fixed-width fields, you must use a format file.</span></span> <span data-ttu-id="41bb7-128">有关详细信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="41bb7-128">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
-   <span data-ttu-id="41bb7-129">逗号分隔值 (CSV) 文件不受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量导入操作支持。</span><span class="sxs-lookup"><span data-stu-id="41bb7-129">Comma-separated value (CSV) files are not supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-import operations.</span></span> <span data-ttu-id="41bb7-130">但是，在某些情况下，CSV 文件可在将数据大容量导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时用作数据文件。</span><span class="sxs-lookup"><span data-stu-id="41bb7-130">However, in some cases, a CSV file can be used as the data file for a bulk import of data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="41bb7-131">请注意，CSV 文件的字段终止符不一定是逗号。</span><span class="sxs-lookup"><span data-stu-id="41bb7-131">Note that the field terminator of a CSV file does not have to be a comma.</span></span> <span data-ttu-id="41bb7-132">若要能够用作大容量导入的数据文件，CSV 文件必须满足以下限制条件：</span><span class="sxs-lookup"><span data-stu-id="41bb7-132">To be usable as a data file for bulk import, a CSV file must comply with the following restrictions:</span></span>  
  
    -   <span data-ttu-id="41bb7-133">数据字段不包含任何字段终止符。</span><span class="sxs-lookup"><span data-stu-id="41bb7-133">Data fields never contain the field terminator.</span></span>  
  
    -   <span data-ttu-id="41bb7-134">数据字段中的值可全部使用引号 ("") 引起或全部都不使用引号。</span><span class="sxs-lookup"><span data-stu-id="41bb7-134">Either none or all of the values in a data field are enclosed in quotation marks ("").</span></span>  
  
     <span data-ttu-id="41bb7-135">若要从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] FoxPro、Visual FoxPro 表 (.dbf) 文件或 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 工作表 (.xls) 文件大容量导入数据，需要将数据转换为 CSV 文件以符合前面的限制条件。</span><span class="sxs-lookup"><span data-stu-id="41bb7-135">To bulk import data from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] FoxPro or Visual FoxPro table (.dbf) file or a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] worksheet (.xls) file, you would need to convert the data into a CSV file that complies to the preceding restrictions.</span></span> <span data-ttu-id="41bb7-136">文件扩展名通常将为 .csv。</span><span class="sxs-lookup"><span data-stu-id="41bb7-136">The file extension will typically be .csv.</span></span> <span data-ttu-id="41bb7-137">然后便可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量导入操作中使用 .csv 文件作为数据文件。</span><span class="sxs-lookup"><span data-stu-id="41bb7-137">You can then use the .csv file as a data file in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-import operation.</span></span>  
  
     <span data-ttu-id="41bb7-138">在 32 位系统上，通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET [和 OLE DB Provider for Jet 可以将 CSV 数据导入](/sql/t-sql/functions/openrowset-transact-sql) 表，但是没有大容量导入优化。</span><span class="sxs-lookup"><span data-stu-id="41bb7-138">On 32-bit systems, it is possible to import CSV data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table without bulk-import optimizations by using [OPENROWSET](/sql/t-sql/functions/openrowset-transact-sql) with the OLE DB Provider for Jet.</span></span> <span data-ttu-id="41bb7-139">通过由位于数据源所在目录的 schema.ini 文件定义的架构，Jet 将文本文件作为表处理。</span><span class="sxs-lookup"><span data-stu-id="41bb7-139">Jet treats text files as tables, with the schema defined by a schema.ini file that is located in the same directory as the data source.</span></span>  <span data-ttu-id="41bb7-140">对于 CSV 数据，schema.ini 文件内的其中一个参数将是“FORMAT=CSVDelimited”。</span><span class="sxs-lookup"><span data-stu-id="41bb7-140">For a CSV data, one of the parameters in the schema.ini file would be "FORMAT=CSVDelimited".</span></span> <span data-ttu-id="41bb7-141">若要使用此解决方案，需要了解 Jet Test IISAMm 如何工作，例如它的连接字符串语法、schema.ini 用法、注册表设置选项等等。</span><span class="sxs-lookup"><span data-stu-id="41bb7-141">To use this solution, you would need to understand how the Jet Test IISAMm operations-its connection string syntax, schema.ini usage, registry setting options, and so on).</span></span>  <span data-ttu-id="41bb7-142">此信息的最佳来源是 Microsoft Access 帮助和知识库 (KB) 文章。</span><span class="sxs-lookup"><span data-stu-id="41bb7-142">The best sources of this information are Microsoft Access Help and Knowledge Base (KB) articles.</span></span> <span data-ttu-id="41bb7-143">有关详细信息，请参阅[初始化文本数据源驱动程序](https://docs.microsoft.com/office/client-developer/access/desktop-database-reference/initializing-the-text-data-source-driver)、[如何通过链接服务器使用 SQL Server 7.0 分布式查询来查询安全的 Access 数据库](https://go.microsoft.com/fwlink/?LinkId=128504)、[如何使用 Jet OLE DB Provider 4.0 连接到 ISAM 数据库](https://go.microsoft.com/fwlink/?LinkId=128505)，以及[如何使用 Jet Provider 的文本 IIsam 打开带分隔符的文本文件](https://go.microsoft.com/fwlink/?LinkId=128501)。</span><span class="sxs-lookup"><span data-stu-id="41bb7-143">For more information, see [Initializing the Text Data Source Driver](https://docs.microsoft.com/office/client-developer/access/desktop-database-reference/initializing-the-text-data-source-driver), [How To Use a SQL Server 7.0 Distributed Query with a Linked Server to Secured Access Databases](https://go.microsoft.com/fwlink/?LinkId=128504), [HOW TO: Use Jet OLE DB Provider 4.0 to Connect to ISAM Databases](https://go.microsoft.com/fwlink/?LinkId=128505), and [How To Open Delimited Text Files Using the Jet Provider's Text IIsam](https://go.microsoft.com/fwlink/?LinkId=128501).</span></span>  
  
 <span data-ttu-id="41bb7-144">此外，将数据文件中的数据大容量导入表还有以下要求：</span><span class="sxs-lookup"><span data-stu-id="41bb7-144">In addition, the bulk import of data from a data file into a table requires the following:</span></span>  
  
-   <span data-ttu-id="41bb7-145">用户必须对表具有 INSERT 和 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="41bb7-145">Users must have INSERT and SELECT permissions on the table.</span></span> <span data-ttu-id="41bb7-146">如果用户使用要求执行数据定义语言 (DDL) 操作（例如禁用约束）的选项时，他们还要具有 ALTER TABLE 权限。</span><span class="sxs-lookup"><span data-stu-id="41bb7-146">Users also need ALTER TABLE permission when they use options that require data definition language (DDL) operations, such as disabling constraints.</span></span>  
  
-   <span data-ttu-id="41bb7-147">使用 BULK INSERT 或 INSERT ... SELECT \* FROM OPENROWSET(BULK...) 大容量导入数据时，必须可以通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的安全性配置文件（如果用户使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供的登录名进行登录）或在委托安全性下使用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录名对数据文件进行读取操作。</span><span class="sxs-lookup"><span data-stu-id="41bb7-147">When you bulk import data by using BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...), the data file must be accessible for read operations by either the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process (if the user logs in using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provided login) or by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login that is used under delegated security.</span></span> <span data-ttu-id="41bb7-148">此外，用户还必须具有 ADMINISTER BULK OPERATIONS 权限以读取文件。</span><span class="sxs-lookup"><span data-stu-id="41bb7-148">Additionally, the user must have ADMINISTER BULK OPERATIONS permission to read the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41bb7-149">由于不支持大容量导入到分区视图，因此无法将数据大容量导入到分区视图。</span><span class="sxs-lookup"><span data-stu-id="41bb7-149">Bulk importing into a partitioned view is unsupported, and attempts to bulk import data into a partitioned view fail.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="41bb7-150">外部资源</span><span class="sxs-lookup"><span data-stu-id="41bb7-150">External Resources</span></span>  
 [<span data-ttu-id="41bb7-151">如何将 Excel 数据导入 SQL Server</span><span class="sxs-lookup"><span data-stu-id="41bb7-151">How to import data from Excel to SQL Server</span></span>](https://support.microsoft.com/kb/321686)  
  
## <a name="change-history"></a><span data-ttu-id="41bb7-152">更改历史记录</span><span class="sxs-lookup"><span data-stu-id="41bb7-152">Change History</span></span>  
  
|<span data-ttu-id="41bb7-153">更新的内容</span><span class="sxs-lookup"><span data-stu-id="41bb7-153">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="41bb7-154">添加了有关使用 OLE DB Provider for Jet 导入 CSV 数据的信息。</span><span class="sxs-lookup"><span data-stu-id="41bb7-154">Added information about using the OLE DB Provider for Jet to import CSV data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41bb7-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41bb7-155">See Also</span></span>  
 <span data-ttu-id="41bb7-156">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="41bb7-156">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="41bb7-157">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41bb7-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="41bb7-158">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41bb7-158">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="41bb7-159">[使用字符格式导入或导出数据 (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41bb7-159">[Use Character Format to Import or Export Data &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md) </span></span>  
 [<span data-ttu-id="41bb7-160">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="41bb7-160">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
  
