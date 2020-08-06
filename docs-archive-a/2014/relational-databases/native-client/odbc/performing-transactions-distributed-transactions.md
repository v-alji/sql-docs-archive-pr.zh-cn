---
title: 执行分布式事务 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ec23fd1883749e35e67f888e26bdf031ccf7fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579549"
---
# <a name="performing-distributed-transactions"></a><span data-ttu-id="54fe2-102">执行分布式事务</span><span class="sxs-lookup"><span data-stu-id="54fe2-102">Performing Distributed Transactions</span></span>
  <span data-ttu-id="54fe2-103">Microsoft 分布式事务处理协调器 (MS DTC) 允许应用程序跨两个或多个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例扩展事务。</span><span class="sxs-lookup"><span data-stu-id="54fe2-103">The Microsoft Distributed Transaction Coordinator (MS DTC) allows applications to extend transactions across two or more instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54fe2-104">此外，该协调器还允许应用程序参与由符合 Open Group DTP XA 标准的事务管理器管理的事务。</span><span class="sxs-lookup"><span data-stu-id="54fe2-104">It also allows applications to participate in transactions managed by transaction managers that comply with the Open Group DTP XA standard.</span></span>  
  
 <span data-ttu-id="54fe2-105">通常，所有事务管理命令都是通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序发送到服务器的。</span><span class="sxs-lookup"><span data-stu-id="54fe2-105">Normally, all transaction management commands are sent through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to the server.</span></span> <span data-ttu-id="54fe2-106">应用程序通过在关闭自动提交模式的情况下调用[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)来启动事务。</span><span class="sxs-lookup"><span data-stu-id="54fe2-106">The application starts a transaction by calling [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) with the autocommit mode turned off.</span></span> <span data-ttu-id="54fe2-107">然后，应用程序执行包含该事务的更新，并通过 SQL_COMMIT 或 SQL_ROLLBACK 选项调用[SQLEndTran](../../native-client-odbc-api/sqlendtran.md) 。</span><span class="sxs-lookup"><span data-stu-id="54fe2-107">The application then performs the updates comprising the transaction and calls [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) with either the SQL_COMMIT or SQL_ROLLBACK option.</span></span>  
  
 <span data-ttu-id="54fe2-108">但是，在使用 MS DTC 时，MS DTC 成为事务管理器，应用程序不再使用**SQLEndTran**。</span><span class="sxs-lookup"><span data-stu-id="54fe2-108">When using MS DTC, however, MS DTC becomes the transaction manager and the application no longer uses **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="54fe2-109">在分布式事务中登记，然后在第二个分布式事务中登记时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序脱离原始分布式事务并在新事务中登记。</span><span class="sxs-lookup"><span data-stu-id="54fe2-109">When enlisted in a distributed transaction, and then enlist in a second distributed transaction, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver defects from the original distributed transaction and enlists in the new transaction.</span></span> <span data-ttu-id="54fe2-110">有关详细信息，请参阅[DTC 程序员参考](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="54fe2-110">For more information, see [DTC Programmer's Reference](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54fe2-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54fe2-111">See Also</span></span>  
 [<span data-ttu-id="54fe2-112">&#40;ODBC&#41;执行事务</span><span class="sxs-lookup"><span data-stu-id="54fe2-112">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
