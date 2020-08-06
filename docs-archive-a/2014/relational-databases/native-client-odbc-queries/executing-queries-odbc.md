---
title: " (ODBC) 执行查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: rothja
ms.author: jroth
ms.openlocfilehash: adc51186803148056401f58f1207d3e9a7abf9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577609"
---
# <a name="executing-queries-odbc"></a><span data-ttu-id="72c15-102">执行查询 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="72c15-102">Executing Queries (ODBC)</span></span>
  <span data-ttu-id="72c15-103">在 ODBC 应用程序初始化连接句柄并与数据源连接后，它为连接句柄分配一个或多个语句句柄。</span><span class="sxs-lookup"><span data-stu-id="72c15-103">After an ODBC application initializes a connection handle and connects with a data source, it allocates one or more statement handles on the connection handle.</span></span> <span data-ttu-id="72c15-104">然后，应用程序可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对语句句柄执行语句。</span><span class="sxs-lookup"><span data-stu-id="72c15-104">The application can then execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements on the statement handle.</span></span> <span data-ttu-id="72c15-105">执行 SQL 语句时的一般事件顺序为：</span><span class="sxs-lookup"><span data-stu-id="72c15-105">The general sequence of events in executing an SQL statement is:</span></span>  
  
1.  <span data-ttu-id="72c15-106">设置所有所需的语句属性。</span><span class="sxs-lookup"><span data-stu-id="72c15-106">Set any required statement attributes.</span></span>  
  
2.  <span data-ttu-id="72c15-107">构造语句。</span><span class="sxs-lookup"><span data-stu-id="72c15-107">Construct the statement.</span></span>  
  
3.  <span data-ttu-id="72c15-108">执行语句。</span><span class="sxs-lookup"><span data-stu-id="72c15-108">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="72c15-109">检索任何结果集。</span><span class="sxs-lookup"><span data-stu-id="72c15-109">Retrieve any result sets.</span></span>  
  
 <span data-ttu-id="72c15-110">应用程序检索 SQL 语句所返回的所有结果集中的所有行后，它可以在同一语句句柄上执行其他查询。</span><span class="sxs-lookup"><span data-stu-id="72c15-110">After an application retrieves all the rows in all of the result sets returned by the SQL statement, it can execute another query on the same statement handle.</span></span> <span data-ttu-id="72c15-111">如果应用程序确定不需要检索特定结果集中的所有行，则可以通过调用[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)或[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)来取消结果集的其余部分。</span><span class="sxs-lookup"><span data-stu-id="72c15-111">If an application determines that it is not required to retrieve all the rows in a particular result set, it can cancel the rest of the result set by calling either [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
 <span data-ttu-id="72c15-112">如果在 ODBC 应用程序中必须使用不同数据多次执行同一 SQL 语句，可以在 SQL 语句的构造中使用用问号 (?) 表示的参数标记：</span><span class="sxs-lookup"><span data-stu-id="72c15-112">If, in an ODBC application, you must execute the same SQL statement multiple times with different data, use a parameter marker denoted by a question mark (?) in the construction of an SQL statement:</span></span>  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="72c15-113">然后，可以通过调用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)将每个参数标记绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="72c15-113">Each parameter marker can then be bound to a program variable by calling [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md).</span></span>  
  
 <span data-ttu-id="72c15-114">执行所有 SQL 语句并处理它们的结果集之后，应用程序释放语句句柄。</span><span class="sxs-lookup"><span data-stu-id="72c15-114">After all SQL statements execute and their result sets process, the application frees the statement handle.</span></span>  
  
 <span data-ttu-id="72c15-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序支持每个连接句柄多个语句句柄。</span><span class="sxs-lookup"><span data-stu-id="72c15-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports multiple statement handles per connection handle.</span></span> <span data-ttu-id="72c15-116">在连接级别管理事务，以便将针对单个连接句柄上的所有语句句柄执行的所有工作视为同一事务的一部分来管理。</span><span class="sxs-lookup"><span data-stu-id="72c15-116">Transactions are managed at the connection level, so that all work performed on all statement handles on a single connection handle are managed as part of the same transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72c15-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="72c15-117">In This Section</span></span>  
  
-   [<span data-ttu-id="72c15-118">分配语句句柄</span><span class="sxs-lookup"><span data-stu-id="72c15-118">Allocating a Statement Handle</span></span>](allocating-a-statement-handle.md)  
  
-   [<span data-ttu-id="72c15-119">构造 SQL 语句 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="72c15-119">Constructing an SQL Statement &#40;ODBC&#41;</span></span>](constructing-an-sql-statement-odbc.md)  
  
-   [<span data-ttu-id="72c15-120">为游标构造 SQL 语句</span><span class="sxs-lookup"><span data-stu-id="72c15-120">Constructing SQL Statements for Cursors</span></span>](constructing-sql-statements-for-cursors.md)  
  
-   [<span data-ttu-id="72c15-121">使用语句参数</span><span class="sxs-lookup"><span data-stu-id="72c15-121">Using Statement Parameters</span></span>](using-statement-parameters.md)  
  
-   [<span data-ttu-id="72c15-122">&#40;ODBC&#41;执行语句</span><span class="sxs-lookup"><span data-stu-id="72c15-122">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements/executing-statements-odbc.md)  
  
-   [<span data-ttu-id="72c15-123">释放语句句柄</span><span class="sxs-lookup"><span data-stu-id="72c15-123">Freeing a Statement Handle</span></span>](freeing-a-statement-handle.md)  
  
## <a name="see-also"></a><span data-ttu-id="72c15-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72c15-124">See Also</span></span>  
 [<span data-ttu-id="72c15-125">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="72c15-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
