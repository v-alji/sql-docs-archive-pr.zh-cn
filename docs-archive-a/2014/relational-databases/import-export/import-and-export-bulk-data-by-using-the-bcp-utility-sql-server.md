---
title: 使用 bcp 实用工具导入和导出批量数据 (SQL Server) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7d1892b26f3c638a696d8ed15e739f56ac2e682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589077"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a><span data-ttu-id="9dbee-102">使用 bcp 实用工具导入和导出大容量数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-102">Import and Export Bulk Data by Using the bcp Utility (SQL Server)</span></span>

<span data-ttu-id="9dbee-103">本主题概述了如何使用 [bcp 实用工具](../../tools/bcp-utility.md) 从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中可使用 SELECT 语句的任意位置（包括分区视图）导出数据。</span><span class="sxs-lookup"><span data-stu-id="9dbee-103">This topic provides an overview for using the [bcp utility](../../tools/bcp-utility.md) to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database where a SELECT statement works, including partitioned views.</span></span>  
  
 <span data-ttu-id="9dbee-104">bcp 实用工具 (Bcp.exe) 是一个使用大容量复制程序 (BCP) API 的命令行工具。</span><span class="sxs-lookup"><span data-stu-id="9dbee-104">The bcp utility (Bcp.exe) is a command-line tool that uses the Bulk Copy Program (BCP) API.</span></span> <span data-ttu-id="9dbee-105">bcp 实用工具可执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="9dbee-105">The bcp utility performs the following tasks:</span></span>  
  
-   <span data-ttu-id="9dbee-106">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的数据批量导出到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="9dbee-106">Bulk exports data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into a data file.</span></span>  
  
-   <span data-ttu-id="9dbee-107">从查询中批量导出数据。</span><span class="sxs-lookup"><span data-stu-id="9dbee-107">Bulk exports data from a query.</span></span>  
  
-   <span data-ttu-id="9dbee-108">将数据文件中的数据批量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="9dbee-108">Bulk imports data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
-   <span data-ttu-id="9dbee-109">生成格式化文件。</span><span class="sxs-lookup"><span data-stu-id="9dbee-109">Generates format files.</span></span>  
  
 <span data-ttu-id="9dbee-110">bcp 实用工具可通过 **bcp** 命令进行访问。</span><span class="sxs-lookup"><span data-stu-id="9dbee-110">The bcp utility is accessed by the **bcp** command.</span></span> <span data-ttu-id="9dbee-111">使用 **bcp** 命令批量导入数据时，除非使用已有的格式化文件，否则必须了解表的架构及其各列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9dbee-111">To use the **bcp** command to bulk import data, you must understand the schema of the table and the data types of its columns, unless you are using a pre-existing format file.</span></span>  
  
 <span data-ttu-id="9dbee-112">bcp 实用工具可将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的数据导出到数据文件，以供其他程序使用。</span><span class="sxs-lookup"><span data-stu-id="9dbee-112">The bcp utility can export data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file for use in other programs.</span></span> <span data-ttu-id="9dbee-113">此实用工具还可将其他程序（通常为另一数据库管理系统 (DBMS)）中的数据导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="9dbee-113">The utility can also import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from another program, usually another database management system (DBMS).</span></span> <span data-ttu-id="9dbee-114">数据首先从源程序导出到数据文件，然后再通过单独的操作将数据文件中的数据复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="9dbee-114">The data is first exported from the source program to a data file and then, in a separate operation, copied from the data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="9dbee-115">**bcp** 命令提供可指定数据文件的数据类型和其他信息的开关。</span><span class="sxs-lookup"><span data-stu-id="9dbee-115">The **bcp** command provides switches that you use to specify the data type of the data file and other information.</span></span> <span data-ttu-id="9dbee-116">如果未指定这些开关，则此命令会提示您指定格式信息，例如数据文件中数据字段的类型。</span><span class="sxs-lookup"><span data-stu-id="9dbee-116">If these switches are not specified, the command prompts for formatting information, such as the type of data fields in a data file.</span></span> <span data-ttu-id="9dbee-117">然后此命令会询问您是否要创建包含交互式响应的格式化文件。</span><span class="sxs-lookup"><span data-stu-id="9dbee-117">The command then asks whether you want to create a format file that contains your interactive responses.</span></span> <span data-ttu-id="9dbee-118">如果希望在以后的批量导入或批量导出操作中具有灵活性，格式化文件通常会很有用。</span><span class="sxs-lookup"><span data-stu-id="9dbee-118">If you want flexibility for future bulk-import or bulk-export operations, a format file is often useful.</span></span> <span data-ttu-id="9dbee-119">可以在稍后对同等数据文件使用 **bcp** 命令时指定该格式化文件。</span><span class="sxs-lookup"><span data-stu-id="9dbee-119">You can specify the format file on later **bcp** commands for equivalent data files.</span></span> <span data-ttu-id="9dbee-120">有关详细信息，请参阅[在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbee-120">For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dbee-121">bcp 实用工具通过使用 ODBC 大容量复制进行编写</span><span class="sxs-lookup"><span data-stu-id="9dbee-121">The bcp utility is written by using the ODBC bulk-copy</span></span>  
  
 <span data-ttu-id="9dbee-122">有关 **bcp** 命令语法的说明，请参阅 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbee-122">For a description of the **bcp** command syntax, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9dbee-123">示例</span><span class="sxs-lookup"><span data-stu-id="9dbee-123">Examples</span></span>

 <span data-ttu-id="9dbee-124">有关 **bcp** 示例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="9dbee-124">For **bcp** examples, see:</span></span>  
  
-   [<span data-ttu-id="9dbee-125">bcp 实用工具</span><span class="sxs-lookup"><span data-stu-id="9dbee-125">bcp Utility</span></span>](../../tools/bcp-utility.md)  
  
-   [<span data-ttu-id="9dbee-126">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-126">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-127">批量导入和导出 XML 文档的示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-127">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-128">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-128">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-129">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-129">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-130">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-130">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-131">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-131">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-132">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-133">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-133">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-134">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="9dbee-135">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dbee-135">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a><span data-ttu-id="9dbee-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9dbee-136">See Also</span></span>

<span data-ttu-id="9dbee-137">[INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql) 
[SELECT 子句 &#40;transact-sql&#41;](/sql/t-sql/queries/select-clause-transact-sql) 
[Bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="9dbee-137">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)
[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql)
[bcp Utility](../../tools/bcp-utility.md) </span></span>  
<span data-ttu-id="9dbee-138">[准备大容量导入数据 &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md) 
[BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
[大容量导入和导出数据 &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) 
[OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) 
[创建格式文件 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="9dbee-138">[Prepare to Bulk Import Data &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md)
[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)
[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)
[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)
[Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md)</span></span>