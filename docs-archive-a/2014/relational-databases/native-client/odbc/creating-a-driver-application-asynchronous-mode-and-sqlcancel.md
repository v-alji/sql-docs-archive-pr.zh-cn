---
title: 异步模式和 SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: rothja
ms.author: jroth
ms.openlocfilehash: 9071c6821e6edeb577b639223e42899d2927bced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588999"
---
# <a name="asynchronous-mode-and-sqlcancel"></a><span data-ttu-id="635b1-102">异步模式和 SQLCancel</span><span class="sxs-lookup"><span data-stu-id="635b1-102">Asynchronous Mode and SQLCancel</span></span>
  <span data-ttu-id="635b1-103">某些 ODBC 函数既可同步操作，也可以异步操作。</span><span class="sxs-lookup"><span data-stu-id="635b1-103">Some ODBC functions can operate either synchronously or asynchronously.</span></span> <span data-ttu-id="635b1-104">应用程序可以为语句句柄或连接句柄启用异步操作。</span><span class="sxs-lookup"><span data-stu-id="635b1-104">The application can enable asynchronous operations for either a statement handle or a connection handle.</span></span> <span data-ttu-id="635b1-105">如果为连接句柄设置了该选项，它将影响连接句柄上的所有语句句柄。</span><span class="sxs-lookup"><span data-stu-id="635b1-105">If the option is set for a connection handle, it affects all statement handles on the connection handle.</span></span> <span data-ttu-id="635b1-106">应用程序使用以下语句启用或禁用异步操作：</span><span class="sxs-lookup"><span data-stu-id="635b1-106">The application uses the following statements to enable or disable asynchronous operations:</span></span>  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="635b1-107">当某个应用程序以异步模式调用 ODBC 函数，在得到服务器已完成命令的通知之前，驱动程序不向应用程序返回控制权。</span><span class="sxs-lookup"><span data-stu-id="635b1-107">When an application calls an ODBC function in synchronous mode, the driver does not return control to the application until it is notified that the server has completed the command.</span></span>  
  
 <span data-ttu-id="635b1-108">异步操作时，驱动程序立即向应用程序返回控制权，甚至在向服务器发送命令之前也可以。</span><span class="sxs-lookup"><span data-stu-id="635b1-108">When operating asynchronously, the driver immediately returns control to the application, even before sending the command to the server.</span></span> <span data-ttu-id="635b1-109">驱动程序将返回代码设置为 SQL_STILL_EXECUTING。</span><span class="sxs-lookup"><span data-stu-id="635b1-109">The driver sets the return code to SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="635b1-110">应用程序随后可执行其他工作。</span><span class="sxs-lookup"><span data-stu-id="635b1-110">The application can then perform other work.</span></span>  
  
 <span data-ttu-id="635b1-111">当应用程序测试命令是否完成时，它会向驱动程序发出带有相同参数的相同函数调用。</span><span class="sxs-lookup"><span data-stu-id="635b1-111">When the application tests for completion of the command, it makes the same function call with the same parameters to the driver.</span></span> <span data-ttu-id="635b1-112">如果驱动程序尚未从服务器接收到回复，它将再次返回 SQL_STILL_EXECUTING。</span><span class="sxs-lookup"><span data-stu-id="635b1-112">If the driver has not yet received an answer from the server, it will again return SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="635b1-113">应用程序必须定期测试该命令，直到返回 SQL_STILL_EXECUTING 之外的代码。</span><span class="sxs-lookup"><span data-stu-id="635b1-113">The application must test the command periodically until the return code is something other than SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="635b1-114">当应用程序收到其他任何返回代码（甚至是 SQL_ERROR）后，它可以确定命令是否已完成。</span><span class="sxs-lookup"><span data-stu-id="635b1-114">When the application gets some other return code, even SQL_ERROR, it can determine that the command has completed.</span></span>  
  
 <span data-ttu-id="635b1-115">有时某个命令长时间未完成。</span><span class="sxs-lookup"><span data-stu-id="635b1-115">Sometimes a command is outstanding for a long time.</span></span> <span data-ttu-id="635b1-116">如果应用程序需要在不等待答复的情况下取消命令，则可以通过使用与未完成的命令相同的语句句柄调用**SQLCancel**来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="635b1-116">If the application needs to cancel the command without waiting for a reply, it can do so by calling **SQLCancel** with the same statement handle as the outstanding command.</span></span> <span data-ttu-id="635b1-117">这是唯一应该使用的**SQLCancel** 。</span><span class="sxs-lookup"><span data-stu-id="635b1-117">This is the only time **SQLCancel** should be used.</span></span> <span data-ttu-id="635b1-118">某些程序员在通过结果集处理部分方法时使用**SQLCancel** ，并希望取消结果集的其余部分。</span><span class="sxs-lookup"><span data-stu-id="635b1-118">Some programmers use **SQLCancel** when they have processed part way through a result set and want to cancel the rest of the result set.</span></span> <span data-ttu-id="635b1-119">应使用[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)或[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)来取消未完成的结果集的剩余部分，而不是**SQLCancel**。</span><span class="sxs-lookup"><span data-stu-id="635b1-119">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) should be used to cancel the remainder of an outstanding result set, not **SQLCancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635b1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="635b1-120">See Also</span></span>  
 [<span data-ttu-id="635b1-121">创建 SQL Server Native Client ODBC 驱动程序应用程序</span><span class="sxs-lookup"><span data-stu-id="635b1-121">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
