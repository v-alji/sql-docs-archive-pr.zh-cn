---
title: 使用 Microsoft 分布式事务处理协调器 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: rothja
ms.author: jroth
ms.openlocfilehash: f7b7da33066a9f4edd01037738ed91155340e6ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581174"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a><span data-ttu-id="25b27-102">使用 Microsoft 分布式事务处理协调器 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="25b27-102">Use Microsoft Distributed Transaction Coordinator (ODBC)</span></span>
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a><span data-ttu-id="25b27-103">使用 MS DTC 更新两个或更多 SQL 服务器</span><span class="sxs-lookup"><span data-stu-id="25b27-103">To update two or more SQL Servers by using MS DTC</span></span>  
  
1.  <span data-ttu-id="25b27-104">使用 MS DTC OLE DtcGetTransactionManager 函数连接到 MS DTC。</span><span class="sxs-lookup"><span data-stu-id="25b27-104">Connect to MS DTC by using the MS DTC OLE DtcGetTransactionManager function.</span></span> <span data-ttu-id="25b27-105">有关 MS DTC 的信息，请参阅 Microsoft 分布式事务处理协调器。</span><span class="sxs-lookup"><span data-stu-id="25b27-105">For information about MS DTC, see Microsoft Distributed Transaction Coordinator.</span></span>  
  
2.  <span data-ttu-id="25b27-106">对要建立的每个 Microsoft SQL Server 连接调用 SQL DriverConnect 一次。</span><span class="sxs-lookup"><span data-stu-id="25b27-106">Call SQL DriverConnect once for each Microsoft SQL Server connection you want to establish.</span></span>  
  
3.  <span data-ttu-id="25b27-107">调用 MS DTC OLE ITransactionDispenser::BeginTransaction 函数以开始 MS DTC 事务，并获得代表事务的事务对象。</span><span class="sxs-lookup"><span data-stu-id="25b27-107">Call the MS DTC OLE ITransactionDispenser::BeginTransaction function to begin an MS DTC transaction and obtain a Transaction object that represents the transaction.</span></span>  
  
4.  <span data-ttu-id="25b27-108">对于要在 MS DTC 事务中登记的每个 ODBC 连接调用一次或多次 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)。</span><span class="sxs-lookup"><span data-stu-id="25b27-108">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) one or more times for each ODBC connection you want to enlist in the MS DTC transaction.</span></span> <span data-ttu-id="25b27-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 第二个参数必须是 SQL_ATTR_ENLIST_IN_DTC，并且第三个参数必须是在步骤 3 中获得的 Transaction 对象。</span><span class="sxs-lookup"><span data-stu-id="25b27-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) second parameter must be SQL_ATTR_ENLIST_IN_DTC and third parameter must be the Transaction object (obtained in Step 3).</span></span>  
  
5.  <span data-ttu-id="25b27-110">对于要更新的每个 SQL Server 调用一次 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)。</span><span class="sxs-lookup"><span data-stu-id="25b27-110">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) once for each SQL Server you want to update.</span></span>  
  
6.  <span data-ttu-id="25b27-111">调用 MS DTC OLE ITransaction::Commit 函数以提交 MS DTC 事务。</span><span class="sxs-lookup"><span data-stu-id="25b27-111">Call the MS DTC OLE ITransaction::Commit function to commit the MS DTC transaction.</span></span> <span data-ttu-id="25b27-112">Transaction 对象不再有效。</span><span class="sxs-lookup"><span data-stu-id="25b27-112">The Transaction object is no longer valid.</span></span>  
  
 <span data-ttu-id="25b27-113">若要执行一系列 MS DTC 事务，请重复步骤 3 到 6。</span><span class="sxs-lookup"><span data-stu-id="25b27-113">To perform a series of MS DTC transactions, repeat Steps 3 through 6.</span></span>  
  
 <span data-ttu-id="25b27-114">若要释放对 Transaction 对象的引用，请调用 MS DTC OLE ITransaction::Return 函数。</span><span class="sxs-lookup"><span data-stu-id="25b27-114">To release the reference to the Transaction object, call the MS DTC OLE ITransaction::Return function.</span></span>  
  
 <span data-ttu-id="25b27-115">若要将 ODBC 连接用于 MS DTC 事务，然后将该连接用于本地 SQL Server 事务，请调用 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)（带有 SQL_DTC_DONE）。</span><span class="sxs-lookup"><span data-stu-id="25b27-115">To use an ODBC connection with an MS DTC transaction, and then use the same connection with a local SQL Server transaction, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_DTC_DONE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25b27-116">还可以对每个 SQL Server 轮流调用 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 和 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)，而不是按照前面步骤 4 和 5 中的建议调用它们。</span><span class="sxs-lookup"><span data-stu-id="25b27-116">You can also call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) and [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) in turn for each SQL Server instead of calling them as suggested earlier in Steps 4 and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b27-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25b27-117">See Also</span></span>  
 [<span data-ttu-id="25b27-118">&#40;ODBC&#41;执行事务</span><span class="sxs-lookup"><span data-stu-id="25b27-118">Performing Transactions &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
