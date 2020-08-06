---
title: 分配语句句柄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: rothja
ms.author: jroth
ms.openlocfilehash: fac0802b474f38f6a6c314dd727fa335d14598d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693830"
---
# <a name="allocating-a-statement-handle"></a><span data-ttu-id="16724-102">分配语句句柄</span><span class="sxs-lookup"><span data-stu-id="16724-102">Allocating a Statement Handle</span></span>
  <span data-ttu-id="16724-103">在应用程序可以执行语句之前，它必须分配语句句柄。</span><span class="sxs-lookup"><span data-stu-id="16724-103">Before an application can execute a statement, it must allocate a statement handle.</span></span> <span data-ttu-id="16724-104">为此，可调用**SQLAllocHandle** ，并将*HandleType*参数设置为 SQL_HANDLE_STMT，并将*将 inputhandle*指向连接句柄。</span><span class="sxs-lookup"><span data-stu-id="16724-104">It does this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_STMT and *InputHandle* pointing to a connection handle.</span></span>  
  
 <span data-ttu-id="16724-105">语句属性是语句句柄的特征。</span><span class="sxs-lookup"><span data-stu-id="16724-105">Statement attributes are characteristics of the statement handle.</span></span> <span data-ttu-id="16724-106">示例语句属性可以包括使用书签以及用于语句结果集的游标类型。</span><span class="sxs-lookup"><span data-stu-id="16724-106">Sample statement attributes can include using bookmarks and the kind of cursor to use with the statement's result set.</span></span> <span data-ttu-id="16724-107">语句属性使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)进行设置，并且使用[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)检索其当前设置。</span><span class="sxs-lookup"><span data-stu-id="16724-107">Statement attributes are set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md), and their current settings are retrieved by using [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md).</span></span> <span data-ttu-id="16724-108">不要求应用程序设置任何语句属性；所有语句属性都具有默认值，并且某些语句属性是驱动程序特定的。</span><span class="sxs-lookup"><span data-stu-id="16724-108">There is no requirement that an application set any statement attributes; all statement attributes have defaults, and some are driver specific.</span></span>  
  
 <span data-ttu-id="16724-109">使用多个 ODBC 语句和连接选项时，请务必小心。</span><span class="sxs-lookup"><span data-stu-id="16724-109">Use caution in the use of several ODBC statement and connection options.</span></span> <span data-ttu-id="16724-110">如果调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)并将*fOption*设置为 SQL_ATTR_LOGIN_TIMEOUT 控制应用程序等待建立连接时等待连接超时的时间 (0 指定无限等待) 。</span><span class="sxs-lookup"><span data-stu-id="16724-110">Calling [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with *fOption* set to SQL_ATTR_LOGIN_TIMEOUT controls the time that an application waits for a connection attempt to time-out while waiting to establish a connection (0 specifies an infinite wait).</span></span> <span data-ttu-id="16724-111">响应时间较长的站点可以将此值设置为较高的值，以确保具有充足的时间完成连接。</span><span class="sxs-lookup"><span data-stu-id="16724-111">Sites that have slow response times can set this value high to make sure that connections have sufficient time to be completed.</span></span> <span data-ttu-id="16724-112">然而，间隔应始终足够短，这样，当驱动程序无法连接时，可以在合理的时间内向用户提供回复。</span><span class="sxs-lookup"><span data-stu-id="16724-112">However, the interval should always be low enough to give the user a response in a reasonable time if the driver cannot connect.</span></span>  
  
 <span data-ttu-id="16724-113">调用**SQLSetStmtAttr**并将*fOption*设置为 SQL_ATTR_QUERY_TIMEOUT 会设置查询超时间隔，以帮助保护服务器和用户的长时间运行的查询。</span><span class="sxs-lookup"><span data-stu-id="16724-113">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_QUERY_TIMEOUT sets a query time-out interval to help protect the server and the user from long-running queries.</span></span>  
  
 <span data-ttu-id="16724-114">如果调用**SQLSetStmtAttr**并将*fOption*设置为 SQL_ATTR_MAX_LENGTH 会限制单个语句可以检索的**文本**和**图像**数据量。</span><span class="sxs-lookup"><span data-stu-id="16724-114">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_LENGTH limits the amount of **text** and **image** data that an individual statement can retrieve.</span></span> <span data-ttu-id="16724-115">如果调用**SQLSetStmtAttr** ，并将*fOption*设置为 SQL_ATTR_MAX_ROWS 也会将行集限制为前*n*行（如果这是所有应用程序都需要）。</span><span class="sxs-lookup"><span data-stu-id="16724-115">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_ROWS also limits a rowset to the first *n* rows if that is all the application requires.</span></span> <span data-ttu-id="16724-116">请注意，设置 SQL_ATTR_MAX_ROWS 会导致驱动程序向服务器发出 SET ROWCOUNT 语句。</span><span class="sxs-lookup"><span data-stu-id="16724-116">Note that setting SQL_ATTR_MAX_ROWS causes the driver to issue a SET ROWCOUNT statement to the server.</span></span> <span data-ttu-id="16724-117">这会影响所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 语句，包括触发器和更新。</span><span class="sxs-lookup"><span data-stu-id="16724-117">This affects all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements, including triggers and updates.</span></span>  
  
 <span data-ttu-id="16724-118">当您设置这些选项时，请务必小心。</span><span class="sxs-lookup"><span data-stu-id="16724-118">Use caution when you are setting these options.</span></span> <span data-ttu-id="16724-119">最好是连接句柄中的所有语句句柄对于 SQL_ATTR_MAX_LENGTH 和 SQL_ATTR_MAX_ROWS 都具有相同的设置。</span><span class="sxs-lookup"><span data-stu-id="16724-119">It is best if all statement handles on a connection handle have the same settings for SQL_ATTR_MAX_LENGTH and SQL_ATTR_MAX_ROWS.</span></span> <span data-ttu-id="16724-120">如果驱动程序从一个语句句柄切换到另一个对于这些选项具有不同值的语句句柄，则驱动程序必须生成适当的 SET TEXTSIZE 和 SET ROWCOUNT 语句以更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="16724-120">If the driver switches from a statement handle to another with different values for these options, the driver must generate the appropriate SET TEXTSIZE and SET ROWCOUNT statements to change the settings.</span></span> <span data-ttu-id="16724-121">驱动程序无法将这些语句与用户 SQL 语句放在相同的批中，因为用户 SQL 语句可能包含必须为批中第一条语句的语句。</span><span class="sxs-lookup"><span data-stu-id="16724-121">The driver cannot put these statements in the same batch as the user SQL statement because the user SQL statement can contain a statement that must be the first statement in a batch.</span></span> <span data-ttu-id="16724-122">驱动程序必须在单独的批中发送 SET TEXTSIZE 和 SET ROWCOUNT 语句，这会自动生成到服务器的一次附加往返。</span><span class="sxs-lookup"><span data-stu-id="16724-122">The driver must send the SET TEXTSIZE and SET ROWCOUNT statements in a separate batch, which automatically generates an additional roundtrip to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16724-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16724-123">See Also</span></span>  
 [<span data-ttu-id="16724-124">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="16724-124">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
