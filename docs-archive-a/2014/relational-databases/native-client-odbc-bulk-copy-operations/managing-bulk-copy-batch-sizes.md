---
title: 管理大容量复制批大小 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f24ece176cbb834e4162f9e516ff23013fd256a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589048"
---
# <a name="managing-bulk-copy-batch-sizes"></a><span data-ttu-id="f43d1-102">管理大容量复制的批大小</span><span class="sxs-lookup"><span data-stu-id="f43d1-102">Managing Bulk Copy Batch Sizes</span></span>
  <span data-ttu-id="f43d1-103">在大容量复制操作中，批的主要目的在于定义事务的范围。</span><span class="sxs-lookup"><span data-stu-id="f43d1-103">The primary purpose of a batch in bulk copy operations is to define the scope of a transaction.</span></span> <span data-ttu-id="f43d1-104">如果没有设置批大小，则大容量复制函数会将整个大容量复制视为一个事务。</span><span class="sxs-lookup"><span data-stu-id="f43d1-104">If a batch size is not set, then bulk copy functions consider an entire bulk copy to be one transaction.</span></span> <span data-ttu-id="f43d1-105">如果设置了批大小，则每个批构成一个事务，当批运行完成时，该事务也就被提交。</span><span class="sxs-lookup"><span data-stu-id="f43d1-105">If a batch size is set, then each batch constitutes a transaction that is committed when the batch finishes.</span></span>  
  
 <span data-ttu-id="f43d1-106">如果在没有指定批大小的情况下执行大容量复制并且遇到错误，则将回滚整个大容量复制。</span><span class="sxs-lookup"><span data-stu-id="f43d1-106">If a bulk copy is performed with no batch size specified and an error is encountered, the entire bulk copy is rolled back.</span></span> <span data-ttu-id="f43d1-107">恢复长时间运行的大容量复制可能需要花费很长的时间。</span><span class="sxs-lookup"><span data-stu-id="f43d1-107">The recovery of a long-running bulk copy can take a long time.</span></span> <span data-ttu-id="f43d1-108">如果设置了批大小，则大容量复制将每个批视为一个事务并分别提交每个批。</span><span class="sxs-lookup"><span data-stu-id="f43d1-108">When a batch size is set, bulk copy considers each batch a transaction and commits each batch.</span></span> <span data-ttu-id="f43d1-109">如果遇到错误，只需回滚最后一个未完成的批。</span><span class="sxs-lookup"><span data-stu-id="f43d1-109">If an error is encountered, only the last outstanding batch needs to be rolled back.</span></span>  
  
 <span data-ttu-id="f43d1-110">此外，批大小还会影响锁定开销。</span><span class="sxs-lookup"><span data-stu-id="f43d1-110">The batch size can also affect locking overhead.</span></span> <span data-ttu-id="f43d1-111">对执行大容量复制时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，可以使用[BCP_CONTROL](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)指定 TABLOCK 提示，以获取表锁而不是行锁。</span><span class="sxs-lookup"><span data-stu-id="f43d1-111">When performing a bulk copy against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the TABLOCK hint can be specified using [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) to acquire a table lock instead of row locks.</span></span> <span data-ttu-id="f43d1-112">对于整个大容量复制操作而言，持有单个表锁的开销最小。</span><span class="sxs-lookup"><span data-stu-id="f43d1-112">The single table lock can be held with minimal overhead for an entire bulk copy operation.</span></span> <span data-ttu-id="f43d1-113">如果未指定 TABLOCK，则对各个行持有锁，并且在大容量复制操作期间维护所有锁的开销会导致性能降低。</span><span class="sxs-lookup"><span data-stu-id="f43d1-113">If TABLOCK is not specified then locks are held on individual rows and the overhead of maintaining all the locks for the duration of the bulk copy can slow performance.</span></span> <span data-ttu-id="f43d1-114">由于仅在事务执行期间才持有锁，因而可以通过指定批大小来解决此问题，因为这样可以定期生成能够释放当前持有的锁的提交。</span><span class="sxs-lookup"><span data-stu-id="f43d1-114">Because locks are only held for the length of a transaction, specifying a batch size addresses this problem by periodically generating a commit that frees the locks currently held.</span></span>  
  
 <span data-ttu-id="f43d1-115">如果要大容量复制大量的行，构成批的行的数目会对性能产生显著影响。</span><span class="sxs-lookup"><span data-stu-id="f43d1-115">The number of rows making up a batch can have significant performance effects when bulk copying a large number of rows.</span></span> <span data-ttu-id="f43d1-116">建议采用的批大小取决于要执行的大容量复制的类型。</span><span class="sxs-lookup"><span data-stu-id="f43d1-116">The recommendations for batch size depend on the type of bulk copy being performed.</span></span>  
  
-   <span data-ttu-id="f43d1-117">在对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进行大容量复制时，请指定 TABLOCK 大容量复制提示并设置一个较大的批大小。</span><span class="sxs-lookup"><span data-stu-id="f43d1-117">When bulk copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specify the TABLOCK bulk copy hint and set a large batch size.</span></span>  
  
-   <span data-ttu-id="f43d1-118">如果不指定 TABLOCK，请将批大小限制为小于 1,000 行。</span><span class="sxs-lookup"><span data-stu-id="f43d1-118">When TABLOCK is not specified, limit batch sizes to less than 1,000 rows.</span></span>  
  
 <span data-ttu-id="f43d1-119">从数据文件大容量复制时，在调用[bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)之前，通过使用 BCPBATCH 选项调用**bcp_control**来指定批大小。</span><span class="sxs-lookup"><span data-stu-id="f43d1-119">When bulk copying in from a data file, the batch size is specified by calling **bcp_control** with the BCPBATCH option before calling [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md).</span></span> <span data-ttu-id="f43d1-120">当使用[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)和[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)从程序变量大容量复制时，将在调用[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x*次后调用[bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)来控制批大小，其中*x*是批处理中的行数。</span><span class="sxs-lookup"><span data-stu-id="f43d1-120">When bulk copying from program variables using [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) and [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), the batch size is controlled by calling [bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) after calling [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* times, where *x* is the number of rows in a batch.</span></span>  
  
 <span data-ttu-id="f43d1-121">除了指定事务大小之外，批还会影响将行通过网络发送到服务器的时间。</span><span class="sxs-lookup"><span data-stu-id="f43d1-121">In addition to specifying the size of a transaction, batches also affect when rows are sent across the network to the server.</span></span> <span data-ttu-id="f43d1-122">大容量复制函数通常会缓存**bcp_sendrow**中的行，直到填充网络数据包，然后将完整数据包发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="f43d1-122">Bulk copy functions normally cache the rows from **bcp_sendrow** until a network packet is filled, and then send the full packet to the server.</span></span> <span data-ttu-id="f43d1-123">但是，当应用程序调用**bcp_batch**时，当前数据包将发送到服务器，而不考虑它是否已填充。</span><span class="sxs-lookup"><span data-stu-id="f43d1-123">When an application calls **bcp_batch**, however, the current packet is sent to the server regardless of whether it has been filled.</span></span> <span data-ttu-id="f43d1-124">使用很小的批大小可能导致向服务器发送许多部分填满的数据包，从而降低性能。</span><span class="sxs-lookup"><span data-stu-id="f43d1-124">Using a very low batch size can slow performance if it results in sending many partially filled packets to the server.</span></span> <span data-ttu-id="f43d1-125">例如，在每个**bcp_sendrow**之后调用**bcp_batch**会导致在单独的数据包中发送每个行，除非行很大，否则会浪费每个数据包中的空间。</span><span class="sxs-lookup"><span data-stu-id="f43d1-125">For example, calling **bcp_batch** after every **bcp_sendrow** causes each row to be sent in a separate packet and, unless the rows are very large, wastes space in each packet.</span></span> <span data-ttu-id="f43d1-126">SQL Server 的网络数据包的默认大小为 4 KB，但应用程序可以通过调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)来更改大小，该大小指定 SQL_ATTR_PACKET_SIZE 属性。</span><span class="sxs-lookup"><span data-stu-id="f43d1-126">The default size of network packets for SQL Server is 4 KB, although an application can change the size by calling [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) specifying the SQL_ATTR_PACKET_SIZE attribute.</span></span>  
  
 <span data-ttu-id="f43d1-127">批处理的另一个副作用是将每个批处理视为未完成的结果集，直到它完成**bcp_batch**。</span><span class="sxs-lookup"><span data-stu-id="f43d1-127">Another side effect of batches is that each batch is considered an outstanding result set until it is completed with **bcp_batch**.</span></span> <span data-ttu-id="f43d1-128">如果在批处理未完成的情况下尝试在连接句柄上执行任何其他操作， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序将发出错误，其中包含 SQLState = "HY000" 和错误消息字符串：</span><span class="sxs-lookup"><span data-stu-id="f43d1-128">If any other operations are attempted on a connection handle while a batch is outstanding, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver issues an error with SQLState = "HY000" and an error message string of:</span></span>  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a><span data-ttu-id="f43d1-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f43d1-129">See Also</span></span>  
 <span data-ttu-id="f43d1-130">[&#40;ODBC&#41;执行大容量复制操作](performing-bulk-copy-operations-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="f43d1-130">[Performing Bulk Copy Operations &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md) </span></span>  
 [<span data-ttu-id="f43d1-131">批量导入和导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f43d1-131">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
