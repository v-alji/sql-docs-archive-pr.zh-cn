---
title: 准备批量导入数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03d45d9c79082b255e9b8b0e4804c50855a3ad7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693361"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a><span data-ttu-id="f337e-102">准备大容量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f337e-102">Prepare to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="f337e-103">只能使用 **bcp** 命令、BULK INSERT 语句或 OPENROWSET(BULK) 函数从数据文件批量导入数据。</span><span class="sxs-lookup"><span data-stu-id="f337e-103">You can use the **bcp** command, BULK INSERT statement, or OPENROWSET(BULK) function to bulk import data from a data file only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f337e-104">可以编写从对象而非文本文件大容量导入数据的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="f337e-104">It is possible to write a custom application that bulk imports data from objects other than a text file.</span></span> <span data-ttu-id="f337e-105">若要从内存缓冲区批量导入数据，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) 应用程序编程接口 (API) 的 bcp 扩展或 OLE DB **IRowsetFastLoad** 接口。</span><span class="sxs-lookup"><span data-stu-id="f337e-105">To bulk import data from memory buffers, use either the bcp extensions to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) application programming interface (API) or the OLE DB **IRowsetFastLoad** interface.</span></span>  <span data-ttu-id="f337e-106">若要从 C# 数据表批量导入数据，请使用 ADO.NET 批量复制 API，即 **SqlBulkCopy**。</span><span class="sxs-lookup"><span data-stu-id="f337e-106">To bulk import data from a C# data table, use the ADO.NET bulk-copy API, **SqlBulkCopy**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f337e-107">不支持将数据大容量导入到远程表中。</span><span class="sxs-lookup"><span data-stu-id="f337e-107">Bulk importing data into a remote table is not supported.</span></span>  
  
 <span data-ttu-id="f337e-108">在将数据文件中的数据大容量导入到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，请使用以下原则：</span><span class="sxs-lookup"><span data-stu-id="f337e-108">Use the following guidelines when you bulk import data from a data file to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f337e-109">为用户帐户获取所需的权限。</span><span class="sxs-lookup"><span data-stu-id="f337e-109">Obtain required permissions for your user account.</span></span>  
  
     <span data-ttu-id="f337e-110">用户帐户，你在其中使用 **bcp** 实用工具、BULK INSERT 语句或 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 语句的用户帐户必须具有表的所需权限，这些权限由表所有者分配。</span><span class="sxs-lookup"><span data-stu-id="f337e-110">The user account in which you use the **bcp** utility, the BULK INSERT statement, or the INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement must have the required permissions on the table, which are assigned by the table owner.</span></span> <span data-ttu-id="f337e-111">有关每个方法所需的权限的详细信息，请参阅 [bcp 实用工具、](../../tools/bcp-utility.md)[OPENROWSET (Transact SQL)](/sql/t-sql/functions/openrowset-transact-sql) 和 [BULK INSERT (Transact SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f337e-111">For more information about permissions that are required by each method, see [bcp Utility](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="f337e-112">使用大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="f337e-112">Use the bulk-logged recovery model.</span></span>  
  
     <span data-ttu-id="f337e-113">此原则适用于使用完整恢复模式的数据库。</span><span class="sxs-lookup"><span data-stu-id="f337e-113">This guideline is for a database that uses the full recovery model.</span></span> <span data-ttu-id="f337e-114">对无索引表（“堆”  ）执行批量操作时，大容量日志恢复模式非常有用。</span><span class="sxs-lookup"><span data-stu-id="f337e-114">The bulk-logged recovery model is useful when performing bulk operations into an unindexed table (a *heap*).</span></span> <span data-ttu-id="f337e-115">使用大容量日志恢复有助于防止事务日志出现空间不足的情况，因为大容量日志恢复不会插入日志行。</span><span class="sxs-lookup"><span data-stu-id="f337e-115">Using bulk-logged recovery helps prevent the transaction log from running out of space because bulk-logged recovery does not perform log row inserts.</span></span> <span data-ttu-id="f337e-116">有关大容量日志恢复模式的详细信息，请参阅[恢复模式 (SQL Server)](../backup-restore/recovery-models-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f337e-116">For more information about the bulk-logged recovery model, see [Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).</span></span>  
  
     <span data-ttu-id="f337e-117">建议您在执行大容量导入操作之前，先将数据库改为使用大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="f337e-117">We recommend that you change the database to use the bulk-logged recovery model immediately before the bulk import operation.</span></span> <span data-ttu-id="f337e-118">之后应立即将数据库重设为完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="f337e-118">Immediately afterwards, you should reset the database to the full recovery model.</span></span> <span data-ttu-id="f337e-119">有关详细信息，请参阅[查看或更改数据库的恢复模式 (SQL Server)](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f337e-119">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f337e-120">有关如何在批量导入操作期间最小化日志记录的详细信息，请参阅 [批量导入中最小化日志记录的先决条件](prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="f337e-120">more information about how to minimize logging during bulk import operations, see [Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
-   <span data-ttu-id="f337e-121">大容量导入数据后进行备份。</span><span class="sxs-lookup"><span data-stu-id="f337e-121">Back up after bulk importing data.</span></span>  
  
     <span data-ttu-id="f337e-122">对于使用简单恢复模式的数据库，建议您在大容量导入操作完成后执行完整备份或差异备份。</span><span class="sxs-lookup"><span data-stu-id="f337e-122">For a database that uses the simple recovery model, we recommend that you take a full or differential backup after the bulk-import operation finishes.</span></span> <span data-ttu-id="f337e-123">有关详细信息，请参阅[创建完整数据库备份 (SQL Server)](../backup-restore/create-a-full-database-backup-sql-server.md) 或[创建差异数据库备份 (SQL Server)](../backup-restore/create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f337e-123">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) or [Create a Differential Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
     <span data-ttu-id="f337e-124">对于大容量日志恢复模式或完整恢复模式，只需执行日志备份就足够了。</span><span class="sxs-lookup"><span data-stu-id="f337e-124">For the bulk-logged recovery model or full recovery model, a log backup is enough.</span></span> <span data-ttu-id="f337e-125">有关详细信息，请参阅[事务日志备份 (SQL Server)](../backup-restore/transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f337e-125">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f337e-126">删除表索引以提高大型大容量导入操作的性能。</span><span class="sxs-lookup"><span data-stu-id="f337e-126">Drop table indexes to improve performance for large bulk imports.</span></span>  
  
     <span data-ttu-id="f337e-127">在导入的数据量与表中已有数据量相比很大时，请使用此原则。</span><span class="sxs-lookup"><span data-stu-id="f337e-127">This guideline is for when you are importing a large amount of data compared to the amount of data that is already in the table.</span></span> <span data-ttu-id="f337e-128">在这种情况下，执行大容量导入操作之前删除表中的索引可显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="f337e-128">In this case, dropping the indexes from the table before you perform the bulk-import operation can significantly increase performance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f337e-129">如果加载的数据量与表中已有的数据量相比较小时，删除索引会适得其反。</span><span class="sxs-lookup"><span data-stu-id="f337e-129">If you are loading a small amount of data compared to the amount of data already in the table, dropping the indexes is counterproductive.</span></span> <span data-ttu-id="f337e-130">因为重新生成索引所需的时间可能要比大容量导入操作期间所节省的时间更长。</span><span class="sxs-lookup"><span data-stu-id="f337e-130">The time required to rebuild the indexes might be longer than the time saved during the bulk-import operation.</span></span>  
  
-   <span data-ttu-id="f337e-131">查找并删除数据文件中的隐藏字符。</span><span class="sxs-lookup"><span data-stu-id="f337e-131">Find and remove hidden characters in the data file.</span></span>  
  
     <span data-ttu-id="f337e-132">许多实用工具和文本编辑器都会显示隐藏字符，这些隐藏字符通常位于数据文件末尾。</span><span class="sxs-lookup"><span data-stu-id="f337e-132">Many utilities and text editors display hidden characters, which are usually at the end of the data file.</span></span> <span data-ttu-id="f337e-133">在大容量导入操作期间，ASCII 数据文件中的隐藏字符会导致问题，这些问题会引发“发现意外空字符”错误。</span><span class="sxs-lookup"><span data-stu-id="f337e-133">During a bulk-import operation, hidden characters in an ASCII data file can cause problems that cause an error of "unexpected null found".</span></span> <span data-ttu-id="f337e-134">查找并删除所有隐藏字符有助于避免此问题。</span><span class="sxs-lookup"><span data-stu-id="f337e-134">Finding and removing all the hidden characters should help prevent this problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f337e-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f337e-135">See Also</span></span>  
 <span data-ttu-id="f337e-136">[使用 bcp 实用工具导入和导出大容量数据 (SQL Server)](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f337e-136">[Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span></span>  
 <span data-ttu-id="f337e-137">[使用 BULK INSERT 或 OPENROWSET (BULK...) 导入批量数据 (SQL Server)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f337e-137">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="f337e-138">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f337e-138">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="f337e-139">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f337e-139">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="f337e-140">[用于批量导入或导出的数据格式 (SQL Server)](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f337e-140">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="f337e-141">OPENROWSET (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f337e-141">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
