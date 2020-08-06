---
title: ODBC 中的事务 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 386b248edfdb6e0ac5eb97b3aeb6c0bbc505a5a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579546"
---
# <a name="transactions-in-odbc"></a><span data-ttu-id="9268a-102">ODBC 中的事务</span><span class="sxs-lookup"><span data-stu-id="9268a-102">Transactions in ODBC</span></span>
  <span data-ttu-id="9268a-103">ODBC 中的事务按连接级别进行管理。</span><span class="sxs-lookup"><span data-stu-id="9268a-103">Transactions in ODBC are managed at the connection level.</span></span> <span data-ttu-id="9268a-104">在应用程序完成某一事务时，它提交或回滚通过该连接上的所有语句句柄完成的所有工作。</span><span class="sxs-lookup"><span data-stu-id="9268a-104">When an application completes a transaction, it commits or rolls back all work completed through all statement handles on that connection.</span></span> <span data-ttu-id="9268a-105">若要提交或回滚事务，应用程序应调用[SQLEndTran](../../native-client-odbc-api/sqlendtran.md) ，而不是提交 COMMIT 或 ROLLBACK 语句。</span><span class="sxs-lookup"><span data-stu-id="9268a-105">To commit or roll back a transaction, applications should call [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) instead of submitting a COMMIT or ROLLBACK statement.</span></span>  
  
 <span data-ttu-id="9268a-106">应用程序调用[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) ，以在两种管理事务的 ODBC 模式之间切换：</span><span class="sxs-lookup"><span data-stu-id="9268a-106">An application calls [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) to switch between the two ODBC modes of managing transactions:</span></span>  
  
-   <span data-ttu-id="9268a-107">自动提交模式</span><span class="sxs-lookup"><span data-stu-id="9268a-107">Autocommit mode</span></span>  
  
     <span data-ttu-id="9268a-108">每个语句都在成功完成后自动提交。</span><span class="sxs-lookup"><span data-stu-id="9268a-108">Each statement is automatically committed when it is completed successfully.</span></span> <span data-ttu-id="9268a-109">当您在自动提交模式中运行时，不要求其他事务管理功能。</span><span class="sxs-lookup"><span data-stu-id="9268a-109">When you run in autocommit mode, no other transaction management functions are required.</span></span>  
  
-   <span data-ttu-id="9268a-110">手动提交模式</span><span class="sxs-lookup"><span data-stu-id="9268a-110">Manual-commit mode</span></span>  
  
     <span data-ttu-id="9268a-111">所有已执行的语句都包含在同一事务中，直到通过调用**SQLEndTran**专门停止它。</span><span class="sxs-lookup"><span data-stu-id="9268a-111">All executed statements are included in the same transaction until it is specifically stopped by calling **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="9268a-112">自动提交模式是针对 ODBC 的默认的事务模式。</span><span class="sxs-lookup"><span data-stu-id="9268a-112">Autocommit mode is the default transaction mode for ODBC.</span></span> <span data-ttu-id="9268a-113">建立连接后，该连接处于自动提交模式，直到调用**SQLSetConnectAttr** ，通过设置自动提交模式来切换为手动提交模式。</span><span class="sxs-lookup"><span data-stu-id="9268a-113">When a connection is made, it is in autocommit mode until **SQLSetConnectAttr** is called to switch to manual-commit mode by setting autocommit mode off.</span></span> <span data-ttu-id="9268a-114">在应用程序关闭自动提交后，发送到数据库的下一个语句将开始某一事务。</span><span class="sxs-lookup"><span data-stu-id="9268a-114">When an application turns autocommit off, the next statement sent to the database starts a transaction.</span></span> <span data-ttu-id="9268a-115">然后，在应用程序调用带有 SQL_COMMIT 或 SQL_ROLLBACK 选项的**SQLEndTran**之前，该事务将一直有效。</span><span class="sxs-lookup"><span data-stu-id="9268a-115">The transaction then remains in effect until the application calls **SQLEndTran** with either the SQL_COMMIT or SQL_ROLLBACK options.</span></span> <span data-ttu-id="9268a-116">**SQLEndTran**在启动下一个事务后发送到数据库的命令。</span><span class="sxs-lookup"><span data-stu-id="9268a-116">The command sent to the database after **SQLEndTran** starts the next transaction.</span></span>  
  
 <span data-ttu-id="9268a-117">如果应用程序从手动提交模式切换到自动提交模式，则驱动程序将提交在该连接上当前打开的所有事务。</span><span class="sxs-lookup"><span data-stu-id="9268a-117">If an application switches from manual-commit to autocommit mode, the driver commits any transactions currently open on the connection.</span></span>  
  
 <span data-ttu-id="9268a-118">ODBC 应用程序不应使用 Transact-SQL 事务语句（例如 BEGIN TRANSACTION、COMMIT TRANSACTION 或 ROLLBACK TRANSACTION），因为这可能导致驱动程序中的不确定行为。</span><span class="sxs-lookup"><span data-stu-id="9268a-118">ODBC applications should not use Transact-SQL transaction statements such as BEGIN TRANSACTION, COMMIT TRANSACTION, or ROLLBACK TRANSACTION because this can cause indeterminate behavior in the driver.</span></span> <span data-ttu-id="9268a-119">ODBC 应用程序应在自动提交模式下运行，而不是使用任何事务管理函数或语句，或在手动提交模式下运行，并使用 ODBC **SQLEndTran**函数提交或回滚事务。</span><span class="sxs-lookup"><span data-stu-id="9268a-119">An ODBC application should run in autocommit mode and not use any transaction management functions or statements, or run in manual-commit mode and use the ODBC **SQLEndTran** function to either commit or roll back transactions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9268a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9268a-120">See Also</span></span>  
 [<span data-ttu-id="9268a-121">&#40;ODBC&#41;执行事务</span><span class="sxs-lookup"><span data-stu-id="9268a-121">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
