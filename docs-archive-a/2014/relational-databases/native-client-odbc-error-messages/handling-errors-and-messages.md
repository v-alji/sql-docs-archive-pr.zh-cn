---
title: 处理错误和消息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: rothja
ms.author: jroth
ms.openlocfilehash: 4701b3224b87e7d19f1121f193d4be20f9d4c441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688906"
---
# <a name="handling-errors-and-messages"></a><span data-ttu-id="30285-102">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="30285-102">Handling Errors and Messages</span></span>
  <span data-ttu-id="30285-103">当应用程序调用 ODBC 函数时，驱动程序执行该函数，并以两种方式返回诊断信息：返回代码指示 ODBC 函数总体成功或失败，诊断记录提供有关函数的详细信息。</span><span class="sxs-lookup"><span data-stu-id="30285-103">When an application calls an ODBC function, the driver executes the function and returns diagnostic information in two ways: A return code indicates the overall success or failure of an ODBC function, and diagnostic records provide detailed information about the function.</span></span> <span data-ttu-id="30285-104">诊断记录包含标题记录和状态记录。</span><span class="sxs-lookup"><span data-stu-id="30285-104">Diagnostic records include a header record and status records.</span></span> <span data-ttu-id="30285-105">即使该函数成功，也仍将至少返回一条诊断记录，即标题记录。</span><span class="sxs-lookup"><span data-stu-id="30285-105">At least one diagnostic record, the header record, is returned even if the function succeeds.</span></span>  
  
 <span data-ttu-id="30285-106">诊断信息用于在开发时捕获编程错误，例如硬编码的 SQL 语句中的无效句柄和语法错误。</span><span class="sxs-lookup"><span data-stu-id="30285-106">Diagnostic information is used at development time to catch programming errors, such as invalid handles and syntax errors in hard-coded SQL statements.</span></span> <span data-ttu-id="30285-107">此外，该信息还用于在运行时捕获运行时错误和警告，例如用户输入的 SQL 语句中的数据截断、规则冲突和语法错误。</span><span class="sxs-lookup"><span data-stu-id="30285-107">It is also used at run time to catch run-time errors and warnings, such as data truncation, rule violations, and syntax errors in SQL statements entered by the user.</span></span> <span data-ttu-id="30285-108">程序逻辑通常基于返回代码。</span><span class="sxs-lookup"><span data-stu-id="30285-108">Program logic is generally based on return codes.</span></span>  
  
 <span data-ttu-id="30285-109">例如，在应用程序调用**SQLFetch**来检索结果集中的行后，返回代码将指示是否已到达结果集的末尾 (SQL_NO_DATA) 、是否 (SQL_SUCCESS_WITH_INFO) 返回了任何信息性消息，或者 (SQL_ERROR) 发生错误。</span><span class="sxs-lookup"><span data-stu-id="30285-109">For example, after an application calls **SQLFetch** to retrieve the rows in a result set, the return code indicates whether the end of the result set was reached (SQL_NO_DATA), if any informational messages were returned (SQL_SUCCESS_WITH_INFO), or if an error occurred (SQL_ERROR).</span></span>  
  
 <span data-ttu-id="30285-110">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序返回 SQL_SUCCESS 以外的任何内容，则应用程序可以调用**SQLGetDiagRec**来检索任何信息或错误消息。</span><span class="sxs-lookup"><span data-stu-id="30285-110">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns anything other than SQL_SUCCESS, the application can call **SQLGetDiagRec** to retrieve any informational or error messages.</span></span> <span data-ttu-id="30285-111">如果有多个消息，请使用**SQLGetDiagRec**向下和向下滚动消息集。</span><span class="sxs-lookup"><span data-stu-id="30285-111">Use **SQLGetDiagRec** to scroll up and down the message set if there is more than one message.</span></span>  
  
 <span data-ttu-id="30285-112">返回代码 SQL_INVALID_HANDLE 始终指示编程错误，并且决不能在运行时遇到。</span><span class="sxs-lookup"><span data-stu-id="30285-112">The return code SQL_INVALID_HANDLE always indicates a programming error and should never be encountered at run time.</span></span> <span data-ttu-id="30285-113">所有其他返回代码提供运行时信息，但 SQL_ERROR 可以指示编程错误。</span><span class="sxs-lookup"><span data-stu-id="30285-113">All other return codes provide run-time information, although SQL_ERROR may indicate a programming error.</span></span>  
  
 <span data-ttu-id="30285-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于 C 的原始本机 API db-library 允许应用程序安装回调错误处理和消息处理函数，这些函数将返回错误或消息。</span><span class="sxs-lookup"><span data-stu-id="30285-114">The original [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native API, DB-Library for C, allows an application to install callback error-handling and message-handling functions that return errors or messages.</span></span> <span data-ttu-id="30285-115">某些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句（如 PRINT、RAISERROR、DBCC 和 SET）将其结果返回到 DB-Library 消息处理程序函数，而不是结果集。</span><span class="sxs-lookup"><span data-stu-id="30285-115">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, such as PRINT, RAISERROR, DBCC, and SET, return their results to the DB-Library message handler function instead of to a result set.</span></span> <span data-ttu-id="30285-116">但是，ODBC API 不具备这种回调功能。</span><span class="sxs-lookup"><span data-stu-id="30285-116">However, the ODBC API has no such callback capability.</span></span> <span data-ttu-id="30285-117">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序检测到返回的消息时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，它会将 ODBC 返回代码设置为 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR 并将消息作为一个或多个诊断记录返回。</span><span class="sxs-lookup"><span data-stu-id="30285-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver detects messages coming back from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it sets the ODBC return code to SQL_SUCCESS_WITH_INFO or SQL_ERROR and returns the message as one or more diagnostic records.</span></span> <span data-ttu-id="30285-118">因此，ODBC 应用程序必须仔细测试这些返回代码，并调用**SQLGetDiagRec**来检索消息数据。</span><span class="sxs-lookup"><span data-stu-id="30285-118">Therefore, an ODBC application must carefully test for these return codes and call **SQLGetDiagRec** to retrieve message data.</span></span>  
  
 <span data-ttu-id="30285-119">有关跟踪错误的详细信息，请参阅[数据访问跟踪](https://go.microsoft.com/fwlink/?LinkId=125805)。</span><span class="sxs-lookup"><span data-stu-id="30285-119">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="30285-120">有关 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中添加的错误跟踪的增强功能的信息，请参阅[访问扩展事件日志中的诊断信息](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)。</span><span class="sxs-lookup"><span data-stu-id="30285-120">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30285-121">本节内容</span><span class="sxs-lookup"><span data-stu-id="30285-121">In This Section</span></span>  
  
-   [<span data-ttu-id="30285-122">处理生成消息的语句</span><span class="sxs-lookup"><span data-stu-id="30285-122">Processing Statements That Generate Messages</span></span>](processing-statements-that-generate-messages.md)  
  
-   [<span data-ttu-id="30285-123">诊断记录和字段</span><span class="sxs-lookup"><span data-stu-id="30285-123">Diagnostic Records and Fields</span></span>](diagnostic-records-and-fields.md)  
  
-   [<span data-ttu-id="30285-124">本机错误号</span><span class="sxs-lookup"><span data-stu-id="30285-124">Native Error Numbers</span></span>](native-error-numbers.md)  
  
-   [<span data-ttu-id="30285-125">SQLSTATE &#40;ODBC 错误代码&#41;</span><span class="sxs-lookup"><span data-stu-id="30285-125">SQLSTATE &#40;ODBC Error Codes&#41;</span></span>](sqlstate-odbc-error-codes.md)  
  
-   [<span data-ttu-id="30285-126">错误消息</span><span class="sxs-lookup"><span data-stu-id="30285-126">Error Messages</span></span>](error-messages.md)  
  
## <a name="see-also"></a><span data-ttu-id="30285-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30285-127">See Also</span></span>  
 [<span data-ttu-id="30285-128">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="30285-128">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
