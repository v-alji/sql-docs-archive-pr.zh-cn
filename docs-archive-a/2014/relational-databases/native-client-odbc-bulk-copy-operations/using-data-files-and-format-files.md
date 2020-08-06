---
title: 使用数据文件和格式化文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e0ee92f79e2c8cab9605db0188e01898df8c23e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693852"
---
# <a name="using-data-files-and-format-files"></a><span data-ttu-id="80028-102">使用数据文件和格式化文件</span><span class="sxs-lookup"><span data-stu-id="80028-102">Using Data Files and Format Files</span></span>
  <span data-ttu-id="80028-103">最简单的大容量复制程序执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="80028-103">The simplest bulk copy program does the following:</span></span>  
  
1.  <span data-ttu-id="80028-104">调用[bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)指定大容量复制 (将 BCP_OUT 从表或视图) 设置为数据文件。</span><span class="sxs-lookup"><span data-stu-id="80028-104">Calls [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to specify bulk copying out (set BCP_OUT) from a table or view to a data file.</span></span>  
  
2.  <span data-ttu-id="80028-105">调用[bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="80028-105">Calls [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="80028-106">数据文件以本机模式创建；因此，来自表或视图中所有列的数据都采用与数据库中相同的格式存储于数据文件中。</span><span class="sxs-lookup"><span data-stu-id="80028-106">The data file is created in native mode; therefore, data from all columns in the table or view are stored in the data file in the same format as in the database.</span></span> <span data-ttu-id="80028-107">然后，通过使用与上述相同的步骤并设置 DB_IN（而非 DB_OUT），将该文件大容量复制到某一服务器中。</span><span class="sxs-lookup"><span data-stu-id="80028-107">The file can then be bulk copied into a server by using these same steps and setting DB_IN instead of DB_OUT.</span></span> <span data-ttu-id="80028-108">只有在源表和目标表都具有完全相同的结构时，这一功能才适用。</span><span class="sxs-lookup"><span data-stu-id="80028-108">This works only if both the source and target tables have exactly the same structure.</span></span> <span data-ttu-id="80028-109">生成的数据文件也可以通过使用 **/n** (本机模式) 开关输入到**bcp**实用工具中。</span><span class="sxs-lookup"><span data-stu-id="80028-109">The resulting data file can also be input to the **bcp** utility by using the **/n** (native mode) switch.</span></span>  
  
 <span data-ttu-id="80028-110">若要大容量复制出 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的结果集，而非直接从表或视图复制：</span><span class="sxs-lookup"><span data-stu-id="80028-110">To bulk copy out the result set of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement instead of directly from a table or view:</span></span>  
  
1.  <span data-ttu-id="80028-111">调用**bcp_init**以指定大容量复制，但为表名称指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="80028-111">Call **bcp_init** to specify bulk copying out, but specify NULL for the table name.</span></span>  
  
2.  <span data-ttu-id="80028-112">调用[bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)将*EOPTION*设置为 BCPHINTS，并将*IValue*设置为指向包含 transact-sql 语句的 SQLTCHAR 字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="80028-112">Call [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) with *eOption* set to BCPHINTS and *iValue* set to a pointer to a SQLTCHAR string containing the Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="80028-113">调用**bcp_exec**执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="80028-113">Call **bcp_exec** to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="80028-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句可以是生成某一结果集的任何语句。</span><span class="sxs-lookup"><span data-stu-id="80028-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be any statement that generates a result set.</span></span> <span data-ttu-id="80028-115">将创建包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的第一个结果集的数据文件。</span><span class="sxs-lookup"><span data-stu-id="80028-115">The data file is created containing the first result set of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="80028-116">如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句生成多个结果集，则大容量复制将忽略第一个结果集之后的所有结果集。</span><span class="sxs-lookup"><span data-stu-id="80028-116">Bulk copy ignores any result set after the first if the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple result sets.</span></span>  
  
 <span data-ttu-id="80028-117">若要创建一个数据文件，其中的列数据与表中的格式不同，请调用[bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)以指定将更改的列数，然后为要更改其格式的每个列调用[bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) 。</span><span class="sxs-lookup"><span data-stu-id="80028-117">To create a data file in which column data is stored in a different format than in the table, call [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to specify how many columns will be changed, then call [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column whose format you want to change.</span></span> <span data-ttu-id="80028-118">这是在调用**bcp_init**之后、调用**bcp_exec**之前完成的。</span><span class="sxs-lookup"><span data-stu-id="80028-118">This is done after calling **bcp_init** but before calling **bcp_exec**.</span></span> <span data-ttu-id="80028-119">**bcp_colfmt**指定列数据在数据文件中的存储格式。</span><span class="sxs-lookup"><span data-stu-id="80028-119">**bcp_colfmt** specifies the format in which the column's data is stored in the data file.</span></span> <span data-ttu-id="80028-120">当大容量复制时，可以使用此方法。你还可以使用**bcp_colfmt**来设置行终止符和列终止符。</span><span class="sxs-lookup"><span data-stu-id="80028-120">It can be used when bulk copying in or out. You can also use **bcp_colfmt** to set the row and column terminators.</span></span> <span data-ttu-id="80028-121">例如，如果您的数据中不包含制表符，则可以通过使用**bcp_colfmt**将制表符设置为每列的终止符来创建制表符分隔文件。</span><span class="sxs-lookup"><span data-stu-id="80028-121">For example, if your data contains no tab characters, you can create a tab-delimited file by using **bcp_colfmt** to set the tab character as the terminator for each column.</span></span>  
  
 <span data-ttu-id="80028-122">大容量复制和使用**bcp_colfmt**时，可以轻松地创建一个格式文件，用于描述你通过在上一次调用**bcp_colfmt**后调用[bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)创建的数据文件。</span><span class="sxs-lookup"><span data-stu-id="80028-122">When bulk copying out and using **bcp_colfmt**, you can easily create a format file describing the data file you have created by calling [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) after the last call to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="80028-123">从格式化文件描述的数据文件中大容量复制时，请通过在**bcp_init**之后调用[bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) ，然后在**bcp_exec**之前读取格式化文件。</span><span class="sxs-lookup"><span data-stu-id="80028-123">When bulk copying in from a data file described by a format file, read the format file by calling [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) after **bcp_init** but before **bcp_exec**.</span></span>  
  
 <span data-ttu-id="80028-124">**Bcp_control**函数在从数据文件大容量复制到时控制多个选项 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="80028-124">The **bcp_control** function controls several options when bulk copying into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file.</span></span> <span data-ttu-id="80028-125">**bcp_control**设置选项，如终止前的最大错误数、要开始大容量复制的文件中的行、要停止的行以及批大小。</span><span class="sxs-lookup"><span data-stu-id="80028-125">**bcp_control** sets options, such as the maximum number of errors before termination, the row in the file on which to start the bulk copy, the row to stop on, and the batch size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80028-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80028-126">See Also</span></span>  
 [<span data-ttu-id="80028-127">&#40;ODBC&#41;执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="80028-127">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
