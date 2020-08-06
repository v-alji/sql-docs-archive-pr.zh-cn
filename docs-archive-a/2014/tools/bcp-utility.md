---
title: bcp 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server]
- exporting data
- row exporting [SQL Server]
- copying data [SQL Server], bcp utility
- command prompt utilities [SQL Server], bcp
- tables [SQL Server], importing data
- column importing [SQL Server]
- bcp utility [SQL Server], command options
- file exporting [SQL Server]
- bulk copy [SQL Server]
- bcp utility [SQL Server], about bcp utility
- tables [SQL Server], exporting data
- row importing [SQL Server]
- importing data, bcp utility
- file importing [SQL Server]
- column exporting [SQL Server]
ms.assetid: c0af54f5-ca4a-4995-a3a4-0ce39c30ec38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ddc4c4e7023a83bfde9295a1410e7db5cb90b84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587114"
---
# <a name="bcp-utility"></a><span data-ttu-id="4b136-102">bcp 实用工具</span><span class="sxs-lookup"><span data-stu-id="4b136-102">bcp Utility</span></span>
  <span data-ttu-id="4b136-103">**Bcp**实用工具 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在实例和用户指定格式的数据文件之间大容量复制数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-103">The **bcp** utility bulk copies data between an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span> <span data-ttu-id="4b136-104">使用 **bcp** 实用工具可以将大量新行导入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表，或将表数据导出到数据文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-104">The **bcp** utility can be used to import large numbers of new rows into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables or to export data out of tables into data files.</span></span> <span data-ttu-id="4b136-105">除非与 **queryout** 选项一起使用，否则使用该实用工具不需要了解 [!INCLUDE[tsql](../includes/tsql-md.md)]知识。</span><span class="sxs-lookup"><span data-stu-id="4b136-105">Except when used with the **queryout** option, the utility requires no knowledge of [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="4b136-106">若要将数据导入表中，必须使用为该表创建的格式文件，或者必须了解表的结构以及对于该表中的列有效的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4b136-106">To import data into a table, you must either use a format file created for that table or understand the structure of the table and the types of data that are valid for its columns.</span></span>  
  
 <span data-ttu-id="4b136-107">![主题链接图标](../../2014/database-engine/media/topic-link.gif "“主题链接”图标") 有关 bcp 语法中使用的语法约定，请参阅 [Transact-SQL 语法约定 (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4b136-107">![Topic link icon](../../2014/database-engine/media/topic-link.gif "Topic link icon") For the syntax conventions that are used for the **bcp** syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-108">如果使用 **bcp** 备份数据，请创建一个格式化文件来记录数据格式。</span><span class="sxs-lookup"><span data-stu-id="4b136-108">If you use **bcp** to back up your data, create a format file to record the data format.</span></span> <span data-ttu-id="4b136-109">**bcp** 数据文件 不包括 任何架构或格式信息，因此如果已删除表或视图并且不具备格式化文件，则可能无法导入数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-109">**bcp** data files do not include any schema or format information, so if a table or view is dropped and you do not have a format file, you may be unable to import the data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b136-110">语法</span><span class="sxs-lookup"><span data-stu-id="4b136-110">Syntax</span></span>  
  
```  
  
   bcp [database_name.] schema.{table_name | view_name | "query" {indata_file | outdata_file | queryoutdata_file | format nul}  
  
[-apacket_size]  
[-bbatch_size]  
[-c]  
[-C { ACP | OEM | RAW | code_page } ]  
[-ddatabase_name]  
[-eerr_file]  
[-E]  
[-fformat_file]  
[-Ffirst_row]  
[-h"hint [,...n]"]   
[-iinput_file]  
[-k]  
[-Kapplication_intent]  
[-Llast_row]  
[-mmax_errors]  
[-n]  
[-N]  
[-ooutput_file]  
[-Ppassword]  
[-q]  
[-rrow_term]  
[-R]  
[-S [server_name[\instance_name]]  
[-tfield_term]  
[-T]  
[-Ulogin_id]  
[-v]  
[-V (80 | 90 | 100 | 110)]  
[-w]  
[-x]  
/?  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b136-111">参数</span><span class="sxs-lookup"><span data-stu-id="4b136-111">Arguments</span></span>  
 <span data-ttu-id="4b136-112">*data_file*</span><span class="sxs-lookup"><span data-stu-id="4b136-112">*data_file*</span></span>  
 <span data-ttu-id="4b136-113">数据文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="4b136-113">Is the full path of the data file.</span></span> <span data-ttu-id="4b136-114">将数据批量导入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时，数据文件将包含要复制到指定的表或视图中的数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-114">When data is bulk imported into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the data file contains the data to be copied into the specified table or view.</span></span> <span data-ttu-id="4b136-115">从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中批量导出数据时，数据文件将包含从表或视图中复制的数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-115">When data is bulk exported from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the data file contains the data copied from the table or view.</span></span> <span data-ttu-id="4b136-116">路径可以有 1 到 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="4b136-116">The path can have from 1 through 255 characters.</span></span> <span data-ttu-id="4b136-117">数据文件最多可包含2个<sup>63</sup> -1 行。</span><span class="sxs-lookup"><span data-stu-id="4b136-117">The data file can contain a maximum of 2<sup>63</sup> - 1 rows.</span></span>  
  
 <span data-ttu-id="4b136-118">*database_name*</span><span class="sxs-lookup"><span data-stu-id="4b136-118">*database_name*</span></span>  
 <span data-ttu-id="4b136-119">指定的表或视图所在数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-119">Is the name of the database in which the specified table or view resides.</span></span> <span data-ttu-id="4b136-120">如果未指定，则使用用户的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="4b136-120">If not specified, this is the default database for the user.</span></span>  
  
 <span data-ttu-id="4b136-121">也可以使用 `d-` 显式指定数据库名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-121">You can also explicitly specify the database name with `d-`.</span></span>  
  
 <span data-ttu-id="4b136-122">**in** _data_file_  |  **out**_data_file_  |  **queryout**_data_file_  |  **格式 nul**</span><span class="sxs-lookup"><span data-stu-id="4b136-122">**in** _data_file_ | **out**_data_file_ | **queryout**_data_file_ | **format nul**</span></span>  
 <span data-ttu-id="4b136-123">指定大容量复制的方向，具体如下：</span><span class="sxs-lookup"><span data-stu-id="4b136-123">Specifies the direction of the bulk copy, as follows:</span></span>  
  
-   <span data-ttu-id="4b136-124">**in** 从文件复制到数据库表或视图。</span><span class="sxs-lookup"><span data-stu-id="4b136-124">**in** copies from a file into the database table or view.</span></span>  
  
-   <span data-ttu-id="4b136-125">**out** 从数据库表或视图复制到文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-125">**out** copies from the database table or view to a file.</span></span> <span data-ttu-id="4b136-126">如果指定了现有文件，则该文件将被覆盖。</span><span class="sxs-lookup"><span data-stu-id="4b136-126">If you specify an existing file, the file is overwritten.</span></span> <span data-ttu-id="4b136-127">提取数据时，请注意 **bcp** 实用工具将空字符串表示为 null，而将 null 字符串表示为空字符串。</span><span class="sxs-lookup"><span data-stu-id="4b136-127">When extracting data, note that the **bcp** utility represents an empty string as a null and a null string as an empty string.</span></span>  
  
-   <span data-ttu-id="4b136-128">**queryout** 从查询中复制，仅当从查询大容量复制数据时才必须指定此选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-128">**queryout** copies from a query and must be specified only when bulk copying data from a query.</span></span>  
  
-   <span data-ttu-id="4b136-129">**format**根据指定的选项（ (**-n**、 `-c` 、 `-w` 或 **-n**) 以及表或视图的分隔符创建格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-129">**format** creates a format file based on the option specified (**-n**, `-c`, `-w`, or **-N**) and the table or view delimiters.</span></span> <span data-ttu-id="4b136-130">大容量复制数据时， **bcp**命令可以引用一个格式化文件，从而使您能够以交互方式重新输入格式信息。</span><span class="sxs-lookup"><span data-stu-id="4b136-130">When bulk copying data, the **bcp** command can refer to a format file, which saves you from re-entering format information interactively.</span></span> <span data-ttu-id="4b136-131">**format** 选项要求指定 **-f** 选项；创建 XML 格式化文件时还需要指定 **-x** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-131">The **format** option requires the **-f** option; creating an XML format file, also requires the **-x** option.</span></span> <span data-ttu-id="4b136-132">有关详细信息，请参阅 [创建格式化文件 (SQL Server)](../relational-databases/import-export/create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-132">For more information, see [Create a Format File &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="4b136-133">必须将 **nul** 指定为值 (**format nul**)。</span><span class="sxs-lookup"><span data-stu-id="4b136-133">You must specify **nul** as the value (**format nul**).</span></span>  
  
 <span data-ttu-id="4b136-134">*owner*</span><span class="sxs-lookup"><span data-stu-id="4b136-134">*owner*</span></span>  
 <span data-ttu-id="4b136-135">表或视图的所有者的名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-135">Is the name of the owner of the table or view.</span></span> <span data-ttu-id="4b136-136">如果执行该操作的用户拥有指定的表或视图，则*owner* 是可选的。</span><span class="sxs-lookup"><span data-stu-id="4b136-136">*owner* is optional if the user performing the operation owns the specified table or view.</span></span> <span data-ttu-id="4b136-137">如果未指定 *owner* ，并且执行该操作的用户不是指定的表或视图的所有者，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将返回错误消息，而且该操作将取消。</span><span class="sxs-lookup"><span data-stu-id="4b136-137">If *owner* is not specified and the user performing the operation does not own the specified table or view, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] returns an error message, and the operation is canceled.</span></span>  
  
 <span data-ttu-id="4b136-138">**"** _查询_ **"**</span><span class="sxs-lookup"><span data-stu-id="4b136-138">**"** _query_ **"**</span></span>  
 <span data-ttu-id="4b136-139">一个返回结果集的 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="4b136-139">Is a [!INCLUDE[tsql](../includes/tsql-md.md)] query that returns a result set.</span></span> <span data-ttu-id="4b136-140">如果该查询返回多个结果集，则只将第一个结果集复制到数据文件，而忽略其余的结果集。</span><span class="sxs-lookup"><span data-stu-id="4b136-140">If the query returns multiple result sets, only the first result set is copied to the data file; subsequent result sets are ignored.</span></span> <span data-ttu-id="4b136-141">将查询用双引号括起来，将查询中嵌入的任何内容用单引号括起来。</span><span class="sxs-lookup"><span data-stu-id="4b136-141">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span> <span data-ttu-id="4b136-142">从查询大容量复制数据时，也必须指定**queryout** 。</span><span class="sxs-lookup"><span data-stu-id="4b136-142">**queryout** must also be specified when bulk copying data from a query.</span></span>  
  
 <span data-ttu-id="4b136-143">只要在执行 bcp 语句之前存储过程内引用的所有表均存在，查询就可以引用该存储过程。</span><span class="sxs-lookup"><span data-stu-id="4b136-143">The query can reference a stored procedure as long as all tables referenced inside the stored procedure exist prior to executing the bcp statement.</span></span> <span data-ttu-id="4b136-144">例如，如果存储过程生成一个临时表，则 **bcp** 语句便会失败，因为该临时表只在运行时可用，而在语句执行时不可用。</span><span class="sxs-lookup"><span data-stu-id="4b136-144">For example, if the stored procedure generates a temp table, the **bcp** statement fails because the temp table is available only at run time and not at statement execution time.</span></span> <span data-ttu-id="4b136-145">在这种情况下，应考虑将存储过程的结果插入表中，然后使用 **bcp** 将数据从表复制到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="4b136-145">In this case, consider inserting the results of the stored procedure into a table and then use **bcp** to copy the data from the table into a data file.</span></span>  
  
 <span data-ttu-id="4b136-146">*table_name*</span><span class="sxs-lookup"><span data-stu-id="4b136-146">*table_name*</span></span>  
 <span data-ttu-id="4b136-147">将数据导入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**) 时为目标表名称，将数据从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导出时 (**out**) 为源表名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-147">Is the name of the destination table when importing data into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**), and the source table when exporting data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).</span></span>  
  
 <span data-ttu-id="4b136-148">view_name</span><span class="sxs-lookup"><span data-stu-id="4b136-148">*view_name*</span></span>  
 <span data-ttu-id="4b136-149">将数据复制到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**) 时为目标视图名称，从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中复制数据时 (**out**) 为源视图名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-149">Is the name of the destination view when copying data into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**), and the source view when copying data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).</span></span> <span data-ttu-id="4b136-150">只有其中所有列都引用同一个表的视图才能用作目标视图。</span><span class="sxs-lookup"><span data-stu-id="4b136-150">Only views in which all columns refer to the same table can be used as destination views.</span></span> <span data-ttu-id="4b136-151">有关将数据复制到视图的限制的详细信息，请参阅[《INSERT &#40;Transact-SQL&#41;》](/sql/t-sql/statements/insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4b136-151">For more information on the restrictions for copying data into views, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
 <span data-ttu-id="4b136-152">-a packet_size</span><span class="sxs-lookup"><span data-stu-id="4b136-152">**-a** _packet_size_</span></span>  
 <span data-ttu-id="4b136-153">指定服务器发出或接收的每个网络数据包的字节数。</span><span class="sxs-lookup"><span data-stu-id="4b136-153">Specifies the number of bytes, per network packet, sent to and from the server.</span></span> <span data-ttu-id="4b136-154">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] （或 **sp_configure** 系统存储过程）来设置服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-154">A server configuration option can be set by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (or the **sp_configure** system stored procedure).</span></span> <span data-ttu-id="4b136-155">但是，可以使用此选项逐个替代服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-155">However, the server configuration option can be overridden on an individual basis by using this option.</span></span> <span data-ttu-id="4b136-156">*packet_size* 的取值范围为 4096 到 65535 字节，默认为 4096 字节。</span><span class="sxs-lookup"><span data-stu-id="4b136-156">*packet_size* can be from 4096 to 65535 bytes; the default is 4096.</span></span>  
  
 <span data-ttu-id="4b136-157">增大数据包可以提高大容量复制操作的性能。</span><span class="sxs-lookup"><span data-stu-id="4b136-157">Increased packet size can enhance performance of bulk-copy operations.</span></span> <span data-ttu-id="4b136-158">如果无法得到请求的较大数据包，则使用默认值。</span><span class="sxs-lookup"><span data-stu-id="4b136-158">If a larger packet is requested but cannot be granted, the default is used.</span></span> <span data-ttu-id="4b136-159">**bcp** 实用工具生成的性能统计信息可以显示所用的数据包大小。</span><span class="sxs-lookup"><span data-stu-id="4b136-159">The performance statistics generated by the **bcp** utility show the packet size used.</span></span>  
  
 <span data-ttu-id="4b136-160">**-b** _batch_size_</span><span class="sxs-lookup"><span data-stu-id="4b136-160">**-b** _batch_size_</span></span>  
 <span data-ttu-id="4b136-161">指定每批导入数据的行数。</span><span class="sxs-lookup"><span data-stu-id="4b136-161">Specifies the number of rows per batch of imported data.</span></span> <span data-ttu-id="4b136-162">每个批次均作为一个单独的事务进行导入并记录，在提交之前会导入整批。</span><span class="sxs-lookup"><span data-stu-id="4b136-162">Each batch is imported and logged as a separate transaction that imports the whole batch before being committed.</span></span> <span data-ttu-id="4b136-163">默认情况下，数据文件中的所有行均作为一个批次导入。</span><span class="sxs-lookup"><span data-stu-id="4b136-163">By default, all the rows in the data file are imported as one batch.</span></span> <span data-ttu-id="4b136-164">若要将行分为多个批次进行操作，请指定小于数据文件中的行数的 *batch_size* 。</span><span class="sxs-lookup"><span data-stu-id="4b136-164">To distribute the rows among multiple batches, specify a *batch_size* that is smaller than the number of rows in the data file.</span></span> <span data-ttu-id="4b136-165">如果任何批次的事务失败，则将只回滚当前批次中的插入。</span><span class="sxs-lookup"><span data-stu-id="4b136-165">If the transaction for any batch fails, only insertions from the current batch are rolled back.</span></span> <span data-ttu-id="4b136-166">已经由已提交事务导入的批次不会受到将来失败的影响。</span><span class="sxs-lookup"><span data-stu-id="4b136-166">Batches already imported by committed transactions are unaffected by a later failure.</span></span>  
  
 <span data-ttu-id="4b136-167">不要将此选项与 **-h "** ROWS_PER_BATCH \*\* = *`bb`* "\*\* 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="4b136-167">Do not use this option in conjunction with the **-h"** ROWS_PER_BATCH **=*`bb`*"** option.</span></span>  
  
 `-c`  
 <span data-ttu-id="4b136-168">使用字符数据类型执行该操作。</span><span class="sxs-lookup"><span data-stu-id="4b136-168">Performs the operation using a character data type.</span></span> <span data-ttu-id="4b136-169">此选项不提示输入每个字段;它使用 `char` 作为存储类型，不带前缀，使用**\t** (制表符) 作为字段分隔符，使用**\r\n** (换行符) 作为行终止符。</span><span class="sxs-lookup"><span data-stu-id="4b136-169">This option does not prompt for each field; it uses `char` as the storage type, without prefixes and with **\t** (tab character) as the field separator and **\r\n** (newline character) as the row terminator.</span></span> <span data-ttu-id="4b136-170">`-c` 与 `-w` 不兼容。</span><span class="sxs-lookup"><span data-stu-id="4b136-170">`-c` is not compatible with `-w`.</span></span>  
  
 <span data-ttu-id="4b136-171">有关详细信息，请参阅[使用字符格式导入或导出数据 (SQL Server)](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-171">For more information, see [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-172">**-C** { **ACP** | **OEM** | **RAW** | *code_page* }</span><span class="sxs-lookup"><span data-stu-id="4b136-172">**-C** { **ACP** | **OEM** | **RAW** | *code_page* }</span></span>  
 <span data-ttu-id="4b136-173">指定该数据文件中数据的代码页。</span><span class="sxs-lookup"><span data-stu-id="4b136-173">Specifies the code page of the data in the data file.</span></span> <span data-ttu-id="4b136-174">*code_page*仅当数据包含 `char` `varchar` `text` 大于127或小于32的字符值的、或列时，code_page 才适用。</span><span class="sxs-lookup"><span data-stu-id="4b136-174">*code_page* is relevant only if the data contains `char`, `varchar`, or `text` columns with character values greater than 127 or less than 32.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-175">建议在格式化文件中为每个列指定一个排序规则名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-175">We recommend specifying a collation name for each column in a format file.</span></span>  
  
|<span data-ttu-id="4b136-176">代码页值</span><span class="sxs-lookup"><span data-stu-id="4b136-176">Code page value</span></span>|<span data-ttu-id="4b136-177">说明</span><span class="sxs-lookup"><span data-stu-id="4b136-177">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="4b136-178">ACP</span><span class="sxs-lookup"><span data-stu-id="4b136-178">ACP</span></span>|[!INCLUDE[vcpransi](../includes/vcpransi-md.md)]<span data-ttu-id="4b136-179">/Microsoft Windows (ISO 1252)。</span><span class="sxs-lookup"><span data-stu-id="4b136-179">/Microsoft Windows (ISO 1252).</span></span>|  
|<span data-ttu-id="4b136-180">OEM</span><span class="sxs-lookup"><span data-stu-id="4b136-180">OEM</span></span>|<span data-ttu-id="4b136-181">客户端使用的默认代码页。</span><span class="sxs-lookup"><span data-stu-id="4b136-181">Default code page used by the client.</span></span> <span data-ttu-id="4b136-182">未指定 **-C** 时使用的默认代码页。</span><span class="sxs-lookup"><span data-stu-id="4b136-182">This is the default code page used if **-C** is not specified.</span></span>|  
|<span data-ttu-id="4b136-183">RAW</span><span class="sxs-lookup"><span data-stu-id="4b136-183">RAW</span></span>|<span data-ttu-id="4b136-184">不进行代码页间的转换。</span><span class="sxs-lookup"><span data-stu-id="4b136-184">No conversion from one code page to another occurs.</span></span> <span data-ttu-id="4b136-185">因为不进行转换，所以这是最快的选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-185">This is the fastest option because no conversion occurs.</span></span>|  
|<span data-ttu-id="4b136-186">*code_page*</span><span class="sxs-lookup"><span data-stu-id="4b136-186">*code_page*</span></span>|<span data-ttu-id="4b136-187">特定的代码页编号，例如 850。</span><span class="sxs-lookup"><span data-stu-id="4b136-187">Specific code page number; for example, 850.</span></span><br /><br /> <span data-ttu-id="4b136-188">**&#42;&#42; 重要 &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]不支持代码页 65001 (UTF-8 编码) 。</span><span class="sxs-lookup"><span data-stu-id="4b136-188">**&#42;&#42; Important &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not support code page 65001 (UTF-8 encoding).</span></span>|  
  
 <span data-ttu-id="4b136-189">`-d`*database_name*</span><span class="sxs-lookup"><span data-stu-id="4b136-189">`-d` *database_name*</span></span>  
 <span data-ttu-id="4b136-190">指定要连接到的数据库。</span><span class="sxs-lookup"><span data-stu-id="4b136-190">Specifies the database to connect to.</span></span> <span data-ttu-id="4b136-191">默认情况下，bcp.exe 连接到用户的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="4b136-191">By default, bcp.exe connects to the user's default database.</span></span> <span data-ttu-id="4b136-192">如果 `-d` 指定了*database_name*和三部分名称 (*database_name*，作为第一个参数传递到 bcp.exe) ，则会发生错误，因为不能将数据库名称指定两次。如果*database_name*以连字符开头 (-) 或正斜杠 (/) ，则不要在 `-d` 和数据库名称之间添加空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-192">If `-d`*database_name* and a three part name (*database_name.schema.table*, passed as the first parameter to bcp.exe) is specified, an error will occur because you cannot specify the database name twice.If *database_name* begins with a hyphen (-) or a forward slash (/), do not add a space between `-d` and the database name.</span></span>  
  
 <span data-ttu-id="4b136-193">**-e** _err_file_</span><span class="sxs-lookup"><span data-stu-id="4b136-193">**-e** _err_file_</span></span>  
 <span data-ttu-id="4b136-194">指定错误文件的完整路径，此文件用于存储 **bcp** 实用工具无法从文件传输到数据库的所有行。</span><span class="sxs-lookup"><span data-stu-id="4b136-194">Specifies the full path of an error file used to store any rows that the **bcp** utility cannot transfer from the file to the database.</span></span> <span data-ttu-id="4b136-195">**bcp** 命令产生的错误消息将被发送到用户的工作站。</span><span class="sxs-lookup"><span data-stu-id="4b136-195">Error messages from the **bcp** command go to the workstation of the user.</span></span> <span data-ttu-id="4b136-196">如果不使用此选项，则不会创建错误文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-196">If this option is not used, an error file is not created.</span></span>  
  
 <span data-ttu-id="4b136-197">如果 *err_file* 以连字符 (-) 或正斜杠 (/) 开头，则不要在 **-e** 与 *err_file* 值之间包含空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-197">If *err_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-e** and the *err_file* value.</span></span>  
  
 <span data-ttu-id="4b136-198">**-E**</span><span class="sxs-lookup"><span data-stu-id="4b136-198">**-E**</span></span>  
 <span data-ttu-id="4b136-199">指定导入数据文件中的标识值用于标识列。</span><span class="sxs-lookup"><span data-stu-id="4b136-199">Specifies that identity value or values in the imported data file are to be used for the identity column.</span></span> <span data-ttu-id="4b136-200">如果未指定 **-E** ，则将忽略要导入的数据文件中此列的标识值，而且 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将根据创建表期间指定的种子值和增量值自动分配唯一值。</span><span class="sxs-lookup"><span data-stu-id="4b136-200">If **-E** is not given, the identity values for this column in the data file being imported are ignored, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns unique values based on the seed and increment values specified during table creation.</span></span>  
  
 <span data-ttu-id="4b136-201">如果数据文件不包含表或视图中的标识列的值，则可使用格式化文件指定，在导入数据时应跳过表或视图中的标识列； [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将自动为该列分配唯一值。</span><span class="sxs-lookup"><span data-stu-id="4b136-201">If the data file does not contain values for the identity column in the table or view, use a format file to specify that the identity column in the table or view should be skipped when importing data; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns unique values for the column.</span></span> <span data-ttu-id="4b136-202">有关详细信息，请参阅 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4b136-202">For more information, see [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).</span></span>  
  
 <span data-ttu-id="4b136-203">**-E** 选项有一个特殊的权限要求。</span><span class="sxs-lookup"><span data-stu-id="4b136-203">The **-E** option has a special permissions requirement.</span></span> <span data-ttu-id="4b136-204">有关详细信息，请参阅本主题后面的“备注”。</span><span class="sxs-lookup"><span data-stu-id="4b136-204">For more information, see "Remarks" later in this topic.</span></span>  
  
 <span data-ttu-id="4b136-205">**-f** _format_file_</span><span class="sxs-lookup"><span data-stu-id="4b136-205">**-f** _format_file_</span></span>  
 <span data-ttu-id="4b136-206">指定格式化文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="4b136-206">Specifies the full path of a format file.</span></span> <span data-ttu-id="4b136-207">此选项的含义取决于使用它的环境，具体如下：</span><span class="sxs-lookup"><span data-stu-id="4b136-207">The meaning of this option depends on the environment in which it is used, as follows:</span></span>  
  
-   <span data-ttu-id="4b136-208">如果 **-f** 与 **format** 选项一起使用，则将为指定的表或视图创建指定的 *format_file* 。</span><span class="sxs-lookup"><span data-stu-id="4b136-208">If **-f** is used with the **format** option, the specified *format_file* is created for the specified table or view.</span></span> <span data-ttu-id="4b136-209">若要创建 XML 格式化文件，请同时指定 **-x** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-209">To create an XML format file, also specify the **-x** option.</span></span> <span data-ttu-id="4b136-210">有关详细信息，请参阅 [创建格式化文件 (SQL Server)](../relational-databases/import-export/create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-210">For more information, see [Create a Format File &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4b136-211">如果与 **in** 或 **out** 选项一起使用，则 **-f** 需要一个现有的格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-211">If used with the **in** or **out** option, **-f** requires an existing format file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b136-212">与 **in** 或 **out** 选项一起使用时，格式化文件是可选的。</span><span class="sxs-lookup"><span data-stu-id="4b136-212">Using a format file in with the **in** or **out** option is optional.</span></span> <span data-ttu-id="4b136-213">如果没有 **-f**选项，则在未指定 **-n**、 `-c` 、 `-w` 或 **-n**时，该命令将提示输入格式信息，并允许你将响应保存在 (默认文件名为 bcp.fmt) 的格式化文件中。</span><span class="sxs-lookup"><span data-stu-id="4b136-213">In the absence of the **-f** option, if **-n**, `-c`, `-w`, or **-N** is not specified, the command prompts for format information and lets you save your responses in a format file (whose default file name is Bcp.fmt).</span></span>  
  
 <span data-ttu-id="4b136-214">如果 *format_file* 以连字符 (-) 或正斜杠 (/) 开头，则不要在 **-f** 与 *format_file* 值之间包含空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-214">If *format_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-f** and the *format_file* value.</span></span>  
  
 <span data-ttu-id="4b136-215">**-F** _first_row_</span><span class="sxs-lookup"><span data-stu-id="4b136-215">**-F** _first_row_</span></span>  
 <span data-ttu-id="4b136-216">指定要从表中导出或从数据文件导入的第一行的编号。</span><span class="sxs-lookup"><span data-stu-id="4b136-216">Specifies the number of the first row to export from a table or import from a data file.</span></span> <span data-ttu-id="4b136-217">此参数需要大于 ( # A0) 0 但小于 (\<) 或等于 (=) 总数行的值。</span><span class="sxs-lookup"><span data-stu-id="4b136-217">This parameter requires a value greater than (>) 0 but less than (\<) or equal to (=) the total number rows.</span></span> <span data-ttu-id="4b136-218">如果未指定此参数，则默认为文件的第一行。</span><span class="sxs-lookup"><span data-stu-id="4b136-218">In the absence of this parameter, the default is the first row of the file.</span></span>  
  
 <span data-ttu-id="4b136-219">*first_row* 可以是一个最大为 2^63-1 的正整数值。</span><span class="sxs-lookup"><span data-stu-id="4b136-219">*first_row* can be a positive integer with a value up to 2^63-1.</span></span> <span data-ttu-id="4b136-220">**-F**_first_row_ 的值从 1 开始。</span><span class="sxs-lookup"><span data-stu-id="4b136-220">**-F**_first_row_ is 1-based.</span></span>  
  
 <span data-ttu-id="4b136-221">**-h"** _hint_[ **,**... *n*] **"**</span><span class="sxs-lookup"><span data-stu-id="4b136-221">**-h"** _hint_[ **,**... *n*] **"**</span></span>  
 <span data-ttu-id="4b136-222">指定向表或视图中大容量导入数据时要用到的提示。</span><span class="sxs-lookup"><span data-stu-id="4b136-222">Specifies the hint or hints to be used during a bulk import of data into a table or view.</span></span>  
  
 <span data-ttu-id="4b136-223">排序\*\* (**_列_[ASC |DESC] [**，**.。。*n*]**) \*\*</span><span class="sxs-lookup"><span data-stu-id="4b136-223">ORDER **(**_column_[ASC | DESC] [**,**...*n*]**)**</span></span>  
 <span data-ttu-id="4b136-224">数据文件中的数据排序次序。</span><span class="sxs-lookup"><span data-stu-id="4b136-224">The sort order of the data in the data file.</span></span> <span data-ttu-id="4b136-225">如果根据表中的聚集索引（如果有）对要导入的数据排序，则可提高批量导入的性能。</span><span class="sxs-lookup"><span data-stu-id="4b136-225">Bulk import performance is improved if the data being imported is sorted according to the clustered index on the table, if any.</span></span> <span data-ttu-id="4b136-226">如果数据文件以不同的次序（即不同于聚集索引键的次序）排序，或者表中不存在任何聚集索引，则将忽略 ORDER 子句。</span><span class="sxs-lookup"><span data-stu-id="4b136-226">If the data file is sorted in a different order, that is other than the order of a clustered index key, or if there is no clustered index on the table, the ORDER clause is ignored.</span></span> <span data-ttu-id="4b136-227">提供的列名必须是目标表中有效的列名。</span><span class="sxs-lookup"><span data-stu-id="4b136-227">The column names supplied must be valid column names in the destination table.</span></span> <span data-ttu-id="4b136-228">默认情况下， **bcp** 假定数据文件没有排序。</span><span class="sxs-lookup"><span data-stu-id="4b136-228">By default, **bcp** assumes the data file is unordered.</span></span> <span data-ttu-id="4b136-229">对于经过优化的批量导入， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 还将验证导入的数据是否已排序。</span><span class="sxs-lookup"><span data-stu-id="4b136-229">For optimized bulk import, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] also validates that the imported data is sorted.</span></span>  
  
 <span data-ttu-id="4b136-230">ROWS_PER_BATCH **=** _bb_</span><span class="sxs-lookup"><span data-stu-id="4b136-230">ROWS_PER_BATCH **=**_bb_</span></span>  
 <span data-ttu-id="4b136-231">每批数据的行数（即 *bb*）。</span><span class="sxs-lookup"><span data-stu-id="4b136-231">Number of rows of data per batch (as *bb*).</span></span> <span data-ttu-id="4b136-232">在未指定 **-b** 时使用，这将导致整个数据文件作为单个事务发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="4b136-232">Used when **-b** is not specified, resulting in the entire data file being sent to the server as a single transaction.</span></span> <span data-ttu-id="4b136-233">服务器根据 *bb*值优化大容量加载。</span><span class="sxs-lookup"><span data-stu-id="4b136-233">The server optimizes the bulk load according to the value *bb*.</span></span> <span data-ttu-id="4b136-234">默认情况下，ROWS_PER_BATCH 是未知的。</span><span class="sxs-lookup"><span data-stu-id="4b136-234">By default, ROWS_PER_BATCH is unknown.</span></span>  
  
 <span data-ttu-id="4b136-235">KILOBYTES_PER_BATCH **=** _cc_</span><span class="sxs-lookup"><span data-stu-id="4b136-235">KILOBYTES_PER_BATCH **=** _cc_</span></span>  
 <span data-ttu-id="4b136-236">每批的以千字节计数的近似数据量（即 *cc*）。</span><span class="sxs-lookup"><span data-stu-id="4b136-236">Approximate number of kilobytes of data per batch (as *cc*).</span></span> <span data-ttu-id="4b136-237">默认情况下，KILOBYTES_PER_BATCH 是未知的。</span><span class="sxs-lookup"><span data-stu-id="4b136-237">By default, KILOBYTES_PER_BATCH is unknown.</span></span>  
  
 <span data-ttu-id="4b136-238">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="4b136-238">TABLOCK</span></span>  
 <span data-ttu-id="4b136-239">指定在大容量加载操作期间获取大容量更新表级别的锁；否则，获取行级别的锁。</span><span class="sxs-lookup"><span data-stu-id="4b136-239">Specifies that a bulk update table-level lock is acquired for the duration of the bulk load operation; otherwise, a row-level lock is acquired.</span></span> <span data-ttu-id="4b136-240">由于在大容量复制操作期间拥有锁可以减少表中的锁争夺，所以此提示可显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="4b136-240">This hint significantly improves performance because holding a lock for the duration of the bulk-copy operation reduces lock contention on the table.</span></span> <span data-ttu-id="4b136-241">如果表没有索引并且指定了 **TABLOCK** ，则该表可以同时由多个客户端加载。</span><span class="sxs-lookup"><span data-stu-id="4b136-241">A table can be loaded concurrently by multiple clients if the table has no indexes and **TABLOCK** is specified.</span></span> <span data-ttu-id="4b136-242">默认情况下，锁定行为由表选项 **table lock on bulk load**决定。</span><span class="sxs-lookup"><span data-stu-id="4b136-242">By default, locking behavior is determined by the table option **table lock on bulk load**.</span></span>  
  
 <span data-ttu-id="4b136-243">CHECK_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="4b136-243">CHECK_CONSTRAINTS</span></span>  
 <span data-ttu-id="4b136-244">指定在批量导入操作期间，必须检查所有对目标表或视图的约束。</span><span class="sxs-lookup"><span data-stu-id="4b136-244">Specifies that all constraints on the target table or view must be checked during the bulk-import operation.</span></span> <span data-ttu-id="4b136-245">如果没有 CHECK_CONSTRAINTS 提示，则忽略所有 CHECK 和 FOREIGN KEY 约束；操作完成后，对表的约束将被标记为不可信。</span><span class="sxs-lookup"><span data-stu-id="4b136-245">Without the CHECK_CONSTRAINTS hint, any CHECK and FOREIGN KEY constraints are ignored, and after the operation the constraint on the table is marked as not-trusted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-246">始终强制使用 UNIQUE、PRIMARY KEY 和 NOT NULL 约束。</span><span class="sxs-lookup"><span data-stu-id="4b136-246">UNIQUE, PRIMARY KEY, and NOT NULL constraints are always enforced.</span></span>  
  
 <span data-ttu-id="4b136-247">在某些时候，需要检查整个表的约束。</span><span class="sxs-lookup"><span data-stu-id="4b136-247">At some point, you will need to check the constraints on the entire table.</span></span> <span data-ttu-id="4b136-248">如果在批量导入操作之前表为非空状态，则重新验证约束的开销可能超过将 CHECK 约束应用于增量数据的开销。</span><span class="sxs-lookup"><span data-stu-id="4b136-248">If the table was nonempty before the bulk import operation, the cost of revalidating the constraint may exceed the cost of applying CHECK constraints to the incremental data.</span></span> <span data-ttu-id="4b136-249">因此，建议您在正常情况下，在进行增量式批量导入时启用约束检查。</span><span class="sxs-lookup"><span data-stu-id="4b136-249">Therefore, we recommend that normally you enable constraint checking during an incremental bulk import.</span></span>  
  
 <span data-ttu-id="4b136-250">当输入数据包含违反约束的行时，您可能希望禁用约束（默认行为）。</span><span class="sxs-lookup"><span data-stu-id="4b136-250">A situation in which you might want constraints disabled (the default behavior) is if the input data contains rows that violate constraints.</span></span> <span data-ttu-id="4b136-251">如果禁用 CHECK 约束，您可以导入数据，然后使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句删除无效数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-251">With CHECK constraints disabled, you can import the data and then use [!INCLUDE[tsql](../includes/tsql-md.md)] statements to remove data that is not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-252">**bcp** 现在会强制执行数据验证和数据检查，这样，在对数据文件中的无效数据执行脚本时，可能会导致脚本失败。</span><span class="sxs-lookup"><span data-stu-id="4b136-252">**bcp** now enforces data validation and data checks that might cause scripts to fail if they are executed on invalid data in a data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-253">**-m** _max_errors_ 开关不适用于约束检查。</span><span class="sxs-lookup"><span data-stu-id="4b136-253">The **-m** _max_errors_ switch does not apply to constraint checking.</span></span>  
  
 <span data-ttu-id="4b136-254">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="4b136-254">FIRE_TRIGGERS</span></span>  
 <span data-ttu-id="4b136-255">与 **in** 参数一同指定，在目标表中定义的任何插入触发器都将在大容量复制操作期间运行。</span><span class="sxs-lookup"><span data-stu-id="4b136-255">Specified with the **in** argument, any insert triggers defined on the destination table will run during the bulk-copy operation.</span></span> <span data-ttu-id="4b136-256">如果未指定 FIRE_TRIGGERS，将不运行任何插入触发器。</span><span class="sxs-lookup"><span data-stu-id="4b136-256">If FIRE_TRIGGERS is not specified, no insert triggers will run.</span></span> <span data-ttu-id="4b136-257">对于 **out**、 **queryout**和 **format** 参数，将忽略 FIRE_TRIGGERS。</span><span class="sxs-lookup"><span data-stu-id="4b136-257">FIRE_TRIGGERS is ignored for the **out**, **queryout**, and **format** arguments.</span></span>  
  
 <span data-ttu-id="4b136-258">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="4b136-258">**-i** _input_file_</span></span>  
 <span data-ttu-id="4b136-259">指定响应文件的名称，其中包含对每个数据字段的命令提示问题的响应，当使用交互模式执行大容量复制时 **， (** `-c` `-w` 未 **-N**指定) 。</span><span class="sxs-lookup"><span data-stu-id="4b136-259">Specifies the name of a response file, containing the responses to the command prompt questions for each data field when a bulk copy is being performed using interactive mode (**-n**, `-c`, `-w`, or **-N** not specified).</span></span>  
  
 <span data-ttu-id="4b136-260">如果 *input_file* 以连字符 (-) 或正斜杠 (/) 开头，则不要在 **-i** 与 *input_file* 值之间包含空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-260">If *input_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-i** and the *input_file* value.</span></span>  
  
 <span data-ttu-id="4b136-261">**-k**</span><span class="sxs-lookup"><span data-stu-id="4b136-261">**-k**</span></span>  
 <span data-ttu-id="4b136-262">指定在操作过程中空列应该保留 null 值，而不是所插入列的任何默认值。</span><span class="sxs-lookup"><span data-stu-id="4b136-262">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span> <span data-ttu-id="4b136-263">有关详细信息，请参阅[在批量导入期间保留 Null 或使用默认值 (SQL Server)](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-263">For more information, see [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-264">-K application_intent</span><span class="sxs-lookup"><span data-stu-id="4b136-264">**-K** _application_intent_</span></span>  
 <span data-ttu-id="4b136-265">连接到服务器时声明应用程序工作负荷类型。</span><span class="sxs-lookup"><span data-stu-id="4b136-265">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="4b136-266">唯一可能的值是 **ReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="4b136-266">The only value that is possible is **ReadOnly**.</span></span> <span data-ttu-id="4b136-267">如果未指定 **-K**，bcp 实用工具将不支持连接到 AlwaysOn 可用性组中的次要副本。</span><span class="sxs-lookup"><span data-stu-id="4b136-267">If **-K** is not specified, the bcp utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="4b136-268">有关详细信息，请参阅[活动辅助副本：可读辅助副本 (AlwaysOn 可用性组) ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-268">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="4b136-269">**-L** _last_row_</span><span class="sxs-lookup"><span data-stu-id="4b136-269">**-L** _last_row_</span></span>  
 <span data-ttu-id="4b136-270">指定要从表中导出或从数据文件中导入的最后一行的编号。</span><span class="sxs-lookup"><span data-stu-id="4b136-270">Specifies the number of the last row to export from a table or import from a data file.</span></span> <span data-ttu-id="4b136-271">此参数的值需要大于 ( # A0) 0 但小于 (\<) 或等于 (=) 最后一行的行号。</span><span class="sxs-lookup"><span data-stu-id="4b136-271">This parameter requires a value greater than (>) 0 but less than (\<) or equal to (=) the number of the last row.</span></span> <span data-ttu-id="4b136-272">如果未指定此参数，则默认为文件的最后一行。</span><span class="sxs-lookup"><span data-stu-id="4b136-272">In the absence of this parameter, the default is the last row of the file.</span></span>  
  
 <span data-ttu-id="4b136-273">*last_row* 可以是一个最大为 2^63-1 的正整数值。</span><span class="sxs-lookup"><span data-stu-id="4b136-273">*last_row* can be a positive integer with a value up to 2^63-1.</span></span>  
  
 <span data-ttu-id="4b136-274">**-m** _max_errors_</span><span class="sxs-lookup"><span data-stu-id="4b136-274">**-m** _max_errors_</span></span>  
 <span data-ttu-id="4b136-275">指定取消 **bcp** 操作之前可能出现的语法错误的最大数目。</span><span class="sxs-lookup"><span data-stu-id="4b136-275">Specifies the maximum number of syntax errors that can occur before the **bcp** operation is canceled.</span></span> <span data-ttu-id="4b136-276">语法错误是指将数据转换为目标数据类型时的错误。</span><span class="sxs-lookup"><span data-stu-id="4b136-276">A syntax error implies a data conversion error to the target data type.</span></span> <span data-ttu-id="4b136-277">*max_errors* 总数不包括只能在服务器中检测到的错误，如约束冲突。</span><span class="sxs-lookup"><span data-stu-id="4b136-277">The *max_errors* total excludes any errors that can be detected only at the server, such as constraint violations.</span></span>  
  
 <span data-ttu-id="4b136-278">无法由 **bcp** 实用工具复制的行将被忽略，并计为一个错误。</span><span class="sxs-lookup"><span data-stu-id="4b136-278">A row that cannot be copied by the **bcp** utility is ignored and is counted as one error.</span></span> <span data-ttu-id="4b136-279">如果未包括此选项，则默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="4b136-279">If this option is not included, the default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-280">**-M**选项也不适用于转换 `money` 或 `bigint` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4b136-280">The **-m** option also does not apply to converting the `money` or `bigint` data types.</span></span>  
  
 <span data-ttu-id="4b136-281">**-n**</span><span class="sxs-lookup"><span data-stu-id="4b136-281">**-n**</span></span>  
 <span data-ttu-id="4b136-282">使用数据的本机（数据库）数据类型执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="4b136-282">Performs the bulk-copy operation using the native (database) data types of the data.</span></span> <span data-ttu-id="4b136-283">此选项不提示输入每个字段，它将使用本机值。</span><span class="sxs-lookup"><span data-stu-id="4b136-283">This option does not prompt for each field; it uses the native values.</span></span>  
  
 <span data-ttu-id="4b136-284">有关详细信息，请参阅[使用本机格式导入或导出数据 (SQL Server)](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-284">For more information, see [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-285">**-N**</span><span class="sxs-lookup"><span data-stu-id="4b136-285">**-N**</span></span>  
 <span data-ttu-id="4b136-286">执行大容量复制操作时，对非字符数据使用本机（数据库）数据类型的数据，对字符数据使用 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="4b136-286">Performs the bulk-copy operation using the native (database) data types of the data for noncharacter data, and Unicode characters for character data.</span></span> <span data-ttu-id="4b136-287">此选项是 `-w` 选项的一个替代选项，并具有更高的性能。此选项主要用于通过数据文件将数据从一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例传送到另一个实例。</span><span class="sxs-lookup"><span data-stu-id="4b136-287">This option offers a higher performance alternative to the `-w` option, and is intended for transferring data from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another using a data file.</span></span> <span data-ttu-id="4b136-288">此选项不提示输入每个字段。</span><span class="sxs-lookup"><span data-stu-id="4b136-288">It does not prompt for each field.</span></span> <span data-ttu-id="4b136-289">如果要传送包含 ANSI 扩展字符的数据，并希望利用本机模式的性能优势，则可使用此选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-289">Use this option when you are transferring data that contains ANSI extended characters and you want to take advantage of the performance of native mode.</span></span>  
  
 <span data-ttu-id="4b136-290">有关详细信息信息，请参阅 [使用 Unicode 本机格式导入或导出数据 (SQL Server)](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-290">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-291">如果使用 bcp.exe with **-N**来导出数据，然后将数据导入到同一表架构中，则在存在固定长度的非 Unicode 字符 (列（例如) ）时，可能会看到截断警告 `char(10)` 。</span><span class="sxs-lookup"><span data-stu-id="4b136-291">If you export and then import data to the same table schema by using bcp.exe with **-N**, you might see a truncation warning if there is a fixed length, non-Unicode character column (for example, `char(10)`).</span></span>  
  
 <span data-ttu-id="4b136-292">可忽略该警告。</span><span class="sxs-lookup"><span data-stu-id="4b136-292">The warning can be ignored.</span></span> <span data-ttu-id="4b136-293">解决此警告的一个方法是使用 **-n** 来替代 **-N**。</span><span class="sxs-lookup"><span data-stu-id="4b136-293">One way to resolve this warning is to use **-n** instead of **-N**.</span></span>  
  
 <span data-ttu-id="4b136-294">-o output_file</span><span class="sxs-lookup"><span data-stu-id="4b136-294">**-o** _output_file_</span></span>  
 <span data-ttu-id="4b136-295">指定文件名称，该文件用于接收从命令提示符重定向来的输出。</span><span class="sxs-lookup"><span data-stu-id="4b136-295">Specifies the name of a file that receives output redirected from the command prompt.</span></span>  
  
 <span data-ttu-id="4b136-296">如果 *output_file* 以连字符 (-) 或正斜杠 (/) 开头，则不要在 **-o** 与 *output_file* 值之间包含空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-296">If *output_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-o** and the *output_file* value.</span></span>  
  
 <span data-ttu-id="4b136-297">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="4b136-297">**-P** _password_</span></span>  
 <span data-ttu-id="4b136-298">指定登录 ID 的密码。</span><span class="sxs-lookup"><span data-stu-id="4b136-298">Specifies the password for the login ID.</span></span> <span data-ttu-id="4b136-299">如果未使用此选项， **bcp** 命令将提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="4b136-299">If this option is not used, the **bcp** command prompts for a password.</span></span> <span data-ttu-id="4b136-300">如果在命令提示符的末尾使用此选项，但不提供密码，则 **bcp** 将使用默认密码 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="4b136-300">If this option is used at the end of the command prompt without a password, **bcp** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="4b136-301">若要屏蔽密码，请不要指定 **-P** 选项和 **-U** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-301">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="4b136-302">而应在指定 **bcp** 以及 **-U** 选项和其他开关（不指定 **-P**）之后按 Enter，这时命令会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="4b136-302">Instead, after specifying **bcp** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and the command will prompt you for a password.</span></span> <span data-ttu-id="4b136-303">这种方法可以确保输入密码时对其屏蔽。</span><span class="sxs-lookup"><span data-stu-id="4b136-303">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="4b136-304">如果 password 以连字符 (-) 或正斜杠 (/) 开头，则不要在 **-P** 与 password 值之间添加空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-304">If *password* begins with a hyphen (-) or a forward slash (/), do not add a space between **-P** and the *password* value.</span></span>  
  
 `-q`  
 <span data-ttu-id="4b136-305">在 **bcp** 实用工具和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例之间的连接中，执行 SET QUOTED_IDENTIFIERS ON 语句。</span><span class="sxs-lookup"><span data-stu-id="4b136-305">Executes the SET QUOTED_IDENTIFIERS ON statement in the connection between the **bcp** utility and an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4b136-306">使用此选项可以指定包含空格或单引号的数据库、所有者、表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-306">Use this option to specify a database, owner, table, or view name that contains a space or a single quotation mark.</span></span> <span data-ttu-id="4b136-307">将由三部分组成的整个表名或视图名用英文双引号 ("") 引起来。</span><span class="sxs-lookup"><span data-stu-id="4b136-307">Enclose the entire three-part table or view name in quotation marks ("").</span></span>  
  
 <span data-ttu-id="4b136-308">必须使用 -q 选项，才能指定包含空格或单引号的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="4b136-308">To specify a database name that contains a space or single quotation mark, you must use the **-q** option.</span></span>  
  
 <span data-ttu-id="4b136-309">`-q` 不适用于传递到 `-d` 的值。</span><span class="sxs-lookup"><span data-stu-id="4b136-309">`-q` does not apply to values passed to `-d`.</span></span>  
  
 <span data-ttu-id="4b136-310">有关详细信息，请参阅本主题后面的“备注”。</span><span class="sxs-lookup"><span data-stu-id="4b136-310">For more information, see Remarks, later in this topic.</span></span>  
  
 <span data-ttu-id="4b136-311">**-r** _row_term_</span><span class="sxs-lookup"><span data-stu-id="4b136-311">**-r** _row_term_</span></span>  
 <span data-ttu-id="4b136-312">指定行终止符。</span><span class="sxs-lookup"><span data-stu-id="4b136-312">Specifies the row terminator.</span></span> <span data-ttu-id="4b136-313">默认的行终止符是 **\n** （换行符）。</span><span class="sxs-lookup"><span data-stu-id="4b136-313">The default is **\n** (newline character).</span></span> <span data-ttu-id="4b136-314">使用此参数可替代默认行终止符。</span><span class="sxs-lookup"><span data-stu-id="4b136-314">Use this parameter to override the default row terminator.</span></span> <span data-ttu-id="4b136-315">有关详细信息，请参阅 [指定字段终止符和行终止符 (SQL Server)](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-315">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-316">如果您在 bcp.exe 命令中以十六进制表示法指定行终止符，则该值将在 0x00 处截断。</span><span class="sxs-lookup"><span data-stu-id="4b136-316">If you specify the row terminator in hexadecimal notation in a bcp.exe command, the value will be truncated at 0x00.</span></span> <span data-ttu-id="4b136-317">例如，如果您指定 0x410041，则将使用 0x41。</span><span class="sxs-lookup"><span data-stu-id="4b136-317">For example, if you specify 0x410041, 0x41 will be used.</span></span>  
  
 <span data-ttu-id="4b136-318">如果 *row_term* 以连字符 (-) 或正斜杠 (/) 开头，则不要在 **-r** 与 *row_term* 值之间包含空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-318">If *row_term* begins with a hyphen (-) or a forward slash (/), do not include a space between **-r** and the *row_term* value.</span></span>  
  
 <span data-ttu-id="4b136-319">**-R**</span><span class="sxs-lookup"><span data-stu-id="4b136-319">**-R**</span></span>  
 <span data-ttu-id="4b136-320">指定使用客户端计算机区域设置中定义的区域格式，将货币、日期和时间数据大容量复制到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="4b136-320">Specifies that currency, date, and time data is bulk copied into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the regional format defined for the locale setting of the client computer.</span></span> <span data-ttu-id="4b136-321">默认情况下，将忽略区域设置。</span><span class="sxs-lookup"><span data-stu-id="4b136-321">By default, regional settings are ignored.</span></span>  
  
 <span data-ttu-id="4b136-322">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="4b136-322">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="4b136-323">指定要连接的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4b136-323">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="4b136-324">如果未指定服务器，则 **bcp** 实用工具将连接到本地计算机上的默认 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4b136-324">If no server is specified, the **bcp** utility connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="4b136-325">如果从网络或本地命名实例上的远程计算机中运行 **bcp** 命令，则必须使用此选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-325">This option is required when a **bcp** command is run from a remote computer on the network or a local named instance.</span></span> <span data-ttu-id="4b136-326">若要连接到服务器上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 默认实例，请仅指定 *server_name*。</span><span class="sxs-lookup"><span data-stu-id="4b136-326">To connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on a server, specify only *server_name*.</span></span> <span data-ttu-id="4b136-327">若要连接到的命名实例 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请*指定 **_\\_** server_name instance_name*。</span><span class="sxs-lookup"><span data-stu-id="4b136-327">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify *server_name\*\*_\\_*\* instance_name\*.</span></span>  
  
 <span data-ttu-id="4b136-328">`-t`*field_term*</span><span class="sxs-lookup"><span data-stu-id="4b136-328">`-t` *field_term*</span></span>  
 <span data-ttu-id="4b136-329">指定字段终止符。</span><span class="sxs-lookup"><span data-stu-id="4b136-329">Specifies the field terminator.</span></span> <span data-ttu-id="4b136-330">默认的字段终止符是 **\t** （制表符）。</span><span class="sxs-lookup"><span data-stu-id="4b136-330">The default is **\t** (tab character).</span></span> <span data-ttu-id="4b136-331">使用此参数可以替代默认字段终止符。</span><span class="sxs-lookup"><span data-stu-id="4b136-331">Use this parameter to override the default field terminator.</span></span> <span data-ttu-id="4b136-332">有关详细信息，请参阅 [指定字段终止符和行终止符 (SQL Server)](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-332">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-333">如果您在 bcp.exe 命令中以十六进制表示法指定字段终止符，则该值将在 0x00 处截断。</span><span class="sxs-lookup"><span data-stu-id="4b136-333">If you specify the field terminator in hexadecimal notation in a bcp.exe command, the value will be truncated at 0x00.</span></span> <span data-ttu-id="4b136-334">例如，如果您指定 0x410041，则将使用 0x41。</span><span class="sxs-lookup"><span data-stu-id="4b136-334">For example, if you specify 0x410041, 0x41 will be used.</span></span>  
  
 <span data-ttu-id="4b136-335">如果*field_term*以连字符开头 (-) 或正斜杠 (/) ，则不要在 `-t` 和*field_term*值之间包含空格。</span><span class="sxs-lookup"><span data-stu-id="4b136-335">If *field_term* begins with a hyphen (-) or a forward slash (/), do not include a space between `-t` and the *field_term* value.</span></span>  
  
 <span data-ttu-id="4b136-336">**-T**</span><span class="sxs-lookup"><span data-stu-id="4b136-336">**-T**</span></span>  
 <span data-ttu-id="4b136-337">指定 **bcp** 实用工具通过使用集成安全性的受信任连接连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b136-337">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="4b136-338">不需要网络用户的安全凭据 login_id 和 password。</span><span class="sxs-lookup"><span data-stu-id="4b136-338">The security credentials of the network user, *login_id*, and *password* are not required.</span></span> <span data-ttu-id="4b136-339">如果未指定 **-T** ，则需要指定 **-U** 和 **-P** 才能成功登录。</span><span class="sxs-lookup"><span data-stu-id="4b136-339">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>  
  
 <span data-ttu-id="4b136-340">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="4b136-340">**-U** _login_id_</span></span>  
 <span data-ttu-id="4b136-341">指定用于连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的登录 ID。</span><span class="sxs-lookup"><span data-stu-id="4b136-341">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b136-342">如果 **bcp** 实用工具通过使用集成安全性的可信连接连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，则使用的是 **-T** 选项（可信连接），而不是用户名和密码的组合。 </span><span class="sxs-lookup"><span data-stu-id="4b136-342">When the **bcp** utility is connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a trusted connection using integrated security, use the **-T** option (trusted connection) instead of the *user name* and *password* combination.</span></span>  
  
 <span data-ttu-id="4b136-343">**-v**</span><span class="sxs-lookup"><span data-stu-id="4b136-343">**-v**</span></span>  
 <span data-ttu-id="4b136-344">报告 **bcp** 实用工具的版本号和版权信息。</span><span class="sxs-lookup"><span data-stu-id="4b136-344">Reports the **bcp** utility version number and copyright.</span></span>  
  
 <span data-ttu-id="4b136-345">**-V** (**80** | **90** | **100**| **110**)</span><span class="sxs-lookup"><span data-stu-id="4b136-345">**-V** (**80** | **90** | **100**| **110**)</span></span>  
 <span data-ttu-id="4b136-346">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]早期版本中的数据类型执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="4b136-346">Performs the bulk-copy operation using data types from an earlier version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4b136-347">此选项并不提示输入每个字段，它将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="4b136-347">This option does not prompt for each field; it uses the default values.</span></span>  
  
 <span data-ttu-id="4b136-348">**80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b136-348">**80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]</span></span>  
  
 <span data-ttu-id="4b136-349">**90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b136-349">**90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]</span></span>  
  
 <span data-ttu-id="4b136-350">**100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 和 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b136-350">**100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]</span></span>  
  
 <span data-ttu-id="4b136-351">**110 =[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="4b136-351">**110 = [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**</span></span>  
  
 <span data-ttu-id="4b136-352">例如，若要为 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]不支持、但是在较高版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中引入的类型生成数据，请使用 -V80 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-352">For example, to generate data for types not supported by [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], but were introduced in later versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use the -V80 option.</span></span>  
  
 <span data-ttu-id="4b136-353">有关详细信息，请参阅 [导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-353">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 `-w`  
 <span data-ttu-id="4b136-354">使用 Unicode 字符执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="4b136-354">Performs the bulk copy operation using Unicode characters.</span></span> <span data-ttu-id="4b136-355">此选项不提示输入每个字段;它使用 `nchar` 作为存储类型，没有前缀， **\t** (制表符) 作为字段分隔符， **\n** (换行符) 作为行终止符。</span><span class="sxs-lookup"><span data-stu-id="4b136-355">This option does not prompt for each field; it uses `nchar` as the storage type, no prefixes, **\t** (tab character) as the field separator, and **\n** (newline character) as the row terminator.</span></span> <span data-ttu-id="4b136-356">`-w` 与 `-c` 不兼容。</span><span class="sxs-lookup"><span data-stu-id="4b136-356">`-w` is not compatible with `-c`.</span></span>  
  
 <span data-ttu-id="4b136-357">有关详细信息，请参阅 [使用 Unicode 字符格式导入或导出数据 (SQL Server)](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-357">For more information, see [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-358">**-x**</span><span class="sxs-lookup"><span data-stu-id="4b136-358">**-x**</span></span>  
 <span data-ttu-id="4b136-359">结合使用该格式\*\*\*\* 和 -f\*\*\*\* format_file__ 选项，可生成基于 XML 的格式化文件，而不是默认的非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-359">Used with the **format** and **-f**_format_file_ options, generates an XML-based format file instead of the default non-XML format file.</span></span> <span data-ttu-id="4b136-360">在导入或导出数据时， **-x** 不起作用。</span><span class="sxs-lookup"><span data-stu-id="4b136-360">The **-x** does not work when importing or exporting data.</span></span> <span data-ttu-id="4b136-361">如果不与格式\*\*\*\* 和 -f\*\*\*\* format_file__ 一起使用，则将生成错误。</span><span class="sxs-lookup"><span data-stu-id="4b136-361">It generates an error if used without both **format** and **-f**_format_file_.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b136-362">备注</span><span class="sxs-lookup"><span data-stu-id="4b136-362">Remarks</span></span>  
 <span data-ttu-id="4b136-363">安装工具时，将安装**bcp** 12.0 客户端 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b136-363">The **bcp** 12.0 client is installed when you install [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] tools.</span></span> <span data-ttu-id="4b136-364">如果同时安装了 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 和早期版本 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的工具，使用的可能是早期版本的 **bcp** 客户端，而不是 **bcp** 12.0 客户端，具体情况取决于 PATH 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="4b136-364">If tools are installed for both [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] and an earlier version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], depending on the value of the PATH environment variable, you might be using the earlier **bcp** client instead of the **bcp** 12.0 client.</span></span> <span data-ttu-id="4b136-365">此环境变量定义 Windows 用于搜索可执行文件的目录集。</span><span class="sxs-lookup"><span data-stu-id="4b136-365">This environment variable defines the set of directories used by Windows to search for executable files.</span></span> <span data-ttu-id="4b136-366">若要确定当前所使用的版本，请在 Windows 命令提示符下运行 **bcp /v** 命令。</span><span class="sxs-lookup"><span data-stu-id="4b136-366">To discover which version you are using, run the **bcp /v** command at the Windows Command Prompt.</span></span> <span data-ttu-id="4b136-367">有关如何在 PATH 环境变量中设置命令路径的信息，请参阅 Windows 帮助。</span><span class="sxs-lookup"><span data-stu-id="4b136-367">For information about how to set the command path in the PATH environment variable, see Windows Help.</span></span>  
  
 <span data-ttu-id="4b136-368">只有当 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 工具和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 一起安装后，才支持 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-368">XML format files are only supported when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="4b136-369">有关在何处查找或如何运行 **bcp** 实用工具的信息以及有关命令提示实用工具语法约定的信息，请参阅[《Command Prompt Utility Reference &#40;Database Engine&#41;》](../tools/command-prompt-utility-reference-database-engine.md)（命令提示实用工具参考（数据库引擎））。</span><span class="sxs-lookup"><span data-stu-id="4b136-369">For information about where to find or how to run the **bcp** utility and about the command prompt utilities syntax conventions, see [Command Prompt Utility Reference &#40;Database Engine&#41;](../tools/command-prompt-utility-reference-database-engine.md).</span></span>  
  
 <span data-ttu-id="4b136-370">有关准备数据以进行批量导入或导出操作的信息，请参阅 [准备用于批量导出或导入的数据 (SQL Server)](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)知识。</span><span class="sxs-lookup"><span data-stu-id="4b136-370">For information on preparing data for bulk import or export operations, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b136-371">有关何时在事务日志中记录由批量导入执行的行插入操作的信息，请参阅 [《Prerequisites for Minimal Logging in Bulk Import》](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)（批量导入的最小日志记录的先决条件）。</span><span class="sxs-lookup"><span data-stu-id="4b136-371">For information about when row-insert operations that are performed by bulk import are logged in the transaction log, see [Prerequisites for Minimal Logging in Bulk Import](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="native-data-file-support"></a><span data-ttu-id="4b136-372">本机数据文件支持</span><span class="sxs-lookup"><span data-stu-id="4b136-372">Native Data File Support</span></span>  
 <span data-ttu-id="4b136-373">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]中， **bcp** 实用工具支持与 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]和 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]兼容的本机数据文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-373">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], the **bcp** utility supports native data files compatible with [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="computed-columns-and-timestamp-columns"></a><span data-ttu-id="4b136-374">计算列和 timestamp 列</span><span class="sxs-lookup"><span data-stu-id="4b136-374">Computed Columns and timestamp Columns</span></span>  
 <span data-ttu-id="4b136-375">为计算列或 `timestamp` 列导入的数据文件中的值将被忽略，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将自动分配值。</span><span class="sxs-lookup"><span data-stu-id="4b136-375">Values in the data file being imported for computed or `timestamp` columns are ignored, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns values.</span></span> <span data-ttu-id="4b136-376">如果数据文件不包含表中的计算列或 `timestamp` 列的值，则可使用格式化文件指定应在导入数据时忽略表中的计算列或 `timestamp` 列；[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将自动为列分配值。</span><span class="sxs-lookup"><span data-stu-id="4b136-376">If the data file does not contain values for the computed or `timestamp` columns in the table, use a format file to specify that the computed or `timestamp` columns in the table should be skipped when importing data; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns values for the column.</span></span>  
  
 <span data-ttu-id="4b136-377">计算列和 `timestamp` 列会照常从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 大容量复制到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="4b136-377">Computed and `timestamp` columns are bulk copied from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to a data file as usual.</span></span>  
  
## <a name="specifying-identifiers-that-contain-spaces-or-quotation-marks"></a><span data-ttu-id="4b136-378">指定包含空格或引号的标识符</span><span class="sxs-lookup"><span data-stu-id="4b136-378">Specifying Identifiers That Contain Spaces or Quotation Marks</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="4b136-379">标识符可以包含嵌入的空格和引号等字符。</span><span class="sxs-lookup"><span data-stu-id="4b136-379">identifiers can include characters such as embedded spaces and quotation marks.</span></span> <span data-ttu-id="4b136-380">此类标识符必须按以下方式处理：</span><span class="sxs-lookup"><span data-stu-id="4b136-380">Such identifiers must be treated as follows:</span></span>  
  
-   <span data-ttu-id="4b136-381">如果在命令指示符处指定的标识符或文件名包含空格或引号，则需用英文双引号 ("") 将该标识符引起来。</span><span class="sxs-lookup"><span data-stu-id="4b136-381">When you specify an identifier or file name that includes a space or quotation mark at the command prompt, enclose the identifier in quotation marks ("").</span></span>  
  
     <span data-ttu-id="4b136-382">例如，下面的 `bcp out` 命令创建了一个名为 `Currency Types.dat`的数据文件：</span><span class="sxs-lookup"><span data-stu-id="4b136-382">For example, the following `bcp out` command creates a data file named `Currency Types.dat`:</span></span>  
  
    ```  
    bcp AdventureWorks2012.Sales.Currency out "Currency Types.dat" -T -c  
    ```  
  
-   <span data-ttu-id="4b136-383">若要指定包含空格或引号的数据库名称，必须使用 `-q` 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-383">To specify a database name that contains a space or quotation mark, you must use the `-q` option.</span></span>  
  
-   <span data-ttu-id="4b136-384">对于包含嵌入空格或引号的所有者、表或视图的名称，可以执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="4b136-384">For owner, table, or view names that contain embedded spaces or quotation marks, you can either:</span></span>  
  
    -   <span data-ttu-id="4b136-385">指定 `-q` 选项，或者</span><span class="sxs-lookup"><span data-stu-id="4b136-385">Specify the `-q` option, or</span></span>  
  
    -   <span data-ttu-id="4b136-386">将所有者、表或视图的名称括在方括号 ([]) 中，并用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="4b136-386">Enclose the owner, table, or view name in brackets ([]) inside the quotation marks.</span></span>  
  
## <a name="data-validation"></a><span data-ttu-id="4b136-387">数据验证</span><span class="sxs-lookup"><span data-stu-id="4b136-387">Data Validation</span></span>  
 <span data-ttu-id="4b136-388">**bcp** 现在会强制执行数据验证和数据检查，这样，在对数据文件中的无效数据执行脚本时，可能会导致脚本失败。</span><span class="sxs-lookup"><span data-stu-id="4b136-388">**bcp** now enforces data validation and data checks that might cause scripts to fail if they are executed on invalid data in a data file.</span></span> <span data-ttu-id="4b136-389">例如， **bcp** 现在可以验证：</span><span class="sxs-lookup"><span data-stu-id="4b136-389">For example, **bcp** now verifies that:</span></span>  
  
-   <span data-ttu-id="4b136-390">`float` 或 `real` 数据类型的本机表示形式是否有效。</span><span class="sxs-lookup"><span data-stu-id="4b136-390">The native representation of `float` or `real` data types are valid.</span></span>  
  
-   <span data-ttu-id="4b136-391">Unicode 数据的字节数是否为偶数。</span><span class="sxs-lookup"><span data-stu-id="4b136-391">Unicode data has an even-byte length.</span></span>  
  
 <span data-ttu-id="4b136-392">可以在早期版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中批量导入的无效数据类型现在可能无法加载。在早期版本中，仅当客户端尝试访问无效数据时才出现失败。</span><span class="sxs-lookup"><span data-stu-id="4b136-392">Forms of invalid data that could be bulk imported in earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might fail to load now; whereas, in earlier versions, the failure did not occur until a client tried to access the invalid data.</span></span> <span data-ttu-id="4b136-393">在大容量加载后查询数据时，添加的验证可最大限度地减少警告。</span><span class="sxs-lookup"><span data-stu-id="4b136-393">The added validation minimizes surprises when querying the data after bulk load.</span></span>  
  
## <a name="bulk-exporting-or-importing-sqlxml-documents"></a><span data-ttu-id="4b136-394">批量导出或导入 SQLXML 文档</span><span class="sxs-lookup"><span data-stu-id="4b136-394">Bulk Exporting or Importing SQLXML Documents</span></span>  
 <span data-ttu-id="4b136-395">若要批量导出或导入 SQLXML 数据，请在格式化文件中使用下列数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="4b136-395">To bulk export or import SQLXML data, use one of the following data types in your format file.</span></span>  
  
|<span data-ttu-id="4b136-396">数据类型</span><span class="sxs-lookup"><span data-stu-id="4b136-396">Data type</span></span>|<span data-ttu-id="4b136-397">效果</span><span class="sxs-lookup"><span data-stu-id="4b136-397">Effect</span></span>|  
|---------------|------------|  
|<span data-ttu-id="4b136-398">SQLCHAR 或 SQLVARYCHAR</span><span class="sxs-lookup"><span data-stu-id="4b136-398">SQLCHAR or SQLVARYCHAR</span></span>|<span data-ttu-id="4b136-399">在客户端代码页或排序规则隐含的代码页中发送数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-399">The data is sent in the client code page or in the code page implied by the collation).</span></span> <span data-ttu-id="4b136-400">与在不指定格式化文件的情况下指定 `-c` 开关具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="4b136-400">The effect is the same as specifying the `-c` switch without specifying a format file.</span></span>|  
|<span data-ttu-id="4b136-401">SQLNCHAR 或 SQLNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="4b136-401">SQLNCHAR or SQLNVARCHAR</span></span>|<span data-ttu-id="4b136-402">以 Unicode 格式发送数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-402">The data is sent as Unicode.</span></span> <span data-ttu-id="4b136-403">与在不指定格式化文件的情况下指定 `-w` 开关具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="4b136-403">The effect is the same as specifying the `-w` switch without specifying a format file.</span></span>|  
|<span data-ttu-id="4b136-404">SQLBINARY 或 SQLVARYBIN</span><span class="sxs-lookup"><span data-stu-id="4b136-404">SQLBINARY or SQLVARYBIN</span></span>|<span data-ttu-id="4b136-405">不经任何转换即发送数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-405">The data is sent without any conversion.</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="4b136-406">权限</span><span class="sxs-lookup"><span data-stu-id="4b136-406">Permissions</span></span>  
 <span data-ttu-id="4b136-407">**bcpout** 操作要求对源表有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="4b136-407">A **bcpout** operation requires SELECT permission on the source table.</span></span>  
  
 <span data-ttu-id="4b136-408">**bcpin** 操作要求至少对目标表有 SELECT/INSERT 权限。</span><span class="sxs-lookup"><span data-stu-id="4b136-408">A **bcpin** operation minimally requires SELECT/INSERT permissions on the target table.</span></span> <span data-ttu-id="4b136-409">此外，如果下列任一条件成立，则要求拥有 ALTER TABLE 权限：</span><span class="sxs-lookup"><span data-stu-id="4b136-409">In addition, ALTER TABLE permission is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="4b136-410">存在约束，但没有指定 CHECK_CONSTRAINTS 提示。</span><span class="sxs-lookup"><span data-stu-id="4b136-410">Constraints exist and the CHECK_CONSTRAINTS hint is not specified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b136-411">禁用约束是默认行为。</span><span class="sxs-lookup"><span data-stu-id="4b136-411">Disabling constraints is the default behavior.</span></span> <span data-ttu-id="4b136-412">若要显式启用约束，请使用 **-h** 选项和 CHECK_CONSTRAINTS 提示。</span><span class="sxs-lookup"><span data-stu-id="4b136-412">To enable constraints explicitly, use the **-h** option with the CHECK_CONSTRAINTS hint.</span></span>  
  
-   <span data-ttu-id="4b136-413">存在触发器，但没有指定 FIRE_TRIGGER 提示。</span><span class="sxs-lookup"><span data-stu-id="4b136-413">Triggers exist and the FIRE_TRIGGER hint is not specified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b136-414">默认情况下，不激发触发器。</span><span class="sxs-lookup"><span data-stu-id="4b136-414">By default, triggers are not fired.</span></span> <span data-ttu-id="4b136-415">若要显式激发触发器，请使用 **-h** 选项和 FIRE_TRIGGERS 提示。</span><span class="sxs-lookup"><span data-stu-id="4b136-415">To fire triggers explicitly, use the **-h** option with the FIRE_TRIGGERS hint.</span></span>  
  
-   <span data-ttu-id="4b136-416">可以使用 **-E** 选项从数据文件导入标识值。</span><span class="sxs-lookup"><span data-stu-id="4b136-416">You use the **-E** option to import identity values from a data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-417">要求对目标表具有 ALTER TABLE 权限是 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]的新要求。</span><span class="sxs-lookup"><span data-stu-id="4b136-417">Requiring ALTER TABLE permission on the target table was new in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="4b136-418">如果用户帐户不具有对目标表的 ALTER TABLE 权限，这项新要求有可能导致不强制使用触发器和约束检查的 **bcp** 脚本失败。</span><span class="sxs-lookup"><span data-stu-id="4b136-418">This new requirement might cause **bcp** scripts that do not enforce triggers and constraint checks to fail if the user account lacks ALTER table permissions for the target table.</span></span>  
  
## <a name="character-mode--c-and-native-mode--n-best-practices"></a><span data-ttu-id="4b136-419">字符模式 (-c) 和本机模式 (-n) 最佳做法</span><span class="sxs-lookup"><span data-stu-id="4b136-419">Character Mode (-c) and Native Mode (-n) Best Practices</span></span>  
 <span data-ttu-id="4b136-420">本节提供与字符模式 (-c) 和本机模式 (-n) 有关的一些建议。</span><span class="sxs-lookup"><span data-stu-id="4b136-420">This section has recommendations for to character mode (-c) and native mode (-n).</span></span>  
  
-   <span data-ttu-id="4b136-421">（管理员/用户）应尽可能使用本机格式 (-n) 以避免分隔符问题。</span><span class="sxs-lookup"><span data-stu-id="4b136-421">(Administrator/User) When possible, use native format (-n) to avoid the separator issue.</span></span> <span data-ttu-id="4b136-422">使用本机格式可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]进行导出和导入。</span><span class="sxs-lookup"><span data-stu-id="4b136-422">Use the native format to export and import using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4b136-423">如果数据将导入到非 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库，则使用 -c 或 -w 选项从[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导出数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-423">Export data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the -c or -w option if the data will be imported to a non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
-   <span data-ttu-id="4b136-424">（管理员）在使用 BCP OUT 时验证数据。</span><span class="sxs-lookup"><span data-stu-id="4b136-424">(Administrator) Verify data when using BCP OUT.</span></span> <span data-ttu-id="4b136-425">例如，在您使用 BCP OUT、BCP IN，然后又使用 BCP OUT 时，请验证数据正确导出，并且终止符值未用作某个数据值的一部分。</span><span class="sxs-lookup"><span data-stu-id="4b136-425">For example, when you use BCP OUT, BCP IN, and then BCP OUT verify that the data is properly exported and the terminator values are not used as part of some data value.</span></span> <span data-ttu-id="4b136-426">请考虑使用随机的十六进制值覆盖默认的终止符（使用 -t 和 -r 选项），以便避免终止符值和数据值之间的冲突。</span><span class="sxs-lookup"><span data-stu-id="4b136-426">Please consider overriding the default terminators (using -t and -r options) with random hexadecimal values to avoid conflicts between terminator values and data values.</span></span>  
  
-   <span data-ttu-id="4b136-427">（用户）使用长且唯一的终止符（任意字节或字符序列）可以最大程度减少与实际字符串值冲突的可能性。</span><span class="sxs-lookup"><span data-stu-id="4b136-427">(User) Use a long and unique terminator (any sequence of bytes or characters) to minimize the possibility of a conflict with the actual string value.</span></span> <span data-ttu-id="4b136-428">这可以通过使用 -t 和 -r 选项实现。</span><span class="sxs-lookup"><span data-stu-id="4b136-428">This can be done by using the -t and -r options.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4b136-429">示例</span><span class="sxs-lookup"><span data-stu-id="4b136-429">Examples</span></span>  
 <span data-ttu-id="4b136-430">本部分包含以下示例：</span><span class="sxs-lookup"><span data-stu-id="4b136-430">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="4b136-431">A.</span><span class="sxs-lookup"><span data-stu-id="4b136-431">A.</span></span> <span data-ttu-id="4b136-432">将表行复制到数据文件中（使用可信连接）</span><span class="sxs-lookup"><span data-stu-id="4b136-432">Copying table rows into a data file (with a trusted connection)</span></span>  
  
-   <span data-ttu-id="4b136-433">B.</span><span class="sxs-lookup"><span data-stu-id="4b136-433">B.</span></span> <span data-ttu-id="4b136-434">将表行复制到数据文件中（使用混合模式身份验证）</span><span class="sxs-lookup"><span data-stu-id="4b136-434">Copying table rows into a data file (with Mixed-mode Authentication)</span></span>  
  
-   <span data-ttu-id="4b136-435">C.</span><span class="sxs-lookup"><span data-stu-id="4b136-435">C.</span></span> <span data-ttu-id="4b136-436">将文件中的数据复制到表中</span><span class="sxs-lookup"><span data-stu-id="4b136-436">Copying data from a file to a table</span></span>  
  
-   <span data-ttu-id="4b136-437">D.</span><span class="sxs-lookup"><span data-stu-id="4b136-437">D.</span></span> <span data-ttu-id="4b136-438">将特定的列复制到数据文件中</span><span class="sxs-lookup"><span data-stu-id="4b136-438">Copying a specific column into a data file</span></span>  
  
-   <span data-ttu-id="4b136-439">E.</span><span class="sxs-lookup"><span data-stu-id="4b136-439">E.</span></span> <span data-ttu-id="4b136-440">将特定的行复制到数据文件中</span><span class="sxs-lookup"><span data-stu-id="4b136-440">Copying a specific row into a data file</span></span>  
  
-   <span data-ttu-id="4b136-441">F.</span><span class="sxs-lookup"><span data-stu-id="4b136-441">F.</span></span> <span data-ttu-id="4b136-442">将查询中的数据复制到数据文件中</span><span class="sxs-lookup"><span data-stu-id="4b136-442">Copying data from a query to a data file</span></span>  
  
-   <span data-ttu-id="4b136-443">G.</span><span class="sxs-lookup"><span data-stu-id="4b136-443">G.</span></span> <span data-ttu-id="4b136-444">创建非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4b136-444">Creating a non-XML format file</span></span>  
  
-   <span data-ttu-id="4b136-445">H.</span><span class="sxs-lookup"><span data-stu-id="4b136-445">H.</span></span> <span data-ttu-id="4b136-446">创建 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4b136-446">Creating an XML format file</span></span>  
  
-   <span data-ttu-id="4b136-447">I.</span><span class="sxs-lookup"><span data-stu-id="4b136-447">I.</span></span> <span data-ttu-id="4b136-448">使用格式化文件进行 **bcp**批量导入</span><span class="sxs-lookup"><span data-stu-id="4b136-448">Using a format file to bulk import with **bcp**</span></span>  
  
### <a name="a-copying-table-rows-into-a-data-file-with-a-trusted-connection"></a><span data-ttu-id="4b136-449">A.</span><span class="sxs-lookup"><span data-stu-id="4b136-449">A.</span></span> <span data-ttu-id="4b136-450">将表行复制到数据文件中（使用可信连接）</span><span class="sxs-lookup"><span data-stu-id="4b136-450">Copying table rows into a data file (with a trusted connection)</span></span>  
 <span data-ttu-id="4b136-451">以下示例阐释了 **表中的** out `AdventureWorks2012.Sales.Currency` 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-451">The following example illustrates the **out** option on the `AdventureWorks2012.Sales.Currency` table.</span></span> <span data-ttu-id="4b136-452">此示例创建一个名为 `Currency.dat` 的数据文件，并使用字符格式将表数据复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="4b136-452">This example creates a data file named `Currency.dat` and copies the table data into it using character format.</span></span> <span data-ttu-id="4b136-453">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-453">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-454">在命令提示符处输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b136-454">At a command prompt, enter the following command:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -T -c  
```  
  
### <a name="b-copying-table-rows-into-a-data-file-with-mixed-mode-authentication"></a><span data-ttu-id="4b136-455">B.</span><span class="sxs-lookup"><span data-stu-id="4b136-455">B.</span></span> <span data-ttu-id="4b136-456">将表行复制到数据文件中（使用混合模式身份验证）</span><span class="sxs-lookup"><span data-stu-id="4b136-456">Copying table rows into a data file (with mixed-mode authentication)</span></span>  
 <span data-ttu-id="4b136-457">以下示例阐释了 **表中的** out `AdventureWorks2012.Sales.Currency` 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-457">The following example illustrates the **out** option on the `AdventureWorks2012.Sales.Currency` table.</span></span> <span data-ttu-id="4b136-458">此示例创建一个名为 `Currency.dat` 的数据文件，并使用字符格式将表数据复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="4b136-458">This example creates a data file named `Currency.dat` and copies the table data into it using character format.</span></span>  
  
 <span data-ttu-id="4b136-459">该示例假定你使用混合模式身份验证，必须使用 **-U** 开关指定登录 ID。</span><span class="sxs-lookup"><span data-stu-id="4b136-459">The example assumes that you are using mixed-mode authentication, you must use the **-U** switch to specify your login ID.</span></span> <span data-ttu-id="4b136-460">并且，除非你连接到本地计算机上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的默认实例，否则请使用 **-S** 开关指定系统名称和实例名称（可选）。</span><span class="sxs-lookup"><span data-stu-id="4b136-460">Also, unless you are connecting to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer, use the **-S** switch to specify the system name and, optionally, an instance name.</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -c -U<login_id> -S<server_name\instance_name>  
```  
  
 <span data-ttu-id="4b136-461">系统将提示您输入密码。</span><span class="sxs-lookup"><span data-stu-id="4b136-461">The system will prompt you for your password.</span></span>  
  
### <a name="c-copying-data-from-a-file-to-a-table"></a><span data-ttu-id="4b136-462">C.</span><span class="sxs-lookup"><span data-stu-id="4b136-462">C.</span></span> <span data-ttu-id="4b136-463">将文件中的数据复制到表中</span><span class="sxs-lookup"><span data-stu-id="4b136-463">Copying data from a file to a table</span></span>  
 <span data-ttu-id="4b136-464">以下示例使用上一个示例中创建的文件 (`Currency.dat`) 来阐释 **in** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-464">The following example illustrates the **in** option by using the file created in the preceding example (`Currency.dat`).</span></span> <span data-ttu-id="4b136-465">但是，此示例将首先创建一个 `AdventureWorks2012 Sales.Currency` 表的空副本 `Sales.Currency2`，数据将被复制到该副本中。</span><span class="sxs-lookup"><span data-stu-id="4b136-465">First, however, this example creates an empty copy of the `AdventureWorks2012 Sales.Currency` table, `Sales.Currency2`, into which the data is copied.</span></span> <span data-ttu-id="4b136-466">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-466">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-467">若要创建空表，可在查询编辑器中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b136-467">To create the empty table, in Query Editor, enter the following command:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO AdventureWorks2012.Sales.Currency2   
FROM AdventureWorks2012.Sales.Currency WHERE 1=2;  
```  
  
 <span data-ttu-id="4b136-468">若要将字符数据大容量复制到新表中（即导入数据），可在命令提示符处输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b136-468">To bulk copy the character data into the new table, that is to import the data, enter the following command at a command prompt:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -c  
```  
  
 <span data-ttu-id="4b136-469">若要验证命令是否成功，并在查询编辑器中显示表的内容，请输入：</span><span class="sxs-lookup"><span data-stu-id="4b136-469">To verify that the command succeeded, display the contents of the table in Query Editor, and enter:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM Sales.Currency2  
```  
  
### <a name="d-copying-a-specific-column-into-a-data-file"></a><span data-ttu-id="4b136-470">D.</span><span class="sxs-lookup"><span data-stu-id="4b136-470">D.</span></span> <span data-ttu-id="4b136-471">将特定的列复制到数据文件中</span><span class="sxs-lookup"><span data-stu-id="4b136-471">Copying a specific column into a data file</span></span>  
 <span data-ttu-id="4b136-472">若要复制特定列，可以使用 **queryout** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-472">To copy a specific column, you can use the **queryout** option.</span></span> <span data-ttu-id="4b136-473">下面的示例仅将 `Name` 表中的 `Sales.Currency` 列复制到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="4b136-473">The following example copies only the `Name` column of the `Sales.Currency` table into a data file.</span></span> <span data-ttu-id="4b136-474">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-474">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-475">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="4b136-475">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT Name FROM AdventureWorks.Sales.Currency" queryout Currency.Name.dat -T -c  
```  
  
### <a name="e-copying-a-specific-row-into-a-data-file"></a><span data-ttu-id="4b136-476">E.</span><span class="sxs-lookup"><span data-stu-id="4b136-476">E.</span></span> <span data-ttu-id="4b136-477">将特定的行复制到数据文件中</span><span class="sxs-lookup"><span data-stu-id="4b136-477">Copying a specific row into a data file</span></span>  
 <span data-ttu-id="4b136-478">若要复制特定行，可以使用 **queryout** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-478">To copy a specific row, you can use the **queryout** option.</span></span> <span data-ttu-id="4b136-479">下面的示例仅将名为 `Jarrod Rana` 的联系人的行从表 `AdventureWorks2012.Person.Person` 复制到数据文件 (`Jarrod Rana.dat`) 中。该示例假定你使用的是 Windows 身份验证，并且与运行 **bcp** 命令的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-479">The following example copies only the row for the contact named `Jarrod Rana` from the `AdventureWorks2012.Person.Person` table into a data file (`Jarrod Rana.dat`).The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-480">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="4b136-480">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT * FROM AdventureWorks2012.Person.Person WHERE FirstName='Jarrod' AND LastName='Rana' "  queryout "Jarrod Rana.dat" -T -c  
```  
  
### <a name="f-copying-data-from-a-query-to-a-data-file"></a><span data-ttu-id="4b136-481">F.</span><span class="sxs-lookup"><span data-stu-id="4b136-481">F.</span></span> <span data-ttu-id="4b136-482">将查询中的数据复制到数据文件中</span><span class="sxs-lookup"><span data-stu-id="4b136-482">Copying data from a query to a data file</span></span>  
 <span data-ttu-id="4b136-483">若要将 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句的结果集复制到数据文件中，请使用 **queryout** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-483">To copy the result set from a [!INCLUDE[tsql](../includes/tsql-md.md)] statement to a data file, use the **queryout** option.</span></span> <span data-ttu-id="4b136-484">下面的示例将 `AdventureWorks2012.Person.Person` 表中的姓名复制到 `Contacts.txt` 数据文件中；这些姓名先按姓排序，再按名排序。</span><span class="sxs-lookup"><span data-stu-id="4b136-484">The following example copies the names from the `AdventureWorks2012.Person.Person` table, ordered by last name then first name, into the `Contacts.txt` data file.</span></span> <span data-ttu-id="4b136-485">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-485">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-486">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="4b136-486">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT FirstName, LastName FROM AdventureWorks2012.Person.Person ORDER BY LastName, Firstname" queryout Contacts.txt -c -T  
```  
  
### <a name="g-creating-a-non-xml-format-file"></a><span data-ttu-id="4b136-487">G.</span><span class="sxs-lookup"><span data-stu-id="4b136-487">G.</span></span> <span data-ttu-id="4b136-488">创建非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4b136-488">Creating a non-XML format file</span></span>  
 <span data-ttu-id="4b136-489">下面的示例为 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中的 `Currency.fmt` 表创建一个非 XML 格式化文件 `Sales.Currency`。</span><span class="sxs-lookup"><span data-stu-id="4b136-489">The following example creates a non-XML format file, `Currency.fmt`, for the `Sales.Currency` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="4b136-490">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-490">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-491">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="4b136-491">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c  -f Currency.fmt  
```  
  
 <span data-ttu-id="4b136-492">有关详细信息，请参阅 [非 XML 格式化文件 (SQL Server)](../relational-databases/import-export/xml-format-files-sql-server.md)早期版本支持的原始格式。</span><span class="sxs-lookup"><span data-stu-id="4b136-492">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).</span></span>  
  
### <a name="h-creating-an-xml-format-file"></a><span data-ttu-id="4b136-493">H.</span><span class="sxs-lookup"><span data-stu-id="4b136-493">H.</span></span> <span data-ttu-id="4b136-494">创建 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4b136-494">Creating an XML format file</span></span>  
 <span data-ttu-id="4b136-495">下面的示例为 `Currency.xml` 数据库中的 `Sales.Currency` 表创建一个名为 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 的 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-495">The following example creates an XML format file named `Currency.xml` for the `Sales.Currency` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="4b136-496">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-496">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-497">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="4b136-497">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c -x -f Currency.xml  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-498">若要使用 **-x** 开关，则必须使用 **bcp** 9.0 客户端。</span><span class="sxs-lookup"><span data-stu-id="4b136-498">To use the **-x** switch, you must be using a **bcp** 9.0 client.</span></span> <span data-ttu-id="4b136-499">有关如何使用**bcp** 9.0 客户端的信息，请参阅 "备注"。</span><span class="sxs-lookup"><span data-stu-id="4b136-499">For information about how to use the **bcp** 9.0 client, see "Remarks."</span></span>  
  
 <span data-ttu-id="4b136-500">有关详细信息，请参阅 [XML 格式化文件 (SQL Server)](../relational-databases/import-export/xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-500">For more information, see [XML Format Files &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).</span></span>  
  
### <a name="i-using-a-format-file-to-bulk-import-with-bcp"></a><span data-ttu-id="4b136-501">I.</span><span class="sxs-lookup"><span data-stu-id="4b136-501">I.</span></span> <span data-ttu-id="4b136-502">使用格式化文件进行 bcp 批量导入</span><span class="sxs-lookup"><span data-stu-id="4b136-502">Using a format file to bulk import with bcp</span></span>  
 <span data-ttu-id="4b136-503">向 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例中导入数据时，若要使用以前创建的格式化文件，请同时使用 **-f** 开关和 **in** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b136-503">To use a previously created format file when importing data into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use the **-f** switch with the **in** option.</span></span> <span data-ttu-id="4b136-504">例如，以下命令通过使用以前创建的格式化文件 (`Currency.dat`)，将数据文件 `Sales.Currency` 的内容大容量复制到 `Sales.Currency2` 表的副本 (`Currency.xml`) 中。</span><span class="sxs-lookup"><span data-stu-id="4b136-504">For example, the following command bulk copies the contents of a data file, `Currency.dat`, into a copy of the `Sales.Currency` table (`Sales.Currency2`) by using the previously created format file (`Currency.xml`).</span></span> <span data-ttu-id="4b136-505">该示例假定你使用 Windows 身份验证，并且与运行 **bcp** 命令所针对的服务器实例之间具有可信连接。</span><span class="sxs-lookup"><span data-stu-id="4b136-505">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="4b136-506">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="4b136-506">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -f Currency.xml  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4b136-507">如果数据文件字段和表中的列不同（例如，在编号、排序或数据类型方面），则可使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="4b136-507">Format files are useful when the data file fields are different from the table columns; for example, in their number, ordering, or data types.</span></span> <span data-ttu-id="4b136-508">有关详细信息，请参阅 [用来导入或导出数据的格式化文件 (SQL Server)](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b136-508">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="4b136-509">其他示例</span><span class="sxs-lookup"><span data-stu-id="4b136-509">Additional Examples</span></span>  
 <span data-ttu-id="4b136-510">以下主题包含有关使用**bcp**的示例：</span><span class="sxs-lookup"><span data-stu-id="4b136-510">The following topics contain examples of using **bcp**:</span></span>  
  
-   [<span data-ttu-id="4b136-511">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-511">Create a Format File &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="4b136-512">批量导入和导出 XML 文档的示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-512">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="4b136-513">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-513">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="4b136-514">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-514">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="4b136-515">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-515">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="4b136-516">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-516">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="4b136-517">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-517">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="4b136-518">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-518">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="4b136-519">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-519">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="4b136-520">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-520">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b136-521">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b136-521">See Also</span></span>  
 <span data-ttu-id="4b136-522">[准备用于大容量导出或导入的数据 &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4b136-522">[Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md) </span></span>  
 <span data-ttu-id="4b136-523">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b136-523">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="4b136-524">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b136-524">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="4b136-525">[将 QUOTED_IDENTIFIER 设置 &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b136-525">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="4b136-526">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b136-526">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="4b136-527">[sp_tableoption &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b136-527">[sp_tableoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql) </span></span>  
 [<span data-ttu-id="4b136-528">用来导入或导出数据的格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b136-528">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
